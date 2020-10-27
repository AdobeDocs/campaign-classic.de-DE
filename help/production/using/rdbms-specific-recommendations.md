---
title: RDBMS-spezifische Empfehlungen
seo-title: RDBMS-spezifische Empfehlungen
description: RDBMS-spezifische Empfehlungen
seo-description: null
page-status-flag: never-activated
uuid: 637c1b5a-0484-4734-a012-eb4ba8036263
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: b2219912-5570-45d2-8b52-52486e29d008
translation-type: tm+mt
source-git-commit: 849e1ebf14f707d9e86c5a152de978acb6f1cb35
workflow-type: tm+mt
source-wordcount: '1128'
ht-degree: 4%

---


# RDBMS-spezifische Empfehlungen{#rdbms-specific-recommendations}

Um Ihnen bei der Erstellung von Wartungsplänen behilflich zu sein, werden in diesem Abschnitt einige Empfehlungen/Best Practices Liste, die an die verschiedenen RDBMS-Motoren angepasst sind, die von Adobe Campaign unterstützt werden. Dies sind jedoch nur Empfehlungen. Es liegt an Ihnen, sie entsprechend Ihren internen Verfahren und Zwängen an Ihre Bedürfnisse anzupassen. Ihr Datenbankadministrator hat die Verantwortung, diese Pläne zu erstellen und auszuführen.

## PostgreSQL {#postgresql}

### Große Tabellen erkennen {#detecting-large-tables}

1. Sie können der Datenbank die folgende Ansicht hinzufügen:

   ```
   create or replace view uvSpace
    as
    SELECT c1.relname AS tablename, c2.relname AS indexname, c2.relpages * 8 / 1024 AS size_mbytes, c2.relfilenode AS filename, 0 AS row_count
    FROM pg_class c1, pg_class c2, pg_index i
    WHERE c1.oid = i.indrelid AND i.indexrelid = c2.oid
    UNION 
    SELECT pg_class.relname AS tablename, NULL::"unknown" AS indexname, pg_class.relpages * 8 / 1024 AS size_mbytes, pg_class.relfilenode AS filename, cast(pg_class.reltuples as integer) AS row_count
    FROM pg_class
    WHERE pg_class.relkind = 'r'::"char"
    ORDER BY 3 DESC, 1, 2 DESC;
   ```

1. Wenn Sie den folgenden Befehl ausführen, können Sie große Tabellen und Indizes ausfindig machen:

   ```
   select * from uvSpace;
   ```

### Einfache Wartung {#simple-maintenance}

Unter PostgreSQL sind die typischen Befehle, die Sie verwenden können, **vakuumvoll** und **reindex**.

Hier ein typisches Beispiel für einen SQL-Wartungsplan, der regelmäßig mit den beiden folgenden Befehlen ausgeführt werden soll:

```
vacuum full nmsdelivery;
 reindex table nmsdelivery;
 
 vacuum full nmsdeliverystat;
 reindex table nmsdeliverystat;
 
 vacuum full xtkworkflow;
 reindex table xtkworkflow;
 
 vacuum full xtkworkflowevent;
 reindex table xtkworkflowevent;
 
 vacuum full xtkworkflowjob;
 reindex table xtkworkflowjob;
 
 vacuum full xtkworkflowlog;
 reindex table xtkworkflowlog;
 
 vacuum full xtkworkflowtask;
 reindex table xtkworkflowtask;
 
 vacuum full xtkjoblog;
 reindex table xtkjoblog;
 
 vacuum full xtkjob;
 reindex table xtkjob;
 
 vacuum full nmsaddress;
 reindex table nmsaddress;

 vacuum full nmsdeliverypart;
 reindex table nmsdeliverypart;
 
 vacuum full nmsmirrorpageinfo;
 reindex table nmsmirrorpageinfo;
```

>[!NOTE]
>
>* Adobe empfiehlt, mit kleineren Tabellen zu beginnen: auf diese Weise, wenn der Prozess auf großen Tabellen (bei denen das Ausfallrisiko am größten ist) fehlschlägt, wurde mindestens ein Teil der Instandhaltung abgeschlossen.
>* Adobe empfiehlt, die für Ihr Datenmodell spezifischen Tabellen hinzuzufügen, die erheblich aktualisiert werden können. Dies kann bei **NmsRecipient** der Fall sein, wenn Sie über große Datenreplikationsflüsse pro Tag verfügen.
>* Die Befehle **Vakuum** und **Neuindizierung** sperren die Tabelle, wodurch einige Prozesse während der Wartung angehalten werden.
>* Bei sehr großen Tischen (normalerweise über 5 Gb) kann **Vakuum gefüllt** ziemlich ineffizient werden und sehr lange dauern. Es wird nicht empfohlen, sie für die **Tabelle YyyNmsBroadLogXxx** zu verwenden.
>* Dieser Wartungsvorgang kann mithilfe einer **[!UICONTROL SQL]** -Aktivität von einem Adobe Campaign-Workflow implementiert werden (weitere Informationen hierzu finden Sie in [diesem Abschnitt](../../workflow/using/architecture.md)). Vergewissern Sie sich, dass Sie die Wartung für eine niedrige Aktivität planen, die nicht mit Ihrem Sicherungsfenster kollidiert.

>



### Erstellen einer Datenbank {#rebuilding-a-database}

PostgreSQL bietet keine einfache Möglichkeit, eine Online-Tabelle neu zu erstellen, da die Tabelle durch **Vakuum voll** gesperrt wird, was eine regelmäßige Produktion verhindert. Dies bedeutet, dass eine Wartung durchgeführt werden muss, wenn die Tabelle nicht verwendet wird. Sie können

* Wartung beim Beenden der Adobe Campaign-Plattform,
* Beenden Sie die verschiedenen Adobe Campaign-Unterdienste, die wahrscheinlich in die neu erstellte Tabelle schreiben (**nlserver stop wfserver instance_name** , um den Workflow-Prozess zu stoppen).

Im Folgenden finden Sie ein Beispiel für die Tabellendefragmentierung mit bestimmten Funktionen zum Generieren der erforderlichen DDL. Mit der folgenden SQL-Datenbank können Sie zwei neue Funktionen erstellen: **GenRebuildTablePart1** und **GenRebuildTablePart2**, die zum Generieren der erforderlichen DDL zum Erstellen einer Tabelle verwendet werden können.

* Mit der ersten Funktion können Sie eine Arbeitstabelle (** _tmp** hier) erstellen, die eine Kopie der ursprünglichen Tabelle ist.
* Die zweite Funktion löscht dann die ursprüngliche Tabelle und benennt die Arbeitstabelle und ihre Indizes um.
* Die Verwendung von zwei Funktionen anstelle einer Funktion bedeutet, dass bei einem Ausfall der ersten Tabelle keine Gefahr besteht, die ursprüngliche Tabelle zu löschen.

```
 -- --------------------------------------------------------------------------
 -- Generate the CREATE TABLE DDL for a table
 -- --------------------------------------------------------------------------
 create or replace function GenTableDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecFld RECORD;
 vstrDDL text;
 vstrFields text;
 vstrNsTable text;
 vstrTableSpace text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 SELECT
 pg_catalog.quote_ident(n.nspname) || '.' || pg_catalog.quote_ident(c.relname),
 pg_catalog.quote_ident(t.spcname)
 INTO
 vstrNsTable, vstrTableSpace
 FROM
 pg_namespace n, pg_class c left outer join pg_tablespace t on c.reltablespace = t.oid
 WHERE
 n.oid = c.relnamespace AND
 c.relname = vstrTable;
 
 vstrDDL = 'CREATE TABLE ' || vstrNsTable || '_tmp(';
 
 vstrFields = ;
 FOR vrecFld IN
 SELECT
 pg_catalog.quote_ident(a.attname) ||
 ' ' || t.typname ||
 case when t.typname='varchar' then '(' || cast(a.atttypmod-4 as text) || ')'
 when t.typname='numeric' then '(' || cast((a.atttypmod-4)/65536 as text) || ',' || cast((a.atttypmod-4)%65536 as text) || ')'
 else end ||
 case when a.attnotnull then ' not null' else end ||
 case when a.atthasdef then ' default '|| d.adsrc else end as DDL
 FROM
 pg_type t, pg_class c, pg_attribute a LEFT OUTER JOIN pg_attrdef d ON d.adrelid=a.attrelid and d.adnum=a.attnum
 WHERE 
 a.attnum > 0 AND
 a.attrelid = c.oid AND
 t.oid = a.atttypid AND
 c.relname = vstrTable
 ORDER BY
 a.attnum
 LOOP
 IF vstrFields <> THEN
 vstrFields = vstrFields || ',' || chr(10) || ' ';
 ELSE
 vstrFields = vstrFields || chr(10) || ' ';
 END IF;
 vstrFields = vstrFields || vrecFld.DDL;
 END LOOP;
 
 vstrDDL = vstrDDL || vstrFields || chr(10) || ')';
 if vstrTableSpace <> then
 vstrDDL = vstrDDL || ' TABLESPACE ' || vstrTableSpace;
 end if;
 vstrDDL = vstrDDL || ';' || chr(10);
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Generate the CREATE INDEX DDL for a table
 -- --------------------------------------------------------------------------
 create or replace function GenIndexDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecIndex RECORD;
 vstrDDL text;
 viFld integer;
 vstrFld text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 FOR vrecIndex IN
 SELECT
 i.indkey, i.indisunique,
 pg_catalog.quote_ident(c.relname) as tablename,
 pg_catalog.quote_ident(ic.relname) as indexname,
 pg_catalog.quote_ident(t.spcname) as tablespace
 FROM
 pg_class c, pg_index i, pg_class ic left outer join pg_tablespace t on ic.reltablespace = t.oid
 WHERE
 i.indexrelid = ic.oid AND
 i.indrelid = c.oid AND
 c.relname = vstrTable
 LOOP
 
  vstrDDL = vstrDDL || 'CREATE ';
  if vrecIndex.indisunique then
  vstrDDL = vstrDDL || 'UNIQUE ';
  end if;
  vstrDDL = vstrDDL ||
   'INDEX ' ||vrecIndex.indexname || '_tmp ON ' ||
   vrecIndex.tablename || '_tmp(';
 
  FOR viFld IN array_lower(vrecIndex.indkey, 1) .. array_upper(vrecIndex.indkey, 1) LOOP
  SELECT pg_catalog.quote_ident(a.attname) INTO vstrFld 
  FROM 
   pg_attribute a, pg_class c
  WHERE 
   a.attnum = vrecIndex.indkey[viFld] AND
   a.attrelid = c.oid AND c.relname=vstrTable;
  
  vstrDDL = vstrDDL || vstrFld;
  if viFld <> array_upper(vrecIndex.indkey, 1) then
   vstrDDL = vstrDDL || ', ';
  end if;
  END LOOP;
  vstrDDL = vstrDDL || ')';
 
  if vrecIndex.tablespace <> then
  vstrDDL = vstrDDL || 'TABLESPACE ' || vrecIndex.tablespace;
  end if;
  vstrDDL = vstrDDL || ';' || chr(10);
 
 END LOOP;
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Generate the ALTER INDEX RENAME for a table
 -- --------------------------------------------------------------------------
 create or replace function GenRenameIndexDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecIndex RECORD;
 vstrDDL text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 FOR vrecIndex IN
  SELECT
  pg_catalog.quote_ident(n.nspname) as namespace,
  pg_catalog.quote_ident(ic.relname) as indexname
  FROM
  pg_namespace n, pg_class c, pg_index i, pg_class ic
  WHERE
  i.indexrelid = ic.oid AND
  n.oid = ic.relnamespace AND
  i.indrelid = c.oid AND
  c.relname = vstrTable
 LOOP
 
  vstrDDL = vstrDDL || 'ALTER INDEX ' || vrecIndex.namespace || '.' || vrecIndex.indexname ||
    '_tmp RENAME TO ' || vrecIndex.indexname ||
    ';' || chr(10);
 END LOOP;
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Build a copy of a table, with index
 -- --------------------------------------------------------------------------
 create or replace function GenRebuildTablePart1(text) returns text as $$
 declare
 vstrTable text;
 vstrTmp text;
 vstrDDL text;
 begin
 vstrTable = lower($1);
  
 vstrDDL = ;
 
 SELECT GenTableDDL(vstrTable) INTO vstrTmp;
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 
 vstrDDL = vstrDDL|| 'INSERT INTO ' || vstrTable || '_tmp SELECT * FROM ' || vstrTable || ';'||chr(10);
 SELECT GenIndexDDL(vstrTable) INTO vstrTmp;
 
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 vstrDDL = vstrDDL|| 'VACUUM ANALYSE '|| vstrTable || '_tmp;' ||chr(10);
 
 return vstrDDL;
 end;
 $$ LANGUAGE plpgsql;
 
 -- --------------------------------------------------------------------------
 -- Drop the original table and rename the copy
 -- --------------------------------------------------------------------------
 create or replace function GenRebuildTablePart2(text) returns text as $$
 declare
 vstrTable text;
 vstrTmp text;
 vstrDDL text;
 begin
 vstrTable = lower($1);
  
 vstrDDL = 'DROP TABLE ' || vstrTable||';'|| chr(10);
 vstrDDL = vstrDDL|| 'ALTER TABLE ' || vstrTable || '_tmp RENAME TO ' || vstrTable ||';'|| chr(10);
 
 SELECT GenRenameIndexDDL(vstrTable) INTO vstrTmp;
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 
 return vstrDDL;
 end;
 $$ LANGUAGE plpgsql;
```

Das folgende Beispiel kann in einem Arbeitsablauf verwendet werden, um die erforderlichen Tabellen neu zu erstellen, anstatt den Befehl **Vakuum/Neu erstellen** zu verwenden:

```
function sqlGetMemo(strSql)
 {
 var res = sqlSelect("s, m:memo", strSql);
 return res.s.m.toString();
 }

 function RebuildTable(strTable)
 {
 // Rebuild a table_tmp
 var strSql = sqlGetMemo("select GenRebuildTablePart1('"+strTable+"')");
 logInfo("Rebuilding table '"+strTable+"'...");
 // logInfo(strSql);
 sqlExec(strSql);
 
 // If fails, there is an exception thrown and so we do not delete the original table
 strSql = sqlGetMemo("select GenRebuildTablePart2('"+strTable+"')");
 logInfo("Swapping table '"+strTable+"'...");
 //logInfo(strSql);
 sqlExec(strSql);
 }
 
 RebuildTable('nmsrecipient');
 RebuildTable('nmsrcpgrlrel');
 // ... other tables here
```

## Oracle {#oracle}

Wenden Sie sich an Ihren Datenbankadministrator, um die für Ihre Oracle-Version am besten geeigneten Verfahren zu ermitteln.

## Microsoft SQL Server {#microsoft-sql-server}

>[!NOTE]
>
>Für Microsoft SQL Server können Sie den auf [dieser Seite](https://ola.hallengren.com/sql-server-index-and-statistics-maintenance.html)beschriebenen Wartungsplan verwenden.

Das folgende Beispiel betrifft Microsoft SQL Server 2005. Wenn Sie eine andere Version verwenden, wenden Sie sich an Ihren Datenbankadministrator, um Informationen zu den Wartungsabläufen zu erhalten.

1. Verbinden Sie sich zunächst mit Microsoft SQL Server Management Studio mit einer Anmeldung mit Administratorrechten.
1. Wechseln Sie zum Ordner &quot; **[!UICONTROL Management&quot;> &quot;Wartungspläne]** &quot;, klicken Sie mit der rechten Maustaste darauf und wählen Sie den Assistenten für den **[!UICONTROL Wartungsplan]**
1. Klicken Sie auf **[!UICONTROL Weiter]** , wenn die erste Seite angezeigt wird.
1. Wählen Sie die Art des zu erstellenden Wartungsplans aus (separate Zeitpläne für jede Aufgabe oder einen einzelnen Plan) und klicken Sie dann auf **[!UICONTROL Ändern...]** Schaltfläche.
1. Wählen Sie im Fenster Eigenschaften **[!UICONTROL des]** Auftragsplanes die gewünschten Ausführungseinstellungen aus und klicken Sie auf **[!UICONTROL OK]** und dann auf **[!UICONTROL Weiter]** .
1. Wählen Sie die gewünschten Aufgaben zur Wartung aus und klicken Sie auf **[!UICONTROL Weiter]** .

   >[!NOTE]
   >
   >Es wird empfohlen, mindestens die unten aufgeführten Aufgaben durchzuführen. Sie können auch die Statistikaktualisierungs-Aufgabe auswählen, obwohl sie bereits vom Datenbankbereinigungsarbeitsablauf ausgeführt wurde.

1. Wählen Sie in der Dropdown-Liste die Datenbank aus, auf der die Aufgabe **[!UICONTROL Datenbankprüfung]** ausgeführt werden soll.
1. Wählen Sie die Datenbank aus und klicken Sie auf **[!UICONTROL OK]** und dann auf **[!UICONTROL Weiter]** .
1. Konfigurieren Sie die Ihrer Datenbank zugewiesene Maximalgröße und klicken Sie dann auf **[!UICONTROL Weiter]** .

   >[!NOTE]
   >
   >Wenn die Größe der Datenbank diesen Schwellenwert überschreitet, versucht der Wartungsplan, nicht verwendete Daten zu löschen, um Speicherplatz freizugeben.

1. Index neu organisieren oder neu erstellen:

   * Wenn die Indexfragmentierungsrate zwischen 10 % und 40 % liegt, wird eine Neuorganisation empfohlen.

      Wählen Sie aus, welche Datenbanken und Objekte (Tabellen oder Ansichten) Sie neu organisieren möchten, und klicken Sie auf **[!UICONTROL Weiter]** .

      >[!NOTE]
      >
      >Je nach Konfiguration können Sie entweder die zuvor ausgewählten Tabellen oder alle Tabellen in Ihrer Datenbank auswählen.

   * Wenn die Indexfragmentierungsrate höher als 40 % ist, wird eine Neuerstellung empfohlen.

      Wählen Sie die Optionen aus, die Sie auf die Aufgabe zur Indexerstellung anwenden möchten, und klicken Sie dann auf **[!UICONTROL Weiter]** .

      >[!NOTE]
      >
      >Der Prozess zum Erstellen von Indizes ist im Hinblick auf die Verwendung des Prozessors restriktiver und sperrt die Datenbankressourcen. Wenn der Index während der Neuerstellung verfügbar sein soll, klicken Sie auf die Option &quot;Index **[!UICONTROL beibehalten]** &quot;.

1. Wählen Sie die Optionen aus, die im Bericht Aktivität angezeigt werden sollen, und klicken Sie dann auf **[!UICONTROL Weiter]** .
1. Überprüfen Sie die Liste der für den Wartungsplan konfigurierten Aufgaben und klicken Sie dann auf **[!UICONTROL Fertig stellen]** .

   Eine Zusammenfassung des Wartungsplans und der Status der einzelnen Schritte wird angezeigt.

1. Klicken Sie nach Abschluss des Wartungsplans auf **[!UICONTROL Schließen]** .
1. Klicken Sie im Microsoft SQL Server-Explorer bei gedrückter Dublette auf den Ordner **[!UICONTROL Management > Wartungspläne]** .
1. Wählen Sie den Adobe Campaign-Wartungsplan aus: Die verschiedenen Schritte werden in einem Workflow beschrieben.

   Beachten Sie, dass im Ordner **[!UICONTROL SQL Server Agent > Aufträge]** ein Objekt erstellt wurde. Mit diesem Objekt können Sie den Wartungsplan Beginn haben. In unserem Beispiel gibt es nur ein Objekt, da alle Wartungs-Aufgaben Teil desselben Plans sind.

   >[!IMPORTANT]
   >
   >Damit dieses Objekt ausgeführt werden kann, muss der Microsoft SQL Server-Agent aktiviert sein.

**Konfigurieren einer separaten Datenbank für Tabellen**

>[!NOTE]
>
>Hierbei handelt es sich um eine optionale Konfiguration.

Mit der Option **WdbcOptions_TempDbName** können Sie eine separate Datenbank für Tabellen auf Microsoft SQL Server konfigurieren. Dadurch werden Backups und Replikation optimiert – 

Diese Option kann verwendet werden, wenn Arbeitstabellen (z. B. die während der Ausführung eines Workflows erstellten Tabellen) in einer anderen Datenbank erstellt werden sollen.

Wenn Sie die Option auf &quot;tempdb.dbo.&quot;festlegen, werden Arbeitstabellen für die temporäre Standarddatenbank von Microsoft SQL Server erstellt. Der Datenbankadministrator muss Schreibzugriff auf die tempdb-Datenbank zulassen.

Wenn diese Option festgelegt ist, wird sie in allen Microsoft SQL Server-Datenbanken verwendet, die in Adobe Campaign konfiguriert sind (Hauptdatenbank und Externe Konti). Beachten Sie, dass Konflikte auftreten können, wenn zwei Externe Konti denselben Server gemeinsam nutzen (da die tempdb-Datei eindeutig ist). Auf dieselbe Weise kann es bei zwei Instanzen mit Kampagne, die denselben MSSQL-Server verwenden, zu Konflikten kommen, wenn sie dasselbe tempdb verwenden.

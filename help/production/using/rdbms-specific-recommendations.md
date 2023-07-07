---
product: campaign
title: RDBMS-spezifische Empfehlungen
description: RDBMS-spezifische Empfehlungen
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: a586d70b-1b7f-47c2-a821-635098a70e45
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1214'
ht-degree: 4%

---

# RDBMS-spezifische Empfehlungen{#rdbms-specific-recommendations}



Um Sie bei der Einrichtung von Wartungsplänen zu unterstützen, finden Sie in diesem Abschnitt einige Empfehlungen und Best Practices, die an die verschiedenen von Adobe Campaign unterstützten RDBMS-Engines angepasst sind. Dies sind jedoch nur Empfehlungen. Es liegt an Ihnen, sie entsprechend Ihren internen Verfahren und Einschränkungen Ihren Bedürfnissen anzupassen. Ihr Datenbankadministrator ist dafür verantwortlich, diese Pläne zu erstellen und auszuführen.

## PostgreSQL {#postgresql}

### Große Tabellen erkennen {#detecting-large-tables}

1. Sie können Ihrer Datenbank die folgende Ansicht hinzufügen:

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

1. Sie können diese Abfrage ausführen, um große Tabellen und Indizes zu sehen:

   ```
   SELECT * FROM uvSpace;
   ```

   Alternativ können Sie diese Abfrage ausführen, um beispielsweise alle Indexgrößen gemeinsam anzuzeigen:

   ```
   SELECT
      tablename,
      sum(size_mbytes) AS "sizeMB_all",
      (
         SELECT sum(size_mbytes)
         FROM uvspace
         AS uv2
         WHERE
            INDEXNAME IS NULL
            AND uv1.tablename = uv2.tablename
      ) AS "sizeMB_data",
      (
         SELECT sum(size_mbytes)
         FROM uvspace 
         AS uv2 
         WHERE
            INDEXNAME IS NOT NULL
            AND uv1.tablename = uv2.tablename
      ) AS "sizeMB_index",
      (
         SELECT ROW_COUNT
         FROM uvspace
         AS uv2
         WHERE
            INDEXNAME IS NULL
            AND uv1.tablename = uv2.tablename
      ) AS ROWS FROM uvspace AS uv1
      GROUP BY tablename
      ORDER BY 2 DESC
   ```

### Einfache Wartung {#simple-maintenance}

In PostgreSQL können Sie die folgenden typischen Suchbegriffe verwenden:

* VACUUM (VOLLSTÄNDIG, ANALYSE, VERBOSE)

Um den VACUUM-Vorgang auszuführen und zu analysieren und zu analysieren, können Sie diese Syntax verwenden:

```
\timing on
VACUUM (FULL, ANALYZE, VERBOSE) <table>;
```

Es wird dringend empfohlen, die ANALYZE -Anweisung nicht wegzulassen. Andernfalls wird der leere Tisch ohne Statistiken belassen. Der Grund dafür ist, dass eine neue Tabelle erstellt und dann die alte gelöscht wird. Daher ändert sich die Objekt-ID (OID) der Tabelle, es werden jedoch keine Statistiken berechnet. Folglich treten sofort Leistungsprobleme auf.

Im Folgenden finden Sie ein typisches Beispiel für einen SQL-Wartungsplan, der regelmäßig ausgeführt werden soll:

```
\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdelivery;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdeliverystat;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflow;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowevent;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowjob;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowlog;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowtask;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkjoblog;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkjob;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsaddress;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdeliverypart;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsmirrorpageinfo;
```

>[!NOTE]
>
>* Adobe empfiehlt, mit kleineren Tabellen zu beginnen: Auf diese Weise wurde zumindest ein Teil der Wartung abgeschlossen, wenn der Prozess in großen Tabellen fehlschlägt (bei denen das Fehlerrisiko am größten ist).
>* Adobe empfiehlt, die für Ihr Datenmodell spezifischen Tabellen hinzuzufügen, die erheblich aktualisiert werden können. Dies kann der Fall sein für **NmsRecipient** wenn Sie über große tägliche Datenreplikationsflüsse verfügen.
>* Die VACUUM-Anweisung sperrt die Tabelle, wodurch einige Prozesse während der Wartung angehalten werden.
>* Bei sehr großen Tabellen (in der Regel über 5 GB) kann die VACUUM FULL-Anweisung sehr ineffizient werden und sehr lange dauern. Adobe rät davon ab, sie für die **YyyNmsBroadLogXxx** Tabelle.
>* Dieser Wartungsvorgang kann mithilfe eines Adobe Campaign-Workflows implementiert werden. **[!UICONTROL SQL]** Aktivität. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../workflow/using/architecture.md). Stellen Sie sicher, dass Sie die Wartung für eine niedrige Aktivitätsdauer planen, die nicht mit Ihrem Sicherungsfenster kollidiert.
>

### Datenbank neu erstellen {#rebuilding-a-database}

PostgreSQL bietet keine einfache Möglichkeit, eine Online-Tabellen-Neuerstellung durchzuführen, da die VACUUM FULL-Anweisung die Tabelle sperrt, wodurch eine reguläre Produktion verhindert wird. Dies bedeutet, dass die Wartung durchgeführt werden muss, wenn die Tabelle nicht verwendet wird. Sie können

* Wartung durchführen, wenn die Adobe Campaign-Plattform angehalten wird,
* Stoppen Sie die verschiedenen Adobe Campaign-Unterdienste, die wahrscheinlich in die neu erstellte Tabelle schreiben (**nlserver stop wfserver instance_name** zum Anhalten des Workflow-Prozesses).

Im Folgenden finden Sie ein Beispiel für die Tabellendefragmentierung mit bestimmten Funktionen zum Generieren der erforderlichen DDL. Mit der folgenden SQL-Datei können Sie zwei neue Funktionen erstellen: **GenRebuildTablePart1** und **GenRebuildTablePart2**, die verwendet werden kann, um die erforderliche DDL für die Erstellung einer Tabelle zu generieren.

* Mit der ersten Funktion können Sie eine Arbeitstabelle (** _tmp** hier) erstellen, die eine Kopie der ursprünglichen Tabelle ist.
* Die zweite Funktion löscht dann die ursprüngliche Tabelle und benennt die Arbeitstabelle und ihre Indizes um.
* Die Verwendung von zwei statt einer Funktion bedeutet, dass bei einem Ausfall der ersten nicht das Risiko besteht, die ursprüngliche Tabelle zu löschen.

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

Das folgende Beispiel kann in einem Workflow verwendet werden, um die erforderlichen Tabellen neu zu erstellen, anstatt die **Vakuum/Neu erstellen** command:

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

Wenden Sie sich an Ihren Datenbankadministrator, um herauszufinden, welche Verfahren für Ihre Oracle-Version am besten geeignet sind.

## Microsoft SQL Server {#microsoft-sql-server}

>[!NOTE]
>
>Für Microsoft SQL Server können Sie den Wartungsplan verwenden, der im Abschnitt [diese Seite](https://ola.hallengren.com/sql-server-index-and-statistics-maintenance.html).

Das folgende Beispiel betrifft Microsoft SQL Server 2005. Wenn Sie eine andere Version verwenden, wenden Sie sich an Ihren Datenbankadministrator, um Informationen über die Wartungsmaßnahmen zu erhalten.

1. Stellen Sie zunächst eine Verbindung zu Microsoft SQL Server Management Studio mit einer Anmeldung mit Administratorrechten her.
1. Navigieren Sie zu **[!UICONTROL Management > Wartungspläne]** Ordner, klicken Sie mit der rechten Maustaste darauf und wählen Sie **[!UICONTROL Wartungsassistent]**.
1. Klicken **[!UICONTROL Nächste]** wenn die erste Seite angezeigt wird.
1. Wählen Sie die Art des zu erstellenden Wartungsplans aus (separate Zeitpläne für jede Aufgabe oder einzelne Zeitpläne für den gesamten Plan) und klicken Sie dann auf die Schaltfläche **[!UICONTROL Ändern...]** Schaltfläche.
1. Im **[!UICONTROL Eigenschaften für Job-Zeitpläne]** die gewünschten Ausführungsparameter auswählen und auf **[!UICONTROL OK]** Klicken Sie auf **[!UICONTROL Nächste]**.
1. Wählen Sie die gewünschten Wartungsaufgaben aus und klicken Sie auf **[!UICONTROL Nächste]**.

   >[!NOTE]
   >
   >Es wird empfohlen, mindestens die unten aufgeführten Wartungsaufgaben durchzuführen. Sie können auch die Aufgabe Statistikaktualisierung auswählen, die jedoch bereits vom Datenbankbereinigungs-Workflow durchgeführt wird.

1. Wählen Sie in der Dropdown-Liste die Datenbank aus, für die Sie die **[!UICONTROL Integrität der Datenbanküberprüfung]** Aufgabe.
1. Wählen Sie die Datenbank aus und klicken Sie auf **[!UICONTROL OK]** Klicken Sie auf **[!UICONTROL Nächste]**.
1. Konfigurieren Sie die Ihrer Datenbank zugewiesene Maximalgröße und klicken Sie auf **[!UICONTROL Nächste]**.

   >[!NOTE]
   >
   >Wenn die Größe der Datenbank diesen Schwellenwert überschreitet, versucht der Wartungsplan, nicht verwendete Daten zu löschen, um Speicherplatz zu sparen.

1. Organisieren oder erstellen Sie den Index neu:

   * Wenn die Indexfragmentierungsrate zwischen 10 % und 40 % liegt, wird eine Neuorganisation empfohlen.

     Wählen Sie aus, welche Datenbanken und Objekte (Tabellen oder Ansichten) Sie neu organisieren möchten, und klicken Sie dann auf **[!UICONTROL Nächste]**.

     >[!NOTE]
     >
     >Je nach Konfiguration können Sie entweder die zuvor ausgewählten Tabellen oder alle Tabellen in Ihrer Datenbank auswählen.

   * Wenn die Indexfragmentierungsrate über 40 % liegt, wird eine Neuerstellung empfohlen.

     Wählen Sie die Optionen aus, die Sie auf die Neuerstellungsaufgabe des Index anwenden möchten, und klicken Sie dann auf **[!UICONTROL Nächste]**.

     >[!NOTE]
     >
     >Der Prozess zur Neuerstellung von Indizes ist im Hinblick auf die Prozessorverwendung strenger und sperrt die Datenbankressourcen. Wählen Sie die **[!UICONTROL Index bei Neuindizierung online halten]** , wenn der Index während der Neuerstellung verfügbar sein soll.

1. Wählen Sie die Optionen aus, die im Aktivitätsbericht angezeigt werden sollen, und klicken Sie auf **[!UICONTROL Nächste]**.
1. Überprüfen Sie die Liste der für den Wartungsplan konfigurierten Aufgaben und klicken Sie auf **[!UICONTROL Beenden]**.

   Eine Zusammenfassung des Wartungsplans und der Status der einzelnen Schritte wird angezeigt.

1. Sobald der Wartungsplan abgeschlossen ist, klicken Sie auf **[!UICONTROL Schließen]**.
1. Doppelklicken Sie im Microsoft SQL Server-Explorer auf die **[!UICONTROL Management > Wartungspläne]** Ordner.
1. Wählen Sie den Adobe Campaign-Wartungsplan aus: Die verschiedenen Schritte werden in einem Workflow beschrieben.

   Beachten Sie, dass ein Objekt im **[!UICONTROL SQL Server Agent > Aufträge]** Ordner. Mit diesem Objekt können Sie den Wartungsplan starten. In unserem Beispiel gibt es nur ein Objekt, da alle Wartungsaufgaben Teil desselben Plans sind.

   >[!IMPORTANT]
   >
   >Damit dieses Objekt ausgeführt werden kann, muss der Microsoft SQL Server-Agent aktiviert sein.

**Separate Datenbank für Arbeitstabellen konfigurieren**

>[!NOTE]
>
>Hierbei handelt es sich um eine optionale Konfiguration.

Mit der Option **WdbcOptions_TempDbName** können Sie eine separate Datenbank für Tabellen auf Microsoft SQL Server konfigurieren. Dadurch werden Backups und Replikation optimiert – 

Diese Option kann verwendet werden, wenn Arbeitstabellen (z. B. die bei Ausführung eines Workflows erstellten Tabellen) in einer anderen Datenbank erstellt werden sollen.

Wenn Sie die Option auf &quot;tempdb.dbo.&quot;festlegen, werden die Arbeitstabellen in der temporären Standarddatenbank von Microsoft SQL Server erstellt. Der Datenbankadministrator muss Schreibzugriff auf die tempdb-Datenbank zulassen.

Wenn die Option festgelegt ist, wird sie in allen in Adobe Campaign konfigurierten Microsoft SQL Server-Datenbanken (Hauptdatenbank und externe Konten) verwendet. Beachten Sie, dass Konflikte auftreten können, wenn zwei externe Konten denselben Server teilen (da die tempdb-Datei eindeutig ist). Wenn zwei Campaign-Instanzen denselben MSSQL-Server verwenden, kann es auf die gleiche Weise zu Konflikten kommen, wenn sie dasselbe tempdb verwenden.

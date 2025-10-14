---
product: campaign
title: RDBMS-spezifische Empfehlungen
description: RDBMS-spezifische Empfehlungen
feature: Monitoring
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: a586d70b-1b7f-47c2-a821-635098a70e45
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '1273'
ht-degree: 3%

---

# RDBMS-spezifische Empfehlungen{#rdbms-specific-recommendations}



Um Sie beim Einrichten von Wartungsplänen zu unterstützen, werden in diesem Abschnitt einige Empfehlungen und Best Practices aufgeführt, die an die verschiedenen von Adobe Campaign unterstützten RDBMS-Engines angepasst sind. Dies sind jedoch nur Empfehlungen. Es liegt an Ihnen, sie an Ihre Bedürfnisse anzupassen, in Übereinstimmung mit Ihrem internen Verfahren und Einschränkungen. Ihr Datenbankadministrator ist dafür verantwortlich, diese Pläne zu erstellen und auszuführen.

## PostgreSQL {#postgresql}

### Erkennen großer Tabellen {#detecting-large-tables}

1. Sie können die folgende Ansicht zu Ihrer Datenbank hinzufügen:

   ```
   create or replace view uvSpace
    as
    SELECT c1.relname AS tablename, c2.relname AS indexname, c2.relpages * 8  / 1024 AS size_mbytes, c2.relfilenode AS filename, cast(0 AS bigint) AS row_count
    FROM pg_class c1, pg_class c2, pg_index i
    WHERE c1.oid = i.indrelid AND i.indexrelid = c2.oid
    UNION
    SELECT pg_class.relname AS tablename, NULL::"unknown" AS indexname, pg_class.relpages * 8  /1024  AS size_mbytes, pg_class.relfilenode AS filename, cast(pg_class.reltuples as bigint) AS row_count
    FROM pg_class
    WHERE pg_class.relkind = 'r'::"char"
    ORDER BY 3 DESC, 1, 2 DESC;
   ```

1. Sie können diese Abfrage ausführen, um große Tabellen und Indizes zu erkennen:

   ```
   SELECT * FROM uvSpace;
   ```

   Alternativ können Sie beispielsweise diese Abfrage ausführen, um alle Indexgrößen gemeinsam anzuzeigen:

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

>[!IMPORTANT]
>
>Adobe empfiehlt dringend, VACUUM FULL nicht auf von Campaign Adobe gehosteten Datenbank-Setups auszuführen. Die empfohlenen Wartungsarbeiten dienen nur als Anleitung für On-Premise-Installationen. Verwenden Sie für benutzerdefinierte Tabellenimplementierungen und Schemata VACUUM FULL auf eigene Gefahr, da VACUUM - ohne Überwachung - ausschließlich Tabellen sperren kann, die zu angehaltenen Abfragen führen, und in einigen Fällen die gesamte Datenbank sperren kann.

In PostgreSQL können Sie die folgenden typischen Schlüsselwörter verwenden:

* VAKUUM (VOLL, ANALYSIEREN, AUSFÜHRLICH)

Um den Vorgang VACUUM auszuführen und zu analysieren und zu timen, können Sie diese Syntax verwenden:

```
\timing on
VACUUM (FULL, ANALYZE, VERBOSE) <table>;
```

Es wird dringend empfohlen, die ANALYZE-Anweisung nicht wegzulassen. Andernfalls bleibt die gesaugte Tabelle ohne Statistiken. Der Grund dafür ist, dass eine neue Tabelle erstellt wird und dann die alte gelöscht wird. Als Ergebnis ändert sich die Objekt-ID (OID) der Tabelle, es werden jedoch keine Statistiken berechnet. Folglich treten sofort Leistungsprobleme auf.

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
>* Adobe empfiehlt, mit kleineren Tabellen zu beginnen: Auf diese Weise ist, wenn der Vorgang bei großen Tabellen fehlschlägt (bei denen das Fehlerrisiko am höchsten ist), zumindest ein Teil der Wartung abgeschlossen.
>* Adobe empfiehlt, die für Ihr Datenmodell spezifischen Tabellen hinzuzufügen, die erheblich aktualisiert werden können. Dies kann bei „NmsRecipient **der Fall sein** wenn Sie über große tägliche Datenreplikationsflüsse verfügen.
>* Die VACUUM-Anweisung sperrt die Tabelle, wodurch einige Prozesse angehalten werden, während die Wartung durchgeführt wird.
>* Bei sehr großen Tabellen (typischerweise über 5 GB) kann die VACUUM FULL-Anweisung sehr ineffizient werden und sehr lange dauern. Adobe rät davon ab, sie für die Tabelle **YyyNmsBroadLogXxx** zu verwenden.
>* Dieser Wartungsvorgang kann durch einen Adobe Campaign-Workflow mithilfe einer **[!UICONTROL SQL]**-Aktivität implementiert werden. Stellen Sie sicher, dass Sie die Wartung für eine kurze Zeitspanne ohne Kollision mit dem Backup-Fenster planen.
>

### Datenbank neu erstellen {#rebuilding-a-database}

PostgreSQL bietet keine einfache Möglichkeit, einen Online-Tabellen-Neuaufbau durchzuführen, da die VACUUM FULL-Anweisung die Tabelle sperrt und so die reguläre Produktion verhindert. Dies bedeutet, dass eine Wartung durchgeführt werden muss, wenn die Tabelle nicht verwendet wird. Sie haben folgende Möglichkeiten:

* eine Wartung durchführen, wenn die Adobe Campaign-Plattform angehalten wird,
* Beenden Sie die verschiedenen Adobe Campaign-Unterdienste, die wahrscheinlich in die neu aufgebaute Tabelle schreiben werden (**nlserver stop wfserver instance_name**, um den Workflow-Prozess zu stoppen).

Im Folgenden finden Sie ein Beispiel für die Tabellendefragmentierung mithilfe spezifischer Funktionen zum Generieren der erforderlichen DDL. Mit dem folgenden SQL-Code können Sie zwei neue Funktionen erstellen: **GenRebuildTablePart1** und **GenRebuildTablePart2**, mit denen die erforderliche DDL zum Erstellen einer Tabelle generiert werden kann.

* Mit der ersten Funktion können Sie eine Arbeitstabelle (hier ** _tmp**) erstellen, die eine Kopie der ursprünglichen Tabelle ist.
* Die zweite Funktion löscht dann die ursprüngliche Tabelle und benennt die Arbeitstabelle und ihre Indizes um.
* Die Verwendung von zwei Funktionen anstelle einer bedeutet, dass Sie bei einem Fehler der ersten nicht das Risiko eingehen, die ursprüngliche Tabelle zu löschen.

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

Das folgende Beispiel kann in einem Workflow verwendet werden, um die erforderlichen Tabellen neu zu erstellen, anstatt den Befehl **vacuum/rebuild** zu verwenden:

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

Wenden Sie sich an Ihren Datenbankadministrator, um mehr über die Verfahren zu erfahren, die für Ihre Version von Oracle am besten geeignet sind.

## Microsoft SQL Server {#microsoft-sql-server}

>[!NOTE]
>
>Für Microsoft SQL Server können Sie den Wartungsplan verwenden, der auf ([ Seite) beschrieben ](https://ola.hallengren.com/sql-server-index-and-statistics-maintenance.html).

Das folgende Beispiel betrifft Microsoft SQL Server 2005. Wenn Sie eine andere Version verwenden, wenden Sie sich an Ihren Datenbankadministrator, um mehr über die Wartungsmaßnahmen zu erfahren.

1. Stellen Sie zunächst eine Verbindung zu Microsoft SQL Server Management Studio her und melden Sie sich als Administrator an.
1. Wechseln Sie zum Ordner **[!UICONTROL Verwaltung > Wartungspläne]**, klicken Sie mit der rechten Maustaste darauf und wählen Sie **[!UICONTROL Wartungsplan-Assistent]**.
1. Klicken Sie **[!UICONTROL Weiter]** wenn die erste Seite angezeigt wird.
1. Wählen Sie die Art des Wartungsplans aus, den Sie erstellen möchten (separate Zeitpläne für jede Aufgabe oder einen einzelnen Zeitplan für den gesamten Plan), und klicken Sie dann auf die Schaltfläche **[!UICONTROL Ändern…]**.
1. Wählen Sie im Fenster **[!UICONTROL Eigenschaften der Auftragsplanung]** die gewünschten Ausführungseinstellungen aus, klicken Sie auf **[!UICONTROL OK]** und dann auf **[!UICONTROL Weiter]**.
1. Wählen Sie die Wartungsaufgaben aus, die Sie durchführen möchten, und klicken Sie dann auf **[!UICONTROL Weiter]**.

   >[!NOTE]
   >
   >Es wird empfohlen, mindestens die unten aufgeführten Wartungsaufgaben durchzuführen. Sie können auch die Aufgabe Statistikaktualisierung auswählen, die jedoch bereits vom Datenbankbereinigungs -Workflow ausgeführt wird.

1. Wählen Sie in der Dropdown-Liste die Datenbank aus, für die Sie die Aufgabe **[!UICONTROL Datenbankintegritätsprüfung]** ausführen möchten.
1. Wählen Sie die Datenbank aus und klicken Sie **[!UICONTROL OK]** und dann auf **[!UICONTROL Weiter]**.
1. Konfigurieren Sie die maximale Größe, die Ihrer Datenbank zugewiesen ist, und klicken Sie dann auf **[!UICONTROL Weiter]**.

   >[!NOTE]
   >
   >Wenn die Größe der Datenbank diesen Schwellenwert überschreitet, versucht der Wartungsplan, nicht verwendete Daten zu löschen, um Speicherplatz freizugeben.

1. Index neu organisieren oder neu erstellen:

   * Wenn die Indexfragmentierungsrate zwischen 10 % und 40 % liegt, wird eine Reorganisation empfohlen.

     Wählen Sie aus, welche Datenbanken und Objekte (Tabellen oder Ansichten) Sie neu organisieren möchten, und klicken Sie dann auf **[!UICONTROL Weiter]**.

     >[!NOTE]
     >
     >Je nach Konfiguration können Sie entweder die zuvor ausgewählten Tabellen oder alle Tabellen in Ihrer Datenbank auswählen.

   * Wenn die Indexfragmentierungsrate höher als 40 % ist, wird eine Neuerstellung empfohlen.

     Wählen Sie die Optionen aus, die Sie auf die Aufgabe zur Neuerstellung des Index anwenden möchten, und klicken Sie dann auf **[!UICONTROL Weiter]**.

     >[!NOTE]
     >
     >Der Neuaufbau-Indexprozess ist im Hinblick auf die Prozessornutzung restriktiver und blockiert die Datenbankressourcen. Wählen Sie die Option **[!UICONTROL Index während der Neuindizierung online halten]**, wenn der Index während der Neuindizierung verfügbar sein soll.

1. Wählen Sie die Optionen aus, die Sie im Aktivitätsbericht anzeigen möchten, und klicken Sie dann auf **[!UICONTROL Weiter]**.
1. Überprüfen Sie die Liste der für den Wartungsplan konfigurierten Aufgaben und klicken Sie dann auf **[!UICONTROL Beenden]**.

   Eine Zusammenfassung des Wartungsplans und der Status seiner verschiedenen Schritte wird angezeigt.

1. Klicken Sie nach Abschluss des Wartungsplans auf **[!UICONTROL Schließen]**.
1. Doppelklicken Sie im Microsoft SQL Server-Explorer auf den Ordner **[!UICONTROL Verwaltung >]**&quot;.
1. Wählen Sie den Adobe Campaign-Wartungsplan aus: die verschiedenen Schritte werden in einem Workflow beschrieben.

   Beachten Sie, dass im Ordner **[!UICONTROL SQL Server-Agent > Vorgänge“ ein]** erstellt wurde. Mit diesem Objekt können Sie den Wartungsplan starten. In unserem Beispiel gibt es nur ein -Objekt, da alle Wartungsaufgaben Teil desselben Plans sind.

   >[!IMPORTANT]
   >
   >Damit dieses Objekt ausgeführt werden kann, muss der Microsoft SQL Server-Agent aktiviert sein.

**Konfigurieren einer separaten Datenbank für Arbeitstabellen**

>[!NOTE]
>
>Diese Konfiguration ist optional.

Mit der Option **WdbcOptions_TempDbName** können Sie eine separate Datenbank für Tabellen auf Microsoft SQL Server konfigurieren. Dadurch werden Backups und Replikation optimiert.

Diese Option kann verwendet werden, wenn die Arbeitstabellen (z. B. die während der Ausführung eines Workflows erstellten Tabellen) in einer anderen Datenbank erstellt werden sollen.

Wenn Sie die Option auf „tempdb.dbo.“ setzen, werden die Arbeitstabellen in der standardmäßigen temporären Datenbank von Microsoft SQL Server erstellt. Der Datenbankadministrator muss Schreibzugriff auf die temporäre Datenbank zulassen.

Wenn die Option festgelegt ist, wird sie für alle in Adobe Campaign konfigurierten Microsoft SQL Server-Datenbanken (Hauptdatenbank und externe Konten) verwendet. Beachten Sie, dass Konflikte auftreten können, wenn zwei externe Konten denselben Server gemeinsam nutzen (da tempdb eindeutig ist). Wenn zwei Campaign-Instanzen denselben MSSQL-Server verwenden, kann es auf dieselbe Weise zu Konflikten kommen, wenn sie dieselbe tempdb verwenden.

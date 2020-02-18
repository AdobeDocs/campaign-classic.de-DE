---
title: SQL Data Management
seo-title: SQL Data Management
description: SQL Data Management
seo-description: null
page-status-flag: never-activated
uuid: b6057496-2dd5-4289-96df-98378e4f0ae7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 18d6f5e1-308f-4080-b7c4-ebf836f74842
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7bcf222f41c0e40368644b76197b07f2ded699f0

---


# SQL Data Management{#sql-data-management}

Die Aktivität **SQL Data Management** ermöglicht Ihnen das Schreiben eigener SQL-Abfragen zum Erstellen und Auffüllen von Arbeitstabellen.

## Voraussetzungen {#prerequisites}

Vor der Konfiguration der Aktivität müssen folgende Voraussetzungen gegeben sein:

* Die Aktivität ist nur für Remote-Datenquellen verfügbar. Das **[!UICONTROL FDA]** (Federated Data Access-)Paket muss daher auf Ihrer Instanz installiert sein (siehe [diesen Abschnitt](../../platform/using/about-fda.md)).
* Das Outbound-Schema muss in der Datenbank vorhanden und mit einer FDA-Datenbank verbunden sein (weitere Informationen zu Datenschemata finden Sie in [diesem Abschnitt](../../configuration/using/about-schema-reference.md)).
* Der Operator, der den Workflow ausführt, muss über die **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY (useSqlDmActivity)]** benannte Berechtigung verfügen. For more on named rights, refer to [this section](../../platform/using/access-management.md#named-rights).

## SQL-Data-Management-Aktivität konfigurieren {#configuring-the-sql-data-management-activity}

1. Specify the activity **[!UICONTROL Label]**.
1. Wählen Sie die **[!UICONTROL External account]** zu verwendende Option und wählen Sie dann die mit diesem externen Konto verknüpfte **[!UICONTROL Outbound schema]** aus.

   >[!CAUTION]
   >
   >Das Outbound-Schema ist unveränderlich und kann nicht bearbeitet werden.

1. Fügen Sie das SQL-Skript hinzu.

   >[!CAUTION]
   >
   >Der Codierer des SQL-Skripts ist dafür verantwortlich, dass das SQL-Skript funktioniert und seine Referenzen (Feldnamen etc.) dem Outbound-Schema entsprechen.

   Wenn Sie einen vorhandenen SQL-Code laden möchten, wählen Sie die **[!UICONTROL The SQL script is contained in an entity stored in the database]** Option aus. SQL-Skripten müssen im Menü **[!UICONTROL Administration]** / **[!UICONTROL Configuration]** / **[!UICONTROL SQL scripts]** erstellt und gespeichert werden.

   Andernfalls können Sie Ihr SQL-Skript auch in den dafür vorgesehenen Bereich kopieren.

   ![](assets/sql_datamanagement.png)

   Mithilfe der Aktivität können Sie die folgenden Variablen im Skript verwenden:

   * **activity.tableName**: SQL-Name der ausgehenden Arbeitstabelle.
   * **task.incomingTransitionByName(‘name’).tableName**: SQL-Name der Arbeitstabelle der zu verwendenden eingehenden Transition (die Transition wird durch den Namen identifiziert).

      >[!NOTE]
      >
      >Der Wert (&#39;&#39;) entspricht dem Feld **[!UICONTROL Name]** Name in den Transition-Eigenschaften.

1. Wenn das SQL-Skript bereits Befehle zum Erstellen einer ausgehenden Arbeitstabelle enthält, heben Sie die Auswahl der **[!UICONTROL Automatically create work table]** Option auf. Andernfalls wird eine Arbeitstabelle automatisch erstellt, sobald der Workflow ausgeführt wird.
1. Wählen Sie **[!UICONTROL Ok]** aus, um die Konfiguration der Aktivität zu bestätigen.

Die Aktivität ist jetzt konfiguriert und kann im Workflow ausgeführt werden.

>[!CAUTION]
>
>Nachdem die Aktivität ausgeführt wurde, ist die Anzahl der gezählten Datensätze in der ausgehenden Transition nur als Richtwert zu erachten. Dieser kann je nach Komplexität des SQL-Skripts variieren.
>  
>Wenn die Aktivität erneut gestartet wird, wird das gesamte Skript unabhängig vom Ausführungsstatus von vorn ausgeführt.

## Muster für SQL-Skripts {#sql-script-samples}

>[!NOTE]
>
>Die Skript-Muster in diesem Abschnitt müssen unter PostgreSQL ausgeführt werden.

Mit diesem Skript können Sie eine Arbeitstabelle erstellen und Daten darin einfügen.

```
CREATE UNLOGGED TABLE <%= activity.tableName %> (
  iRecipientId INTEGER DEFAULT 0,
  sFirstName VARCHAR(100),
  sMiddleName VARCHAR(100),
  sLastName VARCHAR(100),
  sEmail VARCHAR(100)
);

INSERT INTO <%= activity.tableName %>
SELECT iRecipientId, sFirstName, sMiddleName, sLastName, sEmail
FROM nmsRecipient
GROUP BY iRecipientId, sFirstName, sMiddleName, sLastName, sEmail;
```

Mit diesem Skript können Sie eine CTAS-Operation ausführen (CREATE TABLE AS SELECT) und einen Arbeitstabellenindex erstellen:

```
CREATE TABLE <%= activity.tableName %>
AS SELECT iRecipientId, sEmail, sFirstName, sLastName, sMiddleName
FROM nmsRecipient
WHERE sEmail IS NOT NULL
GROUP BY iRecipientId, sEmail, sFirstName, sLastName, sMiddleName;

CREATE INDEX ON <%= activity.tableName %> (sEmail);

ANALYZE <%= activity.tableName %> (sEmail);
```

Mit diesem Skript können Sie zwei Arbeitstabellen verbinden:

```
CREATE TABLE <%= activity.tableName %>
AS SELECT i1.sFirstName, i1.sLastName, i2.sEmail
FROM <%= task.incomingTransitionByName('input1').tableName %> i1
JOIN <%= task.incomingTransitionByName('input2').tableName %> i2 ON (i1.id = i2.id)
```


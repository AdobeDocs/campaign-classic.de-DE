---
product: campaign
title: Schema einer vorhandenen Tabelle
description: Schema einer vorhandenen Tabelle
feature: Custom Resources
role: Data Engineer, Developer
exl-id: 964f1027-627c-4f12-91b5-f258e9ba458b
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 9%

---

# Schema einer vorhandenen Tabelle{#schema-of-an-existing-table}

## Übersicht {#overview}

Wenn das Programm auf die Daten einer existierenden Tabelle, einer SQL-Ansicht oder Daten aus einer Remote-Datenbank zugreifen muss, erstellen Sie das Schema in Adobe Campaign mit den folgenden Daten:

* Name der Tabelle: Geben Sie den Namen der Tabelle (mit Alias bei Verwendung einer Datenbankverbindung) mit dem Attribut &quot;sqltable&quot; ein,
* Schemaschlüssel: Referenzieren Sie die Abstimmfelder,
* Indizes: zum Generieren von Abfragen verwendet,
* die Felder und ihre Position in der XML-Struktur: Füllen Sie nur die in der Anwendung verwendeten Felder aus;
* Links: wenn es Verknüpfungen mit anderen Tabellen der Basis gibt.

## Implementierung {#implementation}

Gehen Sie wie folgt vor, um das entsprechende Schema zu erstellen:

1. Bearbeiten Sie den Knoten **[!UICONTROL Administration>Konfiguration > Datenschemata]** des Adobe Campaign-Baums und klicken Sie auf **[!UICONTROL Neu]** .
1. Wählen Sie die Option **[!UICONTROL Zugriff auf Daten aus einer vorhandenen Tabelle oder einer SQL-Ansicht]** aus und klicken Sie auf **[!UICONTROL Weiter]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Wählen Sie die Tabelle oder die vorhandene Ansicht aus:

   ![](assets/s_ncs_configuration_select_table.png)

1. Passen Sie den Inhalt des Schemas an Ihre Anforderungen an.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   Das Schema muss mit dem Attribut view=&quot;true&quot; im Stammelement `<srcSchema>` gefüllt werden, damit kein SQL-Skript zur Tabellenerstellung generiert werden kann.

**Beispiel** :

```
<srcSchema name="recipient" namespace="cus" view="true">
  <element name="recipient" sqltable="dbsrv.recipient">
    <key name="email">
      <keyfield xpath="@email"/>
    </key>   
    <attribute name="email" type="string" length="80" sqlname="email"/>
  </element>
</srcSchema>
```

## Zugriff auf externe Datenbanken {#accessing-an-external-database}

Mit der Option **Federated Data Access - FDA** haben Sie Zugriff auf die in einer externen Datenbank gespeicherten Daten.

Die Konfiguration, die für den Zugriff auf Daten in einer externen Datenbank durchgeführt werden soll, wird auf [dieser Seite](../../installation/using/creating-data-schema.md) beschrieben.

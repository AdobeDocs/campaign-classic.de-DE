---
product: campaign
title: Schema einer vorhandenen Tabelle
description: Schema einer vorhandenen Tabelle
exl-id: 964f1027-627c-4f12-91b5-f258e9ba458b
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 15%

---

# Schema einer vorhandenen Tabelle{#schema-of-an-existing-table}

![](../../assets/v7-only.svg)

## Überblick {#overview}

Wenn das Programm auf die Daten einer existierenden Tabelle, einer SQL-Ansicht oder Daten aus einer Remote-Datenbank zugreifen muss, erstellen Sie das Schema in Adobe Campaign mit den folgenden Daten:

* Name der Tabelle: Geben Sie den Namen der Tabelle mit dem Attribut &quot;sqltable&quot; ein (mit dem Alias bei Verwendung eines Datenbanklinks),
* Schemaschlüssel: auf das/die Abstimmfeld(e) verweisen,
* Indizes: zur Erzeugung von Abfragen verwendet werden,
* Die Felder und ihre Position in der XML-Struktur: nur die im Antrag verwendeten Felder ausfüllen,
* Links: , wenn es Verbindungen mit den anderen Tabellen der Basis gibt.

## Implementierung {#implementation}

Gehen Sie wie folgt vor, um das entsprechende Schema zu erstellen:

1. Bearbeiten Sie den Knoten **[!UICONTROL Administration > Konfiguration > Datenschemata]** in der Adobe Campaign-Struktur und klicken Sie auf **[!UICONTROL Neu]** .
1. Wählen Sie die **[!UICONTROL Auf Daten aus einer vorhandenen Tabelle oder einer SQL-Ansicht zugreifen]** und klicken Sie auf **[!UICONTROL Nächste]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Wählen Sie die Tabelle oder die vorhandene Ansicht aus:

   ![](assets/s_ncs_configuration_select_table.png)

1. Passen Sie den Inhalt des Schemas an Ihre Anforderungen an.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   Das Schema muss mit dem Attribut view=&quot;true&quot; im `<srcSchema>` root -Element, um kein SQL-Skript zur Tabellenerstellung zu generieren.

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

Die **Federated Data Access - FDA** ermöglicht Ihnen Zugriff auf die in einer externen Datenbank gespeicherten Daten.

Die Konfiguration der Schemata für den Zugriff auf Daten in einer externen Datenbank wird im Abschnitt [diese Seite](../../installation/using/creating-data-schema.md).

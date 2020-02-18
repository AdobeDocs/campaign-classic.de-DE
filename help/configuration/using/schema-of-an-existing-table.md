---
title: Schema einer vorhandenen Tabelle
seo-title: Schema einer vorhandenen Tabelle
description: Schema einer vorhandenen Tabelle
seo-description: null
page-status-flag: never-activated
uuid: cb766259-8ed7-40a1-8df7-75a8a3f9986d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 6877d94d-d6e5-4080-a537-ef1bb6e6f8cf
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7bcf222f41c0e40368644b76197b07f2ded699f0

---


# Schema einer vorhandenen Tabelle{#schema-of-an-existing-table}

## Übersicht {#overview}

Wenn die Anwendung auf die Daten einer vorhandenen Tabelle, einer SQL-Ansicht oder Daten aus einer Remote-Datenbank zugreifen muss, erstellen Sie ihr Schema in Adobe Campaign mit den folgenden Daten:

* Name der Tabelle: Geben Sie den Namen der Tabelle (mit ihrem Alias bei Verwendung eines Datenbanklinks) mit dem Attribut &quot;sqltable&quot;ein,
* Schemaschlüssel: auf das/die Abgleichfeld/die Abgleichfelder verweisen,
* Indizes: zum Generieren von Abfragen verwendet werden,
* Die Felder und ihr Speicherort in der XML-Struktur: nur die im Antrag verwendeten Felder ausfüllen,
* Links: , wenn es Verbindungen zu den anderen Tabellen der Basis gibt.

## Umsetzung {#implementation}

Um das entsprechende Schema zu erstellen, wenden Sie die folgenden Schritte an:

1. Bearbeiten Sie den **[!UICONTROL Administration>Configuration>Data schemas]** Knoten der Adobe Campaign-Struktur und klicken Sie auf **[!UICONTROL New]** .
1. Wählen Sie die **[!UICONTROL Access data from an existing table or an SQL view]** Option aus und klicken Sie auf **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Wählen Sie die Tabelle oder die vorhandene Ansicht aus:

   ![](assets/s_ncs_configuration_select_table.png)

1. Passen Sie den Schemainhalt an Ihre Anforderungen an.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   Das Schema muss mit dem Attribut view=&quot;true&quot; im Stammelement gefüllt werden, damit kein SQL-Skript zur Tabellenerstellung generiert wird. `<srcSchema>`

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

Die Konfiguration für die Schemata zum Zugriff auf Daten in einer externen Datenbank ist auf [dieser Seite](../../platform/using/creating-data-schema.md)ausführlich beschrieben.

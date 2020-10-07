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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 11%

---


# Schema einer vorhandenen Tabelle{#schema-of-an-existing-table}

## Übersicht {#overview}

Wenn die Anwendung auf die Daten einer vorhandenen Tabelle, einer SQL-Ansicht oder Daten aus einer Remote-Datenbank zugreifen muss, erstellen Sie das Schema in Adobe Campaign mit den folgenden Daten:

* Name der Tabelle: Geben Sie den Namen der Tabelle (mit ihrem Alias bei Verwendung eines Datenbanklinks) mit dem Attribut &quot;sqltable&quot;ein,
* schema-Schlüssel: auf das/die Abgleichfeld(e) verweisen,
* Indizes: zur Erzeugung von Abfragen verwendet werden,
* Die Felder und ihr Speicherort in der XML-Struktur: nur die im Antrag verwendeten Felder ausfüllen,
* Links: , wenn es Verbindungen zu den anderen Tabellen der Basis gibt.

## Implementierung{#implementation}

Um das entsprechende Schema zu erstellen, führen Sie die folgenden Schritte aus:

1. Bearbeiten Sie den Knoten **[!UICONTROL Administration>Configuration>Data Schemas]** im Adobe Campaign und klicken Sie auf **[!UICONTROL New]** .
1. Wählen Sie die Option **[!UICONTROL Zugriff auf Daten aus einer vorhandenen Tabelle oder einer SQL-Ansicht]** und klicken Sie auf **[!UICONTROL Weiter]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Wählen Sie die Tabelle oder die vorhandene Ansicht aus:

   ![](assets/s_ncs_configuration_select_table.png)

1. Passen Sie die Schema-Inhalte an Ihre Anforderungen an.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   Das Schema muss mit dem Attribut &quot;Ansicht=&quot;true&quot;im Stammelement gefüllt werden, damit kein SQL-Skript zur Tabellenerstellung generiert wird. `<srcSchema>`

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

Die Konfiguration, die auf den Schemas für den Zugriff auf Daten in einer externen Datenbank durchgeführt werden soll, ist auf [dieser Seite](../../platform/using/creating-data-schema.md)ausführlich beschrieben.

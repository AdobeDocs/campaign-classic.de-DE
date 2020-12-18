---
solution: Campaign Classic
product: campaign
title: Schema einer vorhandenen Tabelle
description: Schema einer vorhandenen Tabelle
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 9%

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

1. Bearbeiten Sie den Knoten **[!UICONTROL Administration>Configuration>Data Schemas]** der Adobe Campaign-Struktur und klicken Sie auf **[!UICONTROL Neu]** .
1. Wählen Sie die Option **[!UICONTROL Daten aus einer vorhandenen Tabelle oder einer SQL-Ansicht]** aus und klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Wählen Sie die Tabelle oder die vorhandene Ansicht aus:

   ![](assets/s_ncs_configuration_select_table.png)

1. Passen Sie die Schema-Inhalte an Ihre Anforderungen an.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   Das Schema muss mit dem Attribut &quot;Ansicht=&quot;true&quot;im Stammelement `<srcSchema>` gefüllt werden, damit kein SQL-Skript zur Tabellenerstellung generiert wird.

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

Mit der Option **Federated Data Access - FDA** können Sie auf die in einer externen Datenbank gespeicherten Daten zugreifen.

Die Konfiguration, die auf den Schemas für den Zugriff auf Daten in einer externen Datenbank durchgeführt werden soll, ist in [dieser Seite](../../installation/using/creating-data-schema.md) beschrieben.

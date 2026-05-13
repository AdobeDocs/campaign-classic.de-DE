---
product: campaign
title: Schema einer vorhandenen Tabelle
description: Schema einer vorhandenen Tabelle
feature: Custom Resources
role: Developer
exl-id: 964f1027-627c-4f12-91b5-f258e9ba458b
TQID: https://experienceleague.adobe.com/Vi1DhgY8tGIhq1TtMOGKeGMrqFgGecfJQHrKyFXTSgg
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2: id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 232
ht-degree: 9%

---

# Schema einer vorhandenen Tabelle{#schema-of-an-existing-table}

## Übersicht {#overview}

Wenn die Anwendung auf die Daten einer bestehenden Tabelle, einer SQL-Ansicht oder auf Daten aus einer Remote-Datenbank zugreifen muss, erstellen Sie ihr Schema in Adobe Campaign mit den folgenden Daten:

* Tabellenname: Geben Sie den Namen der Tabelle (mit ihrem Alias, wenn ein DbLink verwendet wird) mit dem Attribut „sqltable“ ein.
* Schemaschlüssel: Referenzieren der Abstimmfelder,
* -Indizes: zum Generieren von Abfragen,
* Die Felder und ihre Position in der XML-Struktur: Ausfüllen der im Programm verwendeten Felder,
* Relationen: Wenn Joins mit den anderen Tabellen der Basis vorhanden sind.

## Implementierung {#implementation}

Gehen Sie wie folgt vor, um das entsprechende Schema zu erstellen:

1. Bearbeiten Sie den Knoten **[!UICONTROL Administration>Konfiguration>]** Datenschemata der Adobe Campaign-Struktur und klicken Sie auf **[!UICONTROL Neu]** .
1. Wählen Sie die Option **[!UICONTROL Daten aus einer vorhandenen Tabelle oder einer SQL-Ansicht aufrufen]** und klicken Sie auf **[!UICONTROL Weiter]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Tabelle oder vorhandene Ansicht auswählen:

   ![](assets/s_ncs_configuration_select_table.png)

1. Passen Sie den Schemainhalt an Ihre Anforderungen an.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   Das Schema muss mit dem Attribut view=„true“ im `<srcSchema>` Stammelement gefüllt werden, damit kein SQL-Script zur Tabellenerstellung generiert wird.

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

Die **Federated Data Access - FDA**-Option bietet Ihnen Zugriff auf die in einer externen Datenbank gespeicherten Daten.

Die Konfiguration für die Schemata zum Zugriff auf Daten in einer externen Datenbank wird auf [ Seite beschrieben](../../installation/using/creating-data-schema.md).

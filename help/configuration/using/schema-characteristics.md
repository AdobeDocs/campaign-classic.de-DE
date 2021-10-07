---
product: campaign
title: Schemamerkmale
description: Schemamerkmale
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 099161b4-b4cb-433c-aed6-71157269a536
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 2%

---

# Schemamerkmale{#schema-characteristics}

![](../../assets/v7-only.svg)

Die Merkmale eines Schemas, das auf eine vorhandene Tabelle verweist, lauten wie folgt:

* Adobe Campaign darf SQL-Objekte nicht relativ zu vorhandenen Tabellen ändern;
* Die Namen der Tabellen und Spalten müssen explizit angegeben werden.
* Indizes müssen deklariert werden.

>[!IMPORTANT]
>
>Löschen Sie keine Felder in der Standard-Empfängertabelle, auch wenn sie nutzlos sind. Dies kann zu Verhaltensfehlern in der Adobe Campaign-Datenbank führen.

## Das Ansichtsattribut {#the-view-attribute}

Quellschemata akzeptieren das Attribut **view** für das Stammelement **srcSchema** . Sie muss verwendet werden, wenn Adobe Campaign in benutzerdefinierten Tabellen bearbeitet wird. Das Attribut **view=&quot;true&quot;** weist den Datenbankstruktur-Aktualisierungsassistenten an, dieses Schema zu ignorieren. Die Anwendung ist daher nicht berechtigt, die Tabelle, ihre Spalten und Indizes mit dem entsprechenden Schema zu synchronisieren.

Wenn dieses Attribut auf **true** gesetzt ist, wird das Schema nur zum Generieren von SQL-Abfragen für den Zugriff auf die Daten dieser Tabelle verwendet.

## Namen von Tabellen und Spalten {#names-of-tables-and-columns}

Wenn Tabellen vom Tabellenaktualisierungs-Assistenten erstellt werden, werden die Namen der Tabellen und Spalten automatisch anhand der Namen der jeweiligen Schemas und Attribute generiert. Es ist jedoch möglich, die Verwendung der SQL-Namen zu erzwingen, indem die folgenden Attribute eingegeben werden:

* **** sqltableinnerhalb des Hauptelements des Schemas, um die Tabelle anzugeben,
* **** sqlname in jedem Attribut, um die Spalten anzugeben.

**Beispiel**:

```
<element label="Individual" name="individual" sqltable="individual">
    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key> 
    <attribute name="id" type="long" length="32" />
    <attribute name="lastName" type="string" length="100" sqlname="Last_Name"/>
    <attribute name="firstName" type="string" length="100" sqlname="First_Name"/>
    <attribute name="email" type="string" length="100"/>
    <attribute name="mobile" type="string" length="100"/>
</element>
```

Wenn in diesem Beispiel die Namen der Tabellen und Spalten nicht explizit angegeben wurden, hätte die Anwendung **CusIndividual** für die Tabelle, **lastName** und **firstName** für die Spalten verwendet.

In einem Schema ist es möglich, nur einen Teil der Spalten einer vorhandenen Tabelle auszufüllen. Auf nicht ausgefüllte Spalten kann nicht vom Benutzer zugegriffen werden.

## Indexierte Felder {#indexed-fields}

Beim Sortieren der Datensätze einer Liste in der Clientkonsole wird eine bessere Leistung erzielt, indem eine Sortierung nach indizierten Feldern vorgenommen wird. Wenn Sie einen Index in einem Schema deklarieren, zeigt die Konsole die indizierten Felder mit einer roten Linie unter dem Sortierungspfeil links neben der Spaltenbeschriftung an, wie unten dargestellt:

![](assets/s_ncs_integration_mapping_index.png)

In einem Schema wird ein Index wie folgt definiert:

```
<dbindex name="name_of_index" unique="true/false"
  <keyfield xpath="xpath_1st_field"/
  <keyfield xpath="xpath_2nd_field"/
  ...
</dbindex
```

Daher ist es wichtig, vorhandene Indizes der benutzerdefinierten Tabelle im entsprechenden Schema zu deklarieren.

Ein Index wird implizit für jede Schlüssel- und Link-Deklaration des Quellschemas deklariert. Die Indexdeklaration kann durch Angabe des Attributs **noDbIndex=&quot;true&quot;** verhindert werden:

**Beispiel**:

```
<key internal="true" name="customer" noDbIndex="true">
  <keyfield xpath="@customerId"/>
</key>
```

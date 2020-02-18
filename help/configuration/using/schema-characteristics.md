---
title: Schemamerkmale
seo-title: Schemamerkmale
description: Schemamerkmale
seo-description: null
page-status-flag: never-activated
uuid: ca8eb7af-ef22-403a-8f04-ece5dc903174
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 441e80e1-0559-41fd-83e8-afdf94279e75
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Schemamerkmale{#schema-characteristics}

Die Eigenschaften eines Schemas, das auf eine vorhandene Tabelle verweist, sind wie folgt:

* Adobe Campaign darf SQL-Objekte in Bezug auf vorhandene Tabellen nicht ändern.
* Die Namen der Tabellen und Spalten müssen explizit angegeben werden.
* Indizes müssen deklariert werden.

>[!IMPORTANT]
>
>Löschen Sie keine Felder in der Standard-Empfängertabelle, auch wenn sie nutzlos sind. Dies kann zu Verhaltensfehlern in der Adobe Campaign-Datenbank führen.

## Das view-Attribut {#the-view-attribute}

Quellschemata akzeptieren das **Ansichtsattribut** für das **srcSchema** -Stammelement. Es muss verwendet werden, wenn Adobe Campaign in benutzerdefinierten Tabellen manipuliert wird. Das Attribut **view=&quot;true&quot;** weist den Assistenten zum Aktualisieren der Datenbankstruktur an, dieses Schema zu ignorieren. Die Anwendung ist daher nicht berechtigt, die Tabelle, ihre Spalten und Indizes mit dem entsprechenden Schema zu synchronisieren.

Wenn dieses Attribut auf **true** gesetzt ist, wird das Schema nur zum Generieren von SQL-Abfragen für den Zugriff auf die Daten dieser Tabelle verwendet.

## Namen von Tabellen und Spalten {#names-of-tables-and-columns}

Wenn Tabellen vom Tabellenaktualisierungsassistenten erstellt werden, werden die Namen der Tabellen und Spalten automatisch anhand der Namen der jeweiligen Schemata und Attribute generiert. Es ist jedoch möglich, die Verwendung der SQL-Namen durch Eingabe der folgenden Attribute zu erzwingen:

* **sqltable** innerhalb des Hauptelements des Schemas, um die Tabelle anzugeben,
* **sqlname** innerhalb jedes Attributs, um die Spalten anzugeben.

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

In einem Schema ist es möglich, nur einen Teil der Spalten einer vorhandenen Tabelle auszufüllen. Auf nicht ausgefüllte Spalten kann nicht zugegriffen werden.

## Indexierte Felder {#indexed-fields}

Beim Sortieren der Datensätze einer Liste aus der Client-Konsole wird eine bessere Leistung durch Sortieren nach indizierten Feldern erzielt. Wenn Sie einen Index in einem Schema deklarieren, zeigt die Konsole die indizierten Felder mit einer roten Linie unter dem Sortierungspfeil links neben der Spaltenbeschriftung an, wie unten dargestellt:

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

Für jede Schlüssel- und Linkdeklaration des Quellschemas wird implizit ein Index deklariert. Die Indexdeklaration kann durch Angabe des Attributs **noDbIndex=&quot;true&quot;** verhindert werden:

**Beispiel**:

```
<key internal="true" name="customer" noDbIndex="true">
  <keyfield xpath="@customerId"/>
</key>
```


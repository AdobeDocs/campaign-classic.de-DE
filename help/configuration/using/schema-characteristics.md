---
solution: Campaign Classic
product: campaign
title: Schemamerkmale
description: Schemamerkmale
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 2%

---


# Schemamerkmale{#schema-characteristics}

Die Eigenschaften eines Schemas, das auf eine vorhandene Tabelle verweist, sind wie folgt:

* Adobe Campaign darf SQL-Objekte nicht in Bezug auf vorhandene Tabellen ändern.
* Die Namen der Tabellen und Spalten müssen explizit angegeben werden.
* Indizes müssen deklariert werden.

>[!IMPORTANT]
>
>Löschen Sie keine Empfänger in der Standardtabelle, auch wenn sie nutzlos sind. Dies kann zu Verhaltensfehlern in der Adobe Campaign-Datenbank führen.

## Das Attribut &quot;Ansicht&quot; {#the-view-attribute}

Source-Schema akzeptieren das **Ansicht** -Attribut für das **srcSchema** -Stammelement. Es muss verwendet werden, wenn Adobe Campaign in benutzerdefinierten Tabellen manipuliert wird. Das **Ansicht=&quot;true&quot;** -Attribut weist den Updateassistenten für die Datenbankstruktur an, dieses Schema zu ignorieren. Daher ist es dem Antrag untersagt, die Tabelle, ihre Spalten und Indizes mit dem entsprechenden Schema zu synchronisieren.

Wenn dieses Attribut auf **true** gesetzt ist, wird das Schema nur zum Generieren von SQL-Abfragen verwendet, um auf die Daten dieser Tabelle zuzugreifen.

## Namen von Tabellen und Spalten {#names-of-tables-and-columns}

Wenn Tabellen vom Tabellenaktualisierungsassistenten erstellt werden, werden die Tabellen- und Spaltennamen automatisch anhand der jeweiligen Schema- und Attributnamen generiert. Es ist jedoch möglich, die Verwendung der SQL-Namen durch Eingabe der folgenden Attribute zu erzwingen:

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

In einem Schema ist es möglich, nur einen Teil der Spalten einer vorhandenen Tabelle auszufüllen. Nicht ausgefüllte Spalten können nicht vom Benutzer aufgerufen werden.

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

Für jede Schlüssel- und Linkdeklaration des Quell-Schemas wird implizit ein Index deklariert. Die Indexdeklaration kann durch Angabe des Attributs **noDbIndex=&quot;true&quot;** verhindert werden:

**Beispiel**:

```
<key internal="true" name="customer" noDbIndex="true">
  <keyfield xpath="@customerId"/>
</key>
```


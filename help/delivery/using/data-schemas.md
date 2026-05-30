---
product: campaign
title: Verwenden von Datenschemata in Campaign
description: Erfahren Sie, wie Sie in Campaign Datenschemata verwenden
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Data Model
role: User, Developer
exl-id: 3e28bfee-0321-40f4-9ef6-1bdb5b25041b
TQID: https://experienceleague.adobe.com/o90zid7-rdTsQVYd-PZZEWFhrBLiK-Yo7KhAHmzv2is
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 566
ht-degree: 87%

---

# Verwenden von Datenschemata in Campaign{#data-schemas}

Im Folgenden werden einige Grundprinzipien bezüglich der Datenschemata in Adobe Campaign dargestellt.

Erstellung und Konfiguration von Datenschemata in Adobe Campaign werden in [diesem Abschnitt](../../configuration/using/about-schema-edition.md) beschrieben.

## Schemastruktur {#schema-structure}

Das XML-Dokument eines Datenschemas muss die Wurzel **`<srcschema>`** mit den Attributen **name** und **namespace** zur Angabe des Schemanamens und des Namensraums enthalten.

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

Der Einstiegspunkt für das Schema ist sein Hauptelement. Sie ist einfach zu identifizieren, da sie denselben Namen wie das Schema hat und dem Stammelement untergeordnet sein sollte. Die Beschreibung des Inhalts beginnt mit diesem Element.

In einem Content-Management-Schema entspricht das Hauptelement folgendem Muster:

```
<element name="book" template="ncm:content" xmlChildren="true">
```

Das Attribut **template** ermöglicht die Erweiterung des Schemas um die Eigenschaften, die in allen Inhaltsdefinitionen verwendet werden, wie z. B. Name, Erstellungsdatum, Autor, zugeordneter String usw.

Diese Eigenschaften werden im Schema **ncm:content** beschrieben.

>[!NOTE]
>
>Das Attribut **xmlChildren** zeigt, dass die ausgehend vom Hauptelement angegebene Datenstruktur in einem XML-Dokument der Inhaltsinstanz gespeichert ist.

>[!CAUTION]
>
>Beim Anlegen eines neuen Schemas oder bei einer Schema-Erweiterung müssen Sie für das gesamte Schema den gleichen Wert für die Primärschlüsselfolge (@pkSequence) beibehalten.

## Datentypen {#data-types}

Beispiel eines mit Datentypen komplettierten Content-Management-Schemas:

```
<srcSchema name="book" namespace="cus">
  <element name="book" template="ncm:content" xmlChildren="true">
    <attribute name="title" type="string"/>
    <attribute name="date" type="date"/>
    <attribute name="language" type="string"/>
    <element name="chapter">
      <attribute name="name" type="string"/>
      <element name="page" type="string>
        <attribute name="number" type="short"/>
      </element>
    </element>
  </element>
</element>
```

## Eigenschaften {#properties}

Verschiedene Eigenschaften können die Elemente (**`<element>`**) und (**`<attribute>`**) des Datenschemas ergänzen.

Im Content-Management werden vor allem folgende Eigenschaften verwendet:

* **label**: kurze Beschreibung,
* **desc**: lange Beschreibung,
* **default**: Ausdruck, der bei der Inhaltserstellung einen Standardwert ausgibt,
* **userEnum**: freie Aufzählung, die die im Feld eingegebenen Werte speichert und anzeigt,
* **enum**: Aufzählung mit einer festgeschriebenen Werteliste.

Beispiel des um diese Eigenschaften ergänzten Schemas:

```
<srcSchema name="book" namespace="cus">
  <enumeration name="language" basetype="string" default="eng">    
    <value name="fra" label="French"/>    
    <value name="eng" label="English"/>   
  </enumeration>

  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <attribute name="title" type="string" label="Title" default="'New book'"/>
    <attribute name="date" type="date" default="GetDate()"/>
    <attribute name="language" type="string" label="Language" enum="language"/>
    <element name="chapter" label="Chapter">
      <attribute name="name" type="string" label="Name" desc="Name of chapter"/>
      <element name="page" type="string" label="Page" desc="Page content">
        <attribute name="number" type="short" label="Number" default="CounterValue('numPage')"/>
      </element>
    </element>
  </element>
</srcSchema>
```

## Sammlungselemente {#collection-elements}

Eine Sammlung ist eine Liste von Elementen mit gleichem Namen und auf gleicher Hierarchieebene.

In unserem Beispiel sind die Elemente **`<chapter>`** und **`<page>`** Sammlungselemente. Das Attribut **unbound** muss daher der Definition folgender Elemente hinzugefügt werden:

```
<element name="chapter" label="Chapter" unbound="true" ordered="true">
```

```
<element name="page" type="string" label="Page" desc="Content of page" unbound="true">
```

>[!NOTE]
>
>Das Attribut **ordered=&quot;true&quot;** ermöglicht die Sortierung der enthaltenen Sammlungselemente.

## Referenzierung von Elementen {#element-referencing}

Eine Referenzierung von Elementen wird in Inhaltsschemata häufig verwendet. Sie erlaubt es, die Definition eines **`<element>`**-Elements so zu aufzugliedern, dass andere Elemente mit derselben Struktur darauf verweisen können.

Das Attribut **ref** des zu referenzierenden Elements muss mit dem Pfad (XPath) des Referenz-Elements angegeben werden.

**Beispiel**: Hinzufügung eines Segments **Anhang**, welches die gleiche Struktur wie das Element **`<chapter>`** im Beispielschema aufweist.

```
<srcSchema name="book" namespace="cus">
  <element name="section">
    <attribute name="name" type="string" label="Name" desc="Name"/>
    <element name="page" type="string" label="Page" desc="Content of page">
      <attribute name="number" type="short" label="Number" default="CounterValue('numPage')"/>
    </element>

  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <attribute name="title" type="string" label="Title" default="'New book'"/>
    <attribute name="date" type="date" default="GetDate()"/>
    <attribute name="language" type="string" label="Language" enum="language"/>
    <element name="chapter" label="Chapter" ref="section"/>
    <element name="appendix" label="Appendix" ref="section"/>
  </element>
</srcSchema>
```

Die Kapitelstruktur wird in das Element mit dem Namen „section“ außerhalb des Hauptelements verschoben. Kapitel und Abschnitt verweisen auf das Element „section“.

## Compute-String {#compute-string}

Ein **Compute string** ist ein XPath-Ausdruck, der dazu verwendet wird, einen eine Inhaltsinstanz repräsentierenden String zu erzeugen.

Beispiel des zuvor verwendeten Schemas, ergänzt um einen **Compute string**:

```
<srcSchema name="book" namespace="cus">
  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <compute-string expr="@name"/>
    ...
  </element>
</srcSchema>
```

## Schemabearbeitung {#editing-schemas}

Der XML-Inhalt des Quellschemas wird im Editor erfasst:

![](assets/d_ncs_integration_schema_edition.png)

Das Speichern des Quellschemas löst automatisch die Erzeugung des erweiterten Schemas aus.

>[!NOTE]
>
>Im Feld **Name** kann der Schemaschlüssel - bestehend aus Name und Namensraum - erfasst werden. Die Attribute **name** und **namespace** der Wurzel werden automatisch im XML-Editor des Schemas aktualisiert.

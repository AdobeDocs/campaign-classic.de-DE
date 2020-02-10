---
title: Datenschemata
seo-title: Datenschemata
description: Datenschemata
seo-description: null
page-status-flag: never-activated
uuid: 3327a38c-e44d-4581-a67b-bb60c1604a5f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: aeaa9475-3715-40a4-8864-29d126883272
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Datenschemata{#data-schemas}

Im Folgenden werden einige Grundprinzipien bezüglich der Datenschemata in Adobe Campaign dargestellt.

Erstellung und Konfiguration von Datenschemata in Adobe Campaign werden in [diesem Abschnitt](../../configuration/using/about-schema-edition.md) beschrieben.

## Schemastruktur {#schema-structure}

The XML document of a data schema must contain the **`<srcschema>`** root element with the **name** and **namespace** attributes to populate the schema name and its namespace.

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

Der Startpunkt des Schemas ist sein Hauptelement. Es ist leicht identifizierbar, da sein Name mit dem des Schemas identisch ist. Außerdem handelt es sich um das direkte Kindelement der Wurzel. Ausgehend von diesem Element beginnt die Inhaltsbeschreibung.

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

Various properties can be used to enrich the **`<element>`** and **`<attribute>`** elements of the data schema.

Im Content Management werden vor allem folgende Eigenschaften verwendet:

* **label**: kurze Beschreibung,
* **desc**: lange Beschreibung,
* **default**: Ausdruck, der bei der Inhaltserstellung einen Standardwert ausgibt,
* **userEnum**: freie Auflistung, die die im Feld eingegebenen Werte speichert und anzeigt,
* **enum**: Auflistung mit einer festgeschriebenen Werteliste.

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

## Kollektionselemente {#collection-elements}

Eine Kollektion ist eine Liste von Elementen mit gleichem Namen und auf gleicher Hierarchieebene.

In unserem Beispiel sind die Elemente **`<chapter>`** und **`<page>`** Elemente Sammlungselemente. Das **Attribut &quot;ungebunden** &quot;muss daher der Definition folgender Elemente hinzugefügt werden:

```
<element name="chapter" label="Chapter" unbound="true" ordered="true">
```

```
<element name="page" type="string" label="Page" desc="Content of page" unbound="true">
```

>[!NOTE]
>
>Das Attribut **ordered=&quot;true&quot;** ermöglicht die Sortierung der enthaltenen Kollektionselemente.

## Referenzierung von Elementen {#element-referencing}

Elementverweise werden in Inhaltsschemata sehr häufig verwendet. Es ermöglicht Ihnen, die Definition eines **`<element>`** Elements zu factorisieren, sodass auf andere Elemente mit derselben Struktur verwiesen werden kann.

Das Attribut **ref** des zu referenzierenden Elements muss mit dem Pfad (XPath) des Referenz-Elements angegeben werden.

**Beispiel**: Hinzufügen eines **Anhangs** -Abschnitts mit derselben Struktur wie das **`<chapter>`** -Element unseres Beispielschemas.

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

Die Struktur des Elements &quot;Kapitel&quot; wird in das Element mit Namen &quot;Segment&quot; ausgegliedert, welches außerhalb des Hauptelements liegt. Die Elemente &quot;Kapitel&quot; und &quot;Anhang&quot; referenzieren beide das Element &quot;Segment&quot;.

## Compute string {#compute-string}

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

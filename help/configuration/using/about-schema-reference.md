---
product: campaign
title: Erste Schritte mit Schemata in Adobe Campaign
description: Erfahren Sie, wie Sie mit Schemata arbeiten und das konzeptionelle Datenmodell der Adobe Campaign-Datenbank erweitern
feature: Schema Extension
role: Data Engineer, Developer
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
source-git-commit: 44c40bbd8bff16cbe220d3af3a7bb2847762f58b
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 49%

---

# Erste Schritte mit Schemata {#about-schema-reference}

## Was ist ein Schema {#what-is-a-schema}

In diesem Kapitel wird beschrieben, wie Sie Erweiterungsschemata konfigurieren können, um das konzeptionelle Datenmodell der Adobe Campaign-Datenbank zu erweitern.

Genauere Informationen zu den integrierten Campaign-Tabellen und ihrer Interaktion finden Sie im Datenmodell [Campaign Classic](about-data-model.md).

In Adobe Campaign wird die physische und logische Struktur der im Programm übertragenen Daten in XML beschrieben. Ein **Schema** ist ein XML-Dokument, das mit einer Datenbanktabelle verknüpft ist. Es definiert die Datenstruktur und beschreibt die SQL-Definition der Tabelle:

* Der Name der Tabelle
* Felder
* Indizes
* Relationen zu anderen Tabellen

Außerdem wird die XML-Struktur zum Speichern von Daten beschrieben:

* Elemente und Attribute
* Hierarchie der Elemente
* Element- und Attributtypen
* Standardwerte
* Titel, Beschreibungen und andere Eigenschaften.

Mit Schemata können Sie eine Entität in der Datenbank definieren. Es gibt ein Schema für jede Entität.

Die folgende Abbildung zeigt den Speicherort von Schemas im Adobe Campaign-Datensystem:

![](assets/reference_schema_intro.png)

## Syntax von Schemata {#syntax-of-schemas}

Das Stammelement des Schemas ist **`<srcschema>`**. Es enthält die Unterelemente **`<element>`** und **`<attribute>`**.

Das erste **`<element>`**-Unterelement fällt mit dem Stammelement der Entität zusammen.

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">  
    <attribute name="lastName"/>
    <attribute name="email"/>
    <element name="location">
      <attribute name="city"/>
   </element>
  </element>
</srcSchema>
```

>[!NOTE]
>
>Das Stammelement der Entität hat denselben Namen wie das Schema.

![](assets/s_ncs_configuration_schema_and_entity.png)

Die **`<element>`**-Tags definieren die Namen von Entitätselementen. **`<attribute>`**-Tags des Schemas definieren die Namen der Attribute in den **`<element>`**-Tags, mit denen sie verknüpft wurden.

## Identifizierung eines Schemas {#identification-of-a-schema}

Ein Schema wird anhand seines Namens und seines Namespace identifiziert.

Mit einem Namespace können Sie eine Reihe von Schemata nach Interessensgebieten gruppieren. Beispielsweise wird der Namespace **cus** für die kundenspezifische Konfiguration (**customers**) verwendet.

Der Identifizierungsschlüssel eines Schemas ist eine Zeichenfolge, die den Namespace und den Namen enthält, getrennt durch einen Doppelpunkt (z. B. **cus:recipient**.

>[!IMPORTANT]
>
>* Der Name des Namespace muss kurz sein und darf nur autorisierte Zeichen gemäß den XML-Benennungsregeln enthalten.
>
>* Kennungen dürfen nicht mit numerischen Zeichen beginnen.
>
>* Die folgenden Namespaces sind für Beschreibungen der Systementitäten reserviert, die für den Betrieb der Adobe Campaign-Anwendung erforderlich sind, und dürfen nicht verwendet werden: **xtk**, **nl**, **nms**, **ncm**, **temp**, **ncl**, **crm**, **xxl**.
>

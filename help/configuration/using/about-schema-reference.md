---
title: Schemaverweis in Adobe Campaign Classic
description: Erfahren Sie, wie Sie Erweiterungsschemata konfigurieren, um das konzeptionelle Datenmodell der Adobe Campaign Classic-Datenbank zu erweitern.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5130802f3723311bcd09e21fc405d298923dd20e

---


# Informationen zur Schemareferenz{#about-schema-reference}

In diesem Kapitel wird beschrieben, wie Sie Erweiterungsschemata konfigurieren, um das konzeptionelle Datenmodell der Adobe Campaign-Datenbank zu erweitern.

Ein besseres Verständnis der integrierten Kampagnentabellen und ihrer Interaktion finden Sie im Datenmodell [Campaign Classic](https://helpx.adobe.com/campaign/kb/acc-datamodel.html).

Die physische und logische Struktur der in der Anwendung übertragenen Daten wird in XML beschrieben. Es folgt einer für Adobe Campaign spezifischen Grammatik, einem so genannten **Schema**.

Ein Schema ist ein mit einer Datenbanktabelle verknüpftes XML-Dokument. Er definiert die Datenstruktur und beschreibt die SQL-Definition der Tabelle:

* Der Name der Tabelle
* Felder
* Indexe
* Links zu anderen Tabellen

Außerdem wird die XML-Struktur zum Speichern von Daten beschrieben:

* Elemente und Attribute
* Hierarchie der Elemente
* Element- und Attributtypen
* Standardwerte
* Beschriftungen, Beschreibungen und andere Eigenschaften.

Mithilfe von Schemas können Sie eine Entität in der Datenbank definieren. Es gibt ein Schema für jede Entität.

Die folgende Abbildung zeigt den Speicherort von Schemas im Adobe Campaign-Datensystem:

![](assets/reference_schema_intro.png)

## Syntax von Schemas {#syntax-of-schemas}

Das Stammelement des Schemas ist **`<srcschema>`**. Es enthält die **- **`<element>`** und **`<attribute>`** -Unterelemente.

Das erste **`<element>`** Unterelement fällt mit der Stamm-Node der Entität zusammen.

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

Die **`<element>`** -Tags definieren die Namen der Entitätselemente. **`<attribute>`** -Tags des Schemas definieren die Namen der Attribute in den **`<element>`** Tags, mit denen sie verknüpft wurden.

## Identifizierung eines Schemas {#identification-of-a-schema}

Ein Datenschema wird durch seinen Namen und seinen Namespace identifiziert.

Mit einem Namespace können Sie eine Gruppe von Schemata nach Interessensgebieten gruppieren. Beispielsweise wird der **cus** -Namespace für die kundenspezifische Konfiguration (**Kunden**) verwendet.

>[!CAUTION]
>
>Standardmäßig muss der Name des Namespace knapp sein und darf nur autorisierte Zeichen gemäß den XML-Benennungsregeln enthalten.
>
>Bezeichner dürfen nicht mit numerischen Zeichen beginnen.

Bestimmte Namespaces sind für Beschreibungen der Systementitäten reserviert, die für den Betrieb der Adobe Campaign-Anwendung erforderlich sind:

* **xtk**: Plattformsystemdaten,
* **nl**: über die Verwendung des Antrags insgesamt,
* **nms**: bezüglich der Lieferung (Empfänger, Lieferung, Verfolgung usw.),
* **ncm**: über die Verwaltung von Inhalten,
* **temp**: für temporäre Schemata reserviert.

The identification key of a schema is a string built using the namespace and the name separated by a colon; for example: **cus:recipient**.

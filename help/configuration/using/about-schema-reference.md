---
solution: Campaign Classic
product: campaign
title: Info zu Schema-Referenz in Adobe Campaign Classic
description: Erfahren Sie, wie Sie Erweiterungsschema konfigurieren, um das konzeptionelle Datenmodell der Adobe Campaign Classic-Datenbank zu erweitern.
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 7%

---


# Über die Schemareferenz{#about-schema-reference}

In diesem Kapitel wird beschrieben, wie Sie Erweiterungsschema konfigurieren, um das konzeptionelle Datenmodell der Adobe Campaign-Datenbank zu erweitern.

Ein besseres Verständnis der integrierten Kampagnen und ihrer Interaktion finden Sie im [Campaign Classic-Datenmodell](https://helpx.adobe.com/de/campaign/kb/acc-datamodel.html).

Die physische und logische Struktur der in der Anwendung übertragenen Daten wird in XML beschrieben. Es folgt einer für Adobe Campaign spezifischen Grammatik, die als **Schema** bezeichnet wird.

Ein Schema ist ein mit einer Datenbanktabelle verknüpftes XML-Dokument. Er definiert die Datenstruktur und beschreibt die SQL-Definition der Tabelle:

* Der Name der Tabelle
* Felder
* Indizes
* Links zu anderen Tabellen

Außerdem wird die XML-Struktur zum Speichern von Daten beschrieben:

* Elemente und Attribute
* Hierarchie der Elemente
* Element- und Attributtypen
* Standardwerte
* Beschriftungen, Beschreibungen und andere Eigenschaften.

Mit Schemas können Sie eine Entität in der Datenbank definieren. Es gibt ein Schema für jede Entität.

Die folgende Abbildung zeigt die Position von Schemas im Adobe Campaign-Datensystem:

![](assets/reference_schema_intro.png)

## Syntax der Schema {#syntax-of-schemas}

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

Die Tags **`<element>`** definieren die Namen von Entitätselementen. **`<attribute>`** -Tags des Schemas definieren die Namen der Attribute in den  **`<element>`** Tags, mit denen sie verknüpft wurden.

## Identifizierung eines Schemas {#identification-of-a-schema}

Ein Schema wird anhand seines Namens und seines Namensraums identifiziert.

Mit einem Namensraum können Sie eine Reihe von Schemas nach Interessensgebieten gruppieren. Beispielsweise wird der Namensraum **cus** für die kundenspezifische Konfiguration (**Customers**) verwendet.

>[!IMPORTANT]
>
>Standardmäßig muss der Name des Namensraums knapp sein und darf nur autorisierte Zeichen gemäß den XML-Benennungsregeln enthalten.
>
>Bezeichner dürfen nicht mit numerischen Zeichen beginnen.

Bestimmte Namensräume sind für Beschreibungen der Systementitäten reserviert, die für den Betrieb des Adobe Campaign-Antrags erforderlich sind:

* **xtk**: Plattformsystemdaten,
* **nl**: über die Verwendung des Antrags insgesamt,
* **nms**: Versand (Empfänger, Versand, Verfolgung usw.),
* **ncm**: Content-Management,
* **temp**: für vorübergehende Schemas reserviert.

Der Identifizierungsschlüssel eines Schemas ist eine Zeichenfolge, die mithilfe des Namensraums und des durch einen Doppelpunkt getrennten Namens erstellt wird. Beispiel: **cus:Empfänger**.

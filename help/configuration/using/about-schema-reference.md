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

Die physische und logische Struktur der in der Anwendung übertragenen Daten wird in XML beschrieben. It obeys a grammar specific to Adobe Campaign, called a **schema**.

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

Das Stammelement des Schemas ist **`<srcschema>`**. Es enthält die **`<element>`** und die **`<attribute>`** Unterelemente.

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

## Bezeichnung eines Schemas {#identification-of-a-schema}

Ein Schema wird anhand seines Namens und seines Namensraums identifiziert.

Mit einem Namensraum können Sie eine Reihe von Schemas nach Interessensgebieten gruppieren. Beispielsweise wird der **Namensraum &quot;cus** &quot;für die kundenspezifische Konfiguration (**Kunden**) verwendet.

>[!IMPORTANT]
>
>Standardmäßig muss der Name des Namensraums knapp sein und darf nur autorisierte Zeichen gemäß den XML-Benennungsregeln enthalten.
>
>Bezeichner dürfen nicht mit numerischen Zeichen beginnen.

Bestimmte Namensräume sind für Beschreibungen der Systementitäten reserviert, die für den Betrieb des Adobe Campaign-Antrags erforderlich sind:

* **xtk**: Plattformsystemdaten,
* **nl**: über die Verwendung des Antrags insgesamt,
* **nms**: versand (Empfänger, Versand, Verfolgung usw.),
* **ncm**: content-management,
* **temp**: für vorübergehende Schemas reserviert.

The identification key of a schema is a string built using the namespace and the name separated by a colon; for example: **cus:recipient**.

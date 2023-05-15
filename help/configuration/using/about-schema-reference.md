---
product: campaign
title: Über die Schemareferenz in Adobe Campaign Classic
description: Erfahren Sie, wie Sie Erweiterungsschemata konfigurieren, um das konzeptionelle Datenmodell der Adobe Campaign Classic-Datenbank zu erweitern.
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Schema Extension
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 58%

---

# Über die Schemareferenz{#about-schema-reference}

In diesem Kapitel wird beschrieben, wie Sie Erweiterungsschemata konfigurieren, um das konzeptionelle Datenmodell der Adobe Campaign-Datenbank zu erweitern.

Die in Campaign integrierten Tabellen und deren Interaktion werden im Abschnitt [Campaign Classic-Datenmodell](https://helpx.adobe.com/de/campaign/kb/acc-datamodel.html).

Die physische und logische Struktur der im Programm übertragenen Daten wird in XML beschrieben. Sie folgt einer Adobe Campaign-spezifischen Grammatik namens **Schema**.

Ein Schema ist ein mit einer Datenbanktabelle verknüpftes XML-Dokument. Es definiert die Datenstruktur und beschreibt die SQL-Definition der Tabelle:

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

Mit einem Namespace können Sie eine Reihe von Schemas nach Interessensgebieten gruppieren. Beispielsweise wird der Namespace **cus** für die kundenspezifische Konfiguration (**customers**) verwendet.

Der Identifikationsschlüssel eines Schemas ist eine Zeichenfolge, die mithilfe des Namespace und des Namens (durch einen Doppelpunkt getrennt) erstellt wird. Beispiel: **cus:recipient**.

>[!IMPORTANT]
>
>Der Name des Namespace muss kurz sein und darf nur autorisierte Zeichen gemäß den XML-Benennungsregeln enthalten.
>
>Kennungen dürfen nicht mit numerischen Zeichen beginnen.
>
>Die folgenden Namespaces sind für Beschreibungen der Systementitäten reserviert, die für den Betrieb der Adobe Campaign-Anwendung erforderlich sind, und dürfen nicht verwendet werden: **xtk**, **nl**, **nms**, **ncm**, **temp**, **ncl**, **crm**, **xxl**.


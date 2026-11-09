---
product: campaign
title: Erste Schritte mit Schemata in Adobe Campaign
description: Erfahren Sie, wie Sie mit Schemata arbeiten und das konzeptionelle Datenmodell der Adobe Campaign-Datenbank erweitern
feature: Schema Extension
role: Developer
level: Intermediate, Experienced
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
TQID: 'https://experienceleague.adobe.com/ikQVjdkvhTM-361S7mcpRYsuhpqjHxX-Y-9wdRCYldg'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 758d5159759b19f7ef32e8cc8f6237547599e727
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 51%
---
# Erste Schritte mit Schemata {#about-schema-reference}

## Was ist ein Schema {#what-is-a-schema}

In diesem Kapitel wird beschrieben, wie Sie Erweiterungsschemata konfigurieren können, um das konzeptionelle Datenmodell der Adobe Campaign-Datenbank zu erweitern.

Genauere Informationen zu den integrierten Campaign-Tabellen und ihrer Interaktion finden Sie im [Campaign Classic-Datenmodell](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/developer/datamodel){target="_blank"} (Dokumentation zu Campaign v8).

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

>[!NOTE]
>
>Im Zuge der Umstellung von Campaign v7 auf v8 wurde die Campaign Classic-Dokumentation optimiert und neu organisiert. Allgemeine Funktionen sind jetzt nur noch in der Dokumentation zu Campaign v8 verfügbar. Informationen zur Syntax und Identifizierung von Schemata finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/developer/schemas-forms/schemas){target=_blank}.
>
>[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/developer/schemas-forms/schemas){target=_blank}

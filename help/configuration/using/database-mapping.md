---
product: campaign
title: Datenbank-Mapping
description: Datenbank-Mapping
feature: Configuration, Instance Settings
role: Developer
exl-id: 728b509f-2755-48df-8b12-449b7044e317
TQID: 'https://experienceleague.adobe.com/d3oQ8zJVsjVdj9PZ30rQ8hEuern1l3ZlMAWrbymhnvs'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a97306b73a2b577841e6f24536c62b2526e9fda9
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 19%
---
# Datenbank-Mapping{#database-mapping}

Auf dieser Seite wird beschrieben, wie Indizes für die Felder eines Schemas deklariert werden.

Im Zuge der Umstellung von Campaign v7 auf v8 wurde der Campaign Classic-Dokumentationssatz optimiert und neu organisiert. Allgemeine Funktionen sind jetzt nur noch in der Dokumentation zu Campaign v8 verfügbar. Weitere Informationen zur SQL-Zuordnung von Schemata finden Sie in der [&#x200B; zu Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/database-mapping){target=_blank}.

[![Bild](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/database-mapping){target=_blank}

## Indizierte Felder {#indexed-fields}

Mit Indizes können Sie die Leistung der in der Anwendung verwendeten SQL-Abfragen optimieren.

Ein Index wird aus dem Hauptelement des Datenschemas deklariert.

```sql
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Indizes befolgen die folgenden Regeln:

* Ein Index kann auf ein oder mehrere Felder in der Tabelle verweisen
* Ein Index kann in allen Feldern eindeutig sein (um Duplikate zu vermeiden), wenn das Attribut **unique** den Wert „true“ enthält
* Der SQL-Name des Index wird aus dem SQL-Namen der Tabelle und dem Namen des Index bestimmt

>[!NOTE]
>
>* Standardmäßig sind Indizes die ersten Elemente, die über das Hauptelement des Schemas deklariert werden.
>
>* Indizes werden während der Tabellenzuordnung automatisch erstellt (Standard oder FDA).

**Beispiel**:

* Hinzufügen eines Index zur E-Mail-Adresse und zum Ort:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </dbindex>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

* Hinzufügen eines eindeutigen Index zum Namensfeld „id“:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="id" unique="true">
        <keyfield xpath="@id"/> 
      </dbindex>
  
      <dbindex name="email">
        <keyfield xpath="@email"/> 
      </dbindex>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

## Weitere Informationen

Weitere Informationen finden Sie unter den folgenden Links:

* [Erste Schritte mit Schemata](about-schema-reference.md)
* [Schemastruktur](schema-structure.md)
* [Schlüssel-Management](database-keys.md)
* [Link-Verwaltung](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/database-links){target="_blank"} (Dokumentation zu Campaign v8)

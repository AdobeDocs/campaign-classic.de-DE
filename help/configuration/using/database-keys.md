---
product: campaign
title: Schlüsselverwaltung in Datenschemata
description: Grundlegendes zur Schlüsselverwaltung in Datenschemata
feature: Configuration, Instance Settings
role: Developer
exl-id: faf63c8f-9d10-43c1-a990-91361594af9f
TQID: 'https://experienceleague.adobe.com/dErbfzRabMls-5x1S3eRZO94Kqcz9LRh3PaUhVD5zAU'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a97306b73a2b577841e6f24536c62b2526e9fda9
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 28%
---
# Schlüsselverwaltung in Schemata {#management-of-keys}

Jede mit einem Datenschema verknüpfte Tabelle benötigt mindestens einen Schlüssel zur Identifizierung eines Eintrags in einer Tabelle. Auf dieser Seite wird der automatisch inkrementelle Schlüssel beschrieben, der in Campaign Classic v7-Tabellen verwendet wird.

Im Zuge der Umstellung von Campaign v7 auf v8 wurde der Campaign Classic-Dokumentationssatz optimiert und neu organisiert. Allgemeine Funktionen sind jetzt nur noch in der Dokumentation zu Campaign v8 verfügbar. Weitere Informationen zur Schlüsselverwaltung finden Sie in der Dokumentation zu [ v8 ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/database-keys){target=_blank}.

[![Bild](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/database-keys){target=_blank}

## Automatisch inkrementeller Schlüssel {#auto-incremental-key}

Der Primärschlüssel der meisten Adobe Campaign-Tabellen ist eine 32-Bit-Ganzzahl, die automatisch von der Datenbank-Engine generiert wird. Die Berechnung des Schlüsselwerts hängt von einer Sequenz ab (standardmäßig die SQL-Funktion **XtkNewId**), die eine in der gesamten Datenbank eindeutige Zahl generiert. Der Inhalt des Schlüssels wird beim Einfügen des Datensatzes automatisch eingegeben.

Der Vorteil eines inkrementellen Schlüssels besteht darin, dass er einen nicht veränderbaren technischen Schlüssel für die Joins zwischen Tabellen bereitstellt. Darüber hinaus benötigt dieser Schlüssel nicht viel Speicher, da er eine Doppelbyte-Ganzzahl verwendet.

Sie können im Quellschema den Namen der mit dem Attribut **pkSequence** zu verwendenden Sequenz angeben. Wenn dieses Attribut nicht im Quellschema angegeben ist, wird die **XtkNewId** Standardsequenz verwendet. Die Anwendung verwendet dedizierte Sequenzen für die Schemata **nms:broadLog** und **nms:trackingLog** (**NmsBroadLogId** bzw. **NmsTrackingLogId**), da dies die Tabellen sind, die die meisten Datensätze enthalten.

Ab ACC 18.10 **XtkNewId** nicht mehr der Standardwert für die Sequenz in den vordefinierten Schemata. Sie können jetzt ein Schema erstellen oder ein vorhandenes Schema mit einer dedizierten Sequenz erweitern.

>[!IMPORTANT]
>
>Beim Anlegen eines neuen Schemas oder bei einer Schema-Erweiterung müssen Sie für das gesamte Schema den gleichen Wert für die Primärschlüsselsequenz (@pkSequence) beibehalten.

Eine Sequenz, auf die in einem Adobe Campaign-Schema (**NmsTrackingLogId** verwiesen wird), muss mit einer SQL-Funktion verknüpft sein, die die Anzahl der IDs in den Parametern zurückgibt, getrennt durch Kommas. Diese Funktion muss als **GetNew** XXX **Ids** bezeichnet werden, wobei **XXX** der Name der Sequenz ist (z. B **GetNewNmsTrackingLogIds**). Sehen Sie sich die **postgres-nms.sql**, **mssql-nms.sql** oder **oracle-nms.sql** an, die mit der Anwendung im Verzeichnis **datakit/nms/eng/sql/** bereitgestellt werden, um das Beispiel einer Sequenzerstellung „NmsTrackingLogId“ für jede Datenbank-Engine abzurufen.

Um einen eindeutigen Schlüssel zu deklarieren, füllen **das Attribut &quot;**&quot; (mit dem Wert „true„) im Hauptelement des Datenschemas auf.

**Beispiel**:

Deklarieren eines inkrementellen Schlüssels im Quellschema:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

Generiertes Schema:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" autopk="true" pkSequence="XtkNewId" sqltable="CusRecipient"> 
    <dbindex name="id" unique="true">
      <keyfield xpath="@id"/>
    </dbindex>

    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key>

    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iRecipientId" type="long"/>
  </element>
</schema>
```

Zusätzlich zur Definition des Schlüssels und seines Index wurde dem erweiterten Schema ein numerisches Feld namens „id“ hinzugefügt, das den automatisch generierten Primärschlüssel enthält.

>[!IMPORTANT]
>
>Ein Datensatz mit einem auf 0 gesetzten Primärschlüssel wird bei der Erstellung der Tabelle automatisch eingefügt. Durch die Verwendung dieses Datensatzes werden äußere Joins vermieden, die sich bei Volumentabellen als nicht effektiv erweisen. Standardmäßig werden alle Fremdschlüssel mit dem Wert 0 initialisiert. Auf diese Weise kann beim Join immer ein Ergebnis zurückgegeben werden, wenn das Datenelement nicht ausgefüllt wird.


## Weitere Informationen

Weitere Informationen finden Sie unter den folgenden Links:

* [Erste Schritte mit Schemata](about-schema-reference.md)
* [Schemastruktur](schema-structure.md)
* [Datenbank-Mapping](database-mapping.md)
* [Link-Verwaltung](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/database-links){target="_blank"} (Dokumentation zu Campaign v8)
* [Campaign-Datenmodell](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/developer/datamodel){target="_blank"} (Dokumentation zu Campaign v8)

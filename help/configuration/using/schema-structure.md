---
product: campaign
title: Schemastruktur in Adobe Campaign
description: Schemastruktur
feature: Custom Resources
role: Developer
audience: configuration
content-type: reference
level: Intermediate, Experienced
topic-tags: schema-reference
exl-id: 3405efb8-a37c-4622-a271-63d7a4148751
TQID: 'https://experienceleague.adobe.com/dFZ38qRKX-4vTEYS9GosS5TdW-XhnoIq8ckbjnNEJmo'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
  - id: a2002dba-5e37-4dff-8e04-1cc3ec73558c
    internal-label: Custom resources
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: a97306b73a2b577841e6f24536c62b2526e9fda9
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 22%
---
# Schemastruktur verstehen {#schema-structure}

Auf dieser Seite wird aufgelistet, wie die Adobe Campaign-Datentypen den Datentypen der einzelnen Datenbankverwaltungssysteme zugeordnet sind.

Im Zuge der Umstellung von Campaign v7 auf v8 wurde der Campaign Classic-Dokumentationssatz optimiert und neu organisiert. Allgemeine Funktionen sind jetzt nur noch in der Dokumentation zu Campaign v8 verfügbar. Weitere Informationen zur Schemastruktur finden Sie in der Dokumentation zu [&#x200B; v8 &#x200B;](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/developer/schemas-forms/schema-structure){target=_blank}.

[![Bild](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/developer/schemas-forms/schema-structure){target=_blank}

## Zuordnen der Typen von Adobe Campaign-/DBMS-Daten {#mapping-the-types-of-adobe-campaign-dbms-data}

In der folgenden Tabelle sind die Zuordnungen für die Datentypen aufgeführt, die von Adobe Campaign für die verschiedenen Datenbankverwaltungssysteme generiert werden.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Campaign</strong><br /> </td> 
   <td> <strong>PosgreSQL</strong><br /> </td> 
   <td> <strong>Oracle</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> String <br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2 (NVARCHAR2, wenn Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Boolesch<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> ZAHL(3)<br /> </td> 
  </tr> 
  <tr> 
   <td> byte<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> ZAHL(3)<br /> </td> 
  </tr> 
  <tr> 
   <td> Kurz<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> ZAHL(5)<br /> </td> 
  </tr> 
  <tr> 
   <td> Doppelt<br /> </td> 
   <td> DOPPELTE GENAUIGKEIT<br /> </td> 
   <td> SCHWEBEN<br /> </td> 
  </tr> 
  <tr> 
   <td> Lang<br /> </td> 
   <td> GANZZAHL<br /> </td> 
   <td> ZAHL(10)<br /> </td> 
  </tr> 
  <tr> 
   <td> int64<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> ZAHL(20)<br /> </td> 
  </tr> 
  <tr> 
   <td> Datum<br /> </td> 
   <td> DATUM<br /> </td> 
   <td> DATUM<br /> </td> 
  </tr> 
  <tr> 
   <td> Zeit<br /> </td> 
   <td> ZEIT<br /> </td> 
   <td> SCHWEBEN<br /> </td> 
  </tr> 
  <tr> 
   <td> Datum/Uhrzeit<br /> </td> 
   <td> ZEITSTEMPEL<br /> </td> 
   <td> DATUM<br /> </td> 
  </tr> 
  <tr> 
   <td> datetimenotz<br /> </td> 
   <td> ZEITSTEMPEL<br /> </td> 
   <td> DATUM<br /> </td> 
  </tr> 
  <tr> 
   <td> timespan<br /> </td> 
   <td> DOPPELTE GENAUIGKEIT<br /> </td> 
   <td> SCHWEBEN<br /> </td> 
  </tr> 
  <tr> 
   <td> Memo<br /> </td> 
   <td> TEXT<br /> </td> 
   <td> CLOB (NCLOB, wenn Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Blob<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Weitere Informationen

Weitere Informationen finden Sie unter den folgenden Links:

* [Erste Schritte mit Schemata](about-schema-reference.md)
* [Datenbank-Mapping](database-mapping.md)
* [Link-Verwaltung](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/developer/schemas-forms/database-links){target="_blank"} (Dokumentation zu Campaign v8)
* [Schlüssel-Management](database-keys.md)

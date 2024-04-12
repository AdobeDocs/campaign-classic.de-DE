---
product: campaign
title: Wechseln zu Unicode
description: Wechseln zu Unicode
feature: Monitoring
badge-v7-prem: label="On-Premise und Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4cfecf2f-cf98-42c1-b979-cdd26d5de48b
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 7%

---

# Wechseln zu Unicode{#switching-to-unicode}



Für vorhandene **prod** -Instanz in Linux/PostgreSQL werden die folgenden Schritte für den Umstieg auf Unicode ausgeführt:

1. Beenden Sie die Prozesse, die in die Datenbank schreiben:

   ```
   su - neolane
   nlserver shutdown
   ```

1. Datenbank abrufen:

   ```
   su - postgres
   pg_dump mydatabase > mydatabase.sql
   ```

1. Erstellen Sie eine Unicode-Datenbank:

   ```
   createdb -E UNICODE mydatabase_unicode
   ```

1. Datenbank wiederherstellen:

   ```
   psql mydatabase_unicode < mydatabase.sql
   ```

1. Aktualisieren Sie die Option, die angibt, dass die Datenbank Unicode ist:

   ```
   psql mydatabase_unicode
   update XtkOption set sStringValue = 'u'||sStringValue where sName='XtkDatabaseId' and sStringValue not like 'u%';
   ```

1. Auf den Tracking-Servern:

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   Fügen Sie die **u** -Zeichen vor dem Wert für die Datenbank-ID (**databaseId**):

   ```
   <web>
    <redirection databaseId="u7F0000010554364C" trackingPassword="myPassword="/>
   </web>
   ```

1. Auf Servern, die die Datenbank aufrufen:

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   Ändern Sie die Datenbankreferenz:

   ```
   <dataSource name="default">
    <dbcnx encrypted="1" 
    login="<dbuser>:<base_unicode>" password="xxxx="
    provider="postgresql" server="yyyy"/>
   </dataSource>
   ```

1. Starten Sie alle Computer neu:

   ```
   /etc/init.d/apache stop
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   /etc/init.d/apache start
   ```

1. Bestätigen Sie den Schalter. Stellen Sie dazu eine Verbindung über die Adobe Campaign-Konsole her und:

   * Überprüfen Sie, ob die Daten korrekt angezeigt werden, insbesondere die akzentuierten Zeichen:
   * Starten Sie einen Versand und vergewissern Sie sich, dass der Tracking-Abruf funktioniert.

---
solution: Campaign Classic
product: campaign
title: Wechseln zu Unicode
description: Wechseln zu Unicode
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 7%

---


# Wechseln zu Unicode{#switching-to-unicode}

Für eine vorhandene **Prod** -Instanz in Linux/PostgreSQL werden die folgenden Schritte zum Wechseln zu Unicode ausgeführt:

1. Prozesse, die in die Datenbank schreiben, beenden:

   ```
   su - neolane
   nlserver shutdown
   ```

1. Datenbank ablegen:

   ```
   su - postgres
   pg_dump mydatabase > mydatabase.sql
   ```

1. Eine Unicode-Datenbank erstellen:

   ```
   createdb -E UNICODE mydatabase_unicode
   ```

1. Datenbank wiederherstellen:

   ```
   psql mydatabase_unicode < mydatabase.sql
   ```

1. Aktualisieren Sie die Option, die angibt, dass die Datenbank Unicode lautet:

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

   hinzufügen das **u** -Zeichen vor dem Wert für die Datenbank-ID (**databaseId**):

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

   Datenbankverweis ändern:

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

1. Überprüfen Sie den Switch. Stellen Sie dazu eine Verbindung über die Adobe Campaign-Konsole her und:

   * Überprüfen Sie, ob die Daten korrekt angezeigt werden, insbesondere die Zeichen mit Akzentuierung:
   * starten Sie einen Versand und überprüfen Sie, ob der Tracking-Abruf funktioniert.


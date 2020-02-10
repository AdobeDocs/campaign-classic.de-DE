---
title: Wechsel zu Unicode
seo-title: Wechsel zu Unicode
description: Wechsel zu Unicode
seo-description: null
page-status-flag: never-activated
uuid: 5f15b285-7377-453a-aa98-ca4cf14a4c80
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: 0f5399a8-860d-4a1b-86a9-9011b973346b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Wechsel zu Unicode{#switching-to-unicode}

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

   Fügen Sie das **u** -Zeichen vor dem Wert für die Datenbank-ID (**databaseId**) hinzu:

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
   * eine Bereitstellung starten und überprüfen, ob der Tracking-Abruf funktioniert.


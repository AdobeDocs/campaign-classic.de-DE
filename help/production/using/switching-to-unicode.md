---
product: campaign
title: Wechseln zu Unicode
description: Wechseln zu Unicode
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4cfecf2f-cf98-42c1-b979-cdd26d5de48b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 7%

---

# Wechseln zu Unicode{#switching-to-unicode}

![](../../assets/v7-only.svg)

Für eine vorhandene **prod**-Instanz in Linux/PostgreSQL sind die Schritte zum Wechseln zu Unicode wie folgt:

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

   Fügen Sie das Zeichen **u** vor dem Wert hinzu, der sich auf die Datenbankkennung (**databaseId**) bezieht:

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

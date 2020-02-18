---
title: Übliche Befehle
seo-title: Übliche Befehle
description: Übliche Befehle
seo-description: null
page-status-flag: never-activated
uuid: f06df8c0-d4ec-4d6b-84d5-f46d852388a3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 90718075-87a7-4e9a-935b-571010908e79
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: de04b5d3ceb883a571ee665f630be931a68a5a3e

---


# Übliche Befehle{#usual-commands}

In diesem Abschnitt werden die üblichen Befehle in Adobe Campaign aufgeführt.

Der Befehl **nlserver** ist der Eingabebefehl für die gesamte Adobe Campaign-Anwendung.

Dieser Befehl hat folgende Syntax: **nlserver **`<command>`****`<arguments>`****

Der Parameter **`<command>`** entspricht dem Modul.

>[!NOTE]
>
>* In jedem Fall können Sie das **-noconsole** -Argument hinzufügen, um die nach dem Starten der Module angezeigten Kommentare zu löschen.
>* Umgekehrt können Sie das Argument **-verbose** hinzufügen, um weitere Informationen anzuzeigen.
>



## Überwachungsbefehle {#monitoring-commands-}

>[!NOTE]
>
>Um alle Module aufzulisten, müssen Sie den Befehl **nlserver pdump** verwenden.

Sie können den Parameter **-who** hinzufügen, um die ausgeführten Verbindungen (Datenbank und Anwendung) aufzulisten.

```
nlserver pdump -who
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
web@default (9984) - 50.1 Mo
watchdog (2273) - 6.6 Mo
syslogd@default (9931) - 7.0 Mo
trackinglogd@default (9985) - 45.6 Mo
mta@test (9986) - 9.6 Mo
wfserver@test (9987) - 8.8 Mo

Connections ------------------------------------------------------
Last Access IP Instance Login 
DD/MM/YYYY HH:MM:SS 127.0.0.1 default formation_fr|tracking
DD/MM/YYYY HH:MM:SS 127.0.0.1 default internal|monitoring

Connection pool --------------------------------------------------
Datasource Server Provider Login 
default xxxxx myserver myprovider test400
```

Ein weiterer nützlicher Befehl ist **nlserver monitor**. Er listet die XML-Überwachungsdatei auf (die über den Adobe Campaign-Client oder die **Webseite monitor.jsp** bezogen wird).

Sie können den Parameter &quot; **Fehlend** &quot;hinzufügen, um die fehlenden Module aufzulisten (Fehler in Modulen, Herunterfahren von Modulen usw.)

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

Dies entspricht den Modulen mit automatischem Start, die jedoch nicht gestartet wurden.

## Module, Befehle zum Starten {#module-launch-commands}

Die Syntax zum Starten von Modulen hat weiterhin das folgende Format:

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** entspricht dem Namen der Instanz, die in den Konfigurationsdateien eingegeben wurde, oder **Standard** für Module mit nur einer Instanz.

## Dienste beenden {#shut-down-services}

Um Adobe Campaign-Dienste zu beenden, verwenden Sie einen der folgenden Befehle:

* Wenn Sie Zugriff auf Root oder Administrator haben:

   * Unter Linux:

      ```
      /etc/init.d/nlserver6 stop
      ```

      >[!NOTE]
      >
      >Ab 20.1 wird empfohlen, stattdessen den folgenden Befehl zu verwenden (für Linux): nlserver **systemctl stop**

   * Windows:

      ```
      net stop nlserver6
      ```

* Wenn nicht, dann im Adobe Campaign-Konto:

   ```
   nlserver shutdown 
   ```

## Dienste wieder starten {#restart-services}

Ebenso können Sie zum Neustart von Adobe Campaign einen der folgenden Befehle verwenden:

* Wenn Sie Zugriff auf Root oder Administrator haben:

   * Unter Linux: /etc/init.d/nlserver6 start

      >[!NOTE]
      >
      >Ab 20.1 wird empfohlen, stattdessen den folgenden Befehl zu verwenden (für Linux): nlserver **systemctl start**

   * Windows: net start nlserver6

* Andernfalls im Adobe Campaign-Konto: **nlserver watchdog -svc -noconsole**

## Befehl &quot;config&quot; {#the-config-command}

Mit dem Befehl &quot; **config** &quot;können Sie die Serverkonfiguration einschließlich der Neukonfiguration der Datenbankverbindung verwalten.

Verwenden Sie den Befehl **config** der ausführbaren Datei **nlserver** mit dem Parameter **-setdblogin** .

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Geben Sie das Kennwort ein.

So ändern Sie das **interne** Kennwort: **nlserver config -internalpassword**

>[!CAUTION]
>
>Um sich mit der **internen** Kennung anzumelden, müssen Sie vorher ein Kennwort definiert haben. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/campaign-server-configuration.md#internal-identifier).

>[!NOTE]
>
>* Im Allgemeinen können Sie den Befehl **config** verwenden, anstatt die Konfigurationsdateien manuell zu ändern
>* Um die Liste der Parameter abzurufen, verwenden Sie das **-?** Parameter: **nlserver config -?**
>* Bei einer Oracle-Datenbank dürfen Sie das Konto nicht angeben. Die Syntax lautet wie folgt:
>
>  
nlserver config -setdblogin:Oracle:test6@dbserver



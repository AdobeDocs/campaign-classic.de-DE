---
product: campaign
title: Übliche Befehle
description: Übliche Befehle
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 8%

---

# Übliche Befehle{#usual-commands}

![](../../assets/v7-only.svg)

In diesem Abschnitt werden die üblichen Befehle in Adobe Campaign aufgeführt.

Der Befehl **nlserver** ist der Eingabebefehl für die gesamte Adobe Campaign-Anwendung.

Dieser Befehl hat die folgende Syntax: **nlserver **`<command>`****`<arguments>`****

Der Parameter **`<command>`** entspricht dem -Modul.

>[!NOTE]
>
>* Sie können auf jeden Fall das Argument **-noconsole** hinzufügen, um Kommentare zu löschen, die nach dem Starten der Module angezeigt werden.
>* Umgekehrt können Sie das Argument **-verbose** hinzufügen, um weitere Informationen anzuzeigen.

>


## Überwachen von Befehlen {#monitoring-commands-}

>[!NOTE]
>
>Um alle Module aufzulisten, müssen Sie den Befehl **nlserver pdump** verwenden.

Sie können den Parameter **-who** hinzufügen, um die laufenden Verbindungen (Datenbank und Anwendung) aufzulisten.

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

Ein weiterer nützlicher Befehl ist **nlserver monitor**. Es listet die XML-Überwachungsdatei auf (abgerufen im Adobe Campaign-Client oder über die Webseite **monitor.jsp** ).

Sie können den Parameter **-missing** hinzufügen, um die fehlenden Module aufzulisten (Fehler in Modulen, heruntergeladene Module usw.)

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

Dies entspricht den Modulen mit automatischem Start, die jedoch nicht gestartet wurden.

## Module - Launch-Befehle {#module-launch-commands}

Die Syntax zum Starten von Modulen hat weiterhin das folgende Format:

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** entspricht dem in den Konfigurationsdateien angegebenen Namen der Instanz oder  **** Standard für Mono-Instanzmodule.

## Dienste beenden {#shut-down-services}

Um Adobe Campaign-Dienste zu beenden, verwenden Sie einen der folgenden Befehle:

* Wenn Sie über Root- oder Administratorzugriff verfügen:

   * Unter Linux:

      ```
      /etc/init.d/nlserver6 stop
      ```

      >[!NOTE]
      >
      >Ab Version 20.1 wird empfohlen, stattdessen den folgenden Befehl zu verwenden (für Linux): **systemctl stop nlserver**

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

* Wenn Sie über Root- oder Administratorzugriff verfügen:

   * Unter Linux: /etc/init.d/nlserver6 start

      >[!NOTE]
      >
      >Ab 20.1 wird empfohlen, stattdessen den folgenden Befehl zu verwenden (für Linux): **systemctl Beginn nlserver**

   * Windows: net start nlserver6

* Andernfalls im Adobe Campaign-Konto: **nlserver watchdog -svc -noconsole**

## Konfigurationsbefehl {#the-config-command}

Mit dem Befehl **config** können Sie die Serverkonfiguration verwalten, einschließlich der Neukonfiguration der Datenbankverbindung.

Verwenden Sie den Befehl **config** der ausführbaren Datei **nlserver** mit dem Parameter **-setdblogin** .

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Geben Sie das Kennwort ein.

So ändern Sie das Kennwort **internal**: **nlserver config -internalpassword**

>[!IMPORTANT]
>
>Um sich mit der Kennung **Internal** anzumelden, müssen Sie zuvor ein Kennwort definiert haben. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

>[!NOTE]
>
>* Im Allgemeinen können Sie den Befehl **config** verwenden, anstatt die Konfigurationsdateien manuell zu ändern
>* Um die Liste der Parameter zu erhalten, verwenden Sie die **-?** Parameter:  **nlserver config -?**
>* Bei einer Oracle-Datenbank darf das Konto nicht angegeben werden. Die Syntax lautet wie folgt:
>
>  nlserver config -setdblogin:Oracle:test6@dbserver

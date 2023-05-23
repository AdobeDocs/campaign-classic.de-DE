---
product: campaign
title: Übliche Befehle
description: Übliche Befehle
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 9%

---

# Übliche Befehle{#usual-commands}



In diesem Abschnitt werden die üblichen Befehle in Adobe Campaign aufgeführt.

Der Befehl **nlserver** ist der Eingabebefehl für die gesamte Adobe Campaign-Anwendung.

Dieser Befehl hat die folgende Syntax: **nlserver **`<command>`****`<arguments>`****

Der Parameter **`<command>`** dem Modul entspricht.

>[!NOTE]
>
>* Auf jeden Fall können Sie die **-noconsole** -Argument zum Löschen von Kommentaren, die nach dem Start der Module angezeigt werden.
>* Umgekehrt können Sie das -Argument hinzufügen **-verbose** um weitere Informationen anzuzeigen.
>


## Überwachen von Befehlen {#monitoring-commands-}

>[!NOTE]
>
>Um alle Module aufzulisten, müssen Sie die **nlserver pdump** Befehl.

Sie können den Parameter hinzufügen **-who** , um die laufenden Verbindungen (Datenbank und Anwendung) aufzulisten.

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

Ein weiterer nützlicher Befehl ist **nlserver-Monitor**. Sie listet die (im Adobe Campaign-Client oder über die **monitor.jsp** Webseite).

Sie können den Parameter hinzufügen **-missing** , um die fehlenden Module aufzulisten (Fehler in Modulen, heruntergefahren von Modulen usw.)

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
>**`<instance>`** dem in den Konfigurationsdateien angegebenen Namen der Instanz entspricht oder **default** für Mono-Instanzmodule.

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

Die **config** -Befehl können Sie die Serverkonfiguration verwalten, einschließlich der Neukonfiguration der Datenbankverbindung.

Verwenden Sie die **config** des **nlserver** ausführbare Datei mit **-setdblogin** Parameter.

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Geben Sie das Passwort ein.

So ändern Sie die **intern** password: **nlserver config -internalpassword**

>[!IMPORTANT]
>
>So melden Sie sich mit dem **intern** Kennung, müssen Sie zuvor ein Kennwort definiert haben. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

>[!NOTE]
>
>* Anstatt die Konfigurationsdateien manuell zu ändern, können Sie im Allgemeinen die **config** command
>* Um die Liste der Parameter abzurufen, verwenden Sie die **-?** Parameter: **nlserver config -?**
>* Bei einer Oracle-Datenbank darf das Konto nicht angegeben werden. Die Syntax lautet wie folgt:
>
>  nlserver config -setdblogin:Oracle:test6@dbserver

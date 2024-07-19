---
product: campaign
title: Übliche Befehle
description: Übliche Befehle
feature: Monitoring
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
source-git-commit: b7dedddc080d1ea8db700fabc9ee03238b3706cc
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 8%

---

# Übliche Befehle{#usual-commands}



In diesem Abschnitt werden die üblichen Befehle in Adobe Campaign aufgeführt.

Der Befehl **nlserver** ist der Eingabebefehl für die gesamte Adobe Campaign-Anwendung.

Dieser Befehl hat die folgende Syntax: **nlserver **`<command>`****`<arguments>`****

Der Parameter **`<command>`** entspricht dem -Modul.

>[!NOTE]
>
>* Auf jeden Fall können Sie das Argument **-noconsole** hinzufügen, um die nach dem Start der Module angezeigten Kommentare zu löschen.
>* Umgekehrt können Sie das Argument **-verbose** hinzufügen, um weitere Informationen anzuzeigen.
>

## Überwachen von Befehlen {#monitoring-commands-}

>[!NOTE]
>
>Um alle Module aufzulisten, müssen Sie den Befehl **nlserver pdump** verwenden.

Sie können den Parameter **-who** hinzufügen, um die ausgeführten Verbindungen (Datenbank und Anwendung) aufzulisten.

```sql
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

Sie können den Parameter **-missing** hinzufügen, um die fehlenden Module aufzulisten (Fehler in Modulen, heruntergefahren von Modulen usw.)

```sql
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

Dies entspricht den Modulen mit automatischem Start, die jedoch nicht gestartet wurden.

## Module - Launch-Befehle {#module-launch-commands}

Die Syntax zum Starten von Modulen hat weiterhin das folgende Format:

```sql
nlserver start <module>@<INSTANCE>
```

```sql
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** entspricht dem Namen der Instanz, der in den Konfigurationsdateien eingegeben wurde, oder **default** für Mono-Instanzmodule.

## Dienste beenden {#shut-down-services}

Um Adobe Campaign-Dienste zu beenden, verwenden Sie einen der folgenden Befehle:

* Wenn Sie über Root- oder Administratorzugriff verfügen:

   * Unter Linux:

     ```sql
     /etc/init.d/nlserver6 stop
     ```

     >[!NOTE]
     >
     >Ab Version 20.1 wird empfohlen, stattdessen den folgenden Befehl zu verwenden (für Linux): **systemctl stop nlserver**

   * Windows:

     ```sql
     net stop nlserver6
     ```

* Wenn nicht, dann im Adobe Campaign-Konto:

  ```sql
  nlserver shutdown 
  ```

## Dienste wieder starten {#restart-services}

Um Adobe Campaign neu zu starten, können Sie einen der folgenden Befehle verwenden:

* Wenn Sie über Root- oder Administratorzugriff verfügen:

   * Unter Linux: `/etc/init.d/nlserver6 start`

     >[!NOTE]
     >
     >Ab Version 20.1 wird empfohlen, stattdessen den folgenden Befehl zu verwenden (für Linux): **systemctl start nlserver**

   * Windows: `net start nlserver6`

* Andernfalls im Adobe Campaign-Konto: **nlserver watchdog -svc -noconsole**

## Konfigurationsbefehl {#the-config-command}

Mit dem Befehl **config** können Sie die Serverkonfiguration verwalten, einschließlich der Neukonfiguration der Datenbankverbindung.

Verwenden Sie den Befehl **config** der ausführbaren Datei **nlserver** mit dem Parameter **-setdblogin** .

```sql
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```sql
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Geben Sie das Passwort ein.

So ändern Sie das Kennwort **internal**: **nlserver config -internalpassword**

>[!IMPORTANT]
>
>Um sich mit der Kennung **Internal** anzumelden, müssen Sie zuvor ein Kennwort definiert haben. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

>[!NOTE]
>
>* Im Allgemeinen können Sie den Befehl **config** verwenden, anstatt die Konfigurationsdateien manuell zu ändern
>* Um die Liste der Parameter abzurufen, verwenden Sie die **-?** Parameter: **nlserver config -?**
>* Bei einer Oracle-Datenbank darf das Konto nicht angegeben werden. Die Syntax lautet wie folgt:
>
>  `nlserver config -setdblogin:Oracle:test6@dbserver`
>

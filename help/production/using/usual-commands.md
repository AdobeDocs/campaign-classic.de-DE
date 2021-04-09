---
solution: Campaign Classic
product: campaign
title: Übliche Befehle
description: Übliche Befehle
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 8%

---

# Übliche Befehle{#usual-commands}

In diesem Abschnitt werden die üblichen Befehle in Adobe Campaign Liste.

Der Befehl **nlserver** ist der Eingabebefehl für die gesamte Adobe Campaign-Anwendung.

Dieser Befehl hat folgende Syntax: **nlserver **`<command>`****`<arguments>`****

Der Parameter **`<command>`** entspricht dem Modul.

>[!NOTE]
>
>* In jedem Fall können Sie das Argument **-noconsole** hinzufügen, um die nach dem Starten der Module angezeigten Kommentare zu löschen.
>* Umgekehrt können Sie das Argument **-verbose** hinzufügen, um weitere Informationen anzuzeigen.

>



## Überwachungsbefehle {#monitoring-commands-}

>[!NOTE]
>
>Zur Liste aller Module müssen Sie den Befehl **nlserver pdump** verwenden.

Sie können den Parameter **-who** zur Liste der ausgeführten Verbindungen (Datenbank und Anwendung) hinzufügen.

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

Ein weiterer nützlicher Befehl ist **nlserver monitor**. Die XML-Überwachungsdatei wird Liste (im Adobe Campaign oder über die Webseite **monitor.jsp** abgerufen).

Sie können den Parameter **-misst** zur Liste der fehlenden Module hinzufügen (Fehler in Modulen, Herunterfahren von Modulen usw.)

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

Dies entspricht den Modulen mit automatischem Start, die jedoch nicht gestartet wurden.

## Module - Startbefehle {#module-launch-commands}

Die Syntax zum Starten von Modulen hat weiterhin das folgende Format:

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** entspricht dem Namen der Instanz, wie er in den Konfigurationsdateien eingegeben wurde, oder  **** Standard für Module mit nur einer Instanz.

## Dienste beenden {#shut-down-services}

Um Adobe Campaign-Dienste zu beenden, verwenden Sie einen der folgenden Befehle:

* Wenn Sie Zugriff auf Root oder Administrator haben:

   * Unter Linux:

      ```
      /etc/init.d/nlserver6 stop
      ```

      >[!NOTE]
      >
      >Ab 20.1 wird empfohlen, stattdessen den folgenden Befehl zu verwenden (für Linux): **systemctl stop nlserver**

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

   * Unter Linux: /etc/init.d/nlserver6 Beginn

      >[!NOTE]
      >
      >Ab 20.1 wird empfohlen, stattdessen den folgenden Befehl zu verwenden (für Linux): **systemctl Beginn nlserver**

   * Windows: net Beginn nlserver6

* Andernfalls im Adobe Campaign-Konto: **nlserver watchdog -svc -noconsole**

## Der config-Befehl {#the-config-command}

Mit dem Befehl **config** können Sie die Serverkonfiguration einschließlich der Neukonfiguration der Datenbankverbindung verwalten.

Verwenden Sie den Befehl **config** der ausführbaren Datei **nlserver** mit dem Parameter **-setdblogin**.

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Geben Sie das Kennwort ein.

So ändern Sie das **interne**-Kennwort: **nlserver config -internalpassword**

>[!IMPORTANT]
>
>Um sich mit dem Bezeichner **Internal** anzumelden, müssen Sie vorher ein Kennwort definiert haben. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

>[!NOTE]
>
>* Im Allgemeinen können Sie den Befehl **config** verwenden, anstatt die Konfigurationsdateien manuell zu ändern
>* Verwenden Sie zum Abrufen der Liste von Parametern das **-?** Parameter:  **nlserver config -?**
>* Bei einer Oracle-Datenbank dürfen Sie das Konto nicht angeben. Die Syntax lautet wie folgt:

>
>  
nlserver config -setdblogin:Oracle:test6@dbserver


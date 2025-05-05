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
source-git-commit: b8a6a0db27826309456c285c08d4f1d85de70283
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 7%

---

# Übliche Befehle{#usual-commands}



In diesem Abschnitt werden die in Adobe Campaign üblichen Befehle aufgelistet.

Der Befehl **nlserver** ist der Eingabebefehl für die gesamte Adobe Campaign-Anwendung.

Dieser Befehl hat die folgende Syntax: **nlserver &#x200B;**`<command>`**&#x200B;**`<arguments>`**&#x200B;**

Der Parameter **`<command>`** entspricht dem Modul .

>[!NOTE]
>
>* In jedem Fall können Sie das Argument **-noconsole** hinzufügen, um Kommentare zu löschen, die angezeigt werden, sobald die Module gestartet werden.
>* Umgekehrt können Sie das Argument **-verbose** hinzufügen, um weitere Informationen anzuzeigen.
>

## Befehle überwachen {#monitoring-commands-}

>[!NOTE]
>
>Um alle Module aufzulisten, müssen Sie den Befehl **nlserver pdump** verwenden.

Sie können den Parameter **-wer** hinzufügen, um die laufenden Verbindungen (Datenbank und Anwendung) aufzulisten.

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

Ein weiterer nützlicher Befehl ist **nlserver monitor**. Sie listet die XML-Überwachungsdatei auf (im Adobe Campaign-Client oder über die Webseite **monitor.jsp**).

Sie können den Parameter **-missing hinzufügen** um die fehlenden Module aufzulisten (Fehler in Modulen, Herunterfahren von Modulen usw.)

```sql
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

Dies entspricht den Modulen mit automatischem Start, die aber noch nicht gestartet wurden.

## Module Launch-Befehle {#module-launch-commands}

Die Syntax zum Starten von -Modulen hat weiterhin das folgende Format:

```sql
nlserver start <module>@<INSTANCE>
```

```sql
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** entspricht dem Namen der Instanz, wie er in den Konfigurationsdateien eingegeben wurde, oder **Standard** für Module mit Einfach-Instanz.

## Dienste beenden {#shut-down-services}

Verwenden Sie einen der folgenden Befehle, um Adobe Campaign-Services zu stoppen:

* Wenn Sie über Root- oder Administratorrechte verfügen:

   * Unter Linux:

     ```sql
     /etc/init.d/nlserver6 stop
     ```

     >[!NOTE]
     >
     >Ab 20.1 wird stattdessen der folgende Befehl empfohlen (für Linux): **systemctl stop nlserver**

   * Windows:

     ```sql
     net stop nlserver6
     ```

* Wenn nicht, dann im Adobe Campaign-Konto:

  ```sql
  nlserver shutdown 
  ```

## Dienste wieder starten {#restart-services}

Entsprechend können Sie zum Neustart von Adobe Campaign einen der folgenden Befehle verwenden:

* Wenn Sie über Root- oder Administratorrechte verfügen:

   * Unter Linux: `/etc/init.d/nlserver6 start`

     >[!NOTE]
     >
     >Ab 20.1 wird empfohlen, stattdessen den folgenden Befehl zu verwenden (für Linux): **systemctl start nlserver**

   * Unter Windows: `net start nlserver6`

* Andernfalls im Adobe Campaign-Konto: **nlserver watchdog -svc -noconsole**

## Der Konfigurationsbefehl {#the-config-command}

Der **config**-Befehl ermöglicht die Verwaltung der Serverkonfiguration, einschließlich der Neukonfiguration der Datenbankverbindung.

Verwenden Sie den **config** der ausführbaren **nlserver**-Datei mit dem Parameter **-setdblogin**.

```sql
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```sql
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Geben Sie das Passwort ein.

So ändern Sie das **internal**-Kennwort: **nlserver config -internalPassword**

>[!IMPORTANT]
>
>Für die Anmeldung mit der **internen** Kennung muss zuvor ein Kennwort definiert worden sein. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

>[!NOTE]
>
>* Im Allgemeinen können Sie den Befehl **config“ verwenden, anstatt die Konfigurationsdateien manuell** ändern
>* Um die Liste der Parameter zu erhalten, verwenden Sie das **-?**: **nlserver config -?**
>* Bei einer Oracle-Datenbank darf das Konto nicht angegeben werden. Die Syntax sieht wie folgt aus:
>
>  `nlserver config -setdblogin:Oracle:test6@dbserver`
>

Im Folgenden finden Sie ein Beispiel für MSSQL:

```sql
nlserver config -setdblogin:mssql:<login>/"<password>"@<server> -instance:<instance_name> 
```

* -Anmeldung (z. B. account:user) und -Server finden Sie im dataSource-Knoten der Datei config-&lt;instance_name>.xml.
* Das Kennwort muss in Anführungszeichen eingeschlossen werden.


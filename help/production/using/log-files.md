---
product: campaign
title: Protokolldateien
description: Protokolldateien
feature: Monitoring
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: c9d427da-6965-4945-90f0-d0770701d55e
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 5%

---

# Protokolldateien{#log-files}



Die Protokolldateien sind wie folgt aufgebaut:

![](assets/d_ncs_directory.png)

Jedes **nlserver**-Modul generiert eine Protokolldatei, die im folgenden Verzeichnis gespeichert ist: **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

Das **nlserver syslogd**-Modul speichert die Protokolle auf der Festplatte. Dieses Modul ähnelt dem Unix **syslog-Daemon**, wurde jedoch aus Gründen der Kompatibilität zwischen Unix und Windows angepasst. Die anderen Adobe Campaign-Module speichern ihre Protokolle nicht auf der Festplatte, sondern delegieren diese Aufgabe an das **syslogd**-Modul, indem sie UDP-Pakete senden.

Standardmäßig ist auf der Adobe Campaign-Plattform das Modul **syslogd** installiert, es kann jedoch auch ein anderer **syslog-Daemon** verwendet werden. Dieses Modul erstellt die Protokolldateien im Verzeichnis **log**.

Die Protokolle von Modulen mit mehreren Instanzen werden im folgenden Verzeichnis gespeichert: **`<installation directory>`/var/default/log/**. Alle Instanzen nutzen dieselbe Protokolldatei (z. B. **web.log**).

Die Protokolle der anderen Module werden in einem Unterordner gespeichert, der nach der Instanz benannt ist. Jede Instanz verfügt über eigene Protokolldateien.

Protokolldateien für mehrere Instanzen sind in der folgenden Tabelle aufgeführt:

| Datei | Beschreibung |
|---|---|
| web.log | Web-Modulprotokolle (Client-Konsole, Berichte, SOAP-API usw.) |
| webmdl.log | Protokolle aus dem Umleitungsmodul |
| watchdog.log | Protokolle aus dem Adobe Campaign-Prozessüberwachungsmodul |
| trackinglogd.log | Trackinglogs          |

Die Protokolldateien der Mono-Instanz sind in der folgenden Tabelle aufgeführt:

| Datei | Beschreibung |
|---|---|
| mta.log | MTA-Modulprotokolle |
| mtachild.log | Verarbeitungsprotokolle des Nachrichtenversands |
| wfserver.log | Protokolle des Workflow-Server-Moduls |
| runwf.log | Ausführungsprotokolle des Workflows |
| inMail.log | Bounce-Message-Modulprotokoll |
| logins.log | Protokolliert alle Anmeldeversuche für Adobe Campaign (erfolgreich oder nicht) |

>[!IMPORTANT]
>
>Das **redir**-Verzeichnis existiert nur auf Weiterleitungs-Servern. Der Unterordner **url** enthält die Übereinstimmungen mit den umzuleitenden URLs, und der Unterordner **log** enthält die Trackinglogs. Zum Generieren von Trackinglogs muss **Modul** trackinglogd“ ausgeführt werden.

Zur Leistungsoptimierung und Speicheroptimierung wird die Datei logins.log in mehrere Dateien aufgeteilt, eine pro Tag (logins.yy-mm-dd.log), wobei maximal 365 Dateien beibehalten werden. Die Anzahl der Tage kann in der Datei serverConf.xml unter der Option syslogd (**maxNumberOfLoginsFiles**) geändert werden. Weitere Informationen finden Sie in der Dokumentation zur [Server-Konfigurationsdatei](../../installation/using/the-server-configuration-file.md#syslogd).

Standardmäßig sind die Protokolle auf zwei 10 MB-Dateien pro Modul und Instanz beschränkt. Die zweite Datei heißt: **`<modulename>`_2.log**. Die Größe der Protokolle ist daher auf 2,&#42; MB pro Modul und Instanz beschränkt.

Sie können jedoch größere Dateien beibehalten. Ändern Sie dazu den Wert der Einstellung **maxFileSizeMb=„10“** im Knoten **syslogd** der Datei **conf/serverConf.xml**. Dieser Wert stellt die maximale Größe in MB einer Protokolldatei dar.

Wenn Sie weitere Detaillierungsstufen in den Protokollen beibehalten möchten, können Sie die Adobe Campaign-Module mit dem Parameter **-verbose** starten:

**nlserver start `<MODULE>`@`<INSTANCE>` -verbose**

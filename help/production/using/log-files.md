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



Die Protokolldateien sind wie folgt organisiert:

![](assets/d_ncs_directory.png)

Jedes Modul **nlserver** generiert eine Protokolldatei, die im folgenden Verzeichnis gespeichert ist: **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

Das Modul **nlserver syslogd** speichert die Protokolle auf der Festplatte. Dieses Modul ähnelt dem Unix- **syslog-Daemon**, wurde jedoch für die Kompatibilität zwischen Unix und Windows angepasst. Die anderen Adobe Campaign-Module speichern ihre Protokolle nicht auf der Festplatte. Sie delegieren diese Aufgabe an das Modul **syslogd**, indem sie es UDP-Pakete senden.

Standardmäßig ist auf der Adobe Campaign-Plattform das Modul &quot;**syslogd**&quot; installiert. Es ist jedoch möglich, einen anderen &quot;**syslog Daemon**&quot; zu verwenden. Dieses Modul erstellt die Protokolldateien im Verzeichnis **log** .

Die Protokolle von Modulen mit mehreren Instanzen werden im folgenden Verzeichnis gespeichert: **`<installation directory>`/var/default/log/**. Dieselbe Protokolldatei wird von allen Instanzen freigegeben (z. B. **web.log**).

Die Protokolle der anderen Module werden in einem Unterordner gespeichert, der nach der Instanz benannt ist. Jede Instanz verfügt über eigene Protokolldateien.

Protokolldateien mit mehreren Instanzen sind in der folgenden Tabelle aufgeführt:

| Datei | Beschreibung |
|---|---|
| web.log | Webmodulprotokolle (Clientkonsole, Berichte, SOAP API usw.) |
| webmdl.log | Protokolle aus dem Umleitungsmodul |
| watchdog.log | Protokolle vom Adobe Campaign-Prozessüberwachungsmodul |
| trackinglogd.log | Trackinglogs          |

Die Protokolldateien der Mono-Instanz sind in der folgenden Tabelle aufgeführt:

| Datei | Beschreibung |
|---|---|
| mta.log | MTA-Modulprotokolle |
| mtachild.log | Verarbeitungslogs der Nachrichten |
| wfserver.log | Protokolle des Workflow-Server-Moduls |
| runwf.log | Workflow-Ausführungsprotokolle |
| inMail.log | Bounce-Message-Modulprotokoll |
| logins.log | Protokolliert alle Anmeldeversuche für Adobe Campaign (erfolgreich oder nicht) |

>[!IMPORTANT]
>
>Der Ordner &quot;**redir**&quot; ist nur auf Umleitungsservern vorhanden. Das Unterverzeichnis **url** enthält die Übereinstimmungen mit den umzuleitenden URLs und das Unterverzeichnis **log** enthält die Trackinglogs. Um Trackinglogs zu generieren, muss das Modul **trackinglogd** ausgeführt werden.

Zur Optimierung der Leistung und des Speicherplatzes wird die Datei &quot;login.log&quot;in mehrere Dateien aufgeteilt, wobei jeder Tag (login.yy-mm-dd.log) mit maximal 365 Dateien gespeichert wird. Die Anzahl der Tage kann in der Datei serverConf.xml unter syslogd geändert werden (**maxNumberOfLoginsFiles** Option). Weitere Informationen finden Sie in der Dokumentation zur [Server-Konfigurationsdatei](../../installation/using/the-server-configuration-file.md#syslogd).

Standardmäßig sind die Protokolle auf zwei 10 MB Dateien pro Modul und Instanz beschränkt. Die zweite Datei heißt: **`<modulename>`_2.log**. Die Größe der Protokolle ist daher auf 2&#42;10 MB pro Modul und Instanz beschränkt.

Sie können jedoch größere Dateien beibehalten. Um dies zu aktivieren, ändern Sie den Wert der Einstellung **maxFileSizeMb=&quot;10&quot;** im Knoten **syslogd** der Datei **conf/serverConf.xml** . Dieser Wert stellt die maximale Größe einer Protokolldatei in MB dar.

Wenn Sie weitere Detailstufen in den Protokollen beibehalten möchten, können Sie die Adobe Campaign-Module mit dem Parameter **-verbose** starten:

**nlserver start `<MODULE>`@`<INSTANCE>` -verbose**

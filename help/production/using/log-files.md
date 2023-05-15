---
product: campaign
title: Protokolldateien
description: Protokolldateien
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: c9d427da-6965-4945-90f0-d0770701d55e
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 2%

---

# Protokolldateien{#log-files}



Die Protokolldateien sind wie folgt organisiert:

![](assets/d_ncs_directory.png)

Jeder **nlserver** generiert eine Protokolldatei, die im folgenden Verzeichnis gespeichert ist: **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

Die **nlserver syslogd** speichert die Protokolle auf der Festplatte. Dieses Modul ähnelt dem Unix-Modul **syslog daemon**, wurde jedoch für die Kompatibilität zwischen Unix und Windows angepasst. Die anderen Adobe Campaign-Module speichern ihre Protokolle nicht auf der Festplatte. Sie delegieren diese Aufgabe an die **syslogd** -Modul durch Senden von UDP-Paketen.

Standardmäßig verfügt die Adobe Campaign-Plattform über die **syslogd** -Modul installiert ist, es jedoch möglich ist, ein anderes **syslog daemon**. Dieses Modul erstellt die Protokolldateien im **log** Verzeichnis.

Die Protokolle von Modulen mit mehreren Instanzen werden im folgenden Verzeichnis gespeichert: **`<installation directory>`/var/default/log/**. Dieselbe Protokolldatei wird von allen Instanzen (z. B. **web.log**).

Die Protokolle der anderen Module werden in einem Unterordner gespeichert, der nach der Instanz benannt ist. Jede Instanz verfügt über eigene Protokolldateien.

Protokolldateien mit mehreren Instanzen sind in der folgenden Tabelle aufgeführt:

| Datei | Beschreibung |
|---|---|
| web.log | Webmodulprotokolle (Clientkonsole, Berichte, SOAP-API usw.) |
| webmdl.log | Protokolle vom Umleitungsmodul |
| watchdog.log | Protokolle vom Adobe Campaign-Prozessüberwachungsmodul |
| trackinglogd.log | Trackinglogs          |

Die Protokolldateien der Mono-Instanz sind in der folgenden Tabelle aufgeführt:

| Datei | Beschreibung |
|---|---|
| mta.log | MTA-Modulprotokolle |
| mtachild.log | Verarbeitungslogs der Nachrichten |
| wfserver.log | Protokolle des Workflow-Servermoduls |
| runwf.log | Workflow-Ausführungsprotokolle |
| inMail.log | Bounce-Message-Modulprotokoll |
| logins.log | Protokolliert alle Anmeldeversuche für Adobe Campaign (erfolgreich oder nicht) |

>[!IMPORTANT]
>
>Die **redir** -Ordner existiert nur auf Umleitungsservern. Die **url** -Unterverzeichnis enthält die Übereinstimmungen mit den URLs, die umgeleitet werden sollen, und das -Unterverzeichnis **log** enthält die Trackinglogs. Um Trackinglogs zu generieren, muss die **trackinglogd** -Modul ausgeführt werden.

Zur Optimierung der Leistung und des Speicherplatzes wird die Datei &quot;login.log&quot;in mehrere Dateien aufgeteilt, wobei jeder Tag (login.yy-mm-dd.log) mit maximal 365 Dateien gespeichert wird. Die Anzahl der Tage kann in der Datei serverConf.xml unter syslogd (**maxNumberOfLoginsFiles** -Option). Weitere Informationen finden Sie in der Dokumentation unter [Serverkonfigurationsdatei](../../installation/using/the-server-configuration-file.md#syslogd).

Standardmäßig sind die Protokolle auf zwei 10 MB Dateien pro Modul und Instanz beschränkt. Die zweite Datei heißt: **`<modulename>`_2.log**. Die Größe der Logs ist daher auf 2 begrenzt.&#42;10 MB pro Modul und Instanz.

Sie können jedoch größere Dateien beibehalten. Um dies zu aktivieren, ändern Sie den Wert der **maxFileSizeMb=&quot;10&quot;** -Einstellung in **syslogd** Knoten der **conf/serverConf.xml** -Datei. Dieser Wert stellt die maximale Größe einer Protokolldatei in MB dar.

Wenn Sie weitere Details in den Protokollen beibehalten möchten, können Sie die Adobe Campaign-Module mit der **-verbose** Parameter:

**nlserver-Beginn `<MODULE>`@`<INSTANCE>` -verbose**

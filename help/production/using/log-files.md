---
solution: Campaign Classic
product: campaign
title: Protokolldateien
description: Protokolldateien
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 2%

---


# Protokolldateien{#log-files}

Die Protokolldateien sind wie folgt organisiert:

![](assets/d_ncs_directory.png)

Jedes **nlserver** -Modul generiert eine Protokolldatei, die im folgenden Verzeichnis gespeichert ist: **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

Das **nlserver syslogd** Modul speichert die Protokolle auf der Festplatte. Dieses Modul ähnelt dem Unix- **Syslog-Daemon**, wurde jedoch für die Kompatibilität zwischen Unix und Windows angepasst. Die anderen Adobe Campaign-Module speichern ihre Protokolle nicht auf der Festplatte. sie delegieren diese Aufgabe an das **syslogd** -Modul, indem sie es UDP-Pakete senden.

Standardmäßig ist auf der Adobe Campaign-Plattform das **syslogd** -Modul installiert, es ist jedoch möglich, einen anderen **syslog-Daemon** zu verwenden. Dieses Modul erstellt die Protokolldateien im **Protokollverzeichnis** .

Die Protokolle von Modulen mit mehreren Instanzen werden im folgenden Verzeichnis gespeichert: **`<installation directory>`/var/default/log/**. Dieselbe Protokolldatei wird von allen Instanzen freigegeben (z. B. **web.log**).

Die Protokolle der anderen Module werden in einem Unterordner gespeichert, der nach der Instanz benannt ist. Jede Instanz verfügt über eigene Protokolldateien.

Die Protokolldateien mit mehreren Instanzen sind in der folgenden Tabelle aufgeführt:

| Datei | Beschreibung  |
|---|---|
| web.log | Webmodulprotokolle (Client-Konsole, Berichte, SOAP-API usw.) |
| webmdl.log | Protokolle vom Umleitungsmodul |
| watchdog.log | Protokolle vom Adobe Campaign-Prozessüberwachungsmodul |
| trackinglogd.log | Trackinglogs     |

Die Protokolldateien der einzelnen Instanzen sind in der folgenden Tabelle aufgeführt:

| Datei | Beschreibung  |
|---|---|
| mta.log | mta-Modulprotokolle |
| mtachild.log | Meldungs-Versand-Verarbeitungsprotokolle |
| wfserver.log | Protokolle des Workflow-Servermoduls |
| runwf.log | Workflow-Ausführungsprotokolle |
| inMail.log | Protokoll des Abspann-E-Mail-Moduls |
| logins.log | Protokolliert alle Anmeldeversuche zum Adobe Campaign (Erfolg oder nicht) |

>[!IMPORTANT]
>
>Der Ordner **redir** existiert nur auf Umleitungsservern. Der Unterordner **url** enthält die Übereinstimmungen mit den URLs, die umgeleitet werden sollen, und das Unterverzeichnisprotokoll **enthält die Trackinglogs** . Um Trackinglogs zu generieren, muss das **trackinglogd** -Modul ausgeführt werden.

Zur Optimierung der Leistung und Datenspeicherung wird die Datei &quot;login.log&quot;jeden Tag in mehrere Dateien aufgeteilt (logins.yy-mm-dd.log), wobei maximal 365 Dateien beibehalten werden. Die Anzahl der Tage kann in der Datei &quot;serverConf.xml&quot;unter syslogd (Option **maxNumberOfLoginsFiles** ) geändert werden. Weitere Informationen finden Sie in der Dokumentation zur [Serverkonfigurationsdatei](../../installation/using/the-server-configuration-file.md#syslogd).

Standardmäßig sind die Protokolle auf zwei 10 MB Dateien pro Modul und pro Instanz beschränkt. Die zweite Datei heißt: **`<modulename>`_2.log**. Die Größe der Protokolle ist daher auf 2*10 MB pro Modul und pro Instanz begrenzt.

Sie können jedoch größere Dateien beibehalten. Um dies zu aktivieren, ändern Sie den Wert der Einstellung **maxFileSizeMb=&quot;10&quot;** im **syslogd** -Knoten der **Datei conf/serverConf.xml** . Dieser Wert gibt die maximale Größe einer Protokolldatei in MB an.

Wenn Sie weitere Detailstufen in den Protokollen beibehalten möchten, können Sie die Adobe Campaign-Module mit dem **-verbose** -Parameter Beginn ausführen:

**nlserver-Beginn `<MODULE>`@`<INSTANCE>` -verbose**

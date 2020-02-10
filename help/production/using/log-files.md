---
title: Protokolldateien
seo-title: Protokolldateien
description: Protokolldateien
seo-description: null
page-status-flag: never-activated
uuid: 266bc067-0218-4b3e-941c-dc5cd0b6a10d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: fac3e3ec-82a7-4087-ba88-2b28b0f69d1c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9f018df9a2f7516b92f1f25a757065ef268136a5

---


# Protokolldateien{#log-files}

Die Protokolldateien sind wie folgt organisiert:

![](assets/d_ncs_directory.png)

Jedes **nlserver** -Modul generiert eine Protokolldatei, die im folgenden Verzeichnis gespeichert ist: **`<installation directory>`/var/`<instance>`/log/`<module>`.log **.

Das **nlserver syslogd** Modul speichert die Protokolle auf der Festplatte. Dieses Modul ähnelt dem Unix- **Syslog-Daemon**, wurde jedoch für die Kompatibilität zwischen Unix und Windows angepasst. Die anderen Adobe Campaign-Module speichern ihre Protokolle nicht auf der Festplatte. Sie delegieren diese Aufgabe an das **syslogd** -Modul, indem sie es UDP-Pakete senden.

Standardmäßig ist auf der Adobe Campaign-Plattform das **syslogd** -Modul installiert, es ist jedoch möglich, einen anderen **syslog-Daemon** zu verwenden. Dieses Modul erstellt die Protokolldateien im **Protokollverzeichnis** .

Die Protokolle der Module mit mehreren Instanzen werden im folgenden Verzeichnis gespeichert: **`<installation directory>`/var/default/log/**. Dieselbe Protokolldatei wird von allen Instanzen freigegeben (z. B.**web.log **).

Die Protokolle der anderen Module werden in einem Unterordner gespeichert, der nach der Instanz benannt ist. Jede Instanz verfügt über eigene Protokolldateien.

Die Protokolldateien mit mehreren Instanzen sind in der folgenden Tabelle aufgeführt:

| Datei | Description |
|---|---|
| web.log | Webmodulprotokolle (Client-Konsole, Berichte, SOAP-API usw.) |
| webmdl.log | Protokolle vom Umleitungsmodul |
| watchdog.log | Protokolle vom Adobe Campaign-Prozessüberwachungsmodul |
| trackinglogd.log | Tracking logs |

Die Protokolldateien der einzelnen Instanzen sind in der folgenden Tabelle aufgeführt:

| Datei | Description |
|---|---|
| mta.log | mta-Modulprotokolle |
| mtachild.log | Verarbeitungsprotokolle zur Nachrichtenübermittlung |
| wfserver.log | Protokolle des Workflow-Servermoduls |
| runwf.log | Workflow-Ausführungsprotokolle |
| inMail.log | Protokoll des Abspann-Mail-Moduls |
| logins.log | Protokolliert alle Anmeldeversuche bei Adobe Campaign (Erfolg oder nicht) |

>[!CAUTION]
>
>Der Ordner **redir** existiert nur auf Umleitungsservern. Der Unterordner **url** enthält die Übereinstimmungen mit den URLs, die umgeleitet werden sollen, und das Unterverzeichnisprotokoll **enthält die Verfolgungsprotokolle** . Um Verfolgungsprotokolle zu generieren, muss das **trackinglogd** -Modul ausgeführt werden.

Zur Optimierung der Leistung und des Speichers wird die Datei &quot;login.log&quot;jeden Tag in mehrere Dateien aufgeteilt (logins.yy-mm-dd.log), wobei maximal 365 Dateien beibehalten werden. Die Anzahl der Tage kann in der Datei &quot;serverConf.xml&quot;unter syslogd (Option **maxNumberOfLoginsFiles** ) geändert werden. Weitere Informationen finden Sie in der Dokumentation zur [Serverkonfigurationsdatei](../../installation/using/the-server-configuration-file.md#syslogd).

Standardmäßig sind die Protokolle auf zwei 10 MB Dateien pro Modul und pro Instanz beschränkt. Die zweite Datei heißt: **`<modulename>`_2.log **. Die Größe der Protokolle ist daher auf 2*10 MB pro Modul und pro Instanz begrenzt.

Sie können jedoch größere Dateien beibehalten. Um dies zu aktivieren, ändern Sie den Wert der Einstellung **maxFileSizeMb=&quot;10&quot;** im Knoten **syslogd** der Datei **conf/serverConf.xml** . Dieser Wert gibt die maximale Größe einer Protokolldatei in MB an.

Wenn Sie weitere Details in den Protokollen beibehalten möchten, können Sie die Adobe Campaign-Module mit dem **-verbose** -Parameter starten:

**nlserver start`<MODULE>`@`<INSTANCE>`-verbose**

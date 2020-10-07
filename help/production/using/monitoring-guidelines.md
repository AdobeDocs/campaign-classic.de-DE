---
title: Richtlinien für das Monitoring
description: Entdecken Sie Richtlinien und Best Practices zur Überwachung von Kampagnen und Prozessen.
page-status-flag: never-activated
uuid: cf0d782d-47bf-40ae-ab6f-d1d47fa15792
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: introduction
discoiquuid: 8b33e6af-15c3-4b30-8ad6-d76a1f33be21
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 9%

---


# Richtlinien für das Monitoring {#monitoring-guidelines}

## Instanz-Monitoring-Dashboard {#instance-monitoring-dashboard}

Die Registerkarte **[!UICONTROL Überwachung]** , auf die von der Campaign Classic-Homepage aus zugegriffen werden kann, ist der Haupteinstiegspunkt, der Sie bei der Überwachung Ihrer Instanz unterstützt.

Es bietet ein Dashboard für das, was auf Ihrer Instanz geschieht: seinen Status (Build-Version, installierte Pakete usw.), Systemindikatoren, Protokolle, aktuell ausgeführte Workflows, Status der zuletzt gesendeten Versand usw.

Detaillierte Informationen finden Sie [hier](../../production/using/monitoring-processes.md).

![](assets/monitoring_tab.png)

## Monitoring Campaign Classic processes {#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">Überwachen der Instanz</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#moniroting-workflows">Workflows</a></p></td>
<td><img src="assets/do-not-localize/icon_send.svg" width="60px"><p><a href="#monitoring-deliveries">Beobachtung von Sendungen</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">Datenbank überwachen</a></p></td></tr>
</table>

Es stehen weitere Möglichkeiten zur Überwachung der verschiedenen Kampagnen zur Verfügung. Sie bieten verschiedene Möglichkeiten zur Überwachung Ihrer Instanzen, um sicherzustellen, dass Ihr System einwandfrei ist, und eventuell Probleme zu beheben, die beim Einrichten von Workflows, Senden von Versänden usw. auftreten können.

### Überwachen der Instanz {#monitoring-instance}

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**Automatische Überwachungstools**

Es stehen verschiedene automatische Methoden zur Verfügung. , um Sie bei der Überwachung Ihrer Instanz zu unterstützen. Sie können beispielsweise E-Mail-Berichte mit erkannten Anomalien einrichten, eine Liste von Indikatoren im XML-Format abrufen usw. [Klicken Sie hier](../../production/using/monitoring-processes.md#automatic-monitoring) für weitere Informationen.

**Audit-Protokoll**

Der Prüfpfad ermöglicht Ihnen die Visualisierung des vollständigen Verlaufs der Änderungen in Bezug auf Optionen, Workflows und Schema in Ihrer Instanz. [Klicken Sie hier](../../production/using/audit-trail.md) für weitere Informationen.

**Control Panel**

Über die Systemsteuerung können Sie mehrere Einstellungen Ihrer Instanz verwalten: URL-Berechtigungen verwalten, Instanzdetails wie die Build-Versionen Ihrer Server überprüfen usw. Außerdem können Sie damit den verfügbaren Speicherplatz auf den SFTP-Servern überwachen, die mit Ihrer Instanz verbunden sind. [Klicken Sie hier](https://docs.adobe.com/content/help/de-DE/control-panel/using/control-panel-home.html) für weitere Informationen.

>[!NOTE]
>
>Beachten Sie, dass die Systemsteuerung nur für Administratoren zugänglich ist und für alle Kunden mit Adobe Managed Services verfügbar ist.

### Überwachung von Workflows {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**Workflow-Heatmap**

Die Workflow HeatMap bietet eine visuelle Darstellung aller Workflows, die auf Ihrer Instanz ausgeführt werden. Dadurch können Sie die Belastung der Instanz einfach überwachen und Workflows entsprechend planen. [Klicken Sie hier](../../workflow/using/heatmap.md) für weitere Informationen.

**Audit-Protokoll**

Der Audit-Pfad ermöglicht Ihnen, alle Änderungen, die in Workflows vorgenommen wurden, sowie deren Status darzustellen. [Hier klicken](../../production/using/audit-trail.md).

**Workflows Fehlerbehebung**

Bei Problemen mit der Ausführung eines Workflows können spezifische Aktionen ausgeführt werden. [Klicken Sie hier](../../production/using/workflow-execution.md) für weitere Informationen

**Workflow-Statusüberwachung**

Zusätzlich zur Heatmap können Sie einen Workflow erstellen, mit dem Sie den Status einer Workflows überwachen und wiederkehrende Meldungen an die Aufsichtsbehörden senden können. [Klicken Sie hier](../../workflow/using/supervising-workflows.md) für weitere Informationen.

**Allgemeine Leitlinien**

Die Befolgung von Richtlinien und Best Practices bei der Verwendung von Workflows kann zur Verbesserung der Leistung beitragen. Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Bewährte Verfahren bei der Verwendung von Workflows](../../workflow/using/workflow-best-practices.md)
* [Ausführung des Workflows überwachen](../../workflow/using/monitoring-workflow-execution.md)

### Sendungen überwachen {#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**SMTP-Berichte**

SMTP-Berichte zeigen die Statistik des Versands und SMTP-Fehler nach Domäne an. [mehr dazu](../../production/using/monitoring-processes.md)

**Best Practices**

[Best Practices für das Senden und Entwerfen](../../delivery/using/delivery-best-practices.md) von Versänden können Ihnen dabei helfen, ihre Leistung zu verbessern.

**Versand zur Fehlerbehebung** können bei Problemen mit Versänden ausgeführt werden:
* [Probleme mit der Zustellbarkeit](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Probleme mit der Bildanzeige](../../production/using/image-display-issues.md)
* [Leistungsprobleme beim Versand](../../delivery/using/monitoring-a-delivery.md#performance_issues)
* [Probleme](../../production/using/temporary-files.md) mit temporären Dateien - nur *bei lokalen Hostingmodellen*

### Datenbank überwachen {#monitoring-database}

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**Datenbankbereinigungs-Workflow**

Mit dem Arbeitsablauf zur Datenbankbereinigung können Sie veraltete Daten aus Ihrer Datenbank löschen. Es wird empfohlen, exponentielles Wachstum der Datenbank zu vermeiden. [Klicken Sie hier](../../production/using/database-cleanup-workflow.md) für weitere Informationen.

**Fehlerbehebung bei der Datenbankleistung**

Bei Problemen mit Datenbankleistung können spezifische Aktionen ausgeführt werden. [Klicken Sie hier](../../production/using/database-performances.md) für weitere Informationen.

**Wartung der Datenbank**

*Nur lokale und hybride Hostingmodelle*

Es wird empfohlen, dass Sie die Datenbankwartung regelmäßig durchführen, um zu vermeiden, dass zu viel Speicherplatz auf der Festplatte benötigt wird, was sich auf den Datenbankzugriff auswirkt. [Klicken Sie hier](../../production/using/recommendations.md) für weitere Informationen.

**Sicherung und Wiederherstellung**

*Nur lokale und hybride Hostingmodelle*

Die Sicherung ist unverzichtbar, um zu vermeiden, dass Daten im Ereignis eines Problems (physisch oder systembezogen) auf einem Computer verloren gehen. [Klicken Sie hier](../../production/using/backup.md) für weitere Informationen. Das Wiederherstellungsverfahren wird in [diesem Abschnitt](../../production/using/restoration.md)beschrieben.

## Technische Grundsätze des Campaign Classic {#campaign-classic-technical-principles}

Technische Ressourcen finden Sie in der Dokumentation zum Campaign Classic. Wir empfehlen Ihnen, sich mit diesen Themen vertraut zu machen, bevor Sie einen technischen Vorgang an Ihrer Instanz durchführen.

**Hosting-Modelle und -Funktionen**

* [Campaign Classic-Hosting-Modelle](../../installation/using/hosting-models.md)
* [Hosting-Modellfunktionen](https://helpx.adobe.com/de/campaign/kb/acc-on-prem-vs-hosted.html)

**Serverkonfiguration**

*Nur lokale und hybride Hostingmodelle*

* [Erforderliche Serverkonfigurationen](../../installation/using/campaign-server-configuration.md)
* [Serverconf.xml-Dateikonfiguration](../../installation/using/the-server-configuration-file.md)
* [Serverkonfiguration für Auslieferbarkeit](../../installation/using/email-deliverability.md)
* [Befehlszeilen zum Erstellen einer Instanz und Deklarieren einer Datenbank](../../installation/using/command-lines.md)

**Allgemeine Grundsätze**

* [Campaign Classic-Architektur](../../production/using/general-architecture.md)
* [Campaign Classic-Module](../../production/using/operating-principle.md)
* [Campaign Classic-Optionen](../../installation/using/configuring-campaign-options.md)
* [So richten Sie den automatischen Systemstart von Modulen ein](../../production/using/administration.md)
* [Kampagne-Konfigurationsprinzip](../../production/using/configuration-principle.md)
* [Fehlerbehebungsverfahren](../../production/using/performance-and-throughput-issues.md)

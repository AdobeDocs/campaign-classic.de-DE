---
product: campaign
title: Richtlinien für das Überwachen
description: Entdecken Sie Richtlinien und Best Practices zur Überwachung von Campaign-Instanzen und -Prozessen
feature: Monitoring
exl-id: ca0c33c5-7350-462a-bc65-4cab51e529d9
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '744'
ht-degree: 26%

---

# Richtlinien für das Überwachen {#monitoring-guidelines}



## Instanz-Monitoring-Dashboard {#instance-monitoring-dashboard}

Die Registerkarte **[!UICONTROL Monitoring]**, auf die über die Campaign Classic-Homepage zugegriffen werden kann, ist der wichtigste Einstiegspunkt zur Überwachung Ihrer Instanz.

Er bietet ein Dashboard, in dem Sie sehen können, was in Ihrer Instanz passiert: Status (Build-Version, installierte Pakete usw.), Systemindikatoren, Protokolle, derzeit ausgeführte Workflows, Status der zuletzt gesendeten Sendungen usw.

Detaillierte Informationen finden Sie [hier](../../production/using/monitoring-processes.md).

![](assets/monitoring_tab.png)

## Überwachen von Campaign Classic-Prozessen {#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">Überwachen einer Instanz</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#monitoring-workflows">Überwachen von Workflows</a></p></td>
<td><img src="assets/do-not-localize/icon_send.svg" width="60px"><p><a href="#monitoring-deliveries">Überwachen von Sendungen</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">Überwachen der Datenbank</a></p></td></tr>
</table>

Es stehen zusätzliche Möglichkeiten zur Überwachung der verschiedenen Campaign-Prozesse zur Verfügung. Sie bieten verschiedene Möglichkeiten, Ihre Instanzen zu überwachen, um einen ordnungsgemäßen Zustand Ihres Systems sicherzustellen. Zusätzlich können Probleme behoben werden, die beim Einrichten von Workflows, beim Versenden von Sendungen usw. auftreten können.

### Instanz überwachen {#monitoring-instance}

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**Automatische Überwachungstools**

Es stehen mehrere automatische Methoden zur Verfügung. um Sie bei der Überwachung Ihrer Instanz zu unterstützen. Sie können beispielsweise E-Mail-Berichte mit erkannten Anomalien einrichten, eine Liste von Indikatoren im XML-Format abrufen usw. [Klicken Sie hier](../../production/using/monitoring-processes.md#automatic-monitoring), um weitere Informationen zu erhalten.

**Audit-Protokoll**

Das Audit-Protokoll ermöglicht es Ihnen, den vollständigen Verlauf der Änderungen in Bezug auf Optionen, Workflows und Schemata innerhalb Ihrer Instanz zu visualisieren. [Klicken Sie hier](../../production/using/audit-trail.md), um weitere Informationen zu erhalten.

**Control Panel**

Im Control Panel können Sie mehrere Einstellungen Ihrer Instanz verwalten: URL-Berechtigungen verwalten, Details Ihrer Instanz wie die Build-Versionen Ihrer Server überprüfen usw. Das Control Panel ermöglicht Ihnen auch, den verfügbaren Speicherplatz auf den SFTP-Servern zu überwachen, die mit Ihrer Instanz verbunden sind. [Klicken Sie hier](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=de), um weitere Informationen zu erhalten.

>[!NOTE]
>
>Das Control Panel steht allen Administratoren zur Verfügung. Die Schritte, um einem Benutzer Administratorzugriff zu gewähren, finden Sie auf [dieser Seite](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=de#discover-control-panel).
>
>Beachten Sie, dass Ihre Instanz auf AWS gehostet und mit dem [neuesten GA-Build](../../rn/using/rn-overview.md) aktualisiert werden muss. Erfahren Sie in [diesem Abschnitt](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version), wie Sie Ihre Version überprüfen. Um zu überprüfen, ob Ihre Instanz auf AWS gehostet wird, folgen Sie den Schritten auf [dieser Seite](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=de).

### Überwachung von Workflows {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**Workflow-Heatmap**

Die Workflow-Heatmap bietet eine visuelle Darstellung aller Workflows, die auf Ihrer Instanz ausgeführt werden. Damit können Sie die Auslastung der Instanz einfach überwachen und Workflows entsprechend planen. [Klicken Sie hier](../../workflow/using/heatmap.md), um weitere Informationen zu erhalten.

**Audit-Protokoll**

Das Audit-Protokoll ermöglicht es Ihnen, alle Änderungen, die an Workflows vorgenommen wurden, sowie ihren aktuellen Status zu visualisieren. [Hier klicken](../../production/using/audit-trail.md).

**Fehlerbehebung bei Workflows**

Bei Problemen mit der Ausführung eines Workflows können bestimmte Aktionen ausgeführt werden. [Hier klicken](../../production/using/workflow-execution.md) für weitere Informationen

**Workflow-Statusüberwachung**

Zusätzlich zur Heatmap können Sie einen Workflow erstellen, mit dem Sie den Status einer Reihe von Workflows überwachen und wiederkehrende Nachrichten an Supervisoren senden können. [Klicken Sie hier](../../workflow/using/supervising-workflows.md), um weitere Informationen zu erhalten.

**Allgemeine Richtlinien**

Die Befolgung von Richtlinien und Best Practices bei der Verwendung von Workflows kann die Leistung verbessern. Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Best Practices bei der Verwendung von Workflows](../../workflow/using/workflow-best-practices.md)
* [Ausführung des Workflows überwachen](../../workflow/using/monitoring-workflow-execution.md)

### Überwachen von Sendungen {#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**SMTP-Berichte**

SMTP-Berichte enthalten Versandstatistiken und SMTP-Fehler nach Domain. [Weitere Informationen](../../production/using/monitoring-processes.md)

**Best Practices**

[Best Practices für den Versand und die ](../../delivery/using/delivery-best-practices.md) von Sendungen können Sie bei der Verbesserung der Versandleistung unterstützen.

**Fehlerbehebung beim Versand**
Bei Problemen mit Sendungen können spezifische Aktionen durchgeführt werden:
* [Probleme mit der Zustellbarkeit](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Probleme mit der Bildanzeige](../../production/using/image-display-issues.md)
* [Performance-Probleme beim Versand](../../delivery/using/delivery-performances.md)
* [Probleme mit temporären Dateien](../../production/using/temporary-files.md) - *nur On-Premise-Hosting-Modelle*

### Überwachen der Datenbank {#monitoring-database}

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**Datenbankbereinigungs-Workflow**

Der Datenbankbereinigungs-Workflow ermöglicht es Ihnen, veraltete Daten aus Ihrer Datenbank zu löschen. Es wird empfohlen, ein exponentielles Wachstum der Datenbank zu vermeiden. [Klicken Sie hier](../../production/using/database-cleanup-workflow.md), um weitere Informationen zu erhalten.

**Fehlerbehebung bei der Datenbankleistung**

Bei Problemen mit der Datenbankleistung können bestimmte Aktionen ausgeführt werden. [Klicken Sie hier](../../production/using/database-performances.md), um weitere Informationen zu erhalten.

**Wartung der Datenbank**

*Nur On-Premise- und Hybrid-Hosting-Modelle*

Es wird empfohlen, die Datenbankwartung regelmäßig durchzuführen, um eine übermäßige Belastung des Festplattenspeichers zu vermeiden und so den Datenbankzugriff zu beeinträchtigen. [Klicken Sie hier](../../production/using/recommendations.md), um weitere Informationen zu erhalten.

**Sicherung und Wiederherstellung**

*Nur On-Premise- und Hybrid-Hosting-Modelle*

Eine Sicherung ist unerlässlich, um Datenverluste im Falle eines Problems (physisch oder systembedingt) auf einem Computer zu vermeiden. [Klicken Sie hier](../../production/using/backup.md) um weitere Informationen zu erhalten. Das Wiederherstellungsverfahren wird in [diesem Abschnitt](../../production/using/restoration.md) beschrieben.

## Technische Grundlagen des Campaign Classic {#campaign-classic-technical-principles}

Technische Ressourcen finden Sie in der Campaign Classic-Dokumentation. Es wird empfohlen, sich mit diesen Themen vertraut zu machen, bevor Sie einen technischen Vorgang auf Ihrer Instanz durchführen.

**Hosting-Modelle und -Funktionen**

* [Campaign Classic-Hosting-Modelle](../../installation/using/hosting-models.md)
* [Hosting-Modellfunktionen](../../installation/using/capability-matrix.md)

**Konfiguration des Servers**

*Nur On-Premise- und Hybrid-Hosting-Modelle*

* [Server-Konfigurationen](../../installation/using/configuring-campaign-server.md)
* [ServerConf.xml-Dateikonfiguration](../../installation/using/the-server-configuration-file.md)
* [Server-Konfiguration für Zustellbarkeit](../../installation/using/email-deliverability.md)
* [Befehlszeilen zum Erstellen einer Instanz und Deklarieren einer Datenbank](../../installation/using/command-lines.md)

**Allgemeine Grundsätze**

* [Campaign Classic-Architektur](../../production/using/general-architecture.md)
* [Campaign Classic-Module](../../production/using/operating-principle.md)
* [Campaign Classic-Optionen](../../installation/using/configuring-campaign-options.md)
* [Einrichten des automatischen Starts von Modulen](../../production/using/administration.md)
* [Konfigurationsprinzip der Kampagne](../../production/using/configuration-principle.md)
* [Verfahren zur Fehlerbehebung](../../production/using/performance-and-throughput-issues.md)

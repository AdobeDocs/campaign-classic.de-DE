---
product: campaign
title: Richtlinien für das Überwachen
description: Entdecken Sie Richtlinien und Best Practices zur Überwachung von Campaign-Instanzen und -Prozessen
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Monitoring
exl-id: ca0c33c5-7350-462a-bc65-4cab51e529d9
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 29%

---

# Richtlinien für das Überwachen {#monitoring-guidelines}



## Instanz-Monitoring-Dashboard {#instance-monitoring-dashboard}

Die **[!UICONTROL Überwachung]** tab, auf den über die Startseite von Campaign Classic zugegriffen werden kann, ist der Haupteinstiegspunkt, der Sie bei der Überwachung Ihrer Instanz unterstützt.

Es bietet ein Dashboard, was auf Ihrer Instanz geschieht: Status (Build-Version, installierte Pakete usw.), Systemindikatoren, Protokolle, derzeit ausgeführte Workflows, Status der letzten gesendeten Sendungen usw.

Detaillierte Informationen finden Sie [hier](../../production/using/monitoring-processes.md).

![](assets/monitoring_tab.png)

## Überwachen von Campaign Classic-Prozessen {#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">Überwachen einer Instanz</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#monitoring-workflows">Überwachen von Workflows</a></p></td>
<td><img src="assets/do-not-localize/icon_send.svg" width="60px"><p><a href="#monitoring-deliveries">Überwachen von Sendungen</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">Überwachen der Datenbank</a></p></td></tr>
</table>

Es stehen weitere Möglichkeiten zur Überwachung der verschiedenen Campaign-Prozesse zur Verfügung. Sie bieten verschiedene Möglichkeiten, Ihre Instanzen zu überwachen, um sicherzustellen, dass Ihr System einwandfrei funktioniert, und eventuell Probleme zu beheben, die beim Einrichten von Workflows, beim Versand usw. auftreten können.

### Überwachen Ihrer Instanz {#monitoring-instance}

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**Automatische Überwachungstools**

Es stehen verschiedene automatische Methoden zur Verfügung. , damit Sie Ihre Instanz überwachen können. Sie können beispielsweise E-Mail-Berichte mit erkannten Anomalien einrichten, eine Liste von Indikatoren im XML-Format abrufen usw. [Klicken Sie hier](../../production/using/monitoring-processes.md#automatic-monitoring), um weitere Informationen zu erhalten.

**Audit-Protokoll**

Im Audit-Protokoll können Sie den vollständigen Verlauf der Änderungen im Zusammenhang mit Optionen, Workflows und Schemata in Ihrer Instanz visualisieren. [Klicken Sie hier](../../production/using/audit-trail.md), um weitere Informationen zu erhalten.

**Control Panel**

Im Control Panel können Sie verschiedene Einstellungen Ihrer Instanz verwalten: URL-Berechtigungen verwalten, die Details Ihrer Instanz, wie die Build-Versionen Ihrer Server, überprüfen usw. Das Control Panel ermöglicht Ihnen auch, den verfügbaren Speicherplatz auf den SFTP-Servern zu überwachen, die mit Ihrer Instanz verbunden sind. [Klicken Sie hier](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=de), um weitere Informationen zu erhalten.

>[!NOTE]
>
>Das Control Panel steht allen Administratoren zur Verfügung. Die Schritte, um einem Benutzer Administratorzugriff zu gewähren, finden Sie auf [dieser Seite](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=de#discover-control-panel).
>
>Beachten Sie, dass Ihre Instanz auf AWS gehostet und mit dem [neuesten GA-Build](../../rn/using/rn-overview.md) aktualisiert werden muss. Erfahren Sie in [diesem Abschnitt](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version), wie Sie Ihre Version überprüfen. Um zu überprüfen, ob Ihre Instanz auf AWS gehostet wird, folgen Sie den Schritten auf [dieser Seite](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=de).

### Überwachung von Workflows {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**Workflow-Heatmap**

Die Workflow-Heatmap bietet eine visuelle Darstellung aller Workflows, die auf Ihrer Instanz ausgeführt werden. Dadurch können Sie die Auslastung der Instanz einfach überwachen und Workflows entsprechend planen. [Klicken Sie hier](../../workflow/using/heatmap.md), um weitere Informationen zu erhalten.

**Audit-Protokoll**

Im Audit-Protokoll können Sie alle in Workflows vorgenommenen Änderungen sowie deren aktuellen Status visualisieren. [Hier klicken](../../production/using/audit-trail.md).

**Fehlerbehebung bei Workflows**

Bei Problemen mit der Ausführung eines Workflows können spezifische Aktionen durchgeführt werden. [Klicken Sie hier](../../production/using/workflow-execution.md), um weitere Informationen zu erhalten

**Workflow-Statusüberwachung**

Zusätzlich zur Heatmap können Sie einen Workflow erstellen, mit dem Sie den Status einer Reihe von Workflows überwachen und wiederkehrende Nachrichten an Supervisoren senden können. [Klicken Sie hier](../../workflow/using/supervising-workflows.md), um weitere Informationen zu erhalten.

**Allgemeine Richtlinien**

Die Einhaltung von Richtlinien und Best Practices bei der Verwendung von Workflows kann zur Leistungsverbesserung beitragen. Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Best Practices bei der Verwendung von Workflows](../../workflow/using/workflow-best-practices.md)
* [Ausführung des Workflows überwachen](../../workflow/using/monitoring-workflow-execution.md)

### Überwachen von Sendungen {#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**SMTP-Berichte**

SMTP-Berichte zeigen Versandstatistiken und SMTP-Fehler nach Domain an. [Weitere Informationen](../../production/using/monitoring-processes.md)

**Best Practices**

[Best Practices für Versand und Entwurf](../../delivery/using/delivery-best-practices.md) kann Ihnen dabei helfen, ihre Leistung zu verbessern.

**Fehlerbehebung beim Versand**
Bei Problemen mit Sendungen können spezifische Aktionen durchgeführt werden:
* [Probleme mit der Zustellbarkeit](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Probleme mit der Bildanzeige](../../production/using/image-display-issues.md)
* [Leistungsprobleme beim Versand](../../delivery/using/delivery-performances.md)
* [Probleme mit temporären Dateien](../../production/using/temporary-files.md) - *Nur On-Premise-Hosting-Modelle*

### Überwachen der Datenbank {#monitoring-database}

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**Datenbankbereinigungs-Workflow**

Mit dem Datenbankbereinigungs-Workflow können Sie veraltete Daten aus Ihrer Datenbank löschen. Es wird empfohlen, das exponentielle Wachstum der Datenbank zu vermeiden. [Klicken Sie hier](../../production/using/database-cleanup-workflow.md), um weitere Informationen zu erhalten.

**Fehlerbehebung bei der Datenbankleistung**

Bei Problemen mit der Datenbankleistung können bestimmte Aktionen durchgeführt werden. [Klicken Sie hier](../../production/using/database-performances.md), um weitere Informationen zu erhalten.

**Wartung der Datenbank**

*Nur On-Premise- und Hybrid-Hosting-Modelle*

Es wird empfohlen, die Datenbankwartung regelmäßig durchzuführen, um zu vermeiden, dass der Speicherplatz überbeansprucht wird und sich dies auf den Datenbankzugriff auswirkt. [Klicken Sie hier](../../production/using/recommendations.md), um weitere Informationen zu erhalten.

**Sicherung und Wiederherstellung**

*Nur On-Premise- und Hybrid-Hosting-Modelle*

Eine Sicherung ist unerlässlich, um zu verhindern, dass Daten im Falle eines (physischen oder systembezogenen) Problems auf einem Computer verloren gehen. [Klicken Sie hier](../../production/using/backup.md), um weitere Informationen zu erhalten. Das Wiederherstellungsverfahren wird unter [diesem Abschnitt](../../production/using/restoration.md).

## Technische Campaign Classic {#campaign-classic-technical-principles}

Technische Ressourcen finden Sie in der Dokumentation zum Campaign Classic. Wir empfehlen Ihnen, sich mit diesen Themen vertraut zu machen, bevor Sie einen technischen Vorgang auf Ihrer Instanz durchführen.

**Hosting-Modelle und -Funktionen**

* [Campaign Classic-Hosting-Modelle](../../installation/using/hosting-models.md)
* [Hosting-Modellfunktionen](../../installation/using/capability-matrix.md)

**Konfiguration des Servers**

*Nur On-Premise- und Hybrid-Hosting-Modelle*

* [Serverkonfigurationen](../../installation/using/configuring-campaign-server.md)
* [Dateikonfiguration für Serverconf.xml](../../installation/using/the-server-configuration-file.md)
* [Serverkonfiguration für Zustellbarkeit](../../installation/using/email-deliverability.md)
* [Befehlszeilen zum Erstellen einer Instanz und zum Deklarieren einer Datenbank](../../installation/using/command-lines.md)

**Allgemeine Grundsätze**

* [Campaign Classic-Architektur](../../production/using/general-architecture.md)
* [Campaign Classic-Module](../../production/using/operating-principle.md)
* [Campaign Classic-Optionen](../../installation/using/configuring-campaign-options.md)
* [So richten Sie den automatischen Start von Modulen ein](../../production/using/administration.md)
* [Campaign-Konfigurationsprinzip](../../production/using/configuration-principle.md)
* [Fehlerbehebungsverfahren](../../production/using/performance-and-throughput-issues.md)

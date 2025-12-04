---
product: campaign
title: Erste Schritte bei der Überwachung eines Versands
description: Erfahren Sie mehr über die Funktionen zur Überwachung eines Versands in Campaign Classic
feature: Monitoring, Deliverability
role: User
exl-id: 9ce11da0-e37b-459e-8ec7-d2bddf59bdf7
source-git-commit: e60a8391416bc9899548971bddb61705467a80e5
workflow-type: tm+mt
source-wordcount: '835'
ht-degree: 64%

---

# Erste Schritte bei der Überwachung eines Versands {#about-delivery-monitoring}

>[!IMPORTANT]
>
>Auf dieser Seite werden **Campaign Classic v7-spezifische Überwachungsfunktionen** Hybrid- und On-Premise-Bereitstellungen dokumentiert.

## Überwachungsfunktionen

### Versandverfolgung {#monitoring-deliveries}

**Bei Hybrid-/On-Premise-Bereitstellungen** Campaign Classic v7 ist eine zusätzliche Überwachung der Serverressourcen und der MTA-Konfiguration (Mail Transfer Agent) erforderlich.

#### Fehlerbehebung bei ausstehenden Sendungen {#pending-deliveries}

Was passiert, wenn die Nachrichten nicht gesendet werden und ihr Status weiterhin **Ausstehend** lautet?

* Der Prozess wartet auf die Verfügbarkeit von Ressourcen. Möglicherweise wurde der MTA noch nicht gestartet.
Prüfen Sie, ob Ihre mta@instance-Module auf den MTA-Servern gestartet wurden. Starten Sie sie gegebenenfalls. [Weitere Informationen](../../production/using/administration.md).

* Möglicherweise wird für den Versand eine Affinität verwendet, die in der Sendeinstanz noch nicht konfiguriert wurde.
Tipp: Prüfen Sie die Konfiguration der Traffic-Verwaltung (IP-Affinität). Weiterführende Informationen dazu finden Sie im Abschnitt Ausgehenden SMTP-Traffic steuern.

>[!NOTE]
>
>Diese Schritte können nur von einem erfahrenen Benutzer in On-Premise-Installationen ausgeführt werden.

### Zustellbarkeits-Monitoring {#deliverability-monitoring}

#### Installation des Zustellbarkeitspakets {#deliverability-package}

Diese Funktion ist über ein dediziertes Package in Adobe Campaign verfügbar. Damit Sie es verwenden können, muss dieses Package installiert sein. Starten Sie nach Abschluss des Vorgangs den Server neu, damit das Package berücksichtigt wird.

* Für gehostete und hybride Clients wird das **Zustellbarkeits-Monitoring** auf Ihrer Instanz vom technischen Support und von Beratern von Adobe konfiguriert. Weiterführende Informationen dazu erhalten Sie von Ihrem Adobe-Kundenbetreuer.

* Bei On-Premise-Installationen müssen Sie das Package **[!UICONTROL Zustellbarkeits-Monitoring (Email Deliverability)]** über das Menü **[!UICONTROL Tools]** > **[!UICONTROL Erweitert]** > **[!UICONTROL Package-Import]** installieren. Weitere Informationen hierzu finden Sie unter [Installieren von Campaign Classic-Standardpaketen](../../installation/using/installing-campaign-standard-packages.md).

#### Zustellbarkeits-Workflow {#deliverability-workflow}

In Adobe Campaign Classic wird das **Zustellbarkeits-Monitoring** über den Workflow **[!UICONTROL Zustellbarkeit]** verwaltet. Er wird standardmäßig auf allen Instanzen installiert und ermöglicht es Ihnen, die Liste der Regeln für die Bounce-Message-Qualifizierung, die Liste der Domains und die Liste der MXs zu initialisieren. Sobald das Package **[!UICONTROL Zustellbarkeits-Monitoring (Email Deliverability)]** installiert ist, wird dieser Workflow nächtlich ausgeführt, um die Regelliste regelmäßig zu aktualisieren und die Zustellbarkeit der Plattform aktiv zu verwalten.

**Das Zustellbarkeitspaket bietet Ihnen Zugriff auf:**

* Den [Inbox Rendering-Bericht](inbox-rendering.md), mit dem Sie Ihre Nachrichten auf gängigen E-Mail-Clients als Vorschau anzeigen können, um Inhalte und Reputation zu überprüfen.
* Übersicht über die Nachrichtenqualität (Zustellung in der Inbox, Spam).

#### Monitoring-Tools {#monitoring-tools}

**Bei On-Premise** Installationen können Sie die folgenden Überwachungs-Tools verwenden:

* Der **[!UICONTROL Versanddurchsatz]**-Bericht bietet einen Überblick über den Durchsatz der gesamten Plattform für einen bestimmten Zeitraum. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../reporting/using/global-reports.md#delivery-throughput).
* Bei jedem Versand wird ein Bericht mit Versandstatistiken für die verschiedenen Internet-Dienstanbieter (ISPs) erstellt. Es werden verschiedene Datenqualitäts- und Reputationsmetriken angezeigt, die sich auf die Zustellbarkeit auswirken können, einschließlich der folgenden Zahlen:
   * **[!UICONTROL Hardbounces]** geben Auskunft über die Datenqualität. Diese Zahl sollte unter 2 % liegen.
   * **[!UICONTROL Softbounces]** geben Auskunft über die Reputation. Diese Zahl sollte bei keinem ISP über 10 % liegen.

  Lesen Sie diesbezüglich auch den Abschnitt [Versandstatistiken](../../reporting/using/global-reports.md#delivery-statistics).

#### Richtlinien für das Überwachen {#monitoring-guidelines}

**Für On-Premise** Installationen finden Sie hier einige zusätzliche Richtlinien zur Überwachung der Zustellbarkeit:

* Prüfen Sie regelmäßig den [Versanddurchsatz](../../reporting/using/global-reports.md#delivery-throughput) für die gesamte Plattform, um festzustellen, ob er der ursprünglichen Einstellung entspricht.
* Achten Sie darauf, dass [weitere Zustellversuche](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) in den Versandvorlagen korrekt eingerichtet sind (30 Minuten für das Versuchsintervall und mehr als 20 weitere Versuche).
* Prüfen Sie regelmäßig, ob das [Bounce](understanding-delivery-failures.md#bounce-mail-management)-Postfach zugänglich ist, und sorgen Sie dafür, dass die Gültigkeit des Kontos nicht abläuft.
* Prüfen Sie, ob die einzelnen Versanddurchsätze (über das [ Versand-Dashboard](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} abrufbar) der Gültigkeit des Versandinhalts entsprechen (&quot;Flash Sales&quot; zum Beispiel sollten innerhalb von Minuten, nicht von Tagen zugestellt werden).
* Wenn der Versand in Schüben erfolgt, stellen Sie sicher, dass genügend Zeit vorhanden ist, damit ein Schub fertiggestellt werden kann, bevor der nächste beginnt.
* Prüfen Sie, ob die Anzahl der Fehler und der neuen [Quarantänen](understanding-quarantine-management.md) der anderer Sendungen entspricht.
* Prüfen Sie in den [Versandlogs](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard#delivery-logs-and-history){target="_blank"} sorgfältig die Art der hervorgehobenen Fehler (Blockierungsliste, DNS-Probleme, Anti-Spam-Regeln usw.).

### Fehlerbehebung {#delivery-troubleshooting}

Bei Problemen mit Sendungen in (Hybrid-/On-Premise **-Bereitstellungen können spezifische Aktionen** werden:

* [Probleme mit der Zustellbarkeit](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Probleme mit der Bildanzeige](../../production/using/image-display-issues.md)
* [Performance-Probleme beim Versand](delivery-performance-troubleshooting.md)
* [Probleme mit temporären Dateien](../../production/using/temporary-files.md) – *nur On-Premise-Kunden*

## Sendungen überwachen

Die folgenden Ressourcen helfen Ihnen bei der Überwachung und Verfolgung der Versandleistung in Campaign Classic v7:

### Zugriff auf das Versand-Dashboard

Erfahren Sie, wie Sie auf Versandlisten zugreifen und das Versand-Dashboard verwenden können, um Ihre Versandaktivität zu überwachen:

* [Überwachen von Sendungen in der Campaign](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}-Benutzeroberfläche (Dokumentation zu Campaign v8 - gilt für v7 und v8)
* [Versandstatus](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} (Dokumentation zu Campaign v8)
* [Erweitert: Versandlogs anpassen](customize-delivery-logs.md) (nur Hybrid/On-Premise - Schemaerweiterung v7)

### Nachverfolgen von Nachrichteninteraktionen

Öffnungen, Klicks und Empfängerinteraktionen mit Ihren Sendungen verfolgen:

* [Dokumentation zum Nachrichten-Tracking](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking){target="_blank"} (Campaign v8-Dokumentation - gilt für v7 und v8)
* [Konfigurieren getrackter Links](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracked-links){target="_blank"} (Dokumentation zu Campaign v8)
* [Zugriff auf Trackinglogs](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking-logs){target="_blank"} (Dokumentation zu Campaign v8)

### Versandleistung optimieren

Best Practices und Fehlerbehebung bei Leistungsproblemen des Versands:

* [Best Practices für den Versand](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (Dokumentation zu Campaign v8 - gilt für v7 und v8)
* [Versandleistung und Fehlerbehebung](delivery-performance-troubleshooting.md) (Hybrid-/On-Premise-spezifische Konfigurationen für v7)

### Fehler und Quarantänen verstehen

Versandfehler, Bounce Messages und Quarantäneadressen verwalten:

* [Fehlgeschlagene Sendungen analysieren](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (Campaign v8-Dokumentation - umfassende Anleitung für v7 und v8)
* [Quarantäneverwaltung](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (Campaign v8-Dokumentation - umfassendes Handbuch für v7 und v8)
* [Versandfehler und Quarantänekonfiguration](delivery-failures-quarantine.md) (Hybrid-/On-Premise-spezifische Konfigurationen von v7)

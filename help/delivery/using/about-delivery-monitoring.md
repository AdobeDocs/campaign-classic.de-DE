---
product: campaign
title: Erste Schritte bei der Überwachung eines Versands
description: Erfahren Sie mehr über die Funktionen zur Überwachung eines Versands in Campaign Classic
feature: Monitoring, Deliverability
role: User
exl-id: 9ce11da0-e37b-459e-8ec7-d2bddf59bdf7
TQID: https://experienceleague.adobe.com/IRAgAQvquHFcfGDRU9Sof8NpSn3khyRRPOdpIRKUOzg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: b4dd41a7-ccf8-4e9d-918e-acaab534a307
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 906
ht-degree: 97%

---

# Erste Schritte bei der Überwachung eines Versands {#about-delivery-monitoring}

>[!IMPORTANT]
>
>Auf dieser Seite werden **Campaign Classic v7-spezifische Monitoring-Funktionen** für Hybrid- und On-Premise-Bereitstellungen dokumentiert.

## Monitoring-Funktionen

### Versand-Monitoring {#monitoring-deliveries}

**Bei Hybrid-/On-Premise-Bereitstellungen von Campaign Classic v7** ist ein zusätzliches Monitoring der Server-Ressourcen und der MTA-Konfiguration (Mail Transfer Agent) erforderlich.

#### Fehlerbehebung bei ausstehenden Sendungen {#pending-deliveries}

Was passiert, wenn die Nachrichten nicht gesendet werden und ihr Status weiterhin **Ausstehend** lautet?

* Der Ausführungsprozess wartet auf die Verfügbarkeit einiger Ressourcen. Der MTA wurde möglicherweise noch nicht gestartet.
Vergewissern Sie sich, dass Ihre mta@instance Module auf Ihren MTA-Servern gestartet sind, und starten Sie das MTA Modul, falls erforderlich. [Weitere Informationen](../../production/using/administration.md).

* Der Versand verwendet möglicherweise eine Affinität, die auf der Versandinstanz nicht konfiguriert wurde.
Tipp: Überprüfen Sie die Konfiguration der Traffic-Verwaltung (IP-Affinität). Weitere Informationen hierzu finden Sie unter Steuern des ausgehenden SMTP-Traffics.

>[!NOTE]
>
>Diese Schritte können nur von erfahrenen Benutzerinnen und Benutzern bei On-Premise-Installationen durchgeführt werden.

### Zustellbarkeits-Monitoring {#deliverability-monitoring}

#### Installation des Zustellbarkeitspakets {#deliverability-package}

Diese Funktion ist über ein dediziertes Package in Adobe Campaign verfügbar. Damit Sie es verwenden können, muss dieses Package installiert sein. Starten Sie nach Abschluss des Vorgangs den Server neu, damit das Package berücksichtigt wird.

* Für gehostete und hybride Clients wird das **Zustellbarkeits-Monitoring** auf Ihrer Instanz vom technischen Support und von Beratern von Adobe konfiguriert. Weiterführende Informationen dazu erhalten Sie von Ihrem Adobe-Kundenbetreuer.

* Bei On-Premise-Installationen müssen Sie das Package **[!UICONTROL Zustellbarkeits-Monitoring (Email Deliverability)]** über das Menü **[!UICONTROL Tools]** > **[!UICONTROL Erweitert]** > **[!UICONTROL Package-Import]** installieren. Weitere Informationen hierzu finden Sie unter [Installieren von Campaign Classic-Standardpaketen](../../installation/using/installing-campaign-standard-packages.md).

#### Zustellbarkeits-Workflow {#deliverability-workflow}

In Adobe Campaign Classic wird das **Zustellbarkeits-Monitoring** über den Workflow **[!UICONTROL Zustellbarkeit]** verwaltet. Er wird standardmäßig auf allen Instanzen installiert und ermöglicht es Ihnen, die Liste der Regeln für die Bounce-Message-Qualifizierung, die Liste der Domains und die Liste der MXs zu initialisieren. Sobald das Package **[!UICONTROL Zustellbarkeits-Monitoring (Email Deliverability)]** installiert ist, wird dieser Workflow nächtlich ausgeführt, um die Regelliste regelmäßig zu aktualisieren und die Zustellbarkeit der Plattform aktiv zu verwalten.

**Das Zustellbarkeitspaket ermöglicht Ihnen Zugriff auf:**

* Den [Inbox Rendering-Bericht](inbox-rendering.md), mit dem Sie Ihre Nachrichten auf gängigen E-Mail-Clients als Vorschau anzeigen können, um Inhalte und Reputation zu überprüfen.
* Übersicht über die Nachrichtenqualität (Zustellung in der Inbox, Spam).

#### Monitoring-Tools {#monitoring-tools}

**Bei On-Premise-Installationen** können Sie die folgenden Monitoring-Tools verwenden:

* Der **[!UICONTROL Versanddurchsatz]**-Bericht bietet einen Überblick über den Durchsatz der gesamten Plattform für einen bestimmten Zeitraum. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../reporting/using/global-reports.md#delivery-throughput).
* Bei jedem Versand wird ein Bericht mit Versandstatistiken für die verschiedenen Internet-Dienstanbieter (ISPs) erstellt. Es werden verschiedene Datenqualitäts- und Reputationsmetriken angezeigt, die sich auf die Zustellbarkeit auswirken können, einschließlich der folgenden Zahlen:
   * **[!UICONTROL Hardbounces]** geben Auskunft über die Datenqualität. Diese Zahl sollte unter 2 % liegen.
   * **[!UICONTROL Softbounces]** geben Auskunft über die Reputation. Diese Zahl sollte bei keinem ISP über 10 % liegen.

  Lesen Sie diesbezüglich auch den Abschnitt [Versandstatistiken](../../reporting/using/global-reports.md#delivery-statistics).

#### Richtlinien für das Überwachen {#monitoring-guidelines}

**Für On-Premise-Installationen** finden Sie hier einige zusätzliche Richtlinien zum Monitoring der Zustellbarkeit:

* Prüfen Sie regelmäßig den [Versanddurchsatz](../../reporting/using/global-reports.md#delivery-throughput) für die gesamte Plattform, um festzustellen, ob er der ursprünglichen Einstellung entspricht.
* Achten Sie darauf, dass [weitere Zustellversuche](delivery-failures-quarantine.md#retries-after-a-delivery-temporary-failure) in den Versandvorlagen korrekt eingerichtet sind (30 Minuten für das Versuchsintervall und mehr als 20 weitere Versuche).
* Prüfen Sie regelmäßig, ob das [Bounce](delivery-failures-quarantine.md#bounce-mail-management)-Postfach zugänglich ist, und sorgen Sie dafür, dass die Gültigkeit des Kontos nicht abläuft.
* Prüfen Sie, ob die einzelnen Versanddurchsätze (über das [&#x200B; Versand-Dashboard](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} abrufbar) der Gültigkeit des Versandinhalts entsprechen (&quot;Flash Sales&quot; zum Beispiel sollten innerhalb von Minuten, nicht von Tagen zugestellt werden).
* Wenn der Versand in Schüben erfolgt, stellen Sie sicher, dass genügend Zeit vorhanden ist, damit ein Schub fertiggestellt werden kann, bevor der nächste beginnt.
* Prüfen Sie, ob die Anzahl der Fehler und der neuen [Quarantänen](delivery-failures-quarantine.md) der anderer Sendungen entspricht.
* Prüfen Sie in den [Versandlogs](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/delivery-dashboard#delivery-logs-and-history){target="_blank"} sorgfältig die Art der hervorgehobenen Fehler (Blockierungsliste, DNS-Probleme, Anti-Spam-Regeln usw.).

### Fehlerbehebung {#delivery-troubleshooting}

Bei Problemen mit Sendungen in **Hybrid-/On-Premise-Bereitstellungen** können spezifische Aktionen durchgeführt werden:

* [Probleme mit der Zustellbarkeit](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Probleme mit der Bildanzeige](../../production/using/image-display-issues.md)
* [Performance-Probleme beim Versand](delivery-performance-troubleshooting.md)
* [Probleme mit temporären Dateien](../../production/using/temporary-files.md) – *nur On-Premise-Kunden*

## Überwachen von Sendungen

Die folgenden Ressourcen helfen Ihnen beim Monitoring und der Nachverfolgung der Versandleistung in Campaign Classic v7:

### Zugreifen auf das Versand-Dashboard

Erfahren Sie, wie Sie auf Versandlisten zugreifen und das Versand-Dashboard zum Monitoring der Versandaktivität verwenden können:

* [Monitoring von Sendungen in der Campaign-Benutzeroberfläche](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (Dokumentation zu Campaign v8 – gilt für v7 und v8)
* [Versandstatus](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} (Dokumentation zu Campaign v8)
* [Fortgeschritten: Anpassen von Versandlogs](customize-delivery-logs.md) (nur v7 Hybrid/On-Premise – Schemaerweiterung)

### Nachverfolgen von Nachrichteninteraktionen

Verfolgen von Öffnungen, Klicks und Empfängerinteraktionen mit Ihren Sendungen:

* [Dokumentation zum Nachrichten-Tracking](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/analytics/tracking/tracking){target="_blank"} (Dokumentation zu Campaign v8 – gilt für v7 und v8)
* [Konfigurieren nachverfolgter Links](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/analytics/tracking/tracked-links){target="_blank"} (Dokumentation zu Campaign v8)
* [Zugreifen auf Trackinglogs](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/analytics/tracking/tracking-logs){target="_blank"} (Dokumentation zu Campaign v8)

### Optimieren der Versandleistung

Best Practices und Fehlerbehebung bei Problemen mit der Versandleistung:

* [Best Practices für den Versand](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (Dokumentation zu Campaign v8 – gilt für v7 und v8)
* [Versandleistung und Fehlerbehebung](delivery-performance-troubleshooting.md) (spezifische Konfigurationen für v7 Hybrid/On-Premise)

### Informationen zu Fehlern und Quarantänen

Verwalten von Versandfehlern, Bounce-E-Mails und Adressen in Quarantäne:

* [Informationen zu Versandfehlern](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (Dokumentation zu Campaign v8 – umfassende Anleitung für v7 und v8)
* [Quarantäneverwaltung](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (Dokumentation zu Campaign v8 – umfassende Anleitung für v7 und v8)
* [Versandfehler und Quarantänekonfiguration](delivery-failures-quarantine.md) (spezifische Konfigurationen für v7 Hybrid/On-Premise)

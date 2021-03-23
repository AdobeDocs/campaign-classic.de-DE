---
solution: Campaign Classic
product: campaign
title: Monitoring der Zustellbarkeit in Adobe Campaign Classic
description: Erfahren Sie mehr über Tools und Richtlinien zum Monitoring der Zustellbarkeit in Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 5d1a653a9a164c34bb70efcc86ff2d7bdf1130a2
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 88%

---


# Zustellbarkeit überwachen{#monitoring-deliverability}

Im Folgenden finden Sie Informationen zu den verschiedenen Überwachungswerkzeugen von Adobe Campaign sowie einige zusätzliche Richtlinien zur Nutzung der von Adobe Campaign angebotenen Funktionen zur Überwachung der Lieferbarkeit Ihrer Plattform.

## Zustellbarkeits-Monitoring {#configuration}

Diese Funktion ist über ein dediziertes Package in Adobe Campaign verfügbar. Damit Sie es verwenden können, muss dieses Package installiert sein. Starten Sie nach Abschluss des Vorgangs den Server neu, damit das Package berücksichtigt wird.
* Für gehostete und hybride Clients wird das **Zustellbarkeits-Monitoring** auf Ihrer Instanz vom technischen Support und von Beratern von Adobe konfiguriert. Weiterführende Informationen dazu erhalten Sie von Ihrem Adobe-Kundenbetreuer.

* Bei On-Premise-Installationen müssen Sie das Package **[!UICONTROL Zustellbarkeits-Monitoring (Email Deliverability)]** über das Menü **[!UICONTROL Tools]** > **[!UICONTROL Erweitert]** > **[!UICONTROL Package-Import]** installieren. Weitere Informationen hierzu finden Sie unter [Installieren von nativen Campaign Classic-Packages](../../installation/using/installing-campaign-standard-packages.md).

In Adobe Campaign Classic wird das **Zustellbarkeits-Monitoring** über den Workflow **[!UICONTROL Zustellbarkeit]** verwaltet. Er wird standardmäßig auf allen Instanzen installiert und ermöglicht es Ihnen, die Liste der Regeln für die Bounce-Message-Qualifizierung, die Liste der Domains und die Liste der MXs zu initialisieren. Sobald das Package **[!UICONTROL Zustellbarkeits-Monitoring (Email Deliverability)]** installiert ist, wird dieser Workflow nächtlich ausgeführt, um die Regelliste regelmäßig zu aktualisieren und die Zustellbarkeit der Plattform aktiv zu verwalten.

Das Zustellbarkeits-Package ermöglicht Ihnen Zugriff auf:

* Den [Inbox Rendering-Bericht](../../delivery/using/inbox-rendering.md), mit dem Sie Ihre Nachrichten auf gängigen E-Mail-Clients als Vorschau anzeigen können, um Inhalte und Reputation zu überprüfen.
* Übersicht über die Nachrichtenqualität (Zustellung in der Inbox, Spam).

## Monitoring-Tools {#monitoring-tools}

Sie können auch die folgenden Tools verwenden:

* Der **[!UICONTROL Versanddurchsatz]**-Bericht bietet einen Überblick über den Durchsatz der gesamten Plattform für einen bestimmten Zeitraum. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../reporting/using/global-reports.md#delivery-throughput).
* Bei jedem Versand wird ein Bericht mit Versandstatistiken für die verschiedenen Internet-Dienstanbieter (ISPs) erstellt. Es werden verschiedene Datenqualitäts- und Reputationsmetriken angezeigt, die sich auf die Zustellbarkeit auswirken können, einschließlich der folgenden Zahlen:
   * **[!UICONTROL Hardbounces]** geben Auskunft über die Datenqualität. Diese Zahl sollte unter 2 % liegen.
   * **[!UICONTROL Softbounces]** geben Auskunft über die Reputation. Diese Zahl sollte bei keinem ISP über 10 % liegen.

   Lesen Sie diesbezüglich auch den Abschnitt [Versandstatistiken](../../reporting/using/global-reports.md#delivery-statistics).
* Allgemein bietet Ihnen das [Versand-Dashboard](../../delivery/using/about-delivery-monitoring.md) Zugriff auf:
   * die [Versandzusammenfassung](../../delivery/using/delivery-dashboard.md#delivery-summary), die die Details des Versands und die Anzahl der zu sendenden, der verarbeiteten und der erfolgreich gesendeten Nachrichten anzeigt;
   * die [Versandlogs und den Versandverlauf](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history), die zeigen, welche Zielgruppe ausgeschlossen wurde und warum;
   * die [Trackinglogs](../../delivery/using/delivery-dashboard.md#tracking-logs), die Tracking-Daten wie Öffnungen und Klicks anzeigen.

## Richtlinien für das Monitoring {#monitoring-guidelines}

Im Folgenden finden Sie einige zusätzliche Richtlinien zum Zustellbarkeits-Monitoring:

* Prüfen Sie regelmäßig den [Versanddurchsatz](../../reporting/using/global-reports.md#delivery-throughput) für die gesamte Plattform, um festzustellen, ob er der ursprünglichen Einstellung entspricht.
* Achten Sie darauf, dass [weitere Zustellversuche](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) in den Versandvorlagen korrekt eingerichtet sind (30 Minuten für das Versuchsintervall und mehr als 20 weitere Versuche).
* Prüfen Sie regelmäßig, ob das [Bounce](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management)-Postfach zugänglich ist, und sorgen Sie dafür, dass die Gültigkeit des Kontos nicht abläuft.
* Überprüfen Sie den Durchsatz jedes Versands, der über das [Versand-Dashboard](../../delivery/using/delivery-dashboard.md) erreichbar ist, um sicherzustellen, dass er mit der Gültigkeit des Versand-Inhalts (z. B. &#39;Flash-Verkäufe&#39; sollten in Minuten und nicht in Tagen ausgeliefert werden.
* Wenn der Versand in [Schüben](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves) erfolgt, stellen Sie sicher, dass genügend Zeit vorhanden ist, damit ein Schub fertiggestellt werden kann, bevor der nächste beginnt.
* Prüfen Sie, ob die Anzahl der Fehler und der neuen [Quarantänen](../../delivery/using/understanding-quarantine-management.md) der anderer Sendungen entspricht.
* Prüfen Sie in den [Versandlogs](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history) sorgfältig die Art der hervorgehobenen Fehler (Blockierungsliste, DNS-Probleme, Anti-Spam-Regeln usw.).

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->

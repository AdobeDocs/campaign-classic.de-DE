---
solution: Campaign Classic
product: campaign
title: Monitoring der Zustellbarkeit in Adobe Campaign Classic
description: Erfahren Sie mehr über Tools und Richtlinien zum Monitoring der Zustellbarkeit in Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: fa5679d91808edb8e3916d5f0e0f54c73198e934
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 100%

---


# Zustellbarkeit überwachen{#monitoring-deliverability}

Nachstehend finden Sie Einzelheiten zu den verschiedenen Monitoring-Tools von Adobe Campaign sowie weitere Richtlinien zum Monitoring der Zustellbarkeit.

## Monitoring-Tools {#monitoring-tools}

Verwenden Sie die von Adobe Campaign bereitgestellten Funktionen zum Monitoring der Zustellbarkeit Ihrer Plattform.

Das Zustellbarkeits-Package ermöglicht Ihnen Zugriff auf:

* Den [Inbox Rendering-Bericht](../../delivery/using/inbox-rendering.md), mit dem Sie Ihre Nachrichten auf gängigen E-Mail-Clients als Vorschau anzeigen können, um Inhalte und Reputation zu überprüfen.
* Übersicht über die Nachrichtenqualität (Zustellung in der Inbox, Spam).

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
* Prüfen Sie, ob die einzelnen Versanddurchsätze der Gültigkeit des Versandinhalts entsprechen (&quot;Flash Sales&quot; zum Beispiel sollten innerhalb von Minuten, nicht von Tagen zugestellt werden).
* Wenn der Versand in [Schüben](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves) erfolgt, stellen Sie sicher, dass genügend Zeit vorhanden ist, damit ein Schub fertiggestellt werden kann, bevor der nächste beginnt.
* Prüfen Sie, ob die Anzahl der Fehler und der neuen [Quarantänen](../../delivery/using/understanding-quarantine-management.md) der anderer Sendungen entspricht.
* Prüfen Sie in den [Versandlogs](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history) sorgfältig die Art der hervorgehobenen Fehler (Blockierungsliste, DNS-Probleme, Anti-Spam-Regeln usw.).

## Signal Spam {#signal-spam}

Signal Spam ist ein französischer Dienst, der anonymisiertes Feedback-Schleifen-Reporting für französische ISPs anbietet (Orange, SFR).

* Mit diesem Dienst können Sie die Reputation französischer ISPs verfolgen und die Kundenaktivität tracken.

* Signal Spam bietet auch eine eigene Benutzeroberfläche für die direkte Beschwerdemöglichkeit zum Beenden von Benutzerlogs. Durch diese Beschwerden werden dann E-Mails aus der Datenbank entfernt und in Quarantäne gestellt.

## 250ok {#deliverability-250ok}

[250ok](https://250ok.com/) ist eine ergänzende Monitoring-Lösung für die internen Adobe-Zustellbarkeits-Tools, die IP- und Domain-Blockierungslisten und Reputationsindikatoren bereitstellen.

Die bereitgestellten Werte sind in Echtzeit verfügbar, wodurch proaktive Unterstützung gewährleistet ist.

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->

---
title: Überwachung der Lieferbarkeit in Adobe Campaign Classic
description: Erfahren Sie mehr über Tools und Richtlinien zur Überwachung der Lieferbarkeit in Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 0b5c5dbd-f532-4d8a-a255-9e6d88357d8d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 0baef937-f00b-4fc4-8608-a870997be684
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a30c4a2d31c3f674ac4a7bb4827a6951b36014ab
workflow-type: tm+mt
source-wordcount: '754'
ht-degree: 50%

---


# Monitoring der Zustellbarkeit{#monitoring-deliverability}

Nachstehend finden Sie Einzelheiten zu den verschiedenen Überwachungswerkzeugen von Adobe Campaign sowie weitere Richtlinien zur Überwachung der Lieferbarkeit.

## Überwachungswerkzeuge {#monitoring-tools}

Nutzen Sie die von Adobe Campaign angebotenen Funktionen, um die Lieferbarkeit Ihrer Plattform zu überwachen.

Das Zustellbarkeits-Package ermöglicht Ihnen Zugriff auf:

* Technischer Verfolgungsbericht für die tägliche Leistungsbereitstellung (technische Überwachung). Dieser auf Anfrage verfügbare Bericht ermöglicht es Ihnen, einen täglichen Bericht per E-Mail an einer bestimmten Adresse zu erhalten. Weitere Informationen erhalten Sie vom Adobe-Kundenservice-Team.
* Der [Inbox-Renderingbericht](../../delivery/using/inbox-rendering.md) , mit dem Sie Ihre Nachrichten auf wichtigen E-Mail-Clients zur Vorschau von Inhalten und Reputation überprüfen können.
* Übersicht über die Nachrichtenqualität (Posteingang, Spam).

Sie können auch die folgenden Werkzeuge verwenden:

* The **[!UICONTROL Delivery throughput]** report gives you an overview of the entire platform&#39;s throughput for a given period. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../reporting/using/global-reports.md#delivery-throughput).
* Der Bericht zur Überwachung **[!UICONTROL der]** technischen Lieferbarkeit enthält eine Reihe von Qualitätsindikatoren für Ihre Plattform. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](#technical-deliverability-monitoring).
* Das [Versand-Dashboard](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard) gibt Ihnen Zugriff auf die [Versand-Zusammenfassung](../../delivery/using/monitoring-a-delivery.md#delivery-summary), die [Versandlogs, den Verlauf](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history) und die [Trackinglogs](../../delivery/using/monitoring-a-delivery.md#tracking-logs). In ihnen werden Details zum Versand dargestellt und Sie erfahren, welche Zielgruppe warum ausgeschlossen wurde sowie Tracking-Informationen wie z. B. Öffnungen und Klicks. <!--For more on this, see [Monitoring a delivery](../../delivery/using/monitoring-a-delivery.md).-->
* Sie können auch die Anzahl der Nachrichten prüfen, die erfolgreich gesendet, verarbeitet und gesendet werden sollen. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/monitoring-a-delivery.md#number-of-messages-sent)
   <!--[SpamAssassin](../../installation/using/configuring-spamassassin.md)?-->

## Überwachungsleitlinien {#monitoring-guidelines}

Im Folgenden finden Sie einige zusätzliche Leitlinien zur Überwachung der Lieferbarkeit:

* Regularly check the [delivery throughput](../../reporting/using/global-reports.md#delivery-throughput) for the whole platform to verify whether it is consistent with the original set-up.
* Check that [retries](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) are set up correctly (30 minutes for retry period and more than 20 retries) in delivery templates.
* Regularly verify that the [bounce](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management) mailbox is accessible and that the account is not about to expire.
* Prüfen Sie, ob die einzelnen Versanddurchsätze der Gültigkeit des Versandinhalts entsprechen (&quot;Flash Sales&quot; zum Beispiel sollten innerhalb von Minuten, nicht von Tagen zugestellt werden).
* When using [waves](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves), verify that each wave has enough time to finish before the next one is triggered.
* Check that the number of errors and new [quarantines](../../delivery/using/understanding-quarantine-management.md) are consistent with other deliveries.
* Carefully consult the [delivery logs](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history) in detail to check the kind of errors that are highlighted (grey or black-listing, DNS issues, anti-spam rules, etc…).

## Signal Spam {#signal-spam}

Signal Spam ist ein französischer Dienst, der anonymisiertes Feedback-Schleifen-Reporting für französische ISPs anbietet (Orange, SFR).

* Mit diesem Dienst können Sie die Reputation französischer ISPs verfolgen und die Kundenaktivität tracken.

* Signal Spam bietet auch eine eigene Benutzeroberfläche für die direkte Beschwerdemöglichkeit zum Beenden von Benutzerlogs. Durch diese Beschwerden werden dann E-Mails aus der Datenbank entfernt und in Quarantäne gestellt.

## 250ok {#deliverability-250ok}

[250ok](https://250ok.com/) ist eine ergänzende Überwachungslösung zu den internen Adobe-Werkzeugen zur Bereitstellung von IP, Blacklisting und Reputationsindikatoren.

Die bereitgestellten Informationen sind in Echtzeit verfügbar, was eine proaktive Unterstützung ermöglicht.

## Bericht zum technischen Zustellbarkeits-Monitoring {#technical-deliverability-monitoring}

Der Bericht zum technischen Zustellbarkeits-Monitoring wird täglich aktualisiert und ist aufrufbar, indem Sie zu **[!UICONTROL Monitoring]** > **[!UICONTROL Übersicht]** navigieren und auf den Link **[!UICONTROL Technisches Monitoring]** auf dem Tab **[!UICONTROL Startseite]** von Adobe Campaign klicken. Er enthält eine Reihe von Indikatoren zur Zustellungsqualität Ihrer Plattform.

Diese Indikatoren werden täglich um 9 Uhr aktualisiert.

>[!NOTE]
>
>Darüber hinaus können Sie einen täglichen Bericht per E-Mail an einer bestimmten Adresse erhalten. Teilen Sie uns die angeforderte E-Mail-Adresse per E-Mail oder über das Adobe Campaign Extranet mit.

![](assets/s_tn_del_monitoring.png)

Folgende Indikatoren werden im Bericht dargestellt:

* **[!UICONTROL Reverse DNS]**: Adobe Campaign prüft, ob für eine IP-Adresse ein Reverse-DNS angegeben ist und ob dieses wirklich auf die IP zurückverweist.

* **[!UICONTROL SPF]** (Sender Policy Framework): Ein Authentifizierungsmechanismus, der es ISPs und Postfachanbietern ermöglicht zu prüfen, ob der E-Mail-Absender in der sendenden Domain autorisiert ist.

* **[!UICONTROL DomainKeys]**: Von Yahoo entwickelter Service zur Zertifizierung der Identität eines E-Mail-Absenders.

* **[!UICONTROL IP und RBL-Domain]** (Real-time Blackhole List): Eine Liste der IP-Adressen und Domains, die von Blocklist-Organisationen aufgrund schlechter Reputation markiert wurden. Diese Listen werden von speziellen Organisationen wie Spamhaus, Spamcop, SURBL/URIBL etc. geführt. Adobe Campaign verarbeitet derzeit Prüfungen für RBLs, die erhebliche Auswirkungen auf die Zustellbarkeit haben. Diese RBLs spiegeln die Reputation des Absenders wider und können von ISPs referenziert werden, bevor sie den Empfang Ihrer E-Mails akzeptieren.

* **[!UICONTROL SNDS]** (Smart Network Data Services): Ein [Windows Live Hotmail Service](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx) zur Spam-Bekämpfung. Hotmail ist der einzige ISP, der diese Informationen bereitstellt. Benchmark-Ergebnisse sind ein grünes Filterergebnis, eine Beschwerderate von weniger als 0,1 % und keine Spam-Fallen.

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->

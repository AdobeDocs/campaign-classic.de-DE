---
title: Track and monitor messages
seo-title: Track and monitor messages
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5e6ecd636ee0b2199808c03b2fd898a194f0c1ea
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 55%

---


# Tracken und Beobachten {#track-and-monitor}

Sie haben auf die Senden-Schaltfläche geklickt? Lassen Sie uns sehen, was dann passiert. Nach dem Versand der Nachrichten ermöglicht es Ihnen Adobe Campaign die gesendeten Nachrichten zu verfolgen und festzustellen, wie Ihre Empfänger auf darauf reagieren. Dadurch können Sie den zukünftigen Versand verbessern und Ihre nächsten Kampagnen optimieren.

## Sendungen beobachten {#monitoring-deliveries}

Um Ihre Kampagnen steuern zu können, müssen Sie zunächst sichergehen, dass Ihre Nachricht bei Ihren Empfängern tatsächlich angekommen ist.

From Campaign delivery dashboard, you can check the processed messages and delivery audit logs.
In den Versand-Logs können Sie den Status der Nachrichten feststellen. [Mehr dazu](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

Was passiert, wenn die Nachrichten nicht gesendet werden und ihr Status weiterhin **Ausstehend** lautet?

* Der Prozess wartet auf die Verfügbarkeit von Ressourcen. Möglicherweise wurde der MTA noch nicht gestartet.
Überprüfen Sie, ob Ihre mta@instance auf Ihren MTA-Servern gestartet wurden, und Beginn Sie ggf. das MTA-Modul. [Mehr dazu](../../production/using/administration.md).

* Möglicherweise wird für den Versand eine Affinität verwendet, die in der Sendeinstanz noch nicht konfiguriert wurde.
Tipp: Prüfen Sie die Konfiguration der Traffic-Verwaltung (IP-Affinität). Weiterführende Informationen dazu finden Sie im Abschnitt Ausgehenden SMTP-Traffic steuern.

>[!NOTE]
>
>These steps can only be performed by an expert user.

## Tracking {#tracking-deliveries}

Um das Verhalten Ihrer Empfänger besser zu kennen, können Sie nachverfolgen, wie sie auf einen Versand reagieren: Empfang, Öffnen, Klicks auf Links, Abmeldungen usw. In Campaign Classic werden diese Informationen auf der Registerkarte &quot;Verfolgung&quot;der Empfänger, auf die der Versand abzielt, und auf der Registerkarte &quot;Verfolgung&quot;des Versands angezeigt. In Campaign Standard wird er auf der Registerkarte &quot;Trackinglogs&quot;des Versands angezeigt.

**Tipp**: Die Nachrichtenverfolgung ist standardmäßig aktiviert. Um URLs zu konfigurieren, wählen Sie im unteren Bereich des Versand-Assistenten die Option &quot;URLs anzeigen&quot;. Für jede URL der Nachricht können Sie festlegen, ob die Verfolgung aktiviert werden soll.

Weitere Informationen hierzu finden Sie im Abschnitt [Konfigurieren der Verfolgung](../../delivery/using/how-to-configure-tracked-links.md) und in der Beschreibung der [Trackingindikatoren](../../reporting/using/delivery-reports.md#tracking-indicators) .

## Versandleistung {#delivery-performances}

Um die Geschwindigkeit der Nachrichtenzustellung zu messen, können Sie den Versanddurchsatz kontrollieren. Zur Messung der Versandgeschwindigkeit von Nachrichten werden zwei Kennzahlen herangezogen: Anzahl an gesendeten Nachrichten pro Stunde und die gesendete Datenmenge in Bits pro Sekunde. Weiterführende Informationen dazu finden Sie im Abschnitt [Versanddurchsatz](../../reporting/using/global-reports.md#delivery-throughput).

**Tipps**:

* Bewahren Sie auf der Instanz keine fehlgeschlagenen Sendungen auf, da dadurch temporäre Tabellen gespeichert werden, was wiederum die Leistung beeinträchtigt.

* Entfernen Sie nicht mehr benötigte Sendungen und inaktive Empfänger aus der Datenbank, um eine hohe Qualität der Adressen zu gewährleisten.

* Planen Sie nicht die gleichzeitige Durchführung umfangreicher Sendungen. Beachten Sie, dass es 5 bis 10 Minuten dauern kann, bis die Last gleichmäßig über das System verteilt wurde.

## Fehlerbehebung beim Versand {#delivery-troubleshooting}

Bei Problemen mit Versänden können spezifische Aktionen durchgeführt werden:

* [Probleme mit der Lieferbarkeit](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Probleme mit der Bildanzeige](../../production/using/image-display-issues.md)

* [Leistungsprobleme bei Versänden](../../delivery/using/monitoring-a-delivery.md#performance_issues)

* [Temporary files issues](../../production/using/temporary-files.md) - *on-premise customers only*

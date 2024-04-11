---
product: campaign
title: Nachverfolgen und Überwachen von Nachrichten
description: Erfahren Sie, wie Sie Nachrichten nachverfolgen und überwachen
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Monitoring, Reporting
role: User
exl-id: a039a288-2e7b-4f35-9885-ead3ed4347af
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 91%

---

# Verfolgen und überwachen {#track-and-monitor}

Sie haben auf die Schaltfläche **Senden** geklickt? Lassen Sie uns sehen, was dann passiert. Nach dem Versand der Nachrichten ermöglicht es Ihnen Adobe Campaign die gesendeten Nachrichten zu verfolgen und festzustellen, wie Ihre Empfänger darauf reagieren. Dadurch können Sie den zukünftigen Versand verbessern und Ihre nächsten Kampagnen optimieren.

## Überwachen von Sendungen {#monitoring-deliveries}

Um Ihre Kampagnen steuern zu können, müssen Sie zunächst sichergehen, dass Ihre Nachricht bei Ihren Empfängern tatsächlich angekommen ist.

Prüfen Sie im Versand-Dashboard von Campaign die verarbeiteten Nachrichten und Versand-Logs.
In den Versand-Logs können Sie den Status der Nachrichten feststellen. [Weitere Informationen](about-delivery-monitoring.md).

Was passiert, wenn die Nachrichten nicht gesendet werden und ihr Status weiterhin **Ausstehend** lautet?

* Der Prozess wartet auf die Verfügbarkeit von Ressourcen. Möglicherweise wurde der MTA noch nicht gestartet.
Prüfen Sie, ob Ihre mta@instance-Module auf den MTA-Servern gestartet wurden. Starten Sie sie gegebenenfalls. [Weitere Informationen](../../production/using/administration.md).

* Möglicherweise wird für den Versand eine Affinität verwendet, die in der Sendeinstanz noch nicht konfiguriert wurde.
Tipp: Prüfen Sie die Konfiguration der Traffic-Verwaltung (IP-Affinität). Weiterführende Informationen dazu finden Sie im Abschnitt Ausgehenden SMTP-Traffic steuern.

>[!NOTE]
>
>Diese Schritte können nur von einem erfahrenen Benutzer durchgeführt werden.

## Nachverfolgen von Verhaltensmustern {#track-behaviour}

Um das Verhalten Ihrer Empfänger besser kennenzulernen, können Sie ihre Reaktion auf einen Versand verfolgen: Empfang, Öffnung, Klicks auf Links, Abmeldungen usw. In Campaign Classic werden diese Informationen auf der Registerkarte „Tracking“ der Empfänger, auf die der Versand abzielt, und auf der Registerkarte „Tracking“ des Versands angezeigt.

**Tipp**: Das Nachverfolgen von Nachrichten ist standardmäßig aktiviert. Um URLs zu konfigurieren, wählen Sie im unteren Bereich des Versand-Assistenten die Option „URLs anzeigen“ aus. Sie können für jede URL der Nachricht festlegen, ob Sie die Nachverfolgung aktivieren möchten.

Mehr dazu finden Sie im Abschnitt [Konfigurieren der Nachverfolgung](how-to-configure-tracked-links.md) und in der Beschreibung der [Indikatoren für die Nachverfolgung](../../reporting/using/delivery-reports.md#tracking-indicators).

## Versand-Performance {#delivery-performances}

Zur Messung der Versandgeschwindigkeit von Nachrichten können Sie den Versanddurchsatz steuern. Die Kriterien sind die Anzahl der gesendeten Nachrichten pro Stunde und die Größe der Nachrichten (in Bits pro Sekunde). Weitere Informationen finden Sie unter [Versanddurchsatz](../../reporting/using/global-reports.md#delivery-throughput).

**Tipps**:

* Bewahren Sie auf der Instanz keine fehlgeschlagenen Sendungen auf, da dadurch temporäre Tabellen gespeichert werden, was wiederum die Performance beeinträchtigt.

* Entfernen Sie nicht mehr benötigte Sendungen und inaktive Empfänger aus der Datenbank, um eine hohe Qualität der Adressen zu gewährleisten.

* Planen Sie nicht die gleichzeitige Durchführung umfangreicher Sendungen. Beachten Sie, dass es 5 bis 10 Minuten dauern kann, bis die Last gleichmäßig über das System verteilt wurde.

## Fehlerbehebung beim Versand {#delivery-troubleshooting}

Bei Problemen mit Sendungen können spezifische Aktionen durchgeführt werden:

* [Probleme mit der Zustellbarkeit](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Probleme mit der Bildanzeige](../../production/using/image-display-issues.md)

* [Performance-Probleme beim Versand](delivery-performances.md)

* [Probleme mit temporären Dateien](../../production/using/temporary-files.md) – *nur On-Premise-Kunden*

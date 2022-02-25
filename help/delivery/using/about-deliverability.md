---
product: campaign
title: Erste Schritte mit der Zustellbarkeit in Campaign
description: Lernen Sie Best Practices zur Zustellbarkeit kennen
feature: Deliverability
exl-id: f301b34c-244c-4279-b23f-8224ea8eedbe
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: ht
source-wordcount: '724'
ht-degree: 100%

---

# Was ist Zustellbarkeit{#about-deliverability}

![](../../assets/common.svg)

Die Zustellbarkeit misst, wie viele Ihrer Nachrichten erfolgreich den Posteingang Ihrer Empfänger erreichen und nicht als unzustellbar zurückgesendet bzw. als Spam gekennzeichnet werden. [Hier erfahren Sie, warum Zustellbarkeit wichtig ist](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html?lang=de#why-deliverability-matters).

Genauer gesagt bezieht sich die E-Mail-Zustellbarkeit auf die Menge der Merkmale, die die Fähigkeit einer Nachricht bestimmen, über eine persönliche E-Mail-Adresse innerhalb kurzer Zeit und mit der erwarteten Qualität in Bezug auf Inhalt und Format ihr Ziel zu erreichen.

Einen tieferen Einblick in das Thema der Zustellbarkeit und weitere Informationen zu den wichtigsten Bedingungen, Konzepten und Ansätzen zur Zustellbarkeit erhalten Sie im [Adobe-Handbuch mit den Best Practices zur Zustellbarkeit](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=de).

## Verbessern der Zustellbarkeit {#deliverability-key-points}

Probleme mit der Zustellbarkeit hängen in der Regel mit Maßnahmen zum Schutz vor Spam zusammen, die von Internet-Anbietern und Mailserver-Administratoren implementiert werden.

* Allgemeine Empfehlungen zum Entwerfen erfolgreicher E-Mail-Marketing-Kampagnen finden Sie unter [Strategie und Definition der Zustellbarkeit](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html?lang=de).

* Für spezifischere Empfehlungen zur Optimierung der Zustellbarkeit Ihrer Adobe Campaign-E-Mails empfiehlt Adobe die Verwendung der in diesem Abschnitt aufgeführten Best Practices.

>[!NOTE]
>
>Da Internet-Anbieter gezwungen sind, ständig neue, ausgereifte Filtertechniken zu entwickeln, um ihre Kunden vor Spammern zu schützen, ändern sich die für die Zustellbarkeit von E-Mails geltenden Kriterien und Regeln sehr oft. Konsultieren Sie deshalb das [Adobe-Handbuch mit Best Practices zur Zustellbarkeit](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=de), das regelmäßig aktualisiert wird.

### Zustellrate

Die Zustellrate ist der Anteil der Nachrichten, die die Postfächer der Empfänger im Vergleich zur gesamten Anzahl der versendeten Nachrichten erreicht haben. Um die Zustellbarkeit zu verbessern, können Sie versuchen, diese Rate zu erhöhen.

Bei Adobe Campaign hängt die Zustellrate von zahlreichen Faktoren ab, insbesondere von:

* Korrekte Konfiguration der Instanzen: Wenden Sie sich zwecks Hilfe an Ihren Adobe-Support-Mitarbeiter.
* Legitime Netzwerkkonfiguration: siehe [diesen Abschnitt](optimize-delivery.md#network-config) und [Einrichtung von Domains und Strategie](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=de#domain-setup-and-strategy).
* Reputation Ihrer IP-Adresse: siehe [IP-Strategie](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=de#ip-strategy).
* Qualität der Zieladressen: siehe [Quarantäne-Management](optimize-delivery.md#quarantine-management).
* Ein niedriger Anteil von [Beschwerden](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html?lang=de) und [Hardbounces](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html?lang=de#hard-bounces).
* Inhalt Ihrer Nachricht: Siehe [Kontrollieren von E-Mail-Inhalten](control-message-content.md).
* Nachrichtenauthentifizierung (SPF, DKIM, DMARC): siehe [diesen Abschnitt](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=de#authentication).
* Reputation des Absenders: Informationen darüber, wie die wichtigsten Internet-Anbieter die Reputation eines Absenders bewerten, finden Sie in [diesem Abschnitt](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html?lang=de).

## Campaign-Tools für die Zustellbarkeit {#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
Adobe Campaign bietet verschiedene Tools zur Verfolgung und Verbesserung der Zustellbarkeitsleistung Ihrer Plattform. Auf dieser Seite finden Sie auch die wichtigsten Grundsätze, die Sie beachten sollten, um bei der Verwendung von Campaign die Zustellbarkeit zu optimieren.

### Sorgfältiges Erstellen Ihrer Nachricht

Befolgen Sie beim Konfigurieren, Entwerfen und Testen Ihrer Nachricht die in den folgenden Abschnitten aufgeführten Best Practices. Die Nutzung aller von Adobe Campaign bereitgestellten Funktionen hilft Ihnen, die Zustellbarkeit zu verbessern.

* [Best Practices beim Versand](delivery-best-practices.md)
* [Kontrollieren von E-Mail-Inhalten](control-message-content.md)
* [Inbox Rendering](inbox-rendering.md)
* [Durchführen eines Testversands](steps-validating-the-delivery.md#sending-a-proof)

### Einverständnis durch doppelten Opt-in überprüfen {#double-opt-in}

Um das Senden von Nachrichten an ungültige Adressen zu vermeiden, unsachgemäße Kommunikation zu minimieren und die Reputation des Absenders zu verbessern, empfiehlt Adobe die Implementierung eines Mechanismus zum doppelten Opt-in. Mit dieser Methode können Sie sicherstellen, dass sich Ihre Empfänger absichtlich angemeldet haben.

Weitere Informationen hierzu finden Sie unter [Abonnement-Formular mit zweifacher Bestätigung erstellen](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).

Weitere Informationen zu Best Practices bei der Erfassung von Kundendaten finden Sie im [Adobe-Handbuch mit Best Practices zur Zustellbarkeit](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html?lang=de#data-quality-and-hygiene).

### Quarantäne-Management nutzen

Adobe Campaign verwaltet eine Liste, in der Spam-Beschwerden, Hardbounces und Softbounces, die immer wieder auftreten, erfasst werden.

Zum Schutz Ihrer Zustellbarkeit werden die Empfänger, deren Adressen auf dieser Liste stehen, standardmäßig von allen zukünftigen Sendungen ausgeschlossen, da das Senden an diese Kontakte Ihre Reputation beschädigen könnte.

Teilweise werden E-Mails von Providern automatisch als Spam eingestuft, wenn die Anzahl ungültiger Adressen zu hoch ist. Durch die Quarantäne können Sie also vermeiden, von diesen Providern auf eine Blockierungsliste gesetzt zu werden.

Weiterführende Informationen hierzu finden Sie in den folgenden Abschnitten:

* [Ursachen für das Fehlschlagen von Sendungen](understanding-delivery-failures.md)
* [Funktionsweise der Quarantäneverwaltung](understanding-quarantine-management.md)
* [Quarantäne vs. Blockierungsliste](understanding-quarantine-management.md#quarantine-vs-denylist)

### Verwenden von Tools zum Monitoring und Reporting

Verwenden Sie die von Adobe Campaign bereitgestellten Funktionen zur Überwachung der Zustellbarkeit.

Mit Adobe Campaign können Sie die Leistung Ihrer Sendungen anhand einer Reihe integrierter Echtzeitindikatoren und -berichte überprüfen, um einen besseren Einblick in Ihre Sendungen zu erhalten.

Weiterführende Informationen hierzu finden Sie in den folgenden Abschnitten:

* [Überwachen der Zustellbarkeit](monitoring-deliverability.md)
* [Erste Schritte mit dem Überwachen des Versands](about-delivery-monitoring.md)
* [Erste Schritte mit den integrierten Berichten von Campaign](../../reporting/using/about-campaign-built-in-reports.md)

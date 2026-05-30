---
product: campaign
title: Erste Schritte mit der Zustellbarkeit in Campaign
description: Lernen Sie Best Practices zur Zustellbarkeit kennen
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Deliverability
role: User
exl-id: f301b34c-244c-4279-b23f-8224ea8eedbe
TQID: https://experienceleague.adobe.com/UuHzMhIx2zL3VxZXxnKM3UHBlN4Mkr7qy47Ttk-43d0
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: beb7a3c1-66ab-4786-b879-7621375b3c40
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 851
ht-degree: 100%

---

# Was ist Zustellbarkeit{#about-deliverability}

Die Zustellbarkeit misst, wie viele Ihrer Kampagnen erfolgreich den Posteingang Ihrer Empfangenden erreichen und nicht als unzustellbar zurückgesendet bzw. als Spam gekennzeichnet werden. [Hier erfahren Sie, warum Zustellbarkeit wichtig ist](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html?lang=de#why-deliverability-matters).

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

Die Zustellbarkeitsrate ist der Anteil der Nachrichten, die die Postfächer der Empfängerinnen und Empfänger erreicht haben, im Vergleich zur gesamten Anzahl der versendeten Nachrichten. Um die Zustellbarkeit zu verbessern, können Sie versuchen, diese Rate zu erhöhen.

Bei Adobe Campaign hängt die Zustellrate von zahlreichen Faktoren ab, insbesondere von:

* Korrekte Konfiguration der Instanzen: Wenden Sie sich zwecks Hilfe an Ihren Adobe-Support-Mitarbeiter.
* Legitime Netzwerkkonfiguration: siehe [Domain-Setup und Strategie](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=de#domain-setup-and-strategy).
* Reputation Ihrer IP-Adresse: siehe [IP-Strategie](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=de#ip-strategy).
* Ein niedriger Anteil von [Beschwerden](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html?lang=de) und [Hardbounces](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html?lang=de#hard-bounces).
* Inhalt Ihrer Nachricht: Siehe [Kontrollieren von E-Mail-Inhalten](control-message-content.md).
* Nachrichtenauthentifizierung (SPF, DKIM, DMARC): siehe [diesen Abschnitt](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=de#authentication).
* Reputation des Absenders: Informationen darüber, wie die wichtigsten Internet-Anbieter die Reputation eines Absenders auswerten, finden Sie in [diesem Abschnitt](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html?lang=de).

## Campaign-Tools für die Zustellbarkeit {#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
Adobe Campaign bietet verschiedene Tools zur Verfolgung und Verbesserung der Zustellbarkeits-Performance Ihrer Plattform. Auf dieser Seite finden Sie auch die wichtigsten Grundsätze, die Sie beachten sollten, um bei der Verwendung von Campaign die Zustellbarkeit zu optimieren.

### Sorgfältiges Erstellen Ihrer Nachricht

Befolgen Sie beim Konfigurieren, Entwerfen und Testen Ihrer Nachricht die in den folgenden Abschnitten aufgeführten Best Practices. Die Nutzung aller von Adobe Campaign bereitgestellten Funktionen hilft Ihnen, die Zustellbarkeit zu verbessern.

* [Best Practices beim Versand](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/delivery-best-practices.html?lang=de){target="_blank"}.
* [Kontrollieren von E-Mail-Inhalten](control-message-content.md)
* [Rendern des Posteingangs](inbox-rendering.md)
* [Durchführen eines Testversands](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/preview-and-proof.html?lang=de){target="_blank"}

### Einverständnis durch doppelten Opt-in überprüfen {#double-opt-in}

Um das Senden von Nachrichten an ungültige Adressen zu vermeiden, unsachgemäße Kommunikation zu minimieren und die Reputation des Absenders zu verbessern, empfiehlt Adobe die Implementierung eines Mechanismus zum doppelten Opt-in. Mit dieser Methode können Sie sicherstellen, dass sich Ihre Empfänger absichtlich angemeldet haben.

Weitere Informationen hierzu finden Sie unter [Abonnement-Formular mit zweifacher Bestätigung erstellen](../../web/using/use-cases-web-forms.md#create-a-subscription--form-with-double-opt-in).

Weitere Informationen zu Best Practices bei der Erfassung von Kundendaten finden Sie im [Adobe-Handbuch mit Best Practices zur Zustellbarkeit](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html?lang=de#data-quality-and-hygiene).

### Quarantäne-Management nutzen

Adobe Campaign verwaltet eine Liste, in der Spam-Beschwerden, Hardbounces und Softbounces, die immer wieder auftreten, erfasst werden.

Zum Schutz Ihrer Zustellbarkeit werden die Empfänger, deren Adressen auf dieser Liste stehen, standardmäßig von allen zukünftigen Sendungen ausgeschlossen, da das Senden an diese Kontakte Ihre Reputation beschädigen könnte.

Teilweise werden E-Mails von Providern automatisch als Spam eingestuft, wenn die Anzahl ungültiger Adressen zu hoch ist. Durch die Quarantäne können Sie also vermeiden, von diesen Providern auf eine Blockierungsliste gesetzt zu werden.

Weiterführende Informationen hierzu finden Sie in den folgenden Abschnitten:

* [Informationen zu Versandfehlern](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (Campaign v8-Dokumentation – umfassendes Handbuch)
* [Funktionsweise der Quarantäneverwaltung](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (Campaign v8-Dokumentation – umfassendes Handbuch)

### Verwenden von Tools zum Monitoring und Reporting

Verwenden Sie die von Adobe Campaign bereitgestellten Funktionen zur Überwachung der Zustellbarkeit.

Mit Adobe Campaign können Sie die Leistung Ihrer Sendungen anhand einer Reihe integrierter Echtzeitindikatoren und -berichte überprüfen, um einen besseren Einblick in Ihre Sendungen zu erhalten.

Weiterführende Informationen hierzu finden Sie in den folgenden Abschnitten:

* [Erste Schritte bei der Überwachung eines Versands](about-delivery-monitoring.md)
* [Erste Schritte mit den integrierten Berichten von Campaign](../../reporting/using/about-campaign-built-in-reports.md)

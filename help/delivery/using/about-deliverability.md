---
solution: Campaign Classic
product: campaign
title: Über die Zustellbarkeit in Campaign
description: Lernen Sie Best Practices zur Zustellbarkeit kennen.
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: f301b34c-244c-4279-b23f-8224ea8eedbe
translation-type: tm+mt
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 13%

---

# Was ist Zustellbarkeit{#about-deliverability}

Die Lieferbarkeit ermöglicht es Ihnen, den Erfolg Ihrer Kampagnen zu messen, die den Posteingang Ihrer Empfänger erreichen, ohne zu springen oder als Spam gekennzeichnet zu werden. [Erfahren Sie, warum Lieferbarkeit wichtig ist](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html#why-deliverability-matters).

Genauer gesagt bezieht sich die E-Mail-Zustellbarkeit auf den Satz von Merkmalen, die bestimmen, ob eine Nachricht ihr Ziel erreichen kann, über eine persönliche E-Mail-Adresse, innerhalb kurzer Zeit und mit der erwarteten Qualität in Bezug auf Inhalt und Format.

Einen tieferen Einstieg in die Lieferbarkeit und weitere Informationen zu den wichtigsten Lieferbedingungen, -konzepten und -ansätzen finden Sie im Leitfaden [Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=de) zur Lieferbarkeit von Adoben.

## Verbesserung der Zustellbarkeit {#deliverability-key-points}

Probleme mit der Lieferbarkeit sind in der Regel mit Maßnahmen zum Schutz vor Spam verknüpft, die von Internet-Dienstleistern und Mailserveradministratoren implementiert werden.

* Allgemeine Empfehlungen zum Entwerfen erfolgreicher E-Mail-Marketing-Kampagnen finden Sie unter [Auslieferungsstrategie und -definition](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html).

* Für spezifischere Empfehlungen zur Optimierung der Zustellbarkeit Ihrer Adobe Campaign-E-Mails empfiehlt Adobe die Verwendung der in diesem Abschnitt aufgeführten Best Practices.

>[!NOTE]
>
>Da ISPs verpflichtet sind, ständig neue, ausgereifte Filtertechniken zu entwickeln, um ihre Kunden vor Spammer zu schützen, ist die Zustellbarkeit von E-Mails durch ständig wechselnde Kriterien und Regeln gekennzeichnet. Vergewissern Sie sich, dass Sie den Leitfaden [Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html) zur Adobe-Bereitstellung lesen, der regelmäßig aktualisiert wird.

### Auslieferungsrate

Die Auslieferungsrate ist die Anzahl der Nachrichten, die die Postfächer der Empfänger im Vergleich zur Anzahl der ausgelieferten Nachrichten erreicht haben. Um die Lieferbarkeit zu verbessern, können Sie diese Rate erhöhen.

Bei Adobe Campaign hängt die Lieferquote von zahlreichen Faktoren ab, insbesondere von:

* Korrekte Konfiguration der Instanzen: Wenden Sie sich zwecks Hilfe an Ihren Kundenbetreuer.
* Legitime Netzwerkkonfiguration: siehe [diesen Abschnitt](../../delivery/using/optimize-delivery.md#network-config) und [Domäneneinrichtung und -strategie](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#domain-setup-and-strategy).
* Ihre IP-Adresse: Name: siehe [IP-Strategie](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#ip-strategy).
* Qualität der Zieladressen: siehe [Quarantäne-Management](../../delivery/using/optimize-delivery.md#quarantine-management).
* niedrige Raten [Beschwerden](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html) und [harte Absprungrate](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html#hard-bounces).
* Inhalt Ihrer Nachricht: Siehe [Steuern des E-Mail-Inhalts](../../delivery/using/control-message-content.md).
* Nachrichtenauthentifizierung (SPF, DKIM, DMARC): siehe [diesen Abschnitt](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).
* Name des Absenders: Informationen darüber, wie die wichtigsten ISPs den Ruf eines Absenders bewerten, finden Sie in [diesem Abschnitt](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html).

## Kampagne-Bereitstellungs-Tools {#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
Adobe Campaign bietet verschiedene Tools zur Verfolgung und Verbesserung der Bereitstellungsleistung Ihrer Plattform. Auf dieser Seite werden auch die wichtigsten Grundsätze hervorgehoben, die Sie beachten sollten, um die Lieferbarkeit bei der Verwendung der Kampagne zu optimieren.

### Erstellen Sie Ihre Nachricht sorgfältig

Vergewissern Sie sich beim Konfigurieren, Entwerfen und Testen Ihrer Nachricht, dass Sie die in den unten aufgeführten Abschnitten beschriebenen Best Practices befolgen. Die Nutzung aller von Adobe Campaign bereitgestellten Funktionen hilft Ihnen, die Lieferbarkeit zu verbessern.

* [Best Practices beim Versand](../../delivery/using/delivery-best-practices.md)
* [Kontrollieren von E-Mail-Inhalten](../../delivery/using/control-message-content.md)
* [Inbox Rendering](../../delivery/using/inbox-rendering.md)
* [Testversand durchführen](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)

### Einwilligung durch Dublette-Teilnahme überprüfen{#double-opt-in}

Um das Senden von Nachrichten an ungültige Adressen zu vermeiden, unsachgemäße Kommunikation zu begrenzen und den Ruf des Absenders zu verbessern, empfiehlt Adobe die Implementierung eines Dublette-Ausschluss-Mechanismus. Auf diese Weise können Sie sicherstellen, dass Ihre Empfänger absichtlich abonniert haben.

Weitere Informationen hierzu finden Sie unter [Abonnement-Formular mit zweifacher Bestätigung erstellen](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).

Weitere Informationen zu Best Practices bei der Erfassung von Kundendaten finden Sie im Leitfaden [Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html#data-quality-and-hygiene) zur Adobe-Bereitstellung.

### Quarantäne-Management nutzen

Adobe Campaign verwaltet eine Liste, bei der Spam-Beschwerden, harte Absprünge und weiche Absprünge, die konsistent ablaufen, erfasst werden.

Zum Schutz Ihrer Zustellbarkeit werden die Empfänger, deren Adressen auf dieser Liste liegen, standardmäßig von allen zukünftigen Versänden ausgeschlossen, da das Senden an diese Kontakte Ihren Ruf beschädigen könnte.

Teilweise werden E-Mails von Providern automatisch als Spam eingestuft, wenn die Anzahl ungültiger Adressen zu hoch ist. Durch die Quarantäne können Sie also vermeiden, von diesen Providern auf eine Blockierungsliste gesetzt zu werden.

Weitere Informationen finden Sie in den folgenden Abschnitten:

* [Ursachen für Fehler beim Versand](../../delivery/using/understanding-delivery-failures.md)
* [Funktionsweise der Quarantäneverwaltung](../../delivery/using/understanding-quarantine-management.md)
* [Quarantäne vs. Blockierungsliste](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist)

### Überwachungs- und Berichte-Tools verwenden

Nutzen Sie die von Adobe Campaign angebotenen Funktionen, um Ihre Lieferbarkeit zu überwachen.

Mit Adobe Campaign können Sie die Leistung Ihrer Versand anhand einer Reihe integrierter Echtzeitindikatoren und -berichte überprüfen, um einen besseren Einblick in Ihre Versand zu erhalten.

Weitere Informationen finden Sie in den folgenden Abschnitten:

* [Zustellbarkeit überwachen](../../delivery/using/monitoring-deliverability.md)
* [Über die Versandverfolgung](../../delivery/using/about-delivery-monitoring.md)
* [Über native Berichte in Campaign](../../reporting/using/about-campaign-built-in-reports.md)

<!--TO REMOVE
## Background {#background}

Email deliverability presents a major challenge to marketers - whether they're sending a few thousand messages or several billion. One in five messages never reach the inbox, or their intended recipient.

Once relegated as a "technical issue" for the IT department, email deliverability continues to move higher on the marketing agenda. That's because savvy marketers recognize that although many of its elements are technical in nature, deliverability is ultimately a business issue with significant revenue implications.

Consider the email marketing funnel. Deliverability determines the number of messages received, which in turn impacts each subsequent stage of the funnel. Fewer emails received results in fewer opens, fewer clicks, and fewer conversions. **For companies with a large database, the difference between average and great deliverability could literally mean hundreds of thousands to millions of dollars in revenues.**

![](assets/deliverability_overview_1.png)

By settling for average (80%) deliverability, marketers are leaving significant conversions - and dollars - on the table.

What exactly is email deliverability? And how can marketers improve deliverability rates to widen the mouth of the funnel and squeeze more results from their email campaigns?

Email deliverability refers to the set of characteristics that determine a message's ability to reach its destination, via a personal e-mail address, within a short time, and with the expected quality in terms of content and format. These characteristics fall into four main categories: data quality, message and content, sending infrastructure, and reputation. Together, they form the foundation of a successful email deliverability program. This overview outlines the four fundamentals of email deliverability success and offers best practices for reaching the inbox and driving greater revenues from email marketing programs.

![](assets/deliverability_overview_2.png)-->

---
product: campaign
title: Über die Zustellbarkeit in Adobe Campaign Classic
description: Erfahren Sie mehr über die Verwaltung der Zustellbarkeit in Adobe Campaign 
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Deliverability
role: User
exl-id: dcd3a9f9-5fe9-4c28-a4a5-5aed67b036ab
source-git-commit: 0507e0372a81351adc145dafdd3cbe5d5422dc00
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 89%

---

# Steuern der Nachrichteninhalte{#control-message-content}

Um sicherzustellen, dass Ihre E-Mails Ihre Empfänger erreichen und um Ihre E-Mail-Zustellrate zu verbessern, müssen sie eine Reihe von Regeln beachten. Andernfalls kann der Inhalt bestimmter Nachrichten als Spam eingestuft werden. Adobe Campaign stellt Ihnen mehrere Tools zur Verfügung, die Ihnen ermöglichen, Ihre Inhalte entsprechend diesen Regeln zu erstellen.

Befolgen Sie beim Entwerfen Ihrer Nachrichteninhalte die folgenden Grundsätze:

* [Absenderadresse](#sender-address): Die Adresse muss den Absender explizit identifizieren. Die Domain muss im Besitz des Absenders und auf ihn registriert sein. Die Domain-Registrierung darf nicht privat erfolgen.
* [Personalisierung](#personalization): Die Personalisierung von Inhalten und das Definieren einer Sendezeit pro Empfänger erhöhen die Wahrscheinlichkeit, dass Ihre Nachricht geöffnet wird.
* Bilder und Text: Achten Sie auf ein angemessenes Verhältnis zwischen Text und Bildern (z. B. 60 % Text und 40 % Bilder).
* [Abmelde-Link](#opt-out) und Landingpage: Ein Abmelde-Link muss unbedingt vorhanden sein. Er muss gut sichtbar und gültig sein; außerdem muss das Formular funktionieren.
* Vorschau: Verwenden Sie die von Adobe Campaign angebotenen Tools, um den Inhalt Ihrer E-Mails zu überprüfen und zu optimieren ([Inbox Rendering](#message-responsiveness), [SpamAssassin](#spamassassin)).

Weitere Tipps zur Optimierung der Zustellbarkeit beim Entwerfen von Inhalten finden Sie im [Adobe-Handbuch mit den Best Practices zur Zustellbarkeit](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html?lang=de).

>[!NOTE]
>
>Weitere Informationen zum Bearbeiten von E-Mail-Inhalten finden Sie in der [ zu Campaign v8 ](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/emails/defining-the-email-content){target="_blank"}.

## Absenderadresse {#sender-address}

Bestimmte Internet-Anbieter überprüfen die Gültigkeit der Absenderadresse (**[!UICONTROL Von]**), bevor sie Nachrichten annehmen. Eine fehlerhafte Adresse kann dazu führen, dass sie vom empfangenden Server abgelehnt wird.

Sie müssen sicherstellen, dass auf Instanzebene (Menü **[!UICONTROL Tools > Erweitert > Bereitstellungassistent...]**) oder in den am häufigsten verwendeten Szenarien eine richtige Adresse angegeben wird.

Weitere Informationen hierzu finden Sie in der [ zu Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/emails/defining-the-email-content){target="_blank"}.

## Personalisierung {#personalization}

Um das Nutzererlebnis zu verbessern und Empfängerinnen und Empfänger dazu zu bewegen, Ihre E-Mail zu öffnen, ermöglicht Adobe Campaign Ihnen, Ihre Nachrichten zu personalisieren.

Weiterführende Informationen zur Verwendung von Personalisierungsfeldern in Adobe Campaign finden Sie in der [ zu Campaign v8 ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/personalize/personalization-fields){target="_blank"}.

## Ausschluss-Link und -Formular {#opt-out}

Bei der Analyse einer Nachricht wird standardmäßig von einer Typologieregel überprüft, ob ein Abmelde-Link vorhanden ist. Ist dies nicht der Fall, wird ein Warnhinweis erstellt. Sie können diese Regel so ändern, dass statt einer einfachen Warnung ein Fehler ausgelöst wird und ein Versand nicht mehr ohne diesen Link ausgeführt wird. Siehe die [Campaign v8-Dokumentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/delivery-analysis.html){target="_blank"}.

Sie müssen vor jedem Versand überprüfen, ob der Abmelde-Link korrekt funktioniert. Achten Sie beispielsweise beim Testversand darauf, dass der Link gültig ist, das Formular online ist und dass sich durch seine Validierung der Wert des Feldes **[!UICONTROL Diese Person nicht mehr kontaktieren]** auf **[!UICONTROL Ja]** ändert. Führen Sie diese Prüfung regelmäßig durch, da bei der manuellen Eingabe des Links oder der Änderung des Formulars Fehler auftreten können.

Erfahren Sie in der Dokumentation zu [ v8, wie Sie eine Opt-out-](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalization-blocks.html){target="_blank"} einfügen.

Wenn ein Abmeldeproblem erkannt wird, nachdem der Versand bereits begonnen hat, können Sie diejenigen, die auf den Ausschluss-Link klicken, manuell abmelden (z. B. über die gebündelte Aktualisierung), selbst wenn sie ihre Auswahl nicht bestätigen konnten.

Generell empfehlen wir, Empfänger nicht daran zu hindern, sich abzumelden, indem Sie von ihnen verlangen, Felder wie beispielsweise ihre E-Mail-Adresse oder ihren Namen auszufüllen. Das Formular sollte nur eine einzige Validierungsschaltfläche aufweisen und die Abstimmung sollte ausschließlich in der verschlüsselten Kennung stattfinden.

Das Anfordern einer zusätzlichen Bestätigung ist keine zuverlässige Methode: Ein Benutzer kann zwei E-Mail-Adressen in dasselbe Postfach umgeleitet haben (z. B. Vorname.Nachname@club.com und Vorname.Nachname@internet-club.com). Wenn sich der Empfänger nur an die erste Adresse erinnert und sich über eine an die andere Adresse gesendete Nachricht abmelden möchte, würde das Formular dies ablehnen, da die verschlüsselte Kennung und die eingegebene E-Mail-Adresse nicht übereinstimmen.

## Inbox Rendering {#message-responsiveness}

Bevor Sie Ihre Nachricht senden, können Sie testen, wie responsiv Ihre Nachricht ist, indem Sie überprüfen, wie sie auf verschiedenen Geräten aussehen wird. So wird sichergestellt, dass sie in unterschiedlichen Webclients, Webmails und Geräten optimal dargestellt wird.

Zu diesem Zweck unterstützt Adobe Campaign das Rendering und stellt dessen Ergebnisse in einem entsprechenden Bericht zur Verfügung. Dadurch können Sie sich ansehen, wie Nachrichten je nach verwendetem Empfangsmedium beim Empfänger dargestellt werden.

Weiterführende Informationen dazu finden Sie im Abschnitt [Inbox Rendering](inbox-rendering.md).

## SpamAssassin {#spamassassin}

Adobe Campaign bietet die Möglichkeit der Nutzung von SpamAssassin, einem Filterprogramm, das E-Mails eine Punktzahl zuordnet. Diese gibt Auskunft über die Wahrscheinlichkeit, von Anti-Spam-Programmen als unerwünscht eingestuft zu werden.

Auf diese Weise kann vor dem Versandstart im Tab **[!UICONTROL Vorschau]** das Spam-Risiko ausgewertet werden. Ein Hinweis zeigt die erfolgreiche Durchführung der Anti-Spam-Prüfung an.

Weitere Informationen finden Sie in diesem [Abschnitt](spamassassin.md).

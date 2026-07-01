---
product: campaign
title: Über die Zustellbarkeit in Adobe Campaign Classic
description: Erfahren Sie mehr über die Verwaltung der Zustellbarkeit in Adobe Campaign
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Deliverability
role: User
exl-id: dcd3a9f9-5fe9-4c28-a4a5-5aed67b036ab
TQID: https://experienceleague.adobe.com/5O5mdQrj0-Ts1C-lZRDHqDYwit4dSUOZHzG5SVDVitA
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2: id: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 854
ht-degree: 100%

---

# Steuern der Nachrichteninhalte{#control-message-content}

Um sicherzustellen, dass Ihre E-Mails Ihre Empfänger erreichen und um Ihre E-Mail-Zustellrate zu verbessern, müssen sie eine Reihe von Regeln beachten. Andernfalls kann der Inhalt bestimmter Nachrichten als Spam eingestuft werden. Adobe Campaign stellt Ihnen mehrere Tools zur Verfügung, die Ihnen ermöglichen, Ihre Inhalte entsprechend diesen Regeln zu erstellen.

Befolgen Sie beim Entwerfen Ihrer Nachrichteninhalte die folgenden Grundsätze:

* [Absenderadresse](#sender-address): Die Adresse muss den Absender explizit identifizieren. Die Domain muss im Besitz des Absenders und auf ihn registriert sein. Die Domain-Registrierung darf nicht privat erfolgen.
* [Personalisierung](#personalization): Die Personalisierung von Inhalten und das Definieren einer Sendezeit pro Empfänger erhöhen die Wahrscheinlichkeit, dass Ihre Nachricht geöffnet wird.
* Bilder und Text: Achten Sie auf ein angemessenes Verhältnis zwischen Text und Bildern (z. B. 60 % Text und 40 % Bilder).
* [Abmeldelink](#opt-out) und Landingpage: Der Abmeldelink muss vorhanden sein. Er muss gut sichtbar und gültig sein und das Formular muss funktionieren.
* Vorschau: Verwenden Sie die von Adobe Campaign angebotenen Tools, um den Inhalt Ihrer E-Mails zu überprüfen und zu optimieren ([Inbox Rendering](#message-responsiveness), [SpamAssassin](#spamassassin)).

Weitere Tipps zur Optimierung der Zustellbarkeit beim Entwerfen von Inhalten finden Sie im [Adobe-Handbuch mit den Best Practices zur Zustellbarkeit](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html?lang=de).

>[!NOTE]
>
>Weitere Informationen zum Bearbeiten von E-Mail-Inhalten finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=de){target="_blank"}.

## Absenderadresse {#sender-address}

Bestimmte ISPs überprüfen die Gültigkeit der Absenderadresse (**[!UICONTROL Von]**), bevor sie Nachrichten annehmen. Eine schlecht formulierte Adresse könnte vom Empfangs-Server abgelehnt werden.

Sie müssen sicherstellen, dass auf Instanzebene (Menü **[!UICONTROL Tools > Erweitert > Bereitstellungsassistent…]**) oder in den am häufigsten verwendeten Szenarien eine korrekte Adresse angegeben ist.

Weiterführende Informationen finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=de){target="_blank"}.

## Personalisierung {#personalization}

Um das Nutzererlebnis zu verbessern und Empfängerinnen und Empfänger dazu zu bewegen, Ihre E-Mail zu öffnen, ermöglicht Adobe Campaign Ihnen, Ihre Nachrichten zu personalisieren.

Weitere Informationen zur Verwendung von Personalisierungsfeldern in Adobe Campaign finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/personalize/personalization-fields){target="_blank"}.

## Ausschluss-Link und -Formular {#opt-out}

Bei der Analyse einer Nachricht wird standardmäßig von einer Typologieregel überprüft, ob ein Abmelde-Link vorhanden ist. Ist dies nicht der Fall, wird ein Warnhinweis erstellt. Sie können diese Regel so ändern, dass statt einer einfachen Warnung ein Fehler ausgelöst wird und ein Versand nicht mehr ohne diesen Link ausgeführt wird. Weiterführende Informationen dazu finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/delivery-analysis.html?lang=de){target="_blank"}.

Sie müssen vor jedem Versand überprüfen, ob der Abmelde-Link korrekt funktioniert. Achten Sie beispielsweise beim Testversand darauf, dass der Link gültig ist, das Formular online ist und dass sich durch seine Validierung der Wert des Feldes **[!UICONTROL Diese Person nicht mehr kontaktieren]** auf **[!UICONTROL Ja]** ändert. Führen Sie diese Prüfung regelmäßig durch, da bei der manuellen Eingabe des Links oder der Änderung des Formulars Fehler auftreten können.

Weitere Informationen zum Einfügen eines Abmelde-Links finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalization-blocks.html?lang=de){target="_blank"}.

Wenn ein Abmeldeproblem erkannt wird, nachdem der Versand bereits begonnen hat, können Sie diejenigen, die auf den Ausschluss-Link klicken, manuell abmelden (z. B. über die gebündelte Aktualisierung), selbst wenn sie ihre Auswahl nicht bestätigen konnten.

In der Regel sollten Sie Empfängerinnen und Empfängern, die sich abmelden möchten, dies nicht erschweren, indem Sie sie etwa dazu verpflichten, Felder wie ihre E-Mail-Adresse oder ihren Namen auszufüllen. Das Formular sollte nur über eine einzige Validierungsschaltfläche verfügen und die Abstimmung sollte nur mit der verschlüsselten Kennung durchgeführt werden.

Das Anfordern einer zusätzlichen Bestätigung ist keine zuverlässige Methode: Ein Benutzer kann zwei E-Mail-Adressen in dasselbe Postfach umgeleitet haben (z. B. Vorname.Nachname@club.com und Vorname.Nachname@internet-club.com). Wenn sich der Empfänger nur an die erste Adresse erinnert und sich über eine an die andere Adresse gesendete Nachricht abmelden möchte, würde das Formular dies ablehnen, da die verschlüsselte Kennung und die eingegebene E-Mail-Adresse nicht übereinstimmen.

## Rendern des Posteingangs {#message-responsiveness}

Bevor Sie Ihre Nachricht senden, können Sie testen, wie responsiv Ihre Nachricht ist, indem Sie überprüfen, wie sie auf verschiedenen Geräten aussehen wird. So wird sichergestellt, dass sie in unterschiedlichen Webclients, Webmails und Geräten optimal dargestellt wird.

Zu diesem Zweck unterstützt Adobe Campaign das Rendering und stellt dessen Ergebnisse in einem entsprechenden Bericht zur Verfügung. Dadurch können Sie sich ansehen, wie Nachrichten je nach verwendetem Empfangsmedium beim Empfänger dargestellt werden.

Weiterführende Informationen dazu finden Sie im Abschnitt [Inbox Rendering](inbox-rendering.md).

## SpamAssassin {#spamassassin}

Adobe Campaign kann für die Nutzung von SpamAssassin konfiguriert werden. Dies ermöglicht die Bewertung von E-Mails zur Bestimmung, ob für eine Nachricht das Risiko besteht, bei Empfang von Anti-Spam-Tools als Spam eingeordnet zu werden.

Die Risiken können vor Versandstart in der Registerkarte **[!UICONTROL Vorschau]** evaluiert werden. Eine Warnmeldung gibt Auskunft über das Ergebnis des Tests.

Weitere Informationen finden Sie in diesem [Abschnitt](spamassassin.md).

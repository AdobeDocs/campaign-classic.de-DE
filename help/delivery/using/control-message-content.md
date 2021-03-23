---
solution: Campaign Classic
product: campaign
title: Über die Zustellbarkeit in Adobe Campaign Classic
description: Erfahren Sie mehr über die Verwaltung der Zustellbarkeit in Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: d6a581ae86e50c17ac20fe54baf305b864e11790
workflow-type: tm+mt
source-wordcount: '774'
ht-degree: 33%

---


# Steuern des Nachrichteninhalts{#control-message-content}

Um sicherzustellen, dass Ihre E-Mails Ihre Empfänger erreichen und Ihre E-Mail-Zustellungsrate verbessern, müssen sie eine Reihe von Regeln beachten. Andernfalls kann der Inhalt bestimmter Nachrichten als Spam erkannt werden. Adobe Campaign stellt Ihnen mehrere Tools zur Verfügung, mit denen Sie Ihre Inhalte mit diesen Regeln in Einklang bringen können.

Befolgen Sie beim Entwerfen Ihres Nachrichteninhalts die folgenden Grundsätze:

* [Absenderadresse](#sender-address): die Adresse muss den Absender explizit identifizieren. Die Domäne muss sich im Besitz des Absenders befinden und beim Absender registriert sein. Das Domänenregister darf nicht privatisiert werden.
* [Personalisierung](#personalization): Die Personalisierung von Inhalten und das Definieren einer Sendezeit pro Empfänger erhöhen die Wahrscheinlichkeit, dass Ihre Nachricht geöffnet wird.
* Bilder und Text: ein angemessenes Verhältnis von Text und Bild (z. B. 60 % Text und 40 % Bilder).
* [Abmeldung ](#opt-out) und Landingpage: der Link zur Abmeldung ist unverzichtbar. Es muss sichtbar und gültig sein, und das Formular muss funktionsfähig sein.
* Vorschau: Verwenden Sie die von Adobe Campaign angebotenen Tools, um den Inhalt Ihrer E-Mail zu überprüfen und zu optimieren ([Inbox-Rendering](#message-responsiveness), [SpamAssassin](#spamassassin)).

Weitere Tipps zur Optimierung der Bereitstellbarkeit von Inhalten finden Sie im Leitfaden [Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html) zur Adobe-Bereitstellung.

>[!NOTE]
>
>Weitere Informationen zum Bearbeiten von E-Mail-Inhalten finden Sie unter [Definieren des E-Mail-Inhalts](../../delivery/using/defining-the-email-content.md) und [Erstellen personalisierter Inhalte](../../delivery/using/design-and-personalize.md).

## Absenderadresse {#sender-address}

Bestimmte ISPs prüfen die Gültigkeit der Absenderadresse (**[!UICONTROL Von]**), bevor sie Nachrichten annehmen. Eine schlecht geformte Adresse kann dazu führen, dass sie vom empfangenden Server abgelehnt wird.

Sie müssen sicherstellen, dass auf Instanzebene eine korrekte Adresse angegeben wird (Menü **[!UICONTROL Tools > Erweitert > Bereitstellungsassistent...).]**) oder in den am häufigsten verwendeten Szenarien.

Weitere Informationen hierzu finden Sie unter [Definieren des Absenders](../../delivery/using/defining-the-email-content.md).

## Personalisierung     {#personalization}

Um die Benutzererfahrung zu verbessern und Ihre E-Mail-Adresse zu öffnen, können Sie mit Adobe Campaign Ihre Nachrichten personalisieren.

Weitere Informationen zur Verwendung von Personalisierungsfeldern in Adobe Campaign finden Sie unter [dieser Abschnitt](../../delivery/using/personalization-fields.md).

Einige Tipps zur Optimierung der Personalisierung beim Erstellen Ihres Inhalts finden Sie in [diesem Abschnitt](../../delivery/using/design-and-personalize.md#optimize-personalization).

## Abmelde-Link und -Formular {#opt-out}

Standardmäßig prüft eine [Typologieregel](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) bei der Analyse der Nachricht, ob ein Ausschluss-Link enthalten ist, und gibt eine Warnung aus, wenn dieser Link fehlt. Sie können diese Regel so ändern, dass anstelle einer einfachen Warnung ein Fehler ausgegeben wird und ein Versand nicht ohne diesen Link verlassen kann.

Prüfen Sie vor jedem Versand, ob der Abmelde-Link ordnungsgemäß funktioniert. Achten Sie beispielsweise beim Testversand darauf, dass der Link gültig ist, das Formular online ist und dass sich durch seine Validierung der Wert des Feldes **[!UICONTROL Diese Person nicht mehr kontaktieren]** auf **[!UICONTROL Ja]** ändert. Führen Sie diese Prüfung regelmäßig durch, da bei der manuellen Eingabe des Links oder der Änderung des Formulars Fehler auftreten können.

[In diesem Abschnitt](../../delivery/using/personalization-blocks.md#personalization-blocks-example) erfahren Sie, wie man einen Ausschluss-Link einfügt.

Wenn ein Abmeldeproblem erkannt wird, nachdem der Versand bereits begonnen hat, können Sie diejenigen, die auf den Abmelde-Link klicken, manuell abmelden (z. B. über die gebündelte Aktualisierung), selbst wenn sie ihre Auswahl nicht bestätigen konnten.

In der Regel sollten Sie Empfängern, die sich für eine Teilnahme ausschließen möchten, nicht die Möglichkeit geben, sich auszuschließen, indem Sie beispielsweise Felder wie die E-Mail-Adresse oder den Namen ausfüllen. Das Formular sollte nur über eine Überprüfungsschaltfläche verfügen, und der Abgleich sollte nur mit dem verschlüsselten Bezeichner durchgeführt werden.

Die Anforderung zusätzlicher Bestätigung ist nicht zuverlässig: Ein Benutzer kann zwei E-Mail-Adressen in dasselbe Feld umgeleitet haben (z. B. firstname.lastname@club.com und firstname.lastname@internet-club.com). Wenn der Empfänger nur die erste Adresse speichern kann und sich über eine an die andere Adresse gesendete Nachricht abmelden möchte, verweigert das Formular dies, da die verschlüsselte Kennung und die eingegebene E-Mail-Adresse nicht übereinstimmen.

## Inbox Rendering {#message-responsiveness}

Bevor Sie Ihre Nachricht senden, können Sie die Reaktionsgeschwindigkeit Ihrer Nachricht testen, indem Sie überprüfen, wie Ihre Nachricht auf verschiedenen Geräten aussehen wird. So wird sichergestellt, dass sie in unterschiedlichen Webclients, Webmails und Geräten optimal dargestellt wird.

Zu diesem Zweck unterstützt Adobe Campaign das Rendering und stellt dessen Ergebnisse in einem entsprechenden Bericht zur Verfügung. Dadurch können Sie sich ansehen, wie Nachrichten je nach verwendetem Empfangsmedium beim Empfänger dargestellt werden.

Weiterführende Informationen dazu finden Sie im Abschnitt [Inbox Rendering](../../delivery/using/inbox-rendering.md).

## SpamAssassin {#spamassassin}

Adobe Campaign bietet die Möglichkeit der Nutzung von SpamAssassin, einem Filterprogramm, das E-Mails eine Punktzahl zuordnet. Diese gibt Auskunft über die Wahrscheinlichkeit, von Anti-Spam-Programmen als unerwünscht eingestuft zu werden.

Vor dem Starten eines Versands können Sie mit dem Register **[!UICONTROL Vorschau]** die Risiken bewerten. Eine Warnmeldung gibt das Ergebnis des Tests an.

Weitere Informationen finden Sie in diesem [Abschnitt](../../delivery/using/spamassassin.md).
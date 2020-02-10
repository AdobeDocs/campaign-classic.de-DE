---
title: Informationen zur Lieferbarkeit in Adobe Campaign Classic
description: Erfahren Sie mehr über die Verwaltung der Zustellbarkeit in Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 68756f920fbc8658cff552615adbf023b4c5e3aa

---


# Inhalt der Nachricht steuern{#control-message-content}

Um Ihre E-Mail-Zustellungsrate zu verbessern und sicherzustellen, dass Ihre E-Mails an Ihre Empfänger gelangen, muss die E-Mail eine Reihe von Regeln beachten, die nachfolgend beschrieben werden.

## Absenderadresse {#sender-address}

Bestimmte ISPs prüfen die Gültigkeit der Absenderadresse (Von), bevor sie Nachrichten annehmen. Eine schlecht geformte Adresse kann dazu führen, dass sie vom empfangenden Server abgelehnt wird. Sie müssen sicherstellen, dass eine richtige Adresse auf Instanzebene (Menü **[!UICONTROL Tools > Advanced > Deployment wizard...]**) oder in den am häufigsten verwendeten Szenarien angegeben wird.

## Abmelde-Link und -Formular {#opt-out}

Bei der Analyse einer Nachricht wird standardmäßig von einer Typologieregel überprüft, ob ein Abmelde-Link vorhanden ist. Ist dies nicht der Fall, wird ein Warnhinweis erstellt. Sie können diese Regel ändern, sodass anstatt eines einfachen Warnhinweises ein Fehler angezeigt wird und ein Versand ohne diesen Link nicht möglich ist.

Sie müssen vor jedem Senden überprüfen, ob der Ausschluss-Link korrekt funktioniert. Achten Sie beispielsweise beim Senden des Nachweises darauf, dass der Link gültig ist, dass das Formular online ist und dass bei der Überprüfung dieser Wert den Wert des **[!UICONTROL No longer contact this recipient]** Felds in **[!UICONTROL Yes]**&#x200B;ändert. Sie sollten diese Überprüfung systematisch durchführen, da menschliches Versagen immer möglich ist, wenn Sie den Link eingeben oder das Formular ändern.

Wenn ein Abmeldeproblem erkannt wird, nachdem der Versand bereits begonnen hat, können Sie diejenigen, die auf den Abmelde-Link klicken, manuell abmelden (z. B. über die gebündelte Aktualisierung), selbst wenn sie ihre Auswahl nicht bestätigen konnten.

Generell empfehlen wir, Empfänger nicht daran zu hindern, sich abzumelden, indem Sie von ihnen verlangen, Felder wie beispielsweise ihre E-Mail-Adresse oder ihren Namen auszufüllen. Das Formular sollte nur eine einzige Validierungsschaltfläche aufweisen und die Abstimmung sollte ausschließlich in der verschlüsselten Kennung stattfinden. Eine zusätzliche Bestätigung zu verlangen ist keine verlässliche Methode: Ein Benutzer könnte zwei E-Mail-Adressen besitzen, die zum selben Postfach gesendet werden (z. B. vorname.nachname@club.com und vorname.nachname@internet-klub.com). Wenn sich der Empfänger nur an die erste Adresse erinnert und sich über eine an die andere Adresse gesendete Nachricht abmelden möchte, würde das Formular dies ablehnen, da die verschlüsselte Kennung und die eingegebene E-Mail-Adresse nicht übereinstimmen.

## SpamAssassin {#spamassassin}

Adobe Campaign bietet die Möglichkeit der Nutzung von SpamAssassin, einem Filterprogramm, das E-Mails eine Punktzahl zuordnet. Diese gibt Auskunft über die Wahrscheinlichkeit, von Anti-Spam-Programmen als unerwünscht eingestuft zu werden.

Vor dem Starten einer Bereitstellung können Sie mit der Registerkarte &quot;Vorschau&quot;die Risiken bewerten. Eine Warnmeldung gibt das Ergebnis des Tests an.

Weitere Informationen finden Sie in diesem [Abschnitt](../../delivery/using/spamassassin.md).
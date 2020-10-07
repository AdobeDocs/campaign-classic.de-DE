---
title: Über die Zustellbarkeit in Adobe Campaign Classic
description: Erfahren Sie mehr über die Verwaltung der Zustellbarkeit in Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 100%

---


# Steuern des Nachrichteninhalts{#control-message-content}

Wenn Sie die Zustellrate Ihrer E-Mails optimieren möchten, müssen die Nachrichten einer Reihe von Regeln entsprechen, die im Folgenden beschrieben werden.

## Absenderadresse {#sender-address}

Manche ISPs prüfen die Gültigkeit der Absenderadresse (Von), bevor sie Nachrichten akzeptieren. Eine schlecht formulierte Adresse könnte vom Empfangs-Server abgelehnt werden. Achten Sie darauf, dass auf Instanzenebene (Menü **[!UICONTROL Werkzeuge > Erweitert > Softwareverteilungs-Assistent...]**) oder in den am häufigsten verwendeten Szenarios eine korrekte Adresse vorhanden ist.

## Abmelde-Link und -Formular {#opt-out}

Bei der Analyse einer Nachricht wird standardmäßig von einer Typologieregel überprüft, ob ein Abmelde-Link vorhanden ist. Ist dies nicht der Fall, wird ein Warnhinweis erstellt. Sie können diese Regel ändern, sodass anstatt eines einfachen Warnhinweises ein Fehler angezeigt wird und ein Versand ohne diesen Link nicht möglich ist.

Prüfen Sie vor jedem Versand, ob der Abmelde-Link ordnungsgemäß funktioniert. Achten Sie beispielsweise beim Testversand darauf, dass der Link gültig ist, das Formular online ist und dass sich durch seine Validierung der Wert des Feldes **[!UICONTROL Diese Person nicht mehr kontaktieren]** auf **[!UICONTROL Ja]** ändert. Führen Sie diese Prüfung regelmäßig durch, da bei der manuellen Eingabe des Links oder der Änderung des Formulars Fehler auftreten können.

Wenn ein Abmeldeproblem erkannt wird, nachdem der Versand bereits begonnen hat, können Sie diejenigen, die auf den Abmelde-Link klicken, manuell abmelden (z. B. über die gebündelte Aktualisierung), selbst wenn sie ihre Auswahl nicht bestätigen konnten.

Generell empfehlen wir, Empfänger nicht daran zu hindern, sich abzumelden, indem Sie von ihnen verlangen, Felder wie beispielsweise ihre E-Mail-Adresse oder ihren Namen auszufüllen. Das Formular sollte nur eine einzige Validierungsschaltfläche aufweisen und die Abstimmung sollte ausschließlich in der verschlüsselten Kennung stattfinden. Eine zusätzliche Bestätigung zu verlangen ist keine verlässliche Methode: Ein Benutzer könnte zwei E-Mail-Adressen besitzen, die zum selben Postfach gesendet werden (z. B. vorname.nachname@club.com und vorname.nachname@internet-klub.com). Wenn sich der Empfänger nur an die erste Adresse erinnert und sich über eine an die andere Adresse gesendete Nachricht abmelden möchte, würde das Formular dies ablehnen, da die verschlüsselte Kennung und die eingegebene E-Mail-Adresse nicht übereinstimmen.

## SpamAssassin {#spamassassin}

Adobe Campaign bietet die Möglichkeit der Nutzung von SpamAssassin, einem Filterprogramm, das E-Mails eine Punktzahl zuordnet. Diese gibt Auskunft über die Wahrscheinlichkeit, von Anti-Spam-Programmen als unerwünscht eingestuft zu werden.

Auf diese Weise kann vor dem Versandstart im Vorschau-Tab das Spam-Risiko abgeschätzt werden. Ein Hinweis zeigt die erfolgreiche Durchführung der Anti-Spam-Prüfung an.

Weitere Informationen finden Sie in diesem [Abschnitt](../../delivery/using/spamassassin.md).
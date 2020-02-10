---
title: Zweck
seo-title: Zweck
description: Zweck
seo-description: null
page-status-flag: never-activated
uuid: 4452d839-318a-49d8-8abb-4ba04c803e9f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: 7b8ab9d6-e47e-46d8-99df-da793486654c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Zweck{#purpose}

In diesem Anwendungsbeispiel sollen E-Mail-Anhänge dynamisch zu ausgehenden Sendungen hinzugefügt werden.

In diesem Anwendungsbeispiel werden wir zeigen, wie Transaktions-E-Mails mit individuellen/personalisierten Anhängen gesendet werden. Die Anhänge werden nicht vorab auf den Transactional-Messaging-Server hochgeladen, sondern werden unmittelbar erstellt.

Wenn Sie Kundeninteraktionen oder Daten erfassen, müssen Sie diese Informationen unter Umständen am Ende dieses Vorgangs beispielsweise in Form einer an eine E-Mail angehängten PDF-Datei an den Kunden zurücksenden. Hier werden die allgemeinen Schritte für diesen Vorgang beschrieben.

1. Der Kunde öffnet die Webseite und findet ein Produkt, das er kaufen möchte.
1. Der Kunde wählt das Produkt aus und passt einige Optionen an.
1. Der Kunde schließt die Transaktion ab.
1. An den Kunden wird eine E-Mail zur Bestätigung der Transaktion gesendet. Wir möchten in der E-Mail keine personenbezogenen Informationen senden, weshalb wir eine sichere PDF-Datei erstellen und an die E-Mail anfügen.
1. Der Kunde erhält die E-Mail und den Anhang mit den benötigten Informationen.

In diesem Beispiel wird der Anhang nicht vorab erstellt, sondern unmittelbar an die ausgehende E-Mail angehängt. Darüber hinaus können Sie den Inhalt des Anhangs personalisieren. Wenn der Anhang außerdem wie im obigen Beispiel einer Transaktion zugeordnet ist, muss er möglicherweise dynamische Daten enthalten, die im Rahmen der Customer Journey erstellt werden. Auf diese Weise angefügte PDF-Dateien optimieren auch die Sicherheit, da Sie sie verschlüsseln und per HTTPS senden können.

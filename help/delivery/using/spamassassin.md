---
product: campaign
title: SpamAssassin
description: Erfahren Sie, wie Sie mit SpamAssassin die Erkennung von Spam-E-Mails einrichten
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Email, Deliverability
role: User
exl-id: 8be6836d-f7dc-4199-b2b2-b6a9cac9d162
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 63%

---

# SpamAssassin{#spamassassin}

Adobe Campaign kann für die Verwendung mit [SpamAssassin](https://spamassassin.apache.org) konfiguriert werden, einem Drittanbieterdienst, der zum Filtern von E-Mail-Spam verwendet wird. Auf diese Weise können Sie E-Mails bewerten, um festzustellen, ob bei einer Nachricht das Risiko besteht, dass sie von den Anti-Spam-Tools, die beim Empfang verwendet werden, als Spam eingestuft wird.

SpamAssassin nutzt eine Vielzahl von Spam-Erkennungs-Methoden, darunter:

* Spam-Erkennung auf der Basis des DNS und der unscharfen Prüfsumme
* Bayes&#39;sche Filtertechnologie
* Externe Programme
* Blockierungslisten
* Online-Datenbanken

>[!NOTE]
>
>SpamAssassin muss auf dem Adobe Campaign-Anwendungs-Server installiert und konfiguriert werden. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-spamassassin.md).
>
>Die Regeln, mit denen bestimmt wird, ob ein Element Spam ist oder nicht, werden über SpamAssassin verwaltet und können von einem Administrator mit den entsprechenden Berechtigungen bearbeitet werden.

## Verwenden von SpamAssassin in Campaign {#using-spamassassin}

Nachdem Sie Ihren E-Mail-Versand erstellt und seinen Inhalt definiert haben, folgen Sie den unten stehenden Schritten, um die Risiken auszuwerten.

Weiterführende Informationen zur Erstellung und Konzeption eines Versands finden Sie in [diesem Abschnitt](about-email-channel.md).

1. Gehen Sie zum Tab **[!UICONTROL Vorschau]**.
1. Wählen Sie einen Empfänger aus, um Ihren Versand in der Vorschau zu betrachten.

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >Wenn Sie keinen Empfänger auswählen, kann die Anti-Spam-Prüfung nicht durchgeführt werden.

1. Eine Warnmeldung gibt das Ergebnis des Tests aus. Wenn ein hohes Risiko festgestellt wird, wird die folgende Warnmeldung angezeigt:

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. Wählen Sie den Link **[!UICONTROL Details...]** neben dem Warnhinweis aus.
1. Wählen Sie den Tab **[!UICONTROL Anti-Spam-Prüfung]** aus.
1. Gehen Sie zum Bereich **[!UICONTROL Punktzahl/Regel/Beschreibung]**, um sich die Gründe für das Risiko anzusehen.

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>Jedes Mal, wenn Sie auf **[!UICONTROL Anti-Spam-Überprüfung]** klicken, wird der SpamAssassin-Dienst aufgerufen und die Nachricht wird erneut auf Anti-Spam-Erkennung analysiert. Stellen Sie sicher, dass Sie Ihren Inhalt geändert haben, bevor Sie die Anti-Spam-Analyse erneut ausführen.

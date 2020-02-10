---
title: SpamAssassin
seo-title: SpamAssassin
description: SpamAssassin
seo-description: null
page-status-flag: never-activated
uuid: 4f439432-4215-42ed-8f92-b4ca8dd92726
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: d41658ab-ee79-4a5c-a165-d94b81eb2b33
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# SpamAssassin{#spamassassin}

## Über SpamAssassin {#about-spamassassin}

Adobe Campaign bietet die Möglichkeit der Nutzung von [SpamAssassin](https://spamassassin.apache.org), einem Drittanbieterdienst zum Filtern von E-Mail-Spam. Mit diesem Filterprogramm wird E-Mails eine Punktzahl zugeordnet. Diese gibt Auskunft über die Wahrscheinlichkeit, von Anti-Spam-Programmen als unerwünscht eingestuft zu werden.

SpamAssassin nutzt eine Vielzahl von Spam-Erkennungs-Methoden, darunter:

* Spam-Erkennung auf der Basis des DNS und der unscharfen Prüfsumme
* Bayes&#39;sche Filtertechnologie
* Externe Programme
* Blacklists
* Online-Datenbanken

>[!NOTE]
>
>SpamAssassin muss auf dem Adobe-Campaign-Anwendungsserver installiert und konfiguriert werden. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-spamassassin.md).
>
>Die Regeln, mit denen bestimmt wird, ob ein Element Spam ist oder nicht, werden über SpamAssassin verwaltet und können von einem Administrator mit den entsprechenden Berechtigungen bearbeitet werden.

## Verwendung von SpamAssassin {#using-spamassassin}

Nachdem Sie Ihren E-Mail-Versand erstellt und seinen Inhalt definiert haben, folgen Sie den unten stehenden Schritten, um die Risiken zu evaluieren.

Weiterführende Informationen zur Erstellung und Konzeption eines Versands finden Sie in [diesem Abschnitt](../../delivery/using/about-email-channel.md).

1. Go to the **[!UICONTROL Preview]** tab.
1. Wählen Sie einen Empfänger aus, um Ihren Versand in der Vorschau zu betrachten.

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >Wenn Sie keinen Empfänger auswählen, kann die Anti-Spam-Prüfung nicht durchgeführt werden.

1. In einem Warnhinweis wird das Testergebnis angezeigt. Wenn ein hohes Risiko besteht, wird der folgende Warnhinweis angezeigt:

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. Click the **[!UICONTROL More...]** link next to the warning.
1. Wählen Sie die **[!UICONTROL Anti-spam checking]** Registerkarte.
1. Go to the **[!UICONTROL Points / Rule / Description]** section to view the reasons for this risk.

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>Jedes Mal, wenn Sie auf den **[!UICONTROL Anti-spam checking]** Dienst klicken, wird der SpamAssassin-Dienst aufgerufen und die Nachricht wird erneut zur Spam-Erkennung analysiert. Vergewissern Sie sich, dass Sie Ihren Inhalt geändert haben, bevor Sie die Anti-Spam-Analyse erneut ausführen.

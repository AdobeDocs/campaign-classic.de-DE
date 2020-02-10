---
title: Getrackte Links konfigurieren
seo-title: Getrackte Links konfigurieren
description: Getrackte Links konfigurieren
seo-description: null
page-status-flag: never-activated
uuid: 0fb41a43-8a84-4a61-bf93-97e1d448a5ec
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: tracking-messages
discoiquuid: 9cae3861-88eb-447a-aa23-9d1de0710eec
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Getrackte Links konfigurieren{#how-to-configure-tracked-links}

Sie haben die Möglichkeit, für jeden Versand die Zustellung und Klicks auf enthaltene Links zu verfolgen. Auf diese Weise kann das Verhalten der Nachrichtenempfänger analysiert werden.

>[!NOTE]
>
>Der Begriff &quot;Tracking&quot; bezieht sich auf den Umgang der Empfänger mit Nachrichten, während &quot;Webtracking&quot; das Surfverhalten von Webseitenbesuchern dokumentiert (besuchte Seiten, Bestellungen usw.).
>
>Die Konfiguration des Webtrackings wird in [diesem Abschnitt](../../configuration/using/about-web-tracking.md) beschrieben.

Das Tracking von Nachrichten ist standardmäßig aktiviert. Um das Tracken von URLs zu personalisieren, gehen Sie folgendermaßen vor:

1. Select the **[!UICONTROL Display URLs]** option in the lower section of the delivery wizard, under the message content.

   ![](assets/s_ncs_user_email_del_display_urls.png)

   Sobald Sie eine URL in der Liste der getrackten URLs markieren, wird sie im Versandinhalt optisch hervorgehoben. (Dies gilt nicht für den Mirrorseite-Link und den Abmelde-Link, die zum Standard-Package der Anwendung gehören.)

   ![](assets/s_ncs_user_email_del_show_urls.png)

1. Aktivieren oder deaktivieren Sie das Tracking für jede in der Nachricht enthaltene URL.

   >[!CAUTION]
   >
   >Wenn die URL des Links als Titel verwendet wird, empfiehlt es sich, das Tracking zu deaktivieren, damit die Nachricht nicht wegen des Verdachts auf Phishing zurückgewiesen wird.
   >
   >Wenn Sie z. B. die URL www.adobe.com in die Nachricht einfügen und das Tracking aktivieren, wird der Hyperlink in https://nlt.adobe.net/r/?id=xxxxxx umgewandelt. Dieser wird u. U. von den E-Mail-Programmen der Empfänger als Spam interpretiert.

1. Der Tracking-Titel kann angepasst werden. Doppelklicken Sie auf den zu ändernden Titel und geben Sie den neuen Titel ein.

   >[!NOTE]
   >
   >Die Anpassung der Titel der getrackten URLs dient auch der besseren Lesbarkeit der Tracking-Informationen. Identische URLs oder Titel werden bei der Klick-Zählung zusammengefasst.

1. Sie können den gewünschten Tracking-Modus in der Spalte **[!UICONTROL Tracking]** ändern. Wählen Sie dazu einen neuen Modus wie unten dargestellt aus.

   ![](assets/s_ncs_user_select_tracking_mode.png)

   Für jede einzelne URL können Sie den Tracking-Modus auf einen dieser Werte festlegen.

   * **[!UICONTROL Enabled]** : aktiviert die Verfolgung für diese URL.
   * **[!UICONTROL Not tracked]** : deaktiviert die Verfolgung für diese URL.
   * **[!UICONTROL Always enabled]** : aktiviert immer die Verfolgung dieser URL. Diese Informationen werden gespeichert, damit die Verfolgung beim nächsten Mal automatisch aktiviert wird, wenn die URL in einem zukünftigen Nachrichtensatz erneut angezeigt wird.
   * **[!UICONTROL Never tracked]** : aktiviert nie die Verfolgung dieser URL. Diese Informationen werden gespeichert, damit die Verfolgung beim nächsten Mal automatisch deaktiviert wird, wenn die URL in einer zukünftigen Meldung erneut angezeigt wird.
   * **[!UICONTROL Opt-out]** : Diese URL wird als Opt-out-URL behandelt.
   * **[!UICONTROL Mirror page]** : betrachtet diese URL als Spiegelseite-URL.

1. Darüber hinaus können Sie in der Dropdown-Liste der **[!UICONTROL Category]** Spalte eine Kategorie für jede verfolgte URL auswählen. Diese Kategorien können in Berichten angezeigt werden, z. B. in **[!UICONTROL URLs and click streams]** (siehe [diesen Abschnitt](../../reporting/using/reports-on-deliveries.md#urls-and-click-streams)). Kategorien werden in einer bestimmten Aufzählung definiert: **[!UICONTROL urlCategory]** (siehe [Verwalten von Enumerationen](../../platform/using/managing-enumerations.md)).

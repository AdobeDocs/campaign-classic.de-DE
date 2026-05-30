---
product: campaign
title: Personalisieren der Emoticon-Liste
description: Erfahren Sie, wie Sie die Emoticon-Liste unter Verwendung von Adobe Campaign personalisieren können
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Email, Push
role: User, Developer
hide: true
exl-id: b8642df3-1960-4f2c-8273-c3988a3e85f0
TQID: https://experienceleague.adobe.com/QtOpkl4Sa6PJe5IGz4ffvpQdl2QfKA5J47WBKtIg2j8
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
feature_v2: id: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 481
ht-degree: 89%

---

# Personalisieren der Emoticon-Liste {#customize-emoticons}

Die im Popup-Fenster angezeigte Emoticon-Liste wird von einer Auflistung gesteuert, mit der Sie Werte in einer Liste anzeigen können, um die Auswahl zu beschränken, die der Benutzer für ein bestimmtes Feld hat.
Die Reihenfolge der Emoticon-Listen kann angepasst werden. Sie können Ihrer Liste auch weitere Emoticons hinzufügen.

Beachten Sie, dass Emoticons nur für E-Mails und Push-Benachrichtigungen verfügbar sind. Weiterführende Informationen finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=de#inserting-emoticons){target="_blank"}.


## Hinzufügen eines neuen Emoticons {#add-new-emoticon}

>[!CAUTION]
>
>Die Emoticon-Liste kann maximal 81 Einträge enthalten.

1. Wählen Sie ein neues Emoticon, das Sie hinzufügen möchten, von dieser [Seite](https://unicode.org/emoji/charts/full-emoji-list.html) aus. Beachten Sie, dass es mit den verschiedenen Plattformen wie Browser und Betriebssystem kompatibel sein muss.

1. Wählen Sie im **[!UICONTROL Explorer]****[!UICONTROL Administration]** > **[!UICONTROL Plattform]** > **[!UICONTROL Aufzählungen]** und klicken Sie auf die native Aufzählung **[!UICONTROL Emoticon-Liste]**.

   >[!NOTE]
   >
   >Native Aufzählungen können nur von einem Administrator Ihrer Adobe Campaign Classic Console verwaltet werden.

   ![](assets/emoticon_1.png)

1. Wählen Sie **[!UICONTROL Hinzufügen]** aus.

1. Füllen Sie die Felder aus:

   * **[!UICONTROL U+]**: Code des neuen Emoticons. Die Liste der Codes von Emoticons finden Sie auf dieser [Seite](https://unicode.org/emoji/charts/full-emoji-list.html).
Um Kompatibilitätsprobleme zu vermeiden, empfehlen wir Ihnen, Emoticons auszuwählen, die auf Browsern und auf jedem Betriebssystem unterstützt werden.

   * **[!UICONTROL Titel]**: Bezeichnung für Ihr neues Emoticon.

   ![](assets/emoticon_5.png)

1. Klicken Sie auf **[!UICONTROL OK]** und dann **[!UICONTROL Speichern]**, wenn Ihre Konfiguration abgeschlossen ist.
Ihr neues Emoticon wird automatisch im Shop platziert.

1. Um es im Fenster **[!UICONTROL Emoticon einfügen]** Ihrer Sendungen anzuzeigen, wählen Sie das neu erstellte Emoticon aus, indem Sie darauf doppelklicken.

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Anzeigeposition]** aus, an welchem Platz das neue Emoticon angezeigt werden soll. Beachten Sie, dass bei Auswahl einer bereits zugewiesenen Anzeigeposition das vorhandene Emoticon automatisch in den Speicher verschoben wird.

   <br>In diesem Beispiel haben wir die Anzeigeposition Nr. 61 gewählt. Das bedeutet, dass ein vorhandener Eintrag an diesem Platz automatisch in den Speicher verschoben wird und unser neuer Eintrag dessen Position in der Aufzählung einnimmt.

   ![](assets/emoticon_2.png)

1. Ihr neues Emoticon wurde der nativen Aufzählung **[!UICONTROL Emoticon einfügen]** hinzugefügt. Sie können seine **[!UICONTROL Anzeigeposition]** jederzeit ändern oder das Emoticon in den Speicher verschieben, wenn Sie es nicht mehr benötigen.

1. Damit Ihre Änderungen wirksam werden, trennen Sie die Verbindung mit Adobe Campaign Classic und stellen Sie sie erneut her. Wenn Ihr neues Emoticon im Popup-Fenster **[!UICONTROL Emoticon einfügen]** immer noch nicht angezeigt wird, müssen Sie möglicherweise Ihren Cache löschen. Weiterführende Informationen hierzu finden Sie in diesem [Abschnitt](../../platform/using/faq-campaign-classic-v7.md#how-do-i-clear-console-cache).

1. Ihr neues Emoticon finden Sie in Ihren Sendungen jetzt im Popup-Fenster **[!UICONTROL Emoticon einfügen]** an der 61. Position (wie in den vorherigen Schritten konfiguriert). Weiterführende Informationen zur Verwendung von Emoticons in Ihren Sendungen finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=de#inserting-emoticons){target="_blank"}.

   ![](assets/emoticon_4.png)

1. Wenn die folgenden Emoticons im Popup-Fenster **[!UICONTROL Emoticon einfügen]** angezeigt werden, heißt das, dass sie nicht richtig konfiguriert wurden. Überprüfen Sie, ob Ihr **[!UICONTROL U+]**-Code oder die **[!UICONTROL Anzeigeposition]** in der **[!UICONTROL Emoticon-Liste]** korrekt sind.

   ![](assets/emoticon_6.png)

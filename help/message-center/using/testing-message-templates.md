---
product: campaign
title: Testen von Transaktionsnachrichtenvorlagen
description: Erfahren Sie, wie Sie in Adobe Campaign Classic Testadressen in Transaktionsnachrichten zur Anzeige in einer Vorschau und zum Testen verwalten
feature: Transactional Messaging, Message Center, Templates
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 417004c9-ed96-4b98-a518-a3aa6123ee7b
TQID: 'https://experienceleague.adobe.com/jcmXX4aMPaTBatt4m3s-IAaAeoXnjmPaEE4oqIDoIOI'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
  - id: baf8e746-117b-5e73-b179-0a83edc0295f
    internal-label: Templates
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
source-git-commit: 617db6f51887118c965b8938b2b9f14335293875
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 60%
---
# Testen von Transaktionsnachrichtenvorlagen {#testing-message-templates}

Sobald Ihre [Nachrichtenvorlage](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional-template){target="_blank"} (Dokumentation zu Campaign v8) fertig ist, führen Sie die folgenden Schritte aus, um sie in der Vorschau anzuzeigen und zu testen.

Im Zuge der Umstellung von Campaign v7 auf v8 wurde der Campaign Classic-Dokumentationssatz optimiert und neu organisiert. Allgemeine Funktionen sind jetzt nur noch in der Dokumentation zu Campaign v8 verfügbar. Informationen zum Hinzufügen von Testadressen, zur Vorschau einer Transaktionsnachricht und zum Senden eines Testversands finden Sie in der [&#x200B; zu Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional-template#test-message-template){target=_blank}.

[![Bild](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional-template#test-message-template){target=_blank}

## Personalisierungsdaten {#personalization-data}

Sie können Daten aus der Nachrichtenvorlage verwenden, um die Personalisierung von Transaktionsnachrichten zu testen. Mit dieser Funktion wird eine Vorschau generiert oder ein Testversand gesendet. Ebenfalls können Sie anzeigen, wie die Nachricht bei verschiedenen Internet-Anbietern dargestellt wird. Weiterführende Informationen dazu finden Sie im Abschnitt [Inbox Rendering](../../delivery/using/inbox-rendering.md).

Der Zweck dieser Daten besteht darin, Ihre Nachrichten vor dem endgültigen Versand zu testen. Bei diesen Nachrichten handelt es sich nicht um tatsächlich zu verarbeitende Daten. Die XML-Struktur muss jedoch identisch mit der des in der Ausführungsinstanz gespeicherten Ereignisses sein, wie unten dargestellt:

![](assets/messagecenter_create_custo_006.png)

Diese Informationen ermöglichen die Personalisierung des Nachrichteninhalts mithilfe von Personalisierungs-Tags. (Weitere Informationen hierzu finden Sie unter [Nachrichteninhalt erstellen](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional-template#create-message-content){target="_blank"} (Dokumentation zu Campaign v8).

1. Wählen Sie die Transaktionsnachrichtenvorlage aus.

1. Klicken Sie in der Nachrichtenvorlage auf den Tab **[!UICONTROL Testadressen]**.

1. Geben Sie im Inhalt des Ereignisses die Testinformationen im XML-Format ein.

   ![](assets/messagecenter_create_custo_001.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

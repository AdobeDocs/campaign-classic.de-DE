---
product: campaign
title: Ereignistypen erstellen
description: Erfahren Sie, wie Sie Ereignistypen für die Transaktionsnachrichten erstellen, die Sie mit Adobe Campaign Classic versenden möchten
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 98b7c827-f31d-46a6-a28d-40a78a4b4248
source-git-commit: 28279c6ec0eab7f914cf6107cd1ec1cebd05113d
workflow-type: ht
source-wordcount: '183'
ht-degree: 100%

---

# Ereignistypen erstellen {#creating-event-types}



Um sicherzustellen, dass die einzelnen Ereignisse in eine personalisierte Nachricht umgewandelt werden können, müssen Sie zunächst **Ereignistypen** erstellen.

Wählen Sie dazu beim [Erstellen einer Nachrichtenvorlage](../../message-center/using/creating-the-message-template.md) den für die zu versendende Nachricht passenden Ereignistyp aus.

>[!IMPORTANT]
>
>Um in Nachrichtenvorlagen Ereignistypen verwenden zu können, müssen Sie diese zunächst erstellen.

Gehen Sie wie folgt vor, um Ereignistypen für die Verarbeitung in Adobe Campaign zu erstellen:

1. Melden Sie sich bei der **Kontrollinstanz** an.

1. Rufen Sie im Navigationsbaum den Ordner **[!UICONTROL Administration > Plattform > Aufzählungen]** auf.

1. Wählen Sie **[!UICONTROL Ereignistyp]** aus der Liste aus.

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**, um einen Aufzählungswert zu erstellen. Hierbei kann es sich um eine Bestellbestätigung, eine Passwortänderung, eine Änderung des Bestellversands usw. handeln.

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!IMPORTANT]
   >
   >Jeder Ereignistyp muss mit einem Wert in der Aufzählung **[!UICONTROL Ereignistyp]** übereinstimmen.

1. Melden Sie sich nach der Erstellung der Auflistungswerte von Ihrer Instanz ab und wieder an, damit die Änderungen berücksichtigt werden.

>[!NOTE]
>
>Weitere Informationen zum **Arbeiten mit Aufzählungen** finden Sie in der [Dokumentation zu Adobe Campaign v8 (Konsole)](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/config/settings/enumerations){target=_blank}.




---
product: campaign
title: Ereignistypen erstellen
description: Erfahren Sie, wie Sie Ereignistypen erstellen, die mit den Transaktionsnachrichten übereinstimmen, die Sie in Adobe Campaign Classic senden möchten.
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 98b7c827-f31d-46a6-a28d-40a78a4b4248
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 15%

---

# Ereignistypen erstellen {#creating-event-types}

Um sicherzustellen, dass jedes Ereignis in eine personalisierte Nachricht geändert werden kann, müssen Sie zunächst **Ereignistypen** erstellen.

Wenn Sie [eine Nachrichtenvorlage](../../message-center/using/creating-the-message-template.md) erstellen, wählen Sie den Ereignistyp aus, der mit der zu sendenden Nachricht übereinstimmt.

>[!IMPORTANT]
>
>Sie müssen Ereignistypen erstellen, bevor Sie sie in Nachrichtenvorlagen verwenden können.

Gehen Sie wie folgt vor, um Ereignistypen zu erstellen, die von Adobe Campaign verarbeitet werden:

1. Melden Sie sich bei der **Kontrollinstanz** an.

1. Gehen Sie zum Ordner **[!UICONTROL Administration > Plattform > Auflistungen]** des Baums.

1. Wählen Sie **[!UICONTROL Ereignistyp]** aus der Liste aus.

1. Klicken Sie auf **[!UICONTROL Hinzufügen]** , um einen Auflistungswert zu erstellen. Dies kann eine Bestellbestätigung, eine Passwortänderung, eine Änderung des Bestellversands usw. sein.

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!IMPORTANT]
   >
   >Jeder Ereignistyp muss mit einem Wert in der Auflistung **[!UICONTROL Ereignistyp]** übereinstimmen.

1. Melden Sie sich nach der Erstellung der Auflistungswerte von Ihrer Instanz ab und wieder an, damit die Änderungen berücksichtigt werden.

>[!NOTE]
>
>Erfahren Sie mehr über Auflistungen in [Auflistungsverwaltung](../../platform/using/managing-enumerations.md).



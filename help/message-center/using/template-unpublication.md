---
solution: Campaign Classic
product: campaign
title: Vorlagenveröffentlichung
description: Vorlagenveröffentlichung
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 02dee9c4cc03784ccc20f147f816798248bd10f2
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 64%

---


# Veröffentlichung von Vorlagen aufheben{#template-unpublication}

Sobald eine Nachrichtenvorlage in den Ausführungsinstanzen veröffentlicht wurde, kann ihre Veröffentlichung aufgehoben werden. Weitere Informationen zum Veröffentlichungsprozess für Vorlagen finden Sie in diesem Abschnitt [unter](../../message-center/using/template-publication.md).

* Tatsächlich kann eine veröffentlichte Vorlage weiterhin aufgerufen werden, wenn das entsprechende Ereignis ausgelöst wird: Wenn Sie keine Nachrichtenvorlage mehr verwenden, wird empfohlen, die Veröffentlichung rückgängig zu machen. Damit soll verhindert werden, dass versehentlich unerwünschte Transaktionsnachrichten gesendet werden.

   Gehen wir beispielsweise davon aus, dass Sie eine Nachrichtenvorlage veröffentlicht haben, die Sie nur für Weihnachtskampagnen verwenden. Sie können die Veröffentlichung der Vorlage nach der Weihnachtszeit aufheben und im nächsten Jahr erneut veröffentlichen.

* Zudem können Sie keine Transaktionsnachrichten-Vorlagen löschen, die den Status **[!UICONTROL Veröffentlicht]** aufweisen. In diesem Fall müssen Sie die Veröffentlichung der Vorlage zuerst aufheben.

>[!NOTE]
>
>Diese Funktion ist ab Campaign-Version 20.2 verfügbar.

Gehen Sie wie folgt vor, um die Veröffentlichung einer Transaktionsnachrichten-Vorlage aufzuheben.

1. Wechseln Sie auf der Kontrollinstanz zum Ordner **[!UICONTROL Nachrichtencenter > Transaktionsnachrichtenvorlagen]** des Baums.
1. Wählen Sie die Vorlage aus, deren Veröffentlichung Sie aufheben möchten.
1. Klicken Sie auf **[!UICONTROL Veröffentlichung aufheben]**.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. Klicken Sie auf **[!UICONTROL Starten]**.

![](assets/message-center-unpublish.png)

Der Status der Transaktionsnachrichten-Vorlage ändert sich von **[!UICONTROL Veröffentlicht]** in **[!UICONTROL In Bearbeitung]**.

Nach Abschluss der Aufhebung der Veröffentlichung:

* Beide Nachrichtenvorlagen (auf Batch- und Echtzeit-Ereignisse angewendet) werden aus jeder Ausführungsinstanz gelöscht.

   Sie werden nicht mehr im Ordner **[!UICONTROL Administration > Produktion > Message Center-Ausführung > Standard > Transaktionsnachrichtenvorlagen]** angezeigt (siehe [diesen Abschnitt](../../message-center/using/template-publication.md)).

* Nachdem die Veröffentlichung einer Vorlage rückgängig gemacht wurde, können Sie sie aus der Kontrollinstanz löschen.

   Wählen Sie dazu die gewünschte Vorlage aus der Liste aus und klicken Sie oben rechts im Bildschirm auf die Schaltfläche **[!UICONTROL Löschen]**.
---
product: campaign
title: 'Nachrichtenvorlagen veröffentlichen '
description: Erfahren Sie mehr über die Publikation und das Rückgängigmachen der Veröffentlichung von Transaktionsnachrichten in Adobe Campaign Classic.
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 1d55f42b-64bf-4b1f-a317-c1f7456aa5b3
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 86%

---

# Nachrichtenvorlagen veröffentlichen {#publishing-template-messages}

## Vorlagenveröffentlichung {#template-publication}

Wenn die in der Kontrollinstanz erstellte [Nachrichtenvorlage](../../message-center/using/creating-the-message-template.md) fertig ist und [getestet](../../message-center/using/testing-message-templates.md) wurde, können Sie sie veröffentlichen. Dieser Vorgang wird auch auf allen Ausführungsinstanzen veröffentlicht.

Mit der Veröffentlichung können Sie **zwei Nachrichtenvorlagen** in den Ausführungsinstanzen automatisch erstellen. Dadurch können Sie Nachrichten senden, die mit **Echtzeit-Ereignissen** und **Batch-Ereignissen** verknüpft sind.

>[!NOTE]
>
>Bei der Veröffentlichung der Transaktionsnachrichtenvorlagen werden auch die Typologieregeln automatisch auf den Ausführungsinstanzen veröffentlicht.

>[!IMPORTANT]
>
>Wenn Sie an einer Vorlage Änderungen vornehmen, stellen Sie sicher, dass Sie sie erneut veröffentlichen, damit diese Änderungen während des Versands der Transaktionsnachricht wirksam werden.

1. Gehen Sie in der Kontrollinstanz im Navigationsbaum zum Ordner **[!UICONTROL Message Center > Transaktionsnachrichtenvorlagen]**.
1. Wählen Sie die auf den Ausführungsinstanzen zu veröffentlichende Vorlage aus.
1. Klicken Sie auf **[!UICONTROL Veröffentlichen]**.

   ![](assets/messagecenter_publish_model_008.png)

Nach Abschluss der Veröffentlichung werden die beiden Vorlagen, die auf die Echtzeit- und Batch-Ereignisse angewendet werden, im Navigationsbaum der Ausführungsinstanz im Ordner **[!UICONTROL Administration > Betreibung > Message Center > Standard > Transaktionsnachrichten-Vorlagen]** erstellt.

![](assets/messagecenter_deployed_model_001.png)

Sobald eine Vorlage veröffentlicht wurde und das entsprechende Ereignis ausgelöst wird, erhält die Ausführungsinstanz das Ereignis, verknüpft es mit der Transaktionsvorlage und sendet die entsprechende Transaktionsnachricht an jeden Empfänger. Weiterführende Informationen dazu finden Sie unter [Ereignisverarbeitung](../../message-center/using/about-event-processing.md).

>[!NOTE]
>
>Wenn Sie ein vorhandenes Feld der Transaktionsnachrichtenvorlage, z. B. die Absenderadresse, durch einen leeren Wert ersetzen, wird das entsprechende Feld auf der/den Ausführungsinstanz(en) nicht aktualisiert, sobald die Transaktionsnachricht erneut veröffentlicht wird. Es enthält weiterhin den vorherigen Wert.
>
>Wenn Sie jedoch einen nicht leeren Wert hinzufügen, wird das entsprechende Feld wie gewohnt nach der nächsten Veröffentlichung aktualisiert.

## Veröffentlichung von Vorlagen aufheben {#template-unpublication}

Sobald eine Nachrichtenvorlage in den Ausführungsinstanzen veröffentlicht wurde, kann ihre Veröffentlichung aufgehoben werden. Weitere Informationen zum Veröffentlichungsprozess für Vorlagen finden Sie in [diesem Abschnitt](#template-publication).

* Eine veröffentlichte Vorlage kann weiterhin aufgerufen werden, wenn das entsprechende Ereignis ausgelöst wird. Wenn Sie eine Nachrichtenvorlage nicht mehr verwenden, wird deshalb empfohlen, deren Veröffentlichung aufzuheben. Damit wird verhindert, dass versehentlich unerwünschte Transaktionsnachrichten gesendet werden.

   Gehen wir beispielsweise davon aus, dass Sie eine Nachrichtenvorlage veröffentlicht haben, die Sie nur für Weihnachtskampagnen verwenden. Sie können die Veröffentlichung der Vorlage nach der Weihnachtszeit aufheben und im nächsten Jahr erneut veröffentlichen.

* Zudem können Sie keine Transaktionsnachrichten-Vorlagen löschen, die den Status **[!UICONTROL Veröffentlicht]** aufweisen. In diesem Fall müssen Sie die Veröffentlichung der Vorlage zuerst aufheben.

>[!NOTE]
>
>Diese Funktion ist ab Campaign-Version 20.2 verfügbar.

Gehen Sie wie folgt vor, um die Veröffentlichung einer Transaktionsnachrichtenvorlage aufzuheben.

1. Gehen Sie in der Kontrollinstanz im Navigationsbaum zum Ordner **[!UICONTROL Message Center > Transaktionsnachrichtenvorlagen]**.
1. Wählen Sie die Vorlage aus, deren Veröffentlichung Sie aufheben möchten.
1. Klicken Sie auf **[!UICONTROL Veröffentlichung aufheben]**.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. Klicken Sie auf **[!UICONTROL Starten]**.

![](assets/message-center-unpublish.png)

Der Status der Transaktionsnachrichten-Vorlage ändert sich von **[!UICONTROL Veröffentlicht]** in **[!UICONTROL In Bearbeitung]**.

Nach Abschluss der Aufhebung der Veröffentlichung:

* Beide Nachrichtenvorlagen (auf Batch- und Echtzeit-Ereignisse angewendet) werden aus jeder Ausführungsinstanz gelöscht.

   Sie werden im Ordner **[!UICONTROL Administration > Betreibung > Ausführung des Message Center > Standard > Transaktionsnachrichtenvorlagen]** nicht mehr angezeigt (siehe [diesen Abschnitt](#template-publication)).

* Sobald die Veröffentlichung einer Vorlage aufgehoben wurde, können Sie sie aus der Kontrollinstanz löschen.

   Wählen Sie dazu die gewünschte Vorlage aus der Liste aus und klicken Sie oben rechts im Bildschirm auf die Schaltfläche **[!UICONTROL Löschen]**.

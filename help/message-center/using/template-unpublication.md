---
solution: Campaign Classic
product: campaign
title: Vorlagenpublikation
description: Vorlagenpublikation
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 100%

---


# Publikation von Vorlagen rückgängig machen{#template-unpublication}

Sobald eine Nachrichtenvorlage in den Ausführungsinstanzen publiziert wurde, kann sie depubliziert werden.

>[!NOTE]
>
>Diese Funktion ist ab Campaign-Version 20.2 verfügbar.

Eine publizierte Vorlage kann aufgerufen werden. Darum wird empfohlen, eine Nachrichtenvorlage zu depublizieren, wenn Sie sie nicht mehr verwenden. Damit soll verhindert werden, dass versehentlich unerwünschte Transaktionsnachrichten gesendet werden. Gehen wir beispielsweise davon aus, dass Sie eine Nachrichtenvorlage publiziert haben, die Sie nur für Weihnachtskampagnen verwenden. Sie können die Vorlage nach der Weihnachtszeit depublizieren und im nächsten Jahr erneut publizieren.

Zudem können Sie keine Transaktionsnachrichten-Vorlagen löschen, die den Status **[!UICONTROL Publiziert]** aufweisen. In diesem Fall müssen Sie die Vorlage zuerst depublizieren.

Gehen Sie wie folgt vor, um eine Transaktionsnachrichten-Vorlage zu depublizieren.

1. Gehen Sie in der Kontrollinstanz in den Knoten **[!UICONTROL Message Center > Transaktionsnachrichten-Vorlagen]** des Navigationsbaums.
1. Wählen Sie die Vorlage aus, die Sie depublizieren möchten.
1. Klicken Sie auf **[!UICONTROL Depublizieren]**.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. Klicken Sie auf **[!UICONTROL Starten]**.

![](assets/message-center-unpublish.png)

Der Status der Transaktionsnachrichten-Vorlage ändert sich von **[!UICONTROL Publiziert]** in **[!UICONTROL In Bearbeitung]**.

Nach Abschluss der Depublikation:

* Beide Nachrichtenvorlagen (auf Batch- und Echtzeit-Ereignisse angewendet) werden aus jeder Ausführungsinstanz gelöscht. Sie werden im Ordner **[!UICONTROL Administration > Betreibung > Message Center > Standard > Transaktionsnachrichten-Vorlagen]** nicht mehr angezeigt.

* Sobald eine Vorlage depubliziert wurde, können Sie sie bei Bedarf aus der Kontrollinstanz löschen. Wählen Sie dazu die gewünschte Vorlage aus der Liste aus und klicken Sie oben rechts im Bildschirm auf die Schaltfläche **[!UICONTROL Löschen]**.
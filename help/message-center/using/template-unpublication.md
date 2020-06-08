---
title: Vorlagenpublikation
seo-title: Vorlagenpublikation
description: Vorlagenpublikation
seo-description: null
page-status-flag: never-activated
uuid: f83dbe5f-762c-4c58-aeed-6ec289eb522f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 43908738-a71a-49be-ac00-175f57a0555c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 71aeeda3edafc64dbe696ce6f344b8b0ccdc43d1
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 10%

---


# Vorlage ohne Veröffentlichung{#template-unpublication}

Sobald eine Nachrichtenvorlage auf den Ausführungsinstanzen veröffentlicht wurde, kann sie rückgängig gemacht werden.

Tatsächlich kann eine veröffentlichte Vorlage immer noch aufgerufen werden. Wenn Sie daher keine Nachrichtenvorlage mehr verwenden, wird empfohlen, die Veröffentlichung rückgängig zu machen. Damit soll verhindert werden, dass versehentlich eine unerwünschte Transaktionsnachricht gesendet wird. Sie haben beispielsweise eine Nachrichtenvorlage veröffentlicht, die Sie nur für Weihnachten-Kampagnen verwenden. Sie können die Veröffentlichung nach Ablauf der Weihnachtszeit rückgängig machen und sie im nächsten Jahr erneut veröffentlichen.

Außerdem können Sie keine Transaktionsnachrichtenvorlagen mit dem Status &quot; **[!UICONTROL Veröffentlicht]** &quot;löschen. Sie müssen die Veröffentlichung zuerst rückgängig machen.

Gehen Sie wie folgt vor, um die Veröffentlichung einer Transaktionsnachrichtenvorlage rückgängig zu machen.

1. Gehen Sie in der Kontrollinstanz in den Knoten **[!UICONTROL Message Center > Transaktionsnachrichten-Vorlagen]** des Navigationsbaums.
1. Wählen Sie die Vorlage aus, deren Veröffentlichung Sie rückgängig machen möchten.
1. Klicken Sie auf **[!UICONTROL Veröffentlichung rückgängig machen]**.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. Klicken Sie auf **[!UICONTROL Starten]**.

![](assets/message-center-unpublish.png)

Der Status &quot;Transaktionsnachrichtenvorlage&quot;ändert sich von &quot; **[!UICONTROL Veröffentlicht]** &quot;in &quot; **[!UICONTROL Bearbeitung]**&quot;.

Nach Abschluss der Veröffentlichung:

* Beide Meldungsvorlagen (auf Batch- und Echtzeit-Ereignis angewendet) werden aus jeder Ausführungsinstanz gelöscht. Sie werden nicht mehr im Ordner **[!UICONTROL &quot;Administration&quot;> &quot;Produktion&quot;> &quot;Message Center-Ausführung&quot;> &quot;Standard&quot;> &quot;Transaktionsnachrichtenvorlagen]** &quot;angezeigt.

* Sobald die Veröffentlichung einer Vorlage rückgängig gemacht wurde, können Sie sie bei Bedarf aus der Kontrollinstanz löschen. Wählen Sie dazu das gewünschte Element in der Liste aus und klicken Sie auf die Schaltfläche &quot; **[!UICONTROL Löschen]** &quot;oben rechts im Bildschirm.
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
source-git-commit: 1486e897a125520c51661db3030c62ab380fb173
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 62%

---


# Vorlagenpublikation{#template-publication}

Sobald die auf der Kontrollinstanz erstellte Nachrichtenvorlage abgeschlossen ist, können Sie sie auf allen Ausführungsinstanzen veröffentlichen. Mit der Veröffentlichung können Sie automatisch zwei Meldungsvorlagen auf der Ausführungsinstanz erstellen, mit denen Sie Nachrichten senden können, die mit Echtzeit- und Batch-Ereignissen verknüpft sind.

>[!IMPORTANT]
>
>Nach jeder Änderung an der Vorlage muss diese erneut publizert werden, damit die Änderungen in den von der Ausführungsinstanz gesendeten Transaktionsnachrichten berücksichtigt werden.

>[!NOTE]
>
>Bei der Publikation der Transaktionsnachrichten-Vorlagen werden auch die Typologieregeln automatisch auf den Ausführungsinstanzen publiziert.

1. Gehen Sie in der Kontrollinstanz in den Knoten **[!UICONTROL Message Center > Transaktionsnachrichten-Vorlagen]** des Navigationsbaums.
1. Wählen Sie die auf den Ausführungsinstanzen zu publizierende Vorlage aus.
1. Klicken Sie auf **[!UICONTROL Veröffentlichen]**.

   ![](assets/messagecenter_publish_model_008.png)

Once publication is complete, both message templates to be applied to batch and real-time type events are created in the tree of the production instance in the **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]** folder.

![](assets/messagecenter_deployed_model_001.png)

>[!NOTE]
>
>Wenn Sie ein bestehendes Feld der Transaktionsnachrichtenvorlage, wie z. B. die Adresse des Absenders, durch einen leeren Wert ersetzen, wird das entsprechende Feld in der/den Ausführungsinstanz(en) nicht aktualisiert, wenn die Transaktionsnachricht erneut publiziert wird. Es enthält weiterhin den vorherigen Wert. Wenn Sie jedoch einen nicht leeren Wert hinzufügen, wird das entsprechende Feld nach der nächsten Publikation wie gewohnt aktualisiert.

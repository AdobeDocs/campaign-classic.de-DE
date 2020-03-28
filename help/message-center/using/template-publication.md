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
translation-type: ht
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Vorlagenpublikation{#template-publication}

Nach der Erstellung der Nachrichtenvorlage auf der Kontrollinstanz ist diese auf allen Ausführungsinstanzen zu publizieren. Hierbei werden automatisch jeweils zwei Nachrichtenvorlagen auf den Ausführungsinstanzen erstellt, die dem Versand in Echtzeit oder im Stapel (Batch) dienen.

>[!CAUTION]
>
>Nach jeder Änderung an der Vorlage muss diese erneut publizert werden, damit die Änderungen in den von der Ausführungsinstanz gesendeten Transaktionsnachrichten berücksichtigt werden.

>[!NOTE]
>
>Bei der Publikation der Transaktionsnachrichten-Vorlagen werden auch die Typologieregeln automatisch auf den Ausführungsinstanzen publiziert.

1. Gehen Sie in der Kontrollinstanz in den Knoten **[!UICONTROL Message Center > Transaktionsnachrichten-Vorlagen]** des Navigationsbaums.
1. Wählen Sie die auf den Ausführungsinstanzen zu publizierende Vorlage aus.
1. Klicken Sie auf **[!UICONTROL Publizieren]** .

   ![](assets/messagecenter_publish_model_008.png)

Nach Abschluss der Publikation werden die beiden Vorlagen, die auf die Echtzeit- und Batch-Ereignisse angewendet werden, im Navigationsbaum der Ausführungsinstanz im Knoten **[!UICONTROL Administration > Betreibung > Message Center > Standard > Transaktionsnachrichten-Vorlagen]** erstellt.

![](assets/messagecenter_deployed_model_001.png)

>[!NOTE]
>
>Wenn Sie ein bestehendes Feld der Transaktionsnachrichtenvorlage, wie z. B. die Adresse des Absenders, durch einen leeren Wert ersetzen, wird das entsprechende Feld in der/den Ausführungsinstanz(en) nicht aktualisiert, wenn die Transaktionsnachricht erneut publiziert wird. Es enthält weiterhin den vorherigen Wert. Wenn Sie jedoch einen nicht leeren Wert hinzufügen, wird das entsprechende Feld nach der nächsten Publikation wie gewohnt aktualisiert.


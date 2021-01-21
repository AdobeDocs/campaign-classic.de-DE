---
solution: Campaign Classic
product: campaign
title: Vorlagenveröffentlichung
description: Veröffentlichung von Transaktionsnachrichtenvorlagen
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: ht
source-git-commit: 02dee9c4cc03784ccc20f147f816798248bd10f2
workflow-type: ht
source-wordcount: '261'
ht-degree: 100%

---


# Vorlagenveröffentlichung{#template-publication}

Wenn die auf der Kontrollinstanz erstellte Nachrichtenvorlage vollständig ist, können Sie sie veröffentlichen. Dieser Vorgang wird auch auf allen Ausführungsinstanzen veröffentlicht.

Bei der Veröffentlichung können Sie in den Ausführungsinstanzen automatisch zwei Nachrichtenvorlagen erstellen, um Nachrichten senden zu können, die mit Echtzeit- und Batch-Ereignissen verknüpft sind.

>[!NOTE]
>
>Bei der Veröffentlichung der Transaktionsnachrichtenvorlagen werden auch die Typologieregeln automatisch auf den Ausführungsinstanzen veröffentlicht.

>[!IMPORTANT]
>
>Wenn Sie an einer Vorlage Änderungen vornehmen, stellen Sie sicher, dass Sie sie erneut veröffentlichen, damit diese Änderungen während des Versands der Transaktionsnachricht wirksam werden.

1. Gehen Sie in der Kontrollinstanz im Navigationsbaum zu dem Ordner **[!UICONTROL Message Center > Transaktionsnachrichtenvorlagen]**.
1. Wählen Sie die auf den Ausführungsinstanzen zu veröffentlichende Vorlage aus.
1. Klicken Sie auf **[!UICONTROL Veröffentlichen]**.

   ![](assets/messagecenter_publish_model_008.png)

Nach Abschluss der Veröffentlichung werden die beiden Vorlagen, die auf die Echtzeit- und Batch-Ereignisse angewendet werden, im Navigationsbaum der Ausführungsinstanz im Ordner **[!UICONTROL Administration > Betreibung > Message Center > Standard > Transaktionsnachrichten-Vorlagen]** erstellt.

![](assets/messagecenter_deployed_model_001.png)

Sobald eine Vorlage veröffentlicht wurde und das entsprechende Ereignis ausgelöst wird, erhält die Ausführungsinstanz das Ereignis, verknüpft es mit der Transaktionsvorlage und sendet die entsprechende Transaktionsnachricht an jeden Empfänger.

>[!NOTE]
>
>Wenn Sie ein vorhandenes Feld der Transaktionsnachrichtenvorlage, z. B. die Absenderadresse, durch einen leeren Wert ersetzen, wird das entsprechende Feld auf der/den Ausführungsinstanz(en) nicht aktualisiert, sobald die Transaktionsnachricht erneut veröffentlicht wird. Es enthält weiterhin den vorherigen Wert.
>
>Wenn Sie jedoch einen nicht leeren Wert hinzufügen, wird das entsprechende Feld wie gewohnt nach der nächsten Veröffentlichung aktualisiert.

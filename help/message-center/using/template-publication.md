---
solution: Campaign Classic
product: campaign
title: Vorlagenveröffentlichung
description: Veröffentlichung von Transaktionsnachrichtenvorlagen
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 02dee9c4cc03784ccc20f147f816798248bd10f2
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 22%

---


# Vorlagenveröffentlichung{#template-publication}

Wenn die auf der Kontrollinstanz erstellte Nachrichtenvorlage abgeschlossen ist, können Sie sie veröffentlichen. Dieser Vorgang wird auch auf allen Ausführungsinstanzen veröffentlicht.

Mit der Veröffentlichung können Sie automatisch zwei Meldungsvorlagen auf den Ausführungsinstanzen erstellen, mit denen Sie Nachrichten senden können, die mit Echtzeit- und Batch-Ereignissen verknüpft sind.

>[!NOTE]
>
>Beim Veröffentlichen von Transaktionsnachrichtenvorlagen werden Typologieregeln automatisch auch auf den Ausführungsinstanzen veröffentlicht.

>[!IMPORTANT]
>
>Wenn Sie Änderungen an einer Vorlage vornehmen, stellen Sie sicher, dass Sie sie erneut veröffentlichen, damit diese Änderungen während des Versands der Transaktionsnachricht wirksam werden.

1. Wechseln Sie auf der Kontrollinstanz zum Ordner **[!UICONTROL Nachrichtencenter > Transaktionsnachrichtenvorlagen]** des Baums.
1. Wählen Sie die auf den Ausführungsinstanzen zu veröffentlichende Vorlage aus.
1. Klicken Sie auf **[!UICONTROL Veröffentlichen]**.

   ![](assets/messagecenter_publish_model_008.png)

Nach Abschluss der Veröffentlichung werden die beiden Vorlagen, die auf die Echtzeit- und Batch-Ereignisse angewendet werden, im Navigationsbaum der Ausführungsinstanz im Ordner **[!UICONTROL Administration > Betreibung > Message Center > Standard > Transaktionsnachrichten-Vorlagen]** erstellt.

![](assets/messagecenter_deployed_model_001.png)

Sobald eine Vorlage veröffentlicht wurde und das entsprechende Ereignis ausgelöst wird, erhält die Ausführungsinstanz das Ereignis, verknüpft es mit der Transaktionsvorlage und sendet die entsprechende Transaktionsnachricht an jeden Empfänger.

>[!NOTE]
>
>Wenn Sie ein vorhandenes Feld der Transaktionsnachrichtenvorlage, z. B. die Absenderadresse, durch einen leeren Wert ersetzen, wird das entsprechende Feld auf der/den Ausführungsinstanz(n) nicht aktualisiert, sobald die Transaktionsnachricht erneut veröffentlicht wurde. Es enthält weiterhin den vorherigen Wert.
>
>Wenn Sie jedoch einen nicht leeren Wert hinzufügen, wird das entsprechende Feld wie gewohnt nach der nächsten Veröffentlichung aktualisiert.

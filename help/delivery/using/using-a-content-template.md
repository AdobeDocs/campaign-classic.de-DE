---
product: campaign
title: Verwenden einer Inhaltsvorlage
description: Verwenden einer Inhaltsvorlage
badge-v7: label="v7" type="Informative" tooltip="Gilt für Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Templates
exl-id: e43dd68e-2e95-4367-9029-4622fbcb1759
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 81%

---

# Verwenden einer Inhaltsvorlage{#using-a-content-template}



## Über Inhaltsvorlagen {#about-content-templates}

Inhaltsvorlagen können direkt in der Versanderstellung referenziert und verwendet werden. Siehe [Versanderstellung unter Verwendung des Content Managements](#creating-a-delivery-via-content-management).

Sie können auch zum Erstellen von Inhaltsinstanzen genutzt werden. Nach der Erstellung sind diese Instanzen versandbereit (siehe [Versand einer Inhaltsinstanz](#delivering-a-content-instance)) oder exportbereit (siehe [Erstellung einer Inhaltsinstanz](#creating-a-content-instance)).

## Versanderstellung unter Verwendung des Content Managements {#creating-a-delivery-via-content-management}

Sie haben die Möglichkeit, bei der Versanderstellung eine Inhaltsvorlage anzugeben und mithilfe dieser den Inhalt zu erfassen. Im Versand-Assistenten erscheint in diesem Fall ein zusätzlicher Tab mit den Feldern zur Eingabe der variablen Inhaltselemente.

![](assets/s_ncs_content_deliver_a_content.png)

Das Layout wird automatisch auf der Basis der ausgewählten Einstellungen angewendet. Um sie anzuzeigen, klicken Sie auf das **[!UICONTROL HTML-Vorschau]** (oder **[!UICONTROL Textvorschau]** ) und wählen Sie einen Empfänger aus, um Personalisierungselemente zu testen.

![](assets/s_ncs_content_deliver_a_content_html.png)

Weitere Informationen finden Sie im vollständigen Implementierungsbeispiel unter [Inhaltserstellung im Versand-Assistenten](use-case-creating-content-management.md#creating-content-in-the-delivery-wizard).

## Erstellung einer Inhaltsinstanz {#creating-a-content-instance}

Es besteht die Möglichkeit, Inhalte direkt im Explorer zu erstellen. Sie können dann in Workflows genutzt, exportiert oder in neuen Sendungen verwendet werden.

Gehen Sie wie folgt vor:

1. Markieren Sie den Knoten **[!UICONTROL Ressourcen > Inhalte]** und klicken Sie mit der rechten Maustaste auf einen der Inhaltsordner. Wählen Sie die Option **[!UICONTROL Eigenschaften...]**.

   ![](assets/s_ncs_content_folder_properties.png)

1. Wählen Sie die gewünschten Veröffentlichungsvorlagen aus.

   ![](assets/s_ncs_content_folder_templates.png)

1. Nun können Sie über die Schaltfläche **[!UICONTROL Neu]** (rechts oberhalb der Inhaltsliste) neue Inhalte erstellen.

   ![](assets/s_ncs_content_folder_create_a_template.png)

1. Füllen Sie die Felder des Formulars aus.

   ![](assets/s_ncs_content_folder_use_a_template.png)

1. Klicken Sie nun auf den Tab **[!UICONTROL HTML-Vorschau]**, um das Rendering zu prüfen. Im vorliegenden Beispiel fehlen die Angaben in den Personalisierungsfeldern, die auf Daten aus der Datenbank zurückgreifen.

   ![](assets/s_ncs_content_folder_use_a_template_preview.png)

1. Nach seiner Erstellung wird der Inhalt der Liste der verfügbaren Inhalte hinzugefügt. Klicken Sie auf **[!UICONTROL Eigenschaften]** -Link, um Titel, Status oder den Verlauf zu ändern.

   ![](assets/s_ncs_content_folder_template_properties.png)

1. Nach der Validierung kann der Inhalt bei Bedarf erzeugt werden. Dies geschieht durch Klick auf die entsprechende Schaltfläche in der Symbolleiste.

   ![](assets/s_ncs_content_folder_template_generate.png)

   >[!NOTE]
   >
   >Sie haben auch die Möglichkeit, die Erzeugung nicht validierter Inhalte zuzulassen. Ändern Sie in diesem Fall die entsprechende Option in der Veröffentlichungsvorlage. Weitere Informationen hierzu finden Sie unter [Erstellung und Konfiguration der Vorlagen](publication-templates.md#creating-and-configuring-the-template).

   HTML- und Textinhalte werden standardmäßig im **Veröffentlichung** Ordner der Adobe Campaign-Instanz. Sie können den Veröffentlichungsordner über die **NcmPublishingDir** -Option.

## Versand einer Inhaltsinstanz {#delivering-a-content-instance}

Damit eine Inhaltsinstanz automatisch erstellt und versendet werden kann, muss in der Veröffentlichungsvorlage, die für die Inhaltserzeugung verwendet wird, eine Versandvorlage angegeben sein. Weitere Informationen hierzu finden Sie im Abschnitt [Versand](publication-templates.md#delivery).

Des Weiteren muss der Ordner, in dem der Inhalt gespeichert wird, den aus dieser Veröffentlichungsvorlage stammenden Inhalten vorbehalten sein. Ein Inhaltsordner, der die Erzeugung verschiedener Inhaltstypen erlaubt, ist nicht für die automatische Versanderstellung geeignet.

Klicken Sie zur automatischen Erstellung eines Versands mit dem ausgewählten Inhalt auf das **[!UICONTROL Versand]**-Symbol und wählen Sie die Vorlage aus.

![](assets/s_ncs_content_folder_create_the_delivery.png)

Die Inhalte (Text und HTML) werden automatisch eingefügt.

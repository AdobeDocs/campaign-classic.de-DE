---
title: Verwendung von Inhaltsvorlagen
seo-title: Verwendung von Inhaltsvorlagen
description: Verwendung von Inhaltsvorlagen
seo-description: null
page-status-flag: never-activated
uuid: 893b9711-593f-4865-b61a-ef0fede9a2b0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: 48f491b7-bf7b-457f-9cf2-db2bbf4eceea
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Verwendung von Inhaltsvorlagen{#using-a-content-template}

## Über Inhaltsvorlagen {#about-content-templates}

Inhaltsvorlagen können direkt referenziert und in Auslieferungen verwendet werden. Siehe [Erstellen einer Bereitstellung über Content Management](#creating-a-delivery-via-content-management)

Sie können auch zum Erstellen von Inhaltsinstanzen verwendet werden. Nachdem sie erstellt wurden, können diese Instanzen bereitgestellt (siehe [Bereitstellung einer Inhaltsinstanz](#delivering-a-content-instance)) oder exportiert werden (siehe [Erstellen einer Inhaltsinstanz](#creating-a-content-instance)).

## Versanderstellung unter Verwendung des Content Managements {#creating-a-delivery-via-content-management}

Sie haben die Möglichkeit, bei der Versanderstellung eine Inhaltsvorlage anzugeben und mithilfe dieser den Inhalt zu erfassen. Im Versand-Assistenten erscheint in diesem Fall ein zusätzlicher Tab mit den Feldern zur Eingabe der variablen Inhaltselemente.

![](assets/s_ncs_content_deliver_a_content.png)

Das Layout wird automatisch auf Grundlage der ausgewählten Einstellungen angewendet. Klicken Sie zum Anzeigen auf das Symbol **[!UICONTROL HTML preview]** (oder **[!UICONTROL Text preview]** ) und wählen Sie einen Empfänger aus, um die Personalisierungselemente zu testen.

![](assets/s_ncs_content_deliver_a_content_html.png)

Weitere Informationen finden Sie im vollständigen Implementierungsbeispiel: Erstellen [von Inhalten im Bereitstellungsassistenten](../../delivery/using/use-case--creating-content-management.md#creating-content-in-the-delivery-wizard).

## Erstellung einer Inhaltsinstanz {#creating-a-content-instance}

Es besteht die Möglichkeit, Inhalte direkt im Explorer zu erstellen. Sie können dann in Workflows genutzt, exportiert oder in neuen Sendungen verwendet werden.

Gehen Sie wie folgt vor:

1. Wählen Sie die **[!UICONTROL Resources > Contents]** Node des Baumes aus, klicken Sie mit der rechten Maustaste und wählen Sie **[!UICONTROL Properties]**.

   ![](assets/s_ncs_content_folder_properties.png)

1. Wählen Sie die gewünschten Publikationsvorlagen aus.

   ![](assets/s_ncs_content_folder_templates.png)

1. You can now create new content using the **[!UICONTROL New]** button above the content list.

   ![](assets/s_ncs_content_folder_create_a_template.png)

1. Füllen Sie die Felder des Formulars aus.

   ![](assets/s_ncs_content_folder_use_a_template.png)

1. Klicken Sie dann auf die **[!UICONTROL HTML preview]** Registerkarte, um das Rendering anzuzeigen. Hier werden die aus der Datenbank entnommenen Personalisierungsfelder nicht eingegeben.

   ![](assets/s_ncs_content_folder_use_a_template_preview.png)

1. Nach der Erstellung wird der Inhalt der Liste der verfügbaren Inhalte hinzugefügt. Klicken Sie auf den **[!UICONTROL Properties]** Link, um die Bezeichnung, den Status oder den Verlauf zu ändern.

   ![](assets/s_ncs_content_folder_template_properties.png)

1. Nach der Validierung kann der Inhalt bei Bedarf erzeugt werden. Dies geschieht durch Klick auf die entsprechende Schaltfläche in der Symbolleiste.

   ![](assets/s_ncs_content_folder_template_generate.png)

   >[!NOTE]
   >
   >Sie können die Erstellung nicht genehmigter Inhalte autorisieren. Ändern Sie dazu die entsprechende Option in der Veröffentlichungsvorlage. Weitere Informationen hierzu finden Sie unter [Erstellen und Konfigurieren der Vorlage](../../delivery/using/publication-templates.md#creating-and-configuring-the-template).

   HTML- und Text-Inhalte werden standardmäßig im **Publishing**-Ordner der Adobe-Campaign-Instanz erzeugt. Ausgehend von der Option **NcmPublishingDir** können Sie einen anderen Ordner wählen.

## Versand einer Inhaltsinstanz {#delivering-a-content-instance}

Um eine Inhaltsinstanz zu erstellen und bereitzustellen, muss eine Bereitstellungsvorlage mit der Veröffentlichungsvorlage verknüpft sein, mit der dieser Inhalt generiert wird. For more on this, refer to [Delivery](../../delivery/using/publication-templates.md#delivery).

Des Weiteren muss der Ordner, in dem der Inhalt gespeichert wird, den aus dieser Publikationsvorlage stammenden Inhalten vorbehalten sein. Ein Inhaltsordner, der die Erzeugung verschiedener Inhaltstypen erlaubt, ist nicht für die automatische Versanderstellung geeignet.

To create the delivery automatically based on the selected content, click the **[!UICONTROL Delivery]** icon and choose the template.

![](assets/s_ncs_content_folder_create_the_delivery.png)

Die Inhalte (Text und HTML) werden automatisch eingefügt.

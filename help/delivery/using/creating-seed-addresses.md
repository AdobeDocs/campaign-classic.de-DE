---
title: Testadressen erstellen
seo-title: Testadressen erstellen
description: Testadressen erstellen
seo-description: null
page-status-flag: never-activated
uuid: 0dae107a-7b53-4096-93c3-9517b402cbc9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: 6dad49af-4818-471b-9df1-057cc6b9a68a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Testadressen erstellen{#creating-seed-addresses}

Seed addresses are not managed via standard profiles and targets, but in a dedicated node of the Adobe Campaign hierarchy **[!UICONTROL Resources > Campaign management > Seed addresses]**.

Sie können Unterordner erstellen, um die Startadressen zu organisieren. Klicken Sie dazu mit der rechten Maustaste auf den **[!UICONTROL Seed addresses]** Knoten und wählen Sie **[!UICONTROL Create a new 'Seed addresses' folder]**. Benennen Sie den Unterordner und drücken Sie dann **[!UICONTROL Enter]** zur Überprüfung die Eingabetaste. Sie können jetzt Seed-Adressen erstellen oder in diesen Unterordner kopieren. For more on this, refer to [Defining addresses](#defining-addresses).

Mit Adobe Campaign können Sie auch Vorlagen für Startadressen erstellen, die in Auslieferungen oder Kampagnen importiert und je nach den spezifischen Anforderungen der jeweiligen Auslieferungen und Kampagnen angepasst werden. Weitere Informationen finden Sie unter [Erstellen von Vorlagen](#creating-seed-address-templates)für Startadressen.

## Adressen konfigurieren {#defining-addresses}

Gehen Sie zur Erstellung von Testadressen wie folgt vor:

1. Click the **[!UICONTROL New]** button above the list of seed addresses.
1. Geben Sie die mit der Adresse verknüpften Daten in die entsprechenden Felder auf der **[!UICONTROL Recipient]** Registerkarte ein. Die verfügbaren Felder entsprechen den Standardfeldern in den Profilen der Empfänger der Auslieferung (nms:Empfängertabelle): Name, Vorname, E-Mail usw.

   >[!NOTE]
   >
   >Für die Bezeichnung der Adresse werden automatisch die von Ihnen definierten Vor- und Nachnamen verwendet.
   >
   >Es ist bei Testadressen nicht erforderlich, alle Felder in allen Tabs auszufüllen. Fehlende Personalisierungselemente werden zum Zeitpunkt des Versands mit zufälligen Werten ergänzt.

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. In the **[!UICONTROL Seed fields]** tab, enter the values that will be inserted in the delivery logs during the analysis phase (in the **[!UICONTROL nms:broadLog]** table).
1. In the **[!UICONTROL Additional data]** tab, enter the personalization data used for the deliveries created in the Datamanagement workflows and which you want to assign a specific value to.

## Testadressenvorlagen erstellen {#creating-seed-address-templates}

Die Erstellung von Adressenvorlagen, die importiert und für jeden Versand angepasst werden können, folgt dem der Definition einer neuen Testadresse. Der einzige Unterschied besteht darin, dass Vorlagen für Testadressen in einem Ordner vom Typ &quot;Vorlagen&quot; gespeichert werden.

Gehen Sie wie folgt vor, um einen Vorlagenordner zu konfigurieren:

1. Create a new **[!UICONTROL Seed addresses]** type folder, right-click the folder then select **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. Click the **[!UICONTROL Restriction]** tab and add the following filtering condition: **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   Die in diesem Ordner gespeicherten Adressen können nun als Vorlage verwendet werden. Sie können sie in Lieferungen oder Kampagnen importieren und entsprechend den spezifischen Bedürfnissen der betreffenden Lieferungen und Kampagnen anpassen (siehe [Hinzufügen von Saatgutadressen](../../delivery/using/adding-seed-addresses.md)).

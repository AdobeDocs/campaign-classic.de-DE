---
title: Angebotskategorien
seo-title: Angebotskategorien
description: Angebotskategorien
seo-description: null
page-status-flag: never-activated
uuid: 5ac0ae5e-1731-4699-b4ef-f3867ad0ab58
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: a9fad813-3256-4a00-ba74-7dbaba9e8e23
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Angebotskategorien{#creating-offer-categories}

Die Erstellung von Angebotskategorien kann nur in der **[!UICONTROL Design]** Umgebung erfolgen. Sie werden automatisch in der **[!UICONTROL Live]** Umgebung bereitgestellt (d. h. bereitgestellt), wenn das erstellte/geänderte Angebot/die darin enthaltenen Angebote genehmigt wurden. Standardmäßig enthält die **[!UICONTROL Design]** Umgebung eine Kategorie, die alle Angebote erhält. Unterkategorien können erstellt werden, um den Katalogangeboten eine Hierarchie hinzuzufügen.

Für jede Kategorie können verschiedene Verwendungsdaten konfiguriert werden. Nach Ablauf des angegebenen Zeitraums stehen die in der Kategorie enthaltenen Angebote nicht mehr zur Unterbreitung zur Verfügung. Sie haben weiterhin die Möglichkeit, Angeboten einer bestimmten Kategorie bei der Auswahl durch das Angebotsmodul den Vorzug einzuräumen, beispielsweise um ein Produkt zeitlich begrenzt besonders hervorzuheben. Definieren Sie hierfür in der Kategorie einen Gewichtfaktor für den gewünschten Zeitraum. Innerhalb dieses Zeitraums wird die Gewichtung der in der Kategorie enthaltenen Angebote mit dem Faktor multipliziert.

Gehen Sie wie folgt vor, um eine neue Kategorie zu erstellen:

1. Wechseln Sie zum **[!UICONTROL Offer catalog]** Ordner.

   ![](assets/offer_cat_create_001.png)

1. Klicken Sie mit der rechten Maustaste und wählen Sie **[!UICONTROL Create a new "Offer category" folder]** aus der Dropdownliste.

   ![](assets/offer_cat_create_002.png)

1. Benennen Sie die Kategorie erneut. Sie können die Bezeichnung später über die **[!UICONTROL General]** Registerkarte bearbeiten.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >Wiederholen Sie diese Schritte gegebenenfalls, bis Sie die gewünschte Anzahl an Kategorien erstellt haben.

   Nun haben Sie je nach Bedarf die Möglichkeit,

   * assign eligibility dates from the **[!UICONTROL Eligibility]** tab.

      ![](assets/offer_cat_create_004.png)

   * enter key words that may be used to select offers from within this category, using the **[!UICONTROL Themes]** field.

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >Bei Abfrage des Angebotsmoduls werden nur die Angebote ausgegeben, deren Themen oder Kategorien mit den in der Abfrage angegebenen Parametern übereinstimmen.

   * You can temporarily &quot;boost&quot; the offer weight of a category for a given period via the **[!UICONTROL Multiplier weight]** field.

      ![](assets/offer_cat_create_006.png)

Eine Zusammenfassung der Förderfähigkeitsregeln finden Sie im Dashboard der in der Kategorie enthaltenen Angebote. Um sie anzuzeigen, klicken Sie auf den **[!UICONTROL Schedule and eligibility rules of the offer]** Link.

![](assets/offer_create_006.png)


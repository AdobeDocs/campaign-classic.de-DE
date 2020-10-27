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
translation-type: tm+mt
source-git-commit: 8fc3e793ec544948049fc122b44b6bffdebecba0
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 85%

---


# Angebotskategorien{#creating-offer-categories}

Angebotskategorien werden ausschließlich in der **[!UICONTROL Design-Umgebung]** erstellt. Sie werden automatisch für die **[!UICONTROL Live-Umgebung]** freigegeben (d. h. zur Unterbreitung verfügbar gemacht), wenn die enthaltenen Angebote oder ihre Änderungen validiert wurden. Standardmäßig ist in der **[!UICONTROL Design-Umgebung]** bereits eine Kategorie (der Angebotskatalog) enthalten. Sie haben die Möglichkeit, Unterkategorien zu erstellen, um die Angebote zu ordnen und zu hierarchisieren.

Für jede Kategorie können verschiedene Verwendungsdaten konfiguriert werden. Nach Ablauf des angegebenen Zeitraums stehen die in der Kategorie enthaltenen Angebote nicht mehr zur Unterbreitung zur Verfügung. Sie haben weiterhin die Möglichkeit, Angeboten einer bestimmten Kategorie bei der Auswahl durch das Angebotsmodul den Vorzug einzuräumen, beispielsweise um ein Produkt zeitlich begrenzt besonders hervorzuheben. Definieren Sie hierfür in der Kategorie einen Gewichtfaktor für den gewünschten Zeitraum. Innerhalb dieses Zeitraums wird die Gewichtung der in der Kategorie enthaltenen Angebote mit dem Faktor multipliziert.

Gehen Sie wie folgt vor, um eine neue Kategorie zu erstellen:

1. Markieren Sie im Navigationsbaum den Ordner **[!UICONTROL Angebotskatalog]**.

   ![](assets/offer_cat_create_001.png)

1. Klicken Sie mit der rechten Maustaste und wählen Sie im Kontextmenü die Option **[!UICONTROL Angebotskategorie-Ordner hinzufügen]** aus.

   ![](assets/offer_cat_create_002.png)

1. Benennen Sie die Kategorie. Der Titel kann später auch über den **[!UICONTROL Allgemein]**-Tab der Kategorie geändert werden.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >Wiederholen Sie diese Schritte gegebenenfalls, bis Sie die gewünschte Anzahl an Kategorien erstellt haben.

   Nun haben Sie je nach Bedarf die Möglichkeit,

   * Assign eligibility dates from the **[!UICONTROL Eligibility]** tab.

      ![](assets/offer_cat_create_004.png)

   * Enter key words that may be used to select offers from within this category, using the **[!UICONTROL Themes]** field.

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >Bei Abfrage des Angebotsmoduls werden nur die Angebote ausgegeben, deren Themen oder Kategorien mit den in der Abfrage angegebenen Parametern übereinstimmen.

   * Temporarily &quot;boost&quot; the offer weight of a category for a given period via the **[!UICONTROL Multiplier weight]** field.

      ![](assets/offer_cat_create_006.png)

Über den Link **[!UICONTROL Planung und Eignungsregeln des Angebots]** im Dashboard der in der Kategorie enthaltenen Angebote können Sie auf die Details der Eignungskonfiguration zugreifen.

![](assets/offer_create_006.png)


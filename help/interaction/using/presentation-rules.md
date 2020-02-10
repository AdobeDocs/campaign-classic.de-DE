---
title: Unterbreitungsregeln
seo-title: Unterbreitungsregeln
description: Unterbreitungsregeln
seo-description: null
page-status-flag: never-activated
uuid: 460f06f8-cdb9-401d-a45e-e54e56d66781
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: case-study
discoiquuid: 8ef303b4-d9ce-40ee-a6c6-ed5012ab8eb8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 28614a6b0c45deef17d9b3275a16e65bdff4538b

---


# Unterbreitungsregeln{#presentation-rules}

## Unterbreitungsregeln erstellen {#creating-a-presentation-rule}

Angenommen, in Ihrer Datenbank sind verschiedene Angebote für Reisen nach Europa, Afrika, die USA und Kanada enthalten. Sie möchten Kanadareisen vorschlagen. Wenn jedoch ein Empfänger Angebote dieser Kategorie ablehnt, sollen sie kein zweites Mal unterbreitet werden.

Die zu erstellende Regel muss somit sicherstellen, dass Reisen nach Kanada jedem Empfänger nur einmal unterbreitet werden, sollte er sie bei der ersten Unterbreitung ablehnen.

1. Wechseln Sie in der Struktur von Adobe Campaign zum Knoten **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]** .
1. Erstellen Sie eine neue **[!UICONTROL Offer presentation]** Typregel.

   ![](assets/offer_typology_example_001.png)

1. Benennen Sie die Regel und geben Sie gegebenenfalls eine Beschreibung ein.

   ![](assets/offer_typology_example_002.png)

1. Choose the **[!UICONTROL All channels]** option to extend the rule to all channels.

   ![](assets/offer_typology_example_003.png)

1. Click the **[!UICONTROL Edit expression]** link and choose the **[!UICONTROL Category]** node as an expression.

   ![](assets/offer_typology_example_004.png)

1. Wählen Sie als Wert aus dem Angebotskatalog die Kategorie Kanada aus und klicken Sie auf **[!UICONTROL OK]**, um das Abfragefenster zu schließen.

   ![](assets/offer_typology_example_005.png)

1. In the **[!UICONTROL Offer presentation]** tab, choose the same dimensions as those configured in the environment.

   ![](assets/offer_typology_example_006.png)

1. Geben Sie den Zeitraum an, in dem die Regel angewendet werden soll.

   ![](assets/offer_typology_example_007.png)

1. Begrenzen Sie die maximale Vorschlagsanzahl auf einen Vorschlag, damit die Empfänger, die bereits eine Kanadareise abgelehnt haben, nicht erneut ein ähnliches Angebot erhalten.

   ![](assets/offer_typology_example_008.png)

1. Wählen Sie den **[!UICONTROL Offers for the same category]** Filter aus, um alle Angebote aus der Kategorie **Kanada** auszuschließen.

   ![](assets/offer_typology_example_020.png)

1. Select the **[!UICONTROL Rejected propositions]** filter to take into account only propositions rejected by the recipient.

   ![](assets/offer_typology_example_021.png)

1. Wählen Sie nun die von der Regel betroffenen Empfänger aus.

   Im vorliegenden Beispiel handelt es sich um **Vielreisende**.

   ![](assets/offer_typology_example_009.png)

1. Referenzieren Sie die Regel in einer Angeboten vorbehaltenen Typologie.

   ![](assets/offer_typology_example_013.png)

1. Go to the offer environment, (**Environment - Recipient** in this case) and reference the new typology just created using the drop-down list in the **[!UICONTROL Eligibility]** tab.

   ![](assets/offer_typology_example_014.png)

## Unterbreitungsregeln anwenden {#applying-the-presentation-rule}

Nachfolgend wird aufgezeigt, wie die zuvor erstellte Typologieregel arbeitet.

Unterbreiten Sie ein Angebot aus der Kategorie &quot;Kanada&quot;. Wenn das Angebot von einem Empfänger bei der ersten Unterbreitung abgelehnt wird, wird es diesem Empfänger kein zweites Mal vorgeschlagen.

1. In the **Frequent travelers** recipient folder, choose one of the profiles to check the offers for which they are eligible: click the **[!UICONTROL Propositions]** tab, then the **[!UICONTROL Preview]** tab.

   Im vorliegenden Beispiel kommt **Peter Urlaubsreif** für ein Angebot aus der Kategorie **Kanada** infrage.

   ![](assets/offer_typology_example_015.png)

1. Erstellen Sie einen ersten E-Mail-Versand mit Angeboten an die Zielgruppe **Vielreisende**.
1. Wählen Sie die Parameter der Angebotsmodul-Abfrage aus.

   Im vorliegenden Beispiel wird die Kategorie **Amerika** gewählt. Sie enthält die Unterkategorien **USA** und **Kanada**.

   ![](assets/offer_typology_example_016.png)

1. Fügen Sie Ihre Angebote in den Text der Nachricht ein und senden Sie die Lieferung. For more on this, refer to [About outbound channels](../../interaction/using/about-outbound-channels.md).

   Der zuvor ausgewählte Empfänger hat das für ihn infrage kommende Angebot wie geplant erhalten.

1. Aus dem Vorschlagsverlauf ist ersichtlich, dass der Empfänger das Angebot abgelehnt hat.

   ![](assets/offer_typology_example_018.png)

1. Prüfen Sie, für welche Angebote er nun infrage kommt.

   Es zeigt sich, dass kein Angebot zu Kanada ausgewählt wurde.

   ![](assets/offer_typology_example_019.png)

**Verwandtes Thema**

* [Angebote verwalten und Redundanz kanalübergreifend steuern](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Manageoffersandcontrolredundancyacrosschannels)
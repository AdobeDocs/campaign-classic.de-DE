---
solution: Campaign Classic
product: campaign
title: Unterbreitungsregeln
description: Unterbreitungsregeln
audience: interaction
content-type: reference
topic-tags: case-study
exl-id: f9dd9ad6-48da-4a80-9405-109a433a1ed5
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '490'
ht-degree: 100%

---

# Unterbreitungsregeln{#presentation-rules}

## Unterbreitungsregeln erstellen {#creating-a-presentation-rule}

Angenommen, in Ihrer Datenbank sind verschiedene Angebote für Reisen nach Europa, Afrika, die USA und Kanada enthalten. Sie möchten Kanadareisen vorschlagen. Wenn jedoch ein Empfänger Angebote dieser Kategorie ablehnt, sollen sie kein zweites Mal unterbreitet werden.

Die zu erstellende Regel muss somit sicherstellen, dass Reisen nach Kanada jedem Empfänger nur einmal unterbreitet werden, sollte er sie bei der ersten Unterbreitung ablehnen.

1. Markieren Sie im Adobe-Campaign-Navigationsbaum den Knoten **[!UICONTROL Administration]** > **[!UICONTROL Kampagnen]** > **[!UICONTROL Typologieverwaltung]** > **[!UICONTROL Typologieregeln]**.
1. Erstellen Sie eine neue Regel vom Typ **[!UICONTROL Angebotsunterbreitung]**.

   ![](assets/offer_typology_example_001.png)

1. Benennen Sie die Regel und geben Sie gegebenenfalls eine Beschreibung ein.

   ![](assets/offer_typology_example_002.png)

1. Wählen Sie die Option **[!UICONTROL Alle Kanäle]** aus, damit die Regel universell gültig ist.

   ![](assets/offer_typology_example_003.png)

1. Klicken Sie auf den Link **[!UICONTROL Anwendungskriterien der Regel bearbeiten...]** und wählen Sie den Knoten **[!UICONTROL Kategorie]** als Ausdruck.

   ![](assets/offer_typology_example_004.png)

1. Wählen Sie als Wert aus dem Angebotskatalog die Kategorie Kanada aus und klicken Sie auf **[!UICONTROL OK]**, um das Abfragefenster zu schließen.

   ![](assets/offer_typology_example_005.png)

1. Wählen Sie dann im Tab **[!UICONTROL Angebotsunterbreitung]** die Dimensionen aus, die Sie auch auf Umgebungsebene konfiguriert haben.

   ![](assets/offer_typology_example_006.png)

1. Geben Sie den Zeitraum an, in dem die Regel angewendet werden soll.

   ![](assets/offer_typology_example_007.png)

1. Begrenzen Sie die maximale Vorschlagsanzahl auf einen Vorschlag, damit die Empfänger, die bereits eine Kanadareise abgelehnt haben, nicht erneut ein ähnliches Angebot erhalten.

   ![](assets/offer_typology_example_008.png)

1. Wählen Sie aus der Dropdown-Liste den Filter **[!UICONTROL Angebote derselben Kategorie]** aus, um alle Angebote der Kategorie **Kanada** von der Unterbreitung auszuschließen.

   ![](assets/offer_typology_example_020.png)

1. Wählen Sie den Vorschlagsstatus **[!UICONTROL Abgelehnte Vorschläge]**, damit nur die Vorschläge berücksichtigt werden, die der Empfänger nicht angenommen hat.

   ![](assets/offer_typology_example_021.png)

1. Wählen Sie nun die von der Regel betroffenen Empfänger aus.

   Im vorliegenden Beispiel handelt es sich um **Vielreisende**.

   ![](assets/offer_typology_example_009.png)

1. Referenzieren Sie die Regel in einer Angeboten vorbehaltenen Typologie.

   ![](assets/offer_typology_example_013.png)

1. Gehen Sie zum Abschluss in Ihre Angebotsumgebung, hier **Umgebung - Empfänger**, und referenzieren Sie im Tab **[!UICONTROL Eignung]** die Typologie, die auf die zuvor erstellte Regel verweist.

   ![](assets/offer_typology_example_014.png)

## Unterbreitungsregeln anwenden {#applying-the-presentation-rule}

Nachfolgend wird aufgezeigt, wie die zuvor erstellte Typologieregel arbeitet.

Unterbreiten Sie ein Angebot aus der Kategorie &quot;Kanada&quot;. Wenn das Angebot von einem Empfänger bei der ersten Unterbreitung abgelehnt wird, wird es diesem Empfänger kein zweites Mal vorgeschlagen.

1. Wählen Sie ein Profil aus dem Empfängerordner **Vielreisende** aus und prüfen Sie, für welche Angebote dieser Empfänger infrage kommt. Klicken Sie hierfür auf den Tab **[!UICONTROL Vorschläge]** und dann auf **[!UICONTROL Vorschau]**:

   Im vorliegenden Beispiel kommt **Peter Urlaubsreif** für ein Angebot aus der Kategorie **Kanada** infrage.

   ![](assets/offer_typology_example_015.png)

1. Erstellen Sie einen ersten E-Mail-Versand mit Angeboten an die Zielgruppe **Vielreisende**.
1. Wählen Sie die Parameter der Angebotsmodul-Abfrage aus.

   Im vorliegenden Beispiel wird die Kategorie **Amerika** gewählt. Sie enthält die Unterkategorien **USA** und **Kanada**.

   ![](assets/offer_typology_example_016.png)

1. Fügen Sie Ihre Angebote in den Text der Nachricht ein und versenden Sie die Nachricht. Weitere Informationen hierzu finden Sie im Abschnitt [Über ausgehende Kanäle](../../interaction/using/about-outbound-channels.md).

   Der zuvor ausgewählte Empfänger hat das für ihn infrage kommende Angebot wie geplant erhalten.

1. Aus dem Vorschlagsverlauf ist ersichtlich, dass der Empfänger das Angebot abgelehnt hat.

   ![](assets/offer_typology_example_018.png)

1. Prüfen Sie, für welche Angebote er nun infrage kommt.

   Es zeigt sich, dass kein Angebot zu Kanada ausgewählt wurde.

   ![](assets/offer_typology_example_019.png)

**Verwandtes Thema**

* [Verwaltung von Angeboten und kanalübergreifende Kontrolle der Redundanz](https://helpx.adobe.com/de/campaign/kb/simplifying-campaign-management-acc.html#Manageoffersandcontrolredundancyacrosschannels)

---
product: campaign
title: Unterbreitungsregeln
description: Unterbreitungsregeln
feature: Interaction, Offers
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: interaction
content-type: reference
topic-tags: case-study
exl-id: f9dd9ad6-48da-4a80-9405-109a433a1ed5
TQID: https://experienceleague.adobe.com/s2QV1BGLtUfyWg1BfYuryciF9STRK3HpIXNc6oQ0ATY
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
feature_v2:
  - id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
subfeature_v2: []
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 487
ht-degree: 84%

---

# Unterbreitungsregeln{#presentation-rules}



## Unterbreitungsregeln erstellen {#creating-a-presentation-rule}

In unserer Datenbank gibt es mehrere Reiseangebote für Europa, Afrika, die Vereinigten Staaten und Kanada. Wir möchten Angebote für eine Reise nach Kanada senden, aber wenn der Empfänger dieses Angebot ablehnt, möchten wir es nicht erneut an ihn senden

Die zu erstellende Regel muss somit sicherstellen, dass Reisen nach Kanada jedem Empfänger nur einmal unterbreitet werden, sollte er sie bei der ersten Unterbreitung ablehnen.

1. Markieren Sie im Adobe Campaign-Navigationsbaum den Knoten **[!UICONTROL Administration]** > **[!UICONTROL Kampagnen]** > **[!UICONTROL Typologieverwaltung]** > **[!UICONTROL Typologieregeln]**.
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

Wir möchten einen ersten Angebotsvorschlag der Kategorie Kanada versenden. Wenn das Angebot einmal von einem der Empfänger abgelehnt wird, wird es ihm nicht erneut angeboten.

1. Wählen Sie ein Profil aus dem Empfängerordner **Vielreisende** aus und prüfen Sie, für welche Angebote dieser Empfänger infrage kommt. Klicken Sie hierfür auf den Tab **[!UICONTROL Vorschläge]** und dann auf **[!UICONTROL Vorschau]**:

   Im vorliegenden Beispiel kommt **Peter Urlaubsreif** für ein Angebot aus der Kategorie **Kanada** infrage.

   ![](assets/offer_typology_example_015.png)

1. Erstellen Sie einen ersten E-Mail-Versand mit Angeboten an die Zielgruppe **Vielreisende**.
1. Wählen Sie die Parameter der Angebotsmodul-Abfrage aus.

   Im vorliegenden Beispiel wird die Kategorie **Amerika** gewählt. Sie enthält die Unterkategorien **USA** und **Kanada**.

   ![](assets/offer_typology_example_016.png)

1. Fügen Sie Ihre Angebote in den Text der Nachricht ein und versenden Sie die Nachricht. Weitere Informationen hierzu finden Sie im Abschnitt [Über Outbound-Kanäle](../../interaction/using/about-outbound-channels.md).

   Der zuvor ausgewählte Empfänger hat das für ihn infrage kommende Angebot wie geplant erhalten.

1. Aus dem Vorschlagsverlauf ist ersichtlich, dass der Empfänger das Angebot abgelehnt hat.

   ![](assets/offer_typology_example_018.png)

1. Prüfen Sie, für welche Angebote er nun infrage kommt.

   Es zeigt sich, dass kein Angebot zu Kanada ausgewählt wurde.

   ![](assets/offer_typology_example_019.png)

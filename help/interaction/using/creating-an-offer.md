---
title: Erstellung eines Angebots
seo-title: Erstellung eines Angebots
description: Erstellung eines Angebots
seo-description: null
page-status-flag: never-activated
uuid: 9e8b0351-e2a5-4043-be86-e275d2f849ea
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: 010c88f4-9444-448f-bb7b-7191517d2e23
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 100%

---


# Erstellung eines Angebots{#creating-an-offer}

## Angebote erstellen {#creating-the-offer}

Gehen Sie wie folgt vor, um ein Angebot zu erstellen:

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Angebote]** in der Rubrik **[!UICONTROL Kampagnen]**.

   ![](assets/offer_create_001.png)

1. Wählen Sie die **[!UICONTROL Erstellen]**-Schaltfläche aus.

   ![](assets/offer_create_005.png)

1. Benennen Sie das Angebot und wählen Sie die Kategorie aus, zu der es gehören soll.

   ![](assets/offer_create_002.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Erstellung abzuschließen.

   ![](assets/offer_create_003.png)

   Das Angebot ist nun in der Plattform verfügbar und kann konfiguriert werden.

   ![](assets/offer_create_004.png)

## Angebotseignungen konfigurieren {#configuring-offer-eligibility}

Im **[!UICONTROL Eignung]**-Tab des Angebots werden die Verwendungsdaten, auf die Zielgruppe anzuwendende Filter und die Angebotsgewichtung definiert.

### Verwendungsdaten definieren {#defining-the-eligibility-period-of-an-offer}

Wählen Sie mithilfe der Dropdown-Listen Start und Ende der Verwendung des Angebots aus den Kalendern aus.

![](assets/offer_eligibility_create_002.png)

Außerhalb dieses Zeitraums wird das Angebot nicht vom Angebotsmodul ausgewählt. Wenn Sie auch auf Ebene der Kategorie Verwendungsdaten definiert haben, kommt nur der sich überschneidende Zeitraum zum Tragen.

### Zielgruppenfilter {#filters-on-the-target}

Sie können mithilfe von Filtern die Zielgruppe der Angebote einschränken.

Klicken Sie hierfür auf den Link **[!UICONTROL Abfrage bearbeiten...]** und definieren Sie den anzuwendenden Filter. Lesen Sie diesbezüglich auch [diesen Abschnitt](../../platform/using/steps-to-create-a-query.md#step-4---filter-data).

![](assets/offer_eligibility_create_003.png)

Wenn bereits vordefinierte Filter erstellt wurden, können Sie diese in der Liste der Benutzerfilter auswählen. Weitere Informationen hierzu finden Sie unter [Vordefinierte Filter](../../interaction/using/creating-predefined-filters.md).

![](assets/offer_eligibility_create_004.png)

### Angebotsgewichtung {#offer-weight}

Um dem Angebotsmodul die Möglichkeit zu geben, zwischen verschiedenen für eine Person geeigneten Angeboten zu wählen, ist es empfehlenswert, jedem Angebot eine Gewichtung zuzuweisen. Sie können darüber hinaus Filter auf die Zielgruppe anwenden oder die Platzierung, auf die sich das Gewicht beziehen soll, einschränken. Ein Angebot mit einer höheren Gewichtung wird demzufolge einem Angebot mit niedriger Gewichtung vorgezogen.

Es besteht weiterhin die Möglichkeit, für ein Angebot verschiedene Gewichtungen zu definieren, z. B. in Bezug auf einen Zeitraum, eine Zielgruppe oder auch eine Platzierung.

Ein Angebot kann für Kontakte im Alter von 18 bis 25 Jahren eine Gewichtung A aufweisen und eine Gewichtung B für alle Kontakte über 25 Jahre. Einem Angebot, dessen Verwendungszeitraum auf die Sommermonate beschränkt ist, kann im Juli eine Gewichtung A und im August eine Gewichtung B zugewiesen werden.

>[!NOTE]
>
>Die zugewiesene Gewichtung kann vorübergehend entsprechend den Parametern der Kategorie geändert werden, zu der das Angebot gehört. Weitere Informationen hierzu finden Sie unter [Angebotskategorien](../../interaction/using/creating-offer-categories.md).

Gehen Sie wie folgt vor, um eine Gewichtung zu konfigurieren:

1. Wählen Sie **[!UICONTROL Hinzufügen]** aus.

   ![](assets/offer_weight_create_001.png)

1. Geben Sie den Wert der Gewichtung an und benennen Sie sie. Standardmäßig wird der Wert 1 zugeteilt.

   ![](assets/offer_weight_create_006.png)

   >[!CAUTION]
   >
   >Bei Angabe von 0 wird das Angebot als für die Zielgruppe nicht infrage kommend angesehen.

1. Geben Sie gegebenenfalls ein Start- und ein Enddatum ein.

   ![](assets/offer_weight_create_002.png)

1. Beschränken Sie bei Bedarf die Anwendung der Gewichtung auf eine bestimmte Platzierung.

   ![](assets/offer_weight_create_003.png)

1. Konfigurieren Sie einen Zielgruppenfilter.

   ![](assets/offer_weight_create_004.png)

1. Klicken Sie zum Abschluss auf **[!UICONTROL OK]**.

   ![](assets/offer_weight_create_005.png)

   >[!NOTE]
   >
   >Wenn ein bestimmtes Angebot mit verschiedenen Gewichtungen für einen Kontakt infrage kommt, wählt das Angebotsmodul die höchste Gewichtung aus. Das Angebotsmodul schlägt pro Abfrage einem Kontakt jedes Angebot maximal einmal vor.

### Übersicht der für ein Angebot konfigurierten Eignungsregeln {#a-summary-of-offer-eligibility-rules}

Im Dashboard des Angebots können Sie auf die Details der Eignungskonfiguration zugreifen.

Klicken Sie hierfür auf den Link **[!UICONTROL Planung und Eignungsregeln des Angebots]**.

![](assets/offer_eligibility_create_005.png)

## Angebotsinhalte erstellen {#creating-the-offer-content}

1. Gehen Sie in den **[!UICONTROL Bearbeiten]**-Tab des Angebots und klicken Sie auf **[!UICONTROL Inhalt]**.

   ![](assets/offer_content_create_001.png)

1. Füllen Sie die diversen zur Verfügung stehenden Felder aus:

   * **[!UICONTROL Titel]**: Geben Sie den Titel an, der bei Unterbreitung des Angebots angezeigt werden soll. (Hinweis: Es handelt sich hierbei nicht um den Titel, der im Tab **[!UICONTROL Allgemein]** vergeben wurde.)
   * **[!UICONTROL Ziel-URL]**: Geben Sie die URL Ihres Angebots an. Um korrekt verarbeitet werden zu können, muss sie zwingend mit &quot;http://&quot; oder &quot;https://&quot; beginnen.
   * **[!UICONTROL Bild-URL]**: Geben Sie die URL oder einen Zugangspfad für das Bild Ihres Angebots an.
   * **[!UICONTROL HTML-Inhalt]**/**[!UICONTROL Textinhalt]**: Geben Sie den Body Ihres Angebots in den Tab Ihrer Wahl ein. Um Tracking zu generieren, muss der **[!UICONTROL HTML-Inhalt]** aus HTML-Elementen bestehen, die in ein `<div>`-Typelement eingeschlossen werden können. Beispielsweise erzeugt ein `<table>`-Element auf der HTML-Seite Folgendes:

   ```
      <div> 
       <table>
        <tr>
         <th>Month</th>
         <th>Savings</th>   
        </tr>   
        <tr>    
         <td>January</td>
         <td>$100</td>   
        </tr> 
       </table> 
      </div>
   ```

   Die Definition der Annahme-URL wird im Abschnitt [Konfiguration des Status bei Annahme des Vorschlags](../../interaction/using/creating-offer-spaces.md#configuring-the-status-when-the-proposition-is-accepted) beschrieben.

   ![](assets/offer_content_create_002.png)

   Durch Klick auf den Link **[!UICONTROL Inhaltsdefinition]** können Sie prüfen, welche Felder in der Platzierungskonfiguration als Pflichtfelder definiert wurden. Weitere Informationen hierzu finden Sie unter [Angebotsplatzierungen](../../interaction/using/creating-offer-spaces.md).

   ![](assets/offer_content_create_003.png)

   In unserem Beispiel muss das Angebot mindestens einen Titel, ein Bild, einen HTML-Inhalt und eine Ziel-URL aufweisen.

## Angebotsvorschau {#previewing-the-offer}

Sobald der Angebotsinhalt konfiguriert wurde, können Sie die endgültige Darstellung des Angebots für die Empfänger prüfen. Gehen Sie wie folgt vor:

1. Klicken Sie auf den **[!UICONTROL Vorschau]**-Tab.

   ![](assets/offer_preview_create_001.png)

1. Wählen Sie die Darstellung aus, die Sie prüfen möchten.

   ![](assets/offer_preview_create_002.png)

1. Wenn Sie den Inhalt des Angebots personalisiert haben, ist die Auswahl eines Empfängers erforderlich, um die Personalisierung prüfen zu können.

   ![](assets/offer_preview_create_003.png)

## Angebotshypothese erstellen {#creating-a-hypothesis-on-an-offer}

Sie haben die Möglichkeit, Hypothesen bezüglich Ihrer Angebotsvorschläge zu definieren. Auf diese Weise lässt sich der Einfluss der Angebote auf die Verkaufszahlen des derart beworbenen Produkts ermitteln.

>[!NOTE]
>
>Die Hypothesen werden mithilfe von Response Manager erstellt. Bitte prüfen Sie Ihren Lizenzvertrag.

Die zu einem Angebotsvorschlag definierten Hypothesen können im Tab **[!UICONTROL Messung]** des Angebots eingesehen werden.

Weiterführende Informationen zum Erstellen von Hypothesen finden Sie auf [dieser Seite](../../campaign/using/about-response-manager.md).

![](assets/offer_hypothesis_001.png)


---
title: Dynamisches Bild einfügen
seo-title: Dynamisches Bild einfügen
description: Dynamisches Bild einfügen
seo-description: null
page-status-flag: never-activated
uuid: 4acc905e-625c-45aa-bb70-7dde22911aa0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-target
discoiquuid: f6e4d22b-4ad3-4a1e-8a6f-3bdfc1da0535
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f4d5d8474099776f770e88fcaf3bf15256da1be2

---


# Inserting Target dynamic content {#inserting-a-dynamic-image}

In diesem Dokument erfahren Sie, wie Sie ein dynamisches Angebot von Target in eine E-Mail in Adobe Campaign integrieren können.

Wir möchten einen Versand erstellen, der einen Bild-Baustein enthält, der sich entsprechend dem Land des Empfängers dynamisch ändert. Die Daten werden bei jeder mbox-Abfrage gesendet und sind abhängig von der IP-Adresse des Besuchers.

Wir möchten, dass eines der Bilder in dieser E-Mail entsprechend den folgenden Benutzererlebnissen dynamisch angepasst wird:

* Die E-Mail wird in Frankreich geöffnet.
* Die E-Mail wird in den USA geöffnet.
* Wenn keine dieser Bedingungen zutrifft, wird ein Standardbild angezeigt.

![](assets/target_4.png)

Damit dies funktioniert, müssen wir die folgenden Schritte sowohl in Adobe Campaign als auch in der Zielgruppe durchführen:

1. [Einfügen des dynamischen Angebots in eine E-Mail](../../integrations/using/inserting-a-dynamic-image.md#inserting-dynamic-offer)
1. [Erstellen von Umleitungsangeboten](../../integrations/using/inserting-a-dynamic-image.md#create-redirect-offers)
1. [Audiences erstellen](../../integrations/using/inserting-a-dynamic-image.md#audiences-target)
1. [Erstellen einer Erlebnis-Targeting-Aktivität](../../integrations/using/inserting-a-dynamic-image.md#creating-targeting-activity)
1. [Erstellen der Vorschau und Senden der E-Mail](../../integrations/using/inserting-a-dynamic-image.md#preview-send-email)

## Einfügen des dynamischen Angebots in eine E-Mail {#inserting-dynamic-offer}

Sobald Sie mit der Definition der Zielgruppe und des Inhalts Ihrer E-Mail in Adobe Campaign fertig sind, können Sie ein dynamisches Bild aus Target einfügen.

Geben Sie dazu die URL des Standardbildes an, den Speicherort und die Felder, die an Target übermittelt werden sollen.

In Adobe Campaign gibt es zwei Möglichkeiten, ein dynamisches Bild von Target in eine E-Mail einzufügen:

* Wenn Sie den Editor für digitale Inhalte verwenden, wählen Sie ein vorhandenes Bild und wählen Sie **[!UICONTROL Insert]** > **[!UICONTROL Dynamic image served by Adobe Target]** aus der Symbolleiste.

   ![](assets/target_5.png)

* If you are using the standard editor, place the cursor where you want to insert the image and select **[!UICONTROL Include]** > **[!UICONTROL Dynamic image served by Adobe Target...]** from the personalization drop-down menu.

   ![](assets/target_12.png)

### Definieren der Bildparameter {#defining-image-parameters}

* The **[!UICONTROL Default image]**&#39;s URL: The image that will be displayed when none of the conditions are fulfilled. Sie können auch ein Bild aus Ihrer Assets-Bibliothek verwenden.
* The **[!UICONTROL Target location]**: Enter a name for your dynamic offer&#39;s location. Sie müssen diesen Speicherort später in Ihrer Target-Aktivität auswählen.
* Die **[!UICONTROL Landing Page]**: Wenn das Standardbild zu einer Standardbild-Landingpage umgeleitet werden soll. Diese URL gilt nur für die Fälle, in denen das Standardbild in der letzten E-Mail angezeigt wird und optional ist.
* The **[!UICONTROL Additional decision parameters]**: Specify the mapping between the fields defined in the Adobe Target segments and the Adobe Campaign fields. Die in Adobe Campaign verwendeten Felder müssen zuvor in der Rawbox angegeben werden. In unserem Beispiel haben wir das Feld Land hinzugefügt.

Wenn Sie in Adobe Zielgruppe Berechtigungen für Unternehmen verwenden, fügen Sie die entsprechende Eigenschaft in dieses Feld ein. Weitere Informationen zu Berechtigungen für Zielgruppe Enterprise finden Sie auf [dieser Seite](https://marketing.adobe.com/resources/help/en_US/target/target/properties-overview.html).

![](assets/target_13.png)

## Erstellen von Umleitungsangeboten {#create-redirect-offers}

In Zielgruppe können Sie verschiedene Versionen Ihres Angebots erstellen. Für jedes Benutzererlebnis können Sie ein spezifisches Umleitungsangebot definieren und ein anderes Bild wählen.

In unserem Fall benötigen wir zwei Umleitungsangebote. Das dritte (das Standardangebot) wird in Adobe Campaign definiert.

1. Um ein neues Umleitungs-Angebot in Zielgruppe Standard zu erstellen, klicken Sie auf der **[!UICONTROL Content]** Registerkarte auf **[!UICONTROL Code offers]**.

1. Klicken Sie **[!UICONTROL Create]** dann auf **[!UICONTROL Redirect Offer]**.

   ![](assets/target_9.png)

1. Geben Sie einen Namen für das Angebot und die URL Ihres Bildes ein.

   ![](assets/target_6.png)

1. Führen Sie dieselben Schritte für das andere Umleitungsangebot durch. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](https://docs.adobe.com/help/en/target/using/experiences/offers/offer-redirect.html).

## Audiences erstellen {#audiences-target}

In Zielgruppe müssen Sie die beiden Audiencen erstellen, in die die Personen, die Ihr Angebot besuchen, für die verschiedenen bereitzustellenden Inhalte kategorisiert werden. Fügen Sie für jede Zielgruppe eine Regel hinzu, um festzulegen, wer das Angebot sehen kann.

1. Um eine neue Audience in Zielgruppe zu erstellen, klicken Sie auf der **[!UICONTROL Audiences]** Registerkarte auf **[!UICONTROL Create Audience]**.

   ![](assets/audiences_1.png)

1. Hinzufügen Sie Ihrer Audience einen Namen.

   ![](assets/audiences_2.png)

1. Click **[!UICONTROL Add a rule]** and select a category. Die Regel nutzt spezifische Kriterien für die Besucher. Sie können die Regeln verfeinern, indem Sie Bedingungen hinzufügen oder neue Regeln in anderen Kategorien erstellen.

1. Führen Sie dieselben Schritte für die anderen Zielgruppen durch.

## Erstellen einer Erlebnis-Targeting-Aktivität {#creating-targeting-activity}

In Zielgruppe müssen wir eine Erlebnis-Targeting-Aktivität erstellen, die verschiedenen Erlebnisse definieren und sie mit den entsprechenden Angeboten verknüpfen.

### Audience definieren {#defining-the-audience}

1. Um eine Erlebnis-Targeting-Aktivität zu erstellen, klicken Sie auf der **[!UICONTROL Activities]** Registerkarte **[!UICONTROL Create Activity]** dann **[!UICONTROL Experience Targeting]**.

   ![](assets/target_10.png)

1. Wählen Sie **[!UICONTROL Form]** als **[!UICONTROL Experience Composer]**.

1. Wählen Sie eine Audience, indem Sie auf die **[!UICONTROL Change audience]** Schaltfläche klicken.

   ![](assets/target_10_2.png)

1. Wählen Sie die Audience aus, die in den vorherigen Schritten erstellt wurde.

   ![](assets/target_10_3.png)

1. Erstellen Sie ein weiteres Erlebnis, indem Sie auf **[!UICONTROL Add Experience Targeting]**.

### Definieren des Speicherorts und Inhalts {#defining-location-content}

Fügen Sie für jede Zielgruppe Inhalt hinzu:

1. Wählen Sie den Ortsnamen aus, den Sie beim Einfügen des dynamischen Angebots in Adobe Campaign ausgewählt haben.

   ![](assets/target_15.png)

1. Klicken Sie auf die Dropdownschaltfläche und wählen Sie **[!UICONTROL Change Redirect Offer]**.

   ![](assets/target_content.png)

1. Wählen Sie das zuvor erstellte Umleitungsangebot aus.

   ![](assets/target_content_2.png)

1. Befolgen Sie die gleichen Schritte für das zweite Erlebnis.

### Definieren der Aktivität {#defining-activity}

The **[!UICONTROL Target]** window summarizes your activity. Bei Bedarf können Sie weitere Erlebnisse hinzufügen.

![](assets/target_experience.png)

The **[!UICONTROL Goal & Settings]** window allows you to personalize your activity by setting a priority, an objective, or a duration.

The **[!UICONTROL Reporting Settings]** section lets you select an action and edit the parameters that will determine when your goal is achieved.

![](assets/target_experience_2.png)

## Anzeigen einer Vorschau und Senden der E-Mail in Campaign Classic {#preview-send-email}

Sie können nun in Adobe Campaign Ihre E-Mail in der Vorschau ansehen und ihre Darstellung bei verschiedenen Empfängern testen. Sie werden bemerken, dass sich das Bild entsprechend den unterschiedlichen Erlebnissen ändert. To learn more on email creation, refer to this [page](../../delivery/using/defining-the-email-content.md).

Jetzt können Sie Ihre E-Mail einschließlich eines dynamischen Angebots von Target versenden.

![](assets/target_20.png)

---
product: campaign
title: 'Anwendungsfall: Erstellen eines E-Mail-Versands'
description: 'Anwendungsfall: Erstellen eines E-Mail-Versands'
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Web Apps, Web Forms, Landing Pages, Email Design
exl-id: e2679f12-459b-466d-9c82-60a28363b104
TQID: https://experienceleague.adobe.com/5j2bwBpCx4WAyHD4jyypi5EMhw3NS-11-HkoTQ9AnU4
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
subfeature_v2:
  - id: f391046b-0cf3-4e76-bd3b-97fe06654506
  - id: ed29abcd-b6a8-4d4b-ab8b-b7e746973281
  - id: d7be2b01-dc9c-40f7-aace-a151707504ed
  - id: e739ee2b-6228-412e-878f-45de0791417d
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 804
ht-degree: 100%

---

# Anwendungsfall: Erstellen eines E-Mail-Versands{#use-case-creating-an-email-delivery}



In diesem Anwendungsbeispiel lernen Sie die Schritte zum Erstellen eines E-Mail-Versands mit Adobe Campaign Digital Content Editor (DCE) kennen.

Ein Versand soll mit einer personalisierten Vorlage erstellt werden, die Folgendes enthält:

* Eine direkte Adresse des Empfängers (unter Verwendung des Vor- und Nachnamens)
* Zwei Typen von Links auf eine externe URL
* Eine Mirrorseite
* Einen Link auf eine Webanwendung

>[!NOTE]
>
>Bevor Sie beginnen, muss mindestens eine **HTML-Vorlage** entsprechend dem Inhalt Ihrer künftigen Sendungen konfiguriert werden.
>
>Stellen Sie in den **[!UICONTROL Versandeigenschaften]** sicher, dass die **[!UICONTROL Inhaltserstellung]** (auf dem Tab **[!UICONTROL Erweitert]**) auf **[!UICONTROL DCE]** gesetzt ist. Um sicherzustellen, dass der Editor optimal funktioniert, lesen Sie die [Best Practices bei der Inhaltsbearbeitung](content-editing-best-practices.md).

## Schritt 1: Erstellen eines Versands {#step-1---creating-a-delivery}

Um einen neuen Versand zu erstellen, platzieren Sie den Cursor auf dem Tab **Kampagnen** und klicken Sie auf **Sendungen**. Klicken Sie dann über der Liste der vorhandenen Sendungen auf die Schaltfläche **Erstellen**. Weiterführende Informationen zur Erstellung eines Versands finden Sie auf [dieser Seite](../../delivery/using/about-email-channel.md).

![](assets/delivery_step_1.png)

## Schritt 2: Auswählen einer Vorlage {#step-2---selecting-a-template}

Wählen Sie eine Versandvorlage aus und benennen Sie Ihren Versand. Dieser Name ist nur für Benutzende der Adobe Campaign-Konsole sichtbar, nicht aber für die Empfangenden. Die Bezeichnung wird aber in der Liste der Sendungen angezeigt. Bestätigen Sie die Angaben mit der Schaltfläche **[!UICONTROL Fortfahren]**.

![](assets/dce_delivery_model.png)

## Schritt 3: Auswählen eines Inhalts {#step-3---selecting-a-content}

Der Digital Content Editor verfügt über verschiedene native Vorlagen mit unterschiedlichen Strukturen (Spalten, Textbereiche etc.).

Wählen Sie die Inhaltsvorlage aus, das Sie verwenden möchten, und verwenden Sie dann die Schaltfläche **[!UICONTROL Mit dem ausgewählten Inhalt beginnen]**, um die Vorlage im erstellten Versand anzuzeigen.

![](assets/dce_select_model.png)

Darüber hinaus besteht die Möglichkeit, außerhalb von Adobe Campaign erstellte HTML-Inhalte zu importieren, indem Sie die Option **[!UICONTROL Aus einer Datei]** auswählen.

![](assets/dce_select_from_file_template.png)

Sie können diesen Inhalt zur künftigen Verwendung als Vorlage speichern. Nachdem eine personalisierte Inhaltsvorlage erstellt wurde, können Sie sich eine Vorschau in der Liste der Vorlagen ansehen. Konsultieren Sie diesbezüglich die [Vorlagenverwaltung](template-management.md).

>[!CAUTION]
>
>Wenn Sie die **Adobe Campaign-Webschnittstelle** verwenden, müssen Sie eine ZIP-Datei mit dem HTML-Inhalt und den entsprechenden Bildern importieren.

## Schritt 4: Gestalten der Nachricht {#step-4---designing-the-message}

* Vor- und Nachnamen der Empfänger anzeigen

  Um den Vor- und Nachnamen der Empfänger in ein Textfeld Ihres Versands einzufügen, klicken Sie auf das gewünschte Textfeld und platzieren Sie den Cursor an die Stelle, wo der Name angezeigt werden soll. Klicken Sie auf das erste Symbol in der Pop-up-Symbolleiste und danach auf **[!UICONTROL Gestaltungsbaustein]**. Wählen Sie **[!UICONTROL Grußformeln]** und danach **[!UICONTROL OK]** aus.

  ![](assets/dce_personalizationblock_greetings.png)

* Link in ein Bild einfügen

  Um Empfänger eines Versands über ein Bild zu einer externen Adresse weiterzuleiten, klicken Sie auf das jeweilige Bild, um die Symbolleiste zu öffnen, platzieren Sie den Cursor auf das erste Symbol und wählen Sie dann **[!UICONTROL Link auf eine externe URL]** aus. Weitere Informationen finden Sie unter [Link hinzufügen](editing-content.md#adding-a-link).

  ![](assets/dce_externalpage.png)

  Geben Sie die URL für den Link im Feld **URL** im Format **https://www.myURL.com** ein und bestätigen Sie dann Ihre Eingabe.

  Der Link kann jederzeit im rechten Fensterbereich geändert werden.

* Link in Text einfügen

  Um einen externen Link in den Text Ihres Versands einzufügen, wählen Sie Text aus und klicken Sie auf das erste Symbol der Pop-up-Symbolleiste. Wählen Sie **[!UICONTROL Link auf eine externe URL]** aus und geben Sie im Feld **[!UICONTROL URL]** die Adresse des Links ein. Weitere Informationen finden Sie unter [Link hinzufügen](editing-content.md#adding-a-link).

  Der Link kann jederzeit im rechten Fensterbereich geändert werden.

  >[!CAUTION]
  >
  >Der im Feld **[!UICONTROL Titel]** eingegebene Text ersetzt den ursprünglichen Text.

* Mirrorseite hinzufügen

  Um Empfängern zu ermöglichen, Ihren Versandinhalt in einem Webbrowser zu sehen, können Sie in Ihrem Versand einen Link zu einer Mirrorseiten integrieren.

  Klicken Sie auf das Textfeld, in dem der Link erscheinen soll. Klicken Sie auf das erste Symbol in der Pop-up-Symbolleiste und wählen Sie **[!UICONTROL Gestaltungsbaustein]** und danach **[!UICONTROL Mirrorseiten-Link (MirrorPage)]** aus. Klicken Sie zur Bestätigung auf **[!UICONTROL Speichern]**.

  ![](assets/dce_mirrorpage.png)

  >[!CAUTION]
  >
  >Der Titel des Gestaltungsbausteins ersetzt automatisch den Originaltext in Ihrem Versand.

* Einen Link auf eine Webanwendung integrieren

  Mit dem Digital Content Editor können Sie über die Adobe Campaign-Konsole Links auf Webanwendungen integrieren, z. B. auf eine Landingpage oder Formularseite. Weitere Informationen hierzu finden Sie unter [Link auf eine Webanwendung](editing-content.md#link-to-a-web-application).

  Wählen Sie ein Textfeld für Ihren Link auf eine Webanwendung aus und klicken Sie dann auf das erste Symbol. Wählen Sie **[!UICONTROL Link auf eine Webanwendung]** und danach die gewünschte Anwendung aus, indem Sie auf das Symbol am Ende des Feldes **Webanwendung** klicken.

  ![](assets/dce_webapp.png)

  Klicken Sie zur Bestätigung auf **Speichern**.

  >[!NOTE]
  >
  >Für diesen Schritt müssen Sie zunächst mindestens eine Webanwendung speichern. Diese finden Sie auf dem Tab **[!UICONTROL Kampagnen > Webanwendungen]** Ihrer Konsole.

## Schritt 5: Speichern des Versands {#step-5---saving-the-delivery}

Nachdem der Inhalt integriert wurde, speichern Sie den Versand, indem Sie auf **Speichern** klicken. Er wird nun in Ihrer Liste der Sendungen angezeigt, die Sie auf dem Tab **[!UICONTROL Kampagnen > Sendungen]** finden.

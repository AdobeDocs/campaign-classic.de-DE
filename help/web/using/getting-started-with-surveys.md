---
title: Umfragen – Erste Schritte
seo-title: Umfragen – Erste Schritte
description: Umfragen – Erste Schritte
seo-description: null
page-status-flag: never-activated
uuid: 62ca684c-94a7-465a-9536-75e8a96b1c0e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: 2df82006-dcc3-4b07-bc36-b646b1c27aaa
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Umfragen – Erste Schritte{#getting-started-with-surveys}

Hier finden Sie einen kurzen Überblick über die wichtigsten Schritte zur Erstellung einer einfachen Umfrage unter Verwendung der folgenden Vorlage:

![](assets/s_ncs_admin_survey_result.png)

Die einzelnen Schritte sind:

1. [Schritt 1: Erstellen einer Umfrage](#step-1---creating-a-survey),
1. [Schritt 2: Auswählen einer Vorlage](#step-2---selecting-the-template),
1. [Schritt 3: Zusammenstellen der Umfrage](#step-3---building-the-survey),
1. [Schritt 4: Erstellen des Seiteninhalts](#step-4---creating-the-page-content),
1. [Schritt 5: Speichern der Umfragedaten](#step-5---storing-the-survey-data-),
1. [Schritt 6: Publizieren der Seiten](#step-6---publishing-the-pages),
1. [Schritt 7: Freigeben Ihrer Online-Umfrage](#step-7---sharing-your-online-survey).

## Schritt 1: Erstellen einer Umfrage {#step-1---creating-a-survey}

Um eine neue Umfrage zu erstellen, gehen Sie zur **[!UICONTROL Campaigns]** Registerkarte oder **[!UICONTROL Profiles and targets]** klicken Sie auf das **[!UICONTROL Web Applications]** Menü. Click the **[!UICONTROL Create]** button above the list of forms.

![](assets/s_ncs_admin_survey_create.png)

## Schritt 2: Auswählen einer Vorlage {#step-2---selecting-the-template}

Wählen Sie eine Umfragevorlage und geben Sie der Umfrage einen Namen. Dieser Name wird von den Endbenutzern nicht angezeigt, ermöglicht jedoch die Identifizierung der Umfrage in Adobe Campaign. Klicken Sie auf **[!UICONTROL Save]** , um die Umfrage der Liste der Webanwendungen hinzuzufügen.

![](assets/s_ncs_admin_survey_wz_00.png)

## Schritt 3: Zusammenstellen der Umfrage {#step-3---building-the-survey}

Umfragen werden in einer Grafik durch Platzierung der folgenden Elemente erstellt: die Seite(n), wo der Inhalt erstellt wird, die Schritte zum Vorausfüllen der Daten und zum Speichern sowie die Testphasen. Zusätzlich können Skripts und Abfragen eingefügt werden.

To build the chart, click the **[!UICONTROL Edit]** form of the survey.

Eine Umfrage muss **zumindest** die folgenden drei Komponenten enthalten: eine Seite, eine Speicherungsbox und eine Endseite.

* To create a page, select the **[!UICONTROL Page]** object in the left-hand section of the editor and deposit it in the middle section, as shown below:

   ![](assets/s_ncs_admin_survey_new_page.png)

* Next, select the **[!UICONTROL Storage]** object and place it on the output transition of the page.
* Finally, select the **[!UICONTROL End]** object and place it on the end of the output transition of the storage box to obtain the following diagram:

   ![](assets/s_ncs_admin_survey_end.png)

## Schritt 4: Erstellen des Seiteninhalts {#step-4---creating-the-page-content}

Im folgenden Beispiel verwenden wir eine **[!UICONTROL Page (v5 compatibility)]** Typseite. Auf diesen Seitentyp wird über das erweiterte Menü der **[!UICONTROL Edit]** Registerkarte zugegriffen.

![](assets/s_ncs_admin_survey_pagev5.png)

* Eingabefelder hinzufügen

   Um den Inhalt der Seite zu erstellen, müssen Sie sie bearbeiten: Doppelklicken Sie dazu auf das **[!UICONTROL Page]** Objekt. Klicken Sie auf das erste Symbol in der Symbolleiste, um den Assistenten zum Erstellen von Feldern zu öffnen. Um ein Eingabefeld für den Benutzernamen zu erstellen, der im entsprechenden Feld des Empfängerprofils gespeichert werden soll, wählen Sie **[!UICONTROL Edit a recipient]**.

   ![](assets/s_ncs_admin_survey_add_field_menu.png)

   Klicken Sie auf die **[!UICONTROL Next]** Schaltfläche, um das Feld für die Datenspeicherung in der Datenbank auszuwählen. In diesem Fall das Feld &quot;Nachname&quot;.

   ![](assets/s_ncs_admin_survey_choose_field.png)

   Click **[!UICONTROL Finish]** to confirm field creation.

   Wenn die Informationen in einem bereits in der Datenbank vorhandenen Feld gespeichert werden, nimmt das Feld standardmäßig den Namen des ausgewählten Felds an, d. h. in diesem Beispiel &quot;Nachname&quot;. Sie können diese Bezeichnung folgendermaßen ändern:

   ![](assets/s_ncs_admin_survey_change_label.png)

   Erstellen Sie jetzt ein Eingabefeld für die Kundennummer. Wiederholen Sie den Vorgang und wählen Sie das Feld &quot;Kundennummer&quot; aus.

   Wiederholen Sie dieselben Schritte, um ein Feld für die E-Mail-Adresse des Benutzers hinzuzufügen.

* To create a question, right-click the last element in the tree, and select **[!UICONTROL Containers > Question]** , or click the **[!UICONTROL Containers]** icon and select **[!UICONTROL Question]**.

   ![](assets/s_ncs_admin_survey_add_qu.png)

   Geben Sie die Bezeichnung der Frage ein und fügen Sie das/die Antwortfeld(e) als Unterzweig der Frage ein. Dazu muss der mit der Frage verknüpfte Knoten beim Erstellen des Antwortfelds ausgewählt werden. Fügen Sie eine **[!UICONTROL drop-down listx]** mit dem **[!UICONTROL Selection controls]** Symbol oder durch Rechtsklicken hinzu, wie unten dargestellt:

   ![](assets/s_ncs_admin_survey_add_list.png)

   Wählen Sie einen Speicherort aus: Wählen Sie ein Auflistungsfeld aus, um die Werte automatisch abzurufen (in diesem Fall das E-Mail-Format).

   ![](assets/s_ncs_admin_survey_add_itz_list.png)

   Klicken Sie auf der **[!UICONTROL General]** Registerkarte auf den **[!UICONTROL Initialize the list of values from the database]** Link: die Tabelle der Werte wird automatisch eingegeben.

   ![](assets/s_ncs_admin_survey_add_value.png)

   Click **[!UICONTROL OK]** to close the editor, and **[!UICONTROL Save]** to save changes.

   >[!NOTE]
   >
   >Für jedes Feld oder jede Frage können Sie das Seitenlayout an Ihre Anforderungen anpassen, dank der Optionen in der **[!UICONTROL Advanced]** Registerkarte. Das Layout der Umfrageseiten ist in [diesem Abschnitt](../../web/using/about-web-forms.md)ausführlich beschrieben.

   In the detail screen, click the **[!UICONTROL Preview]** tab to view the rendering of the survey you have just created.

   ![](assets/s_ncs_admin_survey_preview.png)

## Schritt 5: Speichern der Umfragedaten {#step-5---storing-the-survey-data-}

Mit der Speicherungsbox können Sie die Antworten der Benutzer in der Datenbank speichern. Wählen Sie dazu einen Abstimmschlüssel aus, um die bereits in der Datenbank vorhandenen Profile zu identifizieren.

Bearbeiten Sie dazu die Box und wählen Sie das Feld aus, das bei der Datenspeicherung als Abstimmschlüssel verwendet wird.

Im unten stehenden Beispiel passiert Folgendes bei der Speicherung (Bestätigung): Wenn ein Profil in der Datenbank gespeichert wird, dessen Kundennummer der im Formular eingegebenen Kundenummer entspricht, wird das Profil aktualisiert. Wenn das Profil noch nicht existiert, wird es erstellt.

![](assets/s_ncs_admin_survey_save_edit.png)

Click **[!UICONTROL OK]** to confirm, then click **[!UICONTROL Save]** to save the survey

## Schritt 6: Publizieren der Seiten {#step-6---publishing-the-pages}

Damit die Benutzer auf die HTML-Seiten zugreifen können, muss die Anwendung verfügbar gemacht werden. Dazu müssen Sie vom Bearbeitungsstatus in den Produktionsstatus wechseln, d. h. die Umfrage publizieren. Gehen Sie dazu wie folgt vor:

* Click the **[!UICONTROL Publish]** button located above the survey dashboard.
* Wählen Sie **[!UICONTROL Start]** aus, um die Publikation zu starten und den Assistenten zu schließen.

   ![](assets/s_ncs_admin_survey_start_publ.png)

   Der Status der Umfrage wechselt zu: **Online**.

   ![](assets/survey_published.png)

## Schritt 7: Freigeben Ihrer Online-Umfrage {#step-7---sharing-your-online-survey}

Sobald sich die Umfrage im Produktionsstatus befindet, kann sie am Server aufgerufen und von Ihnen bereitgestellt werden. Die URL für den Zugriff auf die Umfrage wird im Dashboard angezeigt.

![](assets/survey_url_from_dashboard.png)

Um die Umfrage bereitzustellen, können Sie beispielsweise eine Nachricht mit einem Zugangslink an die Zielpopulation senden oder die Zugriffs-URL auf eine Webseite stellen.

Sie können die Antworten der Benutzer dann mit Berichten und Logs überwachen. Siehe [Antworten tracken](../../web/using/publish--track-and-use-collected-data.md#response-tracking).

>[!CAUTION]
>
>Die öffentliche URL beinhaltet den internen Namen der Umfrage. Wenn dieser geändert wird, wird die URL automatisch aktualisiert. Auch alle Links zur Umfrage müssen dann aktualisiert werden.
>
>Wenn Nachrichten mit dem Link zur Umfrage bereits versendet wurden, funktioniert dieser Link nicht mehr.


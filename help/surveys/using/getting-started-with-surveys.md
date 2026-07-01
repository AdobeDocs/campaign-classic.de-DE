---
product: campaign
title: Wichtige Schritte zum Erstellen einer Umfrage
description: Erste Umfrage mit Campaign erstellen
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Surveys
exl-id: 22e14b24-59ba-4a92-8ffb-f5336793d64f
TQID: https://experienceleague.adobe.com/04KSAxQjavqf-LzX7Ued7pPpggSDfgueZAAqHT6X81M
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: a4671286-a59f-47e3-b97b-90627a1977d5
subfeature_v2: id: ed29abcd-b6a8-4d4b-ab8b-b7e746973281
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 993
ht-degree: 100%

---

# Wichtige Schritte zum Erstellen einer Umfrage{#getting-started-with-surveys}



Hier finden Sie einen kurzen Überblick über die wichtigsten Schritte zur Erstellung einer einfachen Umfrage unter Verwendung der folgenden nativen Vorlage:

![](assets/s_ncs_admin_survey_result.png)

Die einzelnen Schritte sind:

1. [Schritt 1: Erstellen einer Umfrage](#step-1---creating-a-survey),
1. [Schritt 2: Auswählen der Vorlage](#step-2---selecting-the-template),
1. [Schritt 3: Zusammenstellen der Umfrage](#step-3---building-the-survey),
1. [Schritt 4: Erstellen des Seiteninhalts](#step-4---creating-the-page-content),
1. [Schritt 5: Speichern der Umfragedaten](#step-5---storing-the-survey-data-),
1. [Schritt 6: Veröffentlichen der Seiten](#step-6---publishing-the-pages),
1. [Schritt 7: Freigeben Ihrer Online-Umfrage](#step-7---sharing-your-online-survey).

## Schritt 1: Erstellen einer Umfrage {#step-1---creating-a-survey}

Um eine neue Umfrage zu erstellen, rufen Sie die Registerkarte **[!UICONTROL Kampagnen]** oder **[!UICONTROL Profile und Zielgruppen]** auf und klicken Sie auf das Menü **[!UICONTROL Webanwendungen]**. Klicken Sie auf die Schaltfläche **[!UICONTROL Erstellen]** oberhalb der Formularliste.

![](assets/s_ncs_admin_survey_create.png)

## Schritt 2: Auswählen der Vorlage {#step-2---selecting-the-template}

Wählen Sie eine Umfragevorlage aus und benennen Sie die Umfrage. Dieser Name ist für die Endbenutzenden unsichtbar, er dient lediglich zur Identifikation der Umfrage innerhalb von Adobe Campaign. Wählen Sie **[!UICONTROL Speichern]**, um die Umfrage zur Liste der Web-Anwendungen hinzuzufügen.

![](assets/s_ncs_admin_survey_wz_00.png)

## Schritt 3: Zusammenstellen der Umfrage {#step-3---building-the-survey}

Umfragen werden in einer Grafik durch Platzierung der folgenden Elemente erstellt: die Seite(n), wo der Inhalt erstellt wird, die Schritte zum Vorausfüllen der Daten und zum Speichern sowie die Testphasen. Skripte und Abfragen können auch eingefügt werden.

Um die Grafik zu erstellen, wählen Sie das **[!UICONTROL Bearbeitungsformular]** der Umfrage aus.

Eine Umfrage muss **zumindest** die folgenden drei Komponenten enthalten: eine Seite, eine Speicherungsbox und eine Endseite.

* Um eine Seite zu erstellen, wählen Sie im linken Bereich des Editors das Objekt **[!UICONTROL Seite]** aus und legen Sie es wie unten gezeigt in der Mitte ab:

  ![](assets/s_ncs_admin_survey_new_page.png)

* Wählen Sie danach das Objekt **[!UICONTROL Speicherung]** aus und platzieren Sie es auf der ausgehenden Transition der Seite.
* Wählen Sie abschließend das Objekt **[!UICONTROL Ende]** aus und platzieren Sie es am Ende der ausgehenden Transition der Speicherungsbox. Sie erhalten somit die folgende Grafik:

  ![](assets/s_ncs_admin_survey_end.png)

## Schritt 4: Erstellen des Seiteninhalts {#step-4---creating-the-page-content}

Im folgenden Beispiel wird die Seite vom Typ **[!UICONTROL Seite (V5-Kompatibilität)]** verwendet. Der Zugriff auf diesen Seitentyp erfolgt über das erweiterte Menü auf der Registerkarte **[!UICONTROL Bearbeiten]**.

![](assets/s_ncs_admin_survey_pagev5.png)

* **Eingabefelder hinzufügen**

  Um den Inhalt der Seite zu erstellen, müssen Sie sie bearbeiten: Doppelklicken Sie dazu auf das Objekt **[!UICONTROL Seite]**. Klicken Sie auf das erste Symbol in der Symbolleiste, um den Assistenten zur Felderstellung zu öffnen. Um ein Eingabefeld für den Benutzernamen zu erstellen, der im entsprechenden Feld des Empfängerprofils gespeichert werden soll, wählen Sie **[!UICONTROL Empfänger bearbeiten]**.

  ![](assets/s_ncs_admin_survey_add_field_menu.png)

  Klicken Sie auf die Schaltfläche **[!UICONTROL Weiter]**, um das Feld für die Datenspeicherung in der Datenbank festzulegen. In diesem Fall das Feld „Nachname“.

  ![](assets/s_ncs_admin_survey_choose_field.png)

  Wählen Sie zur Bestätigung der Felderstellung die Option **[!UICONTROL Beenden]**.

  Wenn die Informationen in einem bereits in der Datenbank vorhandenen Feld gespeichert werden, nimmt das Feld standardmäßig den Namen des ausgewählten Felds an, in diesem Beispiel also „Nachname“. Sie können diesen Titel wie unten gezeigt ändern:

  ![](assets/s_ncs_admin_survey_change_label.png)

  Erstellen Sie nun ein Eingabefeld für die Kundenummer. Wiederholen Sie den Vorgang und wählen Sie das Feld „Kundennummer“ aus.

  Wiederholen Sie dieselben Schritte, um ein Feld für die E-Mail-Adresse des Benutzers hinzuzufügen.

* **Frage erstellen**

  Um eine Frage zu erstellen, rechtsklicken Sie auf das letzte Element im Baum und wählen Sie **[!UICONTROL Container > Frage]** aus oder klicken Sie auf das Symbol **[!UICONTROL Container]** und wählen Sie danach **[!UICONTROL Frage]** aus.

  ![](assets/s_ncs_admin_survey_add_qu.png)

  Geben Sie den Titel der Frage ein und fügen Sie die Antwortfelder als Unterverzweigung der Frage ein. Beim Erstellen des Antwortfeldes muss der mit der Frage verknüpfte Knoten ausgewählt sein. Fügen Sie eine **[!UICONTROL Dropdown-Liste]** mithilfe des Symbols **[!UICONTROL Auswahldialog]** oder durch Rechtsklicken wie unten gezeigt hinzu:

  ![](assets/s_ncs_admin_survey_add_list.png)

  Wählen Sie einen Speicherort aus: Wählen Sie ein Aufzählungsfeld aus, um die Werte automatisch abzurufen (in diesem Fall das E-Mail-Format).

  ![](assets/s_ncs_admin_survey_add_itz_list.png)

  Wählen Sie im Tab **[!UICONTROL Allgemein]** den Link **[!UICONTROL Werteliste aus der Datenbank übernehmen]** aus. Die Wertetabelle wird daraufhin automatisch eingetragen.

  ![](assets/s_ncs_admin_survey_add_value.png)

  Wählen Sie **[!UICONTROL OK]** aus, um den Editor zu schließen, und **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

  >[!NOTE]
  >
  >Mit den Optionen im Tab **[!UICONTROL Erweitert]** können Sie für jedes Feld oder jede Frage das Seitenlayout nach Bedarf anpassen. Das Layout der Umfragefenster wird in [diesem Abschnitt](../../web/using/about-web-forms.md) näher beschrieben.

  Wählen Sie im Detailfenster den Tab **[!UICONTROL Vorschau]** aus, um sich die Darstellung der soeben erstellten Umfrage anzusehen.

  ![](assets/s_ncs_admin_survey_preview.png)

## Schritt 5: Speichern der Umfragedaten {#step-5---storing-the-survey-data-}

Mit dem Speicherfeld können Sie Benutzerantworten in der Datenbank speichern. Sie müssen einen Abstimmschlüssel auswählen, um die bereits in der Datenbank vorhandenen Profile zu identifizieren.

Bearbeiten Sie dazu die Box und wählen Sie das Feld aus, das bei der Datenspeicherung als Abstimmschlüssel verwendet wird.

Im nachfolgenden Beispiel wird das Profil aktualisiert, wenn beim Speichern (Bestätigen) ein Profil in der Datenbank gespeichert wird, dessen Kontonummer der Eingabe im Formular entspricht. Wenn das Profil nicht vorhanden ist, wird es erstellt.

![](assets/s_ncs_admin_survey_save_edit.png)

Wählen Sie zum Bestätigen **[!UICONTROL OK]** und danach **[!UICONTROL Speichern]** aus, um die Umfrage zu speichern.

## Schritt 6: Veröffentlichen der Seiten {#step-6---publishing-the-pages}

Damit Benutzende auf die HTML-Seiten zugreifen können, muss die Anwendung verfügbar gemacht werden. Sie darf sich nicht mehr in der Bearbeitungsphase befinden, sondern muss in der Produktion bereitstehen. Um eine Umfrage in die Produktion zu übernehmen, müssen Sie sie veröffentlichen. Gehen Sie dazu wie folgt vor:

* Klicken Sie auf die Schaltfläche **[!UICONTROL Veröffentlichen]** oberhalb des Umfrage-Dashboards.
* Klicken Sie auf **[!UICONTROL Start]**, um die Veröffentlichung zu starten und den Assistenten zu schließen.

  ![](assets/s_ncs_admin_survey_start_publ.png)

  Der Status der Umfrage wechselt zu: **Online**.

  ![](assets/survey_published.png)

## Schritt 7: Freigeben Ihrer Online-Umfrage {#step-7---sharing-your-online-survey}

Sobald eine Umfrage in der Produktion veröffentlicht wurde, kann sie am Server aufgerufen und von Ihnen bereitgestellt werden. Die URL für den Zugriff auf die Umfrage wird im Dashboard angezeigt.

![](assets/survey_url_from_dashboard.png)

Um die Umfrage bereitzustellen, können Sie beispielsweise eine Nachricht mit einem Zugangslink an die Zielpopulation senden oder die Zugriffs-URL auf eine Webseite stellen.

Sie können die Antworten der Benutzer dann mit Berichten und Logs überwachen. Siehe [Antworten tracken](../../surveys/using/publish-track-and-use-collected-data.md#response-tracking).

>[!CAUTION]
>
>Die öffentliche URL enthält den internen Namen der Umfrage. Wenn dieser geändert wird, wird die URL automatisch aktualisiert und alle Links zur Umfrage müssen ebenfalls aktualisiert werden.
>
>Wenn Nachrichten mit dem Link zur Umfrage bereits versendet wurden, funktioniert dieser Link nicht mehr.

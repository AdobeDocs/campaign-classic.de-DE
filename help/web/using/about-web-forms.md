---
title: Über Webformulare
seo-title: Über Webformulare
description: Über Webformulare
seo-description: null
page-status-flag: never-activated
uuid: 1d129af4-008b-4f6a-9094-b2edd6c1eee1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 3b8e4691-fcbc-48ef-b529-11c9a9a9d788
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Über Webformulare{#about-web-forms}

Adobe Campaign verfügt über ein grafisches Modul zur Definition und Publikation von Webformularen. Damit können Sie Seiten erstellen, die Eingabe- und Auswahlfelder sowie Daten aus der Datenbank enthalten. Daraus lassen sich wiederum Webseiten zusammenstellen und veröffentlichen, in denen Benutzer Informationen anzeigen oder eingeben können.

In diesem Kapitel erfahren Sie, wie Webformulare erstellt und verwaltet werden, wie Felder und Seiten verwaltet werden und wie der Speichermodus funktioniert.

>[!CAUTION]
>
>Aus Datenschutzgründen empfehlen wir die Verwendung von HTTPS für alle externen Ressourcen.

## Schritte zur Erstellung eines Webformulars {#steps-for-creating-a-web-form}

In diesem Abschnitt werden die Schritte zur Erstellung eines Formulars vom Typ **webForm** in Adobe Campaign sowie die verfügbaren Optionen und Konfigurationen beschrieben. Mit Adobe Campaign können Sie dieses Webformular Benutzern zur Verfügung stellen sowie Antworten erfassen und in der Datenbank archivieren.

>[!CAUTION]
>
>Zur Konfiguration von Webanwendungen und Webformularen benötigen Sie eine vertikale Auflösung von mindestens 900 Pixel (z. B.: 1.600 x 900).

Der Zugriff auf Webformulare erfolgt über das Menü &quot;Webanwendungen&quot;auf der Registerkarte &quot; **Kampagnen** &quot;. In der Adobe Campaign-Struktur werden sie unter dem **[!UICONTROL Resources > Online > Web Applications]** Knoten gruppiert.

To create a Web form, click the **[!UICONTROL Create]** button above the list of Web applications.

![](assets/webapp_create_new.png)

Wählen Sie die Webformularvorlage aus (standardmäßig **[!UICONTROL newWebForm]**).

![](assets/s_ncs_admin_survey_select_template.png)

Damit gelangen Sie zum Dashboard des Formulars.

![](assets/webapp_empty_dashboard.png)

The **[!UICONTROL Edit]** tab lets you create your content.

![](assets/webapp_edit_tab.png)

Um das Webformular zu definieren und zu konfigurieren, gehen Sie folgendermaßen vor:

* Erstellen Sie zunächst die erforderlichen Seiten und Steuerelemente: Eingabefelder, Dropdown-Listen, HTML-Inhalte etc.

   Dieser Schritt wird weiter unten genauer beschrieben.

* Definieren Sie die Seitenreihenfolge und legen Sie für die Anzeige der Seiten Bedingungen fest.

   Dieser Schritt wird unter [Definieren der Seitensequenz](../../web/using/defining-web-forms-page-sequencing.md)von Webformularen ausführlich beschrieben.

* Übersetzen Sie den Inhalt bei Bedarf.

   Dieser Schritt wird unter [Übersetzen eines Webformulars](../../web/using/translating-a-web-form.md)beschrieben.

## Über die Erstellung von Webformularen {#about-web-forms-designing}

Die Seiten des Formulars werden mit einem bestimmten Editor erstellt, mit dem Sie Eingabebereiche (Text), Auswahlfelder (Listen, Kontrollkästchen usw.) und statische Elemente (Bilder, HTML-Inhalte usw.) definieren und konfigurieren können. Sie können in Behälter gruppiert und ihr Layout an Ihre Anforderungen angepasst werden (weitere Informationen finden Sie unter Container [erstellen](../../web/using/defining-web-forms-layout.md#creating-containers)).

In den folgenden Abschnitten wird beschrieben, wie Sie den Inhalt und das Layout von Formularen definieren.

* [Felder zu einem Webformular hinzufügen](../../web/using/adding-fields-to-a-web-form.md),
* [HTML-Inhalt einfügen](../../web/using/static-elements-in-a-web-form.md#inserting-html-content),
* [Statische Elemente in einem Webformular](../../web/using/static-elements-in-a-web-form.md),
* [Layout eines Webformulars definieren](../../web/using/defining-web-forms-layout.md).

>[!NOTE]
>
>* Während des Seitenentwurfs können Sie die endgültige Wiedergabe auf der **[!UICONTROL Preview]** Registerkarte anzeigen. Um Änderungen anzuzeigen, speichern Sie das Formular zuerst. Alle Fehler werden auf der **[!UICONTROL Log]** Registerkarte angezeigt.
>* Um sicherzustellen, dass die Seitenanzeige und die Informationsspeicherung in der gewünschten Reihenfolge erfolgen, aktivieren Sie den Debug-Modus im Webformular. Gehen Sie dazu zur **[!UICONTROL Preview]** Unterregisterkarte und aktivieren Sie das **[!UICONTROL Enable debug mode]** Kontrollkästchen: Alle erfassten Informationen und mögliche Ausführungsfehler werden am Ende jeder Seite angezeigt.
>



### Symbole der Symbolleiste verwenden {#using-the-icons-in-the-toolbar}

Sie können ein Eingabefeld auch mithilfe der Symbole in der Symbolleiste oder eines Rechtsklicks einfügen.

![](assets/s_ncs_admin_webform_add_selection.png)

Wählen Sie in diesem Fall den Typ des hinzuzufügenden Feldes und den Antwort-Speichermodus aus.

![](assets/s_ncs_admin_webform_select_storage.png)

Klicken Sie auf **[!UICONTROL Ok]**, um die Auswahl zu bestätigen.

![](assets/s_ncs_admin_webform_confirm_storage.png)


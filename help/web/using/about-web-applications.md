---
product: campaign
title: Erste Schritte mit Web-Anwendungen
description: Erstellen und teilen Sie dynamische Web-Anwendungen, Landingpages und Umfragen
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Landing Pages, Web Apps
exl-id: df58221f-f71b-49d5-a6a1-c81ddff27fdb
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 100%

---

# Erste Schritte mit Web-Anwendungen{#about-web-applications}



Adobe Campaign ermöglicht Ihnen, mit Daten aus der Datenbank dynamische und interaktive Webanwendungen zu erstellen und zu veröffentlichen, wobei die Inhalte auf die jeweiligen Benutzerrechte abgestimmt sind.

Sie können Seiten erstellen (z. B. ein Bearbeitungsformular in einem Extranet oder Benachrichtigungsformulare, die Daten aus der Datenbank mit Tabellen, Diagrammen, Formularen usw. beinhalten). Mit dieser Funktion können Sie Webseiten entwerfen und posten, auf denen Benutzer Daten suchen oder eingeben können.

Dabei kann es sich um ein Anmeldeformular handeln, dessen Felder wie unten dargestellt mit Daten aus der Adobe Campaign-Datenbank vorausgefüllt wurden:

![](assets/webapp_form_sample.png)

Dieses Kapitel bietet einen Überblick über die Verwaltung von Webanwendungen.

>[!NOTE]
>
>Informationen zur Optimierung der Sicherheit von Webanwendungen finden Sie in der [Checkliste für Sicherheit und Datenschutz](https://helpx.adobe.com/de/campaign/kb/acc-security.html).

>[!CAUTION]
>
>Aus Datenschutzgründen empfehlen wir die Verwendung von HTTPS für alle externen Ressourcen.

## Web-Anwendungsbereich {#web-application-scope}

Web-Anwendungen in Adobe Campaign bieten folgende Funktionen:

* Erstellung eines Formulars mit mehreren Seiten. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](about-web-forms.md).
* Mehrsprachige Umfrageverwaltung mit einem integrierten Übersetzungs-Tool. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](translating-a-web-application.md).
* Grafische Benutzeroberfläche zur Seitenverwaltung, mehrspaltiges Seiten-Layout. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](designing-a-web-application.md).
* Personalisierte Darstellung und Feldposition. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](editing-content.md#adding-personalization-content).
* Anzeige von Umfragefeldern entsprechend den Antworten. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](form-rendering.md#defining-fields-conditional-display).
* Zufällige Anzeige von Fragen. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../surveys/using/building-a-survey.md#adding-questions).
* Bedingte Anzeige von Seiten. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](defining-web-forms-page-sequencing.md#conditional-page-display).
* Informationsüberprüfung vor der Validierung abhängig vom erwarteten Datentyp (Zahl, E-Mail-Adresse, Datum etc.) und von den Pflichtfeldern. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](form-rendering.md#defining-control-settings).
* Einladungen oder Benachrichtigungen per E-Mail. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](publishing-a-web-form.md#delivering-a-form-via-email).
* Personalisierung von Fehler- und Beendigungsnachrichten. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](defining-web-forms-properties.md#setting-up-an-error-page).
* Verwendung von Bildern, Videos, Hypertext-Links, Captcha etc. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](editing-content.md).
* Überwachung der Antworten in Echtzeit Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../surveys/using/publish-track-and-use-collected-data.md#response-tracking).

Das optionale Modul zur Umfrageerstellung (**Umfrage**) bietet die folgenden zusätzlichen Funktionen:

* Dynamische Erweiterung der Datenbank: Erstellung von Antworten, die nicht in der ursprünglichen Datenvorlage enthalten sind. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../surveys/using/managing-answers.md#storing-collected-answers).
* Erstellung spezieller Berichte Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../surveys/using/publish-track-and-use-collected-data.md#reports-on-surveys).

Gegenüber Webanwendungen verfügen Umfragen über eine vereinfachte grafische Benutzeroberfläche mit weniger Steuerelementen zur Bearbeitung.

>[!NOTE]
>
>Weitere Informationen zu Umfragen finden Sie in [diesem Abschnitt](../../surveys/using/about-surveys.md).
>
>Die allgemeinen Funktionen von Webformularen in Adobe Campaign werden in [diesem Abschnitt](about-web-forms.md) beschrieben.

## Implementierung von Web-Anwendungen {#web-application-implementation}

Gehen Sie wie folgt vor, um eine Webanwendung zu erstellen und zu veröffentlichen:

1. Erstellen Sie den Inhalt (Felder, Listen, Tabellen, Diagramme etc.).

   Sehen Sie sich dazu auch den Abschnitt zu den Feldern an, die für Formulare zur Verfügung stehen. Alle diese Felder sind auch für Web-Anwendungen verfügbar. Diese Informationen finden Sie auf [dieser Seite](adding-fields-to-a-web-form.md).

1. Sie können nach Bedarf die Schritte zum Vorausfüllen, Testen und Speichern hinzufügen und das Zugriffskontrollsystem konfigurieren (hauptsächlich für Extranet-Veröffentlichungen).
1. Veröffentlichen Sie die Webanwendung, um sie im Extranet oder in Adobe Campaign verfügbar zu machen.

## Erstkonfiguration von Web-Anwendungen {#web-application-initial-configuration}

Die Erstellung von Webanwendungen erfolgt über den Link **[!UICONTROL Webanwendungen]** in den Tabs **[!UICONTROL Kampagnen]** und **[!UICONTROL Profile und Zielgruppen]**.

Gespeichert werden Webanwendungen im Knoten **[!UICONTROL Ressourcen > Online > Webanwendungen]** des Adobe Campaign-Baums. Konfigurationen befinden sich in folgenden Ordnern:

* **[!UICONTROL Administration > Konfiguration > Formular-Rendering]**: enthält die Rendering-Vorlagen für Webformulare (Anwendungen und Umfragen). Die Vorlage ermöglicht die Generierung eines Formulars. Zusätzlich wird ein CSS-Stylesheet verwendet, das auf Vorlagenebene überschrieben werden kann. Weitere Informationen hierzu finden Sie auf [dieser Seite](form-rendering.md#selecting-the-form-rendering-template).
* **[!UICONTROL Ressourcen > Vorlagen > Webanwendungsvorlagen]**: enthält Formularvorlagen. Diese sind zur Erstellung eines Formulars oder einer Webanwendung erforderlich.

## Web-Anwendungsvorlagen {#web-application-templates}

Standardmäßig bietet Adobe Campaign für jede verfügbare Webanwendung eine Vorlage.

>[!NOTE]
>
>Sie können eine vorhandene Web-Anwendung in eine Vorlage konvertieren. Wählen Sie dazu das Formular aus und klicken Sie mit der rechten Maustaste darauf. Wählen Sie **[!UICONTROL Aktionen > Als Vorlage speichern…]** aus.

Neue Vorlagen werden im Adobe Campaign-Baum im Knoten **[!UICONTROL Ressourcen > Vorlagen > Webanwendungsvorlagen]** erstellt.

Im Erstellungsassistenten können Sie wie unten dargestellt die zu aktivierenden Optionen auswählen.

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>Die verfügbaren Anwendungen hängen von Ihren Optionen und Modulen ab. Nähere Informationen dazu entnehmen Sie bitte Ihrem Lizenzvertrag.

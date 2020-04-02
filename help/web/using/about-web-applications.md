---
title: Über Webanwendungen
seo-title: Über Webanwendungen
description: Über Webanwendungen
seo-description: null
page-status-flag: never-activated
uuid: acfa6e5e-b503-4a1a-871e-e70007874f57
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 3af763ad-6b0d-4f4c-aed1-c5e12efd4760
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 61c7681535dc08e1d705d7d239e96c603bbad339

---


# Über Webanwendungen{#about-web-applications}

Adobe Campaign ermöglicht Ihnen, mit Daten aus der Datenbank dynamische und interaktive Webanwendungen zu erstellen und zu publizieren, wobei die Inhalte auf die jeweiligen Benutzerrechte abgestimmt sind. Damit lassen sich Seiten erstellen, wie etwa Bearbeitungsformulare für das Extranet oder Benachrichtigungsformulare, die Daten aus der Datenbank in Form von Tabellen, Grafiken und Eingabeformularen enthalten. Mit der Webanwendungs-Funktion können Webseiten konzipiert und veröffentlicht werden, in denen Benutzer Informationen suchen oder eingeben können.

Dabei kann es sich um ein Anmeldeformular handeln, dessen Felder wie unten dargestellt mit Daten aus der Adobe Campaign-Datenbank vorausgefüllt wurden:

![](assets/webapp_form_sample.png)

Dieses Kapitel bietet einen Überblick über die Verwaltung von Webanwendungen.

>[!CAUTION]
>
>Aus Datenschutzgründen empfehlen wir die Verwendung von HTTPS für alle externen Ressourcen.

## Webanwendungsbereich {#web-application-scope}

Webanwendungen in Adobe Campaign bieten folgende Funktionen:

* Mehrseitige Formularerstellung. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../web/using/about-web-forms.md).
* Mehrsprachiges Umfragen-Management mit einem integrierten Übersetzungstool. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../web/using/translating-a-web-application.md).
* Grafische Seitenverwaltungs-Oberfläche, mehrspaltiges Seitenlayout. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../web/using/designing-a-web-application.md).
* Rendern von Personalisierung und Feldposition. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../web/using/editing-content.md#adding-personalization-content).
* Bedingte Anzeige von Umfragen-Feldern entsprechend den Antworten. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../web/using/form-rendering.md#defining-fields-conditional-display).
* Zufällige Anzeige von Fragen. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../web/using/building-a-survey.md#adding-questions).
* Bedingte Anzeige von Seiten. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display).
* Vor der Überprüfung prüfen Sie die Informationen je nach Datentyp (Nummer, E-Mail-Adresse, Datum usw.) und den erforderlichen Feldern. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../web/using/form-rendering.md#defining-control-settings).
* E-Mail-Einladungen oder -Benachrichtigungen. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../web/using/publishing-a-web-form.md#delivering-a-form-via-email).
* Personalisierung von Fehler- und Endmeldungen. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../web/using/defining-web-forms-properties.md#setting-up-an-error-page).
* Verwendung von Bildern, Videos, Hypertext-Links, Captcha etc. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../web/using/editing-content.md).
* Überwachung der Antworten in Echtzeit Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../web/using/publish--track-and-use-collected-data.md#response-tracking).

Das optionale Modul zur Umfrageerstellung (**Umfrage**) bietet die folgenden zusätzlichen Funktionen:

* Dynamische Erweiterung der Datenbank: Erstellung von Antworten, die nicht in der ursprünglichen Datenvorlage enthalten sind. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../web/using/managing-answers.md#storing-collected-answers).
* Erstellung spezieller Berichte Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../web/using/publish--track-and-use-collected-data.md#reports-on-surveys).

Gegenüber Webanwendungen verfügen Umfragen über eine vereinfachte grafische Benutzeroberfläche mit weniger Steuerelementen zur Bearbeitung.

>[!NOTE]
>
>Weitere Informationen zu Umfragen finden Sie in [diesem Abschnitt](../../web/using/about-surveys.md).
>
>Die allgemeinen Funktionen von Webformularen in Adobe Campaign werden in [diesem Abschnitt](../../web/using/about-web-forms.md) beschrieben.

## Implementierung von Webanwendungen {#web-application-implementation}

Gehen Sie wie folgt vor, um eine Webanwendung zu erstellen und zu veröffentlichen:

1. Erstellen Sie den Inhalt (Felder, Listen, Tabellen, Diagramme etc.).

   Sehen Sie sich dazu auch den Abschnitt zu den Feldern an, die für Formulare zur Verfügung stehen. Alle diese Felder sind auch für Webanwendungen verfügbar. Diese Informationen finden Sie auf [dieser Seite](../../web/using/adding-fields-to-a-web-form.md).

1. Sie können nach Bedarf die Schritte zum Vorausfüllen, Testen und Speichern hinzufügen und das Zugriffskontrollsystem konfigurieren (hauptsächlich für Extranet-Publikationen).
1. Publizieren Sie die Webanwendung, um sie im Extranet oder in Adobe Campaign verfügbar zu machen.

## Erstkonfiguration von Webanwendungen {#web-application-initial-configuration}

Webanwendung werden über den **[!UICONTROL Web Applications]** Link in den Registerkarten **[!UICONTROL Campaigns]** und **[!UICONTROL Profiles and targets]** erstellt.

Webanwendungen werden im **[!UICONTROL Resources > Online > Web Applications]** Knoten der Adobe Campaign-Struktur gespeichert. Konfigurationen werden in die folgenden Ordner unterteilt:

* **[!UICONTROL Administration > Configuration > Form renderings]**: enthält die Rendervorlagen für die Webformulardarstellung (Anwendungen und Umfragen). Mit der Vorlage können Sie das Formular erstellen. Es wird auch ein CSS-Stylesheet verwendet. Dieses Stylesheet kann auf Vorlagenebene überladen werden. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../web/using/form-rendering.md#selecting-the-form-rendering-template).
* **[!UICONTROL Resources > Templates > Web application templates]**: enthält Formularvorlagen. Um ein Formular oder ein Webanwendung zu erstellen, müssen Sie einen Beginn aus einer Vorlage erstellen.

## Webanwendungsvorlagen {#web-application-templates}

Standardmäßig bietet Adobe Campaign für jede verfügbare Webanwendung eine Vorlage.

>[!NOTE]
>
>You can convert an existing Web application into a template. To do this, select the form and right-click. Select **[!UICONTROL Actions > Save as template...]**.

Sie können neue Vorlagen über den **[!UICONTROL Resources > Templates > Web Application templates]** Knoten der Adobe Campaign-Struktur erstellen.

Im Erstellungsassistenten können Sie wie unten dargestellt die zu aktivierenden Optionen auswählen.

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>Die verfügbaren Anwendungen hängen von Ihren Optionen und Modulen ab. Nähere Informationen dazu entnehmen Sie bitte Ihrem Lizenzvertrag.


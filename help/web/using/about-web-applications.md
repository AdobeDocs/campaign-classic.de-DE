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
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# Über Webanwendungen{#about-web-applications}

Adobe Campaign ermöglicht Ihnen, mit Daten aus der Datenbank dynamische und interaktive Webanwendungen zu erstellen und zu publizieren, wobei die Inhalte auf die jeweiligen Benutzerrechte abgestimmt sind. Damit lassen sich Seiten erstellen, wie etwa Bearbeitungsformulare für das Extranet oder Benachrichtigungsformulare, die Daten aus der Datenbank in Form von Tabellen, Grafiken und Eingabeformularen enthalten. Mit der Webanwendungs-Funktion können Webseiten konzipiert und veröffentlicht werden, in denen Benutzer Informationen suchen oder eingeben können.

Dabei kann es sich um ein Anmeldeformular handeln, dessen Felder wie unten dargestellt mit Daten aus der Adobe Campaign-Datenbank vorausgefüllt wurden:

![](assets/webapp_form_sample.png)

Dieses Kapitel bietet einen Überblick über die Verwaltung von Webanwendungen.

>[!CAUTION]
>
>Aus Datenschutzgründen empfehlen wir die Verwendung von HTTPS für alle externen Ressourcen.

## Anwendungsbereich {#web-application-scope}

Webanwendungen in Adobe Campaign bieten Zugriff auf die folgenden Funktionen:

* Erstellung eines Formulars mit mehreren Seiten
* Mehrsprachige Umfrageverwaltung mit einem integrierten Übersetzungstool
* Grafische Benutzeroberfläche zur Seitenverwaltung, mehrspaltiges Seitenlayout
* Personalisierte Darstellung und Feldposition
* Anzeige von Umfragefeldern entsprechend den Antworten
* Zufällige Anzeige von Fragen
* Definition von Bedingungen zur Anzeige von Seiten
* Informationsprüfung vor der Validierung abhängig vom erwarteten Datentyp (Zahl, E-Mail-Adresse, Datum etc.) und von den Pflichtfeldern
* Einladungen oder Benachrichtigungen per E-Mail
* Personalisierung von Fehler- und Beendigungsnachrichten
* Verwendung von Bildern, Videos, Hypertext-Links, Captcha etc.
* Überwachung der Antworten in Echtzeit

The optional **Survey** creation module offers the following additional functionalities:

* Dynamische Erweiterung der Datenbank: Erstellung von Antworten, die nicht in der ursprünglichen Datenvorlage enthalten sind
* Erstellung spezieller Berichte

Gegenüber Webanwendungen verfügen Umfragen über eine vereinfachte grafische Benutzeroberfläche mit weniger Steuerelementen zur Bearbeitung.

>[!NOTE]
>
>Weitere Informationen zu Umfragen finden Sie in [diesem Abschnitt](../../web/using/about-surveys.md).
>
>Die allgemeinen Funktionen von Webformularen in Adobe Campaign werden in [diesem Abschnitt](../../web/using/about-web-forms.md) beschrieben.

## Webanwendungs-Implementierung {#web-application-implementation}

Gehen Sie wie folgt vor, um eine Webanwendung zu erstellen und zu veröffentlichen:

1. Erstellen Sie den Inhalt (Felder, Listen, Tabellen, Diagramme etc.).

   Sehen Sie sich dazu auch den Abschnitt zu den Feldern an, die für Formulare zur Verfügung stehen. Alle diese Felder sind auch für Webanwendungen verfügbar. Diese Informationen finden Sie auf [dieser Seite](../../web/using/adding-fields-to-a-web-form.md).

1. Sie können nach Bedarf die Schritte zum Vorausfüllen, Testen und Speichern hinzufügen und das Zugriffskontrollsystem konfigurieren (hauptsächlich für Extranet-Publikationen).
1. Publizieren Sie die Webanwendung, um sie im Extranet oder in Adobe Campaign verfügbar zu machen.

## Erstkonfiguration der Webanwendung {#web-application-initial-configuration}

Webanwendungen werden über den **[!UICONTROL Web Applications]** Link in den Registerkarten **[!UICONTROL Campaigns]** und **[!UICONTROL Profiles and targets]** erstellt.

Webanwendungen werden im **[!UICONTROL Resources > Online > Web Applications]** Knoten der Adobe Campaign-Struktur gespeichert. Konfigurationen werden in die folgenden Ordner unterteilt:

* **[!UICONTROL Administration > Configuration > Form renderings]**: enthält die Rendervorlagen für die Webformulardarstellung (Anwendungen und Umfragen). Mit der Vorlage können Sie das Formular erstellen. Es wird auch ein CSS-Stylesheet verwendet. Dieses Stylesheet kann auf Vorlagenebene überladen werden. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../web/using/form-rendering.md#selecting-the-form-rendering-template).
* **[!UICONTROL Resources > Templates > Web application templates]**: enthält Formularvorlagen. Um ein Formular oder eine Webanwendung zu erstellen, müssen Sie mit einer Vorlage beginnen.

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


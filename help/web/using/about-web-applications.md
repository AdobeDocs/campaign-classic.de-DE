---
product: campaign
title: Erste Schritte mit Web-Anwendungen
description: Erstellen und teilen Sie dynamische Web-Anwendungen, Landingpages und Umfragen
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Landing Pages, Web Apps
exl-id: df58221f-f71b-49d5-a6a1-c81ddff27fdb
TQID: https://experienceleague.adobe.com/GP-1vCAYzcgjaOyUs-Zkx6rXOLSNbpF7962OEMsw5YM
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: a7760dfc-5c44-4d77-bb68-c50b1e265c93id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
subfeature_v2: id: ac9c0a9c-8a76-4419-bd64-9c34c5782666id: fb2a841f-c522-491f-9901-a1b939d252df
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d095671a-1355-40aa-8b5f-06c33c68080bid: e0eb8757-182f-49f3-94a4-1587d16f5094id: eddd9b14-83bd-4ff4-9072-54a4a484abb7id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 730
ht-degree: 73%

---

# Erste Schritte mit Web-Anwendungen{#about-web-applications}



Adobe Campaign ermöglicht Ihnen, mit Daten aus der Datenbank dynamische und interaktive Webanwendungen zu erstellen und zu veröffentlichen, wobei die Inhalte auf die jeweiligen Benutzerrechte abgestimmt sind.

Sie können Seiten erstellen, z. B. ein Bearbeitungsformular für ein Extranet oder Benachrichtigungsformulare, die Daten aus der Datenbank mit Tabellen, Diagrammen, Eingabeformularen usw. enthalten. Mit dieser Funktion können Sie Web-Seiten entwerfen und posten, auf denen Benutzer Informationen suchen oder eingeben können.

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
* Informationsüberprüfung vor der Validierung abhängig vom erwarteten Datentyp (Nummer, E-Mail-Adresse, Datum usw.) und die Pflichtfelder. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](form-rendering.md#defining-control-settings).
* Einladungen oder Benachrichtigungen per E-Mail. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](publishing-a-web-form.md#delivering-a-form-via-email).
* Personalisierung von Fehler- und Beendigungsnachrichten. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](defining-web-forms-properties.md#setting-up-an-error-page).
* Verwendung von Bildern, Videos, Hypertext-Links, CAPTCHA usw. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](editing-content.md).
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

Web-Anwendungen werden im Knoten **[!UICONTROL Ressourcen > Online > Web]** der Adobe Campaign-Baumstruktur gespeichert. Konfigurationen sind in die folgenden Ordner unterteilt:

* **[!UICONTROL Administration > Konfiguration > Formularwiedergaben]**: Enthält die Rendering-Vorlagen für die Web-Formularpräsentation (Programme und Umfragen). Mit der Vorlage können Sie das Formular generieren. Außerdem wird ein CSS-Stylesheet verwendet. Dieses Stylesheet kann auf Vorlagenebene überladen werden. Weitere Informationen hierzu finden Sie auf [dieser Seite](form-rendering.md#selecting-the-form-rendering-template).
* **[!UICONTROL Ressourcen > Vorlagen > Webanwendungsvorlagen]**: enthält Formularvorlagen. Um ein Formular oder eine Web-Anwendung zu erstellen, müssen Sie von einer Vorlage ausgehen.

## Web-Anwendungsvorlagen {#web-application-templates}

Standardmäßig bietet Adobe Campaign für jede verfügbare Webanwendung eine Vorlage.

>[!NOTE]
>
>Sie können eine vorhandene Webanwendung in eine Vorlage konvertieren. Wählen Sie dazu das Formular aus und klicken Sie mit der rechten Maustaste darauf. Wählen Sie **[!UICONTROL Aktionen > Als Vorlage speichern…]** aus.

Sie können neue Vorlagen über den Knoten **[!UICONTROL Ressourcen > Vorlagen > Web-Anwendungsvorlagen]** im Adobe Campaign-Baum erstellen.

Im Erstellungsassistenten können Sie wie unten dargestellt die zu aktivierenden Optionen auswählen.

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>Die verfügbaren Anwendungen hängen von Ihren Optionen und Modulen ab. Prüfen Sie diesbezüglich Ihren Lizenzvertrag.

---
title: Über Umfragen
seo-title: Über Umfragen
description: Über Umfragen
seo-description: null
page-status-flag: never-activated
uuid: 31a07a48-2ebb-4b51-ae24-382f3ce3f04a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: ef7d9b16-506a-409c-a578-000b88cd17a2
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 100%

---


# Über Umfragen{#about-surveys}

Adobe Campaign beinhaltet ein Grafikmodul zur Definition und Publikation von Webanwendungen. Damit können Seiten erstellt werden, wie etwa Bearbeitungsformulare für das Extranet oder Benachrichtigungsformulare mit Daten von der Datenbank mit Tabellen, Grafiken und Eingabeformularen. Mit dieser Funktion können Webseiten konzipiert und veröffentlicht werden, in denen Benutzer Informationen suchen oder eingeben können.

Mit dem optionalen **Umfragemodul** können Sie spezielle Webanwendungen erstellen. Beispielsweise können Sie damit Online-Umfragen mithilfe von Formularen erstellen und verwalten, Profilinformationen hinzufügen oder ändern oder eine An- und Abmeldemöglichkeit für Informationsdienste bereitstellen. Die erfassten Antworten werden in der Datenbank oder in lokalen Variablen gespeichert. Anhand der Antworten kann das Datenmodell dynamisch erweitert werden. Außerdem können Sie die Ergebnisse in Echtzeit einsehen, die Antworten filtern und mithilfe spezieller Grafiken analysieren.

Dieses Kapitel erläutert die Erstellung und Verwaltung von **Umfragen**, das Felder- und Seiten-Management sowie die unterschiedlichen Speichermodi und Datensätze.

Die einzelnen Schritte für die Erstellung eines Standard-Webformulars werden in [diesem Abschnitt](../../web/using/about-web-forms.md) beschrieben.

Weiterführende Informationen zur Verwaltung von Webanwendungen finden Sie in [diesem Abschnitt](../../web/using/about-web-applications.md).

>[!CAUTION]
>
>Aus Datenschutzgründen empfehlen wir die Verwendung von HTTPS für alle externen Ressourcen.

## Campaign-Umfragenbereich {#campaign-surveys-scope}

In Adobe Campaign stehen für Webanwendungen im Allgemeinen die folgenden Funktionen zur Verfügung:

* Erstellung eines Formulars mit mehreren Seiten
* Mehrsprachige Umfrageverwaltung mit einem integrierten Übersetzungstool
* Grafische Benutzeroberfläche zur Seitenverwaltung, mehrspaltiges Seitenlayout
* Personalisierte Darstellung und Feldposition
* Anzeige von Umfragefeldern entsprechend den Antworten
* Definition von Bedingungen zur Anzeige von Seiten
* Überprüfung von Informationen vor der Validierung abhängig vom erwarteten Datentyp (Zahl, E-Mail-Adresse, Datum etc.) sowie Pflichtfelder
* Einladungen/Benachrichtigungen per E-Mail
* Personalisierung von Fehler- und Beendigungsnachrichten
* Verwendung von Bildern, Videos, Hypertext-Links, Captcha etc.

>[!NOTE]
>
>Alle Konfigurationen für Webformulare werden in [diesem Abschnitt](../../web/using/about-web-forms.md) erläutert. Hier finden Sie auch Informationen zu Konzepten und Funktionen von Webformularen in Adobe Campaign.

Das optionale Modul zur Umfrageerstellung (**Umfrage**) bietet die folgenden zusätzlichen Funktionen:

* Dynamische Erweiterung der Datenbank: Erstellung von Antworten, die nicht Teil des anfänglichen Datenmodells sind. Weitere Informationen finden Sie unter [Erfasste Antworten speichern](../../web/using/managing-answers.md#storing-collected-answers).
* Verwaltung der Punktzahl. Weitere Informationen hierzu finden Sie im Abschnitt [Verwaltung der Punktzahl](../../web/using/managing-answers.md#score-management).
* Zufällige Anzeige von Fragen. Weitere Informationen hierzu finden Sie unter [Fragen hinzufügen ](../../web/using/building-a-survey.md#adding-questions).
* Echtzeit-Tracking von Antworten. Weitere Informationen hierzu finden Sie im Abschnitt [Antworten tracken](../../web/using/publish--track-and-use-collected-data.md#response-tracking).
* Erstellung spezieller Berichte Weitere Informationen hierzu finden Sie unter [Berichte zu Umfragen](../../web/using/publish--track-and-use-collected-data.md#reports-on-surveys).

Gegenüber Webanwendungen verfügen Umfragen über eine vereinfachte grafische Benutzeroberfläche mit weniger Steuerelementen zur Bearbeitung.

## Schritte zur Implementierung einer Umfrage {#surveys-implementation-steps}

Führen Sie die folgenden Schritte aus, um eine Umfrage zu erstellen und bereitzustellen und ihre Ergebnisse zu verarbeiten.

1. Erstellen Sie die Seiten der Umfrage und deren Inhalt (Eingabefelder, Dropdown-Listen, Fragen etc.).
1. Definieren Sie, wie die Antworten gespeichert werden sollen.

   Ein Zwischenschritt zum Vorausfüllen der Daten kann eingerichtet werden, damit das Formular mit Daten ausgefüllt wird, die sich bereits in der Datenbank befinden. Sie können auch eine Testbox hinzufügen.

1. Publizieren Sie die Umfrage und senden Sie sie dann an Empfänger (schließen Sie z. B. den Link in eine Sendung oder auf einer Website ein).
1. Überwachen Sie die Antworten und prüfen Sie die entsprechenden Berichte.

Weitere Informationen zum Konfigurieren und Sequenzieren dieser Schritte finden Sie in [diesem Abschnitt](../../web/using/about-web-forms.md). In dem Kapitel werden nur die für Umfragen spezifischen Konfigurationen beschrieben.

## Konfiguration von Umfragen {#surveys-configuration}

Die Speicherung von Umfragen erfolgt im Knoten **[!UICONTROL Ressourcen > Online > Webanwendungen]** des Adobe Campaign-Baums. Konfigurationen befinden sich in folgenden Ordnern:

* **[!UICONTROL Administration > Konfiguration > Formular-Rendering]**: enthält die Rendering-Vorlagen für Webformulare (Anwendungen und Umfragen).
* **[!UICONTROL Ressourcen > Vorlagen > Webanwendungsvorlagen]**: enthält die Formularvorlagen. Zur Erstellung eines Formulars benötigen Sie eine Vorlage.

>[!NOTE]
>
>Informationen zur Konfiguration finden Sie in [diesem Abschnitt](../../web/using/about-web-forms.md).


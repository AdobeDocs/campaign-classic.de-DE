---
product: campaign
title: Erste Schritte mit Umfragen
description: Erste Schritte mit Campaign-Umfragen
audience: web
content-type: reference
topic-tags: online-surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
source-git-commit: 86963746d3de3396963d221ddbd1ef7d89733d2f
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 37%

---

# Erste Schritte mit Umfragen{#about-surveys}

Adobe Campaign enthält ein Grafikmodul zur Definition und Veröffentlichung von Webanwendungen. Dies wird verwendet, um Seiten zu erstellen, z. B. ein Bearbeitungsformular für ein Extranet oder Benachrichtigungsformulare, einschließlich Daten aus der Datenbank mit Tabellen, Diagrammen, Formularen usw. Mit dieser Funktion können Sie Webseiten entwerfen und posten, auf denen Benutzer Informationen suchen oder eingeben können.

Mit dem optionalen Add-on **Umfrage** können Sie eine neue Art von Webanwendung erstellen, um Online-Fragebögen zu erstellen und zu verwalten, z. B. Formulare zum Hinzufügen oder Ändern von Profilinformationen, zum Abonnieren oder Abmelden von einem Informationsdienst oder einem Gewinnspielformular. Nachdem die Antworten erfasst wurden, werden sie in der Datenbank oder in lokalen Variablen gespeichert. Das Datenmodell kann mithilfe der Fragebogenantworten dynamisch erweitert werden. Sie können die Ergebnisse in Echtzeit anzeigen, die Antworten filtern und mithilfe spezieller Diagramme analysieren.

In diesem Kapitel wird beschrieben, wie Sie **Umfragen**, Feld- und Seitenverwaltung, Speichermodi und Datensätze erstellen und verwalten.

[!DNL :bulb:] Erfahren Sie auf  [dieser Seite](getting-started-with-surveys.md), wie Sie Ihre erste Umfrage erstellen.

>[!NOTE]
>
>* Ausführliche Anweisungen zum Erstellen eines Standard-Webformulars finden Sie in [diesem Dokument](../../web/using/about-web-forms.md).
   >
   >
* Die Verwaltung von Webanwendungen wird in [diesem Dokument](../../web/using/about-web-applications.md) beschrieben. Weitere Informationen finden Sie in diesem Kapitel.


## Funktionsumfang {#campaign-surveys-scope}

Verwenden Sie in Adobe Campaign [Webanwendungen](../../web/using/about-web-forms.md), um:

* Erstellen mehrseitiger Formulare,
* Verwaltung mehrsprachiger Formulare mit einem integrierten Übersetzungstool,
* grafische Benutzeroberfläche verwalten, mehrspaltiges Seitenlayout,
* Personalisierung hinzufügen und Feldposition definieren,
* Anzeige von Umfragefeldern entsprechend den Antworten,
* Anzeige von Bedingungsseiten,
* Prüfen Sie die Informationen vor der Genehmigung, je nach Datentyp (Anzahl, E-Mail-Adresse, Datum usw.). und Pflichtfelder,
* E-Mail-Einladungen/Benachrichtigungen senden,
* Fehler- und Endseiten personalisieren,
* Bilder, Videos, Hypertext-Links, Captcha usw. in Formularen hinzufügen

Das optionale Modul zur Umfrageerstellung bietet eine benutzerfreundliche Benutzeroberfläche und die folgenden zusätzlichen Funktionen:

* Dynamische Erweiterung der Datenbank: Erstellung von Antworten, die nicht Teil des anfänglichen Datenmodells sind. [Weitere Informationen](../../surveys/using/managing-answers.md#storing-collected-answers).
* Verwaltung der Punktzahl. [Weitere Informationen](../../surveys/using/managing-answers.md#score-management).
* Zufällige Anzeige von Fragen. [Weitere Informationen](../../surveys/using/building-a-survey.md#adding-questions).
* Echtzeit-Tracking von Antworten. [Weitere Informationen](../../surveys/using/publish--track-and-use-collected-data.md#response-tracking).
* Erstellung spezieller Berichte [Weitere Informationen](../../surveys/using/publish--track-and-use-collected-data.md#reports-on-surveys).


## Implementierungsschritte {#surveys-implementation-steps}

Führen Sie die folgenden Schritte aus, um eine Umfrage zu erstellen und bereitzustellen und ihre Ergebnisse zu verarbeiten.

1. Erstellen Sie die Seiten der Umfrage und deren Inhalt (Eingabefelder, Dropdown-Listen, Fragen etc.).
1. Definieren Sie, wie die Antworten gespeichert werden sollen. Ein Zwischenschritt zum Vorausfüllen der Daten kann eingerichtet werden, damit das Formular mit Daten ausgefüllt wird, die sich bereits in der Datenbank befinden. Sie können auch eine Testbox hinzufügen.
1. Veröffentlichen Sie die Umfrage und senden Sie sie dann an Empfänger (schließen Sie z. B. den Link in eine Sendung oder auf einer Website ein).
1. Überwachen Sie die Antworten und prüfen Sie die entsprechenden Berichte.

Weitere Informationen zum Konfigurieren und Sequenzieren dieser Schritte finden Sie in [diesem Dokument](../../web/using/about-web-forms.md). In dem Kapitel werden nur die für Umfragen spezifischen Konfigurationen beschrieben.

>[!CAUTION]
>
>Aus Datenschutzgründen empfehlen wir die Verwendung von HTTPS für alle externen Ressourcen.

## Einstellungen        {#settings}

Umfragen sind standardmäßig im Knoten **[!UICONTROL Ressourcen > Online > Webanwendungen]** des Adobe Campaign-Navigationsbaums verfügbar.

Einstellungen werden in den folgenden Ordnern gespeichert:

* **[!UICONTROL Administration > Konfiguration > Formular-Rendering]**: enthält die Rendering-Vorlagen für Webformulare (Anwendungen und Umfragen).
* **[!UICONTROL Ressourcen > Vorlagen > Webanwendungsvorlagen]**: enthält die Formularvorlagen. Zur Erstellung eines Formulars benötigen Sie eine Vorlage.

>[!NOTE]
>
>Einstellungsdetails finden Sie in [diesem Dokument](../../web/using/about-web-forms.md).

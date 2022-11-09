---
product: campaign
title: Erste Schritte mit Umfragen
description: Erste Schritte mit Campaign-Umfragen
feature: Surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
source-git-commit: 1f80c9967f4859f26dd2890d657f95ada6cf2087
workflow-type: ht
source-wordcount: '535'
ht-degree: 100%

---

# Erste Schritte mit Umfragen{#about-surveys}

![](../../assets/common.svg)

Adobe Campaign enthält ein Grafikmodul zur Definition und Veröffentlichung von Web-Anwendungen. Dies wird verwendet, um Seiten zu erstellen, z. B. ein Bearbeitungsformular für ein Extranet oder Benachrichtigungsformulare, einschließlich Daten aus der Datenbank mit Tabellen, Diagrammen, Formularen usw. Mit dieser Funktion können Sie Web-Seiten entwerfen und posten, auf denen Benutzer Informationen suchen oder eingeben können.

Mit dem optionalen **Umfrage**-Add-on können Sie eine neue Art von Web-Anwendung erstellen, um Online-Fragebögen zu erstellen und zu verwalten, z. B. Formulare zum Hinzufügen oder Ändern von Profilinformationen, zum Abonnieren oder Abmelden von einem Informations-Service oder Teilnahmeformular für einen Wettbewerb. Nachdem die Antworten erfasst wurden, werden sie in der Datenbank oder in lokalen Variablen gespeichert. Das Datenmodell kann mithilfe der Fragebogenantworten dynamisch erweitert werden. Sie können die Ergebnisse in Echtzeit anzeigen, die Antworten filtern und mithilfe spezieller Diagramme analysieren.

In diesem Kapitel wird beschrieben, wie Sie **Umfragen**, Feld- und Seitenverwaltung, Speichermodi und Einträge erstellen und verwalten.

Auf [dieser Seite](getting-started-with-surveys.md) erfahren Sie, wie Sie Ihre erste Umfrage erstellen.

>[!NOTE]
>
>* Die einzelnen Schritte für die Erstellung eines Standard-Web-Formulars werden in [diesem Dokument](../../web/using/about-web-forms.md) beschrieben.
>
>* Die Verwaltung von Web-Anwendungen wird in [diesem Dokument](../../web/using/about-web-applications.md) beschrieben. Weitere Informationen finden Sie in diesem Kapitel.


## Funktionsumfang {#campaign-surveys-scope}

Verwenden Sie in Adobe Campaign [Web-Anwendungen](../../web/using/about-web-forms.md), um:

* mehrseitige Formulare zu erstellen,
* mehrsprachige Formulare mit einem integrierten Übersetzungs-Tool zu verwalten,
* grafische Benutzeroberflächen und ein mehrspaltiges Seiten-Layout zu verwalten,
* Personalisierung hinzuzufügen und die Feldposition zu definieren,
* die Anzeige von Umfragefeldern von den Antworten abhängig zu machen,
* die Anzeige von Seiten abhängig von einer Bedingung zu machen,
* Informationen vor der Genehmigung zu prüfen, je nach Art der erwarteten Daten (Nummer, E-Mail-Adresse, Daten usw.) Pflichtfelder hinzuzufügen,
* E-Mail-Einladungen/Benachrichtigungen zu senden,
* Fehler- und Endseiten zu personalisieren,
* Bilder, Videos, Hypertext-Links, Captcha usw. in Formularen hinzuzufügen.

Das optionale Modul zur Umfrageerstellung bietet eine anwenderfreundliche Benutzeroberfläche und die folgenden zusätzlichen Funktionen:

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

Weitere Informationen zum Konfigurieren und Festlegen der Abfolge dieser Schritte finden Sie in [diesem Dokument](../../web/using/about-web-forms.md). In dem Kapitel werden nur die für Umfragen spezifischen Konfigurationen beschrieben.

>[!CAUTION]
>
>Aus Datenschutzgründen empfehlen wir die Verwendung von HTTPS für alle externen Ressourcen.

## Einstellungen        {#settings}

Umfragen sind standardmäßig im Knoten **[!UICONTROL Ressourcen > Online > Web-Anwendungen]** der Adobe Campaign-Baumstruktur verfügbar.

Einstellungen werden in den folgenden Ordnern gespeichert:

* **[!UICONTROL Administration > Konfiguration > Formular-Rendering]**: enthält die Rendering-Vorlagen für Webformulare (Anwendungen und Umfragen).
* **[!UICONTROL Ressourcen > Vorlagen > Webanwendungsvorlagen]**: enthält die Formularvorlagen. Zur Erstellung eines Formulars benötigen Sie eine Vorlage.

>[!NOTE]
>
>Details zu Einstellungen finden Sie in [diesem Dokument](../../web/using/about-web-forms.md).

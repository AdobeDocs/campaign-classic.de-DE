---
product: campaign
title: Erste Schritte mit Umfragen
description: Erste Schritte mit Campaign-Umfragen
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
TQID: https://experienceleague.adobe.com/VU7basdMR9txUIDVWMgoun9mMhAYlpqq2Uc57qtebo0
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: e0eb8757-182f-49f3-94a4-1587d16f5094id: eddd9b14-83bd-4ff4-9072-54a4a484abb7id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 585
ht-degree: 78%

---

# Erste Schritte mit Umfragen{#about-surveys}

Adobe Campaign enthält ein Grafikmodul zum Definieren und Veröffentlichen von Web-Anwendungen. Damit werden Seiten erstellt, z. B. ein Bearbeitungsformular für ein Extranet oder Benachrichtigungsformulare, die Daten aus der Datenbank mit Tabellen, Diagrammen, Eingabeformularen usw. enthalten. Verwenden Sie diese Funktion, um Web-Seiten zu entwerfen und zu posten, auf denen Benutzer Informationen suchen oder eingeben können.

>[!AVAILABILITY]
>
>Die Umfrageverwaltung ist in Campaign v8 nicht im Kontext einer Enterprise-Bereitstellung (FFDA) verfügbar. Weitere Informationen finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/config/architecture/ffda/enterprise-deployment){target="_blank"}.


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
* Informationen vor der Genehmigung prüfen, je nach Art der erwarteten Daten (Nummer, E-Mail-Adresse, Daten usw.) und Pflichtfelder,
* E-Mail-Einladungen/Benachrichtigungen zu senden,
* Fehler- und Endseiten zu personalisieren,
* Bilder, Videos, Hypertext-Links, Captcha usw. in Formularen hinzuzufügen.

Das optionale Modul zur Umfrageerstellung bietet eine anwenderfreundliche Benutzeroberfläche und die folgenden zusätzlichen Funktionen:

* Dynamische Erweiterung der Datenbank: Erstellung von Antworten, die nicht Teil des anfänglichen Datenmodells sind. [Weitere Informationen](../../surveys/using/managing-answers.md#storing-collected-answers).
* Verwaltung der Punktzahl. [Weitere Informationen](../../surveys/using/managing-answers.md#score-management).
* Zufällige Anzeige von Fragen. [Weitere Informationen](../../surveys/using/building-a-survey.md#adding-questions).
* Echtzeit-Tracking von Antworten. [Weitere Informationen](../../surveys/using/publish-track-and-use-collected-data.md#response-tracking).
* Erstellung spezieller Berichte [Weitere Informationen](../../surveys/using/publish-track-and-use-collected-data.md#reports-on-surveys).


## Implementierungsschritte {#surveys-implementation-steps}

Führen Sie die folgenden Schritte aus, um eine Umfrage zu erstellen und bereitzustellen und ihre Ergebnisse zu verarbeiten.

1. Erstellen Sie die Seiten der Umfrage und deren Inhalt (Eingabefelder, Dropdown-Listen, Fragen etc.).
1. Definieren Sie, wie die Antworten gespeichert werden sollen. Es kann ein Schritt zum Vorabladen von Daten eingefügt werden, um das Formular mit Daten vorab zu laden, die sich bereits in der Datenbank befinden. Sie können auch ein Testfeld hinzufügen.
1. Veröffentlichen Sie die Umfrage und senden Sie sie dann an Empfänger (schließen Sie z. B. den Link in eine Sendung oder auf einer Website ein).
1. Überwachen Sie die Antworten und prüfen Sie die entsprechenden Berichte.

Weitere Informationen zum Konfigurieren und Festlegen der Abfolge dieser Schritte finden Sie in [diesem Dokument](../../web/using/about-web-forms.md). In dem Kapitel werden nur die für Umfragen spezifischen Konfigurationen beschrieben.

>[!CAUTION]
>
>Aus Datenschutzgründen empfehlen wir die Verwendung von HTTPS für alle externen Ressourcen.

## Einstellungen {#settings}

Umfragen sind standardmäßig im Knoten **[!UICONTROL Ressourcen > Online > Web-Anwendungen]** der Adobe Campaign-Baumstruktur verfügbar.

Einstellungen werden in den folgenden Ordnern gespeichert:

* **[!UICONTROL Administration > Konfiguration > Formular-Rendering]**: enthält die Rendering-Vorlagen für Webformulare (Anwendungen und Umfragen).
* **[!UICONTROL Ressourcen > Vorlagen > Webanwendungsvorlagen]**: enthält die Formularvorlagen. Um ein Formular zu erstellen, müssen Sie mit einer Vorlage beginnen.

>[!NOTE]
>
>Details zu Einstellungen finden Sie in [diesem Dokument](../../web/using/about-web-forms.md).

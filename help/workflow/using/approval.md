---
title: Validierung
seo-title: Validierung
description: Validierung
seo-description: null
page-status-flag: never-activated
uuid: 49285790-5aa7-4e15-a657-42e4f78be518
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: a0090c78-5873-446d-8d5f-b0f94ff5d373
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 100%

---


# Validierung{#approval}

Eine **Validierung** wartet auf ein Signal oder die Entscheidung eines Benutzers. Validierungsaufgaben werden Benutzern zugewiesen, die per E-Mail, Webzugriff oder in der Clientkonsole darauf antworten.

## Aufgabenzuweisung {#task-assignment}

Standardmäßig wird eine Validierung einer Benutzergruppe zugewiesen. Gruppen repräsentieren bestimmte Rollen, beispielsweise &#39;Verantwortliche Gruppe Newsletter-Inhalt&#39; oder &#39;Verantwortliche Gruppe Newsletter-Zielgruppe&#39;. Jeder Benutzer der Gruppe kann die Anfrage beantworten, aber nur die erste Antwort wird berücksichtigt (außer bei einer Mehrfach-Validierung).

Bei Bedarf kann die Validierung auch einem einzelnen oder durch die Verwendung von Filtern mehreren Benutzern zugewiesen werden.

* Zur Auswahl eines einzelnen Benutzers ist im Feld **[!UICONTROL Zuweisungstyp]** die Option **[!UICONTROL Benutzer]** zu wählen. Wählen Sie dann aus der Dropdown-Liste des Felds **[!UICONTROL Zuweisung]** den gewünschten Benutzer aus.

   ![](assets/s_advuser_validation_box_assign.png)

   >[!CAUTION]
   >
   >Nur der ausgewählte Benutzer verfügt über die Berechtigung zur Validierung der Aufgabe.

* Es besteht die Möglichkeit, eine Abfrage zu erstellen, um die zur Validierung berechtigten Benutzer zu filtern. Wählen Sie hierzu im Feld **[!UICONTROL Zuweisungstyp]** die Option **[!UICONTROL Filter]** und klicken Sie auf den Link **[!UICONTROL Erweiterte Parameter...]**, um die Filterkriterien zu definieren, wie in unten stehendem Beispiel dargestellt:

   ![](assets/s_advuser_validation_box_filter.png)

Im Fall einer einfachen Validierung, wird die der Wahl des Benutzers entsprechende Transition aktiviert und die Aufgabe abgeschlossen. Andere Benutzer können nun die Aufgabe nicht mehr validieren.

Im Fall einer Mehrfach-Validierung wird für jede vorgenommene Validierung die entsprechende Transaktion aktiviert. Die Aufgabe wird abgeschlossen, sobald alle Benutzer der Gruppe geantwortet haben, oder wenn die Aufgabe abgelaufen ist.

Diese Aktivität betrifft nicht den gesamten Workflow, andere Aufgaben können parallel ausgeführt werden.

Benutzer können die ihnen zugewiesenen Aufgaben in der Clientkonsole validieren. Administratoren können anderen Benutzern zugewiesene Aufgaben ansehen und löschen, sie jedoch nicht validieren.

Änderungen in Bezug auf die Titel oder den Nachrichten-Textkörper der Aktivität haben keinen Einfluss auf laufende Aufgaben. Sollten jedoch die möglichen Antworten geändert werden, werden die neuen Optionen automatisch in den laufenden Aufgaben übernommen.

Auf **Validierungsaufgaben** kann im Knoten **[!UICONTROL Administration > Betreibung > Automatisch erstellte Objekte > Ausstehende Validierungen]** zugegriffen werden. Aus dieser Ansicht heraus gelangen die Benutzer direkt in die verschiedenen Validierungsformulare.

![](assets/s_advuser_validation_from_console.png)

## Eigenschaften {#properties}

In den Benachrichtigungen, die an die für die Validierung ausgewählten Benutzer gesandt werden, können im Titel und im Nachrichten-Textkörper Personalisierungsvariablen verwendet werden.

![](assets/edit_validation.png)

Das **[!UICONTROL Titel]**-Feld entspricht dem Betreff der Benachrichtigungs-E-Mail. Sowohl beim Titel als auch beim Body handelt es sich um JavaScript-Templates, die somit vom Workflow-Kontext ausgehend berechnete Werte enthalten können.

Im unteren Bereich des Editors werden die möglichen Antworten definiert. Jeder Antwort entspricht eine aus der Aktivität ausgehende Transition. Der Name ist die interne Kennung und der Titel, der in der Auswahlliste angezeigte Text.

Klicken Sie auf **[!UICONTROL Erweiterte Parameter...]**, um die für die Benutzerbenachrichtigungen zu verwendende Versandvorlage auszuwählen. Die Standardvorlage (mit internem Namen &#39;notifyAssignee&#39;) übernimmt den Titel und den Nachrichteninhalt sowie einen Link auf die Webseite mit dem Antwortformular.

Die Vorlage kann angepasst werden. Es wird jedoch empfohlen, sie zu duplizieren und unter einem neuen Namen zu speichern. Der Zielgruppenmechanismus (externe Datei, Zielgruppen-Mapping) darf hingegen nicht geändert werden. Er ist für die korrekte Funktionsweise der Benachrichtigungen erforderlich.

Ein Validierungsbeispiel finden Sie im Abschnitt ](../../workflow/using/defining-approvals.md)Validierungen definieren[.

## Ausgabeparameter {#output-parameters}

* **[!UICONTROL response]**

   Kommentar zur Antwort

* **[!UICONTROL responseOperator]**

   Kennung des Benutzers, der die Validierung vorgenommen hat. Dieses Feld enthält einen numerischen Wert, ist aber vom Typ **[!UICONTROL String]**.


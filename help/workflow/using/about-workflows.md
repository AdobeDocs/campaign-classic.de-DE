---
solution: Campaign Classic
product: campaign
title: Über Workflows
description: Automatisieren Sie Prozesse mit Workflows, verwalten Sie Daten und Audiences, senden Sie Nachrichten und vieles mehr.
audience: workflow
content-type: reference
topic-tags: introduction
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 100%

---


# Erste Schritte mit Workflows{#gs-workflows}

## Über Workflows{#about-workflows}

Mit Adobe Campaign verfügen Sie über ein integriertes Workflow-Management-System, welches die zentrale Steuerung aller Prozesse und Vorgänge der Anwendung ermöglicht. Die Workflow-Engine dient der Modellierung und Automatisierung der verschiedenen Aufgaben der Anwendungsserver-Module. Mithilfe der grafischen Oberfläche lassen sich vollständige Arbeitsabläufe zur Segmentierung von Zielgruppen, der Ausführung von Kampagnen, dem Umgang mit Dateien etc. gestalten.

So bieten Workflows beispielsweise die Möglichkeit, Dateien von einem Server herunterladen, sie zu entkomprimieren und die Datensätze in die Adobe-Campaign-Datenbank zu importieren.

Oder benachrichtigen Sie andere Benutzer und fordern Sie sie dazu auf, Vorgänge zu validieren oder an Abstimmungen teilzunehmen. Auf diese Weise können Versandaktionen erstellt und anderen Benutzern vor dem Nachrichtenversand Aufgaben wie die Gestaltung des Inhalts, die Bestimmung der Zielgruppe und die Validierung von Testsendungen zugewiesen werden.

In Adobe Campaign kommen Workflows in unterschiedlichsten Kontexten und zu verschiedenen Zeitpunkten innerhalb der Kampagnenprozesse zum Einsatz.

Beispielhaft seien folgende Vorgänge genannt:

* Durchführen einer Zielgruppenbestimmung. [Mehr dazu](../../workflow/using/building-a-workflow.md#implementation-steps-)
* Erstellen von Kampagnen: Auf dem Tab **[!UICONTROL Workflow]** können Sie die Zielgruppe und die Sendungen erstellen. [Mehr dazu](../../workflow/using/building-a-workflow.md#campaign-workflows)
* Durchführen von technischen Prozessen: Bereinigung, Erfassung von Tracking-Informationen oder vorläufige Berechnungen. [Mehr dazu](../../workflow/using/building-a-workflow.md#technical-workflows)

Der Begriff Workflow bezeichnet einerseits einen Prozess (Workflow-Vorlage: Darstellung eines theoretischen Ablaufs) und andererseits eine Instanz dieses Prozesses (Workflow-Instanz: Darstellung des tatsächlichen Ablaufs).

Die Workflow-Vorlage beschreibt die verschiedenen zu erfüllenden Aufgaben und ihre Abfolge. Aufgabenvorlagen werden als Aktivitäten bezeichnet und durch Symbole repräsentiert. Sie sind durch Transitionen miteinander verbunden.

![](assets/example1.png)

Jeder Workflow besteht aus:

* **[!UICONTROL Activities]**

   Aktivitäten sind Vorlagen für Aufgaben. Es gibt verschiedene Aktivitätstypen, die jeweils durch verschiedene Symbole im Diagramm dargestellt werden. Jeder Aktivitätstyp weist allgemeine und spezifische Eigenschaften auf. So haben beispielsweise alle Aktivitäten einen Namen und einen Titel, aber nur die Aktivität **[!UICONTROL Validierung]** bietet die Möglichkeit, einem Benutzer eine Aufgabe zuzuweisen.

   In einem Workflow-Diagramm kann eine einzelne Aktivität verschiedene Aufgaben auslösen. Dies ist insbesondere der Fall bei Schleifen oder (periodisch) wiederkehrenden Aktionen.

   Alle Workflow-Aktivitäten einschließlich Anwendungsbeispiele finden Sie in [diesem Abschnitt](../../workflow/using/about-activities.md).

* **[!UICONTROL Transitionen]**

   Transitionen stellen die Verbindungen zwischen Aktivitäten her und bestimmen die Reihenfolge der Verarbeitung. Jede Transition verbindet eine Quellaktivität mit einer Zielaktivität. Je nach Quellaktivität existieren verschiedene Transitionstypen. Bestimmte Transitionen bieten die Möglichkeit, zusätzliche Eigenschaften wie z. B. eine Dauer, eine Bedingung oder einen Filter zu definieren.

   Transitionen, die nicht mit einer Zielaktivität verbunden sind, werden als schwebend bezeichnet. Schwebende Transitionen sind orangefarben mit einer Raute anstelle der Pfeilspitze.

   >[!NOTE]
   >
   >Auch mit schwebenden Transitionen kann ein Workflow ausgeführt werden: Die Ausführung erzeugt einen Warnhinweis und wird bei Aktivierung einer derartigen Transition ausgesetzt. Es wird jedoch kein Fehler erzeugt. Auf diese Weise ist es möglich, einen Workflow zu starten, auch wenn seine Konzeption noch nicht vollständig abgeschlossen ist, und ihn nach und nach zu vervollständigen.

   Weiterführende Informationen zur Erstellung eines Workflows finden Sie in [diesem Abschnitt](../../workflow/using/building-a-workflow.md).

* **[!UICONTROL Arbeitstabellen]**

   Arbeitstabellen enthalten alle von der Transition übertragenen Informationen. Dies bedeutet, dass jeder Workflow mehrere Arbeitstabellen beansprucht. Vorausgesetzt, dass sie nicht bereinigt werden, können die Daten der Arbeitstabellen während des ganzen Lebenszyklus eines Workflows verwendet werden. Tatsächlich werden unnütze Tabellen bei jeder Workflow-Passivierung und gegebenenfalls während der Ausführung eines Workflows bereinigt. Letzteres ist bei umfangreichen Arbeitstabellen der Fall, um die Server nicht zu überlasten.

   Weiterführende Informationen zu Workflow-Daten und Tabellen finden Sie in [diesem Abschnitt](../../workflow/using/how-to-use-workflow-data.md).

## Wichtige Grundsätze und Best Practices{#principles-workflows}

In den folgenden Abschnitten finden Sie Anleitungen und Best Practices zur Automatisierung von Prozessen mit Workflows:

* Weiterführende Informationen zu Workflow-Aktivitäten finden Sie auf [dieser Seite](../../workflow/using/how-to-use-workflow-data.md).
* Informationen zum Erstellen eines Workflows finden Sie in [diesem Abschnitt](../../workflow/using/building-a-workflow.md).
* In [diesem Abschnitt](../../workflow/using/importing-data.md) erfahren Sie, wie Sie Daten mithilfe von Workflows in Campaign importieren.
* Die Best Practices bei Workflows werden auf [dieser Seite](../../workflow/using/workflow-best-practices.md) beschrieben.
* Hinweise zur Workflow-Ausführung finden Sie in [diesem Abschnitt](../../workflow/using/starting-a-workflow.md).
* Informationen zum Überwachen von Workflows finden Sie auf [dieser Seite](../../workflow/using/monitoring-workflow-execution.md).
* Erfahren Sie auf [dieser Seite](../../workflow/using/managing-rights.md), wie Sie Benutzern Zugriff auf Workflows gewähren.

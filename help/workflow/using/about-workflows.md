---
title: Über Workflows
seo-title: Über Workflows
description: Über Workflows
seo-description: null
page-status-flag: never-activated
uuid: 19adb0e5-042d-47a0-9f92-24e4b3045dbe
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: introduction
discoiquuid: 868940d1-f19d-4e9a-bffa-8654abb4441c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Über Workflows{#about-workflows}

Mit Adobe Campaign verfügen Sie über ein integriertes Workflow-Management-System, welches die zentrale Steuerung aller Prozesse und Vorgänge der Anwendung ermöglicht. Die Workflow-Engine dient der Modellierung und Automatisierung der verschiedenen Aufgaben der Anwendungsserver-Module. Mithilfe der grafischen Oberfläche lassen sich vollständige Arbeitsabläufe zur Segmentierung von Zielgruppen, der Ausführung von Kampagnen, dem Umgang mit Dateien etc. gestalten.

So bieten Workflows beispielsweise die Möglichkeit, Dateien von einem Server herunterladen, sie zu entkomprimieren und die Datensätze in die Adobe-Campaign-Datenbank zu importieren.

Oder benachrichtigen Sie andere Benutzer und fordern Sie sie dazu auf, Vorgänge zu validieren oder an Abstimmungen teilzunehmen. Auf diese Weise können Versandaktionen erstellt und anderen Benutzern vor dem Nachrichtenversand Aufgaben wie die Gestaltung des Inhalts, die Bestimmung der Zielgruppe und die Validierung von Testsendungen zugewiesen werden.

In Adobe Campaign kommen Workflows in unterschiedlichsten Kontexten und zu verschiedenen Zeitpunkten innerhalb der Kampagnenprozesse zum Einsatz.

Beispielhaft seien folgende Vorgänge genannt:

* Durchführung von Targeting-Kampagnen. For more on this, refer to [Implementation steps](../../workflow/using/building-a-workflow.md#implementation-steps-).
* Erstellen von Kampagnen: können Sie auf der **[!UICONTROL Workflow]** Registerkarte für jede Kampagne das Ziel erstellen und die Auslieferungen erstellen. For more on this, refer to [Campaign workflows](../../workflow/using/building-a-workflow.md#campaign-workflows).
* Technische Prozesse durchführen: Bereinigung, Erfassung von Verfolgungsinformationen oder vorläufige Berechnungen. For more on this, refer to [Technical workflows](../../workflow/using/building-a-workflow.md#technical-workflows).

Der Begriff Workflow bezeichnet einerseits einen Prozess (Workflow-Vorlage: Darstellung eines theoretischen Ablaufs) und andererseits eine Instanz dieses Prozesses (Workflow-Instanz: Darstellung des tatsächlichen Ablaufs).

Die Workflow-Vorlage beschreibt die verschiedenen zu erfüllenden Aufgaben und ihre Abfolge. Aufgabenvorlagen werden als Aktivitäten bezeichnet und durch Symbole repräsentiert. Sie sind durch Transitionen miteinander verbunden.

![](assets/example1.png)

Jeder Workflow besteht aus:

* **[!UICONTROL Activities]**

   Eine Aktivität beschreibt eine Aufgabenvorlage. Die verschiedenen verfügbaren Aktivitäten werden im Diagramm durch Symbole dargestellt. Jeder Typ hat allgemeine Eigenschaften und spezifische Eigenschaften. Während beispielsweise alle Aktivitäten einen Namen und eine Bezeichnung haben, verfügt nur die **[!UICONTROL Approval]** Aktivität über eine Zuweisung.

   In einem Workflow-Diagramm kann eine einzelne Aktivität verschiedene Aufgaben auslösen. Dies ist insbesondere der Fall bei Schleifen oder (periodisch) wiederkehrenden Aktionen.

   Alle Workflow-Aktivitäten einschließlich Anwendungsbeispiele finden Sie in [diesem Abschnitt](../../workflow/using/about-activities.md).

* **[!UICONTROL Transitions]**

   Transitionen stellen die Verbindungen zwischen Aktivitäten her und bestimmen die Reihenfolge der Verarbeitung. Jede Transition verbindet eine Quellaktivität mit einer Zielaktivität. Je nach Quellaktivität existieren verschiedene Transitionstypen. Bestimmte Transitionen bieten die Möglichkeit, zusätzliche Eigenschaften wie z. B. eine Dauer, eine Bedingung oder einen Filter zu definieren.

   Transitionen, die nicht mit einer Zielaktivität verbunden sind, werden als schwebend bezeichnet. Schwebende Transitionen sind orangefarben mit einer Raute anstelle der Pfeilspitze.

   >[!NOTE]
   >
   >Auch mit schwebenden Transitionen kann ein Workflow ausgeführt werden: Die Ausführung erzeugt einen Warnhinweis und wird bei Aktivierung einer derartigen Transition ausgesetzt. Es wird jedoch kein Fehler erzeugt. Auf diese Weise ist es möglich, einen Workflow zu starten, auch wenn seine Konzeption noch nicht vollständig abgeschlossen ist, und ihn nach und nach zu vervollständigen.

   Weiterführende Informationen zur Erstellung eines Workflows finden Sie in [diesem Abschnitt](../../workflow/using/building-a-workflow.md).

* **[!UICONTROL Worktables]**

   Arbeitstabellen enthalten alle von der Transition übertragenen Informationen. Dies bedeutet, dass jeder Workflow mehrere Arbeitstabellen beansprucht. Vorausgesetzt, dass sie nicht bereinigt werden, können die Daten der Arbeitstabellen während des ganzen Lebenszyklus eines Workflows verwendet werden. Tatsächlich werden unnütze Tabellen bei jeder Workflow-Passivierung und gegebenenfalls während der Ausführung eines Workflows bereinigt. Letzteres ist bei umfangreichen Arbeitstabellen der Fall, um die Server nicht zu überlasten.

   Weiterführende Informationen zu Workflow-Daten und Tabellen finden Sie in [diesem Abschnitt](../../workflow/using/how-to-use-workflow-data.md).


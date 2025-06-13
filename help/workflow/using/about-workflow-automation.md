---
product: campaign
title: Über Workflows
description: Automatisieren Sie Prozesse mit Workflows, verwalten Sie Daten und Audiences, senden Sie Nachrichten und vieles mehr
feature: Workflows, Data Management
exl-id: 024a7344-9376-4ff3-926a-003148229f9f
source-git-commit: b353b562bd2f0b0bd2dfde22c6477ab66d499483
workflow-type: ht
source-wordcount: '232'
ht-degree: 100%

---

# Automatisieren mit Workflows {#gs-workflows}

Die Workflows von Adobe Campaign ermöglichen es Ihrem Team, End-to-End-Geschäftsprozesse plattformübergreifend zu optimieren und zu automatisieren. Mit einer intuitiven grafischen Oberfläche können Sie Workflows entwerfen und verwalten, die Aufgaben wie Datensegmentierung, Kampagnenausführung, Dateiverarbeitung und sogar Benutzergenehmigungen an einem Ort koordinieren.

Sie können beispielsweise einen Prozess automatisieren, um eine Datei von einem Remote-Server abzurufen, ihren Inhalt zu extrahieren und die Daten nahtlos auf den Adobe Campaign-Server zu laden. Dies reduziert den manuellen Aufwand und erhöht die betriebliche Effizienz. Die Workflow-Engine stellt sicher, dass jeder Schritt zuverlässig ausgeführt und verfolgt wird, um Sichtbarkeit und Kontrolle zu gewährleisten.

>[!BEGINTABS]

>[!TAB Workflow-Dokumentation]

Weitere Informationen zur Verwaltung von Workflows finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/about-workflows.html?lang=de){target=_blank}.


[![Bild](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/about-workflows.html?lang=de){target=_blank}


>[!TAB Nützliche Links]

Die wichtigsten Schritte für die Workflow-Verwaltung finden Sie in der Dokumentation zu Campaign v8:

* [Workflow-Aktivitäten](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/activities.html?lang=de){target=_blank}: Eine Aktivität ist eine Aufgabenvorlage. Zu den Workflows gehören Zielgruppenbestimmung, Flusskontrolle, Aktions- und Ereignisaktivitäten.

* [Erstellen eines Workflows](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html?lang=de){target=_blank}: Erfahren Sie, wie Sie Zielgruppenbestimmungs-, Kampagnen- und technische Workflows erstellen und ausführen.

* [Best Practices](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/workflow-best-practices.html?lang=de){target=_blank}: Lernen Sie Richtlinien zur Optimierung der Workflow-Leistung von Campaign, zur Verbesserung des Workflow-Designs und zur Definition der richtigen Einstellungen kennen.

* [Überwachen von Workflows](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html?lang=de){target=_blank}: Erfahren Sie, wie Sie die Workflow-Ausführung überwachen, damit alles ordnungsgemäß verläuft.

* [Anwendungsfälle für Workflows](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/workflow-use-cases.html?lang=de){target=_blank}: Lernen Sie Szenarien kennen, in denen Workflows verwendet werden können, und erfahren Sie anhand von End-to-End-Anwendungsfällen, wie Sie die Workflows implementieren.


>[!ENDTABS]





<!--

Adobe Campaign uses workflows to:

* Carry out targeting campaigns. [Learn more](building-a-workflow.md#implementation-steps-)
* Build campaigns: for each campaign, the **[!UICONTROL Workflow]** tab lets you build the target and create the deliveries. [Learn more](building-a-workflow.md#campaign-workflows)
* Perform technical processes: cleanup, collecting tracking information or provisional calculations. [Learn more](building-a-workflow.md#technical-workflows)

A workflow can mean both a process definition (the workflow model, which is a representation of what is supposed to happen) and an instance of this process (a workflow instance, which is a representation of what is actually happening).

The workflow template describes the various tasks to be performed and how they are linked together. The task templates are called activities and are represented by icons. They are linked together by transitions.

![](assets/example1.png)

Each workflow contains:

* **[!UICONTROL Activities]**

  An activity describes a task template. The various activities available are represented on the diagram by icons. Each type has common properties and specific properties. For example, while all activities have a name and label, only the **[!UICONTROL Approval]** activity has an assignment.

  In a workflow diagram, a given activity can produce multiple tasks, in particular when there is a loop or recurrent (periodic) actions.

  All workflow activities are listed in [this section](about-activities.md), including use cases and samples.

* **[!UICONTROL Transitions]**

  Transitions enable you to link activities and to define their sequence. A transition links a source activity to a destination activity. There are several sorts of transitions, which depend on the source activity. Some transitions have additional parameters such as a duration, a condition or a filter.

  A transition which is not linked to a destination activity is colored orange and the arrow head is shown as a diamond.

  >[!NOTE]
  >
  >A workflow containing unterminated transitions can still be executed: a warning message will be generated and the workflow will pause once it reaches the transition but it will not generate an error. It is thus possible to start a workflow without it being finished and to add to it as you go along.

  For more information about how to build a workflow, refer to [this section](building-a-workflow.md).

* **[!UICONTROL Worktables]**

  The worktable contains all the information carried by the transition. Each workflow uses several worktables. The data conveyed in these tables can be accelerated and used throughout the workflow's life cycle, as long as it is not purged. Indeed, unneeded tables are purged each time the workflow is passivated, and possibly during the execution of the largest workflows to avoid overloading the server.

  Learn more on workflow data and tables in [this section](how-to-use-workflow-data.md).

## Key principles and best practices{#principles-workflows}

Refer to these sections to find guidance and best practices to automate processes with workflows:

* Learn more about workflow activities in [this page](how-to-use-workflow-data.md).
* Learn how to build a workflow in [this section](building-a-workflow.md).
* Discover how to use workflows to import data in Campaign in [this section](../../platform/using/import-export-workflows.md).
* Workflow best practices are detailed in [this page](workflow-best-practices.md).
* Find guidance about workflow execution in [this section](starting-a-workflow.md).
* Learn how to monitor workflows in [this page](monitoring-workflow-execution.md).
* Learn how to grant access to users to use workflows in [this page](managing-rights.md).

-->
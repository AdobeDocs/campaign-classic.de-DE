---
product: campaign
title: Über Steuerungsaktivitäten
description: Über Steuerungsaktivitäten
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
feature: Workflows
exl-id: 3810cbd0-159c-4161-b568-1f61dcea0300
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 100%

---

# Steuerungsaktivitäten in Workflows{#about-flow-control-activities}



Folgende Aktivitäten dienen in erster Linie der Koordination anderer Aktivitäten innerhalb eines Workflows.

* **Start und Ende**: markieren den Anfangs- bzw. den Endpunkt eines Workflows. Siehe [Start und Ende](start-and-end.md).
* **Verzweigung**: ermöglicht es Ihnen, alle ausgehende Transitionen zu aktivieren. Siehe Abschnitt [Verzweigung](fork.md).
* **Termin**: wartet, bis alle parallel ablaufenden Aufgaben beendet sind, bevor mit der Ausführung des Workflows fortgefahren wird. Siehe Abschnitt [Verzweigung](fork.md).
* **Planung**: dient der Konfiguration einer Ausführungsplanung für den Workflow. Siehe [Planung](scheduler.md).
* **Test**: aktiviert eine Transition in Abhängigkeit vom Ergebnis eines Tests. Siehe [Test](test.md).
* **Warten**: aktiviert eine ausgehende Transition nach einer definierten Dauer. Siehe [Warten](wait.md).
* **Zeitliche Beschränkung**: setzt die Ausführung einer Aufgabe für eine bestimmte Dauer aus. Siehe [Zeitliche Beschränkung](time-constraint.md).
* **Unter-Workflow**: startet die Ausführung eines weiteren Workflows. Siehe [Unter-Workflow](sub-workflow.md).
* **Sprung**: erzeugt Transitionen ohne direkte Relation. Siehe [Sprung (Startpunkt und Endpunkt)](jump-start-point-and-end-point.md).
* **Externes Signal**: aktiviert eine ausgehende Transition als Reaktion auf ein externes Signal. Lesen Sie diesbezüglich auch den Abschnitt [Externes Signal](external-signal.md).
* **Validierung**: sendet eine E-Mail an einen Benutzer oder eine Benutzergruppe und wartet auf die Validierung, bevor die Ausführung fortgesetzt wird. Siehe Abschnitt [Validierung](approval.md).
* **Warnung**: sendet eine Benachrichtigung an einen Benutzer oder eine Benutzergruppe. Siehe Abschnitt [Warnung](alert.md).
* **Aufgabe**: ermöglicht die Konfiguration der Ausführung von Aufgaben. Siehe Abschnitt [Aufgabe](task.md).

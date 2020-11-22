---
solution: Campaign Classic
product: campaign
title: Technische Workflows überwachen
description: Technische Workflows überwachen
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 100%

---


# Technische Workflows überwachen {#monitoring-technical-workflows}

Technische Workflows müssen überwacht werden und bei einer Störung müssen Maßnahmen ergriffen werden.

Weitere Möglichkeiten zur Überwachung der verschiedenen Campaign-Prozesse werden auf [dieser Seite](../../production/using/monitoring-guidelines.md) vorgestellt.

## Instanz-Monitoring-Dashboard {#instance-monitoring-dashboard}

Auf das Instanz-Monitoring-Dashboard können Sie über die Rubrik **[!UICONTROL Monitoring]** zugreifen.

![](assets/monitoring_technical_workflows1.png)

Prüfen Sie unter &quot;System Indicators&quot; und &quot;core files&quot;, ob Indikatoren rot hervorgehoben sind. Gehen Sie in diesem Fall folgendermaßen vor:

* Prüfen Sie, ob die erforderlichen Prozesse immer aktiv sind.
* Vergewissern Sie sich, dass keiner der Prozesse veraltet ist.
* Vergewissern Sie sich, dass die Protokolldateien der Prozesse keine Alarm auslösenden und wiederkehrenden Fehler aufweisen.

## Technische Workflows {#technical-workflows}

Technische Workflows finden Sie unter **[!UICONTROL Administration]** > **[!UICONTROL Betreibung]** > **[!UICONTROL Technische Workflows]**.

Folgen Sie je nach technischem Workflow den unten beschriebenen Schritten, um ein reibungsloses Funktionieren zu gewährleisten.

In diesem [Abschnitt](../../workflow/using/about-technical-workflows.md) erfahren Sie, was jeder technische Workflow bewirkt.

**[!UICONTROL Datenbankbereinigungs-Workflow (‘cleanup’)]**:

1. Vergewissern Sie sich, dass der Workflow **[!UICONTROL Datenbankbereinigung]** täglich ausgeführt und erfolgreich abgeschlossen wird. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../workflow/using/delivery.md).
1. Vergewissern Sie sich im Protokoll, dass die Ausführungsdauer auch langfristig ungefähr konstant bleibt und andere Workflows nicht stört.
1. Weiterführende Informationen erfahren Sie auf dieser [Seite](../../production/using/database-cleanup-workflow.md).

**[!UICONTROL Tracking-Workflow (‘tracking’)]**:

Vergewissern Sie sich, dass der Tracking-Workflow plangemäß ausgeführt wird (standardmäßig jede Stunde) und im Protokoll keine wiederkehrenden Fehler aufgezeigt werden. Weiterführende Informationen hierzu finden Sie in diesem [Abschnitt](../../workflow/using/delivery.md).

**[!UICONTROL Aktualisierung der Zustellbarkeit (‘deliverabilityUpdate’)]**:

1. Vergewissern Sie sich, dass der **[!UICONTROL Zustellbarkeits-Workflow]** täglich ausgeführt und erfolgreich abgeschlossen wird. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../workflow/using/delivery.md).
1. Prüfen Sie im Protokoll, ob die Regeln regelmäßig aktualisiert werden.

**[!UICONTROL Kampagnenprozesse (&#39;operationMgt&#39;, &#39;deliveryMgt‘ etc.)]**:

1. Sehen Sie sich die Workflows im Ordner **[!UICONTROL Kampagnenprozesse]** an. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../workflow/using/campaign.md).
1. Vergewissern Sie sich, dass die Workflows plangemäß ausgeführt werden und im Protokoll keine wiederkehrenden Fehler aufgezeigt werden.

## Workflow-Supervision {#workflow-supervision}

In der Gruppe **[!UICONTROL Workflow-Supervisoren]** sollten Benutzer enthalten sein, die von Fehlschlägen informiert werden müssen und umgehend Abhilfemaßnahmen setzen können.

![](assets/monitoring_technical_workflows3.png)

Wenn ein Problem auftritt, sollte eine Warnung erzeugt und an die entsprechende Benutzergruppe gesendet werden.

Vergewissern Sie sich, dass für jeden Benutzer eine gültige E-Mail-Adresse angegeben ist.

Alle Workflows, die zur Ausführung der Plattform erforderlich sind, wie etwa tägliche Datenimporte, sollten als &quot;Production&quot; deklariert (Checkbox) und fett dargestellt werden.

## Workflow-Wartungsliste {#workflow-maintenance-list}

Alle benutzerdefinierten technischen Workflows sollten in einem Arbeitsblatt mit folgenden Angaben dokumentiert werden:

* Name und Ort des Workflows
* Zweck
* Zeitplan und Abhängigkeiten
* Verantwortlicher für die Überwachung
* Maßnahmen beim Auftreten eines Problems

![](assets/monitoring_technical_workflows4.png)

## Planung und Automatisierung der Überwachung {#planning-and-automation-of-monitoring}

Durch die Planung der Workflow-Überwachung kann die Überwachung effizienter gestaltet werden. Manche Aufgaben müssen täglich ausgeführt werden, während andere wöchentlich oder monatlich erfolgen.

Die Überwachung kann möglichst effizient gestaltet werden, indem Workflows in Ordnern angeordnet werden, die nach der wiederkehrenden Aufgabe benannt und nach dem Ausführungszeitpunkt sortiert sind.

Durch die Automatisierung der Überwachung können Kosten für Ressourcen eingespart und Aufgaben in geeigneten Intervallen geplant werden.

Sie können einen Monitoring-Workflow einrichten, der den Versand einer E-Mail auslöst, wenn gewisse Aufgaben fehlschlagen oder eine kritische Tabelle zu groß wird.

Sie können eine Ansicht erstellen, in der alle Workflows eines funktionellen Bereichs oder im gesamten System überwacht werden können.

Sie können auch die Vorgangs- oder Berichtsfunktion von Adobe Campaign verwenden, um nach Bedarf eine Dokumentation zu erstellen, die immer auf dem aktuellen Stand ist.

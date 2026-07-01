---
product: campaign
title: Überwachen technischer Workflows
description: Überwachen technischer Workflows
feature: Workflows
hide: true
exl-id: 5e77d196-5c71-438e-8dae-10c6a6e4f29c
TQID: https://experienceleague.adobe.com/Zil5DwLklAKHSiHbsO6m71Lekcy4f8UYQA53uUzkqRg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 533
ht-degree: 100%

---

# Überwachen technischer Workflows {#monitoring-technical-workflows}



Technische Workflows müssen überwacht werden und bei einer Störung müssen Maßnahmen ergriffen werden.

Weitere Möglichkeiten zur Überwachung der verschiedenen Campaign-Prozesse werden auf [dieser Seite](../../production/using/monitoring-guidelines.md) vorgestellt.

## Instanz-Monitoring-Dashboard {#instance-monitoring-dashboard}

Auf das Instanz-Monitoring-Dashboard können Sie über den Tab **[!UICONTROL Monitoring]** zugreifen.

![](assets/monitoring_technical_workflows1.png)

Prüfen Sie unter „Systemindikator“ und „Core-Dateien“, ob Indikatoren rot hervorgehoben sind. Wenn dies der Fall ist, sollten Sie Folgendes tun:

* Prüfen Sie, ob die erforderlichen Prozesse immer aktiv sind.
* Vergewissern Sie sich, dass keiner der Prozesse veraltet ist.
* Vergewissern Sie sich, dass die Protokolldateien der Prozesse keine Alarm auslösenden und wiederkehrenden Fehler aufweisen.

## Technische Workflows {#technical-workflows}

Technische Workflows finden Sie unter **[!UICONTROL Administration]** > **[!UICONTROL Betreibung]** > **[!UICONTROL Technische Workflows]**.

Folgen Sie je nach technischem Workflow den unten beschriebenen Schritten, um ein reibungsloses Funktionieren zu gewährleisten.

In diesem [Abschnitt](about-technical-workflows.md) erfahren Sie, was jeder technische Workflow bewirkt.

**[!UICONTROL Datenbankbereinigungs-Workflow (‘cleanup’)]**:

1. Vergewissern Sie sich, dass der **[!UICONTROL Datenbankbereinigungs-Workflow]** täglich ausgeführt und erfolgreich abgeschlossen wird. Weiterführende Informationen hierzu finden Sie auf [dieser Seite](../../production/using/database-cleanup-workflow.md).
1. Vergewissern Sie sich anhand des Protokolls, dass die verstrichene Zeit langfristig relativ konstant bleibt und andere Workflows nicht beeinträchtigt.

**[!UICONTROL Tracking-Workflow (‘tracking’)]**:

Vergewissern Sie sich, dass der Tracking-Workflow plangemäß ausgeführt wird (standardmäßig jede Stunde) und im Protokoll keine wiederkehrenden Fehler aufgezeigt werden. Weiterführende Informationen hierzu finden Sie in diesem [Abschnitt](delivery.md).

Für die **[!UICONTROL Zustellbarkeit (deliverabilityUpdate)]**:

1. Vergewissern Sie sich, dass der Workflow **[!UICONTROL Zustellbarkeit]** täglich ausgeführt und erfolgreich abgeschlossen wird.
1. Prüfen Sie im Protokoll, ob die Regeln regelmäßig aktualisiert werden.

**[!UICONTROL Kampagnenprozesse (&#39;operationMgt&#39;, &#39;deliveryMgt‘ etc.)]**:

1. Sehen Sie sich die Workflows im Ordner **[!UICONTROL Kampagnenprozesse]** an. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](about-technical-workflows.md).
1. Vergewissern Sie sich, dass die Workflows plangemäß ausgeführt werden und im Protokoll keine wiederkehrenden Fehler aufgezeigt werden.

## Workflow-Supervision {#workflow-supervision}

In der Gruppe **[!UICONTROL Workflow-Verantwortliche]** sollten Benutzer enthalten sein, die von Fehlschlägen informiert werden müssen und umgehend Abhilfemaßnahmen setzen können.

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
* Maßnahmen beim Auftreten eines Fehlers

![](assets/monitoring_technical_workflows4.png)

## Planung und Automatisierung der Überwachung {#planning-and-automation-of-monitoring}

Die Planung der Workflow-Überwachung verbessert ihre Effizienz. Manche Aufgaben müssen täglich ausgeführt werden, während andere wöchentlich oder monatlich erfolgen.

Die Überwachung kann möglichst effizient gestaltet werden, indem Workflows in Ordnern angeordnet werden, die nach der wiederkehrenden Aufgabe benannt und nach dem Ausführungszeitpunkt sortiert sind.

Durch die Automatisierung der Überwachung können Kosten für Ressourcen eingespart und Aufgaben in geeigneten Intervallen geplant werden.

Sie können einen Monitoring-Workflow einrichten, der eine E-Mail sendet, wenn gewisse Aufgaben fehlschlagen oder eine kritische Tabelle zu groß wird.

Sie können eine Ansicht erstellen, in der alle Workflows eines funktionellen Bereichs oder im gesamten System überwacht werden können.

Sie können auch die Auftrags- oder Berichtsfunktion von Adobe Campaign verwenden, um nach Bedarf eine Dokumentation zu erstellen, die immer auf dem aktuellen Stand ist.

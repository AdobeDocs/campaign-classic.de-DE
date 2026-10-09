---
product: campaign
title: Lebenszyklus eines Workflows
description: Erfahren Sie mehr über den Lebenszyklus eines Workflows
feature: Workflows
hide: true
exl-id: fceb5752-dc73-4386-8c18-c4f3e6110ca5
TQID: 'https://experienceleague.adobe.com/-Uu7Js6XOCdXBvaVlGD0uN0kuMzN-Zwq3XoTaTSBi8k'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: 3e213ecc670d5a3cb8299c092ccbb5303858327d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 100%
---
# Lebenszyklus eines Workflows {#workflow-life-cycle}



Der Lebenszyklus eines Workflows gestaltet sich in drei Hauptetappen:

* **In Bearbeitung**

  Hierbei handelt es sich um die Phase der Erstellung. Wenn ein Workflow neu erstellt wird, ist er im Bearbeitungsstatus. Ein solcher Workflow wurde noch nicht vom Server übernommen und kann daher problemlos geändert werden.

* **Gestartet**

  Nach Abschluss der Erstellungsphase kann der Workflow gestartet werden. In dieser Phase wird die Instanz vom Server verarbeitet und die einzelnen Aufgaben werden ausgeführt. Der Workflow kann – mit bestimmten Vorsichtsmaßnahmen – immer noch geändert werden.

* **Abgeschlossen**

  Ein Workflow ist abgeschlossen, wenn keine Aufgaben mehr zur Verarbeitung anstehen, oder wenn ein Benutzer die Workflow-Instanz ausdrücklich angehalten hat.

Beispielsweise sind im unten stehenden Workflow die Aktivitäten **Beginn** und **Versand** umrandet und die Aktivität **Validierung** blinkt.

![](assets/new-workflow-6.png)

Dies bedeutet, dass die ersten beiden Aktivitäten erfolgreich ausgeführt wurden und dass die Validierungsaktivität in Gang ist, d. h. sie wurde erstellt, ist aber noch nicht abgeschlossen.

Oberhalb der Transition nach der Aktivität **Versand** werden die Zeichen **574 - OK** angezeigt. Daran ist erkennbar, dass bei der Versandvorbereitung 574 Empfängerinnen und Empfänger ausgewählt wurden und dass der Vorgang korrekt abgeschlossen wurde. Diese Informationen, die den Transitionen bei ihrer Ausführung hinzugefügt werden, werden von den Aktivitäten berechnet, die Daten verarbeiten.

Der Workflow wartet also auf die Entscheidung eines Benutzers, der der Gruppe angehört, welche in der **Validierung**-Aktivität ausgewählt wurde. Gruppenmitglieder, deren E-Mail-Adresse oder Mobiltelefonnummer in ihrem Profil gespeichert sind, werden über die entsprechenden Kanäle benachrichtigt.

Die Benutzerverwaltung wird in diesem [Abschnitt](../../platform/using/access-management.md) beschrieben.

Weitere Informationen zur Überwachung Ihrer Workflows finden Sie in [diesem Abschnitt](monitoring-workflow-execution.md).

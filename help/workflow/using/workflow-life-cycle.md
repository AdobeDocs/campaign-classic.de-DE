---
product: campaign
title: Lebenszyklus eines Workflows
description: Erfahren Sie mehr über den Lebenszyklus eines Workflows
feature: Workflows
hide: true
hidefromtoc: true
exl-id: fceb5752-dc73-4386-8c18-c4f3e6110ca5
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 100%

---

# Lebenszyklus eines Workflows {#workflow-life-cycle}



Der Lebenszyklus eines Workflows gestaltet sich in drei Hauptetappen:

* **In Bearbeitung**

  Hierbei handelt es sich um die Phase der Erstellung. Ein neu erstellter Workflow weist den Bearbeitungsstatus auf. Ein derartiger Workflow wurde noch nicht vom Server übernommen und kann daher problemlos geändert werden.

* **Gestartet**

  Nach Abschluss der Konzeptionsphase kann der Workflow gestartet werden. Jetzt wird die Instanz vom Server übernommen und die elementaren Aufgaben werden ausgeführt. Der Workflow kann unter Beachtung gewisser Vorsichtsmaßnahmen trotzdem noch geändert werden.

* **Abgeschlossen**

  Ein Workflow ist abgeschlossen, wenn keine Aufgaben mehr zur Verarbeitung anstehen, oder wenn ein Benutzer die Workflow-Instanz ausdrücklich angehalten hat.

Beispielsweise sind im unten stehenden Workflow die Aktivitäten **Beginn** und **Versand** umrandet und die Aktivität **Validierung** blinkt.

![](assets/new-workflow-6.png)

Dies bedeutet, dass die ersten beiden Aktivitäten erfolgreich ausgeführt wurden und dass die Validierungsaktivität in Gang ist, d. h. sie wurde erstellt, ist aber noch nicht abgeschlossen.

Oberhalb der Transition des **Versands** wird **574 - OK** angezeigt. Daran ist erkennbar, dass bei der Versandvorbereitung 574 Empfänger ausgewählt wurden und dass der Vorgang korrekt abgelaufen ist. Diese Art an Informationen wird von Aktivitäten berechnet, die Daten manipulieren, und im Verlauf der Workflow-Ausführung auf den Transitionen angezeigt.

Der Workflow wartet also auf die Entscheidung eines Benutzers, der der Gruppe angehört, welche in der **Validierung**-Aktivität ausgewählt wurde. Gruppenmitglieder, deren E-Mail-Adresse oder Mobiltelefonnummer in ihrem Profil gespeichert sind, werden über die entsprechenden Kanäle benachrichtigt.

Die Benutzerverwaltung wird in diesem [Abschnitt](../../platform/using/access-management.md) beschrieben.

Weitere Informationen zur Überwachung Ihrer Workflows finden Sie in [diesem Abschnitt](monitoring-workflow-execution.md).

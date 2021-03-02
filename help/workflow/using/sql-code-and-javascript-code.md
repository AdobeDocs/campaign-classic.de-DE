---
solution: Campaign Classic
product: campaign
title: SQL-Code und JavaScript-Code
description: Erfahren Sie mehr über die Workflow-Aktivitäten für SQL- und JavaScript-Codes.
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: add0efb4efd5a37129c649b942799622947f3143
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 87%

---


# SQL-Code und JavaScript-Code{#sql-code-and-javascript-code}

## SQL-Code {#sql-code}

Die Aktivität **[!UICONTROL SQL-Code]** führt ein SQL-Script in Form eines JST-Templates aus.

![](assets/sql_code.png)

* **[!UICONTROL Script]**

   Das Skript wird in den zentralen Bereich des Editors eingefügt. Da es sich beim Skript um ein JST-Template handelt, kann es dem Workflow-Kontext entsprechend konfiguriert werden.

* **[!UICONTROL Fehler verarbeiten]**

   Siehe [Fehler verarbeiten](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## JavaScript-Code und erweiterter JavaScript-Code {#javascript-code}

Aktivitäten mit **[!UICONTROL JavaScript-Code]** und **[!UICONTROL erweitertem JavaScript-Code]** führen im Kontext von Workflows ein JavaScript-Skript aus. Weitere Informationen zur Skripterstellung finden Sie im Abschnitt [Scripts/JavaScript-Templates](../../workflow/using/javascript-scripts-and-templates.md).

### Ausführungsverzögerung {#exec-delay}

Ab Version 20.2 wurde eine Ausführungsverzögerung zu den Aktivitäten **[!UICONTROL JavaScript-Code]** und **[!UICONTROL Erweiterter JavaScript-Code]** hinzugefügt. Standardmäßig darf die Ausführungsphase nicht länger als eine Stunde sein. Nach dieser Verzögerung wird der Vorgang mit einer Fehlermeldung abgebrochen und die Ausführung der Aktivität schlägt fehl.

Sie können diese Verzögerung im Feld **[!UICONTROL Ausführung stoppen nach]** in diesen Aktivitäten ändern.

Um diese Begrenzung zu ignorieren, müssen Sie den Wert auf **0** setzen.

### JavaScript-Code {#js-code-desc}

![](assets/javascript_code.png)

* **[!UICONTROL Script]**: Das auszuführende Skript wird in den zentralen Bereich des Editors eingefügt.

* **[!UICONTROL Fehler verarbeiten]**: Siehe [Fehler verarbeiten](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

### Erweiterter JavaScript-Code {#adv-js-code-desc}

![](assets/advanced_javascript_code.png)

* **[!UICONTROL Erster Aufruf]**: Das beim ersten Aufruf auszuführende Skript wird im oberen Bereich des Editors eingefügt.
* **[!UICONTROL Nächste Aufrufe]**: Das bei allen weiteren Aufrufen auszuführende Skript wird im unteren Bereich des Editors eingefügt.
* **[!UICONTROL Transitionen]**: Es ist möglich, mehrere aus dieser Aktivität ausgehende Transitionen zu definieren.
* **[!UICONTROL Zeitplan]** Im Tab **[!UICONTROL Planung]** können der Ausführungszeitpunkt und -rhythmus der Aktivität definiert werden.

Erweitertes JavaScript ist eine persistente Aufgabe und wird in regelmäßigen Abständen zurückgerufen, wenn es nicht als abgeschlossen markiert wurde. Um die Aufgabe zu beenden und künftige Rückrufe zu verhindern, müssen Sie die **Aufgabe.setComplete()**-Methode im Abschnitt **[!UICONTROL Nächste Aufrufe]** verwenden:

```
task.postEvent(task.transitionByName("ok")); // to transition to Ok branch
task.setCompleted();

return 0;
```

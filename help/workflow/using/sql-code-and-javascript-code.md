---
product: campaign
title: SQL-Code und JavaScript-Code
description: Erfahren Sie mehr über die Workflow-Aktivitäten für SQL- und JavaScript-Codes.
feature: Workflows
hide: true
exl-id: 729a2010-c2d8-481b-8c9e-780b9e5f97ef
TQID: https://experienceleague.adobe.com/B-OWeBTtXSxSD1k-qgRq06ymp00LvVH2U7k9yRAN3YE
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: c35995a47788db080636c66827a4bd6dc98806cf
workflow-type: ht
source-wordcount: 300
ht-degree: 100%

---

# SQL-Code und JavaScript-Code{#sql-code-and-javascript-code}



## SQL-Code {#sql-code}

Die Aktivität **[!UICONTROL SQL-Code]** führt ein SQL-Skript aus. Das Skript ist eine JST-Vorlage.

![](assets/sql_code.png)

* **[!UICONTROL Script]**

  Das auszuführende Skript wird im zentralen Bereich des Editors angezeigt. Da es sich beim Skript um eine JST-Vorlage handelt, kann es entsprechend dem Workflow-Kontext konfiguriert werden.

* **[!UICONTROL Fehler verarbeiten]**

  Siehe [Fehler verarbeiten](monitoring-workflow-execution.md#processing-errors).

## JavaScript-Code und erweiterter JavaScript-Code {#javascript-code}

Aktivitäten mit **[!UICONTROL JavaScript-Code]** und **[!UICONTROL erweitertem JavaScript-Code]** führen im Kontext von Workflows ein JavaScript-Script aus. Weitere Informationen zur Scripterstellung finden Sie in diesen Abschnitten:

* [JavaScript-Scripte und -Vorlagen](javascript-scripts-and-templates.md)
* [Beispiele für JavaScript-Code in Workflows](javascript-in-workflows.md)

### Ausführungsverzögerung {#exec-delay}

Ab Version 20.2 wurde eine Ausführungsverzögerung zu den Aktivitäten **[!UICONTROL JavaScript-Code]** und **[!UICONTROL Erweiterter JavaScript-Code]** hinzugefügt. Standardmäßig darf die Ausführungsphase nicht länger als eine Stunde sein. Nach dieser Verzögerung wird der Vorgang mit einer Fehlermeldung abgebrochen und die Ausführung der Aktivität schlägt fehl.

Sie können diese Verzögerung im Feld **[!UICONTROL Ausführung stoppen nach]** in diesen Aktivitäten ändern.

Um diese Begrenzung zu ignorieren, müssen Sie den Wert auf **0** setzen.

### JavaScript-Code {#js-code-desc}

![](assets/javascript_code.png)

* **[!UICONTROL Script]**: Das auszuführende Script wird in den zentralen Bereich des Editors eingefügt.

* **[!UICONTROL Fehler verarbeiten]**: Siehe [Fehler verarbeiten](monitoring-workflow-execution.md#processing-errors).

### Erweiterter JavaScript-Code {#adv-js-code-desc}

![](assets/advanced_javascript_code.png)

* **[!UICONTROL Erster Aufruf]**: Das beim ersten Aufruf auszuführende Script wird im oberen Bereich des Editors eingefügt.
* **[!UICONTROL Nächste Aufrufe]**: Das bei allen weiteren Aufrufen auszuführende Script wird im unteren Bereich des Editors eingefügt.
* **[!UICONTROL Transitionen]**: Es ist möglich, mehrere aus dieser Aktivität ausgehende Transitionen zu definieren.
* **[!UICONTROL Zeitplan]** Im Tab **[!UICONTROL Planung]** können der Ausführungszeitpunkt und -rhythmus der Aktivität definiert werden.

Erweitertes JavaScript ist eine persistente Aufgabe und wird in regelmäßigen Abständen zurückgerufen, wenn es nicht als abgeschlossen markiert wurde. Um die Aufgabe zu beenden und künftige Rückrufe zu verhindern, müssen Sie die **task.setCompleted()**-Methode im Abschnitt **[!UICONTROL Nächste Aufrufe]** verwenden:

```
task.postEvent(task.transitionByName("ok")); // to transition to Ok branch
task.setCompleted();

return 0;
```


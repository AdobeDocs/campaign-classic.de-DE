---
solution: Campaign Classic
product: campaign
title: SQL-Code und JavaScript-Code
description: Erfahren Sie mehr über die Workflow-Aktivitäten für SQL- und JavaScript-Codes.
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 8bcfc8826a66517e6a648dbc57b681778718c33c
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 76%

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

Ab Version 20.2 wurde eine Ausführungsverzögerung zu den Aktivitäten **[!UICONTROL JavaScript-Code]** und **[!UICONTROL Erweiterter JavaScript-Code]** hinzugefügt. Standardmäßig darf die Ausführungsphase nicht länger als eine Stunde sein. Nach diesem Zeitraum wird der Vorgang mit einer Fehlernachricht abgebrochen und die Ausführung der Aktivität schlägt fehl.

Sie können diese Verzögerung im Feld **[!UICONTROL Ausführung nach]** beenden ändern, das in diesen Aktivitäten verfügbar ist.

Um diese Beschränkung zu ignorieren, müssen Sie den Wert auf **0** setzen.

### JavaScript-Code {#js-code-desc}

![](assets/javascript_code.png)

* **[!UICONTROL Script]**: Das auszuführende Skript wird in den zentralen Bereich des Editors eingefügt.

* **[!UICONTROL Prozessfehler]**: Siehe  [Verarbeitungsfehler](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

### Erweiterter JavaScript-Code {#adv-js-code-desc}

![](assets/advanced_javascript_code.png)

* **[!UICONTROL Erster Aufruf]**: Das beim ersten Aufruf auszuführende Skript wird im oberen Bereich des Editors eingefügt.
* **[!UICONTROL Nächste Aufrufe]**: Das bei allen weiteren Aufrufen auszuführende Skript wird im unteren Bereich des Editors eingefügt.
* **[!UICONTROL Transitionen]**: Es ist möglich, mehrere aus dieser Aktivität ausgehende Transitionen zu definieren.
* **[!UICONTROL Zeitplan]** Im Tab **[!UICONTROL Planung]** können der Ausführungszeitpunkt und -rhythmus der Aktivität definiert werden.

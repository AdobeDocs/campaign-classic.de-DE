---
title: SQL-Code und JavaScript-Code
seo-title: SQL-Code und JavaScript-Code
description: SQL-Code und JavaScript-Code
seo-description: null
page-status-flag: never-activated
uuid: 20a39bbf-c6b0-4697-97b4-c07609cfb048
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 1afa75c2-7377-4d03-9105-11bcc9e3206c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 16e35b62cdf42c04139cc17645095a3d1f6e0fa7

---


# SQL-Code und JavaScript-Code{#sql-code-and-javascript-code}

## SQL-Code {#sql-code}

Eine **[!UICONTROL SQL code*]* -Aktivität führt ein SQL-Skript aus. Das Skript ist eine JST-Vorlage.

![](assets/sql_code.png)

* **[!UICONTROL Script]**

   Das Script wird in den zentralen Bereich des Editors eingefügt. Da es sich beim Script um ein JST-Template handelt, kann es dem Workflow-Kontext entsprechend konfiguriert werden.

* **[!UICONTROL Processing errors]**

   Siehe [Verarbeitungsfehler](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## JavaScript-Code und erweiterter JavaScript-Code {#javascript-code}

**[!UICONTROL JavaScript code]** und **[!UICONTROL Advanced JavaScript code]** Aktivitäten führen ein JavaScript-Skript im Kontext eines Workflows aus. Weitere Informationen zur Skripterstellung finden Sie im Abschnitt zu [JavaScript-Skripten und -Vorlagen](../../workflow/using/javascript-scripts-and-templates.md) .

>[!NOTE]
>
>Standardmäßig beträgt die Ausführungsphase von **[!UICONTROL JavaScript code]** und **[!UICONTROL Advanced JavaScript code]** Aktivitäten maximal 1 Stunde. Nach dieser Verzögerung wird der Prozess mit einer Fehlermeldung abgebrochen und die Ausführung der Aktivität schlägt fehl.
>
>Sie können diese Verzögerung im Feld ändern, das in den Eigenschaften der Aktivitäten **[!UICONTROL Stop execution after]** verfügbar ist.

* **[!UICONTROL JavaScript code]**

   ![](assets/javascript_code.png)

   * **[!UICONTROL Script]**: Das Script wird in den zentralen Bereich des Editors eingefügt.
   * **[!UICONTROL Processing errors]**:Siehe [Verarbeitungsfehler](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

* **[!UICONTROL Advanced JavaScript code]**

   ![](assets/advanced_javascript_code.png)

   * **[!UICONTROL First call]**: Das beim ersten Aufruf auszuführende Script wird im oberen Bereich des Editors eingefügt.
   * **[!UICONTROL Next calls]**: Das bei allen weiteren Aufrufen auszuführende Script wird im unteren Bereich des Editors eingefügt.
   * **[!UICONTROL Transitions]**: Es ist möglich, mehrere aus dieser Aktivität ausgehende Transitionen zu definieren.
   * **[!UICONTROL Schedule]**:Auf der **[!UICONTROL Schedule]** Registerkarte können Sie den Zeitpunkt des Auslösens der Aktivität planen.

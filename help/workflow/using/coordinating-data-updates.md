---
title: Datenaktualisierungen koordinieren
seo-title: Datenaktualisierungen koordinieren
description: Datenaktualisierungen koordinieren
seo-description: null
page-status-flag: never-activated
uuid: 003d63f8-3169-4190-882e-e360a83ccafb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: efe09c66-b74b-48f0-9042-5da4342e014e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

---


# Datenaktualisierungen koordinieren{#coordinating-data-updates}

Das folgende Anwendungsbeispiel erläutert die Erstellung eines Workflows, mit dem Aktualisierungen bei der mehrmaligen Ausführung eines Workflows verwaltet werden können.

Dabei muss sichergestellt werden, dass eine Aktualisierung beendet ist, bevor eine weitere durchgeführt wird. Wir werden zu diesem Zweck eine Instanzvariable erstellen und im Workflow testen, ob die Instanz ausgeführt wird, um zu entscheiden, ob die Ausführung des Workflows fortgesetzt und die Aktualisierung durchgeführt werden soll.

![](assets/uc_dataupdate_wkf.png)

Der vorliegende Workflow besteht aus folgenden Aktivitäten:

* **Planung:** Hiermit wird der Workflow zu bestimmten Zeiten durchgeführt.
* **Test:** Hiermit wird geprüft, ob der Workflow bereits ausgeführt wird.
* **Abfrage** und **Daten-Update:** falls der Workflow noch nicht ausgeführt wird; gefolgt von der Aktivität **Ende,** durch die die Instanzvariable des Workflows auf false zurückgesetzt wird.
* **Ende:** falls der Workflow bereits ausgeführt wird.

Gehen Sie zur Erstellung des Workflows wie folgt vor:

1. Fügen Sie die Aktivität **Planung** hinzu und konfigurieren Sie deren Häufigkeit nach Bedarf.
1. Fügen Sie die Aktivität **Test** hinzu, um zu prüfen, ob der Workflow bereits durchgeführt wird, und konfigurieren Sie sie gemäß den unten stehenden Angaben.

   >[!NOTE]
   >
   >&quot;isRunning&quot; ist die für dieses Beispiel ausgewählte Instanzvariable, und keine integrierte Variable.

   ![](assets/uc_dataupdate_test.png)

1. Fügen Sie zur **Nein**-Verzweigung die Aktivität **Ende** hinzu, damit nichts ausgeführt wird, falls der Workflow bereits ausgeführt wird.
1. Fügen Sie die gewünschten Aktivitäten zur **Ja**-Verzweigung hinzu. Für unser Beispiel sind dies die Aktivitäten **Abfrage** und **Daten-Update**.
1. Öffnen Sie die erste Aktivität und fügen Sie dann den Befehl **instance.vars.isRunning = true** auf der **[!UICONTROL Advanced]** Registerkarte hinzu. Auf diese Weise wird die Instanzvariable als ausgeführt eingestellt.

   ![](assets/uc_dataupdate_query.png)

1. Add an **End** activity at the end of the **[!UICONTROL Yes]** fork, then add the **instance.vars.isRunning = false** command in the **[!UICONTROL Advanced]** tab.

   Dadurch wird keine Aktion aufgeführt, solange der Workflow ausgeführt wird.

   ![](assets/uc_dataupdate_end.png)

**Verwandte Themen:**

* [Mehrere gleichzeitige Ausführungen verhindern](../../workflow/using/monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)
* [Daten-Update-Aktivität](../../workflow/using/update-data.md)


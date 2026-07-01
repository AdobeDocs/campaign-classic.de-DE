---
product: campaign
title: Koordinieren von Datenaktualisierungen
description: Koordinieren von Datenaktualisierungen
feature: Workflows, Data Management
hide: true
exl-id: 9959e22e-9aa0-410f-b22c-9ca1cac46b97
TQID: https://experienceleague.adobe.com/G82StaXeELHRHF4C1qMnRK0IekJoF0n-r6xQi63KPlk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 304
ht-degree: 100%

---

# Koordinieren von Datenaktualisierungen{#coordinating-data-updates}



Das folgende Anwendungsbeispiel erläutert die Erstellung eines Workflows, mit dem begleitende Aktualisierungen bei der mehrmaligen Ausführung eines Workflows verwaltet werden können.

Dadurch soll überprüft werden, ob der Aktualisierungsprozess beendet wurde, bevor ein weiterer Aktualisierungsvorgang ausgeführt wird. Wir werden zu diesem Zweck eine Instanzvariable erstellen und im Workflow testen, ob die Instanz ausgeführt wird, um zu entscheiden, ob die Ausführung des Workflows fortgesetzt und die Aktualisierung durchgeführt werden soll.

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
   >„isRunning“ ist die für dieses Beispiel ausgewählte Instanzvariable. Dies ist keine integrierte Variable.

   ![](assets/uc_dataupdate_test.png)

1. Fügen Sie eine Aktivität **Ende** zur **Nein**-Verzweigung hinzu. Dadurch erfolgt keine Ausführung, falls der Workflow bereits ausgeführt wird.
1. Fügen Sie die gewünschten Aktivitäten zur **Ja**-Verzweigung hinzu. Für unser Beispiel sind dies die Aktivitäten **Abfrage** und **Daten-Update**.
1. Öffnen Sie die erste Aktivität und fügen Sie den Befehl **instance.vars.isRunning = true** auf dem Tab **[!UICONTROL Erweitert]** hinzu. Auf diese Weise wird die Instanzvariable auf „wird ausgeführt“ gesetzt.

   ![](assets/uc_dataupdate_query.png)

1. Fügen Sie am Ende der **[!UICONTROL Ja]**-Verzweigung eine **Ende**-Aktivität an und geben Sie danach den Befehl **instance.vars.isRunning = false** im Tab **[!UICONTROL Erweitert]** ein.

   Dadurch wird keine Aktion aufgeführt, solange der Workflow ausgeführt wird.

   ![](assets/uc_dataupdate_end.png)

**Verwandte Themen:**

* [Mehrere gleichzeitige Ausführungen verhindern](monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)
* [Aktivität &quot;Daten-Update&quot;](update-data.md)

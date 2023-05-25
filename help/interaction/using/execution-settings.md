---
product: campaign
title: Ausführungsparameter
description: Ausführungsparameter
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: e2dea4a0-9ed8-47b6-a16b-eeee653d2290
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: ht
source-wordcount: '162'
ht-degree: 100%

---

# Ausführungsparameter{#execution-settings}



Bei Erstellung einer Simulation haben Sie die Möglichkeit, Ausführungsparameter anzugeben. Auf diese Weise können Sie die Ausführung der Simulation in Abhängigkeit von ihrer Prioritätsstufe auf einen Zeitpunkt mit geringer Auslastung verschieben und die SQL-Abfragen im Protokoll speichern.

Eine Änderung dieser Parameter ist im späteren Verlauf im Tab **[!UICONTROL Allgemein]** des Simulationsfensters möglich.

![](assets/offer_simulation_008.png)

* **[!UICONTROL Ausführung auf einen Zeitpunkt mit geringer Auslastung verschieben]**: plant den Simulationsstart in Abhängigkeit von der angegebenen Priorität (Niedrig, Mittel, Hoch) mit dem Ziel, die Leistungen von Adobe Campaign zu optimieren.
* **[!UICONTROL Priorität]**: auf die Simulation angewendete Dringlichkeit, die den Ausführungsbeginn entsprechend verschiebt. Wenn die Option **[!UICONTROL Ausführung auf einen Zeitpunkt mit geringer Auslastung verschieben]** aktiviert wurde, wählt der Workflow der Kampagnenvorgänge einen Zeitpunkt mit geringer Aktivität, um die Simulation zu starten.
* **[!UICONTROL SQL-Abfragen im Protokoll speichern]**: Diese Funktion ist erfahrenen Benutzern vorbehalten. Bei Aktivierung wird dem Protokoll ein Tab hinzugefügt, in dem die SQL-Abfragen angezeigt werden. Dies erleichtert die Fehlerbehebung, wenn die Simulation fehlschlägt.

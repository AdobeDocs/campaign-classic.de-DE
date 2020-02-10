---
title: Ausführungsparameter
seo-title: Ausführungsparameter
description: Ausführungsparameter
seo-description: null
page-status-flag: never-activated
uuid: a6549091-0c33-4fe1-adde-de3b285dd456
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: simulating-offers
discoiquuid: 52b5d5a9-10dc-4601-8fe4-962a2334322b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Ausführungsparameter{#execution-settings}

Bei Erstellung einer Simulation haben Sie die Möglichkeit, Ausführungsparameter anzugeben. Auf diese Weise können Sie die Ausführung der Simulation in Abhängigkeit von ihrer Prioritätsstufe auf einen Zeitpunkt mit geringer Auslastung verschieben und die SQL-Abfragen im Protokoll speichern.

These settings can be changed later in the **[!UICONTROL General]** tab of the simulation window.

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]** : Damit können Sie die Simulation auf Grundlage der gewählten Priorität (niedrig, durchschnittlich oder hoch) planen, um die Leistung von Adobe Campaign zu optimieren.
* **[!UICONTROL Priority]** : Dies ist die Stufe, die für die Simulation zur Planung angewendet wird. Wenn die **[!UICONTROL Schedule execution for a time of low activity]** Option aktiviert ist, wählt der Arbeitsablauf für die Kampagnenverarbeitung eine Zeit niedriger Aktivität aus, um die Kampagne zu starten.
* **[!UICONTROL Log SQL queries in the journal]** : Diese Funktion ist nur für erfahrene Benutzer gedacht. Damit können Sie eine Registerkarte zum Protokoll hinzufügen, auf der SQL-Abfragen angezeigt werden, um mögliche Fehlfunktionen zu erkennen, wenn die Simulation mit Fehlern abgeschlossen ist.


---
product: campaign
title: Ausführungsparameter
description: Ausführungsparameter
feature: Interaction, Offers
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: e2dea4a0-9ed8-47b6-a16b-eeee653d2290
TQID: https://experienceleague.adobe.com/k2-e-laXDXtVyBJnoiyKAdNHKiS3nB-t1X1cEaqeudM
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 171
ht-degree: 56%

---

# Ausführungseinstellungen{#execution-settings}



Beim Erstellen einer Simulation können Sie bei Bedarf Ausführungseinstellungen festlegen. Mit diesen Einstellungen können Sie die Simulation in einer Zeit geringer Aktivität ausführen, je nach ihrer Priorität, oder SQL-Abfragen im Protokoll aufzeichnen. Dieser Schritt ist optional.

Eine Änderung dieser Parameter ist im späteren Verlauf im Tab **[!UICONTROL Allgemein]** des Simulationsfensters möglich.

![](assets/offer_simulation_008.png)

* **[!UICONTROL Ausführung auf einen Zeitpunkt mit geringer Auslastung verschieben]**: plant den Simulationsstart in Abhängigkeit von der angegebenen Priorität (Niedrig, Mittel, Hoch) mit dem Ziel, die Performance von Adobe Campaign zu optimieren.
* **[!UICONTROL Priorität]**: auf die Simulation angewendete Dringlichkeit, die den Ausführungsbeginn entsprechend verschiebt. Wenn die Option **[!UICONTROL Ausführung auf einen Zeitpunkt mit geringer Auslastung verschieben]** aktiviert wurde, wählt der Workflow der Kampagnenvorgänge einen Zeitpunkt mit geringer Aktivität, um die Simulation zu starten.
* **[!UICONTROL SQL-Abfragen im Protokoll speichern]** : Diese Funktion ist nur für erfahrene Benutzer. Auf diese Weise können Sie dem Protokoll eine Registerkarte hinzufügen, auf der SQL-Abfragen angezeigt werden, um mögliche Fehlfunktionen zu erkennen, falls die Simulation mit Fehlern abgeschlossen wird.

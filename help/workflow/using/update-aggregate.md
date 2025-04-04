---
product: campaign
title: Aggregat-Update
description: Erfahren Sie mehr über die Workflow-Aktivität "Aggregat-Update".
feature: Workflows
hide: true
hidefromtoc: true
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 100%

---

# Aggregat-Update{#update-aggregate}



Aggregate dienen Berichtszwecken und werden auf Cube-Niveau definiert. Bei der Konfiguration von Aggregaten steht die Registerkarte **[!UICONTROL Workflow]** zur Verfügung.

Diese Vorgehensweise empfiehlt sich insbesondere bei der Verarbeitung von großen Datenvolumen. Aggregate werden automatisch entsprechend den in der dedizierten Workflow-Aktivität definierten Parametern aktualisiert, damit neu abgerufene Daten bei der Kennzahlenberechnung berücksichtigt werden können.

Aggregate werden im entsprechenden Tab des Cubes definiert.

![](assets/s_advuser_cube_agregate_01.png)


In der **[!UICONTROL Aggregat-Update]**-Aktivität besteht die Wahl zwischen einer vollständigen oder teilweisen Aktualisierung.

Standardmäßig wird das Aggregat bei jeder Ausführung vollständig aktualisiert. Bei Auswahl der teilweisen Aktualisierung sind mithilfe des entsprechenden Links die Aktualisierungsbedingungen zu definieren.

![](assets/s_advuser_cube_agregate_05.png)

**Best practices**: Die Verwendung einer **[!UICONTROL Planung]** ermöglicht die Bestimmung der Aktualisierungshäufigkeit des Aggregats.

![](assets/s_advuser_cube_agregate_04.png)

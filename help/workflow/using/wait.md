---
product: campaign
title: Warten
description: Erfahren Sie mehr über die Workflow-Aktivität "Warten".
feature: Workflows
hide: true
exl-id: 4872f756-14d7-4e37-a9cf-b929c77e34ca
TQID: 'https://experienceleague.adobe.com/sQ3GwMFQnhy6eOmFSfMUwT8Z3UE0p4cHLAjr8CjS2FM'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: 3e213ecc670d5a3cb8299c092ccbb5303858327d
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 100%
---
# Warten{#wait}



Eine **Warten**-Aktivität aktiviert ihre Transition nach einer Zeitverzögerung von einigen Sekunden bis zu mehreren Monaten. Diese Aktivität blockiert nicht die Ausführung weiterer Aufgaben. Der Workflow kann Aufgaben parallel zur wartenden Aufgabe ausführen.

Im Editor werden der Titel und die Wartezeit angegeben, wie unten abgebildet:

![](assets/edit_wait.png)

Im Feld **[!UICONTROL Dauer]** können, wenn in den regionalen Parametern des Benutzers nicht anders angegeben, folgende Einheiten verwendet werden:

* Wenn keine regionalen Einstellungen angegeben sind: **s** für Sekunden, **m** für Minuten, **h** für Stunden, **d** für Tage und **y** für Jahre. Sobald die Eingabe validiert wird, wird der Wert in die am besten lesbare Einheit umgewandelt.

  Die Standardeinheit ist **T** für Tag.

* Wenn die regionalen Parameter für Deutschland definiert wurden, sind folgende Einheiten zu verwenden: **s** für Sekunden, **min** für Minuten, **h** für Stunden, **T** für Tage, **M** für Monate und **J** für Jahre. Sobald die Eingabe validiert wird, wird der Wert in die am besten lesbare Einheit umgewandelt. So wurde in oben stehender Abbildung die Eingabe **90s** in **1 min 30 s** umgewandelt.

  Die Standardeinheit ist **T** für Tag.


---
product: campaign
title: Testen
description: Erfahren Sie mehr über die Workflow-Aktivität "Test".
feature: Workflows
hide: true
exl-id: 6f246d56-01c8-43f5-b12b-c40d258b93c8
TQID: 'https://experienceleague.adobe.com/NaQuMb-U9z0U8QZZnmwgPdKaFacOduVvGWDl9P68qR4'
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
source-wordcount: '197'
ht-degree: 100%
---
# Test{#test}



Mit einer Aktivität des Typs **Test** wird die erste Transition aktiviert, die die damit verknüpfte Bedingung erfüllt. Wenn keine Bedingung erfüllt ist und die Option **[!UICONTROL Standardtransition verwenden]** aktiviert ist, wird die Standardtransition aktiviert.

Eine Bedingung ist ein JavaScript-Ausdruck, der als &#39;true&#39; oder &#39;false&#39; ausgewertet werden muss. Um den Ausdruck einzugeben, klicken Sie auf das Symbol rechts neben dem Namen der Bedingung und wählen Sie **[!UICONTROL Bearbeiten…]**.

![](assets/edit_test.png)

Weitere Informationen zu allen zusätzlichen JavaScript-Funktionen und SOAP-Methoden des über Workflow-JavaScript zugänglichen Applikationsservers finden Sie in der [JSAPI-Dokumentation](https://experienceleague.adobe.com/de/tools/campaign-api).

Im Editor können auch direkt Variablen eingegeben werden. Weitere Informationen zum Arbeiten mit Variablen finden Sie in [diesem Abschnitt](javascript-scripts-and-templates.md#variables).

Bedingungen können im Bearbeitungsfenster der Aktivitätseigenschaften hinzugefügt, gelöscht oder geordnet oder über die Transition geändert werden.

Wenn ein Berechnungsergebnis in verschiedenen Bedingungen verwendet werden soll, kann die Berechnung im Initialisierungsskript der Aktivität erfolgen. Das Ergebnis muss dann in einer Variablen der Aufgabe gespeichert werden, damit es für die Bedingungsskripts verfügbar ist (task.vars.xxx).


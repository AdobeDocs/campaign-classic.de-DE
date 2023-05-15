---
product: campaign
title: Test
description: Erfahren Sie mehr über die Workflow-Aktivität "Test".
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 6f246d56-01c8-43f5-b12b-c40d258b93c8
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 100%

---

# Test{#test}



Ein **Test** aktiviert die erste Transition, welche die ihm zugeordneten Bedingungen erfüllt. Wenn keine der Bedingungen &#39;wahr&#39; zurückgibt, wird die **[!UICONTROL Standard-Verzweigung]** aktiviert, vorrausgesetzt, die entsprechende Option wurde angekreuzt.

Eine Bedingung ist ein JavaScript-Ausdruck, der entweder &#39;true&#39; oder &#39;false&#39; zurückgibt. Klicken Sie auf die Schaltfläche rechts in der Bedingungsspalte und wählen Sie die Option **[!UICONTROL Bearbeiten...]** aus.

![](assets/edit_test.png)

Weitere Informationen zu allen zusätzlichen JavaScript-Funktionen und SOAP-Methoden des über Workflow-JavaScript zugänglichen Applikationsservers finden Sie in der [JSAPI-Dokumentation](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=de).

Im Editor können auch direkt Variablen eingegeben werden. Weitere Informationen zum Arbeiten mit Variablen finden Sie in [diesem Abschnitt](javascript-scripts-and-templates.md#variables).

Bedingungen können im Bearbeitungsfenster der Aktivitätseigenschaften hinzugefügt, gelöscht oder geordnet oder über die Transition geändert werden.

Wenn ein Berechnungsergebnis in verschiedenen Bedingungen verwendet werden soll, kann die Berechnung im Initialisierungsscript der Aktivität erfolgen. Das Ergebnis ist dann in einer Variablen der Aufgabe zu speichern, damit es für die Bedingungsscripts verfügbar ist (task.vars.xxx).

---
title: Test
seo-title: Test
description: Test
seo-description: null
page-status-flag: never-activated
uuid: 3522f4ac-3a72-4ff1-b3aa-1b4c283ef2bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 78c70ef4-807d-45d4-ac87-2b741c0ef5cb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f7ed7e59be2cfbde467b0c80d21cfbf52016a2b8
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 93%

---


# Test{#test}

Ein **Test** aktiviert die erste Transition, welche die ihm zugeordneten Bedingungen erfüllt. Wenn keine der Bedingungen &#39;wahr&#39; zurückgibt, wird die **[!UICONTROL Standard-Verzweigung]** aktiviert, vorrausgesetzt, die entsprechende Option wurde angekreuzt.

Eine Bedingung ist ein JavaScript-Ausdruck, der entweder &#39;true&#39; oder &#39;false&#39; zurückgibt. Klicken Sie auf die Schaltfläche rechts in der Bedingungsspalte und wählen Sie die Option **[!UICONTROL Bearbeiten...]** aus.

![](assets/edit_test.png)

Weitere Informationen zu allen zusätzlichen JavaScript-Funktionen und SOAP-Methoden des über Workflow-JavaScript zugänglichen Applikationsservers finden Sie in der [JSAPI-Dokumentation](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).

Im Editor können auch direkt Variablen eingegeben werden. For more  information on how to work with variables, refer to [this section](../../workflow/using/javascript-scripts-and-templates.md#variables).

Bedingungen können im Bearbeitungsfenster der Aktivitätseigenschaften hinzugefügt, gelöscht oder geordnet oder über die Transition geändert werden.

Wenn ein Berechnungsergebnis in verschiedenen Bedingungen verwendet werden soll, kann die Berechnung im Initialisierungsscript der Aktivität erfolgen. Das Ergebnis ist dann in einer Variablen der Aufgabe zu speichern, damit es für die Bedingungsscripts verfügbar ist (task.vars.xxx).

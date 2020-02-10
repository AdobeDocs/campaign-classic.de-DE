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
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Test{#test}

A **Test** type activity activates the first transition that satisfies the condition associated with it. If no condition is satisfied and if the **[!UICONTROL Use the default fork]** option is activated, the default transition will be activated.

A condition is a JavaScript expression that must be evaluated to &#39;true&#39; or &#39;false&#39;. To enter the expression, click the icon to the right of the name of the condition, and then select **[!UICONTROL Edit...]**.

![](assets/edit_test.png)

Weitere Informationen zu allen zusätzlichen JavaScript-Funktionen und SOAP-Methoden des über Workflow-JavaScript zugänglichen Applikationsservers finden Sie in der [JSAPI-Dokumentation](http://docs.campaign.adobe.com/doc/AC/en/jsapi/p-1.html).

Im Editor können auch direkt Variablen eingegeben werden.

Bedingungen können im Bearbeitungsfenster der Aktivitätseigenschaften hinzugefügt, gelöscht oder geordnet oder über die Transition geändert werden.

Wenn ein Berechnungsergebnis in verschiedenen Bedingungen verwendet werden soll, kann die Berechnung im Initialisierungsscript der Aktivität erfolgen. Das Ergebnis ist dann in einer Variablen der Aufgabe zu speichern, damit es für die Bedingungsscripts verfügbar ist (task.vars.xxx).

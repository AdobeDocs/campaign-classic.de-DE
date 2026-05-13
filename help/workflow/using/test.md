---
product: campaign
title: Test
description: Erfahren Sie mehr über die Workflow-Aktivität "Test".
feature: Workflows
hide: true
exl-id: 6f246d56-01c8-43f5-b12b-c40d258b93c8
TQID: https://experienceleague.adobe.com/NaQuMb-U9z0U8QZZnmwgPdKaFacOduVvGWDl9P68qR4
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 198
ht-degree: 59%

---

# Test{#test}



Eine **Test**-Aktivität aktiviert die erste Transition, die die damit verbundene Bedingung erfüllt. Wenn keine Bedingung erfüllt ist und die Option **[!UICONTROL Standardverzweigung verwenden]** aktiviert ist, wird die Standardüberblendung aktiviert.

Eine Bedingung ist ein JavaScript-Ausdruck, der als &#39;true&#39; oder &#39;false&#39; ausgewertet werden muss. Um den Ausdruck einzugeben, klicken Sie auf das Symbol rechts neben dem Namen der Bedingung und wählen Sie **[!UICONTROL Bearbeiten…]**.

![](assets/edit_test.png)

Weitere Informationen zu allen zusätzlichen JavaScript-Funktionen und SOAP-Methoden des über Workflow-JavaScript zugänglichen Applikationsservers finden Sie in der [JSAPI-Dokumentation](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=de).

Im Editor können auch direkt Variablen eingegeben werden. Weitere Informationen zum Arbeiten mit Variablen finden Sie in [diesem Abschnitt](javascript-scripts-and-templates.md#variables).

Bedingungen können im Bearbeitungsfenster der Aktivitätseigenschaften hinzugefügt, gelöscht oder geordnet oder über die Transition geändert werden.

Soll das Ergebnis einer Berechnung unter verschiedenen Bedingungen wiederverwendet werden, so ist es möglich, es im Initialisierungsskript der Aktivität zu berechnen. Das Ergebnis muss in einer Variablen der Aufgabe gespeichert werden, auf die die Bedingungsskripte zugreifen können (task.vars.xxx).

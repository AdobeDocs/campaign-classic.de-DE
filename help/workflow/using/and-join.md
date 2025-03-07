---
product: campaign
title: Und-Verknüpfung
description: Und-Verknüpfung
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 8b6d5c03-e104-4cf0-82ab-a08467e3e478
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: ht
source-wordcount: '191'
ht-degree: 100%

---

# Und-Verknüpfung{#and-join}



Bei einer Und-Verknüpfung wird die ausgehende Transition erst aktiviert, wenn alle eingehenden Transitionen aktiviert wurden, d. h. wenn alle vorherigen Aktivitäten abgeschlossen sind. Dadurch lässt sich sicherstellen, dass gewisse Aktivitäten beendet sind, bevor die Workflow-Ausführung fortgesetzt wird.

Beispielsweise können Sie eine Und-Verknüpfungsaktivität bei der Inhaltserstellung und Automatisierung des Versand verwenden, um sicherzustellen, dass ein Versand erst gestartet wird, wenn die Zielgruppe abgefragt und die Schritte zur Inhaltsaktualisierung abgeschlossen sind. Ein spezielles Anwendungsbeispiel ist in [diesem Abschnitt](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content) verfügbar.

![](assets/and-join-usage.png)

>[!NOTE]
>
>Beachten Sie, dass eingehende Transitionen, die mit verschiedenen Zielgruppenbestimmungsdimensionen konfiguriert sind, nicht mit der Aktivität **[!UICONTROL Und-Verknüpfung]** zusammengeführt werden können.

Die an die ausgehende Transition übermittelte Population entspricht der Hauptmenge, die zuvor aus den eingehenden Transitionen der Aktivität bestimmt wurde.

Die ausgehende Transition kann nur eine der eingehenden Populationen enthalten. Wenn die Hauptmenge nicht bestimmt wurde, wird die an die ausgehende Transition übermittelte Population zufällig ausgewählt.

>[!CAUTION]
>
>Bei Verwendung einer **UND-Verknüpfung** fusionieren die Ereignisvariablen. Wenn eine Variable aber mehrmals definiert wurde, entsteht ein Konflikt und es wird ein unbestimmter Wert ausgegeben. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](javascript-scripts-and-templates.md#event-variables).

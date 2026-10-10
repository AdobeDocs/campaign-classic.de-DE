---
product: campaign
title: Und-Verknüpfung
description: Und-Verknüpfung
feature: Workflows
hide: true
exl-id: 8b6d5c03-e104-4cf0-82ab-a08467e3e478
TQID: 'https://experienceleague.adobe.com/L6SmrK6xHkRqZI69OepbB4drLPfrX-cmvi6h6su3LYk'
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
# Und-Verknüpfung{#and-join}



Bei einer Verknüpfung wird die ausgehende Transition erst aktiviert, wenn alle eingehenden Transitionen aktiviert wurden, d. h. wenn alle vorherigen Aktivitäten abgeschlossen sind. Auf diese Weise können Sie sicherstellen, dass bestimmte Aktivitäten abgeschlossen sind, bevor Sie mit der Ausführung des Workflows fortfahren.

Beispielsweise können Sie eine Und-Verknüpfungsaktivität bei der Inhaltserstellung und Automatisierung des Versand verwenden, um sicherzustellen, dass ein Versand erst gestartet wird, wenn die Zielgruppe abgefragt und die Schritte zur Inhaltsaktualisierung abgeschlossen sind. Ein spezielles Anwendungsbeispiel ist in [diesem Abschnitt](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content) verfügbar.

![](assets/and-join-usage.png)

>[!NOTE]
>
>Beachten Sie, dass eingehende Transitionen, die mit verschiedenen Zielgruppendimensionen konfiguriert sind, nicht mit der Aktivität **[!UICONTROL Und-Verknüpfung]** zusammengeführt werden können.

Die an die ausgehende Transition übermittelte Population entspricht der Hauptmenge, die zuvor aus den eingehenden Transitionen der Aktivität bestimmt wurde.

Die ausgehende Transition darf nur eine der Populationen der eingehenden Transition enthalten. Wenn die Aktivität nicht bestimmt wurde, wird für die ausgehende Transition zufällig eine der eingehenden Populationen ausgewählt.

>[!CAUTION]
>
>Bei Verwendung einer **UND-Verknüpfung** werden die Ereignisvariablen zusammengeführt. Wenn eine Variable aber mehrmals definiert wurde, entsteht ein Konflikt und es wird ein unbestimmter Wert ausgegeben. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](javascript-scripts-and-templates.md#event-variables).

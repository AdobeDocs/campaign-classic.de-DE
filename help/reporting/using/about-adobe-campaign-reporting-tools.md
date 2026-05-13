---
product: campaign
title: Über Reporting-Tools in Adobe Campaign
description: Analysieren des Erfolgs Ihrer Kampagnen in nativen oder benutzerdefinierten Berichten
feature: Reporting, Monitoring
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
exl-id: 1ef30004-e1b0-4dde-8104-0ee9e8aa9d8b
TQID: https://experienceleague.adobe.com/4D-bCeMQakNjr7OXhiZ1u0Sfp5MZWwzZzHtykBfFzZ8
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616a
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 362
ht-degree: 50%

---

# Erste Schritte mit Reporting {#about-adobe-campaign-reporting-tools}



Zusätzlich zu [ integrierten Berichten ](../../reporting/using/about-campaign-built-in-reports.md) Sie mit Adobe Campaign Berichte in verschiedenen Kontexten und für unterschiedliche Anforderungen erstellen. Die Grundsätze der Verwendung und die Implementierungsmodi werden in diesem Dokument beschrieben.

Adobe Campaign ist kein spezielles Reporting-Tool: In Adobe Campaign erstellte Berichte ermöglichen es Ihnen hauptsächlich, aggregierte Daten anzuzeigen. Adobe Campaign-Berichte, die Daten analysieren und darstellen, sind nicht für Datenbankexporte konzipiert.

Der Export von Daten aus Adobe Campaign ist mithilfe der Datenexport-Aktivität im Rahmen eines Workflows möglich. Weiterführende Informationen finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/action-activities.html?lang=de){target="_blank"}.

Adobe Campaign bietet verschiedene Reporting-Tools:

1. **Native Berichte**: Adobe Campaign bietet eine Berichtserie über Sendungen, Kampagnen, Plattformaktivitäten, optionale Funktionen usw. Diese Berichte stehen über die verschiedenen Funktionen zur Verfügung, auf die sie sich beziehen. Sie können an Ihre individuellen Bedürfnisse angepasst werden.

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../reporting/using/about-campaign-built-in-reports.md).

1. **Deskriptive Datenanalyse**: Adobe Campaign bietet ein visuelles Tool zur Erstellung von Statistiken zu den in der Datenbank gespeicherten Daten. Mit einem speziellen Assistenten können Sie anschauliche Analyseberichte erstellen und deren Inhalt und Layout an Ihre Bedürfnisse anpassen.

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../reporting/using/about-descriptive-analysis.md).

1. **Personalisierte Berichte**: Mit Adobe Campaign können Sie Berichte zu den Daten in der Datenbank erstellen. Sobald diese erstellt wurden, werden sie in den entsprechenden Kontexten verfügbar gemacht.

   Je nach Komplexität der Abfragen, Berechnungen und Volumina können die in diesen Berichten analysierten Daten über eine Abfrage gesammelt und in einer Liste (Workflow vom Typ „Daten-Management„) oder einem Cube (unter Verwendung der Marketing-Analyse) voraggregiert werden. Sie wird in Form einer Pivot-Tabelle oder einer Gruppenliste angezeigt.

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../reporting/using/about-reports-creation-in-campaign.md).

1. **Analyseberichte**: Explorative Datenanalyse unter Verwendung von Marketing Analytics.

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../reporting/using/ac-cubes.md).

>[!CAUTION]
>
>Um sicherzustellen, dass der Bericht korrekt angezeigt, genutzt und exportiert werden kann, darf dieser nicht mehr als 1000 Zeilen enthalten.

---
title: Über Reporting-Tools in Adobe Campaign
description: Analysieren Sie den Erfolg Ihrer Kampagnen in integrierten oder benutzerspezifischen Berichten.
page-status-flag: never-activated
uuid: a8122c9e-60ba-4ef7-bc63-05d6cf16fad0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: reporting-in-adobe-campaign
discoiquuid: c5dad561-0708-4b7a-84a0-eb00beff58c6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: eccf0e9899426c2517748c7a72611ff098291cd2
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 96%

---


# Erste Schritte mit Reporting {#about-adobe-campaign-reporting-tools}

Neben den [nativen Berichten](../../reporting/using/about-campaign-built-in-reports.md) ermöglicht es Adobe Campaign, Berichte in unterschiedlichen Kontexten und den verschiedenen Bedürfnissen entsprechend zu erstellen. Die Anwendungsprinzipien und ihre Umsetzung werden im vorliegenden Dokument beschrieben.

Adobe Campaign ist keine auf Reporting spezialisierte Anwendung: Die hier erstellten Berichte dienen hauptsächlich der Visualisierung aggregierter Daten. Adobe-Campaign-Berichte erlauben somit die Darstellung und Analyse von Daten, sind aber nicht zum Export dieser aus der Datenbank geeignet.

Der Export von Daten aus Adobe Campaign ist mithilfe der Datenexport-Aktivität im Rahmen eines Workflows möglich. Lesen Sie hierzu [diesen Abschnitt](../../workflow/using/about-action-activities.md).

Adobe Campaign bietet verschiedene Reporting-Tools:

1. **Native Berichte**: Adobe Campaign bietet eine Berichtserie über Sendungen, Kampagnen, Plattform-Aktivitäten, optionale Funktionalitäten und mehr. Diese Berichte sind jeweils über die Funktionalitäten verfügbar, auf die sie sich beziehen. Sie können Ihren Bedürfnissen entsprechend angepasst werden.

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../reporting/using/about-campaign-built-in-reports.md).

1. **Deskriptive Datenanalyse**: Werkzeug, das die Erzeugung fachbezogener Statistiken über die in der Datenbank enthaltenen Daten ermöglicht. Sie können Berichte mit deskriptiven Analysen über einen dedizierten Assistenten erstellen und ihren Inhalt sowie ihre Darstellung Ihren Bedürfnissen entsprechend definieren.

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../reporting/using/about-descriptive-analysis.md).

1. **Benutzerdefinierte Berichte**: Berichte über die in Ihrer Datenbank enthaltenen Daten. Nach ihrer Erstellung sind die Berichte in den jeweils zutreffenden Kontexten zugänglich.

   Je nach Komplexität der Abfragen und Berechnungen sowie der bewegten Datenmenge werden die in den Berichten zu analysierenden Daten über eine Abfrage gesammelt und in einer Liste (Workflow vom Typ &quot;Data Management&quot;) oder einem Cube (unter Verwendung der Option Marketing Analytics) voraggregiert. Sie werden in Form einer Pivot-Tabelle oder einer Liste mit Gruppierung angezeigt.

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../reporting/using/about-reports-creation-in-campaign.md).

1. **Analyseberichte**: Explorative Datenanalyse unter Verwendung von Marketing Analytics.

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../reporting/using/about-cubes.md).

>[!CAUTION]
>
>Um sicherzustellen, dass der Bericht korrekt angezeigt, genutzt und exportiert werden kann, darf dieser nicht mehr als 1000 Zeilen enthalten.
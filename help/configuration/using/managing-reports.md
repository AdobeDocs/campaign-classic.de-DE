---
product: campaign
title: Berichte verwalten
description: Berichte verwalten
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
source-git-commit: 3997412f14666fa61bf71d0f0a0653f5cc042e19
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 3%

---

# Berichte verwalten{#managing-reports}

![](../../assets/common.svg)

Berichte, die auf einem Schema basieren, das speziell für die Standard-Adobe Campaign-Empfänger bestimmt ist (nm:recipient oder schema verknüpft), müssen neu entwickelt werden, um die Daten der benutzerdefinierten Tabelle und deren über das Zielgruppen-Mapping verknüpften Tabellen zu berücksichtigen (siehe [Zielgruppen-Mapping](../../configuration/using/target-mapping.md) Abschnitt).

Informationen zum Erstellen neuer Berichte finden Sie unter [diesem Abschnitt](../../reporting/using/about-reports-creation-in-campaign.md).

In einigen Fällen müssen Sie auch neue Cubes einrichten, die speziell für diese Tabellen gelten. Cubes werden im Abschnitt [diesem Abschnitt](../../reporting/using/about-cubes.md).

Folgende Berichte sind betroffen:

* **[!UICONTROL Verfolgung aktueller Vorschläge]** (recentPropositions): Echtzeitverfolgung der Vorschläge.
* **[!UICONTROL Öffnungsverteilung]** (opensByUserAgent): nach Benutzersoftware aufgeschlüsselte Öffnungen.
* **[!UICONTROL Statistiken zu Teilungsaktivitäten]** (forwardActivities): Analyse von Teilungen, Öffnungen und Abonnements nach Zeiträumen.
* **[!UICONTROL Trackingindikatoren]** (mobileAppDeliveryFeedback): Trackingindikatoren für einen Versand in einer Mobile App.
* **[!UICONTROL Angebotsanalyse]** (offerAnalysis): Angebotsanalyse nach Datum und Kanal.
* **[!UICONTROL Reaktionsrate]** (mobileAppDistribution): Reaktionsrate der letzten Sendungen.
* **[!UICONTROL Abonnementverteilung]** (mobileAppDistribution): Verteilung der aktiven Abonnements nach Mobile Apps.

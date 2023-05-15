---
product: campaign
title: Berichte verwalten
description: Berichte verwalten
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 3%

---

# Berichte verwalten{#managing-reports}



Berichte, die auf einem Schema basieren, das speziell für die Standard-Adobe Campaign-Empfänger bestimmt ist (nm:recipient oder schema verknüpft), müssen neu entwickelt werden, um die Daten der benutzerdefinierten Tabelle und deren über das Zielgruppen-Mapping verknüpften Tabellen zu berücksichtigen (siehe [Zielgruppen-Mapping](../../configuration/using/target-mapping.md) Abschnitt).

Informationen zum Erstellen neuer Berichte finden Sie unter [diesem Abschnitt](../../reporting/using/about-reports-creation-in-campaign.md).

In einigen Fällen müssen Sie auch neue Cubes einrichten, die speziell für diese Tabellen gelten. Cubes werden im Abschnitt [diesem Abschnitt](../../reporting/using/ac-cubes.md).

Folgende Berichte sind betroffen:

* **[!UICONTROL Verfolgung aktueller Vorschläge]** (recentPropositions): Echtzeitverfolgung der Vorschläge.
* **[!UICONTROL Öffnungsverteilung]** (opensByUserAgent): nach Benutzersoftware aufgeschlüsselte Öffnungen.
* **[!UICONTROL Statistiken zu Teilungsaktivitäten]** (forwardActivities): Analyse von Teilungen, Öffnungen und Abonnements nach Zeiträumen.
* **[!UICONTROL Trackingindikatoren]** (mobileAppDeliveryFeedback): Trackingindikatoren für einen Versand in einer Mobile App.
* **[!UICONTROL Angebotsanalyse]** (offerAnalysis): Angebotsanalyse nach Datum und Kanal.
* **[!UICONTROL Reaktionsrate]** (mobileAppDistribution): Reaktionsrate der letzten Sendungen.
* **[!UICONTROL Abonnementverteilung]** (mobileAppDistribution): Verteilung der aktiven Abonnements nach Mobile Apps.

---
product: campaign
title: Berichte verwalten
description: Berichte verwalten
feature: Reporting, Configuration
role: Data Engineer, Developer
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 6%

---

# Berichte verwalten{#managing-reports}



Berichte, die auf einem Schema basieren, das speziell für die Standard-Adobe Campaign-Empfänger bestimmt ist (nm:recipient oder schema verknüpft), müssen neu entwickelt werden, um die Daten der benutzerdefinierten Tabelle und deren über das Zielgruppen-Mapping verknüpften Tabellen zu berücksichtigen (siehe [Zielgruppen-Mapping](../../configuration/using/target-mapping.md) Abschnitt).

Informationen zum Erstellen neuer Berichte finden Sie unter [diesem Abschnitt](../../reporting/using/about-reports-creation-in-campaign.md).

In einigen Fällen müssen Sie auch neue Cubes einrichten, die speziell für diese Tabellen gelten. Cubes werden im Abschnitt [diesem Abschnitt](../../reporting/using/ac-cubes.md).

Folgende Berichte sind betroffen:

* **[!UICONTROL Verfolgung aktueller Vorschläge]** (recentPropositions): Echtzeitverfolgung von Vorschlägen.
* **[!UICONTROL Öffnungsverteilung]** (opensByUserAgent): öffnet sich je nach Benutzersoftware aufgeschlüsselt.
* **[!UICONTROL Statistiken zu Teilungsaktivitäten]** (forwardActivities): Analyse der Teilungsaktivitäten, Öffnungen und Abonnements nach Zeiträumen.
* **[!UICONTROL Trackingindikatoren]** (mobileAppDeliveryFeedback): Trackingindikatoren für einen Versand in einer Mobile App.
* **[!UICONTROL Angebotsanalyse]** (offerAnalysis): Angebotsanalyse nach Datum und Kanal.
* **[!UICONTROL Reaktionsrate]** (mobileAppDistribution): Reaktionsrate der letzten Sendungen.
* **[!UICONTROL Abonnementverteilung]** (mobileAppDistribution): Verteilung der aktiven Abonnements nach Mobile Apps.

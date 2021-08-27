---
product: campaign
title: Verwalten von Berichten
description: Verwalten von Berichten
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 3%

---

# Verwalten von Berichten{#managing-reports}

![](../../assets/v7-only.svg)

Berichte, die auf einem Schema basieren, das speziell für die Standard-Adobe Campaign-Empfänger gilt (nm:recipient oder schema linked), müssen neu entwickelt werden, um die Daten der benutzerdefinierten Tabelle und deren über das Zielgruppen-Mapping verknüpften Tabellen zu berücksichtigen (siehe Abschnitt [Zielgruppen-Mapping](../../configuration/using/target-mapping.md) ).

Informationen zum Erstellen neuer Berichte finden Sie in [diesem Abschnitt](../../reporting/using/about-reports-creation-in-campaign.md).

In einigen Fällen müssen Sie auch neue Cubes einrichten, die speziell für diese Tabellen gelten. Cubes werden in [diesem Abschnitt](../../reporting/using/about-cubes.md) beschrieben.

Folgende Berichte sind betroffen:

* **[!UICONTROL Verfolgung aktueller Vorschläge]**  (recentPropositions): Echtzeitverfolgung der Vorschläge.
* **[!UICONTROL Öffnungsverteilung]**  (opensByUserAgent): nach Benutzersoftware aufgeschlüsselte Öffnungen.
* **[!UICONTROL Statistiken zu Teilungsaktivitäten]**  (forwardActivities): Analyse von Teilungen, Öffnungen und Abonnements nach Zeiträumen.
* **[!UICONTROL Trackingindikatoren]**  (mobileAppDeliveryFeedback): Trackingindikatoren für einen Versand in einer Mobile App.
* **[!UICONTROL Angebotsanalyse]**  (offerAnalysis): Angebotsanalyse nach Datum und Kanal.
* **[!UICONTROL Reaktionsrate]**  (mobileAppDistribution): Reaktionsrate der letzten Sendungen.
* **[!UICONTROL Abonnementverteilung]**  (mobileAppDistribution): Verteilung der aktiven Abonnements nach Mobile Apps.

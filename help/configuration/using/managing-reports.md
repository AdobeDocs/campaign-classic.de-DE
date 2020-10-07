---
title: Verwalten von Berichten
seo-title: Verwalten von Berichten
description: Verwalten von Berichten
seo-description: null
page-status-flag: never-activated
uuid: 3b8e6f11-4cbd-450e-871b-50fd0ead96db
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 21777423-0c8a-4bb1-b210-972f660648bd
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 4%

---


# Verwalten von Berichten{#managing-reports}

Berichte, die auf einem Schema basieren, das für die standardmäßigen Adobe Campaign-Empfänger spezifisch ist (nm:Empfänger oder verknüpftes Schema), müssen neu entwickelt werden, um die Daten aus der benutzerspezifischen Tabelle und deren über das Zielgruppen-Mapping verknüpften Tabellen zu berücksichtigen (siehe Abschnitt [Zielgruppen-Mapping](../../configuration/using/target-mapping.md) ).

Informationen zum Erstellen neuer Berichte finden Sie in [diesem Abschnitt](../../reporting/using/about-reports-creation-in-campaign.md).

In einigen Fällen müssen Sie auch neue Cuben einführen, die sich speziell auf diese Tabellen beziehen. Cubes are detailed in [this section](../../reporting/using/about-cubes.md).

Folgende Berichte sind betroffen:

* **[!UICONTROL Nachverfolgung]** aktueller Vorschläge (jüngste Vorschläge): Echtzeitpropositionserfassung.
* **[!UICONTROL Aufschlüsselung von &quot;openByUserAgent&quot;]** : wird nach Benutzersoftware aufgeschlüsselt angezeigt.
* **[!UICONTROL Statistik der Freigabeaktivitäten]** (forwardActivities): analyse der Freigabe von Aktivitäten, Öffnen und Abonnements pro Zeitraum.
* **[!UICONTROL Rückverfolgungsindikatoren]** (mobileAppDeliveryFeedback): Tracking-Indikatoren für einen Versand in einer Mobilanwendung.
* **[!UICONTROL Angebot-Analyse]** (offerAnalysis): analyse des Angebots nach Datum und Kanal.
* **[!UICONTROL Reaktivitätsrate]** (mobileAppDistribution): Reaktivitätsrate für die neuesten Versand.
* **[!UICONTROL Aufschlüsselung von Abonnements]** (mobileAppDistribution): Aufschlüsselung aktiver Abonnement nach Mobilanwendung.


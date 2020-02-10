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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Verwalten von Berichten{#managing-reports}

Berichte, die auf einem Schema basieren, das spezifisch für die standardmäßigen Adobe Campaign-Empfänger ist (nm:empfänger oder Schema verknüpft), müssen neu entwickelt werden, um die Daten aus der benutzerdefinierten Tabelle und deren Tabellen zu berücksichtigen, die über die Zielzuordnung verknüpft sind (siehe Abschnitt [Target-Zuordnung](../../configuration/using/target-mapping.md) ).

Informationen zum Erstellen neuer Berichte finden Sie in [diesem Abschnitt](../../reporting/using/about-reports-creation-in-campaign.md).

In einigen Fällen müssen Sie auch neue Würfel einsetzen, die spezifisch für diese Tabellen sind. Cubes are detailed in [this section](../../reporting/using/about-cubes.md).

Folgende Berichte sind betroffen:

* **[!UICONTROL Recent proposition tracking]** (jüngste Vorschläge): Echtzeitpropositionserfassung.
* **[!UICONTROL Breakdown of opens]** (openByUserAgent): wird nach Benutzersoftware aufgeschlüsselt angezeigt.
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities): Analyse von Freigabeaktivitäten, -öffnen und -abonnements pro Zeitraum.
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback): Tracking-Indikatoren für eine Bereitstellung in einer mobilen Anwendung.
* **[!UICONTROL Offer analysis]** (offerAnalysis): Angebotsanalyse nach Datum und Kanal.
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution): Reaktivitätsrate für die letzten Auslieferungen.
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution): Aufschlüsselung aktiver Abonnements nach Mobilanwendung.


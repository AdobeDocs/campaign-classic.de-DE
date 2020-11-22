---
solution: Campaign Classic
product: campaign
title: Verwalten von Berichten
description: Verwalten von Berichten
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 3%

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


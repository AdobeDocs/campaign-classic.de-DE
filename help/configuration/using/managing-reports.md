---
product: campaign
title: Verwalten von Berichten
description: Verwalten von Berichten
feature: Reporting, Configuration
role: Developer
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 8%

---

# Verwalten von Berichten{#managing-reports}



Berichte, die auf einem Schema basieren, das spezifisch für die Standardempfänger von Adobe Campaign ist (nm:recipient oder verknüpftes Schema), müssen neu entwickelt werden, um die Daten aus der benutzerdefinierten Tabelle und ihren über das Zielgruppen-Mapping verknüpften Tabellen zu berücksichtigen (siehe Abschnitt [Zielgruppen-Mapping](../../configuration/using/target-mapping.md)).

Informationen zum Erstellen neuer Berichte finden Sie [diesem Abschnitt](../../reporting/using/about-reports-creation-in-campaign.md).

In einigen Fällen müssen Sie auch neue Cubes, die für diese Tabellen spezifisch sind, einfügen. Cubes werden in [&#x200B; Abschnitt &#x200B;](../../reporting/using/ac-cubes.md).

Die folgenden Berichte sind betroffen:

* **[!UICONTROL Letzte Vorschlagsverfolgung]** (aktuelle Vorschläge): Echtzeit-Vorschlagsverfolgung.
* **[!UICONTROL Aufschlüsselung der Öffnungen]** (opensByUserAgent): Öffnungen, aufgeschlüsselt nach Benutzersoftware.
* **[!UICONTROL Statistiken der Freigabeaktivitäten]** (forwardActivities): Analyse der Freigabeaktivitäten, Öffnungen und Abonnements nach Zeitraum.
* **[!UICONTROL Tracking-Indikatoren]** (mobileAppDeliveryFeedback): Tracking-Indikatoren für einen Versand in einer Mobile App.
* **[!UICONTROL Angebotsanalyse]** (offerAnalysis): Angebotsanalyse nach Datum und Kanal.
* **[!UICONTROL Reaktionsrate]** (mobileAppDistribution): Reaktionsrate der letzten Sendungen.
* **[!UICONTROL Aufschlüsselung der Abonnements]** (mobileAppDistribution): Aufschlüsselung der aktiven Abonnements nach Mobile App.

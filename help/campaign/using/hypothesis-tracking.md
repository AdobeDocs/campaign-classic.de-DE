---
title: Hypothesenverfolgung
seo-title: Hypothesenverfolgung
description: Hypothesenverfolgung
seo-description: null
page-status-flag: never-activated
uuid: cb949a9d-8bbe-446b-b5b4-22234a91a68b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: 4452bfc6-9ac4-4d81-a63c-879a163c13ee
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# Hypothesenverfolgung{#hypothesis-tracking}

Das Ergebnis der Hypothesenberechnungen kann auf unterschiedlichen Ebenen der Adobe-Campaign-Plattform eingesehen werden. So sind die von der Hypothese berechneten Indikatoren und die Empfängerreaktionen in der Messhypothese selbst verfügbar; sie werden darüber hinaus auch in den betreffenden Kampagnen und Sendungen in Form von Hypothesenberichten anschaulich dargestellt.

## Hypothesenergebnisse {#hypothesis-results}

### Indicators {#indicators}

Nachdem die Hypothese berechnet wurde, werden mehrere Messindikatoren automatisch aktualisiert. Diese sind auf der **[!UICONTROL General]** Registerkarte der Hypothese verfügbar.

![](assets/response_hypothesis_delivery_example_010.png)

Es handelt sich um folgende Indikatoren:

* **Reagierende Kontakte**: Anzahl der kontaktierten Individuen, die der Abfrage der Hypothese entsprechen.
* **Reaktionsrate Kontakte**: Anzahl reagierender Kontakte/Kontakte des Versands insgesamt.
* **Reagierende Individuen der Kontrollgruppe**: Anzahl der der Hypothese entsprechenden Individuen der Kontrollgruppe.
* **Reaktionsrate Kontrollgruppe**: Anzahl von reagierenden Individuen der Kontrollgruppe/Individuen der Kontrollgruppe des Versands insgesamt.
* **Anzahl Reaktionen**: Anzahl der Datensätze in der Tabelle, die die Beziehung zwischen Individuen, Hypothese und Transaktionstabelle enthält.

Für die vollständige Liste der Indikatoren klicken Sie auf den **[!UICONTROL Display the list]** Link:

![](assets/response_hypothesis_indicators_002.png)

Folgende Informationen werden von den Indikatoren bereitgestellt:

* **Gesamtumsatz Kontakte**: Summe der durch die kontaktierten Individuen generierten Einnahmen.
* **Gesamtumsatz Kontrollgruppe**: Summe der durch die Anzahl der Individuen der Kontrollgruppe generierten Einnahmen.
* **Durchschnittlicher Umsatz Kontakte**: Summe Einnahmen/Anzahl Kontakte.
* **Durchschnittlicher Umsatz Kontrollgruppe**: Summe Einnahmen/Anzahl Individuen der Kontrollgruppe.
* **Gesamtspanne Kontakte**: Insgesamt durch die kontaktierten Individuen generierte Spanne.
* **Gesamtspanne Kontrollgruppe**: Insgesamt durch die Individuen der Kontrollgruppe generierte Spanne.
* **Durchschnittliche Spanne Kontakte**: Gesamtspanne/Anzahl Kontakte.
* **Durchschnittliche Spanne Kontrollgruppe**: Gesamtspanne/Anzahl Individuen der Kontrollgruppe.
* **Umsatzzuwachs**: (Durchschnittlicher Umsatz der Kontakte - Durchschnittlicher Umsatz der Individuen in der Kontrollgruppe) x Anzahl Kontakte.
* **Zusätzliche Spanne**: (Durchschnittliche Spanne der Kontakte - Durchschnittliche Spanne der Individuen in der Kontrollgruppe) / Anzahl Kontakte.
* **Durchschnittliche Kosten Kontakte**: Berechnete Kosten des Versands / Anzahl Kontakte.
* **ROI**: Berechnete Kosten des Versands / Gesamtspanne Kontakte.
* **Effektiver ROI**: Berechnete Kosten des Versands / Zusätzliche Spanne.
* **Signifikanz**: enthält Werte von 0 bis 3, die die jeweilige Signifikanz der Kampagne ausdrücken.

### Reaktionen {#reactions}

You can view recipients&#39; reactions to the hypotheses via the **[!UICONTROL Reactions]** tab.

1. Once hypothesis calculation is complete, go to the **[!UICONTROL Campaign management > Measurement hypotheses]** node of the Adobe Campaign tree.
1. Select the desired hypothesis and click the **[!UICONTROL Reactions]** tab to view the list of recipients likely to purchase something following the marketing campaign.

   ![](assets/response_hypothesis_reactions_001.png)

## Berichte {#reports}

Mit der **[!UICONTROL Hypothesis report]** können Sie die Ergebnisse der Hypothesen anzeigen, die für Kampagnen und Lieferungen durchgeführt wurden. Dieser Bericht enthält die anhand der Hypothese berechneten Indikatoren (weitere Informationen finden Sie unter [Indikatoren](#indicators)).

* **Auf Kampagnenebene**: Klicken Sie auf den **[!UICONTROL Reports]** Link der jeweiligen Kampagne und wählen Sie die **[!UICONTROL Hypothesis report]**. Dieser Bericht enthält eine Liste der Kampagnenlieferungen und die für jede Lieferung berechneten Hypothesen.

   ![](assets/response_hypothesis_campaign_report_001.png)

* **Auf Zustellungsebene**: Um auf den Bericht zuzugreifen, öffnen Sie die entsprechende Bereitstellung, klicken Sie auf die **[!UICONTROL Reports]** Registerkarte **[!UICONTROL Summary]** und wählen Sie die **[!UICONTROL Hypothesis report]**. Wenn mehrere Hypothesen für dieselbe Lieferung berechnet wurden, enthält der Bericht alle Hypothesen.

   ![](assets/response_hypothesis_delivery_report_001.png)

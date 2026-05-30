---
product: campaign
title: Tracking von Hypothesen
description: Erfahren Sie, wie Sie Hypothesen in Campaign Response Manager verfolgen.
feature: Campaigns, Monitoring, Reporting
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 1dc6d03b-698c-4750-9563-0676fcd185df
TQID: https://experienceleague.adobe.com/MKJg0M0gWR9XvgsRkXvZqAkNx2IzLg24l9c4nG26r20
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616a
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: c2be0313-b3ae-45e0-b454-d20bf54b23f2
subfeature_v2: id: d72afaa0-c842-48c8-9a3c-51b7911edc1b
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 487
ht-degree: 81%

---

# Hypothesenverfolgung{#hypothesis-tracking}



Das Ergebnis der Hypothesenberechnungen kann auf unterschiedlichen Ebenen der Adobe Campaign-Plattform eingesehen werden. So sind die von der Hypothese berechneten Indikatoren und die Reaktionen der Zielpopulation in der Messhypothese selbst verfügbar; sie werden darüber hinaus auch in den betreffenden Kampagnen und Sendungen in Form von Hypothesenberichten anschaulich dargestellt.

## Hypothesenergebnisse {#hypothesis-results}

### Indikatoren {#indicators}

Nach der Berechnung der Hypothese werden mehrere Messindikatoren automatisch aktualisiert. Diese sind auf der Registerkarte **[!UICONTROL Allgemein]** der Hypothese verfügbar.

![](assets/response_hypothesis_delivery_example_010.png)

Es handelt sich um folgende Indikatoren:

* **Reagierende Kontakte**: Anzahl der kontaktierten Individuen, die der Abfrage der Hypothese entsprechen.
* **Reaktionsrate Kontakte**: Anzahl reagierender Kontakte/Kontakte des Versands insgesamt.
* **Reagierende Individuen der Kontrollgruppe**: Anzahl der der Hypothese entsprechenden Individuen der Kontrollgruppe.
* **Reaktionsrate Kontrollgruppe**: Anzahl von reagierenden Individuen der Kontrollgruppe/Individuen der Kontrollgruppe des Versands insgesamt.
* **Anzahl Reaktionen**: Anzahl der Datensätze in der Tabelle, die die Beziehung zwischen Individuen, Hypothese und Transaktionstabelle enthält.

Klicken Sie auf den Link **[!UICONTROL Liste anzeigen]**, um eine Liste aller Indikatoren anzuzeigen:

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
* **Zusätzlicher Umsatz**: (Durchschnittlicher Umsatz der kontaktierten Personen – durchschnittlicher Umsatz der Kontrollgruppe)&#42;Anzahl der kontaktierten Personen
* **Zusätzliche Spanne**: (Durchschnittliche Spanne der Kontakte - Durchschnittliche Spanne der Individuen in der Kontrollgruppe) / Anzahl Kontakte.
* **Durchschnittliche Kosten Kontakte**: Berechnete Kosten des Versands / Anzahl Kontakte.
* **ROI**: Berechnete Kosten des Versands / Gesamtspanne Kontakte.
* **Effektiver ROI**: Berechnete Kosten des Versands / Zusätzliche Spanne.
* **Signifikanz**: enthält Werte von 0 bis 3, die die jeweilige Signifikanz der Kampagne ausdrücken.

### Reaktionen {#reactions}

Sie können die durch die Hypothesen generierten Empfängerreaktionen im Tab **[!UICONTROL Reaktionen]** einsehen.

1. Gehen Sie nach Abschluss der Hypothesenberechnung in den Knoten **[!UICONTROL Kampagnenverwaltung > Messhypothesen]** des Adobe Campaign-Navigationsbaums.
1. Wählen Sie die gewünschte Hypothese aus der Liste aus und klicken Sie auf den Tab **[!UICONTROL Reaktionen]**, um die Liste der Empfänger anzuzeigen, die im Anschluss an die Marketing-Kampagne möglicherweise einen Kauf tätigen.

   ![](assets/response_hypothesis_reactions_001.png)

## Berichte {#reports}

Im **[!UICONTROL Hypothesenbericht]** können Sie die Ergebnisse der Hypothesen zu Kampagnen und Sendungen einsehen. Dieser Bericht enthält die von der Hypothese berechneten Indikatoren (weitere Informationen finden Sie unter [Indikatoren](#indicators)).

* **Auf Kampagnenebene**: Klicken Sie auf den Link **[!UICONTROL Berichte]** der entsprechenden Kampagne und wählen Sie den **[!UICONTROL Hypothesenbericht]**. Dieser Bericht enthält die Liste der in Campaign durchgeführten Sendungen sowie die für jeden Versand berechneten Hypothesen.

  ![](assets/response_hypothesis_campaign_report_001.png)

* **Auf Versandebene**: Um auf den Bericht zuzugreifen, öffnen Sie den betreffenden Versand, klicken Sie auf der Registerkarte **[!UICONTROL Zusammenfassung]** auf **[!UICONTROL Berichte]** und wählen Sie den **[!UICONTROL Hypothesenbericht]**. Wenn mehrere Hypothesen für denselben Versand berechnet wurden, enthält der Bericht alle Hypothesen.

  ![](assets/response_hypothesis_delivery_report_001.png)

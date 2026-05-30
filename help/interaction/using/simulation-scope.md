---
product: campaign
title: Simulationsperimeter
description: Simulationsperimeter
feature: Interaction, Offers
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: 4f6b3de2-3fdf-441d-925d-476e20e75c6f
TQID: https://experienceleague.adobe.com/mZ618bV3lzbXS09MXBXJxM5RizvMWl6lEgw0Bwb2bGI
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
feature_v2:
  - id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
subfeature_v2: []
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 250
ht-degree: 48%

---

# Simulationsumfang{#simulation-scope}



## Perimeter konfigurieren {#definition-of-the-scope}

Die Perimeterkonfiguration erfolgt im Tab **[!UICONTROL Perimeter]**.

Folgende Felder müssen zwingend ausgefüllt werden:

* Angebotsumgebung oder -kategorie
* Platzierung
* Kontaktdatum. Angebote, die am Kontaktdatum nicht infrage kommen, werden nicht berücksichtigt.
* Zielpopulation.

  Wenn kein Zielgruppenfilter angegeben wird, wird die gesamte Empfängertabelle in der Simulation berücksichtigt.

* Anzahl an zu simulierenden Vorschlägen pro Kontakt.

  Der Empfänger erhält so viele Vorschläge. Wenn Sie beispielsweise 5 eingeben, erhält jeder Empfänger maximal 5 Angebotsvorschläge.

  ![](assets/offer_simulation_009.png)

Zur weiteren Feinabstimmung der in der Simulation zu berücksichtigenden Angebote können Themen angegeben werden. Diese müssen zuvor auf Ebene der Kategorie definiert werden.

Sie können die Simulation auch für alle Angebote oder nur für die Online-Angebote durchführen. Einige Filter ermöglichen es Ihnen, Ihre Auswahl bei Bedarf zu ändern.

>[!NOTE]
>
>Sie müssen ein Kontaktdatum angeben. Auf diese Weise kann das Interaction-Modul die Angebote in der ausgewählten Umgebung oder Kategorie sortieren. Wenn kein Datum konfiguriert ist, gibt die Simulation einen Fehler aus.

## Berichtsachsen hinzufügen {#adding-reporting-axes}

Im Tab **[!UICONTROL Berechnungen]** können Sie auf die Zielgruppe oder direkt auf die Angebote bezogene Berichtsachsen hinzufügen, um die Analyse der Simulation zu bereichern.

Klicken Sie dazu auf die Schaltfläche **[!UICONTROL Hinzufügen]** und wählen Sie die entsprechenden Felder aus. Achsen werden für die Berechnung der Simulation verwendet und werden im Analysebericht angezeigt. Weitere Informationen hierzu finden Sie im Abschnitt [Simulationsverfolgung](../../interaction/using/simulation-tracking.md).

![](assets/offer_simulation_011.png)

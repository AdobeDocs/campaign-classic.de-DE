---
title: Simulationsperimeter
seo-title: Simulationsperimeter
description: Simulationsperimeter
seo-description: null
page-status-flag: never-activated
uuid: d3145926-0a7e-455f-9b93-55be1b2a0518
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: simulating-offers
discoiquuid: ef658468-e20b-45d9-a714-c152e55c1c79
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Simulationsperimeter{#simulation-scope}

## Perimeter konfigurieren {#definition-of-the-scope}

Open the **[!UICONTROL Scope]** tab to choose your settings.

Folgende Felder müssen zwingend ausgefüllt werden:

* Angebotsumgebung oder -kategorie
* Platzierung
* Kontaktdatum - berücksichtigt werden nur Angebote, die zum Kontaktdatum infrage kommen
* Zielgruppe

   Wenn kein Zielgruppenfilter angegeben wird, wird die gesamte Empfängertabelle in der Simulation berücksichtigt.

* Anzahl an zu simulierenden Vorschlägen pro Kontakt.

   Der Empfänger erhält genau so viele Vorschläge, wie angegeben. Bei Angabe von 5 beispielsweise erhält jede Zielperson maximal 5 Angebotsvorschläge.

   ![](assets/offer_simulation_009.png)

Zur weiteren Feinabstimmung der in der Simulation zu berücksichtigenden Angebote können Themen angegeben werden. Diese müssen zuvor auf Ebene der Kategorie definiert werden.

Sie haben des Weiteren die Möglichkeit, die Simulation für alle Angebote durchzuführen oder sie auf die publizierten Angebote zu beschränken. Mithilfe diverser Filter lässt sich die Auswahl weiter eingrenzen.

>[!NOTE]
>
>Die Angabe des Kontaktdatums ist zwingend erforderlich. Dies erlaubt dem Angebotsmodul eine erste Filterung aus der Gesamtheit der in der Umgebung oder Kategorie enthaltenen Angebote. Ohne Kontaktdatum endet die Simulation mit einem Fehler.

## Berichtsachsen hinzufügen {#adding-reporting-axes}

You can enhance the simulation analysis by adding reporting axes on the target or the offers themselves via the **[!UICONTROL Calculations]** tab.

Klicken Sie dazu auf die **[!UICONTROL Add]** Schaltfläche und wählen Sie die entsprechenden Felder aus. Die Achsen werden zur Berechnung der Simulation verwendet und im Analysebericht angezeigt. For more on this, refer to [Simulation tracking](../../interaction/using/simulation-tracking.md).

![](assets/offer_simulation_011.png)


---
product: campaign
title: Angebote auf einem Outbound-Kanal
description: Angebote auf einem Outbound-Kanal
feature: Interaction, Offers
badge-v7: label="v7" type="Informative" tooltip="Gilt für Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: interaction
content-type: reference
topic-tags: case-study
exl-id: 77fee343-09d1-4d60-be43-efe02953a70c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 100%

---

# Angebote auf einem Outbound-Kanal{#offers-on-an-outbound-channel}



## Angebote per E-Mail versenden {#email-offer-delivery}

Angenommen, Sie verfügen in Ihrer Datenbank über eine Reihe von Angeboten für Reisen nach Afrika. Eignung, Kontexte und Darstellungen der Angebote wurden bereits konfiguriert. Nun soll eine E-Mail-Kampagne zur Unterbreitung der Angebote erstellt werden.

1. Erstellen Sie Ihre Kampagne und den Workflow zur Bestimmung der Zielgruppe.

   ![](assets/offer_delivery_example_001.png)

1. Öffnen Sie die Versand-Aktivität und klicken Sie auf das Symbol **[!UICONTROL Angebote]**.

   ![](assets/offer_delivery_example_002.png)

1. Wählen Sie die E-Mail-Platzierung der Live-Umgebung aus, die die Reiseangebote enthält.

   ![](assets/offer_delivery_example_003.png)

1. Wählen Sie die Kategorie mit den Angeboten für Afrikareisen aus.

   ![](assets/offer_delivery_example_004.png)

1. Geben Sie an, dass pro E-Mail jeweils zwei Angebote unterbreitet werden sollen.

   ![](assets/offer_delivery_example_005.png)

1. Schließen Sie das Angebotsfenster und erstellen Sie den Inhalt Ihres Versands.

   ![](assets/offer_delivery_example_006.png)

1. Fügen Sie nun mithilfe der Personalisierungsfelder den ersten Angebotsvorschlag in den Versandinhalt ein und wählen Sie die HTML-Rendering-Funktion.

   ![](assets/offer_delivery_example_007.png)

1. Fügen Sie auf die gleiche Weise den zweiten Angebotsvorschlag ein.

   ![](assets/offer_delivery_example_008.png)

1. Klicken Sie auf **[!UICONTROL Vorschau]** und wählen Sie einen Empfänger aus, um Nachricht und Angebote so anzeigen zu lassen, wie der Empfänger sie erhalten wird.

   ![](assets/offer_delivery_example_009.png)

1. Speichern Sie den Versand und starten Sie den Zielgruppen-Workflow.
1. Öffnen Sie den Versand und gehen Sie in den Tab **[!UICONTROL Verfolgung]**: Sie können feststellen, dass das Angebotsmodul die zu unterbreitenden Vorschläge aus den verschiedenen, in der Kategorie verfügbaren Angeboten ausgewählt hat.

   ![](assets/offer_delivery_example_010.png)

## Durchführen einer Angebotssimulation {#perform-an-offer-simulation}

1. Klicken Sie im Tab **[!UICONTROL Profile und Zielgruppen]** auf die Schaltfläche **[!UICONTROL Simulationen]** und anschließend auf **[!UICONTROL Erstellen]**.

   ![](assets/offer_simulation_001.png)

1. Benennen Sie die Simulation und geben Sie gegebenenfalls Ausführungsparameter an.

   ![](assets/offer_simulation_example_002.png)

1. Speichern Sie die Simulation. Sie öffnet sich automatisch in einem neuen Tab.

   ![](assets/offer_simulation_example_003.png)

1. Gehen Sie in den Tab **[!UICONTROL Bearbeiten]** > **[!UICONTROL Perimeter]**.

   ![](assets/offer_simulation_example_004.png)

1. Wählen Sie die Kategorie aus, für die Sie die Angebotssimulation durchführen möchten.

   ![](assets/offer_simulation_example_005.png)

1. Wählen Sie die Platzierung aus.

   ![](assets/offer_simulation_example_006.png)

1. Geben Sie einen Zeitraum an. Es muss zumindest ein Startdatum definiert werden. Dies ermöglicht es dem Angebotsmodul, die Angebote zu filtern und nur jene zu berücksichtigen, die zum angegebenen Zeitpunkt tatsächlich zur Verfügung stehen werden.
1. Geben Sie bei Bedarf Themen an, um die Anzahl der Angebote zu begrenzen.

   Im vorliegenden Beispiel enthält die Kategorie **Finanzdienstleistungen** zwei Unterkategorien mit je einem unterschiedlichen Thema. Die Simulation soll sich nur auf die Kategorie mit dem Anwendungsthema **Kunden > 1 Jahr** beziehen.

   ![](assets/offer_simulation_example_007.png)

1. Definieren Sie die Zielgruppe.

   ![](assets/offer_simulation_example_008.png)

1. Geben Sie die Anzahl an Angeboten an, die Sie jedem Empfänger unterbreiten möchten.

   Im vorliegenden Beispiel soll das Angebotsmodul für jeden Empfänger die drei Angebote auswählen, die die höchste Gewichtung aufweisen.

   ![](assets/offer_simulation_example_009.png)

1. Speichern Sie die Konfiguration und klicken Sie im **[!UICONTROL Dashboard]** auf **[!UICONTROL Simulation starten]**.

   ![](assets/offer_simulation_example_010.png)

1. Nach Abschluss der Simulation können Sie im Tab **[!UICONTROL Ergebnisse]** die Verteilung der Vorschläge pro Angebot ansehen.

   Im vorliegenden Beispiel beruht die Verteilung wie konfiguriert auf drei Vorschlägen.

   ![](assets/offer_simulation_example_011.png)

1. Rufen Sie den Bericht **[!UICONTROL Angebotsverteilung nach Rang]** auf, um die Reihenfolge der durch das Angebotsmodul ausgewählten Angebote im Detail anzusehen.

   ![](assets/offer_simulation_example_012.png)

1. Ändern Sie bei Bedarf den Perimeter Ihrer Simulation und klicken Sie erneut auf **[!UICONTROL Simulation starten]**, bis das Ergebnis Ihren Erwartungen entspricht.

   ![](assets/offer_simulation_example_010.png)

1. Sie haben mithilfe der Verlaufs- und Exportfunktionen des Berichts die Möglichkeit, die Simulationsdaten zu speichern.

   ![](assets/offer_simulation_example_013.png)

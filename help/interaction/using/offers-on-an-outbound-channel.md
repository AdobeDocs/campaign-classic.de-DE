---
product: campaign
title: Angebote auf einem Outbound-Kanal
description: Angebote auf einem Outbound-Kanal
feature: Interaction, Offers
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: interaction
content-type: reference
topic-tags: case-study
exl-id: 77fee343-09d1-4d60-be43-efe02953a70c
TQID: https://experienceleague.adobe.com/WGoYaHNR13J47UVmKpHRSm9aw0T8ZrvHUl9zGXezQBU
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 478
ht-degree: 84%

---

# Angebote auf einem Outbound-Kanal{#offers-on-an-outbound-channel}



## Angebote per E-Mail versenden {#email-offer-delivery}

In unserer Datenbank gibt es eine Kategorie von Reiseangeboten nach Afrika. Die Eignung, der Kontext und die Darstellungen jedes Angebots wurden konfiguriert. Wir möchten nun eine Kampagne erstellen, um unsere Angebote per E-Mail zu präsentieren.

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

1. Schließen Sie das Fenster für die Angebotsverwaltung und erstellen Sie den Inhalt Ihres Versands.

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

1. Speichern Sie die Simulation. Dieser wird dann in einer neuen Registerkarte geöffnet.

   ![](assets/offer_simulation_example_003.png)

1. Gehen Sie in den Tab **[!UICONTROL Bearbeiten]** > **[!UICONTROL Perimeter]**.

   ![](assets/offer_simulation_example_004.png)

1. Wählen Sie die Kategorie aus, für die Sie die Angebotssimulation durchführen möchten.

   ![](assets/offer_simulation_example_005.png)

1. Wählen Sie die Platzierung für die Simulation aus.

   ![](assets/offer_simulation_example_006.png)

1. Gültigkeitsdaten eingeben. Sie müssen mindestens ein Startdatum eingeben. Auf diese Weise kann das Angebotsmodul Angebote filtern und diejenigen auswählen, die zu einem bestimmten Datum gültig sind.
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

1. Nach Abschluss der Simulation können Sie im Tab **[!UICONTROL Ergebnisse]** die Aufschlüsselung der Vorschläge pro Angebot ansehen.

   Im vorliegenden Beispiel beruht die Aufschlüsselung wie konfiguriert auf drei Vorschlägen.

   ![](assets/offer_simulation_example_011.png)

1. Rufen Sie den Bericht **[!UICONTROL Angebotsaufschlüsselung nach Rang]** auf, um die Reihenfolge der durch das Angebotsmodul ausgewählten Angebote im Detail anzusehen.

   ![](assets/offer_simulation_example_012.png)

1. Ändern Sie bei Bedarf den Perimeter Ihrer Simulation und klicken Sie erneut auf **[!UICONTROL Simulation starten]**, bis das Ergebnis Ihren Erwartungen entspricht.

   ![](assets/offer_simulation_example_010.png)

1. Sie haben mithilfe der Verlaufs- und Exportfunktionen des Berichts die Möglichkeit, die Simulationsdaten zu speichern.

   ![](assets/offer_simulation_example_013.png)

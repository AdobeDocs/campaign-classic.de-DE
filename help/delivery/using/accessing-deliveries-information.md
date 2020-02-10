---
title: Auf Versandinformationen zugreifen
seo-title: Auf Versandinformationen zugreifen
description: Auf Versandinformationen zugreifen
seo-description: null
page-status-flag: never-activated
uuid: dc8f0267-1884-4a39-9a7d-d5ef21932928
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: d2631c67-7781-4baa-b24e-e7921353d131
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 211556bbf023731ffeab2e90692410a852ab3555

---


# Auf Versandinformationen zugreifen{#accessing-deliveries-information}

## Auf die Versandliste zugreifen {#accessing-the-list-of-deliveries}

To access the list of deliveries, go to the **[!UICONTROL Campaigns]** universe and click the **[!UICONTROL Deliveries]** link.

If you use [the Explorer view](../../platform/using/adobe-campaign-workspace.md#about-adobe-campaign-explorer), you can access all deliveries via the **[!UICONTROL Campaign management > Deliveries]** node in the tree.

>[!NOTE]
>
>Informationen zum Adobe Campaign-Arbeitsbereich finden Sie in [diesem Abschnitt](../../platform/using/adobe-campaign-workspace.md).

Auf dieser Seite werden alle in der Datenbank gespeicherten Sendungen angezeigt. Sie haben die Möglichkeit, Status, Erfolgsquoten und Änderungsdaten einzusehen.

![](assets/d_ncs_user_filter_interface_delivery01.png)

>[!NOTE]
>
>Informationen zu den verfügbaren Filtern finden Sie in [diesem Abschnitt](../../platform/using/filtering-options.md).

Im Versand-Assistenten werden Sendungen konfiguriert, validiert und abgeschickt. Der Inhalt des Assistenten hängt vom gewählten Kommunikationskanal (E-Mail, Mobile, Push, Briefpost) und den Rechten des Benutzers ab.

Durch die Auswahl eines Versands aus der Liste gelangen Sie in ein Fenster, das Ihnen die Bearbeitung des entsprechenden Versands ermöglicht. So können Sie den Versand zum Beispiel absenden oder stoppen.

![](assets/s_ncs_user_interface_delivery02.png)

Je nach Fortschritt im Versandzyklus weisen die Sendungen verschiedene Status auf:

* Abgebrochen
* Fehlgeschlagen
* Ausstehend
* Abgeschlossen
* Ausgesetzt
* Erneuter Versuch läuft
* Gestartet
* Versandbereit
* In Vorbereitung
* Zielgruppenberechnung
* In Bearbeitung

Die Status lassen sich leicht anhand der verschiedenfarbigen Label unterscheiden:

![](assets/s_ncs_user_status_campaigns_120.png)

The drop-down list next to the **[!UICONTROL Create]** button enables you to filter deliveries based on their status.

![](assets/delivery_filter_status.png)

## Auf den Versandkalender zugreifen {#accessing-the-delivery-calendar}

Um auf den Lieferkalender zuzugreifen, gehen Sie zum **[!UICONTROL Campaign]** Universum und klicken Sie auf den **[!UICONTROL Campaign calendar]** Link. Dieser Kalender zeigt die Aufschlüsselung der Kampagnen im Zeitverlauf an. Sie können die Anzeige nach Monat, Woche oder Tag anpassen.

![](assets/s_ncs_user_interface_delivery04.png)

Click the name of a delivery to display the main information about it. You can also open the campaign if necessary by clicking **[!UICONTROL Open]**.

![](assets/s_ncs_user_interface_delivery05.png)

## Auf Informationen zum Versanddurchsatz zugreifen {#accessing-deliveries-throughput-information}

Die Informationen auf der **[!UICONTROL Delivery throughput]** Seite betreffen alle Auslieferungen der Plattform. Zur Messung der Geschwindigkeit, mit der die Nachrichten gesendet werden, sind die Kriterien die Anzahl der gesendeten Nachrichten pro Stunde und die Größe der Nachrichten (in Bits pro Sekunde). Im folgenden Beispiel zeigt die erste Grafik die erfolgreichen Auslieferungen in Blau und die Anzahl der fehlerhaften Auslieferungen in Orange.

You can choose the time slot for which the throughput is calculated. To do this, select the value from the drop-down list, and then click **[!UICONTROL Refresh]**.

![](assets/s_ncs_user_interface_delivery06.png)

>[!NOTE]
>
>Bei gehosteten oder hybriden Installationen zeigt die Seite, wenn Sie auf die erweiterte MTA aktualisiert haben, den Durchsatz nicht mehr an Ihre E-Mail-Empfänger an. **[!UICONTROL Delivery throughput]** Es zeigt die Durchsatzgeschwindigkeit für die Weiterleitung Ihrer Nachrichten von Campaign auf die erweiterte MTA.
>
>Weitere Informationen zur erweiterten MTA-Datei für Adobe Campaign finden Sie in diesem [Dokument](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html).
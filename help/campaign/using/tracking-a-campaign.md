---
title: Kampagnen verfolgen
seo-title: Kampagnen verfolgen
description: Kampagnen verfolgen
seo-description: null
page-status-flag: never-activated
uuid: 66919c81-b22c-4138-a654-ea53154ba718
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: e1f8958d-f036-4635-be6e-ebdbea6ac116
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Kampagnen verfolgen{#tracking-a-campaign}

Zentrale Benutzer haben die Möglichkeit, die Bestellungen und Evaluierungen der angebotenen Kampagnenkits zu verfolgen.

Folgende Funktionen stehen ihnen hierzu zur Verfügung:

* [Filtern von Kits](#filter-packages),
* [Bearbeiten von Kits](#edit-packages),
* [Abbrechen von Kits](#cancel-a-package),
* [Zurücksetzen von Kits](#reinitializing-a-package).

## Filtern von Kits {#filter-packages}

In der **[!UICONTROL Campaigns universe]** Liste können Sie angeben, **[!UICONTROL Campaign packages]** welche Gruppen alle vorhandenen verteilten Marketing-Kampagnen gruppieren. Sie können diese Liste so filtern, dass nur Kampagnen angezeigt werden, die entweder veröffentlicht wurden, verspätet, ausstehende Genehmigung usw. Klicken Sie dazu auf die Links im oberen Bereich dieser Ansicht, oder verwenden Sie den **[!UICONTROL Filter list]** Link und wählen Sie den anzuzeigenden Kampagnenpaketstatus aus.

![](assets/mkg_dist_catalog_filter.png)

## Bearbeiten von Kits {#edit-packages}

The **[!UICONTROL Campaign packages]** page lets you view the summary of each package.

Sie enthält folgende Informationen: Titel, Kampagnentyp, Referenzkampagne des Kits sowie sein Speicherordner.

Klicken Sie zum Öffnen des Kits auf seinen Titel. Daraufhin werden die von den Lokalstellen ausgeführten Bestellungen und ihr Status angezeigt.

This information is also offered in the **[!UICONTROL Campaign orders]** view which lists all orders.

![](assets/mkg_dist_catalog_op_command_details.png)

Zentrale Benutzer verfügen über zwei unterschiedliche Möglichkeiten, eine Bestellung zu bearbeiten:

1. Sie können auf den Titel der Bestellung klicken, um sie zu öffnen. Daraufhin werden Details der Bestellung angezeigt.

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   The **[!UICONTROL Edit > General]** tab lets you view information entered by the local entity when it ordered the campaign.

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. Der Benutzer kann auf den Titel des Kits klicken, um ihn zu öffnen und gegebenenfalls bestimmte Parameter zu verändern.

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## Abbrechen von Kits {#cancel-a-package}

Die Zentralstelle kann ein Kampagnenkit jederzeit abbrechen.

Click **[!UICONTROL Cancel]** in the campaign package **[!UICONTROL Dashboard]**.

![](assets/mkg_dist_cancel_op_from_dashboard.png)

The **[!UICONTROL Comment]** field lets you justify the cancellation.

Auf Niveau einer **lokalen Kampagne** löscht der Abbruch eines Kits diesen aus der Liste der für die Lokalstellen verfügbaren Kampagnen.

Auf Niveau einer **partizipativen Kampagne** hat der Abbruch eines Kits folgende Auswirkungen:

1. Abbruch aller mit diesem Kit verbundenen Bestellungen;

   ![](assets/mkg_dist_mutual_op_cancelled.png)

1. Abbruch der Hauptkampagne und Anhalten aller laufenden Vorgänge (Workflows, Sendungen);

   ![](assets/mkg_dist_mutual_op_cancelled1.png)

1. Versand einer Benachrichtigung an alle betroffenen Lokalstellen.

   ![](assets/mkg_dist_mutual_op_cancelled2.png)

Die Zentralstelle kann nach dem Abbruch immer noch auf das Kit zugreifen und es bei Bedarf zurücksetzen. Damit das Kit den Lokalstellen wieder zur Verfügung gestellt werden kann, muss es erneut validiert und gestartet werden. Die Zurücksetzung eines Kampagnenkits wird im Folgenden beschrieben.

## Zurücksetzen von Kits {#reinitializing-a-package}

Das Zurücksetzen eines Kampagnenkits dient dazu, dieses zu bearbeiten und anschließend den Lokalstellen erneut zur Verfügung zu stellen.

1. Öffnen Sie hierzu das entsprechende Kit.
1. Klicken Sie auf den **[!UICONTROL Reinitialize the package to reuse it]** Link und dann auf **[!UICONTROL OK]**.

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. Click the **[!UICONTROL Save]** button to approve package re-initialization.

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. The package status changes to **[!UICONTROL Being edited]**. Modify, approve and publish it again to restore it to the list of campaign package.

>[!NOTE]
>
>Sie haben auch die Möglichkeit, ein abgebrochenes Kampagnenkit zurückzusetzen.


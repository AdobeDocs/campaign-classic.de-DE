---
title: Externe Empfängertabelle verwenden
seo-title: Externe Empfängertabelle verwenden
description: Externe Empfängertabelle verwenden
seo-description: null
page-status-flag: never-activated
uuid: a6147425-14f0-41e8-a47f-3e7072deafa7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: 92c32b2d-d8bf-41ab-9349-ef4a15f10521
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Externe Empfängertabelle verwenden{#using-an-external-recipient-table}

Wenn es sich bei der Auslieferungstabelle um eine externe Tabelle handelt, müssen Sie zusätzliche Konfigurationen vornehmen. Das **[!UICONTROL nms:seedmember]** Schema muss erweitert werden. Den Saatgutadressen wird eine Registerkarte hinzugefügt, um die entsprechenden Felder zu definieren, wie nachfolgend gezeigt:

![](assets/s_ncs_user_seedlist_new_tab.png)

Geben Sie in diesem Fall die Testadressen-Daten direkt in den jeweiligen Feldern des entsprechenden Tabs auf Ebene des Versands ein oder importieren Sie Adressenvorlagen:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

Die Schemaerweiterung **nms:seedMember** wird in [diesem Abschnitt](../../configuration/using/seed-addresses.md) näher erläutert.

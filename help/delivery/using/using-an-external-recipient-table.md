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
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '90'
ht-degree: 100%

---


# Externe Empfängertabelle verwenden{#using-an-external-recipient-table}

Im Falle einer externen Versandtabelle sind zusätzliche Konfigurationen erforderlich. So muss das Schema **[!UICONTROL nms:seedmember]** erweitert werden. Der im Zuge dessen hinzugefügte Tab erlaubt die Angabe der entsprechenden Felder, wie in unten stehendem Beispiel dargestellt:

![](assets/s_ncs_user_seedlist_new_tab.png)

Geben Sie in diesem Fall die Testadressen-Daten direkt in den jeweiligen Feldern des entsprechenden Tabs auf Ebene des Versands ein oder importieren Sie Adressenvorlagen:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

Die Schemaerweiterung **nms:seedMember** wird in [diesem Abschnitt](../../configuration/using/seed-addresses.md) näher erläutert.

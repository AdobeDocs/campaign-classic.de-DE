---
solution: Campaign Classic
product: campaign
title: Externe Empfängertabelle verwenden
description: Externe Empfängertabelle verwenden
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 100%

---


# Externe Empfängertabelle verwenden{#using-an-external-recipient-table}

Im Falle einer externen Versandtabelle sind zusätzliche Konfigurationen erforderlich. So muss das Schema **[!UICONTROL nms:seedmember]** erweitert werden. Der im Zuge dessen hinzugefügte Tab erlaubt die Angabe der entsprechenden Felder, wie in unten stehendem Beispiel dargestellt:

![](assets/s_ncs_user_seedlist_new_tab.png)

Geben Sie in diesem Fall die Testadressen-Daten direkt in den jeweiligen Feldern des entsprechenden Tabs auf Ebene des Versands ein oder importieren Sie Adressenvorlagen:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

Die Schemaerweiterung **nms:seedMember** wird in [diesem Abschnitt](../../configuration/using/seed-addresses.md) näher erläutert.

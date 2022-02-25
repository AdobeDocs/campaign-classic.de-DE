---
product: campaign
title: Externe Empfängertabelle verwenden
description: Externe Empfängertabelle verwenden
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: ht
source-wordcount: '85'
ht-degree: 100%

---

# Externe Empfängertabelle verwenden{#using-an-external-recipient-table}

![](../../assets/common.svg)

Im Falle einer externen Versandtabelle sind zusätzliche Konfigurationen erforderlich. So muss das Schema **[!UICONTROL nms:seedmember]** erweitert werden. Der im Zuge dessen hinzugefügte Tab erlaubt die Angabe der entsprechenden Felder, wie in unten stehendem Beispiel dargestellt:

![](assets/s_ncs_user_seedlist_new_tab.png)

Geben Sie in diesem Fall die Testadressen-Daten direkt in den jeweiligen Feldern des entsprechenden Tabs auf Ebene des Versands ein oder importieren Sie Adressenvorlagen:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

Die Schemaerweiterung **nms:seedMember** wird in [diesem Abschnitt](../../configuration/using/seed-addresses.md) näher erläutert.

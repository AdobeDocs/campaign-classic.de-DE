---
product: campaign
title: Verwenden einer externen Empfängertabelle
description: Verwenden einer externen Empfängertabelle
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Audiences
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 78%

---

# Verwenden einer externen Empfängertabelle{#using-an-external-recipient-table}



Wenn es sich bei der Versandtabelle um eine externe Tabelle handelt, müssen Sie zusätzliche Konfigurationen vornehmen. Das Schema **[!UICONTROL nms:seedmember]** muss erweitert werden. Den Testadressen wird ein Tab hinzugefügt, in dem die entsprechenden Felder wie unten dargestellt definiert werden:

![](assets/s_ncs_user_seedlist_new_tab.png)

Geben Sie in diesem Fall die Testadressen-Daten direkt in den jeweiligen Feldern des entsprechenden Tabs auf Ebene des Versands ein oder importieren Sie Adressenvorlagen:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

Die Schemaerweiterung **nms:seedMember** wird in [diesem Abschnitt](../../configuration/using/seed-addresses.md) näher erläutert.

---
product: campaign
title: Verwenden einer externen Empfängertabelle
description: Verwenden einer externen Empfängertabelle
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Audiences
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
TQID: https://experienceleague.adobe.com/Uq5yqNYkyDrFVtueUlkIOEC9XEUaYtBArNy8-t1rKAw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 92
ht-degree: 85%

---

# Verwenden einer externen Empfängertabelle{#using-an-external-recipient-table}



Wenn es sich bei der Versandtabelle um eine externe Tabelle handelt, müssen Sie zusätzliche Konfigurationen vornehmen. Das **[!UICONTROL nms:seedmember]**-Schema muss erweitert werden. Es wird eine Registerkarte zu den Testadressen hinzugefügt, um die entsprechenden Felder wie folgt zu definieren:

![](assets/s_ncs_user_seedlist_new_tab.png)

Geben Sie in diesem Fall die Testadressen-Daten direkt in den jeweiligen Feldern des entsprechenden Tabs auf Ebene des Versands ein oder importieren Sie Adressenvorlagen:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

Die **nms:seedMember**-Schemaerweiterung lautet [dieser Abschnitt](../../configuration/using/seed-addresses.md).

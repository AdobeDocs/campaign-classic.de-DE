---
product: campaign
title: Konfigurieren von Populationsmustern
description: Erfahren Sie anhand eines speziellen Anwendungsbeispiels, wie Sie A/B-Tests durchführen
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: A/B Testing
role: User
exl-id: 1ca01cab-734a-4299-b112-04eec51222fb
TQID: https://experienceleague.adobe.com/HWbHtS5F-je1GiNdr25dD17W-MpJ-K3xp-T8kKC-c10
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
feature_v2: id: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2: id: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: e739ee2b-6228-412e-878f-45de0791417d
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 206
ht-degree: 82%

---

# A/B-Tests: Konfigurieren der Testpopulation {#step-2--configuring-population-samples}

## Konfigurieren der Abfrageaktivität {#configuring-the-query-activity}

* Öffnen Sie die **[!UICONTROL Abfrage]** per Doppelklick.

  ![](assets/use_case_abtesting_createrecipients_001.png)

* Klicken Sie auf den Link **[!UICONTROL Abfrage bearbeiten]** und wählen Sie die Empfänger aus, die die Zielgruppe enthalten soll.

  ![](assets/use_case_abtesting_createrecipients_002.png)

* Verbinden Sie die **[!UICONTROL Abfrage]** mit der **[!UICONTROL Aufspaltung]**.

  ![](assets/use_case_abtesting_createrecipients_003.png)

## Konfigurieren der Aufspaltungsaktivität {#configuring-the-split-activity}

Mithilfe dieser Aktivität können Sie mehrere Populationen erstellen: die Population, die Versand A erhält, die Population, die Versand B erhält, und die verbleibende Population. Durch die Auswahl per Zufallsauswahl können Sie nur einen Teil der Population jedes Versands auswählen.

1. Erstellung der Testpopulation A:

   * Öffnen Sie die **[!UICONTROL Aufspaltung]** per Doppelklick.

     ![](assets/use_case_abtesting_createrecipients_004.png)

   * Ändern Sie den Titel für die Testpopulation A entsprechend ab.

     ![](assets/use_case_abtesting_createrecipients_005.png)

   * Aktivieren Sie die Option **[!UICONTROL Anzahl von Datensätzen begrenzen]**.

     ![](assets/use_case_abtesting_createrecipients_006.png)

   * Klicken Sie auf den Link **[!UICONTROL Bearbeiten]**, kreuzen Sie **[!UICONTROL Zufallsauswahl aktivieren]** an und klicken Sie auf **[!UICONTROL Weiter]**.

     ![](assets/use_case_abtesting_createrecipients_007.png)

   * Begrenzen Sie die Testpopulation auf 10 % und klicken Sie auf **[!UICONTROL Beenden]**.

     ![](assets/use_case_abtesting_createrecipients_008.png)

1. Erstellung der Testpopulation B:

   * Klicken Sie auf **[!UICONTROL Hinzufügen]**, um einen zweiten Tab für die Testpopulation B zu erstellen.

     ![](assets/use_case_abtesting_createrecipients_009.png)

   * Begrenzen Sie wie zuvor die Testpopulation auf 10 %.

     ![](assets/use_case_abtesting_createrecipients_010.png)

1. Erstellung der verbleibenden Population:

   * Gehen Sie in den **[!UICONTROL Allgemein]**-Tab.

     ![](assets/use_case_abtesting_createrecipients_011.png)

   * Aktivieren Sie die Option **[!UICONTROL Komplement erzeugen]**.

     ![](assets/use_case_abtesting_createrecipients_012.png)

   * Benennen Sie die verbleibende Population und klicken Sie auf **[!UICONTROL OK]**, um die Aktivität zu schließen.

     ![](assets/use_case_abtesting_createrecipients_013.png)

Jetzt können Sie die beiden Versandvorlagen erstellen. [Weitere Informationen](a-b-testing-uc-delivery-templates.md).

---
solution: Campaign Classic
product: campaign
title: Populationsmuster konfigurieren
description: Erfahren Sie, wie Sie A/B-Tests mit einem speziellen Anwendungsfall durchführen.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 177b4e74c75e4fcca70dc90b5ff2c0406181e0f7
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 90%

---


# Populationsmuster konfigurieren {#step-2--configuring-population-samples}

## Konfiguration der Abfrage {#configuring-the-query-activity}

* Öffnen Sie die **[!UICONTROL Abfrage]** per Doppelklick.

   ![](assets/use_case_abtesting_createrecipients_001.png)

* Klicken Sie auf den Link **[!UICONTROL Abfrage bearbeiten]** und wählen Sie die Empfänger aus, die die Zielgruppe enthalten soll.

   ![](assets/use_case_abtesting_createrecipients_002.png)

* Verbinden Sie die **[!UICONTROL Abfrage]** mit der **[!UICONTROL Aufspaltung]**.

   ![](assets/use_case_abtesting_createrecipients_003.png)

## Konfiguration der Aufspaltung {#configuring-the-split-activity}

Mithilfe dieser Aktivität werden die drei Populationen erstellt: A, B und Rest. Dank der Zufallsauswahl erhält jeweils nur ein Teil jeder Population den entsprechenden Versand.

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

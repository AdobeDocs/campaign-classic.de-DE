---
product: campaign
title: Sendungen konfigurieren
description: Erfahren Sie anhand eines speziellen Anwendungsbeispiels, wie Sie A/B-Tests durchführen
exl-id: 809de30b-7d08-40de-bf3e-dc80d62eae80
source-git-commit: 90c52ec144a6a3c1b534a80507e38fa3ed64fc83
workflow-type: ht
source-wordcount: '244'
ht-degree: 100%

---

# Sendungen im Workflow konfigurieren {#step-4--configuring-the-deliveries-in-the-workflow}

![](../../assets/common.svg)

Sobald die [Populationen erstellt wurden](a-b-testing-uc-population-samples.md), können Sie die Sendungen konfigurieren. In diesem Anwendungsfall ermöglichen es die ersten beiden Sendungen, verschiedene Inhalte an die Populationen A und B zu senden. Der dritte Versand ist der Fallback-Versand: Er wird an die Empfänger gesendet, die weder zu A noch zu B gehören. Der Inhalt wird durch ein Skript erstellt und ist entweder mit A oder B identisch, je nachdem, welcher Empfänger die höchste Öffnungsrate erzielt hat. Wir müssen eine Wartezeit für die dritte Sendung konfigurieren, um das Ergebnis der Sendungen A und B zu ermitteln. Aus diesem Grund beinhaltet die dritte Sendung eine Aktivität vom Typ **[!UICONTROL Warten]**.

1. Verbinden Sie ausgehend von der Aufspaltung die Transition der Population A mit einer der **[!UICONTROL E-Mail-Versand]**-Aktivitäten.

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. Öffnen Sie den Versand per Doppelklick.
1. Wählen Sie aus der Dropdown-Liste die Versandvorlage A aus.

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. Klicken Sie auf **[!UICONTROL Fortfahren]** und anschließend auf .

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. Verbinden Sie ausgehend von der Aufspaltung die Transition der Population B mit der zweiten **[!UICONTROL E-Mail-Versand]**-Aktivität.

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. Öffnen Sie den Versand, wählen Sie die Vorlage B und speichern Sie den Versand.

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. Verbinden Sie ausgehend von der Aufspaltung die Transition der verbleibenden Population mit der **[!UICONTROL Warten]**-Aktivität.

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. Öffnen Sie die **[!UICONTROL Warten]**-Aktivität und legen Sie die Wartezeit auf 5 Tage fest.

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. Verbinden Sie die **[!UICONTROL Warten]**-Aktivität mit der **[!UICONTROL JavaScript-Code]**-Aktivität.

   ![](assets/use_case_abtesting_createdeliveries_008.png)

Jetzt können Sie das Skript erstellen. [Weitere Informationen](a-b-testing-uc-script.md).

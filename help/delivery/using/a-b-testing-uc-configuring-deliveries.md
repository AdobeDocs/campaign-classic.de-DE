---
product: campaign
title: Sendungen konfigurieren
description: Erfahren Sie anhand eines speziellen Anwendungsbeispiels, wie Sie A/B-Tests durchführen
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: A/B Testing
exl-id: 809de30b-7d08-40de-bf3e-dc80d62eae80
TQID: https://experienceleague.adobe.com/7fr4R6dly8-CJh9XYRpAwus1-AUJaz496LOPrWebt0k
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: e739ee2b-6228-412e-878f-45de0791417d
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 259
ht-degree: 100%

---

# A/B-Tests: Konfigurieren der Sendungen im Workflow {#step-4--configuring-the-deliveries-in-the-workflow}

Sobald die [Populationen erstellt wurden](a-b-testing-uc-population-samples.md), können Sie die Sendungen konfigurieren. In diesem Anwendungsfall ermöglichen es die ersten beiden Sendungen, verschiedene Inhalte an die Populationen A und B zu senden. Der dritte Versand ist der Fallback-Versand: Er wird an die Empfänger gesendet, die weder zu A noch zu B gehören. Der Inhalt wird durch ein Script erstellt und ist entweder mit A oder B identisch, je nachdem, welcher Empfänger die höchste Öffnungsrate erzielt hat. Wir müssen eine Wartezeit für die dritte Sendung konfigurieren, um das Ergebnis der Sendungen A und B zu ermitteln. Aus diesem Grund beinhaltet die dritte Sendung eine Aktivität vom Typ **[!UICONTROL Warten]**.

1. Gehen Sie zur Aktivität **[!UICONTROL Aufspalten]**  und verknüpfen Sie den für Population A bestimmten Übergang mit einer der E-Mail-Sendungen, die bereits im Workflow enthalten sind.

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

Jetzt können Sie das Script erstellen. [Weitere Informationen](a-b-testing-uc-script.md).

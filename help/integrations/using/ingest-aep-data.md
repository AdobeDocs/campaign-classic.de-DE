---
product: campaign
title: Aufnehmen von Adobe Experience Platform-Segmenten in Campaign
description: Erfahren Sie, wie Sie Adobe Experience Platform-Zielgruppen in Campaign Classic aufnehmen
feature: Experience Platform Integration
audience: integrations
content-type: reference
exl-id: 6db8a653-b649-402c-8814-24826edadba7
TQID: https://experienceleague.adobe.com/gZ3arUya5UYcZckqtlDObZTA7laUmVttTDHxgOb97vE
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 324
ht-degree: 100%

---

# Aufnehmen von Adobe Experience Platform-Segmenten in Campaign {#destinations}



Um Adobe Experience Platform-Zielgruppen in Campaign aufzunehmen und sie in Ihren Workflows zu verwenden, müssen Sie zunächst Adobe Campaign als ein Adobe Experience Platform-**Ziel** verbinden und mit dem zu exportierenden Segment konfigurieren.

Nachdem das Ziel konfiguriert ist, werden die Daten an Ihren Speicherort exportiert. Zur Aufnahme der Daten muss in Campaign Classic noch ein spezieller Workflow erstellt werden.

## Adobe Campaign als Ziel verbinden

Konfigurieren Sie in Adobe Experience Platform eine Verbindung mit Adobe Campaign, indem Sie einen Speicherort für die exportierten Segmente auswählen. In diesem Schritt können Sie auch die zu exportierenden Segmente auswählen und zusätzliche XDM-Felder angeben, die einbezogen werden sollen.

Weitere Informationen finden Sie in der [Dokumentation zu Zielen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=de).

Nachdem das Ziel konfiguriert wurde, erstellt Adobe Experience Platform eine tabulatorgetrennte .txt- oder .csv-Datei an dem von Ihnen angegebenen Speicherort. Dieser Vorgang wird einmal alle 24 Stunden geplant und ausgeführt.

Sie können jetzt einen Campaign Classic-Workflow konfigurieren, um das Segment in Campaign aufzunehmen.

## Import-Workflow in Campaign Classic erstellen

Nachdem Campaign Classic als Ziel konfiguriert wurde, müssen Sie einen Workflow erstellen, um die von Adobe Experience Platform exportierte Datei zu importieren.

Fügen Sie dazu die Aktivität **[!UICONTROL Dateiübertragung]** hinzu und konfigurieren Sie sie. Weiterführende Informationen zur Konfiguration dieser Aktivität finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/file-transfer.html?lang=de){target="_blank"}.

![](assets/rtcdp-file-transfer.png)

Sie können dann Ihren Workflow gemäß Ihren Anforderungen erstellen (Datenbank mit den Segmentdaten aktualisieren, kanalübergreifende Sendungen an das Segment ausführen usw.).

Beispielsweise wird im folgenden Workflow die Datei täglich von Ihrem Speicherort heruntergeladen und anschließend die Campaign-Datenbank mit den Segmentdaten aktualisiert.

![](assets/rtcdp-workflow.png)

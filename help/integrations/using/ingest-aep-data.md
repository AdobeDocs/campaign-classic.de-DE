---
product: campaign
title: Adobe Experience Platform-Segmente in Campaign aufnehmen
description: Erfahren Sie, wie Sie Adobe Experience Platform-Audiences in Campaign Classic aufnehmen.
audience: integrations
content-type: reference
exl-id: 6db8a653-b649-402c-8814-24826edadba7
source-git-commit: 8b970705f0da6a9e09de9fadb3e1a8c5f4814f9f
workflow-type: ht
source-wordcount: '305'
ht-degree: 100%

---

# Adobe Experience Platform-Segmente in Campaign aufnehmen {#destinations}

![](../../assets/common.svg)

Um Adobe Experience Platform-Audiences in Campaign aufzunehmen und sie in Ihren Workflows zu verwenden, müssen Sie zunächst Adobe Campaign als ein Adobe Experience Platform-**Ziel** verbinden und mit dem zu exportierenden Segment konfigurieren.

Nachdem das Ziel konfiguriert ist, werden die Daten an Ihren Speicherort exportiert. Zur Aufnahme der Daten muss in Campaign Classic noch ein spezieller Workflow erstellt werden.

## Adobe Campaign als Ziel verbinden

Konfigurieren Sie in Adobe Experience Platform eine Verbindung mit Adobe Campaign, indem Sie einen Speicherort für die exportierten Segmente auswählen. In diesem Schritt können Sie auch die zu exportierenden Segmente auswählen und zusätzliche XDM-Felder angeben, die einbezogen werden sollen.

Weitere Informationen finden Sie in der [Dokumentation zu Zielen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=de).

Nachdem das Ziel konfiguriert wurde, erstellt Adobe Experience Platform eine tabulatorgetrennte .txt- oder .csv-Datei an dem von Ihnen angegebenen Speicherort. Dieser Vorgang wird einmal alle 24 Stunden geplant und ausgeführt.

Sie können jetzt einen Campaign Classic-Workflow konfigurieren, um das Segment in Campaign aufzunehmen.

## Import-Workflow in Campaign Classic erstellen

Nachdem Campaign Classic als Ziel konfiguriert wurde, müssen Sie einen Workflow erstellen, um die von Adobe Experience Platform exportierte Datei zu importieren.

Fügen Sie dazu die Aktivität **[!UICONTROL Dateiübertragung]** hinzu und konfigurieren Sie sie. Weiterführende Informationen zur Konfiguration dieser Aktivität finden Sie in [diesem Abschnitt](../../workflow/using/file-transfer.md).

![](assets/rtcdp-file-transfer.png)

Sie können dann Ihren Workflow gemäß Ihren Anforderungen erstellen (Datenbank mit den Segmentdaten aktualisieren, kanalübergreifende Sendungen an das Segment ausführen usw.).

Beispielsweise wird im folgenden Workflow die Datei täglich von Ihrem Speicherort heruntergeladen und anschließend die Campaign-Datenbank mit den Segmentdaten aktualisiert.

![](assets/rtcdp-workflow.png)

---
product: campaign
title: Voraussetzungen für die Campaign-Installation unter Windows
description: Voraussetzungen für die Campaign-Installation unter Windows
feature: Installation, Instance Settings
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: a7cf59cc-9260-4109-af4c-b2e2a9c999da
TQID: 'https://experienceleague.adobe.com/vECxz7-bt6DMteRM-N4BtD6Uo5qonHrkgQQeEOkTSt0'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 14%
---
# Erste Schritte mit der Installation von Campaign unter Windows {#prerequisites-of-campaign-installation-in-windows}



Die zur Installation von Adobe Campaign erforderliche technische Konfiguration und Software wird in der [Kompatibilitätsmatrix) ](../../rn/using/compatibility-matrix.md).

Der Adobe Campaign-Server-Installationsprozess für die Verwendung in mehreren Instanzen wird unten unter „Installieren [ Servers“ ](../../installation/using/installing-the-server.md).

Die wichtigsten Schritte sind:

1. Installieren Sie den Anwendungs-Server, siehe [Ausführen des Installationsprogramms](../../installation/using/installing-the-server.md#executing-the-installation-program).
1. Informationen zur Integration in einen Webserver (optional, je nach den bereitgestellten Komponenten) finden Sie unter [Konfigurieren des IIS-Webservers](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

Sobald die Installationsschritte abgeschlossen sind, müssen Sie die Instanzen, die Datenbank und den Server konfigurieren. Weitere Informationen hierzu finden Sie unter [Über die Erstkonfiguration](../../installation/using/about-initial-configuration.md).

>[!NOTE]
>
>Wenn Adobe Campaign in einer Windows-Umgebung bereitgestellt wird, können Benutzende mit den erforderlichen Zugriffsrechten während der Dateibearbeitung im Netzwerk die UNC-Syntax (Universal.Uniform Naming Convention) für Zugriffspfade verwenden.

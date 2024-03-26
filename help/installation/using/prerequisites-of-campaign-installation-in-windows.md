---
product: campaign
title: Voraussetzungen für die Installation von Campaign unter Windows
description: Voraussetzungen für die Installation von Campaign unter Windows
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
badge-v7-prem: label="On-Premise und Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: a7cf59cc-9260-4109-af4c-b2e2a9c999da
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 14%

---

# Erste Schritte mit der Installation von Campaign unter Windows {#prerequisites-of-campaign-installation-in-windows}



Die für die Installation von Adobe Campaign erforderliche technische Konfiguration und Software wird im Abschnitt [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md).

Der Adobe Campaign-Serverinstallationsprozess für die Verwendung mehrerer Instanzen wird nachfolgend beschrieben in [Installieren des Servers](../../installation/using/installing-the-server.md).

Die wichtigsten Schritte sind:

1. Installieren Sie den Anwendungsserver, siehe [Ausführen des Installationsprogramms](../../installation/using/installing-the-server.md#executing-the-installation-program).
1. Integration in einen Webserver (optional, je nach bereitgestellter Komponente); siehe [Konfigurieren des IIS-Webservers](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

Nach Abschluss der Installationsschritte müssen Sie die Instanzen, die Datenbank und den Server konfigurieren. Weitere Informationen hierzu finden Sie unter [Über die Erstkonfiguration](../../installation/using/about-initial-configuration.md).

>[!NOTE]
>
>Wenn Adobe Campaign in einer Windows-Umgebung bereitgestellt wird, können Benutzer mit den erforderlichen Zugriffsrechten die UNC-Syntax (Universal.Uniform Naming Convention) für Zugriffspfade während der Dateibearbeitung im Netzwerk verwenden.

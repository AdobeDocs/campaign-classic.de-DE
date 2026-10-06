---
product: campaign
title: Wiederherstellung
description: Wiederherstellung
feature: Monitoring
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: ba4db1af-778c-4c34-9a3c-49f41faa49b5
TQID: 'https://experienceleague.adobe.com/ZXUhBpNXWOjaLlJ0U1ToxAi9HlC0AKenRKIIu0z-63c'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '84'
ht-degree: 25%
---
# Wiederherstellung{#restoration}



Auf einem sauberen Server erfolgt die Wiederherstellung wie folgt:

* auf einem installierten und konfigurierten Betriebssystem (Netzwerke),
* Installieren Sie Anwendungen von Drittanbietern: Webserver, JDK (falls erforderlich),
* Installieren Sie Adobe Campaign-Binärdateien mit demselben Build wie das Quellsystem,
* Konfigurationsdateien, Trackinglogs und Weiterleitungsdateien kopieren,
* Datenbank erstellen und neu erstellen,
* Starten Sie Adobe Campaign.

Weitere Informationen finden Sie im **Installationshandbuch**.

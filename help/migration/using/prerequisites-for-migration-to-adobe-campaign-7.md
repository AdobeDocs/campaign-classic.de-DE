---
title: Voraussetzungen für die Migration zu Adobe Campaign 7
seo-title: Voraussetzungen für die Migration zu Adobe Campaign 7
description: Voraussetzungen für die Migration zu Adobe Campaign 7
seo-description: null
page-status-flag: never-activated
uuid: 9f4e4cdf-5338-4597-9d9d-5a3bd13033c7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
discoiquuid: a3bbd8cc-97c6-4b08-adbf-76ab77b97262
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 27%

---


# Voraussetzungen für die Migration zu Adobe Campaign 7{#prerequisites-for-migration-to-adobe-campaign}

Bevor Sie eine Migration ausführen, lesen Sie die Abschnitte [Bevor Sie die Migration](../../migration/using/before-starting-migration.md) starten und Ihre Plattform [](../../migration/using/configuring-your-platform.md) konfigurieren.

Bei der Migration von v6.02 zu Adobe Campaign v7 werden einige Dateien, die zuvor bereitgestellt wurden, nicht bereitgestellt.

Wenn ein Clientfehler angezeigt wird, müssen Sie entweder Ihre Dashboards mit dem neuen Adobe Campaign-v7-Code aktualisieren oder manuell die folgenden Dateien aus der v6.02-Instanz in die v7-Instanz kopieren:

```
v6.02 files and spaces:
/usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
/usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
v6.1 files and spaces:
/usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
/usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
```

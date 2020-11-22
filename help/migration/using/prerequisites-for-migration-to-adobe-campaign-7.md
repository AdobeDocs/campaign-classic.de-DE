---
solution: Campaign Classic
product: campaign
title: Voraussetzungen für die Migration zu Adobe Campaign 7
description: Voraussetzungen für die Migration zu Adobe Campaign 7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 22%

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

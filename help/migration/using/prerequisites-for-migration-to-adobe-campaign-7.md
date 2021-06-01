---
product: campaign
title: Voraussetzungen für die Migration zu Adobe Campaign 7
description: Voraussetzungen für die Migration zu Adobe Campaign 7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 747d8a2c-b13a-4852-a9b5-0d37b236a36f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 22%

---

# Voraussetzungen für die Migration zu Adobe Campaign 7{#prerequisites-for-migration-to-adobe-campaign}

Lesen Sie vor der Ausführung einer Migration die Abschnitte [Vor der Migration](../../migration/using/before-starting-migration.md) und [Konfigurieren Ihrer Plattform](../../migration/using/configuring-your-platform.md) .

Bei der Migration von v6.02 zu Adobe Campaign v7 werden einige Dateien, die zuvor bereitgestellt wurden, nicht bereitgestellt.

Wenn ein Clientfehler angezeigt wird, müssen Sie entweder Ihre Dashboards mit dem neuen Adobe Campaign v7-Code aktualisieren oder die folgenden Dateien manuell von der v6.02-Instanz in die v7-Instanz kopieren:

```
v6.02 files and spaces:
/usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
/usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
v6.1 files and spaces:
/usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
/usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
```

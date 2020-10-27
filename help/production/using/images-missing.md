---
title: Fehlende Bilder
seo-title: Fehlende Bilder
description: Fehlende Bilder
seo-description: null
page-status-flag: never-activated
uuid: 0dc73ea0-70bc-476d-bdff-2e62d6929f21
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: e001db7a-7c53-477e-a534-ce4d83d68559
translation-type: tm+mt
source-git-commit: d509dc584cd4ae17c6dda85c09fceee8c6162dba
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 7%

---


# Fehlende Bilder{#images-missing}

In der Version 17.9 wurden mehrere Dateien (insbesondere Symbole) verschoben.

Bei gehosteten Kunden hat dies keine Auswirkungen. Bei lokalen Installationen lesen Sie bitte Folgendes.

**Apache-Benutzer:**

Apache-Benutzer haben keine Auswirkung, wenn sie die bereitgestellte **apache_neolane.conf verwenden**

**IIS-Benutzer:**

Bei IIS-Benutzern (unter Windows) werden nach dem Build-Update mehrere Symbole in der Konsole fehlen. Weitere IIS-Aktualisierungsschritte sind erforderlich:

1. Klicken Sie nach dem Build-Update auf **is_neolane_setup.vbs** im Installationsordner der Kampagne. Der Standardpfad lautet C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Starten Sie die IIS-Site neu, die durch den vorherigen Schritt aktualisiert wurde.


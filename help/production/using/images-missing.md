---
title: Bilder fehlen
seo-title: Bilder fehlen
description: Bilder fehlen
seo-description: null
page-status-flag: never-activated
uuid: 0dc73ea0-70bc-476d-bdff-2e62d6929f21
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: e001db7a-7c53-477e-a534-ce4d83d68559
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3801665574d0cdc9c0caf46fb2f0eede38f1b2cc

---


# Bilder fehlen{#images-missing}

In der Version 17.9 wurden mehrere Dateien (insbesondere Symbole) verschoben.

Bei gehosteten Kunden hat dies keine Auswirkungen. Bei lokalen Installationen lesen Sie bitte Folgendes.

**Apache-Benutzer:**

Apache-Benutzer haben keine Auswirkung, wenn sie die bereitgestellte **apache_neolane.conf verwenden**

**IIS-Benutzer:**

Bei IIS-Benutzern (unter Windows) werden nach dem Build-Update mehrere Symbole in der Konsole fehlen. Weitere IIS-Aktualisierungsschritte sind erforderlich:

1. Doppelklicken Sie nach dem Build-Update auf **is_neolane_setup.vbs** im Installationsordner von Campaign. Der Standardpfad lautet C:\Program Files (x86)\Adobe\Adobe Campaign v7\tomcat-7\conf
1. Starten Sie die IIS-Site neu, die im vorherigen Schritt aktualisiert wurde.


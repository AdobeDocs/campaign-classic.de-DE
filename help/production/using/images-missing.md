---
solution: Campaign Classic
product: campaign
title: Fehlende Bilder
description: Fehlende Bilder
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 5%

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


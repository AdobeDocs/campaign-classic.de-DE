---
product: campaign
title: Fehlende Bilder
description: Fehlende Bilder
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 5%

---

# Fehlende Bilder{#images-missing}



In Version 17.9 wurden mehrere Dateien (insbesondere Symbole) verschoben.

Für gehostete Kunden hat dies keine Auswirkungen. Für On-Premise-Installationen lesen Sie bitte Folgendes.

**Apache-Benutzer:**

Apache-Benutzer haben keine Auswirkungen, wenn sie die bereitgestellte **apache_neolane.conf** verwenden.

**IIS-Benutzer:**

Für IIS-Benutzer (unter Windows) werden nach der Build-Aktualisierung mehrere Symbole in der Konsole fehlen. Weitere IIS-Aktualisierungsschritte sind erforderlich:

1. Doppelklicken Sie nach der Build-Aktualisierung im Installationsverzeichnis von Campaign auf **is_neolane_setup.vbs** . Der Standardpfad lautet C:\Program Dateien (x86)\Adobe\Adobe Campaign v7\conf
1. Starten Sie die IIS-Site neu, die durch den vorherigen Schritt aktualisiert wurde.

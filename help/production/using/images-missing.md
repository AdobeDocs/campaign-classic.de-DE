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



In Version 17.9 wurden mehrere Dateien (insbesondere Icons) verschoben.

Für gehostete Kunden gibt es keine Auswirkungen. Bei On-Premise-Installationen lesen Sie bitte Folgendes.

**Apache-Benutzer:**

Es gibt keine Auswirkungen für Apache-Benutzer, wenn sie die bereitgestellte Datei **apache_neolane.conf** verwenden.

**IIS-Benutzer:**

Für IIS-Benutzer (unter Windows) fehlen nach der Build-Aktualisierung mehrere Symbole in der Konsole. Zusätzliche Schritte zur IIS-Aktualisierung sind erforderlich:

1. Doppelklicken Sie nach dem Build-Update **iis_neolane_setup.vbs** im Campaign-Installationsverzeichnis. Der Standardpfad lautet C:\Program (x86)\Adobe\Adobe Campaign v7\conf
1. Starten Sie die IIS-Site neu, die durch den vorherigen Schritt aktualisiert wurde.

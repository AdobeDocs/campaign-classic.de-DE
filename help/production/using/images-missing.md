---
product: campaign
title: Fehlende Bilder
description: Fehlende Bilder
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
TQID: https://experienceleague.adobe.com/GDlcjvzSGP70FlVGHmnhJHsqC3SFG5Y-kQOohR00j8c
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2: id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 111
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

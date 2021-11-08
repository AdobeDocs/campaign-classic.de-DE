---
product: campaign
title: Fehlende Bilder
description: Fehlende Bilder
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 5%

---

# Fehlende Bilder{#images-missing}

![](../../assets/v7-only.svg)

In Version 17.9 wurden mehrere Dateien (insbesondere Symbole) verschoben.

Für gehostete Kunden hat dies keine Auswirkungen. Für On-Premise-Installationen lesen Sie bitte Folgendes.

**Apache-Benutzer:**

Es gibt keine Auswirkungen für Apache-Benutzer, wenn sie die bereitgestellte **apache_neolane.conf**.

**IIS-Benutzer:**

Für IIS-Benutzer (unter Windows) werden nach der Build-Aktualisierung mehrere Symbole in der Konsole fehlen. Weitere IIS-Aktualisierungsschritte sind erforderlich:

1. Doppelklicken Sie nach der Build-Aktualisierung auf **is_neolane_setup.vbs** im Installationsordner von Campaign. Der Standardpfad lautet C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Starten Sie die IIS-Site neu, die durch den vorherigen Schritt aktualisiert wurde.

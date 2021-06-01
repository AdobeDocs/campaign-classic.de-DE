---
product: campaign
title: JSP-Verhalten
description: JSP-Verhalten
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 16%

---

# JSP-Verhalten{#jsp-behavior}

Wenn bestimmte **jsp**-Aufträge nicht erfolgreich ausgeführt werden, müssen Sie sie zur Neukompilierung zwingen.

Geben Sie dazu die folgenden Befehle ein:

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

Die **jsp**-Aufträge werden bei der nächsten Verbindung neu generiert.

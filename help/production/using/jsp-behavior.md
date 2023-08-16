---
product: campaign
title: JSP-Verhalten
description: JSP-Verhalten
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
badge-v7-prem: label="On-Premise und Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '61'
ht-degree: 47%

---

# JSP-Verhalten{#jsp-behavior}



Wenn **jsp** Aufträge nicht erfolgreich ausgeführt werden, müssen Sie sie zur Neukompilierung zwingen.

Geben Sie dazu die folgenden Befehle ein:

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

Die **jsp** Aufträge werden bei der nächsten Verbindung neu generiert.

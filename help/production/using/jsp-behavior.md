---
product: campaign
title: JSP-Verhalten
description: JSP-Verhalten
feature: Monitoring
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
TQID: https://experienceleague.adobe.com/IQSjBaSbnZcsqs0glv8z1aIwOBbtVO2roeXlJiYgEfo
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: '54'
ht-degree: 44%
---
# JSP-Verhalten{#jsp-behavior}



Wenn bestimmte **jsp**-Aufträge nicht erfolgreich ausgeführt werden, müssen Sie die Neukompilierung erzwingen.

Geben Sie dazu die folgenden Befehle ein:

```
nlserver stop web
cd nl6/tomcat-X
rm -r work/
nlserver start web
```

Die **jsp**-Aufträge werden bei der nächsten Verbindung neu generiert.

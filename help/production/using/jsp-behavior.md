---
product: campaign
title: JSP-Verhalten
description: JSP-Verhalten
feature: Monitoring
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
TQID: https://experienceleague.adobe.com/IQSjBaSbnZcsqs0glv8z1aIwOBbtVO2roeXlJiYgEfo
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 66
ht-degree: 54%

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

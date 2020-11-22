---
solution: Campaign Classic
product: campaign
title: JSP-Verhalten
description: JSP-Verhalten
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 16%

---


# JSP-Verhalten{#jsp-behavior}

Wenn bestimmte **jsp** -Aufträge nicht erfolgreich ausgeführt werden, müssen Sie sie zur Neukompilierung zwingen.

Geben Sie dazu die folgenden Befehle ein:

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

Die **JSP** -Aufträge werden beim nächsten Verbinden neu generiert.

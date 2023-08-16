---
product: campaign
title: Deinstallieren von Campaign
description: Informationen zur Deinstallation von Campaign
feature: Installation
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: appendices
exl-id: e2b026ba-aaf3-443d-8c36-c908288a14fd
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '43'
ht-degree: 41%

---

# Deinstallieren von Campaign{#uninstalling-campaign}



>[!CAUTION]
>
>Durch diese Verfahren wird Adobe Campaign dauerhaft deinstalliert. Alle Daten gehen verloren.

**RHEL:**

```
rpm -e nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Debian:**

```
apt purge nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Windows:**

Mehr dazu erfahren Sie auf [dieser Seite](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version). Vergessen Sie nicht, den Installationsordner von Campaign zu entfernen.

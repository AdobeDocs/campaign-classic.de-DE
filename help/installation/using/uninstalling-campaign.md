---
solution: Campaign Classic
product: campaign
title: Deinstallieren von Campaign
description: Informationen zum Deinstallieren von Kampagnen
audience: installation
content-type: reference
topic-tags: appendices
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 30%

---


# Deinstallieren von Campaign{#uninstalling-campaign}

>[!CAUTION]
>
>Durch diese Verfahren wird das Adobe Campaign dauerhaft deinstalliert. Alle Daten gehen verloren.

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

Mehr dazu erfahren Sie auf [dieser Seite](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version). Vergessen Sie nicht, den Installationsordner der Kampagne zu entfernen.

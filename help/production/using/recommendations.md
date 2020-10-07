---
title: 'Empfehlungen   '
seo-title: 'Empfehlungen   '
description: 'Empfehlungen   '
seo-description: null
page-status-flag: never-activated
uuid: d898fe6d-7627-405f-b2bc-b17bf1dc9e96
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: a31c5c9f-503f-4b55-8409-34d4addbd581
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 3%

---


# Empfehlungen{#recommendations}

Adobe Campaign ist ein hochgradig transaktionales System (OLTP-Datenbank). Das bedeutet, dass die zugrunde liegende Datenbank häufig aktualisiert wird, was zu einer Leistungsminderung im Laufe der Zeit führt. Um dieses Problem zu vermeiden, ist eine regelmäßige Datenbankwartung erforderlich.

>[!CAUTION]
>
>Eine Datenbank funktioniert nur dann optimal, wenn sie regelmäßig gepflegt wird. Die von einigen RDBMS angebotene automatische Wartung ist nicht ausreichend und ersetzt nicht die eingehende Wartung, wie auch bei anderen relationalen Datenbank-Transaktionsmanagementsystemen.
>  
>Die in diesem Dokument beschriebenen Verfahren sind Empfehlungen. Für Wartungspläne ist Ihr Datenbankadministrator verantwortlich, der bei Problemen als erster Ansprechpartner fungieren muss.


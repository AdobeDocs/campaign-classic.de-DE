---
solution: Campaign Classic
product: campaign
title: 'Empfehlungen   '
description: 'Empfehlungen   '
audience: production
content-type: reference
topic-tags: database-maintenance
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 2%

---


# Empfehlungen{#recommendations}

Adobe Campaign ist ein hochgradig transaktionales System (OLTP-Datenbank). Das bedeutet, dass die zugrunde liegende Datenbank häufig aktualisiert wird, was zu einer Leistungsminderung im Laufe der Zeit führt. Um dieses Problem zu vermeiden, ist eine regelmäßige Datenbankwartung erforderlich.

>[!IMPORTANT]
>
>Eine Datenbank funktioniert nur dann optimal, wenn sie regelmäßig gepflegt wird. Die von einigen RDBMS angebotene automatische Wartung ist nicht ausreichend und ersetzt nicht die eingehende Wartung, wie auch bei anderen relationalen Datenbank-Transaktionsmanagementsystemen.
>  
>Die in diesem Dokument beschriebenen Verfahren sind Empfehlungen. Für Wartungspläne ist Ihr Datenbankadministrator verantwortlich, der bei Problemen als erster Ansprechpartner fungieren muss.

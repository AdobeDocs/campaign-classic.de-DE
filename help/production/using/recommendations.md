---
product: campaign
title: Recommendations
description: Recommendations
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 2%

---

# Recommendations{#recommendations}

Adobe Campaign ist ein hochgradig transaktionales System (OLTP-Datenbank). Dies bedeutet, dass die zugrunde liegende Datenbank häufig aktualisiert wird, was zu einer Leistungsbeeinträchtigung im Laufe der Zeit führt. Um dieses Problem zu vermeiden, ist eine regelmäßige Datenbankwartung erforderlich.

>[!IMPORTANT]
>
>Eine Datenbank funktioniert nur optimal, wenn sie regelmäßig gepflegt wird. Die automatische Wartung, die von einigen RDBMS angeboten wird, reicht nicht aus und ersetzt nicht die eingehende Wartung, wie dies bei anderen Transaktionsverwaltungssystemen der relationalen Datenbank der Fall ist.
>  
>Die in diesem Dokument beschriebenen Verfahren sind Empfehlungen. Wartungspläne sind für Ihren Datenbankadministrator verantwortlich, der bei Problemen als erster Ansprechpartner fungieren muss.

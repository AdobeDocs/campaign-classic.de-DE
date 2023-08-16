---
product: campaign
title: Empfehlungen
description: Empfehlungen
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
badge-v7-prem: label="On-Premise und Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 20%

---

# Empfehlungen{#recommendations}



Adobe Campaign ist ein hochgradig transaktionales System (OLTP-Datenbank). Dies bedeutet, dass die zugrunde liegende Datenbank häufig aktualisiert wird, was zu einer Leistungsbeeinträchtigung im Laufe der Zeit führt. Um dieses Problem zu vermeiden, ist eine regelmäßige Datenbankwartung erforderlich.

>[!IMPORTANT]
>
>Eine Datenbank funktioniert nur optimal, wenn sie regelmäßig gepflegt wird. Die automatische Wartung, die von einigen RDBMS angeboten wird, reicht nicht aus und ersetzt nicht die eingehende Wartung, wie dies bei anderen Transaktionsverwaltungssystemen der relationalen Datenbank der Fall ist.
>  
>Die in diesem Dokument beschriebenen Verfahren sind Empfehlungen. Für Wartungspläne ist Ihr Datenbankadministrator verantwortlich, der bei Problemen als erster Ansprechpartner fungieren muss.

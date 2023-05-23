---
product: campaign
title: Empfehlungen
description: Empfehlungen
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 2%

---

# Empfehlungen{#recommendations}



Adobe Campaign ist ein hochgradig transaktionales System (OLTP-Datenbank). Dies bedeutet, dass die zugrunde liegende Datenbank häufig aktualisiert wird, was zu einer Leistungsbeeinträchtigung im Laufe der Zeit führt. Um dieses Problem zu vermeiden, ist eine regelmäßige Datenbankwartung erforderlich.

>[!IMPORTANT]
>
>Eine Datenbank funktioniert nur optimal, wenn sie regelmäßig gepflegt wird. Die automatische Wartung, die von einigen RDBMS angeboten wird, reicht nicht aus und ersetzt nicht die eingehende Wartung, wie dies bei anderen Transaktionsverwaltungssystemen der relationalen Datenbank der Fall ist.
>  
>Die in diesem Dokument beschriebenen Verfahren sind Empfehlungen. Für Wartungspläne ist Ihr Datenbankadministrator verantwortlich, der bei Problemen als erster Ansprechpartner fungieren muss.

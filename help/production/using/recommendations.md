---
product: campaign
title: Empfehlungen
description: Empfehlungen
feature: Monitoring
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 12%

---

# Empfehlungen{#recommendations}



Adobe Campaign ist ein stark transaktionales System (OLTP-Datenbank). Dies bedeutet, dass die zugrunde liegende Datenbank häufig aktualisiert wird, was im Laufe der Zeit zu Leistungseinbußen führt. Um diese Art von Problem zu vermeiden, ist eine regelmäßige Wartung der Datenbank erforderlich.

>[!IMPORTANT]
>
>Eine Datenbank funktioniert nur dann optimal, wenn sie regelmäßig gepflegt wird. Die von einigen RDBMS angebotene automatische Wartung ist nicht ausreichend und ersetzt nicht die eingehende Wartung, wie bei allen relationalen Datenbanktransaktionsmanagement-Systemen.
>  
>Die in diesem Dokument beschriebenen Verfahren sind Empfehlungen. Wartungspläne liegen in der Verantwortung Ihres Datenbankadministrators, der bei Problemen Ihr erster Ansprechpartner sein muss.

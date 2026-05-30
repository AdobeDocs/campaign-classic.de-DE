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
TQID: https://experienceleague.adobe.com/hz0wmjq8MEpmen-C30F0tHt5-sRXjQAJ6vaie3hjfAo
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 136
ht-degree: 24%

---

# Empfehlungen{#recommendations}



Adobe Campaign ist ein stark transaktionales System (OLTP-Datenbank). Dies bedeutet, dass die zugrunde liegende Datenbank häufig aktualisiert wird, was im Laufe der Zeit zu Leistungseinbußen führt. Um diese Art von Problem zu vermeiden, ist eine regelmäßige Wartung der Datenbank erforderlich.

>[!IMPORTANT]
>
>Eine Datenbank funktioniert nur dann optimal, wenn sie regelmäßig gepflegt wird. Die von einigen RDBMS angebotene automatische Wartung ist nicht ausreichend und ersetzt nicht die eingehende Wartung, wie bei allen relationalen Datenbanktransaktionsmanagement-Systemen.
>  
>Die in diesem Dokument beschriebenen Verfahren sind Empfehlungen. Wartungspläne liegen in der Verantwortung Ihres Datenbankadministrators, der bei Problemen Ihr erster Ansprechpartner sein muss.

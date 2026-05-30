---
product: campaign
title: Einleitung
description: Einleitung
feature: Monitoring, Upgrade
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 3e39a0d2-ff7e-4233-82bb-2b360f696a33
TQID: https://experienceleague.adobe.com/L6Ais2NSt-Z29b7Jgz25a6uYInel9V-Hb5kv0u6oSLo
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 194
ht-degree: 1%

---

# Einleitung{#introduction}



In diesem Abschnitt wird das Verfahren für das Upgrade von Adobe Campaign auf Client- und Serverseite beschrieben und der Wechsel zu Unicode in einer vorhandenen Instanz beschrieben.

>[!NOTE]
>
>Bei Hosted/Managed Services-Instanzen müssen Sie sich mit Ihrem Adobe-Administrator abstimmen.\
>Bei On-Premise-Instanzen erhalten Sie Unterstützung von Adobe Consultants.

Das Upgrade muss auf alle Server angewendet werden, auf denen Adobe Campaign installiert ist.

1. Migrieren Sie die Weiterleitungs- und Tracking-Server (Apache/IIS).
1. Migrieren Sie die Power Booster-/Cluster-Server.
1. Migrieren Sie den Marketing-Server.

Adobe Campaign basiert auf mehreren Prozessen, die Server-seitig ausgeführt werden und die Sie bei Aktualisierungen bearbeiten müssen, insbesondere:

* Anwendungs-Server (nlserver web)
* Versand-Server (nlserver mta)
* Weiterleitungs-Server (webmdl)

>[!CAUTION]
>
>Die Client-Konsole sollte auf demselben Build wie die Server-Instanz erstellt werden.

>[!NOTE]
>
>Weiterführende Informationen zu den verschiedenen Adobe Campaign-Prozessen finden Sie [diesem Abschnitt](../../installation/using/general-architecture.md#logical-application-layer).\
>Bei Verwendung der Architektur vom Typ Power Booster oder Power Cluster müssen Sie diesen Prozess auf alle Power Booster/Cluster-Server anwenden.

Wenn die neue Version eine Änderung der Datenbankstruktur erfordert, empfehlen wir, die Server in der folgenden Reihenfolge neu zu starten:

1. Anwendungsserver (nlserver web),
1. Weiterleitungsserver (webmdl),
1. Versand-Server (nlserver mta).

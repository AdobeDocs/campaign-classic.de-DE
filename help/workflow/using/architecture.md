---
product: campaign
title: Architektur
description: Workflows werden über eine dedizierte Engine verarbeitet. Diese kann zur besseren Lastverteilung simultan auf mehreren Servern gestartet werden
feature: Workflows
hide: true
exl-id: 46801f78-706c-4dfa-bce7-3d15f569f222
TQID: https://experienceleague.adobe.com/lQLXeSTFhKRCNhA9SdShd9Nyd1mbNt-KPa-XJw-6wAs
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 116
ht-degree: 19%

---

# Architektur {#architecture}



Workflows werden von einem bestimmten Modul verarbeitet. Dieses Modul kann auf mehreren Servern gestartet werden, um die Verarbeitungslast zu teilen.

![](assets/architecture.png)

* Der Prozess &#39;Workflow-Instanz-Runner&#39; (runwf) führt alle Aufgaben einer bestimmten Workflow-Instanz aus. Wenn vorerst keine auszuführenden Aufgaben vorhanden sind, wird sie „passiv“, das heißt sie speichert ihren Status in der Datenbank und stoppt dann.
* Das Modul &#39;Workflow-Server&#39; (wfserver) überwacht aktuelle Workflow-Instanzen. Wenn eine Aufgabe ausgeführt werden soll, erstellt dieses Modul einen Prozess zum Aktivieren (oder Reaktivieren) der entsprechenden Instanz.

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
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 116
ht-degree: 19%

---

# Architektur {#architecture}



Workflows werden von einem bestimmten Modul verarbeitet. Dieses Modul kann auf mehreren Servern gestartet werden, um die Verarbeitungslast zu teilen.

![](assets/architecture.png)

* Der Prozess &#39;Workflow-Instanz-Runner&#39; (runwf) führt alle Aufgaben einer bestimmten Workflow-Instanz aus. Wenn vorerst keine auszuführenden Aufgaben vorhanden sind, wird sie „passiv“, das heißt sie speichert ihren Status in der Datenbank und stoppt dann.
* Das Modul &#39;Workflow-Server&#39; (wfserver) überwacht aktuelle Workflow-Instanzen. Wenn eine Aufgabe ausgeführt werden soll, erstellt dieses Modul einen Prozess zum Aktivieren (oder Reaktivieren) der entsprechenden Instanz.

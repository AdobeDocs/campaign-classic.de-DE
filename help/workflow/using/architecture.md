---
product: campaign
title: Architektur
description: Workflows werden über eine dedizierte Engine verarbeitet. Diese kann zur besseren Lastverteilung simultan auf mehreren Servern gestartet werden.
feature: Workflows
exl-id: 46801f78-706c-4dfa-bce7-3d15f569f222
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 100%

---

# Architektur {#architecture}

![](../../assets/v7-only.svg)

Workflows werden über eine dedizierte Engine verarbeitet. Diese kann zur besseren Lastverteilung simultan auf mehreren Servern gestartet werden.

![](assets/architecture.png)

* Der Prozess &#39;Workflow Instance Runner&#39; (runwf) führt alle Aufgaben einer spezifischen Workflow-Instanz aus. Sobald keine Aufgaben mehr zur unmittelbaren Verarbeitung anstehen, wird der Prozess passiviert, d. h. er speichert seinen derzeitigen Status in der Datenbank und hält an.
* Das Modul &#39;Workflow Server&#39; (wfserver) überwacht die laufenden Workflow-Instanzen. Wenn Aufgaben zur Ausführung anstehen, erstellt das Modul einen Prozess, um die entsprechende Instanz zu aktivieren oder zu reaktivieren.

---
product: campaign
title: Einleitung
description: Einleitung
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 3e39a0d2-ff7e-4233-82bb-2b360f696a33
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 5%

---

# Einleitung{#introduction}

![](../../assets/v7-only.svg)

In diesem Abschnitt wird das Verfahren für die Aktualisierung von Adobe Campaign, Client- und Server-seitig beschrieben und der Wechsel zu Unicode einer vorhandenen Instanz beschrieben.

>[!NOTE]
>
>Bei gehosteten Instanzen müssen Sie sich mit Ihrem Adobe-Administrator abstimmen.\
>Bei On-Premise-Instanzen können Sie Hilfe von Adobe Consultants erhalten.

Das Upgrade muss auf alle Server angewendet werden, auf denen Adobe Campaign installiert ist.

1. Migrieren Sie die Umleitungs- und Tracking-Server (Apache/IIS).
1. Migrieren Sie die Power Booster-/Cluster-Server.
1. Migrieren Sie den Marketing-Server.

Adobe Campaign basiert auf mehreren serverseitigen Prozessen, die Sie bei Aktualisierungen bearbeiten müssen, insbesondere:

* Anwendungs-Server (nlserver web)
* Versandserver (nlserver mta)
* Weiterleitungsserver (webmdl)

>[!CAUTION]
>
>Die Client-Konsole sollte denselben Build haben wie die Server-Instanz.

>[!NOTE]
>
>Weitere Informationen zu den verschiedenen Adobe Campaign-Prozessen finden Sie unter [diesem Abschnitt](../../installation/using/general-architecture.md#logical-application-layer).\
>Bei Verwendung der Power Booster- oder Power Cluster-Architektur müssen Sie diesen Prozess auf alle Power Booster-/Cluster-Server anwenden.

Wenn die neue Version eine Änderung der Datenbankstruktur beinhaltet, empfehlen wir, die Server in der folgenden Reihenfolge neu zu starten:

1. Anwendungs-Server (nlserver web),
1. Weiterleitungsserver (webmdl),
1. Versandserver (nlserver mta).

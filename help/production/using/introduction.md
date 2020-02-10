---
title: Einleitung
seo-title: Einleitung
description: Einleitung
seo-description: null
page-status-flag: never-activated
uuid: 4192a74e-1d4f-4784-80e3-53aaefa9141e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: 772992bf-588f-42bd-a72a-986a88815264
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Einleitung{#introduction}

In diesem Abschnitt wird das Verfahren für die Aktualisierung von Adobe Campaign, clientseitig und serverseitig beschrieben und der Wechsel zu Unicode einer vorhandenen Instanz beschrieben.

>[!NOTE]
>
>Bei gehosteten Instanzen müssen Sie sich mit Ihrem Adobe-Administrator abstimmen.\
>Bei lokalen Instanzen erhalten Sie Unterstützung von Adobe-Beratern.

Die Aktualisierung muss auf alle Server angewendet werden, auf denen Adobe Campaign installiert ist.

1. Migrieren Sie die Umleitungs- und Tracking-Server (Apache/IIS).
1. Migrieren Sie die Power Booster/Cluster-Server.
1. Migrieren des Marketing-Servers.

Adobe Campaign basiert auf verschiedenen serverseitigen Prozessen, die Sie während der Updates bearbeiten müssen, insbesondere:

* Anwendungsserver (nlserver web)
* Bereitstellungsserver (nlserver-Metadaten)
* Umleitungsserver (webmdl)

>[!NOTE]
>
>For more on the various Adobe Campaign processes, refer to [this section](../../installation/using/general-architecture.md#logical-application-layer).\
>Bei Verwendung der Power Booster- oder Power Cluster-Architektur müssen Sie diesen Prozess auf alle Power Booster/Cluster-Server anwenden.

Wenn die neue Version eine Änderung der Datenbankstruktur beinhaltet, empfehlen wir, die Server in der folgenden Reihenfolge neu zu starten:

1. Anwendungsserver (nlserver web),
1. Umleitungsserver (webmdl),
1. Bereitstellungsserver (nlserver-Metadaten).


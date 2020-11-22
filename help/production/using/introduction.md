---
solution: Campaign Classic
product: campaign
title: Einleitung
description: Einleitung
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 1%

---


# Einleitung{#introduction}

In diesem Abschnitt wird das Verfahren für die Aktualisierung von Adobe Campaign, clientseitig und serverseitig beschrieben und der Wechsel zu Unicode einer vorhandenen Instanz beschrieben.

>[!NOTE]
>
>Bei gehosteten Instanzen müssen Sie sich mit Ihrem Adoben-Administrator abstimmen.\
>Bei lokalen Instanzen können Sie Hilfe von Adobe Consultants erhalten.

Die Aktualisierung muss auf alle Server angewendet werden, auf denen Adobe Campaign installiert ist.

1. Migrieren Sie die Umleitungs- und Tracking-Server (Apache/IIS).
1. Migrieren Sie die Power Booster/Cluster-Server.
1. Migrieren des Marketing-Servers.

Adobe Campaign basiert auf verschiedenen serverseitigen Prozessen, die Sie während der Updates bearbeiten müssen, insbesondere:

* Anwendungsserver (nlserver web)
* Versand-Server (nlserver-Metadaten)
* Umleitungsserver (webmdl)

>[!NOTE]
>
>For more on the various Adobe Campaign processes, refer to [this section](../../installation/using/general-architecture.md#logical-application-layer).\
>Bei Verwendung der Power Booster- oder Power Cluster-Architektur müssen Sie diesen Prozess auf alle Power Booster/Cluster-Server anwenden.

Wenn die neue Version eine Änderung der Datenbankstruktur beinhaltet, empfehlen wir, die Server in der folgenden Reihenfolge neu zu starten:

1. Anwendungsserver (nlserver web),
1. Umleitungsserver (webmdl),
1. Versand-Server (nlserver-Metadaten).


---
product: campaign
title: Messaging-Server
description: Messaging-Server
feature: Installation, Instance Settings
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 12%
---
# Messaging-Server{#messaging-server}



Adobe Campaign verarbeitet ausgehende E-Mails nativ. Ein herkömmlicher E-Mail-Server ist jedoch erforderlich, um eingehende Nachrichten zu empfangen, die mit zurückgegebenen E-Mails verknüpft sind (von E-Mail-Daemons). Die auf diesem Server konfigurierten Postfächer werden automatisch von der Anwendung verarbeitet.

Alle Server, die für den POP3-Zugriff konfiguriert sind, können für den Empfang von Rücksendungen verwendet werden, wenn sie beim Abholen der E-Mail die SMTP-Kopfzeilen „Message-ID“ beibehalten. Beispielsweise befinden sich Implementierungen mit Qmail, SendMail und Microsoft Exchange derzeit in der Produktionsumgebung. Einige Installationen von Lotus Notes/Domino haben jedoch ein Problem mit der Pflege von „Message-Id“-Headern aufgedeckt.

>[!CAUTION]
>
>Dieser Mail-Server ist möglicherweise mit hohen Belastungen konfrontiert: In der Anfangsphase können typische Listen eine Absprungrate von bis zu 10 % aufweisen (wenn Sie 100.000 Nachrichten senden, rechnen Sie mit 10.000 Absprüngen).
>
>Daher empfehlen wir, bei dieser Aufgabe nicht den Messaging-Server Ihres Unternehmens zu verwenden, da er stark betroffen sein kann.
>
>Es wird empfohlen, eine bestimmte Subdomain Ihres DNS und einen dedizierten Server für Bounce Messages zu konfigurieren.

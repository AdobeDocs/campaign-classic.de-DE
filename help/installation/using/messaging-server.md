---
product: campaign
title: Messaging-Server
description: Messaging-Server
feature: Installation, Instance Settings
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 9%

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

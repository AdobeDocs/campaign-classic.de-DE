---
title: Messaging-Server
seo-title: Messaging-Server
description: Messaging-Server
seo-description: null
page-status-flag: never-activated
uuid: d7de0405-23eb-4a0d-80a5-c75d661771bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 1556e87f-9d92-4548-a75a-4f44030ab8d5
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 4%

---


# Messaging-Server{#messaging-server}

Adobe Campaign verarbeitet ausgehende E-Mails nativ, für den Empfang von eingehenden Nachrichten, die mit zurückgesendeten E-Mails verknüpft sind (von mailer daemon), ist jedoch ein herkömmlicher E-Mail-Server erforderlich. Die auf diesem Server konfigurierten Postfächer werden automatisch von der Anwendung verarbeitet.

Alle für den POP3-Zugriff konfigurierten Server können für den Empfang von Rücksendungen verwendet werden, wenn die SMTP-Header &quot;Message-ID&quot;beim Abruf der E-Mail erhalten bleiben. Beispielsweise sind Implementierungen mit Qmail, SendMail und Microsoft Exchange derzeit in Produktion. Einige Installationen von Lotus Notes/domino haben jedoch ein Problem mit der Pflege von &quot;Message-Id&quot;-Headern aufgedeckt.

>[!CAUTION]
>
>Dieser E-Mail-Server muss möglicherweise schwere Lasten verarbeiten: In der Anfangsphase können typische Listen bis zu 10 % Absprungraten erzeugen (wenn Sie 100.000 Nachrichten senden, erhalten Sie 10.000 Absprünge).
>
>Deshalb empfehlen wir, Ihren Firma Messaging-Server für diese Aufgabe nicht zu verwenden, da dies stark beeinträchtigt werden kann.
>
>Es empfiehlt sich, eine bestimmte Subdomäne Ihres DNS und einen dedizierten Server für die Absprungmail zu konfigurieren.

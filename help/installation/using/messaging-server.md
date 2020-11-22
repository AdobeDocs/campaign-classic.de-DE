---
solution: Campaign Classic
product: campaign
title: Messaging-Server
description: Messaging-Server
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 3%

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

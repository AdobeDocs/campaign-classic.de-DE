---
product: campaign
title: Messaging-Server
description: Messaging-Server
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
badge-v7-prem: label="On-Premise und Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 12%

---

# Messaging-Server{#messaging-server}



Adobe Campaign verarbeitet ausgehende E-Mails nativ, doch ist ein herkömmlicher E-Mail-Server erforderlich, um eingehende Nachrichten zu erhalten, die mit zurückgegebenen E-Mails verknüpft sind (von Mailer-Daemons). Die auf diesem Server konfigurierten Postfächer werden automatisch von der Anwendung verarbeitet.

Alle für den POP3-Zugriff konfigurierten Server können für den Empfang von E-Mails verwendet werden, wenn sie beim Abruf der E-Mail die SMTP-Header &quot;Message-ID&quot;beibehalten. Beispielsweise sind Implementierungen mit Qmail, SendMail und Microsoft Exchange derzeit in Produktion. Einige Installationen von Lotus Notes/domino zeigten jedoch ein Problem bei der Pflege von &quot;Message-Id&quot;-Kopfzeilen.

>[!CAUTION]
>
>Dieser E-Mail-Server muss möglicherweise eine hohe Auslastung bewältigen: In ersten Phasen können typische Listen bis zu 10 % der Absprungraten produzieren (wenn Sie 100.000 Nachrichten senden, erwarten Sie 10.000 Bounces).
>
>Daher empfehlen wir, für diese Aufgabe nicht Ihren Unternehmens-Messaging-Server zu verwenden, da dies stark beeinträchtigt sein kann.
>
>Es wird empfohlen, eine bestimmte Subdomain Ihres DNS und einen dedizierten Server für Bounce Messages zu konfigurieren.

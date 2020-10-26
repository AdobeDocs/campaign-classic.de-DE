---
title: Datenbanken mit Blockierungslisten
seo-title: Datenbanken mit Blockierungslisten
description: Datenbanken mit Blockierungslisten
seo-description: null
page-status-flag: never-activated
uuid: 8a4a69f9-87d5-4044-bc55-76cdcb2e7800
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: eede254d-2b25-46ed-b10f-fa1d54780a75
translation-type: ht
source-git-commit: 75cbb8d697a95f4cc07768e6cf3585e4e079e171
workflow-type: ht
source-wordcount: '373'
ht-degree: 100%

---


# Datenbanken mit Blockierungslisten{#denylist-databases}

Mehrere Organisationen unterhalten Datenbanken mit IP-Adressen und Domains, die den Ruf haben, von Spammern verwendet zu werden. Zum besseren Verständnis, warum manche Nachrichten als Spam zurückgewiesen wurden, kann es hilfreich sein, sich diese Seiten anzusehen. Es besteht im Allgemeinen die Möglichkeit, das Entfernen von fälschlich auf diese Listen gesetzten Adressen zu fordern.

Diese Art von Datenbanken, die über einen DNS-Mechanismus abgefragt werden, nennt sich RBL (Real-time Blackhole Lists). Es gibt drei verschiedene RBL-Typen:

* Nach IP-Adresse: Auflistung von IP-Adressen, die Spam senden oder ihn wahrscheinlich weiterleiten.
* Nach Absender-Domain: Auflistung von Absender-Domains (vollständige Domain der Bounce-Message-Adresse), die Spam senden oder eine falsche Konfiguration aufweisen.
* Nach Webdomain: Auflistung der in den Link-URLs vorkommenden Domains (wie die bei den Registraren verzeichneten High-Level-Domains) sowie der im Spam-Inhalt enthaltenen Bilder. In Adobe Campaign handelt es sich bei der zu berücksichtigenden Domain im Allgemeinen um die für das Tracking verwendete Adresse.

Im Folgenden finden Sie eine Liste der am häufigsten verwendeten RBLs. Eine umfassendere Liste finden Sie unter [https://www.dnsstuff.com/](https://tools.dnsstuff.com/).

* **Spamhaus**

   Weiterführende Informationen finden Sie unter [https://www.spamhaus.org/](https://www.spamhaus.org/),

   wobei es sich um die wichtigste Datenbank handelt. In diese Liste aufgenommen zu werden, ist eine ernst zu nehmende Situation. In diesem Fall müssen Sie UNVERZÜGLICH reagieren und Geschäftsabteilungen, Verantwortliche für Zustellbarkeit und den Adobe-Campaign-Support informieren.

* **SpamCop**

   Weiterführende Informationen finden Sie unter [https://www.spamcop.net/](https://www.spamcop.net/),

   wobei es sich um eine der bekanntesten Datenbanken handelt. Sollte eine Ihrer IP-Adressen auf diese Liste geraten, bedeutet das im Allgemeinen, dass SpamCop-Benutzer Ihre Nachrichten als Spam deklariert oder dass Sie Ihre Nachrichten an eine Spam-Falle (honeypot) von SpamCop gesendet haben.

* **URIBL**

   Weiterführende Informationen finden Sie unter [https://www.uribl.com/](https://www.uribl.com/),

   wobei es sich um eine Liste handelt, in der Domains identifiziert sind, die regelmäßig in als Spam deklarierten Nachrichten auftauchen. Sollte Ihre Domain auf dieser Liste stehen, kann das einen starken Einfluss auf Ihre Zustellbarkeit haben. In diesem Fall sollten Sie unverzüglich die für Zustellbarkeit zuständigen Abteilungen sowie den Adobe-Campaign-Support informieren.

* **SURBL**

   Besuchen Sie die Seite [http://www.surbl.org/](http://www.surbl.org/),

   auf der Webseiten identifiziert werden, die regelmäßig in Spam auftauchen. Sollte Ihre Domain auf dieser Liste stehen, kann das einen starken Einfluss auf Ihre Zustellbarkeit haben. In diesem Fall sollten Sie unverzüglich die für Zustellbarkeit zuständigen Abteilungen sowie den Adobe-Campaign-Support informieren.

* **iX Manitu**

   Diese IP-Liste findet v. a. in Deutschland Verwendung. Besuchen Sie die Seite [https://www.heise.de/ix/nixspam/](https://www.heise.de/ix/nixspam/).

<!--* SORBS

  [https://www.nl.sorbs.net](https://www.nl.sorbs.net) compiles a list of IP addresses that are reputed to be dynamic IP address (i.e. attributed temporarily to ISP subscribers) or "open relay" addresses. Certain domains check whether the IP address of a sender is not listed on this site before accepting email. Checking the IP addresses on this site can prove useful.-->
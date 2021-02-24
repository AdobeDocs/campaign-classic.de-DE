---
solution: Campaign Classic
product: campaign
title: Erste Schritte mit der Verfolgung von personalisierten Links
description: Erfahren Sie, wie Sie Links in E-Mails schreiben, die personalisiert werden können, und wie Sie die Verfolgung in Campaign Classic unterstützen.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 151667637a12667f5eda1590e64e01de493be9ce
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# Erste Schritte mit der Verfolgung von personalisierten Links {#tracking-personalized-links}

Die Links in E-Mail-Inhalten, die Personalisierung enthalten, müssen eine bestimmte Syntax verfolgen.

Mit JavaScript in E-Mail-Inhalten (HTML oder Text) können Sie dynamische Inhalte mit zwei Einschränkungen erstellen und an die Empfänger senden:

* Das Skript kann nicht direkt auf die Datenbank zugreifen (SQL-Funktion und API-Funktionen sind nicht verfügbar),
* Adobe Campaign muss URLs erkennen können, damit Links verfolgt werden können (Zweck dieses Dokuments).

Zur Erkennung der Verfolgung bettet das Adobe Campaign [Tidy](http://www.html-tidy.org/) ein, um die HTML-Quelle zu analysieren und das Muster zu erkennen. Es werden alle URLs des Inhalts so Liste, dass sie einzeln verfolgt werden können. Adobe Campaign verwendet erneut Tidy, um die URL (`http://myurl.com`) durch eine URL zu ersetzen, die auf den Adobe Campaign-Umleitungsserver verweist.

Beispiel: `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` wird für einen bestimmten Empfänger durch folgende ersetzt: `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

Dabei gilt:

* &quot;h&quot;bedeutet HTML-Inhalt (oder &quot;t&quot;für Textinhalte).
* 617791 ist die Nachrichten-ID / wideLog-ID (hexadezimal).
* 71ffa3 ist die NmsDelivery-ID (hexadezimal).
* 71ffa8 ist die NmsTrackingUrl-ID (hexadezimal).
* p1, p2 usw. sind alle Parameter, die in der URL ersetzt werden sollen.

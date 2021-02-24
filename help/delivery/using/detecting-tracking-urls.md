---
solution: Campaign Classic
product: campaign
title: Erkennen von Tracking-URLs
description: Erfahren Sie mehr über das empfohlene Muster zur Verfolgung von URLs.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 151667637a12667f5eda1590e64e01de493be9ce
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 2%

---


# Erkennen von Tracking-URLs

## Beispiel für Nichterkennung

`<%= getURL("http://mynewsletter.com") %>` funktioniert und sendet den eigentlichen Inhalt der Webseite per E-Mail an die Empfänger. Aber keiner der Links wird verfolgt. Der Grund dafür ist, dass die MTA `"<%=getURL(..."` für jede E-Mail vor dem Senden ausführt. Es kann für jeden Empfänger unterschiedlich sein, sodass Adobe Campaign die zu verfolgenden URLs nicht kennt und ihnen eine Tag-ID zuweist.

Wenn die herunterzuladende Seite für alle Empfänger gleich ist, sollten Sie Folgendes tun:

`<%@ include url="http://mynewsletter.com" %>`

In diesem Fall wird die Seite während der Analyse vor der Verfolgungserkennung heruntergeladen. Dadurch kann Adobe Campaign die Links ermitteln, eine Tag-ID zuweisen und sie nachverfolgen.

## Empfohlenes Muster

Nach der Verarbeitung der `<%@`-Anweisungen hat die nachzuverfolgende URL die folgende Syntax: `<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>Alle anderen Muster werden nicht von der Adobe unterstützt und sollten vermieden werden, um potenzielle Sicherheitslücken zu vermeiden.

## Warnungen unter http://&lt;%=myURL%>

Die `<a href="http://<%=myURL%>">`-Syntax ist nicht sicher und wird nicht empfohlen, da:

* Durch die Zündung können einige Links falsch gepatcht werden, was zufällig geschehen kann. Das typische Symptom ist ein HTML-Element, das in den E-Mail-Testversänden, aber nicht in der Vorschau sichtbar ist.
* Das Entfernen der URL ist problematisch, einige Zeichen in der URL können Probleme verursachen.
* Sie können keinen Parameter mit dem Namen ID in Konflikt mit Parametern in der Umleitungs-URL haben.
* Das Interesse an der Verfolgung ist dann auf Statistiken über den Versand beschränkt, da Adobe Campaign alle möglichen Werte von &quot;myURL&quot;gleichgültig verfolgt.

Weitere Informationen finden Sie auf [dieser Seite](https://helpx.adobe.com/de/campaign/kb/acc-security.html#privacy).


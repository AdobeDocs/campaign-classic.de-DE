---
product: campaign
title: Erkennen von Tracking-URLs
description: Erfahren Sie mehr über die empfohlenen Muster zum Tracken von URLs.
feature: Monitoring
role: User, Developer
exl-id: 7611d6a1-6c55-4ba3-b905-58426c944991
TQID: https://experienceleague.adobe.com/F63e0G1uyp-tXDiBk9cau5P-HBHttCkiFD2yw657RBw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 298
ht-degree: 100%

---

# Erkennen von Tracking-URLs

## Beispiel einer Nichterkennung

`<%= getURL("http://mynewsletter.com") %>` funktioniert und sendet den eigentlichen Inhalt der Web-Seite per E-Mail an die Empfänger. Es wird jedoch keiner der Links verfolgt. Der Grund dafür ist, dass der MTA `"<%=getURL(..."` für jede E-Mail vor dem Senden ausführt. Dies kann für jeden Empfänger unterschiedlich sein, weswegen Adobe Campaign die zu verfolgenden URLs nicht kennt und ihnen eine Tag-ID zuweist.

Wenn die herunterzuladende Seite für alle Empfänger gleich ist, sollten Sie Folgendes tun:

`<%@ include url="http://mynewsletter.com" %>`

In diesem Fall wird die Seite während der Analyse vor der Tracking-Erkennung heruntergeladen. Dadurch kann Adobe Campaign die Links ermitteln, eine Tag-ID zuweisen und sie verfolgen.

## Empfohlenes Muster

Nach der Verarbeitung der `<%@`-Anweisungen hat die zu verfolgende URL die folgende Syntax: `<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>Alle anderen Muster werden von Adobe nicht unterstützt und sollten vermieden werden, um potenzielle Sicherheitslücken zu verhindern.

## Ungesichertes Muster

Wenn Sie personalisierte Links zu Ihrem Inhalt hinzufügen, achten Sie darauf, dass im Hostname-Teil der URL keine Personalisierung vorhanden ist. So lassen sich potenzielle Sicherheitslücken verhindern. Weiterführende Informationen finden Sie auf [dieser Seite](../../installation/using/privacy.md#url-personalization).

Die Syntax `<a href="http://<%=myURL%>">` ist beispielsweise **nicht sicher** und muss vermieden werden.

* Die Verwendung dieser Syntax kann zu Sicherheitsproblemen führen, wenn der von Adobe Campaign generierte Link einen oder mehrere Parameter enthält.
* Tidy kann einige der Links fälschlicherweise patchen, was zufällig passieren kann. Das typische Symptom ist ein HTML-Element, das in den E-Mail-Testsendungen sichtbar ist, nicht jedoch in der Vorschau.
* Das Maskieren der URL ist problematisch, einige Zeichen in der URL können Probleme verursachen.
* In der Weiterleitungs-URL darf kein Parameter mit einem Parameter namens &quot;ID&quot; in Konflikt stehen.
* Das Tracking beschränkt sich dann auf Statistiken über den Versand, da Adobe Campaign ohne Differenzierung alle möglichen Werte von &quot;myURL&quot; verfolgt.

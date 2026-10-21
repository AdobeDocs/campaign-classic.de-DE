---
product: campaign
title: Erkennen von Tracking-URLs
description: Erfahren Sie mehr über die empfohlenen Muster zum Tracken von URLs.
feature: Monitoring
role: User, Developer
exl-id: 7611d6a1-6c55-4ba3-b905-58426c944991
TQID: 'https://experienceleague.adobe.com/F63e0G1uyp-tXDiBk9cau5P-HBHttCkiFD2yw657RBw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: d7e5f68c0d2e0b94fd5cfdf2981bed29f33d9f62
workflow-type: ht
source-wordcount: '247'
ht-degree: 100%
---
# Erkennen von Tracking-URLs

Adobe Campaign erkennt während der Versandanalyse in Ihrem Inhalt die zu trackenden URLs.

Im Zuge der Umstellung von Campaign v7 auf v8 wurde die Campaign Classic-Dokumentation optimiert und neu organisiert. Allgemeine Funktionen sind jetzt nur noch in der Dokumentation zu Campaign v8 verfügbar. Weitere Informationen dazu, wie URLs erkannt werden und welche Muster zu verwenden sind, finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/analytics/tracking/personalized-links#url-detection){target=_blank}.

[![Bild](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/analytics/tracking/personalized-links#url-detection){target=_blank}

## Ungesichertes Muster

Wenn Sie personalisierte Links zu Ihrem Inhalt hinzufügen, achten Sie darauf, dass im Hostname-Teil der URL keine Personalisierung vorhanden ist. So lassen sich potenzielle Sicherheitslücken verhindern. Weiterführende Informationen finden Sie auf [dieser Seite](../../installation/using/privacy.md#url-personalization).

Die Syntax `<a href="http://<%=myURL%>">` ist beispielsweise **nicht sicher** und muss vermieden werden.

* Die Verwendung dieser Syntax kann zu Sicherheitsproblemen führen, wenn der von Adobe Campaign generierte Link einen oder mehrere Parameter enthält.
* Tidy kann einige der Links fälschlicherweise patchen, was zufällig passieren kann. Das typische Symptom ist ein HTML-Element, das in den E-Mail-Testsendungen sichtbar ist, nicht jedoch in der Vorschau.
* Das Maskieren der URL ist problematisch, einige Zeichen in der URL können Probleme verursachen.
* In der Weiterleitungs-URL darf kein Parameter mit einem Parameter namens &quot;ID&quot; in Konflikt stehen.
* Das Tracking beschränkt sich dann auf Statistiken über den Versand, da Adobe Campaign ohne Differenzierung alle möglichen Werte von &quot;myURL&quot; verfolgt.

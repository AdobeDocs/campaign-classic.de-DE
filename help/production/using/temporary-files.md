---
product: campaign
title: Temporäre Dateien
description: Temporäre Dateien
feature: Monitoring
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
TQID: https://experienceleague.adobe.com/eZnGm-WK-etrLLbJ-aeuSqakYAfPNBQd2q3JlEd4rE8
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 15%
---
# Temporäre Dateien{#temporary-files}



Fehlermeldungen wie die folgende können (insbesondere in Versandlogs) angezeigt werden, wenn das System in die Produktion geht:

*Datei &#39;/tmp/tmp0000.tmp&#39; kann nicht in /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml umbenannt werden;(errno=18, ungültige geräteübergreifende Verknüpfung) (iRc=-52)*

Die Ursache ist wie folgt:

Adobe Campaign generiert temporäre Dateien unter **/tmp** und benennt sie dann um, um sie nach **/usr/local/neolane/nl6/var** zu verschieben. Dieser Fehler tritt auf, wenn beide Ordner (**/tmp** und **/usr/local/neolane/nl6/var**, was in der Tat eine symbolische Verknüpfung zu **/var/nl6** ist) verschiedenen Geräten entsprechen. Der Befehl **df** wird zur Überprüfung verwendet.

Um dieses Problem zu beheben, müssen die temporären Dateien auf demselben Gerät wie das Ziel generiert werden.

Führen Sie beispielsweise Folgendes aus:

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

Fügen Sie dann hinzu:

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```

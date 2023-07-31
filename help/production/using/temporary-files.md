---
product: campaign
title: Temporäre Dateien
description: Temporäre Dateien
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
badge-v7-prem: label="On-Premise und Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 14%

---

# Temporäre Dateien{#temporary-files}



Fehlermeldungen wie die folgenden werden möglicherweise angezeigt (insbesondere in Versandlogs), wenn das System in die Produktion aufgenommen wird:

*Die Datei &quot;/tmp/tmp0000.tmp&quot;kann nicht in /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml umbenannt werden;(errno=18, Invalid cross-device link) (iRc=-52)*

Die Ursache lautet wie folgt:

Adobe Campaign generiert temporäre Dateien unter **/tmp** und benennt sie dann um, um sie in **/usr/local/neolane/nl6/var**. Dieser Fehler tritt auf, wenn beide Ordner (**/tmp** und **/usr/local/neolane/nl6/var**, was in der Tat eine symbolische Verknüpfung zu **/var/nl6**) verschiedenen Geräten entsprechen. Die **df** -Befehl wird zur Überprüfung verwendet.

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

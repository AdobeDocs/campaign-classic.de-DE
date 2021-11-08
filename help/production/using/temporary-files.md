---
product: campaign
title: Temporäre Dateien
description: Temporäre Dateien
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 4%

---

# Temporäre Dateien{#temporary-files}

![](../../assets/v7-only.svg)

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

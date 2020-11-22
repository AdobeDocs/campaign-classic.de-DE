---
solution: Campaign Classic
product: campaign
title: Temporäre Dateien
description: Temporäre Dateien
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 4%

---


# Temporäre Dateien{#temporary-files}

Wenn Fehlermeldungen wie die folgenden angezeigt werden (insbesondere in Versandlogs), wenn das System in Produktion genommen wird:

**Datei &quot;/tmp/tmp0000.tmp&quot;kann nicht in /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml umbenannt werden;(errno=18, Ungültiger Link über mehrere Geräte) (iRc=-52)**

Die Ursache lautet:

Adobe Campaign generiert temporäre Dateien unter **/tmp** und benennt sie dann um, um sie in **/usr/local/neolane/nl6/var** zu verschieben. Dieser Fehler tritt auf, wenn beide Ordner (**/tmp** und **/usr/local/neolane/nl6/var**, die eigentlich eine symbolische Verknüpfung zu **/var/nl6** ist) unterschiedlichen Geräten entsprechen. Der **Befehl &quot;df** &quot;wird zur Überprüfung verwendet.

Um dieses Problem zu beheben, müssen die temporären Dateien auf demselben Gerät wie das Ziel generiert werden. Beispielsweise durch Ausführung:

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

und fügen Sie dann Folgendes hinzu:

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```


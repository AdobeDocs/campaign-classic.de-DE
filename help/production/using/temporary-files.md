---
title: Temporäre Dateien
seo-title: Temporäre Dateien
description: Temporäre Dateien
seo-description: null
page-status-flag: never-activated
uuid: ae7ec619-e93f-41fb-ba7c-fcbcf4cba84f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: f18237b0-ef54-46a6-9c14-34b038f9de18
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2a11a73b0679c0a65dc10f71869bf2a6c6efc008

---


# Temporäre Dateien{#temporary-files}

Wenn Fehlermeldungen wie die folgenden angezeigt werden (insbesondere in Lieferprotokollen), wenn das System in die Produktion aufgenommen wird:

**Datei &quot;/tmp/tmp0000.tmp&quot;kann nicht in /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml umbenannt werden;(errno=18, Ungültiger Link über mehrere Geräte) (iRc=-52)**

Die Ursache lautet:

Adobe Campaign generiert temporäre Dateien unter **/tmp** und benennt sie dann um, um sie in **/usr/local/neolane/nl6/var** zu verschieben. Dieser Fehler tritt auf, wenn beide Ordner (**/tmp** und **/usr/local/neolane/nl6/var**, die eigentlich eine symbolische Verknüpfung zu **/var/nl6** ist) unterschiedlichen Geräten entsprechen. Der **Befehl &quot;df** &quot;wird zur Überprüfung verwendet.

Um dieses Problem zu beheben, müssen die temporären Dateien auf demselben Gerät wie das Ziel generiert werden. Beispiel:

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

und fügen Sie dann Folgendes hinzu:

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```


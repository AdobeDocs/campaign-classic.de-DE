---
title: Und-Verknüpfung
seo-title: Und-Verknüpfung
description: Und-Verknüpfung
seo-description: null
page-status-flag: never-activated
uuid: 8234d6cd-0e9b-4187-9ddf-9e1f86aa1b9a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 075206aa-ff7b-4fa8-a05d-14a29fb119ba
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Und-Verknüpfung{#and-join}

Bei einer Und-Verknüpfung wird die ausgehende Transition erst aktiviert, wenn alle eingehenden Transitionen aktiviert wurden. Dadurch lässt sich sicherstellen, dass gewisse Aktivitäten beendet sind, bevor die Workflow-Ausführung fortgesetzt wird.

Die an die ausgehende Transition übermittelte Population entspricht der Hauptmenge, die zuvor aus den eingehenden Transitionen der Aktivität bestimmt wurde.

Die ausgehende Transition kann nur eine der eingehenden Populationen enthalten. Wenn die Hauptmenge nicht bestimmt wurde, wird die an die ausgehende Transition übermittelte Population zufällig ausgewählt.

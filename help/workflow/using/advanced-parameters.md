---
product: campaign
title: Erweiterte Parameter
description: Erweiterte Parameter
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Data Management
exl-id: 6c90ac2f-0d2b-48b0-9245-3e5e3a3d027c
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: ht
source-wordcount: '541'
ht-degree: 100%

---

# Erweiterte Parameter{#advanced-parameters}



Der Bildschirm der Workflow-Eigenschaften enthält einen **[!UICONTROL Erweitert]**-Tab, welcher beispielsweise die Konfiguration des Verhaltens bei Fehlern und die Ausführungsdauer sowie die Erstellung eines Initialisierungsscripts erlaubt. Der Bildschirm erscheint je nach Aktivität in vereinfachter oder detaillierter Form:

* vereinfacht für die Aktivität **[!UICONTROL Start]** und **[!UICONTROL Ende]**;

   ![](assets/wf-advanced-basic.png)

* detailliert für die **[!UICONTROL Abfrageaktivität]**.

   ![](assets/wf-advanced-full.png)

Im Folgenden werden die im **[!UICONTROL Erweitert]**-Tab jeweils auszufüllenden Felder beschrieben.

## Name {#name}

Dieses Feld enthält den internen Namen der Aktivität.

## Bild {#image}

In diesem Feld können Sie das mit einer Aktivität verknüpfte Bild ändern. Weiterführende Informationen finden Sie unter [Ändern von Aktivitäts-Bildern](managing-activity-images.md).

## Ausführung {#execution}

Definieren Sie hier die Art der Aufgabenausführung. Drei Optionen stehen zur Verfügung:

In der Regel werden diese Optionen im Diagramm durch Rechtsklick auf die Aktivität ausgewählt.

* **[!UICONTROL Normal]** - die Aufgabe wird ausgeführt.
* **[!UICONTROL Nicht aktivieren]** - die Aufgabe sowie alle im selben Zweig folgenden Aktivitäten werden nicht ausgeführt.
* **[!UICONTROL Aktivieren aber nicht ausführen]** - die Aufgabe sowie alle im selben Zweig folgenden Aktivitäten werden mit sofortiger Wirkung ausgesetzt. Dies ist v. a. dann interessant, wenn die Aufgabe in Ihrer Anwesenheit gestartet werden soll. Klicken Sie zum gewünschten Ausführungszeitpunkt mit der rechten Maustaste auf eine Aktivität und wählen Sie **[!UICONTROL Normale Ausführung]**.

## Affinität {#affinity}

Es besteht die Möglichkeit, die Ausführung eines Workflows oder einer Workflow-Aktivität auf einem bestimmten Rechner zu erzwingen. Hierzu müssen eine oder mehrere Tendenzwerte auf Workflow- oder Aktivitätsniveau definiert werden.

Die Konfiguration von Workflows mit hoher Disponibilität wird in diesem [Abschnitt](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities) erläutert.


## Max. Ausführungsdauer {#max--execution-period}

In diesem Feld kann eine maximale Dauer für die Workflow-Ausführung bestimmt werden. Wenn eine Aufgabe die angegebene Dauer überschreitet, zeigt das **[!UICONTROL Instanz-Monitoring]** einen Warnhinweis bezüglich des Workflows an. Auf diese Seite kann von der Startseite aus über die Rubrik **[!UICONTROL Monitoring]** zugegriffen werden.****

## Verhalten {#behavior}

In diesem Feld wird das Verhalten des Workflows im Fall von asynchronen Aufgaben bestimmt. Zwei Optionen stehen zur Verfügung:

* **[!UICONTROL Mehrere autorisierte Aufgaben]** - mehrere Aufgaben können gleichzeitig ausgeführt werden.
* **[!UICONTROL Die laufende Aufgabe ist prioritär]** - solange eine Aufgabe läuft, wird keine neue Aufgabe gestartet.

## Zeitzone {#time-zone}

In diesem Feld können Sie die Zeitzone der Aktivität auswählen. Weiterführende Informationen finden Sie unter [Verwalten von Zeitzonen](managing-time-zones.md).

## Fehler {#in-case-of-errors}

In diesem Feld wird angegeben, wie mit Fehlern bei der Aktivität umgegangen werden soll. Zwei Optionen stehen zur Verfügung:

* **[!UICONTROL Prozess aussetzen]**: Der Workflow wird automatisch angehalten. Der Status ändert sich in **[!UICONTROL Fehlgeschlagen]**. Nach Lösung des Problems kann der Workflow neu gestartet werden.
* **[!UICONTROL Ignorieren]**: Diese Aufgabe sowie alle folgenden Aufgaben (in derselben Verzweigung) werden nicht ausgeführt. Diese Konfiguration empfiehlt sich bei wiederkehrenden Aufgaben. Wenn die Verzweigung im weiteren Verlauf eine Planungsaktivität enthält, wird diese automatisch zum nächsten geplanten Zeitpunkt ausgelöst.
* **[!UICONTROL Abbruch bei Fehler]**: Der Workflow wird automatisch angehalten und kann nicht neu gestartet werden. Der Status ändert sich in **[!UICONTROL Fehlgeschlagen]**.

## Initialisierungsskript {#initialization-script}

In diesem Feld können Sie Variablen initialisieren oder Aktivitätseigenschaften ändern. Weiterführende Informationen finden Sie unter [Scripts/JavaScript-Templates](javascript-scripts-and-templates.md).

## Kommentar {#comment}

Hier kann eine Beschreibung eingegeben werden. Es handelt sich um ein freies Textfeld.****

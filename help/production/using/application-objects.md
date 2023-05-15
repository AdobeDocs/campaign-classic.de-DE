---
product: campaign
title: Anwendungsobjekte
description: Anwendungsobjekte
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: fb4798d7-0a2c-455b-86b6-3dcb5fd25c82
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 4%

---

# Anwendungsobjekte{#application-objects}



Integrierte Objekte sollten überwacht werden, und es ist wichtig zu verhindern, dass sie zu stark wachsen.

## Sequenz von IDs {#sequence-of-ids}

Adobe Campaign verwendet eine ID-Sequenz, die entsprechend verwendet werden muss: **xtkNewId**. Wenn die Sequenz sehr schnell verwendet wird (d. h. ab 100.000 pro Tag), müssen Sie sicherstellen, dass sie Ihren Geschäftsanforderungen entspricht, z. B. dem Versand von Millionen E-Mails pro Tag. Es ist möglich, eine eigene Sequenz für bestimmte Tabellen zu definieren. Sie können einen Workflow zur Überwachung der ID-Nutzung einrichten.

Wenn die Sequenz mehr als 2 Milliarden erreicht (2.147.483.648 ist die genaue Zahl), geht sie zurück auf null. Es muss vermieden werden und es gibt Probleme, weshalb diese Reihenfolge überwacht werden muss.

Um dies bei großen Tabellen zu verhindern, sollten Sie eine bestimmte Sequenz verwenden. Dies kann mit der **pkSequence** -Attribut im Schema.

Hochfrequente Workflows, die viele Protokolle erstellen, verbrauchen viele IDs. Es wird daher dringend empfohlen, zu viele Protokolle und hohe Frequenzen in Workflows zu vermeiden.

Wenn die Sequenz bereits einen Zyklus durchlaufen hat, besteht die beste Lösung darin, zu negativen IDs zu wechseln, beginnend bei -2.147.483.648.

## Ordner {#folders}

Es sollte in jeder Instanz weniger als 1000 Ordner geben. Wenn mehr Ordner vorhanden sind, kann dies zu Leistungsproblemen beim Campaign-Client führen. Sie können einen Überwachungsauftrag einrichten, um die Anzahl der Ordner, Workflows usw. zu zählen und regelmäßig Berichte zu erstellen.

Diese Methode hebt auch Benutzer hervor, die zu viele Objekte erstellen.

## Sendungen {#deliveries}

Es sollten zu jedem Zeitpunkt weniger als 1000 Sendungen in der Instanz durchgeführt werden. Viele Sendungen verbrauchen Speicherplatz in der Datenbank und verursachen Probleme. Eine Instanz, die mehr als 10 Sendungen pro Tag erstellt, muss entsprechend den Geschäftsanforderungen geprüft werden. Erwägen Sie die Verwendung von fortlaufenden Sendungen, um weniger Sendungen zu erstellen. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../workflow/using/continuous-delivery.md).

Sendungen, die älter als zwei Jahre sind, sollten aus der Instanz gelöscht werden.

## Dateien {#files}

Die Anzahl der Dateien auf der Festplatte des Anwendungsservers sollte nicht unbegrenzt steigen.

Import-Workflows erstellen Dateien und verursachen so eine Festplattenerweiterung. Dies lässt sich durch Verwendung des Standards [Datei-Wächter](../../workflow/using/file-collector.md) Aktivität. Der Datei-Wächter verschiebt Dateien in einen temporären Ordner und löscht sie automatisch.

Wenn ein Workflow Dateien importiert und nicht die Standardfunktionen nutzt, muss er bereinigt werden, um Speicherplatz auf ein Minimum zu beschränken.

## Transaktionsdaten und -protokolle {#transactional-data-and-logs}

Alle [Workflow](../../workflow/using/data-life-cycle.md#work-table) -Import von Daten in Adobe Campaign bewirkt, dass die Datenbankgröße zunimmt.

Vergewissern Sie sich, dass die Bereinigungs- oder Bereinigungs-Workflows ausgeführt werden und dass die Datensätze effektiv bereinigt werden. Alle Transaktionsdaten und -protokolle müssen bereinigt werden. Die Bereinigungsaufgabe bereinigt nur die Standardtabellen: Tracking und Broadlogs. Bestimmte Tabellen müssen durch bestimmte Workflows bereinigt werden. Weitere Informationen finden Sie in [diesem Abschnitt](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

Achten Sie auf Alterungsdaten, indem Sie das älteste Erstellungsdatum der Datensätze überprüfen.

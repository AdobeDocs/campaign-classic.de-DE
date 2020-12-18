---
solution: Campaign Classic
product: campaign
title: Anwendungsobjekte
description: Anwendungsobjekte
audience: production
content-type: reference
topic-tags: database-maintenance
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 4%

---


# Anwendungsobjekte{#application-objects}

Integrierte Objekte sollten überwacht werden, und es ist wichtig zu verhindern, dass sie zu viel wachsen.

## Sequenz der IDs {#sequence-of-ids}

Adobe Campaign verwendet eine ID-Sequenz, die entsprechend verwendet werden muss: **xtkNewId**. Wenn die Sequenz sehr schnell genutzt wird (d. h. ab 100.000 pro Tag), müssen Sie sicherstellen, dass sie mit Ihren Geschäftsanforderungen übereinstimmt, z. B. das Versenden von Millionen E-Mails pro Tag. Es ist möglich, eine eigene Sequenz für bestimmte Tabellen zu definieren. Sie können einen Workflow zur Überwachung der ID-Nutzung einrichten.

Wenn die Sequenz mehr als 2 Milliarden erreicht (2.147.483.648 ist die exakte Zahl), geht sie zurück auf Null. Es muss vermieden und Probleme geschaffen werden, weshalb diese Sequenz überwacht werden muss.

Um dies bei großen Tabellen zu verhindern, sollten Sie eine bestimmte Sequenz verwenden. Dies kann mit dem Attribut **pkSequence** im Schema erfolgen.

Hochfrequente Workflows, die viele Protokolle erzeugen, benötigen viele IDs. Es wird daher dringend empfohlen, zu viele Protokolle und hohe Frequenzen in Workflows zu vermeiden.

Wenn die Sequenz bereits abgebrochen wurde, ist es am besten, zu negativen IDs zu wechseln, beginnend mit -2.147.483.648.

## Ordner {#folders}

Es sollten auf jeder Instanz weniger als 1000 Ordner vorhanden sein. Wenn mehr Ordner vorhanden sind, kann dies zu Leistungsproblemen mit dem Kampagne-Client führen. Sie können einen Überwachungsauftrag einrichten, um die Anzahl der Ordner, Workflows usw. zu zählen und regelmäßig einen Bericht zu erstellen.

Bei dieser Methode werden auch Benutzer hervorgehoben, die zu viele Objekte erstellen.

## Sendungen {#deliveries}

Die Instanz sollte immer weniger als 1000 Versand umfassen. Viele Versand verbrauchen Speicherplatz in der Datenbank und verursachen Probleme. Eine Instanz, die mehr als 10 Versand pro Tag erstellt, muss anhand der Geschäftsanforderungen geprüft werden. Erwägen Sie, fortlaufende Versand zu verwenden, um weniger Versand zu erstellen. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../workflow/using/continuous-delivery.md).

Versände, die älter als zwei Jahre sind, sollten aus dem Vorfall entfernt werden.

## Dateien {#files}

Die Anzahl der Dateien auf dem Anwendungsserver sollte nicht unbegrenzt steigen.

Importieren Sie Workflows erstellen Sie Dateien und verursachen Sie dadurch eine Festplattenerweiterung. Dies kann mithilfe der standardmäßigen Aktivität [Datei-Wächter](../../workflow/using/file-collector.md) verhindert werden. Der Dateisammler verschiebt Dateien in einen temporären Ordner und löscht sie automatisch.

Wenn ein Workflow Dateien importiert und nicht die Standardfunktionen nutzt, muss er bereinigt werden, damit der Speicherplatz auf der Festplatte auf ein Minimum beschränkt bleibt.

## Transaktionsdaten und Protokolle {#transactional-data-and-logs}

Jeder [Workflow](../../workflow/using/data-life-cycle.md#work-table), der Daten in Adobe Campaign importiert, führt zu einer Vergrößerung der Datenbankgröße.

Vergewissern Sie sich, dass Workflows bereinigt oder bereinigt werden, und löschen Sie die Datensätze effektiv. Alle Transaktionsdaten und Protokolle müssen bereinigt werden. Die Bereinigungstabellen werden nur von der Aufgabe bereinigt: Tracking und breite Protokolle. Spezifische Tabellen müssen durch bestimmte Workflows bereinigt werden. Siehe [diesen Abschnitt](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

Achten Sie auf ältere Transaktionsdaten, indem Sie das älteste Erstellungsdatum der Datensätze überprüfen.

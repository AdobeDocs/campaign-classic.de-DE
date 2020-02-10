---
title: Anwendungsobjekte
seo-title: Anwendungsobjekte
description: Anwendungsobjekte
seo-description: null
page-status-flag: never-activated
uuid: 84fbad0f-872d-4aca-8ea9-007577be076d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: 24d4875b-81fa-4bf3-8cf0-e6998bec4949
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e1937c1ddcbde092a22f4fe8c50d3d72b02cfeed

---


# Anwendungsobjekte{#application-objects}

Integrierte Objekte sollten überwacht werden, und es ist wichtig zu verhindern, dass sie zu viel wachsen.

## Sequenz von IDs {#sequence-of-ids}

Adobe Campaign verwendet eine ID-Sequenz, die entsprechend genutzt werden muss: **xtkNewId**. Wenn die Sequenz sehr schnell genutzt wird (d. h. ab 100.000 pro Tag), müssen Sie sicherstellen, dass sie mit Ihren Geschäftsanforderungen übereinstimmt, z. B. das Senden von Millionen E-Mails pro Tag. Es ist möglich, eine eigene Sequenz für bestimmte Tabellen zu definieren. Sie können einen Workflow zur Überwachung der ID-Nutzung einrichten.

Wenn die Sequenz mehr als 2 Milliarden erreicht (2.147.483.648 ist die exakte Zahl), geht sie zurück auf Null. Es muss vermieden und Probleme geschaffen werden, weshalb diese Sequenz überwacht werden muss.

Um dies bei großen Tabellen zu verhindern, sollten Sie eine bestimmte Sequenz verwenden. Dies kann mit dem **pkSequence** -Attribut im Schema durchgeführt werden.

Hochfrequente Arbeitsabläufe, die viele Protokolle erzeugen, benötigen viele IDs. Es wird daher dringend empfohlen, zu viele Protokolle und hohe Frequenzen in Workflows zu vermeiden.

Wenn die Sequenz bereits abgebrochen wurde, ist es am besten, zu negativen IDs zu wechseln, beginnend mit -2.147.483.648.

## Ordner {#folders}

Es sollten auf jeder Instanz weniger als 1000 Ordner vorhanden sein. Wenn mehr Ordner vorhanden sind, kann dies zu Leistungsproblemen mit dem Campaign-Client führen. Sie können einen Überwachungsauftrag einrichten, um die Anzahl der Ordner, Arbeitsabläufe usw. zu zählen und regelmäßig einen Bericht zu erstellen.

Bei dieser Methode werden auch Benutzer hervorgehoben, die zu viele Objekte erstellen.

## Deliveries {#deliveries}

Es sollten zu jedem Zeitpunkt weniger als 1000 Auslieferungen auf dem Vorkommen erfolgen. Viele Auslieferungen verbrauchen Speicherplatz in der Datenbank und verursachen Probleme. Ein Fall, bei dem mehr als 10 Auslieferungen pro Tag erstellt werden, muss auf Geschäftsanforderungen hin überprüft werden. Erwägen Sie, kontinuierliche Auslieferungen zu verwenden, um weniger Auslieferungen zu erzielen. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../workflow/using/continuous-delivery.md).

Lieferungen, die älter als zwei Jahre sind, sollten aus dem Vorfall entfernt werden.

## Dateien {#files}

Die Anzahl der Dateien auf dem Anwendungsserver sollte nicht unbegrenzt steigen.

Importieren von Workflows erstellen Dateien und verursachen somit eine Festplattenerweiterung. Dies kann durch die Verwendung der standardmäßigen [Dateikollektor](../../workflow/using/file-collector.md) verhindert werden. Der Dateisammler verschiebt Dateien in einen temporären Ordner und löscht sie automatisch.

Wenn ein Workflow Dateien importiert und nicht die Standardfunktionen nutzt, muss er bereinigt werden, damit der Speicherplatz auf der Festplatte auf ein Minimum beschränkt bleibt.

## Transaktionsdaten und -protokolle {#transactional-data-and-logs}

Jeder [Workflow](../../workflow/using/executing-a-workflow.md#work-table) , der Daten in Adobe Campaign importiert, sorgt für eine größere Datenbankgröße.

Überprüfen Sie, ob Arbeitsabläufe zum Bereinigen oder Bereinigen ausgeführt werden, und entfernen Sie die Datensätze effektiv. Alle Transaktionsdaten und Protokolle müssen bereinigt werden. Die Bereinigungsaufgabe bereinigt nur die Standardtabellen: Tracking und breite Protokolle. Spezifische Tabellen müssen durch bestimmte Arbeitsabläufe bereinigt werden. Siehe [diesen Abschnitt](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

Achten Sie auf ältere Transaktionsdaten, indem Sie das älteste Erstellungsdatum der Datensätze überprüfen.

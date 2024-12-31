---
product: campaign
title: Anwendungsobjekte
description: Anwendungsobjekte
feature: Monitoring
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: fb4798d7-0a2c-455b-86b6-3dcb5fd25c82
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 4%

---

# Anwendungsobjekte{#application-objects}



Integrierte Objekte sollten überwacht werden. Es ist daher wichtig, zu verhindern, dass sie zu stark anwachsen.

## ID-Sequenz {#sequence-of-ids}

Adobe Campaign verwendet eine ID-Sequenz, die entsprechend genutzt werden muss: **xtkNewId**. Wenn die Sequenz sehr schnell verwendet wird (d. h. ab 100.000 pro Tag), müssen Sie sicherstellen, dass sie mit Ihren Geschäftsanforderungen übereinstimmt, z. B. indem Sie täglich Millionen von E-Mails senden. Es ist möglich, eine dedizierte Sequenz für bestimmte Tabellen zu definieren. Sie können einen Workflow zur Überwachung der ID-Nutzung einrichten.

Wenn die Sequenz mehr als 2 Milliarden erreicht (2.147.483.648 ist die exakte Zahl), geht sie zurück auf null. Sie muss vermieden werden und schafft Probleme, weshalb diese Abfolge überwacht werden muss.

Um dies bei großen Tabellen zu verhindern, sollten Sie eine bestimmte Sequenz verwenden. Dies kann mit dem Attribut **pkSequence** im Schema erfolgen.

Häufige Workflows, die viele Protokolle erstellen, verbrauchen viele IDs. Es wird daher dringend empfohlen, zu viele Protokolle und hohe Häufigkeiten in Workflows zu vermeiden.

Wenn die Sequenz bereits getaktet ist, ist die beste Lösung, auf negative IDs umzuschalten, beginnend bei -2.147.483.648.

## Ordner {#folders}

Es sollte auf jeder Instanz weniger als 1000 Ordner geben. Mehr Ordner als diese Anzahl kann zu Leistungsproblemen mit dem Campaign-Client führen. Sie können einen Überwachungsauftrag einrichten, um die Anzahl der Ordner, Workflows usw. zu zählen und Berichte in regelmäßigen Abständen zu erstellen.

Diese Methode hebt auch Benutzer hervor, die zu viele Objekte erstellen.

## Sendungen {#deliveries}

Es sollten zu jedem Zeitpunkt weniger als 1.000 Sendungen in der Instanz vorhanden sein. Viele Sendungen belasten den Datenbankspeicherplatz und verursachen Probleme. Eine Instanz, die mehr als 10 Sendungen pro Tag erstellt, muss mit den Geschäftsanforderungen abgeglichen werden. Verwenden Sie fortlaufende Sendungen, um weniger Sendungen zu erstellen. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../workflow/using/continuous-delivery.md).

Sendungen, die älter als zwei Jahre sind, sollten aus der Instanz gelöscht werden.

## Dateien {#files}

Die Anzahl der Dateien auf dem Anwendungsserverdatenträger sollte nicht unbegrenzt ansteigen.

Import-Workflows erstellen Dateien und führen daher zu einer Festplattenerweiterung. Dies kann mithilfe der standardmäßigen Aktivität [Datei-Wächter](../../workflow/using/file-collector.md) verhindert werden. Der Datei-Wächter verschiebt Dateien in einen temporären Ordner und löscht sie automatisch.

Wenn ein Workflow Dateien importiert und nicht die Standardfunktionen verwendet, muss er bereinigt werden, um den Speicherplatz auf ein Minimum zu beschränken.

## Transaktionsdaten und -protokolle {#transactional-data-and-logs}

Jeder [Workflow](../../workflow/using/data-life-cycle.md#work-table) der Daten in Adobe Campaign importiert, vergrößert die Datenbank entsprechend.

Überprüfen Sie, ob Bereinigungs- oder Bereinigungs-Workflows ausgeführt werden und Datensätze effektiv bereinigen. Alle Transaktionsdaten und -protokolle müssen bereinigt werden. Die Bereinigungsaufgabe löscht nur die Standardtabellen „Tracking“ und „Umfassende Protokolle“. Bestimmte Tabellen müssen durch bestimmte Workflows bereinigt werden. Weitere Informationen finden Sie in [diesem Abschnitt](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

Achten Sie auf veraltete Transaktionsdaten, indem Sie das älteste Erstellungsdatum der Datensätze überprüfen.

---
solution: Campaign Classic
product: campaign
title: Best Practices für die Versandleistung
description: Erfahren Sie mehr über die Versandleistung und die entsprechenden Best Practices.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: 5b43412286762977c416665d296908a9bfc9b20a
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 100%

---


# Best Practices für die Versandleistung {#delivery-performances}

Wir empfehlen, die folgenden Richtlinien zu befolgen, um sicherzustellen, dass Ihre Sendungen gut funktionieren, sowie die angegebenen Prüfungen durchzuführen, wenn Sie auf Versandprobleme stoßen.

**Verwandte Themen:**

* [Versand-Dashboard](../../delivery/using/delivery-dashboard.md)
* [Fehlerbehebung beim Versand](../../delivery/using/delivery-troubleshooting.md)
* [Über die Zustellbarkeit](../../delivery/using/about-deliverability.md)

## Best Practices zur Leistungserhaltung {#best-practices-performance}

* Bewahren Sie auf der Instanz keine fehlgeschlagenen Sendungen auf, da dadurch temporäre Tabellen gespeichert werden, was wiederum die Leistung beeinträchtigt.

* Entfernen Sie nicht mehr benötigte Sendungen.

* Inaktive Empfänger in den letzten 12 Monaten werden aus der Datenbank entfernt, um die Adressenqualität zu erhalten.

* Planen Sie nicht die gleichzeitige Durchführung umfangreicher Sendungen. In einem Zeitraum von 5 bis 10 Minuten wird die Last gleichmäßig über das System verteilt. Koordinieren Sie die Planung von Sendungen mit anderen Team-Mitgliedern, um eine optimale Leistung zu gewährleisten. Wenn der Marketing-Server viele verschiedene Aufgaben gleichzeitig ausführt, kann die Leistung verlangsamt werden.

* Halten Sie die Größe Ihrer E-Mails so gering wie möglich. Die empfohlene maximale Größe einer E-Mail beträgt ca. 35 KB. Die Größe eines E-Mail-Versands generiert eine bestimmte Menge an Volumen auf den sendenden Servern.

* Große Sendungen wie Sendungen an über eine Million Empfänger benötigen Platz in den Versandwarteschlangen. Dies allein ist kein Problem für den Server, aber in Kombination mit Dutzenden von anderen großen Sendungen, die alle gleichzeitig ausgehen, kann es zu einer Versandverzögerung führen.

* Durch Personalisierung in E-Mails werden Daten für jeden Empfänger aus der Datenbank abgerufen. Bei vielen Personalisierungselementen erhöht sich dadurch die Datenmenge, die zur Vorbereitung des Versands benötigt wird.

* Indexieren von Adressen. Um die Performance der in der Anwendung verwendeten SQL-Abfragen zu optimieren, kann ein Index vom Hauptelement des Datenschemas deklariert werden.

>[!NOTE]
>
>ISPs würden Adressen nach einer Inaktivitätsphase deaktivieren. Bounce-Nachrichten werden an den Absender gesendet, um sie über diesen neuen Status zu informieren.

## Checkliste bei Versandproblemen {#performance-issues}

Bei mangelhafter Zustellbarkeit überprüfen Sie Folgendes:

* **Die Versandgröße**: Größere Sendungen benötigen zur Ausführung länger. MTA-Kindprozesse werden für Standard-Bündelgrößen konfiguriert. Diese sind für die meisten Instanzen ausreichend, müssen jedoch überprüft werden, wenn Sendungen immer zu langsam durchgeführt werden.
* **Die Zielgruppe des Versands**: Die Versandleistung kann durch Softbounce-Fehler beeinträchtigt werden, die entsprechend der Konfiguration der Neuversuche gehandhabt werden. Je größer die Anzahl der Fehler ist, desto mehr Neuversuche sind nötig.
* **Die Gesamtauslastung der Plattform**: Wenn mehrere große Sendungen durchgeführt werden, kann die gesamte Plattform davon beeinträchtigt sein. In diesem Zusammenhang sollten Sie auch die IP-Reputation und Probleme bei der Zustellbarkeit überprüfen. Weiterführende Informationen dazu finden Sie im Adobe Campaign-Handbuch zu [Best Practices für die Optimierung der Zustellbarkeit](../../delivery/using/deliverability-key-points.md) und auf [dieser Seite](../../delivery/using/about-deliverability.md).

Auch die Wartung der Plattform und der Datenbank kann die Leistung beim Versand beeinträchtigen. Weiterführende Informationen dazu finden Sie auf [dieser Seite](../../production/using/database-performances.md).

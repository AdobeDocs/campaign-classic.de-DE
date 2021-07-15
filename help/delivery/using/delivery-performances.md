---
product: campaign
title: Best Practices für die Versandleistung
description: Erfahren Sie mehr über die Versandleistung und die entsprechenden Best Practices.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: ht
source-wordcount: '458'
ht-degree: 100%

---

# Best Practices für die Versandleistung {#delivery-performances}

Wir empfehlen, die folgenden Richtlinien zu befolgen, um sicherzustellen, dass Ihre Sendungen gut funktionieren, sowie die angegebenen Prüfungen durchzuführen, wenn Sie auf Versandprobleme stoßen.

**Verwandte Themen:**

* [Versand-Dashboard](delivery-dashboard.md)
* [Fehlerbehebung beim Versand](delivery-troubleshooting.md)
* [Über die Zustellbarkeit](about-deliverability.md)

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

* **Die Versandgröße**: Größere Sendungen benötigen zur Ausführung länger. Untergeordnete MTA-Prozesse werden für Standard-Bündelgrößen konfiguriert. Diese sind für die meisten Instanzen ausreichend, müssen jedoch überprüft werden, wenn Sendungen immer zu langsam durchgeführt werden.
* **Die Zielgruppe des Versands**: Die Versandleistung kann durch Softbounce-Fehler beeinträchtigt werden, die entsprechend der Konfiguration der Neuversuche gehandhabt werden. Je größer die Anzahl der Fehler ist, desto mehr Neuversuche sind nötig.
* **Die Gesamtlast der Plattform**: Wenn mehrere große Sendungen ausgeführt werden, kann die gesamte Plattform beeinträchtigt sein. Sie können auch die IP-Reputation und Probleme mit der Zustellbarkeit überprüfen. Weitere Informationen finden Sie in [diesem Abschnitt](about-deliverability.md) und im [Adobe-Handbuch mit den Best Practices zur Zustellbarkeit](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=de).

Auch die Wartung der Plattform und der Datenbank kann die Leistung beim Versand beeinträchtigen. Weiterführende Informationen dazu finden Sie auf [dieser Seite](../../production/using/database-performances.md).

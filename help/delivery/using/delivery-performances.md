---
product: campaign
title: Best Practices für die Versand-Performance
description: Erfahren Sie mehr über die Versand-Performance und die entsprechenden Best Practices
badge-v7: label="v7" type="Informative" tooltip="Gilt für Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Deliverability
role: User, Data Engineer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 97%

---

# Best Practices für die Versand-Performance {#delivery-performances}

Wir empfehlen, die folgenden Richtlinien zu befolgen, um sicherzustellen, dass Ihre Sendungen gut funktionieren, sowie die angegebenen Prüfungen durchzuführen, wenn Sie auf Versandprobleme stoßen.

**Verwandte Themen:**

* [Versand-Dashboard](delivery-dashboard.md)
* [Fehlerbehebung beim Versand](delivery-troubleshooting.md)
* [Über die Zustellbarkeit](about-deliverability.md)

## Best Practices zur Performance-Erhaltung {#best-practices-performance}

* Bewahren Sie auf der Instanz keine fehlgeschlagenen Sendungen auf, da dadurch temporäre Tabellen gespeichert werden, was wiederum die Performance beeinträchtigt.

* Entfernen Sie nicht mehr benötigte Sendungen.

* Inaktive Empfänger in den letzten 12 Monaten werden aus der Datenbank entfernt, um die Adressenqualität zu erhalten.

* Planen Sie nicht die gleichzeitige Durchführung umfangreicher Sendungen. In einem Zeitraum von 5 bis 10 Minuten wird die Last gleichmäßig über das System verteilt. Koordinieren Sie die Planung von Sendungen mit anderen Team-Mitgliedern, um eine optimale Performance zu gewährleisten. Wenn der Marketing-Server viele verschiedene Aufgaben gleichzeitig ausführt, kann die Performance verlangsamt werden.

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
* **Die Zielgruppe des Versands**: Die Versand-Performance kann durch Softbounce-Fehler beeinträchtigt werden, die entsprechend der Konfiguration der Neuversuche gehandhabt werden. Je größer die Anzahl der Fehler ist, desto mehr Neuversuche sind nötig.
* **Die Gesamtlast der Plattform**: Wenn mehrere große Sendungen ausgeführt werden, kann die gesamte Plattform beeinträchtigt sein. Sie können auch die IP-Reputation und Probleme mit der Zustellbarkeit überprüfen. Weitere Informationen finden Sie in [diesem Abschnitt](about-deliverability.md) und im [Adobe-Handbuch mit den Best Practices zur Zustellbarkeit](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=de).

Die Wartung der Plattform und der Datenbank kann sich auch auf die Leistung beim Versand auswirken. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../production/using/database-performances.md).

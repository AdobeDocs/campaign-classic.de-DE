---
product: campaign
title: Best Practices für die Versand-Performance
description: Erfahren Sie mehr über die Versand-Performance und die entsprechenden Best Practices
feature: Deliverability
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 6%

---

# Best Practices für die Versand-Performance {#delivery-performances}

>[!NOTE]
>
>Eine umfassende Anleitung zur Versandleistung und zu Best Practices finden Sie auf der Seite [Best Practices für den Versand in Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices) . Diese Inhalte gelten für Benutzende von Campaign Classic v7 und Campaign v8.
>
>Auf dieser Seite werden **Campaign Classic v7-spezifische Leistungskonfigurationen** Hybrid- und On-Premise-Bereitstellungen dokumentiert.

Umfassende Best Practices zur Versandleistung, Plattformoptimierung, Quarantäneverwaltung, Datenbankwartung und Planungsempfehlungen finden Sie in der [ zu Best Practices für den Versand in Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}.

## Leistungsoptimierung {#best-practices-performance}

Bei Hybrid-/On-Premise-Bereitstellungen von **Campaign Classic v7** die folgenden Datenbank- und Infrastrukturoptimierungen die Versandleistung verbessern:

### Datenbankoptimierung

**Indexadressen**, um die Leistung der in der Anwendung verwendeten SQL-Abfragen zu optimieren. Ein Index kann über das Hauptelement des Datenschemas deklariert werden. Diese Optimierung erfordert den direkten Datenbankzugriff und die Schemaanpassung, die in On-Premise-Bereitstellungen verfügbar sind.

### Infrastrukturoptimierung

**Konfiguration großer Sendungen**: Sendungen an mehr als eine Million Empfänger benötigen Speicherplatz in den Versandwarteschlangen. Bei On-Premise-Installationen können die untergeordneten MTA-Elemente so konfiguriert werden, dass benutzerdefinierte Batch-Größen verarbeitet werden. Wenden Sie sich an Ihren Systemadministrator, um diese Einstellungen auf der Grundlage Ihrer Infrastrukturkapazität anzupassen.

>[!NOTE]
>
>Für Benutzende von Campaign v8 Managed Cloud Services werden die Infrastrukturoptimierung und die MTA-Konfiguration von Adobe verwaltet. Siehe Best Practices beim Versand [ Campaign v8 ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} Leistungsempfehlungen für Ihre -Bereitstellung.

## Wartung der Datenbank {#performance-issues}

Bei **Hybrid-/On-Premise-Bereitstellungen von Campaign Classic v7** sich die Plattform- und Datenbankwartung direkt auf die Versandleistung aus.

Zu den regelmäßigen Wartungsaufgaben gehören:

**Datenbankbereinigung**: Verwenden Sie den Datenbankbereinigungs-Workflow, um alte Versandlogs, Tracking-Daten und temporäre Tabellen zu entfernen. Schlechte Datenbankwartung kann die Versandvorbereitung und den Versand verlangsamen.

**Überwachung der Datenbankleistung** Überwachen der Abfrageleistung, der Indexfragmentierung und der Tabellenstatistiken. Ausführliche Anleitungen finden Sie auf [dieser Seite](../../production/using/database-performances.md).

**Technisches Workflow-Monitoring**: Stellen Sie sicher, dass alle technischen Workflows (insbesondere Bereinigungs-, Tracking- und Zustellbarkeits-Update-Workflows) fehlerfrei ordnungsgemäß ausgeführt werden.

>[!NOTE]
>
>Benutzende von Campaign v8 Managed Cloud Services überwachen und verwalten die Datenbankwartung und die technischen Workflows von Adobe. Konzentrieren Sie sich auf die versandspezifische Überwachung, wie in der Dokumentation [Überwachen von Sendungen in Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"} beschrieben.

## Verwandte Themen

* [Best Practices für den Versand](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (Dokumentation zu Campaign v8)
* [Zustellbarkeit überwachen](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"} (Dokumentation zu Campaign v8)
* [Fehlerbehebung beim Versand](delivery-troubleshooting.md)
* [Datenbankleistung](../../production/using/database-performances.md) (v7 Hybrid/On-Premise)

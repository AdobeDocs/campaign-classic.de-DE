---
product: campaign
title: Versandleistung und Fehlerbehebung
description: Erfahren Sie, wie Sie die Versandleistung optimieren und Probleme in Campaign Classic v7 beheben können.
feature: Monitoring, Deliverability, Troubleshooting
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: 2ebae2b84741bf26dd44c872702dbf3b0ebfc453
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 5%

---

# Versandleistung und Fehlerbehebung {#delivery-performance-troubleshooting}

>[!NOTE]
>
>Eine umfassende Anleitung zur Versandleistung und zu Best Practices finden Sie auf der Seite [Best Practices für den Versand in Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices) . Diese Inhalte gelten für Benutzende von Campaign Classic v7 und Campaign v8.
>
>Auf dieser Seite werden **Campaign Classic v7-spezifische Konfigurationen** Leistungsoptimierung und Fehlerbehebung in Hybrid- und On-Premise-Bereitstellungen dokumentiert.

Umfassende Best Practices zur Versandleistung, Plattformoptimierung, Quarantäneverwaltung, Datenbankwartung und Planungsempfehlungen finden Sie in der [&#x200B; zu Best Practices für den Versand in Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}.

## Leistungsoptimierung {#performance-optimization}

Bei Hybrid-/On-Premise-Bereitstellungen von **Campaign Classic v7** die folgenden Datenbank- und Infrastrukturoptimierungen die Versandleistung verbessern.

### Datenbankoptimierung

**Indexadressen**, um die Leistung der in der Anwendung verwendeten SQL-Abfragen zu optimieren. Ein Index kann über das Hauptelement des Datenschemas deklariert werden. Diese Optimierung erfordert den direkten Datenbankzugriff und die Schemaanpassung, die in On-Premise-Bereitstellungen verfügbar sind.

### Infrastrukturoptimierung

**Konfiguration großer Sendungen**: Sendungen an mehr als eine Million Empfänger benötigen Speicherplatz in den Versandwarteschlangen. Bei On-Premise-Installationen können die untergeordneten MTA-Elemente so konfiguriert werden, dass benutzerdefinierte Batch-Größen verarbeitet werden. Wenden Sie sich an Ihren Systemadministrator, um diese Einstellungen auf der Grundlage Ihrer Infrastrukturkapazität anzupassen.

>[!NOTE]
>
>Für Benutzende von Campaign v8 Managed Cloud Services werden die Infrastrukturoptimierung und die MTA-Konfiguration von Adobe verwaltet. Siehe Best Practices beim Versand [&#x200B; Campaign v8 &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} Leistungsempfehlungen für Ihre -Bereitstellung.

### Wartung der Datenbank {#database-maintenance}

Bei **Hybrid-/On-Premise-Bereitstellungen von Campaign Classic v7** sich die Plattform- und Datenbankwartung direkt auf die Versandleistung aus.

Zu den regelmäßigen Wartungsaufgaben gehören:

**Datenbankbereinigung**: Verwenden Sie den Datenbankbereinigungs-Workflow, um alte Versandlogs, Tracking-Daten und temporäre Tabellen zu entfernen. Schlechte Datenbankwartung kann die Versandvorbereitung und den Versand verlangsamen.

**Überwachung der Datenbankleistung** Überwachen der Abfrageleistung, der Indexfragmentierung und der Tabellenstatistiken. Ausführliche Anleitungen finden Sie auf [dieser Seite](../../production/using/database-performances.md).

**Technisches Workflow-Monitoring**: Stellen Sie sicher, dass alle technischen Workflows (insbesondere Bereinigungs-, Tracking- und Zustellbarkeits-Update-Workflows) fehlerfrei ordnungsgemäß ausgeführt werden.

>[!NOTE]
>
>Benutzende von Campaign v8 Managed Cloud Services überwachen und verwalten die Datenbankwartung und die technischen Workflows von Adobe. Konzentrieren Sie sich auf die versandspezifische Überwachung, wie in der Dokumentation [Überwachen von Sendungen in Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"} beschrieben.

## Fehlerbehebung bei Versandproblemen {#troubleshooting}

>[!NOTE]
>
>Eine umfassende Anleitung zur Fehlerbehebung beim Versand finden Sie in der Dokumentation zu Campaign v8 , die sowohl für Benutzende von Campaign Classic v7 als auch Campaign v8 gilt:
>
>* Häufige Versandfehler und -lösungen: [Fehlgeschlagene Sendungen verstehen](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}
>* Diagnose langsamer Sendungen: [Überwachen von Sendungen in der Campaign-Benutzeroberfläche](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}
>* Best Practices für den Versand: [Best Practices für den Versand](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}
>
>In diesem Abschnitt wird die **Campaign Classic v7-spezifische Fehlerbehebung** Hybrid- und On-Premise-Bereitstellungen beschrieben.

Bei Hybrid-/On-Premise-Bereitstellungen von **Campaign Classic v7** die folgenden Schritte zur Fehlerbehebung spezifisch für die von Ihnen verwaltete Infrastruktur.

### MX-Regelkonfiguration

Wenn bei bestimmten ISPs Einschränkungsprobleme auftreten, müssen Sie möglicherweise Ihre MX-Regelkonfiguration überprüfen und anpassen. Weitere Informationen zu MX-Regeln und -Kontingenten finden Sie [diesem Abschnitt](../../installation/using/email-deliverability.md#about-mx-rules).

### Datenbankwartung für die Versandleistung

Wenn der folgende Fehler in Mid-Sourcing-Bereitstellungen auftritt:

```
Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
```

Die Ursache hängt mit Leistungsproblemen zusammen, bei denen die Marketing-Instanz zu viel Zeit mit dem Erstellen von Daten verbringt, bevor sie diese an den Mid-Sourcing-Server sendet.

**Bei On-Premise** Installationen führen Sie einen Leerlauf durch und indizieren Sie die Datenbank neu. Weiterführende Informationen zur Wartung der Datenbank finden Sie in [diesem Abschnitt](../../production/using/recommendations.md).

Zusätzlich sollten Sie alle Workflows mit einer terminierten Aktivität und alle Workflows mit fehlgeschlagenem Status neu starten. Weitere Informationen finden Sie in [diesem Abschnitt](../../workflow/using/scheduler.md).

### Überwachen technischer Workflows

Stellen Sie bei On-Premise-Installationen sicher, dass alle technischen Workflows im Zusammenhang mit der Zustellbarkeit fehlerfrei ausgeführt werden:

**Workflow zur Aktualisierung der Zustellbarkeit**: Aktualisiert die Regeln für die Bounce-Message-Qualifizierung und die Zustellbarkeitsindikatoren.

**Tracking-Workflow**: Verarbeitet Tracking-Daten für gesendete Sendungen.

**Datenbankbereinigungs-Workflow**: Bereinigt regelmäßig alte Versandlogs und temporäre Tabellen, um die Leistung aufrechtzuerhalten.

Überprüfen Sie den Workflow-Status **[!UICONTROL Administration]** > **&#x200B;**&#x200B;> **[!UICONTROL Technische Workflows]**.

>[!NOTE]
>
>Für Benutzende von Campaign v8 Managed Cloud Services werden technische Workflows und die Infrastrukturüberwachung von Adobe verwaltet. Konzentrieren Sie sich auf den Versandinhalt und die Zielgruppenbestimmung, wie in der Dokumentation zu [&#x200B; v8 &#x200B;](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}.

## Verwandte Themen

* [Fehlgeschlagene Sendungen analysieren](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (Dokumentation zu Campaign v8)
* [Best Practices für den Versand](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (Dokumentation zu Campaign v8)
* [Überwachen von Sendungen in der Campaign-Benutzeroberfläche](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (Dokumentation zu Campaign v8)
* [Datenbankwartung](../../production/using/recommendations.md) (v7 Hybrid/On-Premise)
* [E-Mail-Zustellbarkeit](../../installation/using/email-deliverability.md) (Hybrid/On-Premise von v7)
* [Datenbankleistung](../../production/using/database-performances.md) (v7 Hybrid/On-Premise)


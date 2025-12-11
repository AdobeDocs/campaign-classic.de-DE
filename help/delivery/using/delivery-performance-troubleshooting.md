---
product: campaign
title: Versandleistung und Fehlerbehebung
description: Erfahren Sie, wie Sie in Campaign Classic v7 die Versandleistung optimieren und Probleme beheben
feature: Monitoring, Deliverability, Troubleshooting
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: 2ebae2b84741bf26dd44c872702dbf3b0ebfc453
workflow-type: ht
source-wordcount: '669'
ht-degree: 100%

---

# Versandleistung und Fehlerbehebung {#delivery-performance-troubleshooting}

>[!NOTE]
>
>Eine umfassende Anleitung zur Versandleistung und zu Best Practices finden Sie auf der Seite [Best Practices für den Versand in Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/start/delivery-best-practices). Diese Inhalte gelten für Benutzende von Campaign Classic v7 und Campaign v8.
>
>Auf dieser Seite werden **Campaign Classic v7-spezifische Konfigurationen** zur Leistungsoptimierung und Fehlerbehebung bei Hybrid- und On-Premise-Bereitstellungen dokumentiert.

Umfassende Best Practices zur Versandleistung, Plattformoptimierung, Quarantäneverwaltung, Datenbankwartung und Planungsempfehlungen finden Sie in der [Dokumentation zu Best Practices für den Versand in Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}.

## Leistungsoptimierung {#performance-optimization}

Bei **Hybrid-/On-Premise-Bereitstellungen von Campaign Classic v7** können die folgenden Datenbank- und Infrastrukturoptimierungen die Versandleistung verbessern.

### Datenbankoptimierung

**Indizieren der Adressen**, um die Leistung der in der Anwendung verwendeten SQL-Abfragen zu optimieren. Ein Index wird über das Hauptelement des Datenschemas deklariert. Diese Optimierung erfordert den direkten Datenbankzugriff und die Schemaanpassung, die in On-Premise-Bereitstellungen verfügbar sind.

### Infrastrukturoptimierung

**Konfiguration großer Sendungen**: Sendungen an über eine Million Empfängerinnen und Empfänger benötigen Platz in den Versandwarteschlangen. Bei On-Premise-Installationen können die untergeordneten MTA-Elemente so konfiguriert werden, dass benutzerdefinierte Batch-Größen verarbeitet werden. Wenden Sie sich an Ihre bzw. Ihren Systemadmin, um diese Einstellungen auf der Grundlage Ihrer Infrastrukturkapazität anzupassen.

>[!NOTE]
>
>Für Benutzende von Campaign v8 Managed Cloud Services werden die Infrastrukturoptimierung und die MTA-Konfiguration von Adobe verwaltet. Unter [Best Practices beim Versand in Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} finden Sie Leistungsempfehlungen für Ihre Bereitstellung.

### Wartung der Datenbank {#database-maintenance}

Bei **Hybrid-/On-Premise-Bereitstellungen von Campaign Classic v7** wirken sich Plattform- und Datenbankwartung direkt auf die Versandleistung aus.

Zu den regelmäßigen Wartungsaufgaben gehören:

**Datenbankbereinigung**: Verwenden Sie den Datenbankbereinigungs-Workflow, um alte Versandlogs, Tracking-Daten und temporäre Tabellen zu entfernen. Schlechte Datenbankwartung kann die Versandvorbereitung und den Versand verlangsamen.

**Monitoring der Datenbankleistung**: Überwachen Sie Abfrageleistung, Indexfragmentierung und Tabellenstatistiken. Detaillierte Anleitungen finden Sie [auf dieser Seite](../../production/using/database-performances.md).

**Monitoring technischer Workflows**: Stellen Sie sicher, dass alle technischen Workflows (insbesondere Bereinigungs-, Tracking- und Zustellbarkeits-Update-Workflows) ordnungsgemäß und fehlerfrei ausgeführt werden.

>[!NOTE]
>
>Bei Benutzenden von Campaign v8 Managed Cloud Services werden die Datenbankwartung und die technischen Workflows von Adobe überwacht und verwaltet. Konzentrieren Sie sich auf das versandspezifische Monitoring, wie in der Dokumentation [Monitoring von Sendungen in Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"} beschrieben.

## Fehlerbehebung beim Versand {#troubleshooting}

>[!NOTE]
>
>Eine umfassende Anleitung zur Fehlerbehebung beim Versand finden Sie in der Dokumentation zu Campaign v8, die sowohl für Benutzende von Campaign Classic v7 als auch Campaign v8 gilt:
>
>* Häufige Versandfehler und -lösungen: [Informationen zu Versandfehlern](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}
>* Diagnose langsamer Sendungen: [Monitoring von Sendungen in der Campaign-Benutzeroberfläche](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}
>* Best Practices für den Versand: [Best Practices für den Versand](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}
>
>In diesem Abschnitt wird die **Campaign Classic v7-spezifische Fehlerbehebung** bei Hybrid- und On-Premise-Bereitstellungen beschrieben.

Bei **Hybrid-/On-Premise-Bereitstellungen von Campaign Classic v7** gelten die folgenden Schritte zur Fehlerbehebung spezifisch für die von Ihnen verwaltete Infrastruktur.

### MX-Regelkonfiguration

Wenn bei bestimmten ISPs Einschränkungsprobleme auftreten, müssen Sie möglicherweise Ihre MX-Regelkonfiguration überprüfen und anpassen. Weitere Informationen zu MX-Regeln und Kontingenten finden Sie [in diesem Abschnitt](../../installation/using/email-deliverability.md#about-mx-rules).

### Datenbankwartung für die Versandleistung

Wenn der folgende Fehler in Mid-Sourcing-Bereitstellungen auftritt:

```
Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
```

Die Ursache hierfür sind Performance-Probleme, wenn die Marketing-Instanz zu lange für die Generierung von Daten benötigt, bevor diese an den Mid-Sourcing-Server gesendet werden.

**Bei On-Premise-Installationen** führen Sie ein Vacuum durch und indizieren Sie die Datenbank neu. Weiterführende Informationen zur Wartung der Datenbank finden Sie in [diesem Abschnitt](../../production/using/recommendations.md).

Zusätzlich sollten Sie alle Workflows mit einer terminierten Aktivität und alle Workflows mit fehlgeschlagenem Status neu starten. Weitere Informationen finden Sie in [diesem Abschnitt](../../workflow/using/scheduler.md).

### Monitoring technischer Workflows

Stellen Sie bei On-Premise-Installationen sicher, dass alle technischen Workflows im Zusammenhang mit der Zustellbarkeit fehlerfrei ausgeführt werden:

**Zustellbarkeits-Update-Workflow**: Aktualisiert die Regeln für die Bounce-E-Mail-Qualifizierung und die Zustellbarkeitsindikatoren.

**Tracking-Workflow**: Verarbeitet Tracking-Daten für gesendete Sendungen.

**Datenbankbereinigungs-Workflow**: Bereinigt regelmäßig alte Versandlogs und temporäre Tabellen, um die Leistung aufrechtzuerhalten.

Überprüfen Sie den Workflow-Status unter **[!UICONTROL Administration]** > **[!UICONTROL Produktion]** > **[!UICONTROL Technische Workflows]**.

>[!NOTE]
>
>Für Benutzende von Campaign v8 Managed Cloud Services wird das Monitoring der technischen Workflows und der Infrastruktur von Adobe verwaltet. Konzentrieren Sie sich auf den Versandinhalt und die Zielgruppenbestimmung, wie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} beschrieben.

## Verwandte Themen

* [Informationen zu Versandfehlern](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (Dokumentation zu Campaign v8)
* [Best Practices für den Versand](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (Dokumentation zu Campaign v8)
* [Monitoring von Sendungen in der Campaign-Benutzeroberfläche](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (Dokumentation zu Campaign v8)
* [Datenbankwartung](../../production/using/recommendations.md) (v7 Hybrid/On-Premise)
* [E-Mail-Zustellbarkeit](../../installation/using/email-deliverability.md) (v7 Hybrid/On-Premise)
* [Datenbankleistung](../../production/using/database-performances.md) (v7 Hybrid/On-Premise)


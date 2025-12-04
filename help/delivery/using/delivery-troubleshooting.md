---
product: campaign
title: Fehlerbehebung beim Versand
description: Erfahren Sie mehr über die Versand-Performance und wie Sie Probleme beim Versand-Monitoring beheben können
feature: Monitoring, Deliverability, Troubleshooting
role: User
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 16%

---

# Fehlerbehebung beim Versand {#delivery-troubleshooting}

>[!NOTE]
>
>Eine umfassende Anleitung zur Fehlerbehebung beim Versand finden Sie in der Dokumentation zu Campaign v8 , die sowohl für Benutzende von Campaign Classic v7 als auch Campaign v8 gilt:
>
>* Häufige Versandfehler und -lösungen: [Fehlgeschlagene Sendungen verstehen](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}
>* Diagnose langsamer Sendungen: [Überwachen von Sendungen in der Campaign-Benutzeroberfläche](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}
>* Best Practices für den Versand: [Best Practices für den Versand](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}
>
>Auf dieser Seite wird die **Campaign Classic v7-spezifische Fehlerbehebung** Hybrid- und On-Premise-Bereitstellungen beschrieben.

## Fehlerbehebung {#v7-specific}

Bei Hybrid-/On-Premise-Bereitstellungen von **Campaign Classic v7** die folgenden Schritte zur Fehlerbehebung spezifisch für die von Ihnen verwaltete Infrastruktur:

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

Überprüfen Sie den Workflow-Status **[!UICONTROL Administration]** > **** > **[!UICONTROL Technische Workflows]**.

>[!NOTE]
>
>Für Benutzende von Campaign v8 Managed Cloud Services werden technische Workflows und die Infrastrukturüberwachung von Adobe verwaltet. Konzentrieren Sie sich auf den Versandinhalt und die Zielgruppenbestimmung, wie in der Dokumentation zu [ v8 ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}.

## Verwandte Themen

* [Fehlgeschlagene Sendungen analysieren](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (Dokumentation zu Campaign v8)
* [Best Practices für den Versand](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (Dokumentation zu Campaign v8)
* [Überwachen von Sendungen in der Campaign-Benutzeroberfläche](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (Dokumentation zu Campaign v8)
* [Datenbankwartung](../../production/using/recommendations.md) (v7 Hybrid/On-Premise)
* [E-Mail-Zustellbarkeit](../../installation/using/email-deliverability.md) (Hybrid/On-Premise von v7)

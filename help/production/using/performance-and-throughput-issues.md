---
title: Leistungs- und Durchsatzprobleme
seo-title: Leistungs- und Durchsatzprobleme
description: Leistungs- und Durchsatzprobleme
seo-description: null
page-status-flag: never-activated
uuid: 28c35453-9a15-44a3-9961-f4c604c209c2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: ec66e3e3-b09a-44a4-914d-e3b38c7643f8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: bc54cef4c44be4c694e062f56685dbb09d2fcf8e
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 7%

---


# Leistungs- und Durchsatzprobleme{#performance-and-throughput-issues}

>[!NOTE]
>
>Zunächst sollten Sie überprüfen, ob der neueste Build installiert ist. Dadurch wird sichergestellt, dass Sie über die neuesten Funktionen und Fehlerbehebungen verfügen. Weitere Informationen zum Inhalt der einzelnen Versionen finden Sie in den [Versionshinweisen](../../rn/using/latest-release.md) .

## Hardware und Infrastruktur {#hardware-and-infrastructure}

Die allgemeinen Richtlinien für die Hardwareanforderungen für das lokale Campaign Classic sind in diesem [Artikel](https://helpx.adobe.com/de/campaign/kb/hardware-sizing-guide.html)beschrieben.

Das Beratungsteam kann gehosteten Kunden ein Tool zur Verfügung stellen, mit dem Sie ganz einfach Ansichten darüber vornehmen können, wie viel Platz die verschiedenen Datenbanktypen und der auf der SFTP-Site genutzte Platz einnehmen. Darüber hinaus bietet es Tools, mit denen Sie unnötige Daten bereinigen können. Wenden Sie sich an das Beratungs- oder Supportteam, wenn dieses Tool implementiert werden muss. Hier einige wichtige Punkte, die Sie mit diesem Tool überprüfen müssen:

* Wenn die Indexgröße größer als die Tabellengröße ist, ist ein Vakuum erforderlich.
* Überprüfen Sie die Tabellen mit der maximalen Aufblähung. If these tables are frequently used, they need to be vacuumed.
* Datenbankblockierung kann dazu führen, dass E-Mails nicht mehr gesendet werden.

Adobe Campaign also provides a [tool](../../production/using/monitoring-processes.md#manual-monitoring) to check CPU and RAM usage. Verwenden Sie dieses Tool und prüfen Sie spezifische Indikatoren wie: **Arbeitsspeicher**, **Arbeitsspeicher**, **Datenträger**, **aktive Prozesse**. Wenn die Werte zu hoch sind, können Sie versuchen, die Anzahl der Workflows zu reduzieren oder die Workflows zu verschiedenen Zeitpunkten auf den Beginn zu planen.

## Datenbankleistung {#database-performances}

In den meisten Fällen sind Leistungsprobleme mit der Datenbankwartung verbunden. Im Folgenden werden die wichtigsten Elemente aufgeführt:

* Konfiguration: Wir empfehlen, die anfängliche Plattformkonfiguration des Adobe Campaigns zu überprüfen und eine vollständige Hardwareprüfung durchzuführen.
* Installation and configuration of the Adobe Campaign platform: check network configuration and platform deliverability options.
* Datenbankwartung: Vergewissern Sie sich, dass die Aufgabe zur Datenbankbereinigung betriebsbereit ist und dass die Datenbankwartung ordnungsgemäß geplant und ausgeführt wurde. Überprüfen Sie die Anzahl und Größe der Arbeitstabellen.
* Echtzeitdiagnose: Überprüfen Sie die Prozess- und Plattformprotokolldateien und überwachen Sie dann die Aktivität der Datenbank, während Sie die Ausgabe erneut erstellen.

>[!NOTE]
>
>For more information, refer to this section: [Database performances](../../production/using/database-performances.md).

## Application Configuration {#application-configuration}

Here are is a list of articles related to application configuration best practices:

* MTA- und MTAChild-Prozesse und -Speicher: das **Modul mta** verteilt Nachrichten an seine untergeordneten **mtachild** -Module. Each **mtachild** prepares messages before requesting an authorization from the statistics server, and sending them. Refer to this [page](../../installation/using/email-deliverability.md) for more information.
* TLS configuration: enabling TLS globally is not recommended because it can reduce throughput. Stattdessen sollten die vom Bereitstellungsteam verwalteten TLS-Einstellungen pro Domäne je nach Bedarf angepasst werden. Weitere Informationen finden Sie auf dieser [Seite](../../installation/using/email-deliverability.md#mx-configuration) .
* DKIM: to insure the security level of the DKIM, 1024b is the Best Practices recommended encryption size. Niedrigere DKIM-Schlüssel werden von den meisten Zugangsanbietern nicht als gültig angesehen. Lesen Sie diese [Seite](../../delivery/using/technical-recommendations.md#dkim) und diese [Technote](https://helpx.adobe.com/de/campaign/kb/domain-name-delegation.html).

## Probleme mit der Lieferbarkeit {#deliverability-issues}

Im Folgenden finden Sie eine Liste bewährter Verfahren und Artikel zur Lieferbarkeit:

* IP reputation: if the IP reputation is not good enough, there will be an impact on performance. Das **Lieferbarkeitsüberwachungsmodul** Angebot verschiedene Tools zur Verfolgung der Leistung Ihrer Plattform. Mehr dazu erfahren Sie auf [dieser Seite](../../delivery/using/monitoring-deliverability.md).
* IP warm-up: the IP warm-up is performed by the deliverability team. This involves gradually increasing the number of emails through new IPs over a period of a few weeks.
* IP affinity setup: an incorrect IP affinity setup can stop the emails altogether (incorrect operator/affinity name in configuration) or reduce the throughput (small number of IPs in the affinity). Mehr dazu erfahren Sie auf [dieser Seite](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* E-Mail-Größe: Die E-Mail-Größe spielt eine wichtige Rolle beim Durchsatz. Die empfohlene maximale E-Mail-Größe beträgt 60 KB. Mehr dazu erfahren Sie auf [dieser Seite](https://helpx.adobe.com/legal/product-descriptions/campaign.html). In the [Delivery throughput](../../reporting/using/global-reports.md#delivery-throughput) report, check the number of bytes transferred by hour.
* Große Anzahl ungültiger Empfänger: Wenn eine große Anzahl ungültiger Empfänger vorhanden ist, kann dies den Durchsatz beeinflussen. Die MTA versucht weiterhin, E-Mails an ungültige Empfänger zu senden. Stellen Sie sicher, dass Ihre Datenbank gut gepflegt ist.
* Umfang der Personalisierung: Wenn ein Versand in &quot;Personalisierung in Bearbeitung&quot;bleibt, überprüfen Sie das in Gestaltungsbausteinen verwendete JavaScript.

>[!NOTE]
>
>Siehe auch Abschnitt [Wichtigste](../../delivery/using/deliverability-key-points.md) Bereitstellungspunkte.


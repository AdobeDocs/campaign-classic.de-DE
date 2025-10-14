---
product: campaign
title: Performance- und Durchsatzprobleme
description: Performance- und Durchsatzprobleme
feature: Monitoring
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: fe69efda-a052-4f67-9c13-665f011d0a2b
source-git-commit: 6803b6628313db9108a191fd143dac68ee799149
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 15%

---

# Performance- und Durchsatzprobleme{#performance-and-throughput-issues}

Zunächst sollten Sie überprüfen, ob der neueste Build installiert ist. Dadurch wird sichergestellt, dass Sie über die neuesten Funktionen und Fehlerbehebungen verfügen.

Weitere Informationen zum Inhalt [&#x200B; einzelnen Versionen finden &#x200B;](../../rn/using/latest-release.md) in den Versionshinweisen .

## Hardware und Infrastruktur {#hardware-and-infrastructure}

Allgemeine Richtlinien zu den Hardwareanforderungen für On-Premise-Campaign Classic finden Sie auf dieser [Seite](https://helpx.adobe.com/de/campaign/kb/hardware-sizing-guide.html).

Das Beratungs-Team kann gehosteten Kunden ein Tool zur Verfügung stellen, mit dem Sie leicht feststellen können, wie viel Speicherplatz von verschiedenen Tabellentypen in der Datenbank sowie von der SFTP-Site belegt wird. Darüber hinaus stehen Tools zur Verfügung, mit denen Sie unnötige Daten bereinigen können. Wenden Sie sich an die [Adobe](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)Kundenunterstützung, wenn Sie dieses Tool implementieren müssen. Im Folgenden finden Sie einige wichtige Dinge, die Sie mit diesem Tool überprüfen sollten:

* Wenn die Indexgröße größer als die Tabellengröße ist, ist ein Vakuum erforderlich.
* Überprüfen Sie die Tabellen, die die maximale Aufblähung aufweisen. Wenn diese Tabellen häufig verwendet werden, müssen sie abgesaugt werden.
* Durch die Blockierung von Datenbanken können E-Mails nicht mehr gesendet werden.

Adobe Campaign bietet außerdem ein [Tool](../../production/using/monitoring-processes.md#manual-monitoring) um die CPU- und RAM-Nutzung zu überprüfen. Verwenden Sie dieses Tool und betrachten Sie bestimmte Indikatoren wie: **Speicher**, **Arbeitsspeicher wechseln**, **Festplatte**, **Aktive Prozesse**. Wenn die Werte zu hoch sind, können Sie versuchen, die Anzahl der Workflows zu reduzieren, oder den Start von Workflows zu unterschiedlichen Zeiten planen.

## Prüfung der Datenbank {#database-performances}

In den meisten Fällen sind Leistungsprobleme mit der Datenbankwartung verbunden. Im Folgenden sind die wichtigsten Punkte aufgeführt, die überprüft werden müssen:

* Konfiguration: Es wird empfohlen, die anfängliche Adobe Campaign-Plattformkonfiguration zu überprüfen und eine vollständige Hardwareprüfung durchzuführen.
* Installation und Konfiguration der Adobe Campaign-Plattform: Überprüfen Sie die Optionen für die Netzwerkkonfiguration und Plattformzustellbarkeit.
* Datenbankwartung: Stellen Sie sicher, dass die Datenbankbereinigung betriebsbereit ist und die Datenbankwartung korrekt geplant und ausgeführt wird. Überprüfen Sie die Anzahl und Größe der Arbeitstabellen.
* Echtzeitdiagnose: Überprüfen Sie die Prozess- und Platform-Protokolldateien und überwachen Sie dann die Datenbankaktivität, während Sie das Problem neu erstellen.

>[!NOTE]
>
>Weiterführende Informationen finden Sie in diesem Abschnitt: [Datenbankleistung](../../production/using/database-performances.md).

## Anwendungskonfiguration {#application-configuration}

Im Folgenden finden Sie eine Liste von Artikeln zu Best Practices für die Anwendungskonfiguration:

* MTA- und MTAChild-Prozesse und -Speicher: Das **mta**-Modul verteilt Nachrichten an seine untergeordneten **mtachild**-Module. Jedes **mtachild** bereitet Nachrichten vor, bevor es eine Autorisierung vom Statistikserver anfordert und sendet. Weitere Informationen finden Sie auf dieser [Seite.](../../installation/using/email-deliverability.md)
* TLS-Konfiguration: Die globale Aktivierung von TLS wird nicht empfohlen, da dadurch der Durchsatz reduziert werden kann. Stattdessen sollten TLS-Einstellungen pro Domain, die vom Zustellbarkeits-Team verwaltet werden, je nach Bedarf angepasst werden. Weitere Informationen finden Sie auf dieser [Seite.](../../installation/using/email-deliverability.md#mx-configuration)

  >[!NOTE]
  >
  >Die Beauftragung des Zustellbarkeits-Teams ist vertraglich geregelt. Kundinnen und Kunden sollten sich an den Adobe-Support wenden, um diesbezügliche Informationen zu erhalten.

* DKIM: Um die Sicherheitsstufe von DKIM zu gewährleisten, ist 1024b die empfohlene Verschlüsselungsgröße. Niedrigere DKIM-Schlüssel werden von den meisten Zugriffsanbietern nicht als gültig erachtet. Mehr dazu erfahren Sie auf [dieser Seite](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=de#authentication).

## Probleme mit der Zustellbarkeit {#deliverability-issues}

Im Folgenden finden Sie eine Liste von Best Practices und Artikeln zur Zustellbarkeit:

* IP-Reputation: Wenn die IP-Reputation nicht gut genug ist, wirkt sich dies auf die Leistung aus. Das **Zustellbarkeits-Monitoring** bietet verschiedene Tools, um die Zustellbarkeitsleistung Ihrer Plattform zu verfolgen. Mehr dazu erfahren Sie auf [dieser Seite](../../delivery/using/monitoring-deliverability.md).
* IP-Warm-up: Das IP-Warm-up wird vom Zustellbarkeits-Team durchgeführt. Dazu gehört, die Anzahl der E-Mails über neue IPs über einen Zeitraum von einigen Wochen schrittweise zu erhöhen.

  >[!NOTE]
  >
  >Die Beauftragung des Zustellbarkeits-Teams ist vertraglich geregelt. Kundinnen und Kunden sollten sich an den Adobe-Support wenden, um diesbezügliche Informationen zu erhalten.

* Einrichtung der IP-Affinität: Eine falsche Einrichtung der IP-Affinität kann die E-Mails ganz stoppen (falscher Benutzer-/Affinitätsname in der Konfiguration) oder den Durchsatz reduzieren (geringe Anzahl von IPs in der Affinität). Mehr dazu erfahren Sie auf [dieser Seite](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* E-Mail-Größe: Die E-Mail-Größe spielt eine wichtige Rolle im Durchsatz. Die empfohlene maximale E-Mail-Größe beträgt 60 KB. Mehr dazu erfahren Sie [Seite](https://helpx.adobe.com/de/legal/product-descriptions/campaign.html). Überprüfen Sie im [Versanddurchsatz](../../reporting/using/global-reports.md#delivery-throughput) die Anzahl der pro Stunde übertragenen Bytes.
* Große Anzahl ungültiger Empfänger: Wenn eine große Anzahl ungültiger Empfänger vorhanden ist, kann dies den Durchsatz beeinträchtigen. Der MTA versucht weiterhin, E-Mails an ungültige Empfänger zu senden. Stellen Sie sicher, dass Ihre Datenbank gut gepflegt ist.
* Umfang der Personalisierung: Wenn ein Versand in &quot;Personalization in Bearbeitung“ bleibt, überprüfen Sie die in Personalisierungsblöcken verwendete JavaScript.

>[!NOTE]
>
>Siehe auch den Abschnitt [Zustellbarkeit](../../delivery/using/about-deliverability.md). Weitere Informationen zur Zustellbarkeit finden Sie im [Adobe-Handbuch mit den Best Practices zur Zustellbarkeit](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=de).

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
source-git-commit: 8fd9949ec03b7c2cdf88a9d5fcf5c8d8fd85f7d0

---


# Leistungs- und Durchsatzprobleme{#performance-and-throughput-issues}

>[!NOTE]
>
>Zunächst sollten Sie überprüfen, ob der neueste Build installiert ist. Dadurch wird sichergestellt, dass Sie über die neuesten Funktionen und Fehlerbehebungen verfügen. Weitere Informationen zum Inhalt der einzelnen Versionen finden Sie in den [Versionshinweisen](https://docs.campaign.adobe.com/doc/AC/en/RN.html) .

## Hardware und Infrastruktur {#hardware-and-infrastructure}

Allgemeine Richtlinien für Hardwareanforderungen für lokale Campaign Classic finden Sie in diesem [Artikel](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html).

Das Beratungsteam kann gehosteten Kunden ein Tool zur Verfügung stellen, mit dem Sie leicht erkennen können, wie viel Platz von verschiedenen Tabellentypen in der Datenbank genutzt wird, sowie den auf der SFTP-Site verwendeten Platz. Darüber hinaus bietet es Tools, mit denen Sie unnötige Daten bereinigen können. Wenden Sie sich an das Beratungs- oder Supportteam, wenn dieses Tool implementiert werden muss. Hier einige wichtige Punkte, die Sie mit diesem Tool überprüfen müssen:

* Wenn die Indexgröße größer als die Tabellengröße ist, ist ein Vakuum erforderlich.
* Überprüfen Sie die Tabellen mit der maximalen Aufblähung. Wenn diese Tabellen häufig verwendet werden, müssen sie evakuiert werden.
* Datenbankblockierung kann dazu führen, dass E-Mails nicht mehr gesendet werden.

Adobe Campaign bietet auch ein [Tool](../../production/using/monitoring-processes.md#manual-monitoring) zur Überprüfung der CPU- und RAM-Nutzung. Verwenden Sie dieses Tool und prüfen Sie spezifische Indikatoren wie: **Arbeitsspeicher**, **Arbeitsspeicher**, **Datenträger**, **aktive Prozesse**. Wenn die Werte zu hoch sind, können Sie versuchen, die Anzahl der Arbeitsabläufe zu reduzieren oder Workflows planen, die zu unterschiedlichen Zeiten beginnen.

## Datenbankleistungen {#database-performances}

In den meisten Fällen sind Leistungsprobleme mit der Datenbankwartung verbunden. Im Folgenden werden die wichtigsten Elemente aufgeführt:

* Konfiguration: Es wird empfohlen, die anfängliche Adobe Campaign-Plattformkonfiguration zu überprüfen und eine vollständige Hardwareprüfung durchzuführen.
* Installation und Konfiguration der Adobe Campaign-Plattform: Überprüfen Sie Netzwerkkonfigurations- und Plattformbereitstellungsoptionen.
* Datenbankwartung: Stellen Sie sicher, dass die Datenbankbereinigungsaufgabe aktiv ist und dass die Datenbankwartung ordnungsgemäß geplant und ausgeführt wird. Überprüfen Sie die Anzahl und Größe der Arbeitstabellen.
* Echtzeitdiagnose: Überprüfen Sie die Prozess- und Plattformprotokolldateien und überwachen Sie dann die Datenbankaktivität, während Sie das Problem neu erstellen.

>[!NOTE]
>
>For more information, refer to this section: [Database performances](../../production/using/database-performances.md).

## Anwendungskonfiguration {#application-configuration}

Im Folgenden finden Sie eine Liste von Artikeln zu Best Practices für die Anwendungskonfiguration:

* MTA- und MTAChild-Prozesse und -Speicher: das **Modul mta** verteilt Nachrichten an seine untergeordneten **mtachild** -Module. Jede **mtachild** erstellt Nachrichten, bevor sie eine Autorisierung vom Statistikserver anfordert und sie sendet. Weitere Informationen finden Sie auf dieser [Seite](../../installation/using/email-deliverability.md) .
* TLS-Konfiguration: Die globale Aktivierung von TLS wird nicht empfohlen, da dies den Durchsatz reduzieren kann. Stattdessen sollten die vom Bereitstellungsteam verwalteten TLS-Einstellungen pro Domäne je nach Bedarf angepasst werden. Weitere Informationen finden Sie auf dieser [Seite](../../installation/using/email-deliverability.md#mx-configuration) .
* DKIM: zur Gewährleistung der Sicherheitsstufe des DKIM ist 1024b die empfohlene Verschlüsselungsgröße. Niedrigere DKIM-Schlüssel werden von den meisten Zugangsanbietern nicht als gültig angesehen. Lesen Sie diese [Seite](../../delivery/using/technical-recommendations.md#dkim) und diese [Technote](https://helpx.adobe.com/campaign/kb/domain-name-delegation.html).

## Probleme mit der Lieferbarkeit {#deliverability-issues}

Im Folgenden finden Sie eine Liste der Best Practices und Artikel im Zusammenhang mit der Lieferbarkeit:

* IP-Ruf: Wenn der IP-Ruf nicht gut genug ist, wirkt sich dies auf die Leistung aus. Das **Lieferbarkeitsüberwachungsmodul** bietet verschiedene Tools zur Verfolgung der Leistung Ihrer Plattform. Mehr dazu erfahren Sie auf [dieser Seite](../../delivery/using/monitoring-deliverability.md).
* IP-Aufwärmen: die IP-Aufwärmphase wird vom Zustellteam durchgeführt. Dazu gehört die schrittweise Erhöhung der Anzahl der E-Mails durch neue IPs über einen Zeitraum von einigen Wochen.
* IP-Affinitätseinstellung: eine falsche IP-Affinitätseinstellung kann die E-Mails ganz stoppen (inkorrekter Operator-/Affinitätsname in der Konfiguration) oder den Durchsatz reduzieren (geringe Anzahl von IPs in der Affinität). Mehr dazu erfahren Sie auf [dieser Seite](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* E-Mail-Größe: Die E-Mail-Größe spielt eine wichtige Rolle beim Durchsatz. Die empfohlene maximale E-Mail-Größe beträgt 60 KB. Mehr dazu erfahren Sie auf [dieser Seite](https://helpx.adobe.com/legal/product-descriptions/campaign.html). Überprüfen Sie im Bericht [Bereitstellungsdurchsatz](../../reporting/using/delivery-reports.md#delivery-throughput) die Anzahl der nach Stunde übertragenen Byte.
* Große Anzahl ungültiger Empfänger: Wenn eine große Anzahl ungültiger Empfänger vorhanden ist, kann dies den Durchsatz beeinflussen. Die MTA versucht weiterhin, E-Mails an ungültige Empfänger zu senden. Stellen Sie sicher, dass Ihre Datenbank gut gepflegt ist.
* Umfang der Personalisierung: Wenn eine Bereitstellung in &quot;Personalisierung in Bearbeitung&quot;bleibt, überprüfen Sie das in Personalisierungsblöcken verwendete JavaScript.

>[!NOTE]
>
>Vergessen Sie nicht, sich an den [Lieferanleitungen](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) zu wenden.


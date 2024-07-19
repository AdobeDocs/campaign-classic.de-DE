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

Zunächst sollten Sie überprüfen, ob der neueste Build installiert ist. Dadurch wird sichergestellt, dass Sie über die neuesten Funktionen und Fehlerkorrekturen verfügen.

Weitere Informationen zum Inhalt der einzelnen Versionen finden Sie in den [Versionshinweisen](../../rn/using/latest-release.md) .

## Hardware und Infrastruktur {#hardware-and-infrastructure}

Allgemeine Richtlinien für Hardwareanforderungen für On-Premise-Campaign Classic finden Sie auf dieser [Seite](https://helpx.adobe.com/de/campaign/kb/hardware-sizing-guide.html).

Das Beratungsteam kann gehosteten Kunden ein Tool zur Verfügung stellen, mit dem Sie leicht erkennen können, wie viel Platz von verschiedenen Tabellentypen in der Datenbank genutzt wird und welcher Platz auf der SFTP-Site genutzt wird. Darüber hinaus stellt es Tools bereit, mit denen Sie unnötige Daten bereinigen können. Wenden Sie sich an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) , wenn dieses Tool implementiert werden muss. Im Folgenden finden Sie einige wichtige Aspekte, die mit diesem Tool überprüft werden müssen:

* Wenn die Indexgröße größer als die Tabellengröße ist, ist ein Vakuum erforderlich.
* Überprüfen Sie die Tabellen, die die maximale Temperatur aufweisen. Wenn diese Tabellen häufig verwendet werden, müssen sie evakuiert werden.
* Das Blockieren der Datenbank kann dazu führen, dass E-Mails nicht mehr gesendet werden.

Adobe Campaign bietet außerdem ein [Tool](../../production/using/monitoring-processes.md#manual-monitoring) zur Überprüfung der CPU- und RAM-Nutzung. Verwenden Sie dieses Tool und sehen Sie sich bestimmte Indikatoren an, z. B.: **Speicher**, **Speicher tauschen**, **Datenträger**, **aktive Prozesse**. Wenn die Werte zu hoch sind, können Sie versuchen, die Anzahl der Workflows zu reduzieren oder Workflows so planen, dass sie zu unterschiedlichen Zeitpunkten beginnen.

## Datenbanküberprüfung {#database-performances}

In den meisten Fällen hängen Leistungsprobleme mit der Datenbankwartung zusammen. Im Folgenden finden Sie die wichtigsten zu prüfenden Elemente:

* Konfiguration: Es wird empfohlen, die anfängliche Konfiguration der Adobe Campaign-Plattform zu überprüfen und eine vollständige Hardwareprüfung durchzuführen.
* Installation und Konfiguration der Adobe Campaign-Plattform: Aktivieren Sie die Optionen für die Netzwerkkonfiguration und die Plattform-Zustellbarkeit.
* Datenbankwartung: Stellen Sie sicher, dass die Datenbankbereinigung funktioniert und die Datenbankwartung ordnungsgemäß geplant und ausgeführt wird. Überprüfen Sie die Anzahl und Größe der Arbeitstabellen.
* Echtzeitdiagnose: Überprüfen Sie die Prozess- und Plattformprotokolldateien und überwachen Sie dann die Datenbankaktivität, während Sie das Problem neu erstellen.

>[!NOTE]
>
>Weitere Informationen finden Sie in diesem Abschnitt: [Datenbankleistung](../../production/using/database-performances.md).

## Anwendungskonfiguration {#application-configuration}

Im Folgenden finden Sie eine Liste von Artikeln zu Best Practices für die Anwendungskonfiguration:

* MTA- und MTAChild-Prozesse und -Speicher: Das Modul **mta** verteilt Nachrichten an seine untergeordneten **mtachild**-Module. Jeder **mtachild** bereitet Nachrichten vor, bevor er eine Autorisierung vom Statistikserver anfordert, und sendet sie. Weitere Informationen finden Sie auf dieser [Seite.](../../installation/using/email-deliverability.md)
* TLS-Konfiguration: Die globale Aktivierung von TLS wird nicht empfohlen, da dadurch der Durchsatz reduziert werden kann. Stattdessen sollten die vom Zustellbarkeitsteam verwalteten TLS-Einstellungen pro Domäne entsprechend den Anforderungen angepasst werden. Weitere Informationen finden Sie auf dieser [Seite.](../../installation/using/email-deliverability.md#mx-configuration)

  >[!NOTE]
  >
  >Die Beauftragung des Zustellbarkeits-Teams ist vertraglich geregelt. Kundinnen und Kunden sollten sich an den Adobe-Support wenden, um diesbezügliche Informationen zu erhalten.

* DKIM: Um das Sicherheitsniveau des DKIM zu gewährleisten, empfiehlt sich die Verschlüsselungsgröße 1024b. Niedrigere DKIM-Schlüssel werden von den meisten Zugangsanbietern nicht als gültig betrachtet. Mehr dazu erfahren Sie auf [dieser Seite](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=de#authentication).

## Probleme mit der Zustellbarkeit {#deliverability-issues}

Im Folgenden finden Sie eine Liste mit Best Practices und Artikeln zur Zustellbarkeit:

* IP-Reputation: Wenn die IP-Reputation nicht gut genug ist, wirkt sich dies auf die Leistung aus. Das Modul **Zustellbarkeits-Monitoring** bietet verschiedene Tools, um die Zustellbarkeitsleistung Ihrer Plattform zu verfolgen. Mehr dazu erfahren Sie auf [dieser Seite](../../delivery/using/monitoring-deliverability.md).
* IP-Warmup: Die IP-Aufwärmung wird vom Zustellbarkeitsteam durchgeführt. Hierzu gehört eine schrittweise Erhöhung der Anzahl der E-Mails durch neue IP-Adressen über einen Zeitraum von einigen Wochen.

  >[!NOTE]
  >
  >Die Beauftragung des Zustellbarkeits-Teams ist vertraglich geregelt. Kundinnen und Kunden sollten sich an den Adobe-Support wenden, um diesbezügliche Informationen zu erhalten.

* IP-Affinitäts-Setup: Eine falsche IP-Affinitätseinstellung kann die E-Mails ganz stoppen (falscher Operator-/Affinitätsname in der Konfiguration) oder den Durchsatz reduzieren (geringe Anzahl von IPs in der Affinität). Mehr dazu erfahren Sie auf [dieser Seite](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* E-Mail-Größe: Die E-Mail-Größe spielt eine wichtige Rolle beim Durchsatz. Die empfohlene maximale E-Mail-Größe beträgt 60 KB. Weitere Informationen finden Sie auf dieser [Seite](https://helpx.adobe.com/legal/product-descriptions/campaign.html). Überprüfen Sie im Bericht [Versanddurchsatz](../../reporting/using/global-reports.md#delivery-throughput) die Anzahl der nach Stunde übertragenen Bytes.
* Große Anzahl ungültiger Empfänger: Bei einer großen Anzahl ungültiger Empfänger kann dies den Durchsatz beeinträchtigen. Der MTA versucht weiterhin, E-Mails an ungültige Empfänger zu senden. Bitte stellen Sie sicher, dass Ihre Datenbank gut gepflegt ist.
* Personalisierungsbetrag: Wenn ein Versand in &quot;Personalization in Bearbeitung&quot;bleibt, überprüfen Sie die JavaScript, die in Gestaltungsbausteinen verwendet wird.

>[!NOTE]
>
>Siehe auch Abschnitt [Zustellbarkeit](../../delivery/using/about-deliverability.md) . Weitere Informationen zur Zustellbarkeit finden Sie im [Adobe-Handbuch mit den Best Practices zur Zustellbarkeit](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=de).

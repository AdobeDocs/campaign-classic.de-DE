---
product: campaign
title: Performance- und Durchsatzprobleme
description: Performance- und Durchsatzprobleme
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
badge-v7-prem: label="On-Premise und Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: fe69efda-a052-4f67-9c13-665f011d0a2b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 10%

---

# Performance- und Durchsatzprobleme{#performance-and-throughput-issues}



Zunächst sollten Sie überprüfen, ob der neueste Build installiert ist. Dadurch wird sichergestellt, dass Sie über die neuesten Funktionen und Fehlerkorrekturen verfügen.

Siehe Abschnitt [Versionshinweise](../../rn/using/latest-release.md) für weitere Informationen zum Inhalt der einzelnen Versionen.

## Hardware und Infrastruktur {#hardware-and-infrastructure}

Die allgemeinen Richtlinien für Hardwareanforderungen für On-Premise-Campaign Classic werden in diesem Abschnitt beschrieben. [page](https://helpx.adobe.com/de/campaign/kb/hardware-sizing-guide.html).

Das Beratungsteam kann gehosteten Kunden ein Tool zur Verfügung stellen, mit dem Sie leicht erkennen können, wie viel Platz von verschiedenen Tabellentypen in der Datenbank genutzt wird und welcher Platz auf der SFTP-Site genutzt wird. Darüber hinaus stellt es Tools bereit, mit denen Sie unnötige Daten bereinigen können. Kontakt [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) , wenn Sie dieses Tool implementieren müssen. Im Folgenden finden Sie einige wichtige Aspekte, die mit diesem Tool überprüft werden müssen:

* Wenn die Indexgröße größer als die Tabellengröße ist, ist ein Vakuum erforderlich.
* Überprüfen Sie die Tabellen, die die maximale Temperatur aufweisen. Wenn diese Tabellen häufig verwendet werden, müssen sie evakuiert werden.
* Das Blockieren der Datenbank kann dazu führen, dass E-Mails nicht mehr gesendet werden.

Adobe Campaign bietet auch eine [Tool](../../production/using/monitoring-processes.md#manual-monitoring) , um die CPU- und RAM-Nutzung zu überprüfen. Verwenden Sie dieses Tool und sehen Sie sich spezifische Indikatoren an, z. B.: **Speicher**, **Speicher tauschen**, **Disk**, **Aktive Prozesse**. Wenn die Werte zu hoch sind, können Sie versuchen, die Anzahl der Workflows zu reduzieren oder Workflows so planen, dass sie zu unterschiedlichen Zeitpunkten beginnen.

## Datenbanküberprüfung {#database-performances}

In den meisten Fällen hängen Leistungsprobleme mit der Datenbankwartung zusammen. Im Folgenden finden Sie die wichtigsten zu prüfenden Elemente:

* Konfiguration: Es wird empfohlen, die anfängliche Konfiguration der Adobe Campaign-Plattform zu überprüfen und eine vollständige Hardwareprüfung durchzuführen.
* Installation und Konfiguration der Adobe Campaign-Plattform: Aktivieren Sie die Optionen für die Netzwerkkonfiguration und die Plattform-Zustellbarkeit.
* Datenbankwartung: Stellen Sie sicher, dass die Datenbankbereinigung funktioniert und die Datenbankwartung ordnungsgemäß geplant und ausgeführt wird. Überprüfen Sie die Anzahl und Größe der Arbeitstabellen.
* Echtzeitdiagnose: Überprüfen Sie die Prozess- und Plattformprotokolldateien und überwachen Sie dann die Datenbankaktivität, während Sie das Problem neu erstellen.

>[!NOTE]
>
>Weiterführende Informationen finden Sie in diesem Abschnitt: [Datenbankleistung](../../production/using/database-performances.md).

## Anwendungskonfiguration {#application-configuration}

Im Folgenden finden Sie eine Liste von Artikeln zu Best Practices für die Anwendungskonfiguration:

* MTA- und MTAChild-Prozesse und -Speicher: die **mta** -Modul verteilt Nachrichten an seine **mtachild** untergeordnete Module. Jeder **mtachild** erstellt Nachrichten, bevor eine Autorisierung vom Statistikserver angefordert wird, und sendet sie. Weitere Informationen finden Sie auf dieser [Seite.](../../installation/using/email-deliverability.md)
* TLS-Konfiguration: Die globale Aktivierung von TLS wird nicht empfohlen, da dadurch der Durchsatz reduziert werden kann. Stattdessen sollten die vom Zustellbarkeitsteam verwalteten TLS-Einstellungen pro Domäne entsprechend den Anforderungen angepasst werden. Weitere Informationen finden Sie auf dieser [Seite.](../../installation/using/email-deliverability.md#mx-configuration)
* DKIM: Um das Sicherheitsniveau des DKIM zu gewährleisten, empfiehlt sich die Verschlüsselungsgröße 1024b. Niedrigere DKIM-Schlüssel werden von den meisten Zugangsanbietern nicht als gültig betrachtet. Mehr dazu erfahren Sie auf [dieser Seite](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=de#authentication).

## Probleme mit der Zustellbarkeit {#deliverability-issues}

Im Folgenden finden Sie eine Liste mit Best Practices und Artikeln zur Zustellbarkeit:

* IP-Reputation: Wenn die IP-Reputation nicht gut genug ist, wirkt sich dies auf die Leistung aus. Die **Zustellbarkeits-Monitoring** bietet verschiedene Tools, um die Zustellbarkeitsleistung Ihrer Plattform zu verfolgen. Mehr dazu erfahren Sie auf [dieser Seite](../../delivery/using/monitoring-deliverability.md).
* IP-Warmup: Die IP-Aufwärmung wird vom Zustellbarkeitsteam durchgeführt. Hierzu gehört eine schrittweise Erhöhung der Anzahl der E-Mails durch neue IP-Adressen über einen Zeitraum von einigen Wochen.
* IP-Affinitäts-Setup: Eine falsche IP-Affinitätseinstellung kann die E-Mails ganz stoppen (falscher Operator-/Affinitätsname in der Konfiguration) oder den Durchsatz reduzieren (geringe Anzahl von IPs in der Affinität). Mehr dazu erfahren Sie auf [dieser Seite](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* E-Mail-Größe: Die E-Mail-Größe spielt eine wichtige Rolle beim Durchsatz. Die empfohlene maximale E-Mail-Größe beträgt 60 KB. Siehe hierzu [page](https://helpx.adobe.com/legal/product-descriptions/campaign.html). Im [Versanddurchsatz](../../reporting/using/global-reports.md#delivery-throughput) -Bericht die Anzahl der Bytes überprüfen, die nach Stunde übertragen wurden.
* Große Anzahl ungültiger Empfänger: Bei einer großen Anzahl ungültiger Empfänger kann dies den Durchsatz beeinträchtigen. Der MTA versucht weiterhin, E-Mails an ungültige Empfänger zu senden. Bitte stellen Sie sicher, dass Ihre Datenbank gut gepflegt ist.
* Personalisierungsbetrag: Wenn ein Versand in &quot;Gestaltete Personalisierung&quot; verbleibt, überprüfen Sie das in Gestaltungsbausteinen verwendete JavaScript.

>[!NOTE]
>
>Siehe auch [Zustellbarkeit](../../delivery/using/about-deliverability.md) Abschnitt. Weitere Informationen zur Zustellbarkeit finden Sie im [Adobe-Handbuch mit den Best Practices zur Zustellbarkeit](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=de).

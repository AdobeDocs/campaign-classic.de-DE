---
title: Datenbankleistungen
seo-title: Datenbankleistungen
description: Datenbankleistungen
seo-description: null
page-status-flag: never-activated
uuid: 47ff7532-1fe7-47c2-bc3b-0f46d3a4a288
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 6358c8fd-2b75-4462-acd1-887ee44d3110
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 34cd6e6cf5652c9e2163848c2b1ef32f53ee6ca4

---


# Datenbankleistungen{#database-performances}

Die meisten Leistungsprobleme sind mit der Datenbankwartung verbunden. Hier sind vier wichtige Hinweise, die Ihnen bei der Suche nach der Ursache für eine langsame Leistung helfen:

* Konfiguration,
* Installation und Konfiguration der Adobe Campaign-Plattform,
* Bereinigung der Datenbank,
* Echtzeitdiagnose.

## Konfiguration {#configuration}

Überprüfen Sie, ob die ursprüngliche Adobe Campaign-Plattformkonfiguration noch gültig ist, und überprüfen Sie bei Bedarf die Anforderungen Ihres Kunden hinsichtlich der Lieferbarkeit oder der Datenbankgröße neu. Es wird empfohlen, eine vollständige Hardwareprüfung (CPU, RAM, IO-System) durchzuführen.

>[!NOTE]
>
>Einblicke dazu finden Sie im Handbuch[ zu ](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html)Adobe Campaign Harware Sizing.

## Plattformkonfiguration {#platform-configuration}

Eine unangemessene Konfiguration kann sich auf die Plattformleistung auswirken. Es wird empfohlen, die Netzwerkkonfiguration, die Optionen für die Plattformbereitstellung sowie die MTA-Konfiguration in der Datei &quot; **serverConf.xml** &quot;zu überprüfen.

## Bereinigung der Datenbank {#database-maintenance}

**Datenbankbereinigungsaufgabe**

Stellen Sie sicher, dass die Datenbankbereinigungsaufgabe aktiv ist. Zeigen Sie dazu die Protokolldateien an, um zu sehen, ob sie Fehler enthalten. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../production/using/database-cleanup-workflow.md).

**Instandhaltungspläne**

Stellen Sie sicher, dass die Datenbankwartung korrekt geplant und ausgeführt wurde. Wenden Sie sich hierfür an Ihren Datenbankadministrator, um mehr über Folgendes zu erfahren:

* ihre Instandhaltungspläne,
* zuvor ausgeführte Instandhaltungspläne,
* die Skriptprotokolle anzeigen.

Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../production/using/recommendations.md).

>[!CAUTION]
>
>Wenn Sie eine Midsourcing-Konfiguration verwenden, ist es wichtig, dass Datenbanken regelmäßig gepflegt werden. Bei der Analyse einer Bereitstellung auf der Marketing-Plattform sendet die Marketing-Instanz Informationen an die Mid-Sourcing-Instanz. Wenn der Prozess verlangsamt wird, wird die Marketinginstanz beeinträchtigt.

**Verwalten von Arbeitstabellen**

Bitte überprüfen Sie die Anzahl und Größe der Arbeitstische. Wenn sie eine bestimmte Größe überschreiten, wirkt sich dies auf die Datenbankleistung aus. Diese Tabellen werden durch Arbeitsabläufe und Auslieferungen erstellt. Sie bleiben in der Datenbank, während Workflows und Auslieferungen aktiv sind. Um die Größe von Arbeitstabellen zu begrenzen, können Sie die folgenden Vorgänge ausführen:

* Auslieferungen mit folgenden Status beenden oder löschen: **[!UICONTROL Failed]** , **[!UICONTROL In progress]** , **[!UICONTROL Ready for delivery]** oder **[!UICONTROL Paused]** .
* Workflows, die aufgrund eines Fehlers angehalten werden, beenden oder löschen,
* beenden Sie alle Arbeitsabläufe, die für Tests verwendet werden, die keine **[!UICONTROL End]** Aktivität enthalten und deren Status daher erhalten bleibt **[!UICONTROL Paused]** .

>[!CAUTION]
>
>Wenn der Vorgang eine lange Zeit in Anspruch nimmt und viel Platz frei macht, bedeutet dies, dass eine gründliche Wartung erforderlich ist (Indexrekonstruktion usw.). Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../production/using/recommendations.md).

**Prozessüberwachung in Adobe Campaign**

Abhängig von den Installationseinstellungen von Adobe Campaign können zwei Tools zur Plattformüberwachung verwendet werden:

* die Produktionsseite der Instanz. For more on this, refer to [Manual monitoring](../../production/using/monitoring-processes.md#manual-monitoring).
* das Skript netreport. Weitere Informationen finden Sie unter [Automatische Überwachung über Adobe Campaign-Skripten](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts).

## Spezifikationen {#specifics}

Es kann erforderlich werden, eine Echtzeitdiagnose durchzuführen, um die Ursache des Problems zu ermitteln. Überprüfen Sie zunächst die Prozess- und Plattformprotokolldateien und überwachen Sie dann die Datenbankaktivität, während Sie das Problem erneut erstellen. Achten Sie insbesondere auf Folgendes:

* den Instandhaltungsplan,
* SQL-Abfragen, die ausgeführt werden,
* unabhängig davon, ob externe Prozesse gleichzeitig ausgeführt werden (Reinigung, Import, Berechnung der Aggregation usw.).


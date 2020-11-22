---
solution: Campaign Classic
product: campaign
title: Datenbankleistung
description: Datenbankleistung
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 8%

---


# Datenbankleistung{#database-performances}

Die meisten Leistungsprobleme sind mit der Datenbankwartung verbunden. Hier sind vier wichtige Hinweise, die Ihnen bei der Suche nach der Ursache für eine langsame Leistung helfen:

* Konfiguration,
* Installation und Konfiguration der Adobe Campaign-Plattform,
* Wartung der Datenbank,
* Echtzeitdiagnose.

## Konfiguration {#configuration}

Überprüfen Sie, ob die anfängliche Adobe Campaign-Plattformkonfiguration noch gültig ist, und überprüfen Sie bei Bedarf die Anforderungen Ihres Kunden hinsichtlich der Lieferbarkeit oder der Datenbankgröße neu. Es wird empfohlen, eine vollständige Hardware-Prüfung durchzuführen (CPU, RAM, IO-System).

>[!NOTE]
>
>Einblicke dazu finden Sie im Leitfaden [zum](https://helpx.adobe.com/de/campaign/kb/hardware-sizing-guide.html) Adobe Campaign Harware Sizing.

## Plattformkonfiguration {#platform-configuration}

Eine unangemessene Konfiguration kann sich auf die Plattformleistung auswirken. Es wird empfohlen, die Netzwerkkonfiguration, die Optionen für die Plattformbereitstellung sowie die MTA-Konfiguration in der Datei &quot; **serverConf.xml** &quot;zu überprüfen.

## Bereinigung der Datenbank {#database-maintenance}

**Aufgabe zur Datenbankbereinigung**

Stellen Sie sicher, dass die Aufgabe zur Datenbankbereinigung betriebsbereit ist. Ansicht Sie dazu die Protokolldateien, um festzustellen, ob sie Fehler enthalten. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../production/using/database-cleanup-workflow.md).

**Instandhaltungspläne**

Stellen Sie sicher, dass die Datenbankwartung korrekt geplant und ausgeführt wurde. Wenden Sie sich hierfür an Ihren Datenbankadministrator, um mehr über Folgendes zu erfahren:

* ihre Instandhaltungspläne,
* zuvor ausgeführte Instandhaltungspläne,
* ansicht der Skriptprotokolle.

Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../production/using/recommendations.md).

>[!IMPORTANT]
>
>Wenn Sie eine Mid-Sourcing-Konfiguration verwenden, ist es wichtig, dass Datenbanken regelmäßig gepflegt werden. Beim Analysieren eines Versands auf der Marketing-Plattform sendet die Marketing-Instanz Informationen an die Mid-Sourcing-Instanz. Wenn der Prozess verlangsamt wird, wird die Marketinginstanz beeinträchtigt.

**Verwalten von Arbeitstabellen**

Bitte überprüfen Sie die Anzahl und Größe der Arbeitstische. Wenn sie eine bestimmte Größe überschreiten, wirkt sich dies auf die Datenbankleistung aus. Diese Tabellen werden von Workflows und Versänden erstellt. Sie bleiben in der Datenbank, während Workflows und Versand aktiv sind. Um die Größe von Arbeitstabellen zu begrenzen, können Sie die folgenden Vorgänge ausführen:

* versand mit den folgenden Status beenden oder löschen: **[!UICONTROL Fehlgeschlagen]** , **[!UICONTROL Wird]** ausgeführt , **[!UICONTROL Bereit für Versand]** oder **[!UICONTROL Angehalten]** .
* workflows, die aufgrund eines Fehlers angehalten wurden, beenden oder löschen,
* alle Workflows, die für Tests verwendet werden, die keine **[!UICONTROL End]** -Aktivität enthalten und deren Status daher **[!UICONTROL angehalten]** bleibt, beenden.

>[!IMPORTANT]
>
>Wenn der Vorgang eine lange Zeit in Anspruch nimmt und viel Platz frei macht, bedeutet dies, dass eine gründliche Wartung erforderlich ist (Indexrekonstruktion usw.). Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../production/using/recommendations.md).

**Adobe Campaign-Prozessüberwachung**

Abhängig von den Installationseinstellungen des Adobe Campaigns können zwei Tools zur Plattformüberwachung verwendet werden:

* die Produktionsseite der Instanz. For more on this, refer to [Manual monitoring](../../production/using/monitoring-processes.md#manual-monitoring).
* das Skript netreport. Weitere Informationen finden Sie unter [Automatische Überwachung über Adobe Campaign-Skripte](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts).

## Spezifikationen {#specifics}

Es kann erforderlich werden, eine Echtzeitdiagnose durchzuführen, um die Ursache des Problems zu identifizieren. Beginn überprüfen Sie die Prozess- und Plattformprotokolldateien und überwachen Sie dann die Aktivität der Datenbank, während Sie die Ausgabe erneut erstellen. Achten Sie insbesondere auf Folgendes:

* den Instandhaltungsplan,
* SQL-Abfragen, die ausgeführt werden,
* unabhängig davon, ob externe Prozesse gleichzeitig ausgeführt werden (Datenbereingung, Importe, Aggregat usw.).


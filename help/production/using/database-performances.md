---
product: campaign
title: Datenbankleistung
description: Datenbankleistung
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 33dcfd4b-51fd-44f4-98e0-23eafb79d7da
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 8%

---

# Datenbankleistung{#database-performances}

![](../../assets/v7-only.svg)

Die meisten Leistungsprobleme hängen mit der Datenbankwartung zusammen. Im Folgenden finden Sie vier wichtige Hinweise, die Ihnen bei der Suche nach der Ursache für eine langsame Leistung helfen:

* Konfiguration
* Installation und Konfiguration der Adobe Campaign-Plattform
* Wartung der Datenbank
* Echtzeitdiagnose

## Konfiguration {#configuration}

Überprüfen Sie, ob die ursprüngliche Adobe Campaign-Plattformkonfiguration weiterhin gültig ist, und überprüfen Sie bei Bedarf die Anforderungen Ihres Kunden hinsichtlich Zustellbarkeit oder Datenbankgröße neu. Es wird auch empfohlen, eine vollständige Hardware-Prüfung durchzuführen (CPU, RAM, IO-System).

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Handbuch zur Hardwarebemessung von Adobe Campaign](https://helpx.adobe.com/de/campaign/kb/hardware-sizing-guide.html) für Einblicke.

## Plattformkonfiguration {#platform-configuration}

Eine unangemessene Konfiguration kann sich auf die Leistung der Plattform auswirken. Es wird empfohlen, die Netzwerkkonfiguration, die Optionen für die Zustellbarkeit von Plattformen sowie die MTA-Konfiguration im Abschnitt **serverConf.xml** -Datei.

## Wartung der Datenbank {#database-maintenance}

**Aufgabe &quot;Datenbankbereinigung&quot;**

Stellen Sie sicher, dass die Datenbankbereinigung funktioniert. Zeigen Sie dazu die Protokolldateien an, um zu sehen, ob sie Fehler enthalten. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../production/using/database-cleanup-workflow.md).

**Wartungspläne**

Stellen Sie sicher, dass die Datenbankwartung korrekt geplant und ausgeführt wurde. Wenden Sie sich diesbezüglich an Ihren Datenbankadministrator, um mehr über folgende Themen zu erfahren:

* Instandhaltungsplanung
* Zuvor ausgeführte Wartungspläne
* Skriptprotokolle anzeigen

Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../production/using/recommendations.md).

>[!IMPORTANT]
>
>Wenn Sie eine Mid-Sourcing-Konfiguration verwenden, ist es wichtig, dass Datenbanken regelmäßig gepflegt werden. Bei der Analyse eines Versands auf der Marketing-Plattform sendet die Marketing-Instanz Informationen an die Mid-Sourcing-Instanz. Wenn der Prozess verlangsamt wird, wirkt sich dies auf die Marketing-Instanz aus.

**Arbeitstabellen verwalten**

Bitte überprüfen Sie Anzahl und Größe der Arbeitstabellen. Wenn sie eine bestimmte Größe überschreiten, wirkt sich dies auf die Datenbankleistung aus. Diese Tabellen werden durch Workflows und Sendungen erstellt. Sie bleiben in der Datenbank, während Workflows und Sendungen aktiv sind. Um die Größe von Arbeitstabellen zu begrenzen, können Sie die folgenden Aktionen durchführen:

* Sendungen mit den folgenden Status anhalten oder löschen: **[!UICONTROL Fehlgeschlagen]**, **[!UICONTROL In Bearbeitung]**, **[!UICONTROL Versandbereit]** oder **[!UICONTROL Angehalten]**.
* Workflows, die aufgrund eines Fehlers ausgesetzt wurden, beenden oder löschen.
* Beenden Sie alle Workflows, die für Tests verwendet werden, die keine **[!UICONTROL Ende]** Tätigkeit, deren Status somit erhalten bleibt **[!UICONTROL Angehalten]**.

>[!IMPORTANT]
>
>Wenn der Vorgang lange dauert und viel Speicherplatz freisetzt, bedeutet dies, dass eine gründliche Wartung erforderlich ist (Neuerstellung von Indizes usw.). Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../production/using/recommendations.md).

**Adobe Campaign-Prozessüberwachung**

Abhängig von den Adobe Campaign-Installationseinstellungen können für die Plattformüberwachung zwei Tools verwendet werden:

* Die Produktionsseite der Instanz. Weitere Informationen hierzu finden Sie unter [Manuelle Überwachung](../../production/using/monitoring-processes.md#manual-monitoring).
* Die *netreport* Skript. Weitere Informationen hierzu finden Sie unter [Automatische Überwachung über Adobe Campaign-Skripte](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts).

## Spezifikationen {#specifics}

Es kann erforderlich werden, eine Echtzeitdiagnose durchzuführen, um die Ursache des Problems zu ermitteln. Überprüfen Sie zunächst die Prozess- und Plattformprotokolldateien und überwachen Sie dann die Datenbankaktivität, während Sie das Problem neu erstellen. Beachten Sie insbesondere Folgendes:

* Instandhaltungsplan
* SQL-Abfragen werden ausgeführt
* Gibt an, ob externe Prozesse gleichzeitig ausgeführt werden (Bereinigung, Importe, Aggregatberechnung usw.).

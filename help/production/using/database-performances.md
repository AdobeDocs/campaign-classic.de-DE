---
product: campaign
title: Datenbankleistung
description: Datenbankleistung
feature: Monitoring
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 33dcfd4b-51fd-44f4-98e0-23eafb79d7da
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 8%

---

# Datenbank-Performance{#database-performances}



Die meisten Leistungsprobleme hängen mit der Datenbankwartung zusammen. Im Folgenden finden Sie vier wichtige Hinweise, die Ihnen dabei helfen, die Ursache für die langsame Leistung zu finden:

* Konfiguration
* Installation und Konfiguration der Adobe Campaign-Plattform
* Wartung der Datenbank
* Echtzeitdiagnose

## Konfiguration {#configuration}

Vergewissern Sie sich, dass die anfängliche Adobe Campaign-Plattformkonfiguration weiterhin gültig ist, und bewerten Sie bei Bedarf die Anforderungen Ihres Kunden in Bezug auf Zustellbarkeit oder Datenbankgröße neu. Es wird außerdem empfohlen, eine vollständige Hardwareprüfung durchzuführen (CPU, RAM, IO-System).

>[!NOTE]
>
>Weitere Informationen finden Sie in der Anleitung zur Hardware-Dimensionierung ](https://helpx.adobe.com/de/campaign/kb/hardware-sizing-guide.html) [Adobe Campaign.

## Platform-Konfiguration {#platform-configuration}

Unsachgemäße Konfigurationen können die Plattformleistung beeinträchtigen. Es wird empfohlen, die Netzwerkkonfiguration, Plattformzustellbarkeitsoptionen sowie die MTA-Konfiguration in der Datei **serverConf.xml** zu überprüfen.

## Wartung der Datenbank {#database-maintenance}

**Datenbankbereinigungsaufgabe**

Stellen Sie sicher, dass die Datenbankbereinigung betriebsbereit ist. Sehen Sie sich dazu die Protokolldateien an, um festzustellen, ob sie Fehler enthalten. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../production/using/database-cleanup-workflow.md).

**Wartungspläne**

Stellen Sie sicher, dass die Datenbankwartung korrekt geplant und ausgeführt wird. Wenden Sie sich dazu an Ihren Datenbankadministrator, um mehr über Folgendes zu erfahren:

* Ihr Wartungsplan
* Zuvor ausgeführte Wartungspläne
* Anzeigen der Skriptprotokolle

Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../production/using/recommendations.md).

>[!IMPORTANT]
>
>Wenn Sie eine Mid-Sourcing-Konfiguration verwenden, ist es wichtig, dass Datenbanken regelmäßig gepflegt werden. Bei der Analyse eines Versands auf der Marketing-Plattform sendet die Marketing-Instanz Informationen an die Mid-Sourcing-Instanz. Wenn der Prozess verlangsamt wird, ist die Marketing-Instanz betroffen.

**Arbeitstabellen verwalten**

Bitte Anzahl und Größe der Arbeitstabellen überprüfen. Wenn sie eine bestimmte Größe überschreiten, wird die Datenbankleistung beeinträchtigt. Diese Tabellen werden von Workflows und Sendungen erstellt. Sie verbleiben in der Datenbank, während Workflows und Sendungen aktiv sind. Um die Größe von Arbeitstabellen zu begrenzen, können Sie die folgenden Vorgänge ausführen:

* Beenden oder löschen Sie Sendungen mit den Status **[!UICONTROL Fehlgeschlagen]**, **[!UICONTROL In]**, **[!UICONTROL Bereit für Versand]** oder **[!UICONTROL Paused]**.
* Beenden oder Löschen von Workflows, die aufgrund eines Fehlers angehalten wurden.
* Beenden Sie alle Workflows, die für Tests verwendet werden, die keine **[!UICONTROL Ende]**-Aktivität enthalten und deren Status daher &quot;**[!UICONTROL &quot;]**.

>[!IMPORTANT]
>
>Wenn der Vorgang lange dauert und viel Platz freisetzt, bedeutet dies, dass eine gründliche Wartung erforderlich ist (Neuerstellung des Index usw.). Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../production/using/recommendations.md).

**Adobe Campaign-Prozessüberwachung**

Abhängig von den Adobe Campaign-Installationseinstellungen können zwei Tools zur Plattformüberwachung verwendet werden:

* Die Produktionsseite der Instanz. Weitere Informationen hierzu finden Sie unter [Manuelle Überwachung](../../production/using/monitoring-processes.md#manual-monitoring).
* Das *netreport*-Skript. Weitere Informationen hierzu finden Sie unter [Automatische Überwachung über Adobe Campaign-Skripte](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts).

## Besonderheiten {#specifics}

Es kann erforderlich werden, eine Echtzeitdiagnose durchzuführen, um die Ursache des Problems zu identifizieren. Überprüfen Sie zunächst die Prozess- und Platform-Protokolldateien und überwachen Sie dann die Datenbankaktivität, während Sie das Problem neu erstellen. Achten Sie insbesondere auf Folgendes:

* Der Plan zur Wartungsausführung
* Ausgeführte SQL-Abfragen
* Ob gleichzeitig externe Prozesse ausgeführt werden (Bereinigung, Importe, Aggregatberechnung usw.).

---
product: campaign
title: Zeitzonen-Management
description: Zeitzonen-Management
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: e5ed96cc-3fc7-4af4-a29e-5a4c81f4fe39
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '905'
ht-degree: 1%

---

# Zeitzonen-Management{#time-zone-management}

## Grundprinzip {#operating-principle}

Mit Adobe Campaign können Sie Datumsangaben anhand ihrer Zeitzone angeben: Dadurch können internationale Benutzer weltweit an verschiedenen Zeitzonen arbeiten. Jedes Land, das dieselbe Instanz verwendet, kann die Ausführung von Kampagnen, Tracking, Archivierung usw. verwalten. abhängig von der Ortszeit.

Damit die Adobe Campaign-Plattform auf internationaler Ebene genutzt werden kann, müssen alle von den Systemen verwendeten Daten mit einer Zeitzone verknüpft werden können. Ein Datum, dessen Zeitzone bekannt ist, kann daher unabhängig von der Zeitzone in eine andere Zeitzone importiert werden.

Mit Adobe Campaign können Sie Daten/Uhrzeiten im UTC-Format (Coordinated Universal Time) speichern. Wenn Daten verfügbar gemacht werden, werden sie in das lokale Datum/die lokale Uhrzeit des Benutzers konvertiert. Die Konvertierung erfolgt automatisch, wenn die Datenbank in UTC konfiguriert ist (siehe [Konfiguration](#configuration)). Wenn die Datenbank nicht in UTC konfiguriert ist, werden Informationen zur Zeitzone der Daten in der Plattform in einer Option gespeichert.

Die wichtigsten Plattformfunktionen für das Zeitzonen-Management sind: Import-/Export-Daten und Benutzer- und Workflow-Management. Das **Vererbungskonzept** ist für Importe/Exporte oder Workflows verfügbar. Standardmäßig sind sie für die Zeitzone des Datenbankservers konfiguriert. Sie können jedoch neue Zeitzonen für einen Workflow und sogar für eine einzelne Aktivität definieren.

**** Benutzer können die Zeitzonen während der  **Versandkonfiguration** ändern und die Zeitzone angeben, in der der Versand ausgeführt werden soll.

>[!IMPORTANT]
>
>Wenn die Datenbank nicht mehrere Zeitzonen verwaltet, müssen SQL-Abfragen für alle Datenfiltermanipulationen in der Zeitzone des Datenbankservers ausgeführt werden.

Jeder Adobe Campaign-Operator ist mit einer Zeitzone verknüpft: Diese Informationen werden in ihrem Profil konfiguriert. Weitere Informationen hierzu finden Sie in [diesem Dokument](../../platform/using/access-management.md).

Wenn die Adobe Campaign-Plattform keine Zeitzonen-Verwaltung erfordert, können Sie einen Speichermodus im lokalen Format mit einer bestimmten verknüpften Zeitzone beibehalten.

## Recommendations {#recommendations}

Zeitzonen kombinieren verschiedene Realitäten: Der Ausdruck kann eine konstante Zeitverzögerung mit dem UTC-Datum oder die Zeiten einer Region beschreiben, die sich zweimal jährlich ändern können (Sommerzeit).

In postgreSQL beispielsweise berücksichtigt der Befehl **SET TIME ZONE &#39;Europe/Paris&#39;;** Sommer- und Winterzeiten: das Datum wird in UTC+1 oder UTC+2 je nach Jahreszeit ausgedrückt.

Wenn Sie jedoch den Befehl **SET TIME ZONE 0200;** verwenden, ist die Zeitverzögerung immer UTC+2.

## Konfiguration {#configuration}

Der Speichermodus für Datum und Uhrzeit wird während der Datenbankerstellung ausgewählt (siehe [Erstellen einer neuen Instanz](#creating-a-new-instance)). Bei einer Migration werden die mit Daten verknüpften Stunden in lokale Daten und Stunden umgewandelt (siehe [Migration](#migration)).

Aus technischer Sicht gibt es zwei Möglichkeiten, **Date+time** Typinformationen in der Datenbank zu speichern:

1. ZEITSTEMPEL IM TIMEZONformat: Die Datenbank-Engine speichert Daten in UTC. Jede geöffnete Sitzung verfügt über eine Zeitzone und die Daten werden entsprechend konvertiert.
1. Lokales Format + lokale Zeitzone: Alle Daten werden im lokalen Format gespeichert (keine Zeitverzögerung) und ihnen wird eine einzige Zeitzone zugewiesen. Die Zeitzone wird in der Option **WdbcTimeZone** der Adobe Campaign-Instanz gespeichert und kann über das Menü **[!UICONTROL Administration > Plattform > Optionen]** des Navigationsbaums geändert werden.

>[!IMPORTANT]
>
>Bitte beachten Sie, dass diese Änderung zu Problemen bei der Datenkonsistenz und Synchronisierung führen kann.

### Erstellen einer neuen Instanz {#creating-a-new-instance}

Damit mehrere internationale Benutzer an derselben Instanz arbeiten können, müssen Sie bei der Erstellung der Instanz Zeitzonen konfigurieren, um Zeitzonen zwischen Ländern zu verwalten. Wählen Sie bei der Instanzerstellung im Abschnitt **[!UICONTROL Zeitzone]** der Datenbankkonfigurationsphase den Datums- und Uhrzeitmanagementmodus aus.

Aktivieren Sie die Option **[!UICONTROL UTC-Datenbank (Datumsfelder mit Zeitzone)]** , um alle Daten mit Datum und Uhrzeit im UTC-Format (SQL-Felder und XML-Felder) zu speichern.

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>Wenn Sie **Oracle** verwenden, müssen die Zeitzonendateien (.dat) der Oracle-Client-Ebenen mit den auf dem Server installierten Zeitzonendateien kompatibel sein.

Wenn die Datenbank nicht UTC ist, können Sie eine der in der Dropdown-Liste angebotenen Zeitzonen auswählen. Sie können auch die Zeitzone des Servers verwenden oder die Option UTC (Coordinated Universal Time) auswählen.

![](assets/install_wz_unselect_utc_option.png)

Wenn die Option **[!UICONTROL UTC Database (Datumsfelder mit Zeitzone)]** ausgewählt ist, werden die SQL-Felder im Format TIMESTAMP MIT ZEITZONE gespeichert.

Andernfalls werden sie im lokalen Format gespeichert und Sie müssen die Zeitzone auswählen, die auf die Datenbank angewendet werden soll.

### Migration {#migration}

Bei der Migration zu einer früheren Version (ohne Zeitzonen-Management) müssen Sie den Datenspeichermodus in der Datenbank definieren.

Um die Kompatibilität mit externen Tools sicherzustellen, die auf die Adobe Campaign-Datenbank zugreifen, bleiben die SQL-Felder vom Typ **Datum+Uhrzeit** standardmäßig im lokalen Format gespeichert.

XML-Felder, die Datumsangaben enthalten, werden jetzt in UTC gespeichert. Beim Laden werden Felder, die nicht im UTC-Format vorliegen, automatisch mithilfe der Zeitzone des Servers konvertiert. Dies bedeutet, dass alle XML-Felder schrittweise in das UTC-Format konvertiert werden.

Um eine vorhandene Instanz zu verwenden, fügen Sie die Option **WdbcTimeZone** hinzu und geben Sie die Zeitzone der Instanz ein.

>[!IMPORTANT]
>
>Stellen Sie sicher, dass der richtige Wert für die WdbcTimeZone-Option konfiguriert ist: später vorgenommene Änderungen können zu Inkonsistenzen führen.

Beispiel möglicher Werte:

* Europe/Paris,
* Europa/London,
* America/New_York usw.

   Diese Werte werden aus der tz-Datenbank (Olson) übernommen. Weitere Informationen finden Sie unter [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

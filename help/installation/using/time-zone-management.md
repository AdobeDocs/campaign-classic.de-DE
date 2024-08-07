---
product: campaign
title: Zeitzonen-Management
description: Zeitzonen-Management
feature: Installation, Instance Settings
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: e5ed96cc-3fc7-4af4-a29e-5a4c81f4fe39
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '970'
ht-degree: 2%

---

# Zeitzonen-Management{#time-zone-management}



## Grundprinzip {#operating-principle}

Mit Adobe Campaign können Sie Datumsangaben entsprechend ihrer Zeitzone angeben: Dies ermöglicht es internationalen Benutzern, in verschiedenen Zeitzonen weltweit zu arbeiten. Jedes Land, das dieselbe Instanz verwendet, kann die Ausführung von Kampagnen, Tracking, Archivierung usw. verwalten. abhängig von der Ortszeit.

Damit die Adobe Campaign-Plattform international genutzt werden kann, müssen alle von den Systemen verwendeten Daten mit einer Zeitzone verknüpft werden können. Ein Datum, dessen Zeitzone bekannt ist, kann daher unabhängig von der Zeitzone in eine andere Zeitzone importiert werden.

Mit Adobe Campaign können Sie Daten/Uhrzeiten im UTC-Format (Coordinated Universal Time) speichern. Wenn Daten verfügbar gemacht werden, werden sie in das lokale Datum/die lokale Uhrzeit des Benutzers konvertiert. Die Konvertierung erfolgt automatisch, wenn die Datenbank in UTC konfiguriert ist (siehe [Konfiguration](#configuration)). Wenn die Datenbank nicht in UTC konfiguriert ist, werden Informationen zur Zeitzone der Daten in der Plattform in einer Option gespeichert.

Die wichtigsten Plattformfunktionen im Zeitzonen-Management sind: Import/Export von Daten und Benutzer- und Workflow-Management. Das **Vererbungskonzept** ist für Importe/Exporte oder Workflows verfügbar. Standardmäßig sind sie für die Zeitzone des Datenbankservers konfiguriert. Sie können jedoch neue Zeitzonen für einen Workflow und sogar für eine einzelne Aktivität definieren.

**Benutzer** können die Zeitzonen während der **Versandkonfiguration** ändern und die Zeitzone angeben, in der der Versand ausgeführt wird.

>[!IMPORTANT]
>
>Wenn die Datenbank nicht mehrere Zeitzonen verwaltet, müssen SQL-Abfragen für alle Datenfiltermanipulationen in der Zeitzone des Datenbankservers ausgeführt werden.

Jeder Adobe Campaign-Benutzer ist einer Zeitzone zugeordnet: Diese Informationen werden in seinem Profil konfiguriert. Weitere Informationen hierzu finden Sie in [diesem Dokument](../../platform/using/access-management.md).

Wenn die Adobe Campaign-Plattform keine Zeitzonen-Verwaltung erfordert, können Sie einen Speichermodus im lokalen Format mit einer bestimmten verknüpften Zeitzone beibehalten.

## Empfehlungen {#recommendations}

Zeitzonen kombinieren mehrere Realitäten: Der Ausdruck kann eine konstante Zeitverzögerung mit dem UTC-Datum oder die Zeiten einer Region beschreiben, die sich zweimal im Jahr ändern kann (Sommerzeit).

In postgreSQL beispielsweise berücksichtigt der Befehl **SET TIME ZONE &#39;Europe/Paris&#39;;** Sommer- und Winterzeiten: Das Datum wird je nach Jahreszeit in UTC+1 oder UTC+2 ausgedrückt.

Wenn Sie jedoch den Befehl **ZEITZONE 0200;** verwenden, ist die Zeitverzögerung immer UTC+2.

## Konfiguration {#configuration}

Der Speichermodus für Datum und Uhrzeit wird während der Datenbankerstellung ausgewählt (siehe [Erstellen einer neuen Instanz](#creating-a-new-instance)). Bei einer Migration werden die mit Datumsangaben verknüpften Stunden in lokale Daten und Stunden umgewandelt (siehe [Migration](#migration)).

Aus technischer Sicht gibt es zwei Möglichkeiten, Informationen vom Typ **Datum+Uhrzeit** in der Datenbank zu speichern:

1. Format ZEITSTEMPEL MIT ZEITZONE: Die Datenbank-Engine speichert Datumsangaben in UTC. Jede geöffnete Sitzung verfügt über eine Zeitzone und die Daten werden entsprechend konvertiert.
1. Lokales Format + lokale Zeitzone: Alle Daten werden im lokalen Format gespeichert (keine Zeitverzögerungsverwaltung) und ihnen wird eine einzige Zeitzone zugewiesen. Die Zeitzone wird in der Option **WdbcTimeZone** der Adobe Campaign-Instanz gespeichert und kann über das Menü **[!UICONTROL Administration > Plattform > Optionen]** des Navigationsbaums geändert werden.

>[!IMPORTANT]
>
>Bitte beachten Sie, dass diese Änderung zu Problemen bei der Datenkonsistenz und Synchronisierung führen kann.

### Erstellen einer neuen Instanz {#creating-a-new-instance}

Damit mehrere internationale Benutzer an derselben Instanz arbeiten können, müssen Sie bei der Erstellung der Instanz Zeitzonen konfigurieren, um Zeitzonen zwischen Ländern zu verwalten. Wählen Sie bei der Instanzerstellung im Abschnitt **[!UICONTROL Zeitzone]** der Datenbankkonfigurationsphase den Datums- und Uhrzeitverwaltungsmodus aus.

Aktivieren Sie die Option **[!UICONTROL UTC-Datenbank (Datumsfelder mit Zeitzone)]** , um alle Daten mit Datum und Uhrzeit im UTC-Format (SQL-Felder und XML-Felder) zu speichern.

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>Wenn Sie **Oracle** verwenden, müssen die Zeitzonendateien (.dat) der Oracle-Client-Ebenen mit den auf dem Server installierten Zeitzonendateien kompatibel sein.

Wenn die Datenbank nicht UTC ist, können Sie eine der in der Dropdown-Liste angebotenen Zeitzonen auswählen. Sie können auch die Zeitzone des Servers verwenden oder die Option UTC (Coordinated Universal Time) auswählen.

![](assets/install_wz_unselect_utc_option.png)

Wenn die Option **[!UICONTROL UTC Database (date fields with time zone)]** ausgewählt ist, werden die SQL-Felder im Format TIMESTAMP WITH TIMEZONE gespeichert.

Andernfalls werden sie im lokalen Format gespeichert und Sie müssen die Zeitzone auswählen, die auf die Datenbank angewendet werden soll.

### Migration {#migration}

Bei der Migration zu einer früheren Version (ohne Zeitzonen-Management) müssen Sie den Datenspeichermodus in der Datenbank definieren.

Um die Kompatibilität mit externen Tools sicherzustellen, die auf die Adobe Campaign-Datenbank zugreifen, bleiben die SQL-Felder vom Typ **Datum+Uhrzeit** standardmäßig im lokalen Format gespeichert.

XML-Felder, die Datumsangaben enthalten, werden jetzt in UTC gespeichert. Beim Laden werden Felder, die nicht im UTC-Format vorliegen, automatisch mithilfe der Zeitzone des Servers konvertiert. Dies bedeutet, dass alle XML-Felder schrittweise in das UTC-Format konvertiert werden.

Um eine vorhandene Instanz zu verwenden, fügen Sie die Option **WdbcTimeZone** hinzu und geben Sie die Zeitzone der Instanz ein.

>[!IMPORTANT]
>
>Stellen Sie sicher, dass der richtige Wert für die Option WdbcTimeZone konfiguriert ist: Später durchgeführte Änderungen können zu Inkonsistenzen führen.

Beispiel möglicher Werte:

* Europe/Paris,
* Europe/London,
* America/New_York usw.

  Diese Werte werden aus der tz-Datenbank (Olson) übernommen. Weitere Informationen finden Sie unter [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

## Oracle-Datenbank und Zeitzone des Servers

Für die Hauptdatenbank verwendet Campaign die Zeitzone des Servers, um die Zeitzone der Sitzung für die Datenbankverbindung festzulegen. Die Option &quot;WdbcTimeZone&quot;hat keine Auswirkungen. Die Zeitzone des Servers sollte also mit der Zeitzone der von Campaign verwendeten Hauptdatenbank übereinstimmen. Wenn Sie die Zeitzone des Servers nicht ändern können, kann die von Campaign verwendete Zeitzone überschrieben werden, indem Sie die TZ-Umgebungsvariable in customer.sh festlegen.
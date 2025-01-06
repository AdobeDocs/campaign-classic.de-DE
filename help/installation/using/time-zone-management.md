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
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '970'
ht-degree: 2%

---

# Zeitzonen-Management{#time-zone-management}



## Grundprinzip {#operating-principle}

Mit Adobe Campaign können Sie Termine in Abhängigkeit von ihrer Zeitzone angeben. Dies ermöglicht es internationalen Anwendern, weltweit an verschiedenen Zeitzonen zu arbeiten. Jedes Land, das dieselbe Instanz verwendet, kann die Ausführung von Kampagnen, Tracking, Archivierung usw. verwalten Abhängig von der Ortszeit.

Damit die Adobe Campaign-Plattform international genutzt werden kann, müssen alle von den Systemen verwendeten Daten mit einer Zeitzone verknüpft werden können. Ein Datum, dessen Zeitzone bekannt ist, kann somit in eine beliebige andere Zeitzone oder unabhängig von der Zeitzone importiert werden.

Mit Adobe Campaign können Sie Daten/Uhrzeiten im UTC-Format (Coordinated Universal Time) speichern. Wenn Daten verfügbar gemacht werden, werden sie in das lokale Datum/die lokale Uhrzeit des Benutzers konvertiert. Die Konvertierung wird automatisch durchgeführt, wenn die Datenbank in UTC konfiguriert ist (siehe [Konfiguration](#configuration)). Wenn die Datenbank nicht in UTC konfiguriert ist, werden Informationen zur Zeitzone der Datumsangaben in der Plattform in einer Option gespeichert.

Die wichtigsten Plattformfunktionen zur Zeitzonenverwaltung sind: Import/Export von Daten sowie Benutzer- und Workflow-Verwaltung. Das **Vererbungskonzept** ist für Importe/Exporte oder Workflows verfügbar. Sie sind standardmäßig für die Zeitzone des Datenbank-Servers konfiguriert. Sie können jedoch neue Zeitzonen für einen Workflow und sogar für eine einzelne Aktivität neu definieren.

**Benutzer** können die Zeitzonen während der **Versandkonfiguration** ändern und die bestimmte Zeitzone angeben, in der der Versand ausgeführt wird.

>[!IMPORTANT]
>
>Wenn die Datenbank nicht mehrere Zeitzonen verwaltet, müssen für alle Datenfiltermanipulationen SQL-Abfragen in der Zeitzone des Datenbank-Servers ausgeführt werden.

Jeder Adobe Campaign-Benutzer ist mit einer Zeitzone verknüpft: Diese Informationen werden in seinem Profil konfiguriert. Weiterführende Informationen hierzu finden Sie in [diesem Dokument](../../platform/using/access-management.md).

Wenn für die Adobe Campaign-Plattform keine Zeitzonenverwaltung erforderlich ist, können Sie einen Speichermodus im lokalen Format mit einer bestimmten verknüpften Zeitzone beibehalten.

## Empfehlungen {#recommendations}

Zeitzonen kombinieren mehrere Realitäten: Der Ausdruck kann eine konstante Zeitverzögerung mit dem UTC-Datum beschreiben, oder die Zeiten einer Region, die sich zweimal im Jahr ändern kann (Sommerzeit).

In PostgreSQL beispielsweise berücksichtigt der Befehl **ZEITZONE FESTLEGEN &#39;Europa/Paris&#39;;** Sommer- und Winterzeit: Das Datum wird je nach Jahreszeit in UTC+1 oder UTC+2 angegeben.

Wenn Sie jedoch den Befehl **ZEITZONE 0200;** festlegen verwenden, ist die Zeitverzögerung immer UTC+2.

## Konfiguration {#configuration}

Der Speichermodus für Datum und Uhrzeit wird bei der Datenbankerstellung ausgewählt (siehe [Erstellen einer neuen Instanz](#creating-a-new-instance)). Im Falle einer Migration werden die mit Datumsangaben verknüpften Stunden in lokale Daten und Stunden konvertiert (siehe [Migration](#migration)).

Aus technischer Sicht gibt es zwei Möglichkeiten, Typinformationen vom Typ **Datum+Uhrzeit** in der Datenbank zu speichern:

1. ZEITSTEMPEL IM ZEITZONENFORMAT: Die Datenbank-Engine speichert Datumsangaben in UTC. Jede Sitzung, die geöffnet wird, hat eine Zeitzone und die Daten werden entsprechend konvertiert.
1. Lokales Format + lokale Zeitzone: Alle Daten werden im lokalen Format gespeichert (keine Zeitverzögerungsverwaltung) und ihnen wird eine einzige Zeitzone zugewiesen. Die Zeitzone wird in der Option **WdbcTimeZone** der Adobe Campaign-Instanz gespeichert und kann über das Menü **[!UICONTROL Administration > Plattform > Optionen]** des Navigationsbaums geändert werden.

>[!IMPORTANT]
>
>Beachten Sie, dass diese Änderung zu Datenkonsistenz- und Synchronisationsproblemen führen kann.

### Erstellen einer neuen Instanz {#creating-a-new-instance}

Damit mehrere internationale Benutzer an derselben Instanz arbeiten können, müssen Sie beim Erstellen der Instanz die Zeitzonen konfigurieren, um Zeitverzögerungen zwischen Ländern zu verwalten. Wählen Sie während der Instanzerstellung im Abschnitt **[!UICONTROL Zeitzone“ der Datenbankkonfigurationsphase den]**- und Zeitverwaltungsmodus aus.

Aktivieren Sie die Option **[!UICONTROL UTC-Datenbank (Datumsfelder mit Zeitzone)]**, um alle Daten mit Daten und Uhrzeiten im UTC-Format (SQL-Felder und XML-Felder) zu speichern.

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>Wenn Sie **Oracle** verwenden, müssen die Zeitzonendateien (.dat) der Oracle-Client-Ebenen mit den auf dem Server installierten Zeitzonendateien kompatibel sein.

Wenn die Datenbank nicht UTC ist, können Sie eine der in der Dropdown-Liste angebotenen Zeitzonen auswählen. Sie können auch die Zeitzone des Servers verwenden oder die Option UTC (Coordinated Universal Time) auswählen.

![](assets/install_wz_unselect_utc_option.png)

Wenn die Option **[!UICONTROL UTC-Datenbank (Datumsfelder mit Zeitzone)]** ausgewählt ist, werden die SQL-Felder im Format ZEITSTEMPEL MIT ZEITZONE gespeichert.

Andernfalls werden sie im lokalen Format gespeichert und Sie müssen die Zeitzone auswählen, die auf die Datenbank angewendet werden soll.

### Migration {#migration}

Bei der Migration auf eine frühere Version (ohne Zeitzonenverwaltung) müssen Sie den Datenspeicherungsmodus in der Datenbank definieren.

Um die Kompatibilität mit externen Tools, die auf die Adobe Campaign-Datenbank zugreifen, zu gewährleisten **bleiben die SQL** Felder vom Typ „Datum+Uhrzeit“ standardmäßig im lokalen Format gespeichert.

XML-Felder, die Datumsangaben enthalten, werden jetzt in UTC gespeichert. Während des Ladevorgangs werden Felder, die nicht im UTC-Format vorliegen, automatisch anhand der Zeitzone des Servers konvertiert. Das bedeutet, dass alle XML-Felder schrittweise in das UTC-Format konvertiert werden.

Um eine vorhandene Instanz zu verwenden, fügen Sie die Option **WdbcTimeZone** hinzu und geben Sie die Zeitzone der Instanz ein.

>[!IMPORTANT]
>
>Stellen Sie sicher, dass für die Option „WdbcTimeZone“ der richtige Wert konfiguriert ist. Später vorgenommene Änderungen können zu Inkonsistenzen führen.

Beispiel für mögliche Werte:

* Europa/Paris,
* Europe/London,
* America/New_York usw.

  Diese Werte werden aus der tz-Datenbank (Olson) übernommen. Weitere Informationen finden Sie unter [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

## Oracle-Datenbank und Server-Zeitzone

Für die Hauptdatenbank verwendet Campaign die Zeitzone des Servers, um die Zeitzone der Sitzung für die Datenbankverbindung festzulegen. Die Option „WdbcTimeZone“ hat keine Auswirkungen. Die Zeitzone des Servers sollte daher mit der Zeitzone der von Campaign verwendeten Hauptdatenbank übereinstimmen. Wenn Sie die Zeitzone des Servers nicht ändern können, kann die von Campaign verwendete Zeitzone überschrieben werden, indem die Umgebungsvariable TZ in customer.sh festgelegt wird.
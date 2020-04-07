---
title: Zugriff auf externe Datenbanken
seo-title: Zugriff auf externe Datenbanken
description: Zugriff auf externe Datenbanken
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 6143f23e05f4528a9d76aece3a6e41165e2f95d4

---


# Zugriffsberechtigungen auf Remote-Datenbank {#remote-database-access-rights}

Damit ein Benutzer über FDA Aktionen in einer Datenbank ausführen kann, muss er über eine entsprechende Berechtigung in Adobe Campaign verfügen.

1. Wählen Sie die **[!UICONTROL Administration > Access Management > Named Rights]** Node im Adobe Campaign Explorer aus.
1. Erstellen Sie eine neue Berechtigung, indem Sie einen Titel eingeben.
1. Das Feld **[!UICONTROL Name]** muss das Format **user:base@server** aufweisen, wobei:

   * **user** dem Namen des Benutzers in der externen Datenbank entspricht.
   * **base** dem Namen der externen Datenbank entspricht.
   * **server** dem Namen des Servers der externen Datenbank entspricht.

      >[!NOTE]
      >
      >Der Teil **:base** ist in Oracle optional.

1. Save the named right then link it to your chosen user from the **[!UICONTROL Administration > Access Management > Operators]** node of the Adobe Campaign explorer.

Damit die in einer externen Datenbank enthaltenen Daten verarbeitet werden können, muss der Adobe-Campaign-Benutzer zumindest Schreibberechtigungen für die Datenbank besitzen, damit er Arbeitstabellen erstellen kann. Diese werden automatisch von Adobe Campaign gelöscht.

Generell sind die folgenden Berechtigungen erforderlich:

* **CONNECT**: Verbindung mit der Remote-Datenbank,
* **READ Data**: Nur Lesezugriff auf Tabellen, die Kundendaten enthalten,
* **READ &#39;MetaData&#39;**: Zugriff auf Serverdatenkataloge zum Abruf der Tabellenstruktur,
* **LOAD**: Ladevorgänge für große Datenmengen in Arbeitstabellen (erforderlich bei der Arbeit an Kollektionen und Joins),
* **CREATE/DROP** for **TABLE/INDEX/PROCEDURE/FUNCTION** (nur für von Adobe Campaign generierte Tabellen),
* **EXPLAIN** (empfohlen): für die Leistungsüberwachung im Fall von Problemen,
* **WRITE Data** (abhängig vom Integrationsszenario).

Der Datenbankadministrator muss sicherstellen, dass diese Rechte mit den für die einzelnen Datenbankmaschinen spezifischen Rechten übereinstimmen. Weitere Informationen finden Sie im folgenden Abschnitt.

## FDA {#fda-rights}

|   | Snowflake | Redshift | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Verbindung zur Remote-Datenbank herstellen** | VERWENDUNG IN WAREHOUSE, NUTZUNG AUF DATENBANK UND VERWENDUNG AUF SCHEMA | Erstellen eines mit dem AWS-Konto verknüpften Benutzers | Berechtigung &quot;SITZUNG ERSTELLEN&quot; | CONNECT-Berechtigung | CONNECT-Berechtigung | Erstellen eines Benutzers, der mit einem Remote-Host verbunden ist, der ALLE BERECHTIGUNGEN hat |
| **Erstellen von Tabellen** | CREATE TABLE ON SCHEMA - Berechtigung | Berechtigung ERSTELLEN | Berechtigung &quot;CREATE TABLE&quot; | Berechtigung &quot;TABELLEN ERSTELLEN&quot; | Berechtigung ERSTELLEN | Berechtigung ERSTELLEN |
| **Erstellen von Indizes** | K. A. | Berechtigung ERSTELLEN | INDEX- oder ERSTELLUNGSBEDINGUNGEN FÜR INDEX | ALTER-Berechtigung | Berechtigung ERSTELLEN | INDEX-Berechtigung |
| **Erstellen von Funktionen** | FUNKTION FÜR SCHEMA ERSTELLEN | USAGE ON LANGUAGE plpythonu Privileg, um externe Python Skripte aufrufen zu können | VERFAHREN ERSTELLEN oder EINE BELIEBIGE VERFAHRENSberechtigung ERSTELLEN | Berechtigung &quot;FUNKTION ERSTELLEN&quot; | USAGE-Berechtigung | ROUTINE-Berechtigung ERSTELLEN |
| **Verfahren erstellen** | K. A. | USAGE ON LANGUAGE plpythonu Privileg, um externe Python Skripte aufrufen zu können | VERFAHREN ERSTELLEN oder EINE BELIEBIGE VERFAHRENSberechtigung ERSTELLEN | Berechtigung &quot;VERFAHREN ERSTELLEN&quot; | USAGE-Berechtigung (Verfahren sind Funktionen) | ROUTINE-Berechtigung ERSTELLEN |
| **Objekte entfernen (Tabellen, Indizes, Funktionen, Verfahren)** | Eigentümer des Objekts | Eigentümer des Objekts oder Superuser | ALLE &lt; Objekt > Berechtigung ABLAUFEN | ALTER-Berechtigung | Tabelle: Besitz des Tabellenindex: Inhaber der Indexfunktion: Eigentümer der Funktion | DROP-Berechtigung |
| **Überwachen von Hinrichtungen** | MONITOR-Berechtigung für das erforderliche Objekt | Keine Berechtigung erforderlich, um den Befehl EXPLAIN zu verwenden | INSERT- und SELECT-Berechtigung und erforderliche Berechtigung, um die Anweisung auszuführen, auf der der EXPLAIN-PLAN basiert | SHOWPLAN-Berechtigung | Für die Verwendung der EXPLAIN-Anweisung ist keine Berechtigung erforderlich | SELECT-Berechtigung |
| **Daten schreiben** | INSERT- und/oder UPDATE-Berechtigungen (je nach Schreibvorgang) | INSERT- und UPDATE-Berechtigungen | EINFÜGEN und AKTUALISIEREN oder EINFÜGEN UND AKTUALISIEREN VON BELIEBIGEN TABELLENberechtigungen | INSERT- und UPDATE-Berechtigungen | INSERT- und UPDATE-Berechtigungen | INSERT- und UPDATE-Berechtigungen |
| **Daten in Tabellen laden** | &quot;STAGE AUF SCHEMA ERSTELLEN&quot;, &quot;AUSWÄHLEN&quot;und &quot;EINFÜGEN&quot;auf den Berechtigungen der Zielgruppe | AUSWÄHLEN UND EINFÜGEN | AUSWÄHLEN UND EINFÜGEN | INSERT-, ADMINISTER-BULK-VORGÄNGE und ALTER TABELLENberechtigungen | AUSWÄHLEN UND EINFÜGEN | DATEI-Berechtigung |
| **Zugriff auf Client-Daten** | &quot;AUF (ZUKÜNFTIGE) TABELLE(EN)&quot;ODER &quot;ANSICHT(n)&quot;AUSWÄHLEN | SELECT-Berechtigung | AUSWÄHLEN ODER AUSWÄHLEN DER BELIEBIGEN TABELLENRECHTE | Berechtigung AUSWÄHLEN | SELECT-Berechtigung | SELECT-Berechtigung |
| **Zugriff auf Metadaten** | WÄHLEN SIE DIE SCHEMA-Berechtigung &quot;INFORMATION_SCHEMA&quot; | SELECT-Berechtigung | Keine Berechtigung erforderlich, um die Anweisung &quot;DESCRIPTION&quot;zu verwenden | Berechtigung &quot;ANSICHT DEFINITION&quot; | Keine Berechtigung erforderlich, um den Befehl &quot;\d table&quot;zu verwenden | SELECT-Berechtigung |

|   | DB2 UDB | TeraData | InfiniDB | Sybase IQ/Sybase ASE | Netezza | Grollen | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Verbindung zur Remote-Datenbank herstellen** | CONNECT-Behörde | CONNECT-Berechtigung | Erstellen eines Benutzers, der mit einem Remote-Host verbunden ist, der ALLE BERECHTIGUNGEN hat | Keine Berechtigung erforderlich für die Verwendung der CONNECT-Anweisung | Keine Berechtigung erforderlich | CONNECT-Berechtigung | CONNECT-Berechtigung |
| **Erstellen von Tabellen** | CREATETAB-Behörde | CREATE TABLE or TABLE keyword | Berechtigung ERSTELLEN | RESSOURCENbehörde und Berechtigung ERSTELLEN | Berechtigung für TABELLE | Berechtigung ERSTELLEN | Berechtigung ERSTELLEN |
| **Erstellen von Indizes** | INDEX-Berechtigung | CREATE INDEX or INDEX keyword | INDEX-Berechtigung | RESSOURCENbehörde und Berechtigung ERSTELLEN | INDEX-Berechtigung | Berechtigung ERSTELLEN | Berechtigung ERSTELLEN |
| **Erstellen von Funktionen** | IMPLICIT_SCHEMA-Behörde oder CREATEIN-Berechtigung | CREATE FUNCTION or FUNCTION keyword | ROUTINE-Berechtigung ERSTELLEN | RESOURCE-Behörde oder DBA-Behörde für Java-Funktionen | FUNKTIONSBERECHTIGUNG | USAGE-Berechtigung | Berechtigung &quot;FUNKTION ERSTELLEN&quot; |
| **Verfahren erstellen** | IMPLICIT_SCHEMA-Behörde oder CREATEIN-Berechtigung | VERFAHREN ODER VERFAHREN ERSTELLEN | ROUTINE-Berechtigung ERSTELLEN | RESSOURCEN | VERFAHRENSRECHT | USAGE-Berechtigung | Berechtigung &quot;FUNKTION ERSTELLEN&quot; |
| **Objekte entfernen (Tabellen, Indizes, Funktionen, Verfahren)** | DROPIN-Berechtigung oder -STEUERUNGSBerechtigung oder Eigentümer des Objekts | DROP &lt; Objekt > oder objektbezogener Suchbegriff | DROP-Berechtigung | Eigentümer des Objekts oder der DBA-Behörde | DROP-Berechtigung | Eigentümer des Objekts | Eigentümer des Objekts |
| **Überwachen von Hinrichtungen** | ERLÄUTERUNGSSTELLE | Für die Verwendung der EXPLAIN-Anweisung ist keine Berechtigung erforderlich | SELECT-Berechtigung | Nur ein Systemadministrator kann sp_showplan ausführen | Für die Verwendung der EXPLAIN-Anweisung ist keine Berechtigung erforderlich | Für die Verwendung der EXPLAIN-Anweisung ist keine Berechtigung erforderlich | Für die Verwendung der EXPLAIN-Anweisung ist keine Berechtigung erforderlich |
| **Daten schreiben** | INSERT- und UPDATE-Berechtigungen oder DATAACCESS-Behörde | INSERT- und UPDATE-Berechtigungen | INSERT- und UPDATE-Berechtigungen | INSERT- und UPDATE-Berechtigungen | INSERT- und UPDATE-Berechtigungen | INSERT- und UPDATE-Berechtigungen | INSERT- und UPDATE-Berechtigungen |
| **Daten in Tabellen laden** | LOAD-Behörde | Berechtigungen AUSWÄHLEN und EINFÜGEN, um die Anweisungen COPY TO bzw. COPY VON zu verwenden | DATEI-Berechtigung | Seien Sie der Eigentümer der Tabelle oder der ALTER-Berechtigung. Abhängig von der Option -gl kann LOAD TABLE nur ausgeführt werden, wenn der Benutzer über die DBA-Autorität verfügt | AUSWÄHLEN UND EINFÜGEN | AUSWÄHLEN UND EINFÜGEN | AUSWÄHLEN UND EINFÜGEN |
| **Zugriff auf Client-Daten** | INSERT/UPDATE-Berechtigungen oder DATAACCESS-Behörde | SELECT-Berechtigung | SELECT-Berechtigung | Berechtigung AUSWÄHLEN | SELECT-Berechtigung | SELECT-Berechtigung | SELECT-Berechtigung |
| **Zugriff auf Metadaten** | Keine Autorisierung erforderlich für die Verwendung der Anweisung | ANZEIGEN, Berechtigung | SELECT-Berechtigung | Keine Berechtigung erforderlich für die Verwendung der Anweisung &quot;DESCRIPTION&quot; | Keine Berechtigung erforderlich, um den Befehl &quot;\d table&quot;zu verwenden | Keine Berechtigung erforderlich, um den Befehl &quot;\d table&quot;zu verwenden | Keine Berechtigung erforderlich, um den SHOW-Befehl zu verwenden |
---
title: Zugriff auf eine externe Datenbank
description: Zugriffsberechtigungen für externe Datenbanken
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 9bbde65aea6735e30e95e75c2b6ae5445d4a2bdd
workflow-type: tm+mt
source-wordcount: '1029'
ht-degree: 99%

---


# Zugriffsberechtigungen auf Remote-Datenbank {#remote-database-access-rights}

Damit ein Benutzer über FDA Aktionen in einer Datenbank ausführen kann, muss er über eine entsprechende Berechtigung in Adobe Campaign verfügen.

1. Wählen Sie im Adobe-Campaing-Explorer über den Knoten **[!UICONTROL Administration > Zugriffe > Spezifische Berechtigungen]** aus.
1. Erstellen Sie eine neue Berechtigung, indem Sie einen Titel eingeben.
1. Das Feld **[!UICONTROL Name]** muss das Format **user:base@server** aufweisen, wobei:

   * **user** dem Namen des Benutzers in der externen Datenbank entspricht.
   * **base** dem Namen der externen Datenbank entspricht.
   * **server** dem Namen des Servers der externen Datenbank entspricht.

      >[!NOTE]
      >
      >Der Teil **:base** ist in Oracle optional.

1. Speichern Sie die spezifische Berechtigung und verknüpfen Sie sie dann mit dem ausgewählten Benutzer über den Knoten **[!UICONTROL Administration > Zugriffe > Benutzer]** im Adobe-Campaign-Explorer.

Damit die in einer externen Datenbank enthaltenen Daten verarbeitet werden können, muss der Adobe-Campaign-Benutzer zumindest Schreibberechtigungen für die Datenbank besitzen, damit er Arbeitstabellen erstellen kann. Diese werden automatisch von Adobe Campaign gelöscht.

Generell sind die folgenden Berechtigungen erforderlich:

* **CONNECT**: Verbindung mit der Remote-Datenbank,
* **READ Data**: Nur Lesezugriff auf Tabellen, die Kundendaten enthalten,
* **READ &#39;MetaData&#39;**: Zugriff auf Serverdatenkataloge zum Abruf der Tabellenstruktur,
* **LOAD**: Ladevorgänge für große Datenmengen in Arbeitstabellen (erforderlich bei der Arbeit an Kollektionen und Joins),
* **CREATE/DROP** für **TABLE/INDEX/PROCEDURE/FUNCTION** (nur bei von Adobe Campaign generierten Tabellen),
* **EXPLAIN** (empfohlen): für die Leistungsüberwachung im Fall von Problemen,
* **WRITE Data** (abhängig vom Integrationsszenario).

Der Datenbankadministrator muss sicherstellen, dass diese Berechtigungen mit den spezifischen Berechtigungen der einzelnen Datenbank-Engines übereinstimmen. Weitere Informationen finden Sie im folgenden Abschnitt.

## FDA-Berechtigungen {#fda-rights}

|   | Snowflake | Redshift | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Herstellen einer Verbindung zu einer Remote-Datenbank** | Berechtigungen USAGE ON WAREHOUSE, USAGE ON DATABASE und USAGE ON SCHEMA | Erstellen eines mit dem AWS-Konto verknüpften Benutzers | Berechtigung CREATE SESSION | Berechtigung CONNECT | Berechtigung CONNECT | Erstellen eines Benutzers, der mit einem Remotehost verbunden ist, der ALLE BERECHTIGUNGEN hat |
| **Erstellen von Tabellen** | Berechtigung CREATE TABLE ON SCHEMA | Berechtigung CREATE | Berechtigung CREATE TABLE | Berechtigung CREATE TABLE | Berechtigung CREATE | Berechtigung CREATE |
| **Erstellen von Indizes** | K. A. | Berechtigung CREATE | Berechtigung INDEX oder CREATE ANY INDEX | Berechtigung ALTER | Berechtigung CREATE | Berechtigung INDEX |
| **Erstellen von Funktionen** | Berechtigung CREATE FUNCTION ON SCHEMA | Berechtigung USAGE ON LANGUAGE plpythonu, um externe Python-Skripte aufrufen zu können | Berechtigung CREATE PROCEDURE oder CREATE ANY PROCEDURE | Berechtigung CREATE FUNCTION | Berechtigung USAGE | Berechtigung CREATE ROUTINE |
| **Erstellen von Verfahren** | K. A. | Berechtigung USAGE ON LANGUAGE plpythonu, um externe Python-Skripte aufrufen zu können | Berechtigung CREATE PROCEDURE oder CREATE ANY PROCEDURE | Berechtigung CREATE PROCEDURE | Berechtigung USAGE (Verfahren sind Funktionen) | Berechtigung CREATE ROUTINE |
| **Entfernen von Objekten (Tabellen, Indizes, Funktionen, Verfahren)** | Eigentümer des Objekts | Eigentümer des Objekts oder Superuser | Berechtigung DROP ANY &lt; Objekt > | Berechtigung ALTER | Tabelle: Eigentümer der Tabelle Index: Eigentümer des Index Funktion: Eigentümer der Funktion | Berechtigung DROP |
| **Überwachen von Ausführungen** | Berechtigung MONITOR für das erforderliche Objekt | Keine Berechtigung erforderlich, um den Befehl EXPLAIN zu verwenden | Berechtigung INSERT und SELECT und erforderliche Berechtigung, um die Anweisung auszuführen, auf der EXPLAIN PLAN basiert | Berechtigung SHOWPLAN | Zur Verwendung der EXPLAIN-Anweisung ist keine Berechtigung erforderlich | Berechtigung SELECT |
| **Schreiben von Daten** | Berechtigungen INSERT und/oder UPDATE (je nach Schreibvorgang) | Berechtigungen INSERT und UPDATE | Berechtigungen INSERT und UPDATE oder INSERT und UPDATE ANY TABLE | Berechtigungen INSERT und UPDATE | Berechtigungen INSERT und UPDATE | Berechtigungen INSERT und UPDATE |
| **Laden von Daten in Tabellen** | Berechtigungen CREATE STAGE ON SCHEMA, SELECT und INSERT für die Zieltabelle | Berechtigungen SELECT und INSERT | Berechtigungen SELECT und INSERT | Berechtigungen INSERT, ADMINISTER BULK OPERATIONS und ALTER TABLE | Berechtigungen SELECT und INSERT | Berechtigung FILE |
| **Zugreifen auf Client-Daten** | Berechtigungen SELECT für (FUTURE) TABLE(S) oder VIEW(S) | Berechtigung SELECT | Berechtigung SELECT oder SELECT ANY TABLE | Berechtigung SELECT | Berechtigung SELECT | Berechtigung SELECT |
| **Zugreifen auf Metadaten** | Berechtigung SELECT für INFORMATION_SCHEMA SCHEMA | Berechtigung SELECT | Keine Berechtigung zur Verwendung der Anweisung DESCRIBE erforderlich | Berechtigung VIEW DEFINITION | Keine Berechtigung erforderlich, um den Befehl „\d table“ zu verwenden | Berechtigung SELECT |

|   | DB2 UDB | Teradata | InfiniDB | Sybase IQ/Sybase ASE | Netezza | Greenplum | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Herstellen einer Verbindung zu einer Remote-Datenbank** | Entscheidungsniveau CONNECT | Berechtigung CONNECT | Erstellen eines Benutzers, der mit einem Remotehost verbunden ist, der ALLE BERECHTIGUNGEN hat | Keine Berechtigung erforderlich für die Verwendung der CONNECT-Anweisung | Keine Berechtigung erforderlich | Berechtigung CONNECT | Berechtigung CONNECT |
| **Erstellen von Tabellen** | Entscheidungsniveau CREATETAB | Schlüsselwort CREATE TABLE oder TABLE | Berechtigung CREATE | Entscheidungsniveau RESOURCE und Berechtigung CREATE | Berechtigung TABLE | Berechtigung CREATE | Berechtigung CREATE |
| **Erstellen von Indizes** | Berechtigung INDEX | Schlüsselwort CREATE INDEX oder INDEX | Berechtigung INDEX | Entscheidungsniveau RESOURCE und Berechtigung CREATE | Berechtigung INDEX | Berechtigung CREATE | Berechtigung CREATE |
| **Erstellen von Funktionen** | Entscheidungsniveau IMPLICIT_SCHEMA oder Berechtigung CREATEIN | Schlüsselwort CREATE FUNCTION oder FUNCTION | Berechtigung CREATE ROUTINE | Entscheidungsniveau RESOURCE oder Entscheidungsniveau DBA für Java-Funktionen | Berechtigung FUNCTION | Berechtigung USAGE | Berechtigung CREATE FUNCTION |
| **Erstellen von Verfahren** | Entscheidungsniveau IMPLICIT_SCHEMA oder Berechtigung CREATEIN | Schlüsselwort CREATE PROCEDURE oder PROCEDURE | Berechtigung CREATE ROUTINE | Entscheidungsniveau RESOURCE | Berechtigung PROCEDURE | Berechtigung USAGE | Berechtigung CREATE FUNCTION |
| **Entfernen von Objekten (Tabellen, Indizes, Funktionen, Verfahren)** | Berechtigung DROPIN oder Berechtigung CONTROL oder Eigentümer des Objekts | DROP &lt; Objekt > oder objektbezogenes Schlüsselwort | Berechtigung DROP | Eigentümer des Objekts oder Entscheidungsniveau DBA | Berechtigung DROP | Eigentümer des Objekts | Eigentümer des Objekts |
| **Überwachen von Ausführungen** | Entscheidungsniveau EXPLAIN | Zur Verwendung der EXPLAIN-Anweisung ist keine Berechtigung erforderlich | Berechtigung SELECT | Nur ein Systemadministrator kann sp_showplan ausführen | Zur Verwendung der EXPLAIN-Anweisung ist keine Berechtigung erforderlich | Zur Verwendung der EXPLAIN-Anweisung ist keine Berechtigung erforderlich | Zur Verwendung der EXPLAIN-Anweisung ist keine Berechtigung erforderlich |
| **Schreiben von Daten** | Berechtigungen INSERT und UPDATE oder Entscheidungsniveau DATAACCESS | Berechtigungen INSERT und UPDATE | Berechtigungen INSERT und UPDATE | Berechtigungen INSERT und UPDATE | Berechtigungen INSERT und UPDATE | Berechtigungen INSERT und UPDATE | Berechtigungen INSERT und UPDATE |
| **Laden von Daten in Tabellen** | Entscheidungsniveau LOAD | Berechtigungen SELECT und INSERT, um die Anweisungen COPY TO bzw. COPY FROM zu verwenden | Berechtigung FILE | Seien Sie Eigentümer der Tabelle oder der ALTER-Berechtigung. Je nach der Option -gl kann LOAD TABLE ggf. nur ausgeführt werden, wenn der Benutzer über das Entscheidungsniveau DBA verfügt | Berechtigungen SELECT und INSERT | Berechtigungen SELECT und INSERT | Berechtigungen SELECT und INSERT |
| **Zugreifen auf Client-Daten** | Berechtigungen INSERT/UPDATE oder Entscheidungsniveau DATAACCESS | Berechtigung SELECT | Berechtigung SELECT | Berechtigung SELECT | Berechtigung SELECT | Berechtigung SELECT | Berechtigung SELECT |
| **Zugreifen auf Metadaten** | Kein Entscheidungsniveau erforderlich für die Verwendung der Anweisung DESCRIBE | Berechtigung SHOW | Berechtigung SELECT | Keine Berechtigung erforderlich für die Verwendung der Anweisung DESCRIBE | Keine Berechtigung erforderlich, um den Befehl „\d table“ zu verwenden | Keine Berechtigung erforderlich, um den Befehl „\d table“ zu verwenden | Keine Berechtigung erforderlich, um den SHOW-Befehl zu verwenden |
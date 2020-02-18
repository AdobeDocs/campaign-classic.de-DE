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
source-git-commit: d2758b5e81d1720a4f01a610e51c4a33995d88d1

---


# Zugriffsberechtigungen auf Remote-Datenbank {#remote-database-access-rights}

Damit ein Benutzer über FDA Aktionen in einer Datenbank ausführen kann, muss er über eine entsprechende Berechtigung in Adobe Campaign verfügen.

1. Wählen Sie den **[!UICONTROL Administration > Access Management > Named Rights]** Knoten im Adobe Campaign-Explorer aus.
1. Erstellen Sie eine neue Berechtigung, indem Sie einen Titel eingeben.
1. The **[!UICONTROL Name]** field must take the following format **user:base@server**, where :

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
* **CREATE/DROP** für **TABLE/INDEX/PROCEDURE/FUNCTION**,
* **EXPLAIN** (empfohlen): für die Leistungsüberwachung im Fall von Problemen,
* **WRITE Data** (abhängig vom Integrationsszenario).

>[!NOTE]
>
>Der Datenbankadministrator muss diese Berechtigungen an die jeweiligen Berechtigungen für jede Datenbank-Engine anpassen. Weiterführende Informationen finden Sie unter [Spezifische RDBMS-Berechtigungen](https://docs.campaign.adobe.com/doc/AC6.1/en/technicalResources/technicalResources.html).
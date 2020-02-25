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
source-git-commit: cb081f893b7da13cda5892409b063b8781e93b2a

---


# Herstellung der Datenbankverbindung {#connecting-to-the-database}

Um eine Verbindung mit der externe Datenbank zu ermöglichen, müssen Sie die Verbindungsparameter angeben, d. h. die gewünschte Datenquelle und den Namen der Tabelle mit den zu ladenden Daten.

>[!CAUTION]
>
>Der Adobe Campaign-Benutzer benötigt spezifische Rechte für die externe Datenbank und den Adobe Campaign-Anwendungsserver, um Daten aus einer externen Datenbank zu verarbeiten. Weitere Informationen finden Sie im Abschnitt [Zugriffsrechte](../../platform/using/remote-database-access-rights.md) für Remote-Datenbanken.
>
>Um Fehlfunktionen zu verhindern, müssen Benutzer, die auf geteilte Remote-Daten zugreifen, von getrennten Arbeitsplätzen aus arbeiten.

## Geteilte Verbindung erstellen {#creating-a-shared-connection}

Sie können auf eine gemeinsam genutzte externe Datenbank über Adobe Campaign zugreifen, vorausgesetzt die Verbindung ist aktiv.

1. Die Konfiguration muss vorher über den **[!UICONTROL Administration > Platform > External accounts]** Knoten definiert werden.
1. Klicken Sie auf die **[!UICONTROL New]** Schaltfläche und wählen Sie den **[!UICONTROL External database]** Typ aus.
1. Define the **[!UICONTROL Connection]** parameters of the external database.

   Bei Verbindungen zu einer **ODBC**-Datenbank muss das Feld **[!UICONTROL Server]** den Namen der ODBC-Datenquelle und nicht den Servernamen enthalten. Darüber hinaus können je nach verwendeter Datenbank zusätzliche Konfigurationen erforderlich sein. Siehe Abschnitt [Spezifische Konfigurationen nach Datenbanktyp](../../platform/using/specific-configuration-database.md) .

1. Once the parameters are entered, click the **[!UICONTROL Test the connection]** button to approve them.

   ![](assets/wf-external-account-create.png)

1. If necessary, uncheck the **[!UICONTROL Enabled]** option to disable access to this database without deleting its configuration.
1. Damit Adobe Campaign auf diese Datenbank zugreifen kann, müssen Sie die SQL-Funktionen bereitstellen. Klicken Sie auf die **[!UICONTROL Parameters]** Registerkarte und dann auf die **[!UICONTROL Deploy functions]** Schaltfläche.

   ![](assets/wf-external-account-functions.png)

You can define specific work tablespaces for the tables and for the index in the **[!UICONTROL Parameters]** tab.

## Herstellen einer temporären Verbindung {#creating-a-temporary-connection}

Sie können eine Verbindung zu einer externen Datenbank direkt aus den Workflow-Aktivitäten definieren. In diesem Fall befindet es sich in einer lokalen externen Datenbank, die für die Verwendung in einem aktuellen Workflow reserviert ist: sie wird nicht in den externen Konten gespeichert. Diese Art der pünktlichen Verbindung kann für verschiedene Aktivitäten des Workflows erstellt werden, insbesondere für die **[!UICONTROL Query]**, die **[!UICONTROL Data loading (RDBMS)]** Aktivität, die **[!UICONTROL Enrichment]** Aktivität oder die **[!UICONTROL Split]** Aktivität.

>[!CAUTION]
>
>Diese Art der Konfiguration wird nicht empfohlen, kann aber regelmäßig verwendet werden, um Daten abzurufen. Dennoch sollten Sie ein externes Konto gemäß der Beschreibung in Abschnitt [Erstellen einer geteilten Verbindung](#creating-a-shared-connection) erstellen.

Gehen Sie in der Abfrageaktivität zur Erstellung einer periodischen Verbindung zu einer externen Datenbank beispielsweise folgendermaßen vor:

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Add data...]** und wählen Sie die **[!UICONTROL External data]** Optionen aus.
1. Select the **[!UICONTROL Locally defining the data source]** option.

   ![](assets/wf_add_data_local_external_data.png)

1. Wählen Sie aus der Dropdown-Liste die Zieldatenbank-Engine aus. Geben Sie den Namen des Servers und die Authentifizierungsparameter ein.

   Geben Sie auch den Namen der externen Datenbank an.

   ![](assets/wf_add_data_local_external_data_param.png)

   Click the **[!UICONTROL Next]** button.

1. Wählen Sie die Tabelle aus, in der die Daten gespeichert sind.

   Sie können den Namen der Tabelle direkt in das entsprechende Feld eingeben oder auf das Bearbeiten-Symbol klicken, um eine Liste mit Datenbanktabellen zu öffnen.

   ![](assets/wf_add_data_local_external_data_select_table.png)

1. Klicken Sie auf die **[!UICONTROL Add]** Schaltfläche, um ein oder mehrere Abgleichungsfelder zwischen den externen Datenbankdaten und den Daten in der Adobe Campaign-Datenbank zu definieren. Die **[!UICONTROL Edit expression]** Symbole der **[!UICONTROL Remote field]** und **[!UICONTROL Local field]** gibt Ihnen Zugriff auf die Liste der Felder der einzelnen Tabellen.

   ![](assets/wf_add_data_local_external_data_join.png)

1. Spezifizieren Sie nötigenfalls eine Filterbedingung und den Datensortierungsmodus.
1. Select the additional data to be collected in the external database. To do this, double click on the fields(s) that you want to add to display them in the **[!UICONTROL Output columns]**.

   ![](assets/wf_add_data_local_external_data_select.png)

   Click **[!UICONTROL Finish]** to confirm this configuration.

## Sichere Verbindung {#secure-connection}

>[!NOTE]
>
>Eine sichere Verbindung ist nur für PostgreSQL verfügbar.

Sie können durch das Konfigurieren eines externen FDA-Kontos eine sichere Verbindung für den Zugriff auf eine externe Datenbank herstellen.

Schreiben Sie zu diesem Zweck &quot;**:ssl**&quot; hinter die Serveradresse und die Adresse des verwendeten Ports. Beispiel: **192.168.0.52:4501:ssl**.

Die Daten werden dadurch unter Verwendung des sicheren SSL-Protokolls gesendet.

## Ergänzende Konfigurationen {#additional-configurations}

Nötigenfalls können Sie das Schema zur Datenverarbeitung in einer externe Datenbank erstellen. Ebenso ermöglicht Ihnen Adobe Campaign das Definieren eines Mappings für die Daten in einer externen Tabelle. Diese Konfigurationen sind allgemeiner Art und werden nicht auf einzelne Workflows angewendet.

>[!NOTE]
>
>Weiterführende Informationen zur Erstellung von Schemata in Adobe Campaign und zur Definition eines neuen Daten-Mappings finden Sie auf [dieser Seite](../../configuration/using/about-schema-edition.md).
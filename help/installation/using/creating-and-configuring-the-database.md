---
product: campaign
title: Datenbank erstellen und konfigurieren
description: Datenbank erstellen und konfigurieren
feature: Installation, Instance Settings
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f40bab8c-5064-40d9-beed-101a9f22c094
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '1352'
ht-degree: 1%

---

# Datenbank erstellen und konfigurieren{#creating-and-configuring-the-database}

Beim Erstellen einer Datenbank bietet Adobe Campaign zwei verschiedene Optionen:

1. Datenbank erstellen oder wiederverwenden: Wählen Sie diese Option, wenn Sie eine neue Datenbank erstellen oder eine vorhandene wiederverwenden möchten. Siehe [&#x200B; 1: Erstellen/Recycling einer Datenbank](#case-1--creating-recycling-a-database).
1. Verwenden einer vorhandenen Datenbank: Wählen Sie diese Option, wenn bereits eine leere Datenbank von Ihrem Administrator erstellt wurde und Sie sie verwenden möchten, oder um die Struktur einer vorhandenen Datenbank zu erweitern. Siehe [Fall 2: Verwenden einer vorhandenen Datenbank](#case-2--using-an-existing-database).

Die Konfigurationsschritte werden nachfolgend beschrieben.

>[!CAUTION]
>
>Namen von Datenbanken, Benutzern und Schemata dürfen nicht mit einer Zahl beginnen oder Sonderzeichen enthalten.
>
>Nur die **interne** Kennung kann diese Vorgänge ausführen. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

## 1. Fall: Erstellen/Recycling einer Datenbank {#case-1--creating-recycling-a-database}

Die Schritte zum Erstellen einer Datenbank oder zum Recycling einer vorhandenen Datenbank werden nachfolgend beschrieben. Einige Konfigurationen hängen von der verwendeten Datenbank-Engine ab:

Die folgenden Schritte sind erforderlich:

* [Schritt 1: Auswählen der Datenbank-Engine](#step-1---selecting-the-database-engine),
* [Schritt 2: Herstellen einer Verbindung mit dem Server](#step-2---connecting-to-the-server),
* [Schritt 3: Verbindung und Merkmale der Datenbank](#step-3---connection-and-characteristics-of-the-database),
* [Schritt 4: Zu installierende &#x200B;](#step-4---packages-to-install),
* [Schritt 5 - Erstellungsschritte](#step-5---creation-steps),
* [Schritt 6: Erstellen der Datenbank](#step-6---creating-the-database).

### 1. Schritt - Datenbank-Engine auswählen {#step-1---selecting-the-database-engine}

Wählen Sie in der Dropdown-Liste die Datenbank-Engine aus.

![](assets/s_ncs_install_db_select_engine.png)

Die unterstützten Datenbanken sind in der Campaign-[&#x200B; (Kompatibilitätsmatrix) &#x200B;](../../rn/using/compatibility-matrix.md).

Identifizieren Sie den Server und wählen Sie den auszuführenden Vorgangstyp aus. In diesem Fall **[!UICONTROL Erstellen oder recyceln Sie eine Datenbank]**.

![](assets/s_ncs_install_db_oracle_creation01.png)

Je nach ausgewählter Datenbank-Engine können die Informationen zur Server-Identifizierung variieren.

* Für eine **Oracle**-Engine geben Sie den **TNS-Namen** ein, der für den Anwendungsserver definiert ist.
* Für eine **PostgreSQL**-Engine müssen Sie den auf dem Anwendungsserver definierten DNS-Namen (oder die IP-Adresse) angeben, um auf den Datenbankserver zugreifen zu können.
* Für eine **Microsoft SQL Server**-Engine müssen Sie Folgendes definieren: den auf dem Anwendungsserver definierten DNS-Namen (oder die IP-Adresse) für den Zugriff auf den Datenbankserver: **DNS** oder **DNS`\<instance>`** (Instanzmodus),

  >[!CAUTION]
  >
  > Ab 20.3 wird die Windows NT-Authentifizierung eingestellt. **[!UICONTROL SQL Server-Authentifizierung]** ist jetzt der einzige Authentifizierungsmodus, der für Microsoft SQL Server verfügbar ist. [Weitere Informationen](../../rn/using/deprecated-features.md)

  ![](assets/s_ncs_install_db_mssql_creation01.png)

### Schritt 2: Herstellen einer Verbindung zum Server {#step-2---connecting-to-the-server}

Definieren Sie im Fenster **[!UICONTROL Serverzugriff]** den Datenbankserverzugriff.

![](assets/s_ncs_install_db_oracle_creation02.png)

Geben Sie dazu den Namen und das Passwort eines **Administration-Systemkontos** ein, das für den Zugriff auf die Datenbanken berechtigt ist, d. h.:

* **system** für eine Oracle-Datenbank,
* **sa** für eine Microsoft SQL Server-Datenbank,
* **postgres** für eine PostgreSQL-Datenbank,

### Schritt 3: Verbindung und Merkmale der Datenbank {#step-3---connection-and-characteristics-of-the-database}

Mit dem folgenden Schritt können Sie die Einstellungen für die Anmeldung bei der Datenbank konfigurieren.

![](assets/s_ncs_install_db_oracle_creation03.png)

Sie müssen die folgenden Einstellungen definieren:

* Geben Sie den Namen der zu erstellenden Datenbank an.
* Geben Sie das Passwort des Kontos ein, das mit dieser Datenbank verknüpft ist.
* Gibt an, ob die Datenbank in Unicode vorliegen muss.

  Mit **[!UICONTROL Option]** Unicode-Datenbank) können Sie alle Zeichentypen unabhängig von der Sprache in Unicode speichern.

  >[!NOTE]
  >
  >Bei einer Oracle-Datenbank können Sie mit **[!UICONTROL Option]** Unicode-Speicher **Felder vom Typ NCLOB** und **NVARCHAR** verwenden.
  > 
  >Wenn Sie diese Option nicht auswählen, muss der Zeichensatz (Zeichensatz) der Oracle-Datenbank die Datenspeicherung in allen Sprachen ermöglichen (AL32UTF8 wird empfohlen).

* Wählen Sie eine Zeitzone für die Datenbank aus und geben Sie an, ob sie in UTC sein soll (falls verfügbar).

  Weitere Informationen hierzu finden Sie unter [Zeitzonenverwaltung](../../installation/using/time-zone-management.md).

### Schritt 4: Zu installierende Pakete {#step-4---packages-to-install}

Wählen Sie die Pakete aus, die Sie installieren möchten.

Informationen dazu, welche Lösungen und Optionen Sie installieren dürfen, z. B. „Interaction“ oder „Social Marketing“, finden Sie in Ihrem Lizenzvertrag.

![](assets/s_ncs_install_modules.png)

### 5. Schritt - Erstellungsschritte {#step-5---creation-steps}

Im Fenster **[!UICONTROL Erstellungsschritte]** können Sie das zur Erstellung der Tabellen verwendete SQL-Script anzeigen und bearbeiten.

![](assets/s_ncs_install_db_oracle_creation04.png)

* Für eine Oracle-, Microsoft SQL Server- oder PostgreSQL-Datenbank kann der Administrator auch die **Speicherparameter** definieren, die beim Erstellen von Datenbankobjekten verwendet werden sollen.

  Diese Parameter erhalten die exakten Tablespace-Namen (Warnung: Groß-/Kleinschreibung beachten). Sie werden jeweils im Knoten **[!UICONTROL Administration > Plattform > Optionen]** in den folgenden Optionen gespeichert (siehe [diesen Abschnitt](../../installation/using/configuring-campaign-options.md#database)):

   * **WdbcOptions_TableSpaceUser**: Benutzertabellen basierend auf einem Schema
   * **WdbcOptions_TableSpaceIndex**: Index der Benutzertabellen basierend auf einem Schema
   * **WdbcOptions_TableSpaceWork**: Arbeitstabellen ohne Schema
   * **WdbcOptions_TableSpaceWorkIndex**: Index der Arbeitstabellen ohne Schema

* Für eine Oracle-Datenbank muss der Adobe Campaign-Benutzer Zugriff auf die Oracle-Bibliotheken haben, in der Regel als Mitglied der **oinstall**-Gruppe.
* Mit **[!UICONTROL Option „Administratorkennwort festlegen oder ändern]** können Sie das mit dem Adobe Campaign-Benutzer verknüpfte Kennwort mit Administratorrechten eingeben.

  Aus Sicherheitsgründen wird empfohlen, ein Administratorkennwort für das Adobe Campaign-Konto zu definieren.

### Schritt 6: Erstellung der Datenbank {#step-6---creating-the-database}

In der letzten Phase des Assistenten können Sie die Datenbank erstellen. Klicken Sie **[!UICONTROL Start]** zur Bestätigung.

![](assets/s_ncs_install_db_oracle_creation06.png)

Nachdem die Datenbank erstellt wurde, können Sie erneut eine Verbindung herstellen, um die Konfiguration der Instanz abzuschließen.

Sie müssen jetzt den Bereitstellungsassistenten starten, um die Konfiguration der Instanz abzuschließen. Siehe [Bereitstellungsassistent](../../installation/using/deploying-an-instance.md#deployment-assistant).

Die Verbindungseinstellungen für die mit der Instanz verknüpfte Datenbank werden in der Datei gespeichert, **`/conf/config-<instance>.xml`** sich im Adobe Campaign-Installationsverzeichnis befindet.

Beispiel einer Microsoft SQL Server-Konfiguration in der base61-Datenbank, die mit dem „Campaign“-Konto mit seinem verschlüsselten Kennwort verknüpft ist:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

## 2. Fall: Verwenden einer vorhandenen Datenbank {#case-2--using-an-existing-database}

Sowohl die Datenbank als auch der Benutzer müssen vom Datenbankadministrator erstellt und die Zugriffsrechte korrekt konfiguriert worden sein.

Für eine Oracle-Datenbank sind die erforderlichen Mindestrechte beispielsweise: GRANT CONNECT, RESOURCE und UNLIMITED TABLESPACE.

Um eine vorhandene Datenbank zu verwenden, gehen Sie wie folgt vor:

* [Schritt 1: Auswählen des Datenbank-](#step-1---choosing-the-database-engine),
* [Schritt 2: Datenbankverbindungseinstellungen](#step-2---database-connection-settings),
* [Schritt 3: Zu installierende &#x200B;](#step-3---packages-to-install),
* [Schritt 4: Erstellungsschritte](#step-4---creation-steps),
* [Schritt 5: Erstellen der Datenbank](#step-5---creating-the-database).

### 1. Schritt - Datenbank-Engine auswählen {#step-1---choosing-the-database-engine}

Wählen Sie die Datenbank-Engine aus der Dropdown-Liste aus.

![](assets/s_ncs_install_db_select_engine.png)

Identifizieren Sie den Server und wählen Sie den gewünschten Vorgang aus. Wählen Sie in diesem Fall **[!UICONTROL Vorhandene Datenbank verwenden]**.

![](assets/s_ncs_install_db_oracle_exists_01.png)

Je nach ausgewählter Datenbank-Engine können die Informationen zur Server-Identifizierung variieren.

* Für eine **Oracle**-Engine geben Sie den **TNS-Namen** ein, der für den Anwendungsserver definiert ist.
* Für eine **PostgreSQL**-Engine müssen Sie den auf dem Anwendungsserver definierten DNS-Namen (oder die IP-Adresse) angeben, um auf den Datenbankserver zugreifen zu können.
* Für eine **Microsoft SQL Server**-Engine müssen Sie Folgendes definieren:

   1. den DNS-Namen (oder die IP-Adresse), der auf dem Anwendungsserver für den Zugriff auf den Datenbankserver definiert ist,
   1. Die Sicherheitsmethode für den Zugriff auf Microsoft SQL Server: **[!UICONTROL SQL Server-]** oder **[!UICONTROL Windows NT-Authentifizierung]**.

      ![](assets/s_ncs_install_db_mssql_exists_01.png)

### Schritt 2: Einstellungen der Datenbankverbindung {#step-2---database-connection-settings}

Definieren Sie **[!UICONTROL Fenster]** Datenbank“ die Datenbankverbindungseinstellungen.

![](assets/s_ncs_install_db_oracle_exists_02.png)

Sie müssen die folgenden Einstellungen definieren:

* Geben Sie den Namen der zu verwendenden Datenbank ein.
* Geben Sie den Namen und das Kennwort des Kontos ein, das mit dieser Datenbank verknüpft ist.

  >[!NOTE]
  >
  >Stellen Sie sicher, dass sowohl der Schemaname als auch der Benutzername übereinstimmen. Es wird empfohlen, die Datenbank über die Client-Konsole der Campaign-Konsole zu erstellen.
  >Für eine Oracle-Datenbank müssen Sie den Kontonamen nicht eingeben.

* Gibt an, ob die Datenbank Unicode sein soll oder nicht.

### Schritt 3: Zu installierende Pakete {#step-3---packages-to-install}

Wählen Sie die Pakete aus, die Sie installieren möchten.

Informationen dazu, welche Lösungen und Optionen Sie installieren dürfen, z. B. „Interaction“ oder „Leads“, finden Sie in Ihrem Lizenzvertrag.

![](assets/s_ncs_install_modules.png)

### 4. Schritt - Erstellungsschritte {#step-4---creation-steps}

Im Fenster **[!UICONTROL Erstellungsschritte]** können Sie das zur Erstellung der Tabellen verwendete SQL-Script anzeigen und bearbeiten.

![](assets/s_ncs_install_db_oracle_creation04.png)

* Für Oracle-, Microsoft SQL Server- oder PostgreSQL-Datenbanken kann der Administrator die **Speicherparameter** definieren, die beim Erstellen von Datenbankobjekten verwendet werden sollen.
* Für eine Oracle-Datenbank muss der Adobe Campaign-Benutzer Zugriff auf die Oracle-Bibliotheken haben, in der Regel als Mitglied der **oinstall**-Gruppe.
* Mit **[!UICONTROL Option „Administratorkennwort festlegen oder ändern]** können Sie das mit dem Adobe Campaign-Benutzer verknüpfte Kennwort mit Administratorrechten eingeben.

  Aus Sicherheitsgründen wird empfohlen, ein Administratorkennwort für das Adobe Campaign-Konto zu definieren.

### Schritt 5: Datenbank erstellen {#step-5---creating-the-database}

In der letzten Phase des Assistenten können Sie die Datenbank erstellen. Klicken Sie **[!UICONTROL Start]** zur Bestätigung.

![](assets/s_ncs_install_db_oracle_creation06.png)

Sobald die Datenbankerstellung abgeschlossen ist, können Sie die Verbindung wiederherstellen, um die Instanzkonfiguration abzuschließen.

Sie müssen jetzt den Bereitstellungsassistenten starten, um die Konfiguration der Instanz abzuschließen. Siehe [Bereitstellungsassistent](../../installation/using/deploying-an-instance.md#deployment-assistant).

Die Verbindungseinstellungen für die mit der Instanz verknüpfte Datenbank werden in der Datei gespeichert, **`/conf/config-<instance>.xml`** sich im Adobe Campaign-Installationsverzeichnis befindet.

Beispiel einer Microsoft SQL Server-Konfiguration in der base61-Datenbank, die mit dem „Campaign“-Konto mit seinem verschlüsselten Kennwort verknüpft ist:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

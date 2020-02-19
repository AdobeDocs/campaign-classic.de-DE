---
title: Datenbank erstellen und konfigurieren
seo-title: Datenbank erstellen und konfigurieren
description: Datenbank erstellen und konfigurieren
seo-description: null
page-status-flag: never-activated
uuid: e5143d55-61fa-416a-80db-c29a0caf9a3e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: 7dd8a6a5-7cca-4e92-8226-1b9e450dfaf9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4869eb41f942a89c48bc213913c44b70ae777bfc

---


# Creating and configuring the database{#creating-and-configuring-the-database}

Wenn Sie eine Datenbank erstellen, bietet Adobe Campaign zwei verschiedene Optionen:

1. Erstellen oder Recycling einer Datenbank: Wählen Sie diese Option, wenn Sie eine neue Datenbank erstellen oder eine vorhandene erneut verwenden möchten. Siehe [Fall 1: Erstellen/Recycling einer Datenbank](#case-1--creating-recycling-a-database).
1. Verwenden einer vorhandenen Datenbank: Wählen Sie diese Option, wenn Ihr Administrator bereits eine leere Datenbank erstellt hat und Sie diese verwenden möchten. oder um die Struktur einer vorhandenen Datenbank zu erweitern. Siehe [Fall 2: Verwenden einer vorhandenen Datenbank](#case-2--using-an-existing-database).

Die Konfigurationsschritte werden nachfolgend beschrieben.

>[!CAUTION]
>
>Die Namen von Datenbanken, Benutzern und Schemas dürfen nicht mit einer Zahl beginnen oder Sonderzeichen enthalten.
>
>Nur der **interne** Bezeichner kann diese Vorgänge ausführen. For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

##  Fall 1: Erstellen/Recycling einer Datenbank {#case-1--creating-recycling-a-database}

Die Schritte zum Erstellen einer Datenbank oder zum Recycling einer vorhandenen Datenbank werden nachfolgend beschrieben. Einige Konfigurationen hängen von der verwendeten Datenbank-Engine ab:

Es handelt sich um die folgenden Schritte:

* [Schritt 1: Auswählen der Datenbank-Engine](#step-1---selecting-the-database-engine),
* [Schritt 2: Verbindung zum Server](#step-2---connecting-to-the-server)herstellen,
* [Schritt 3 - Verbindung und Merkmale der Datenbank](#step-3---connection-and-characteristics-of-the-database),
* [Schritt 4 - Zu installierende](#step-4---packages-to-install)Pakete,
* [Schritt 5 - Erstellungsschritte](#step-5---creation-steps),
* [Schritt 6 - Erstellen der Datenbank](#step-6---creating-the-database).

### Schritt 1: Auswählen der Datenbank-Engine {#step-1---selecting-the-database-engine}

Wählen Sie die Datenbank-Engine unter den in der Dropdownliste aufgeführten aus.

![](assets/s_ncs_install_db_select_engine.png)

Unterstützte Datenbanken werden im Abschnitt [Kompatibilitätsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)dargestellt.

Identifizieren Sie den Server und wählen Sie den Typ des Vorgangs aus, der ausgeführt werden soll. In diesem Fall **[!UICONTROL Create or recycle a database]**.

![](assets/s_ncs_install_db_oracle_creation01.png)

Je nach ausgewählter Datenbank-Engine können die Serverkennungsinformationen variieren.

* Geben Sie für eine **Oracle** -Engine den für den Anwendungsserver definierten **TNS-Namen** ein.
* Bei einer **PostgreSQL** - oder **DB2** -Engine müssen Sie den DNS-Namen (oder die IP-Adresse) angeben, der auf dem Anwendungsserver definiert ist, um auf den Datenbankserver zuzugreifen.
* Für eine **Microsoft SQL Server** -Engine müssen Sie Folgendes definieren:

   1. der auf dem Anwendungsserver für den Zugriff auf den Datenbankserver definierte DNS-Name (oder IP-Adresse): **DNS** oder **DNS\ `<instance>`** (Instanzmodus),
   1. die Authentifizierungsmethode für den Zugriff auf Microsoft SQL Server: **[!UICONTROL SQL Server authentication]** oder **[!UICONTROL Windows NT authentication]**.

      ![](assets/s_ncs_install_db_mssql_creation01.png)

### Schritt 2: Verbindung zum Server herstellen {#step-2---connecting-to-the-server}

Definieren Sie im **[!UICONTROL Server access]** Fenster den Datenbankserverzugriff.

![](assets/s_ncs_install_db_oracle_creation02.png)

Geben Sie dazu den Namen und das Kennwort eines Kontos **des** Administrationssystems ein, das Zugriff auf die Datenbanken hat, d. h.:

* **System** für eine Oracle-Datenbank,
* **sa** für eine Microsoft SQL Server-Datenbank,
* **Postings** für eine PostgreSQL-Datenbank,
* **db2inst1** für eine DB2-Datenbank.

### Schritt 3: Verbindung und Merkmale der Datenbank {#step-3---connection-and-characteristics-of-the-database}

Im folgenden Schritt können Sie die Einstellungen für die Anmeldung bei der Datenbank konfigurieren.

![](assets/s_ncs_install_db_oracle_creation03.png)

Sie müssen die folgenden Einstellungen definieren:

* Geben Sie den Namen der zu erstellenden Datenbank an.

   >[!NOTE]
   >
   >Bei einer DB2-Datenbank darf der Name der Datenbank 8 Zeichen nicht überschreiten.

* Geben Sie das Kennwort des mit dieser Datenbank verknüpften Kontos ein.
* Geben Sie an, ob sich die Datenbank in Unicode befinden muss.

   Mit der **[!UICONTROL Unicode database]** Option können Sie alle Zeichentypen unabhängig von der Sprache in Unicode speichern.

   >[!NOTE]
   >
   >Bei einer Oracle-Datenbank können Sie mit der **[!UICONTROL Unicode storage]** Option **NCLOB** - und **NVARCHAR** -Typfelder verwenden.
   > 
   >Wenn Sie diese Option nicht auswählen, muss der Zeichensatz (Zeichensatz) der Oracle-Datenbank die Datenspeicherung in allen Sprachen aktivieren (AL32UTF8 wird empfohlen).

* Wählen Sie eine Zeitzone für die Datenbank und geben Sie an, ob die Datenbank in UTC (falls verfügbar) enthalten sein soll.

   Weitere Informationen finden Sie unter [Zeitzonenverwaltung](../../installation/using/time-zone-management.md).

### Schritt 4: Zu installierende Pakete {#step-4---packages-to-install}

Wählen Sie die Pakete aus, die Sie installieren möchten.

Überprüfen Sie anhand Ihrer Lizenzvereinbarung, welche Lösungen und Optionen Sie installieren dürfen, z. B. &quot;Interaktion&quot;oder &quot;Social Marketing&quot;.

![](assets/s_ncs_install_modules.png)

### Schritt 5: Erstellungsschritte {#step-5---creation-steps}

Im **[!UICONTROL Creation steps]** Fenster können Sie das SQL-Skript, das zum Erstellen der Tabellen verwendet wird, anzeigen und bearbeiten.

![](assets/s_ncs_install_db_oracle_creation04.png)

* Bei einer Oracle-, Microsoft SQL Server- oder PostgreSQL-Datenbank kann der Administrator auch die **Speicherparameter** definieren, die beim Erstellen von Datenbankobjekten verwendet werden sollen.

   Diese Parameter erhalten die genauen Tablespace-Namen (Warnung: Groß-/Kleinschreibung beachten). Sie werden in den folgenden Optionen im **[!UICONTROL Administration > Platform > Options]** Knoten gespeichert:

   * **WdbcOptions_TableSpaceUser**: Benutzertabellen basierend auf einem Schema
   * **WdbcOptions_TableSpaceIndex**: Index der Benutzertabellen basierend auf einem Schema
   * **WdbcOptions_TableSpaceWork**: Arbeitstabellen ohne Schema
   * **WdbcOptions_TableSpaceWorkIndex**: Index der Arbeitstabellen ohne Schema

* Bei einer Oracle-Datenbank muss der Adobe Campaign-Benutzer Zugriff auf die Oracle-Bibliotheken haben, normalerweise als Mitglied der **oinstall** -Gruppe.
* Mit dieser **[!UICONTROL Set or change the administrator password]** Option können Sie das mit dem Adobe Campaign-Operator verknüpfte Kennwort mit Administratorrechten eingeben.

   Es wird empfohlen, aus Sicherheitsgründen ein Adobe Campaign-Kontoverwaltungskennwort zu definieren.

### Schritt 6: Erstellen der Datenbank {#step-6---creating-the-database}

Im letzten Schritt des Assistenten können Sie die Datenbank erstellen. Klicken Sie **[!UICONTROL Start]** zur Bestätigung.

![](assets/s_ncs_install_db_oracle_creation06.png)

Nachdem die Datenbank erstellt wurde, können Sie eine erneute Verbindung herstellen, um die Instanzkonfiguration abzuschließen.

Sie müssen jetzt den Bereitstellungsassistenten starten, um die Konfiguration der Instanz abzuschließen. Siehe [Bereitstellungsassistent](../../installation/using/deploying-an-instance.md#deployment-wizard).

Die Verbindungseinstellungen für die mit der Instanz verknüpfte Datenbank werden in der Datei gespeichert, die sich im Installationsverzeichnis von Adobe Campaign befindet. **`/conf/config-<instance>.xml`**

Beispiel einer Microsoft SQL Server-Konfiguration auf der Basis der Base61-Datenbank, die mit dem &quot;campaign&quot;-Konto mit dem verschlüsselten Kennwort verknüpft ist:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

##  Fall 2: Verwenden einer vorhandenen Datenbank {#case-2--using-an-existing-database}

Die Datenbank sowie der Benutzer müssen vom Datenbankadministrator erstellt und die Zugriffsrechte korrekt konfiguriert worden sein.

Für eine Oracle-Datenbank sind beispielsweise die folgenden Mindestrechte erforderlich: GEWÄHREN SIE VERBINDUNG, RESSOURCE UND UNLIMITED TABLESPACE.

Um eine vorhandene Datenbank zu verwenden, gehen Sie wie folgt vor:

* [Schritt 1: Auswählen der Datenbank-Engine](#step-1---choosing-the-database-engine),
* [Schritt 2: Einstellungen](#step-2---database-connection-settings)der Datenbankverbindung
* [Schritt 3 - Zu installierende](#step-3---packages-to-install)Pakete,
* [Schritt 4 - Erstellungsschritte](#step-4---creation-steps),
* [Schritt 5 - Erstellen der Datenbank](#step-5---creating-the-database).

### Schritt 1: Auswählen der Datenbank-Engine {#step-1---choosing-the-database-engine}

Wählen Sie die Datenbank-Engine aus der Dropdownliste.

![](assets/s_ncs_install_db_select_engine.png)

Identifizieren Sie den Server und wählen Sie die Art des Vorgangs, den Sie ausführen möchten. In diesem Fall **[!UICONTROL Use an existing database]**.

![](assets/s_ncs_install_db_oracle_exists_01.png)

Je nach ausgewählter Datenbank-Engine können die Serverkennungsinformationen variieren.

* Geben Sie für eine **Oracle** -Engine den für den Anwendungsserver definierten **TNS-Namen** ein.
* Bei einer **PostgreSQL** - oder **DB2** -Engine müssen Sie den DNS-Namen (oder die IP-Adresse) angeben, der auf dem Anwendungsserver definiert ist, um auf den Datenbankserver zuzugreifen.
* Für eine **Microsoft SQL Server** -Engine müssen Sie Folgendes definieren:

   1. der auf dem Anwendungsserver für den Zugriff auf den Datenbankserver definierte DNS-Name (oder IP-Adresse),
   1. die Sicherheitsmethode für den Zugriff auf Microsoft SQL Server: **[!UICONTROL SQL Server authentication]** oder **[!UICONTROL Windows NT authentication]**.

      ![](assets/s_ncs_install_db_mssql_exists_01.png)

### Schritt 2: Einstellungen für die Datenbankverbindung {#step-2---database-connection-settings}

Legen Sie im **[!UICONTROL Database]** Fenster die Einstellungen für die Datenbankverbindung fest.

![](assets/s_ncs_install_db_oracle_exists_02.png)

Sie müssen die folgenden Einstellungen definieren:

* Geben Sie den Namen der zu verwendenden Datenbank ein,
* Geben Sie den Namen und das Kennwort des mit dieser Datenbank verknüpften Kontos ein,

   >[!NOTE]
   >
   >Bei einer Oracle-Datenbank müssen Sie nicht den Kontonamen eingeben.

* Geben Sie an, ob die Datenbank Unicode sein soll oder nicht.

### Schritt 3: Zu installierende Pakete {#step-3---packages-to-install}

Wählen Sie die Pakete aus, die Sie installieren möchten.

Überprüfen Sie anhand Ihrer Lizenzvereinbarung, welche Lösungen und Optionen Sie installieren dürfen, z. B. &quot;Interaktion&quot;oder &quot;Interessenten&quot;.

![](assets/s_ncs_install_modules.png)

### Schritt 4: Erstellungsschritte {#step-4---creation-steps}

Im **[!UICONTROL Creation steps]** Fenster können Sie das SQL-Skript, das zum Erstellen der Tabellen verwendet wird, anzeigen und bearbeiten.

![](assets/s_ncs_install_db_oracle_creation04.png)

* Bei Oracle-, Microsoft SQL Server- oder PostgreSQL-Datenbanken kann der Administrator die **Speicherparameter** definieren, die beim Erstellen von Datenbankobjekten verwendet werden sollen.
* Bei einer Oracle-Datenbank muss der Adobe Campaign-Benutzer Zugriff auf die Oracle-Bibliotheken haben, normalerweise als Mitglied der **oinstall** -Gruppe.
* Mit dieser **[!UICONTROL Set or change the administrator password]** Option können Sie das mit dem Adobe Campaign-Operator verknüpfte Kennwort mit Administratorrechten eingeben.

   Es wird empfohlen, aus Sicherheitsgründen ein Adobe Campaign-Kontoverwaltungskennwort zu definieren.

### Step 5 - Creating the database {#step-5---creating-the-database}

Im letzten Schritt des Assistenten können Sie die Datenbank erstellen. Klicken Sie **[!UICONTROL Start]** zur Bestätigung.

![](assets/s_ncs_install_db_oracle_creation06.png)

Nach Abschluss der Datenbankerstellung können Sie die Verbindung zum Abschluss der Instanzkonfiguration wiederherstellen.

Sie müssen jetzt den Bereitstellungsassistenten starten, um die Konfiguration der Instanz abzuschließen. Siehe [Bereitstellungsassistent](../../installation/using/deploying-an-instance.md#deployment-wizard).

Die Verbindungseinstellungen für die mit der Instanz verknüpfte Datenbank werden in der Datei gespeichert, die sich im Installationsverzeichnis von Adobe Campaign befindet. **`/conf/config-<instance>.xml`**

Beispiel einer Microsoft SQL Server-Konfiguration auf der Basis der Base61-Datenbank, die mit dem &quot;campaign&quot;-Konto mit dem verschlüsselten Kennwort verknüpft ist:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```


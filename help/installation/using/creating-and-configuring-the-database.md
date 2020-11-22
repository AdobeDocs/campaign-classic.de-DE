---
solution: Campaign Classic
product: campaign
title: Erstellen und Konfigurieren der Vorlagen
description: Erstellen und Konfigurieren der Vorlagen
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1342'
ht-degree: 1%

---


# Erstellen und Konfigurieren der Vorlagen{#creating-and-configuring-the-database}

Wenn Sie eine Datenbank erstellen, bietet Adobe Campaign zwei verschiedene Optionen:

1. Erstellen oder Recycling einer Datenbank: Wählen Sie diese Option, wenn Sie eine neue Datenbank erstellen oder eine vorhandene erneut verwenden möchten. Siehe [Fall 1: Erstellen/Recycling einer Datenbank](#case-1--creating-recycling-a-database).
1. Verwenden einer vorhandenen Datenbank: Wählen Sie diese Option, wenn Ihr Administrator bereits eine leere Datenbank erstellt hat und Sie diese verwenden möchten. oder um die Struktur einer vorhandenen Datenbank zu erweitern. Siehe [Fall 2: Verwenden einer vorhandenen Datenbank](#case-2--using-an-existing-database).

Die Konfigurationsschritte werden nachfolgend beschrieben.

>[!CAUTION]
>
>Die Namen von Datenbanken, Benutzern und Schemas dürfen nicht mit einer Nummer oder Sonderzeichen Beginn werden.
>
>Diese Vorgänge können nur vom **internen** Bezeichner ausgeführt werden. For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

## Fall 1: Erstellen/Recycling einer Datenbank {#case-1--creating-recycling-a-database}

Die Schritte zum Erstellen einer Datenbank oder zum Recycling einer vorhandenen Datenbank werden nachfolgend beschrieben. Einige Konfigurationen hängen von der verwendeten Datenbank-Engine ab:

Es handelt sich dabei um die folgenden Schritte:

* [Schritt 1: Auswählen der Datenbank-Engine](#step-1---selecting-the-database-engine),
* [Schritt 2: Verbindung zum Server](#step-2---connecting-to-the-server)herstellen,
* [Schritt 3 - Verbindung und Merkmale der Datenbank](#step-3---connection-and-characteristics-of-the-database),
* [Schritt 4 - Zu installierende](#step-4---packages-to-install)Pakete,
* [Schritt 5 - Erstellungsschritte](#step-5---creation-steps),
* [Schritt 6 - Erstellen der Datenbank](#step-6---creating-the-database).

### Schritt 1: Auswählen der Datenbank-Engine {#step-1---selecting-the-database-engine}

Wählen Sie die Datenbank-Engine unter den in der Dropdown-Liste aufgeführten aus.

![](assets/s_ncs_install_db_select_engine.png)

Unterstützte Datenbanken werden in der [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md)der Kampagne aufgeführt.

Identifizieren Sie den Server und wählen Sie den Typ des Vorgangs aus, der ausgeführt werden soll. In diesem Fall **[!UICONTROL erstellen oder recyceln Sie eine Datenbank]**.

![](assets/s_ncs_install_db_oracle_creation01.png)

Je nach ausgewählter Datenbank-Engine können die Serverkennungsinformationen variieren.

* Geben Sie für eine **Oracle** -Engine den für den Anwendungsserver definierten **TNS-Namen** ein.
* Bei einer **PostgreSQL** - oder **DB2** -Engine müssen Sie den DNS-Namen (oder die IP-Adresse) angeben, der auf dem Anwendungsserver definiert ist, um auf den Datenbankserver zuzugreifen.
* Für eine **Microsoft SQL Server** -Engine müssen Sie Folgendes definieren: der auf dem Anwendungsserver für den Zugriff auf den Datenbankserver definierte DNS-Name (oder IP-Adresse): **DNS** oder **DNS`\<instance>`** (Instanzmodus),

   >[!CAUTION]
   >
   > Ab 20.3 wird die Windows NT-Authentifizierung deaktiviert. **[!UICONTROL Die SQL Server-Authentifizierung]** ist jetzt der einzige für Microsoft SQL Server verfügbare Authentifizierungsmodus. [Mehr dazu](../../rn/using/deprecated-features.md)

   ![](assets/s_ncs_install_db_mssql_creation01.png)

### Schritt 2: Verbindung zum Server herstellen {#step-2---connecting-to-the-server}

Definieren Sie im Fenster **[!UICONTROL Serverzugriff]** den Datenbankserverzugriff.

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

* Geben Sie das Kennwort des Kontos ein, das mit dieser Datenbank verknüpft ist.
* Geben Sie an, ob sich die Datenbank in Unicode befinden muss.

   Mit der **[!UICONTROL Unicode-Datenbankoption]** können Sie alle Zeichentypen unabhängig von der Sprache in Unicode speichern.

   >[!NOTE]
   >
   >Bei einer Oracle-Datenbank können Sie mit der **[!UICONTROL Option &quot;Unicode-Datenspeicherung]** &quot;die Felder **NCLOB** und **NVARCHAR** verwenden.
   > 
   >Wenn Sie diese Option nicht auswählen, muss der Zeichensatz (Zeichensatz) der Oracle-Datenbank die Datenspeicherung der Daten in allen Sprachen aktivieren (AL32UTF8 wird empfohlen).

* Wählen Sie eine Zeitzone für die Datenbank und geben Sie an, ob die Datenbank in UTC (falls verfügbar) enthalten sein soll.

   For more on this, refer to [Time zone management](../../installation/using/time-zone-management.md).

### Schritt 4: Zu installierende Pakete {#step-4---packages-to-install}

Wählen Sie die Pakete aus, die Sie installieren möchten.

Überprüfen Sie anhand Ihrer Lizenzvereinbarung, welche Lösungen und Optionen Sie installieren dürfen, z. B. &quot;Interaktion&quot;oder &quot;Social Marketing&quot;.

![](assets/s_ncs_install_modules.png)

### Schritt 5: Erstellungsschritte {#step-5---creation-steps}

Im Fenster &quot; **[!UICONTROL Erstellungsschritte]** &quot;können Sie das SQL-Skript, das zum Erstellen der Tabellen verwendet wird, anzeigen und bearbeiten.

![](assets/s_ncs_install_db_oracle_creation04.png)

* Bei einer Oracle-, Microsoft SQL Server- oder PostgreSQL-Datenbank kann der Administrator auch die **Datenspeicherung-Parameter** definieren, die beim Erstellen von Datenbankobjekten verwendet werden.

   Diese Parameter erhalten die genauen Tablespace-Namen (Warnung: Groß-/Kleinschreibung beachten). Sie werden jeweils im Knoten **[!UICONTROL Administration > Plattform > Optionen]** in den folgenden Optionen gespeichert (siehe [diesen Abschnitt](../../installation/using/configuring-campaign-options.md#database)):

   * **WdbcOptions_TableSpaceUser**: Benutzertabellen basierend auf einem Schema
   * **WdbcOptions_TableSpaceIndex**: Index der Benutzertabellen basierend auf einem Schema
   * **WdbcOptions_TableSpaceWork**: Arbeitstabellen ohne Schema
   * **WdbcOptions_TableSpaceWorkIndex**: Index der Arbeitstabellen ohne Schema

* Bei einer Oracle-Datenbank muss der Adobe Campaign-Benutzer Zugriff auf die Oracle-Bibliotheken haben, normalerweise als Mitglied der **Installationsgruppe** .
* Mit der Option **[!UICONTROL Administratorkennwort]** festlegen oder ändern können Sie das mit dem Adobe Campaign-Operator verknüpfte Kennwort mit Administratorrechten eingeben.

   Es wird empfohlen, aus Sicherheitsgründen ein Passwort für den Adobe Campaign-Kontoadministrator zu definieren.

### Schritt 6: Erstellen der Datenbank {#step-6---creating-the-database}

Im letzten Schritt des Assistenten können Sie die Datenbank erstellen. Click **[!UICONTROL Start]** to confirm.

![](assets/s_ncs_install_db_oracle_creation06.png)

Nachdem die Datenbank erstellt wurde, können Sie eine erneute Verbindung herstellen, um die Instanzkonfiguration abzuschließen.

Sie müssen jetzt den Bereitstellungsassistenten Beginn ausführen, um die Konfiguration der Instanz abzuschließen. Weitere Informationen finden Sie im [Bereitstellungsassistenten](../../installation/using/deploying-an-instance.md#deployment-wizard).

Die Verbindungseinstellungen für die mit der Instanz verknüpfte Datenbank werden in der Datei gespeichert, die im Installationsverzeichnis des Adobe Campaigns **`/conf/config-<instance>.xml`** enthalten ist.

Beispiel für eine Microsoft SQL Server-Konfiguration auf der Base61-Datenbank, die mit dem verschlüsselten Kennwort des Kontos &quot;Kampagne&quot;verknüpft ist:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

## Fall 2: Verwenden einer vorhandenen Datenbank {#case-2--using-an-existing-database}

Die Datenbank sowie der Benutzer müssen vom Datenbankadministrator erstellt und die Zugriffsrechte korrekt konfiguriert worden sein.

Für eine Oracle-Datenbank sind beispielsweise die folgenden Mindestrechte erforderlich: ZUSCHUSS CONNECT, RESOURCE UND UNBEGRENZTER TABLESPACE.

Um eine vorhandene Datenbank zu verwenden, gehen Sie wie folgt vor:

* [Schritt 1: Auswählen der Datenbank-Engine](#step-1---choosing-the-database-engine),
* [Schritt 2: Einstellungen](#step-2---database-connection-settings)der Datenbankverbindung,
* [Schritt 3 - Zu installierende](#step-3---packages-to-install)Pakete,
* [Schritt 4 - Erstellungsschritte](#step-4---creation-steps),
* [Schritt 5 - Erstellen der Datenbank](#step-5---creating-the-database).

### Schritt 1: Auswählen der Datenbank-Engine {#step-1---choosing-the-database-engine}

Wählen Sie die Datenbank-Engine aus der Dropdown-Liste.

![](assets/s_ncs_install_db_select_engine.png)

Identifizieren Sie den Server und wählen Sie die Art des Vorgangs, den Sie ausführen möchten. In diesem Fall **[!UICONTROL verwenden Sie eine vorhandene Datenbank]**.

![](assets/s_ncs_install_db_oracle_exists_01.png)

Je nach ausgewählter Datenbank-Engine können die Serverkennungsinformationen variieren.

* Geben Sie für eine **Oracle** -Engine den für den Anwendungsserver definierten **TNS-Namen** ein.
* Bei einer **PostgreSQL** - oder **DB2** -Engine müssen Sie den DNS-Namen (oder die IP-Adresse) angeben, der auf dem Anwendungsserver definiert ist, um auf den Datenbankserver zuzugreifen.
* Für eine **Microsoft SQL Server** -Engine müssen Sie Folgendes definieren:

   1. der auf dem Anwendungsserver für den Zugriff auf den Datenbankserver definierte DNS-Name (oder IP-Adresse),
   1. die Sicherheitsmethode für den Zugriff auf Microsoft SQL Server: **[!UICONTROL SQL Server-Authentifizierung]** oder **[!UICONTROL Windows NT-Authentifizierung]**.

      ![](assets/s_ncs_install_db_mssql_exists_01.png)

### Schritt 2: Einstellungen für die Datenbankverbindung {#step-2---database-connection-settings}

Legen Sie im Fenster &quot; **[!UICONTROL Datenbank]** &quot;die Einstellungen für die Datenbankverbindung fest.

![](assets/s_ncs_install_db_oracle_exists_02.png)

Sie müssen die folgenden Einstellungen definieren:

* Geben Sie den Namen der zu verwendenden Datenbank ein,
* Geben Sie den Namen und das Kennwort des mit dieser Datenbank verknüpften Kontos ein,

   >[!NOTE]
   >
   >Achten Sie darauf, dass sowohl der Name des Schemas als auch der Benutzername übereinstimmen. Es wird empfohlen, eine Datenbank über den Kampagne Console-Client zu erstellen.
   >Bei einer Oracle-Datenbank müssen Sie keinen Kontonamen eingeben.

* Geben Sie an, ob die Datenbank Unicode sein soll oder nicht.

### Schritt 3: Zu installierende Pakete {#step-3---packages-to-install}

Wählen Sie die Pakete aus, die Sie installieren möchten.

Überprüfen Sie anhand Ihrer Lizenzvereinbarung, welche Lösungen und Optionen Sie installieren dürfen, z. B. &quot;Interaktion&quot;oder &quot;Interessenten&quot;.

![](assets/s_ncs_install_modules.png)

### Schritt 4: Erstellungsschritte {#step-4---creation-steps}

Im Fenster &quot; **[!UICONTROL Erstellungsschritte]** &quot;können Sie das SQL-Skript, das zum Erstellen der Tabellen verwendet wird, anzeigen und bearbeiten.

![](assets/s_ncs_install_db_oracle_creation04.png)

* Bei Oracle-, Microsoft SQL Server- oder PostgreSQL-Datenbanken kann der Administrator die **Datenspeicherung-Parameter** definieren, die beim Erstellen von Datenbankobjekten verwendet werden.
* Bei einer Oracle-Datenbank muss der Adobe Campaign-Benutzer Zugriff auf die Oracle-Bibliotheken haben, normalerweise als Mitglied der **Installationsgruppe** .
* Mit der Option **[!UICONTROL Administratorkennwort]** festlegen oder ändern können Sie das mit dem Adobe Campaign-Operator verknüpfte Kennwort mit Administratorrechten eingeben.

   Es wird empfohlen, aus Sicherheitsgründen ein Passwort für den Adobe Campaign-Kontoadministrator zu definieren.

### Step 5 - Creating the database {#step-5---creating-the-database}

Im letzten Schritt des Assistenten können Sie die Datenbank erstellen. Click **[!UICONTROL Start]** to confirm.

![](assets/s_ncs_install_db_oracle_creation06.png)

Nach Abschluss der Datenbankerstellung können Sie die Verbindung zum Abschluss der Instanzkonfiguration wiederherstellen.

Sie müssen jetzt den Bereitstellungsassistenten Beginn ausführen, um die Konfiguration der Instanz abzuschließen. Weitere Informationen finden Sie im [Bereitstellungsassistenten](../../installation/using/deploying-an-instance.md#deployment-wizard).

Die Verbindungseinstellungen für die mit der Instanz verknüpfte Datenbank werden in der Datei gespeichert, die im Installationsverzeichnis des Adobe Campaigns **`/conf/config-<instance>.xml`** enthalten ist.

Beispiel für eine Microsoft SQL Server-Konfiguration auf der Base61-Datenbank, die mit dem verschlüsselten Kennwort des Kontos &quot;Kampagne&quot;verknüpft ist:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```


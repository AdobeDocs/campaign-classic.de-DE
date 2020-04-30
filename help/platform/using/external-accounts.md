---
title: Externe Konten
seo-title: Externe Konten
description: Externe Konten
seo-description: null
page-status-flag: never-activated
uuid: e06e7a36-b449-4ab0-a4f6-fa82dbb8de11
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: administration-basics
discoiquuid: da60b9ca-4b51-4bff-affc-2b12c576973a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 090ec1f9b30c8548075493757b814a8bb40bea30

---


# Externe Konten{#external-accounts}

Externe Konten sind Konfigurationen, die den Zugriff auf Server außerhalb von Adobe Campaign erlauben. Mit diesen externen Konten ist es möglich, in Campaign-Workflows auf Daten zuzugreifen und diese zu verwalten.

Die folgenden externen Konten können eingerichtet werden:

* [Externes Routing-Konto](#routing-external-account)
* [Externes FTP-Konto](#ftp-external-account)
* [Externes Konto für eine externe Datenbank](#external-database-external-account)
* [Externes Web Analytics-Konto](#web-analytics-external-account)
* [Externes Facebook Connect-Konto](#facebook-connect-external-account)
* [Externes Konto der Ausführungsinstanz](#execution-instance-external-account)
* [Externes Adobe Experience Cloud-Konto](#adobe-experience-cloud-external-account)
* [Externes SFTP-Konto](#sftp-external-account)
* [Externes Adobe-Experience-Manager-Konto](#adobe-experience-manager-external-account)
* [Externes Amazon Simple Storage Service-Konto (S3)](#amazon-simple-storage-service--s3--external-account)
* [externes Azure-Konto](#azure-external-account)
* [Externes Hadoop-Konto](#hadoop-external-account)
* [Externes Microsoft Dynamics CRM-Konto](#microsoft-dynamics-crm-external-account)
* [Externes Oracle On Demand-Konto](#oracle-on-demand-external-account)
* [Externes Salesforce CRM-Konto](#salesforce-crm-external-account)

## Externes Konto erstellen {#creating-an-external-account}

Adobe Campaign enthält eine Reihe vordefinierter externer Konten. Sie können aber auch Ihre eigenen externen Konten erstellen, um eine Verbindung mit externen Systemen wie FTP-Servern zum Zweck des Dateitransfers herzustellen.

Externe Konten werden von technischen Prozessen, wie technischen Workflows oder Kampagnen-Workflows, verwendet. Bei der Einrichtung eines Dateitransfers in einem Workflow oder bei einem Datenaustausch mit einer anderen Anwendung (Adobe Target, Experience Manager etc.) müssen Sie ein externes Konto auswählen.

1. From the **[!UICONTROL Explorer]**, unfold the **[!UICONTROL Administration]** menu.
1. Blenden Sie das **[!UICONTROL Platform]** Menü aus und klicken Sie auf **[!UICONTROL External accounts]**.

   ![](assets/ext_account_1.png)

1. Click the **[!UICONTROL New]** button.

   ![](assets/ext_account_2.png)

1. Geben Sie ein **[!UICONTROL Label]** und ein **[!UICONTROL Internal Name]**. Beide werden bei der Auswahl von Externen Konti in Workflows verwendet.
1. Check **[!UICONTROL Enabled]** if you want your connection to be enabled.
1. Select your external account **[!UICONTROL Type]** which one you want to create.
1. Konfigurieren Sie den Zugriff auf das Konto, indem Sie die Anmeldeinformationen entsprechend dem gewählten externen Kontotyp angeben.

   Die nötigen Informationen werden normalerweise vom Anbieter des Servers bereitgestellt, mit dem Sie eine Verbindung herstellen möchten.

1. Klicks **[!UICONTROL Save]**.

Das externe Konto wird angelegt und in die Liste der externen Konten aufgenommen. Es steht jetzt für Ihre Daten- und Dateitransfers oder Routing-Konfigurationen in Workflow-Aktivitäten und Versandeigenschaften bereit.

## Externes Konto für Bounce Messages {#bounce-mails-external-account}

Das externe Konto **Bounce Messages** gibt das externe POP3-Konto an, das für die Verbindung mit dem E-Mail-Dienst verwendet werden soll. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../workflow/using/inbound-emails.md).

Alle Server, die für den POP3-Zugriff konfiguriert sind, können für den Empfang von Antwortsendungen verwendet werden.

![](assets/ext_account_6.png)

To configure the **[!UICONTROL Bounce mails (defaultPopAccount)]** external account:

* **[!UICONTROL Server]**

   URL des POP3-Servers

* **[!UICONTROL Port]**

   Nummer des POP3-Verbindungsports. Standardmäßig ist dies der Port 110.

* **[!UICONTROL Account]**

   Name des Benutzers.

* **[!UICONTROL Password]**

   Passwort des Benutzerkontos.

* **[!UICONTROL Encryption]**

   Type of chosen encryption between **[!UICONTROL By default]**, **[!UICONTROL POP3 + STARTTLS]**, **[!UICONTROL POP3]** or **[!UICONTROL POP3S]**.

## Externes Routing-Konto {#routing-external-account}

Mit dem externen **[!UICONTROL Routing]**-Konto können Sie jeden in Adobe Campaign verfügbaren Kanal abhängig von den installierten Packages konfigurieren.

![](assets/ext_account_7.png)

Die folgenden Kanäle können konfiguriert werden:

* [Email](../../installation/using/deploying-an-instance.md#email-channel-parameters)
* [Mobiltelefon (SMS)](../../delivery/using/sms-channel.md#activating-an-external-account).
* [Phone](../../delivery/using/other-channels.md)
* [Briefpost](../../delivery/using/about-direct-mail-channel.md)
* [Agentur](../../delivery/using/other-channels.md)
* [Facebook](../../social/using/publishing-on-facebook-walls.md#delegating-write-access-to-adobe-campaign)
* [Twitter](../../social/using/configuring-publishing-on-twitter.md)
* [iOS-Kanal](../../delivery/using/configuring-the-mobile-application.md#configuring-the-mobile-application-ios)
* [Android-Kanal](../../delivery/using/configuring-the-mobile-application.md#configuring-the-mobile-application-android)

## Externes FTP-Konto {#ftp-external-account}

Mit dem externen FTP-Konto können Sie den Zugriff auf einen Server außerhalb von Adobe Campaign konfigurieren und testen. Um Verbindungen mit externen Systemen wie dem FTP-Server 898, der für Dateiübertragungen verwendet wird, einzurichten, können Sie eigene externe Konten erstellen. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../workflow/using/file-transfer.md).

Geben Sie dazu in diesem externen Konto die Adresse und die Zugangsdaten für die Verbindungsherstellung zum FTP-Server an.

![](assets/ext_account_8.png)

* **[!UICONTROL Server]**

   Name des FTP-Servers

* **[!UICONTROL Port]**

   Nummer des FTP-Verbindungsports. Standardmäßig ist dies Port 21.

* **[!UICONTROL Account]**

   Name des Benutzers.

* **[!UICONTROL Password]**

   Passwort des Benutzerkontos.

* **[!UICONTROL Encryption]**

   Type of chosen encryption between **[!UICONTROL None]** or **[!UICONTROL SSL]**.

Informationen zu diesen Zugangsdaten finden Sie auf dieser [Seite](https://help.dreamhost.com/hc/en-us/articles/115000675027-FTP-overview-and-credentials).

## Externes Konto für eine externe Datenbank {#external-database-external-account}

Adobe Campaign bietet mehrere Connectors, mit denen Sie mit externen Anwendungen kommunizieren und sich mit Datenbank-Engines verbinden können.

![](assets/ext_account_11.png)

Die folgenden Verbindungstypen können konfiguriert werden:

* Oracle. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../platform/using/specific-configuration-database.md#configure-access-to-oracle).
* Netezza. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../platform/using/specific-configuration-database.md#configure-access-to-netezza).
* SAP HANA. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../platform/using/specific-configuration-database.md#configure-access-to-sap-hana).
* InfiniDB
* Microsoft SQL Server
* AsterData
* PostgreSQL
* Teradata
* DB2
* Amazon Redshift
* ODBC (Sybase ASE, Sybase IQ)
* HTTP-Weiterleitung auf Remote-Datenbank

### Schneeflocken-Externe Konto {#snowflake-external-account}

The **Snowflake** external account allows you to connect your Campaign instance to your Snowflake external database. For more information on how to configure Campaign Classic with Snowflake, refer to this [page](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake).

Um dieses externe Konto für die gemeinsame Verwendung mit Adobe Campaign zu konfigurieren, müssen Sie die folgenden Informationen eingeben:

* **[!UICONTROL Server]**

       URL des Snowflake-Servers.
   
* **[!UICONTROL Account]**

       Name des Benutzers.
   
* **[!UICONTROL Password]**

       Passwort des Benutzerkontos.
   
* **[!UICONTROL Database]**

       Name der Datenbank.
   
![](assets/snowflake.png)

### Externes Teradata-Konto {#teradata-external-account}

Über das externe **Teradata**-Konto können Sie Ihre Kampagneninstanz mit Ihrer externen Teradata-Datenbank verbinden. Weiterführende Informationen zum Konfigurieren von Campaign Classic mit Teradata finden Sie auf dieser [Seite](https://helpx.adobe.com/de/campaign/kb/campaign_fda_teradata.html) oder in diesem [Abschnitt](../../platform/using/specific-configuration-database.md#configure-access-to-teradata).

![](assets/ext_account_19.png)

Um dieses externe Konto für die gemeinsame Verwendung mit Adobe Campaign zu konfigurieren, müssen Sie die folgenden Informationen eingeben:

* **[!UICONTROL Type]**

   Choose the **[!UICONTROL Teradata]** type.

* **[!UICONTROL Server]**

   URL oder Name Ihres Teradata-Servers

* **[!UICONTROL Account]**

   Name des Kontos, mit dem auf die Teradata-Datenbank zugegriffen wird

* **[!UICONTROL Password]**

   Passwort, das für die Verbindung zur Teradata-Datenbank verwendet wird

* **[!UICONTROL Database]**

   Dieses Feld kann leer gelassen werden.

* **[!UICONTROL Options]**

   Optionen, die über Teradata übermittelt werden sollen.

* **[!UICONTROL Timezone]**

   Die in Teradata eingestellte Zeitzone.

![](assets/ext_account_20.png)

Wenn sich mehrere Adobe Campaign-Benutzer mit demselben externen FDA-Teradata-Konto verbinden, können Sie im Tab **[!UICONTROL Query banding]** einen Satz von Schlüssel/Wert-Paaren für eine Sitzung festlegen.

Jedes Mal, wenn ein Campaign-Benutzer eine Abfrage in der Teradata-Datenbank ausführt, sendet Adobe Campaign Metadaten, die aus einer Liste von Schlüsseln bestehen, die diesem Benutzer zugeordnet sind. Diese Daten können dann von Teradata-Administratoren für Prüfzwecke oder zur Verwaltung von Zugriffsrechten verwendet werden.

Check the **[!UICONTROL Active]** box to activate this feature

Im **[!UICONTROL Default]** Feld können Sie ein Standardband für die Abfrage eingeben, das verwendet wird, wenn ein Benutzer über kein zugewiesenes Abfragen-Band verfügt. Wenn dieses Feld leer gelassen wird, können Benutzer ohne Abfrage keine Teradata verwenden.

Mit dem **[!UICONTROL Users]** Feld können Sie für jeden Benutzer ein Abfrage-Band angeben. Sie können so viele Schlüssel/Wert-Paare hinzufügen, wie Sie benötigen, z. B. priority=1;workload=high. Wenn dem Benutzer kein Abfragen-Band zugewiesen ist, wird das **[!UICONTROL Default]** Feld angewendet.

Weitere Informationen zu **[!UICONTROL Query banding]** finden Sie im [Teradata-Handbuch](https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw).

## Externes Web Analytics-Konto {#web-analytics-external-account}

Mit dem **[!UICONTROL Web Analytics (Adobe Analytics - Data connector)]** Externe Konto können Sie Daten aus Adobe Analytics in Segmentform an Adobe Campaign weiterleiten. Umgekehrt sendet es Indikatoren und Attribute von E-Mail-Kampagnen, die von Adobe Campaign an Adobe Analytics - Data Connector gesendet werden.

![](assets/ext_account_10.png)

Für dieses externe Konto muss die Berechnungsformel für getrackte URLs angereichert und die Verbindung zwischen den beiden Lösungen genehmigt werden. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../platform/using/adobe-analytics-data-connector.md#step-2--create-the-external-account-in-campaign).

## Externes Facebook Connect-Konto {#facebook-connect-external-account}

Mit dem externen Konto **[!UICONTROL Facebook Connect]** können Sie in Facebook-Anwendungen personalisierte Inhalte anzeigen. Dadurch wird es einfacher, über dieses soziale Netzwerk potenzielle Kunden zu gewinnen.

Für jede Facebook-Anwendung müssen Sie ein externes **[!UICONTROL Facebook Connect]**-Konto erstellen. For more on this, refer to [page](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

![](assets/ext_account_12.png)

* **[!UICONTROL Hosting mode]**

   Hosting-Modus der Anwendung zwischen **[!UICONTROL hosted by a partner]** oder **[!UICONTROL hosted by this instance]**.

* **[!UICONTROL Application ID]**

   App-ID Ihrer Facebook-Anwendung

* **[!UICONTROL Application secret]**

   App-Geheimnis Ihrer Facebook-Anwendung.

Wenn Sie den Modus &quot;Auf dieser Instanz gehostet&quot; gewählt haben, muss die Sichere Canvas-URL in das Feld **Facebook Web Games (https)** auf Facebook eingefügt werden.

Informationen zu diesen Zugangsdaten finden Sie auf dieser [Seite](https://developers.facebook.com/docs/facebook-login/access-tokens).

## Externes Konto der Ausführungsinstanz {#execution-instance-external-account}

Wenn Sie eine aufgegliederte Architektur haben, müssen Sie die mit der Kontrollinstanz verbundenen Ausführungsinstanzen spezifizieren und miteinander verbinden. Transaktionsnachrichtenvorlagen werden in der Ausführungsinstanz bereitgestellt.

![](assets/ext_account_13.png)

* **[!UICONTROL URL]**

   URL des Servers, auf dem die Ausführungsinstanz installiert ist.

* **[!UICONTROL Account]**

   Name des Kontos, muss mit dem Message Center Agent übereinstimmen, der im Benutzerordner definiert ist

* **[!UICONTROL Password]**

   Passwort des Kontos, wie es im Benutzerordner definiert ist

Weiterführende Informationen zur Konfiguration finden Sie auf dieser [Seite](../../message-center/using/creating-a-shared-connection.md#control-instance).

## Externes Adobe Experience Cloud-Konto {#adobe-experience-cloud-external-account}

To connect to the Adobe Campaign console using an Adobe ID, you must configure the **[!UICONTROL Adobe Experience Cloud (MAC)]** external account.

![](assets/ext_account_9.png)

* **[!UICONTROL IMS server]**

   URL Ihres IMS-Servers. Stellen Sie sicher, dass sowohl Staging- als auch Produktionsinstanzen auf den gleichen IMS-Produktionsendpunkt verweisen.

* **[!UICONTROL IMS scope]**

   Der hier definierte Umfang muss eine Teilmenge der vom IMS bereitgestellten Perimeter sein.

* **[!UICONTROL IMS client identifier]**

   Die ID Ihres IMS-Client

* **[!UICONTROL IMS client secret]**

   Ihr IMS-Client-Geheimnisses.

* **[!UICONTROL Callback server]**

   Zugriff-URL Ihrer Adobe Campaign-Instanz.

* **[!UICONTROL IMS organization ID]**

   ID Ihrer IMS-Organisation. Um Ihre Organisations-ID zu finden, gehen Sie auf diese [Seite](https://marketing.adobe.com/resources/help/de_DE/mcloud/faq.html) (**Wo finde ich meine IMS-Organisations-ID?**).

* **[!UICONTROL Association mask]**

   Syntax, die es ermöglicht, Konfigurationsnamen im Enterprise Dashboard mit den Gruppen in Adobe Campaign zu synchronisieren

* **[!UICONTROL Server]**

   URL Ihrer Adobe Experience Cloud-Instanz

* **[!UICONTROL Tenant]**

   Name Ihres Adobe Experience Cloud-Mandanten

Weiterführende Informationen zur Konfiguration finden Sie auf dieser [Seite](../../integrations/using/configuring-ims.md).

## Externes SFTP-Konto  {#sftp-external-account}

Mit dem externen SFTP-Konto können Sie den Zugriff auf einen Server außerhalb von Adobe Campaign konfigurieren und testen. Um Verbindungen mit externen Systemen wie dem SFTP-Server einzurichten, der für Dateiübertragungen verwendet wird, können Sie eigene externe Konten erstellen. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../workflow/using/file-transfer.md).

![](assets/ext_account_4.png)

* **[!UICONTROL Server]**

   URL des SFTP-Servers

* **[!UICONTROL Port]**

   Port-Nummer der FTP-Verbindung. Der Standard-Port ist 22.

* **[!UICONTROL Account]**

   Kontoname, der für die Verbindung zum SFTP-Server verwendet wird

* **[!UICONTROL Password]**

   Passwort, das für die Verbindung zum SFTP-Server verwendet wird

## Externes Adobe-Experience-Manager-Konto {#adobe-experience-manager-external-account}

The **[!UICONTROL AEM (AEM instance)]** external account allows you to manage the content of your email deliveries as well as your forms directly in Adobe Experience Manager.

![](assets/ext_account_5.png)

* **[!UICONTROL Server]**

   URL des Adobe-Experience-Manager-Servers

* **[!UICONTROL Port]**

   Kontoname, der für die Verbindung mit der Adobe Experience Manager-Authoring-Instanz verwendet wird

* **[!UICONTROL Password]**

   Passwort, das für die Verbindung mit der Adobe Experience Manager-Authoring-Instanz verwendet wird

Weiterführende Informationen hierzu finden Sie in diesem [Abschnitt](../../integrations/using/about-adobe-experience-manager.md).

## Externes Amazon Simple Storage Service-Konto (S3){#amazon-simple-storage-service--s3--external-account}

Der Amazon Simple Storage Service (S3) Connector kann zum Import oder Export von Daten in Adobe Campaign verwendet werden. Es kann in einer Workflow-Aktivität eingerichtet werden. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../workflow/using/file-transfer.md).

![](assets/ext_account_3.png)

Zum Einrichten dieses neuen externen Kontos benötigen Sie die folgenden Informationen:

* **[!UICONTROL AWS S3 Account Server]**

   Die URL Ihres Servers sollte folgendermaßen ausgefüllt werden:

   ```
   <S3bucket name>.s3.amazonaws.com/<s3object path>
   ```

* **[!UICONTROL AWS access key ID]**

   Informationen darüber, wo Sie Ihre Kennung des AWS-Zugangsschlüssels finden, erfahren Sie auf dieser [Seite](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) .

* **[!UICONTROL Secret access key to AWS]**

   Informationen darüber, wo Sie Ihren geheimen AWS-Zugangsschlüssel finden, erfahren Sie auf dieser [Seite](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/).

* **[!UICONTROL AWS Region]**

   Weiterführende Informationen zur AWS-Region finden Sie auf dieser [Seite](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/).

* The **[!UICONTROL Use server side encryption]** checkbox allows you to store your file in S3 encrypted mode.

Informationen darüber, wo Sie die Kennung des Zugriffsschlüssels und den geheimen Zugriffsschlüssel finden, erfahren Sie im [Handbuch](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) der Amazon-Webdienste .

## externes Azure-Konto {#azure-external-account}

Mit dem externen **[!UICONTROL Azure]**-Konto können Sie über Adobe Campaign auf eine gemeinsam genutzte externe Datenbank zugreifen, vorausgesetzt die Verbindung ist aktiv.

![](assets/ext_account_15.png)

* **[!UICONTROL Server]**

   URL des Azure-Servers

* **[!UICONTROL Encryption]**

   Type of chosen encryption between **[!UICONTROL None]** or **[!UICONTROL SSL]**.

* **[!UICONTROL Access key]**

   Informationen darüber, wo Sie Ihren Zugangsschlüssel finden, erfahren Sie auf dieser [Seite](https://docs.microsoft.com/de-de/azure/storage/common/storage-account-manage) (Abschnitt **Zugangsschlüssel anzeigen und kopieren**).

## Externes Hadoop-Konto {#hadoop-external-account}

Mit dem externen **[!UICONTROL Hadoop]**-Konto können Sie über Adobe Campaign auf eine gemeinsam genutzte externe Datenbank zugreifen, vorausgesetzt die Verbindung ist aktiv. Weiterführende Informationen zur Konfiguration des Zugriffs auf Hadoop finden Sie in [diesem Abschnitt](../../platform/using/specific-configuration-database.md#configure-access-to-hadoop).

![](assets/ext_account_16.png)

* **[!UICONTROL Server]**

   URL des Hadoop-Servers

* **[!UICONTROL User account name]**

   Name des Kontos, mit dem auf die Hadoop zugegriffen wird

## Externes Microsoft Dynamics CRM-Konto {#microsoft-dynamics-crm-external-account}

Das externe **[!UICONTROL Microsoft Dynamics CRM]**-Konto ermöglicht den Import und Export von Microsoft Dynamics-Daten in Adobe Campaign.

Wie Sie den Microsoft Dynamics Connector zur Verwendung mit Adobe Campaign konfigurieren müssen, hängt von Ihrem Bereitstellungstyp ab.
Bei den Bereitstellungstypen **[!UICONTROL On-premise]** und **[!UICONTROL Office 365]** müssen Sie folgende Details angeben:

![](assets/ext_account_21.png)

* **[!UICONTROL Account]**

   Konto, mit dem die Anmeldung bei Microsoft CRM erfolgt

* **[!UICONTROL Server]**

   URL Ihres Microsoft CRM-Servers

* **[!UICONTROL Password]**

   Passwort, mit dem die Anmeldung bei Microsoft CRM erfolgt

* **[!UICONTROL Company name]** für die Bereitstellung vor Ort und Office 365

   Der Name Ihres Unternehmens.

* **[!UICONTROL Organization name]** für lokale Bereitstellung

   Name Ihrer Organisation
Organization name which can be found in the Developers resources dashboard in Microsoft Dynamics, **[!UICONTROL Unique Name]** field.

* **[!UICONTROL CRM version]** für lokale Anwendungen

   Version des CRM zwischen **[!UICONTROL Dynamics CRM 2007]**, **[!UICONTROL Dynamics CRM 2015]** oder **[!UICONTROL Dynamics CRM 2016]**.

With **[!UICONTROL Web API]** deployment type and **[!UICONTROL Password credentials]** authentication, you need to provide the following details:

![](assets/ext_account_14.png)

* **[!UICONTROL Account]**

   Konto, mit dem die Anmeldung bei Microsoft CRM erfolgt

* **[!UICONTROL Server]**

   URL Ihres Microsoft CRM-Servers

* **[!UICONTROL Client identifier]**

   Client-ID, die von Microsoft Azurblaus Management Portal in der **[!UICONTROL Update your code]** Kategorie, **[!UICONTROL Client ID]** Feld gefunden werden kann.

* **[!UICONTROL CRM version]**

   Version des CRM zwischen **[!UICONTROL Dynamics CRM 2007]**, **[!UICONTROL Dynamics CRM 2015]** oder **[!UICONTROL Dynamics CRM 2016]**.

With **[!UICONTROL Web API]** deployment type and **[!UICONTROL Certificate]** authentication, you need to provide the following details:

![](assets/ext_account_22.png)

* **[!UICONTROL Server]**

   URL Ihres Microsoft CRM-Servers

* **[!UICONTROL Private Key (Base64 encoded)]**

   Privater Schlüssel mit Base64-Kodierung

* **[!UICONTROL Custom Key identifier]**

* **[!UICONTROL Key ID]**

* **[!UICONTROL Client identifier]**

   Client-ID, die von Microsoft Azurblaus Management Portal in der **[!UICONTROL Update your code]** Kategorie, **[!UICONTROL Client ID]** Feld gefunden werden kann.

* **[!UICONTROL CRM version]**

   Version des CRM zwischen **[!UICONTROL Dynamics CRM 2007]**, **[!UICONTROL Dynamics CRM 2015]** oder **[!UICONTROL Dynamics CRM 2016]**.

Weiterführende Informationen zur Konfiguration finden Sie auf dieser [Seite](../../platform/using/crm-connectors.md#example-for-microsoft-dynamics).

## Externes Oracle On Demand-Konto {#oracle-on-demand-external-account}

Das externe **[!UICONTROL Oracle on demand]**-Konto ermöglicht den Import und Export von Oracle-Daten in Adobe Campaign.

![](assets/ext_account_18.png)

Um dieses externe Konto für die gemeinsame Verwendung mit Adobe Campaign zu konfigurieren, müssen Sie die folgenden Informationen eingeben:

* **[!UICONTROL Account]**

   Konto, mit dem die Anmeldung bei Oracle CRM On Demand erfolgt

* **[!UICONTROL Server]**

   URL Ihres Oracle CRM On Demand-Servers

* **[!UICONTROL Password]**

   Passwort, mit dem die Anmeldung bei Oracle CRM On Demand erfolgt

Weiterführende Informationen zur Konfiguration finden Sie auf dieser [Seite](../../platform/using/crm-connectors.md#example-for-oracle-on-demand).

## Externes Salesforce CRM-Konto {#salesforce-crm-external-account}

Das externe **[!UICONTROL Salesforce CRM]**-Konto ermöglicht den Import und Export von Salesforce-Daten in Adobe Campaign.

![](assets/ext_account_17.png)

Um dieses externe Konto für die gemeinsame Verwendung mit Adobe Campaign zu konfigurieren, müssen Sie die folgenden Informationen eingeben:

* **[!UICONTROL Account]**

   Konto, mit dem die Anmeldung bei Salesforce CRM erfolgt

* **[!UICONTROL Password]**

   Passwort, mit dem die Anmeldung bei Salesforce CRM erfolgt

* **[!UICONTROL Client identifier]**

   Informationen darüber, wo Sie Ihre Client-Kennung finden, erfahren Sie auf dieser [Seite](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL Security token]**

   Informationen darüber, wo Sie Ihr Security-Token finden, erfahren Sie auf dieser [Seite](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL API version]**

   Version of the API between **[!UICONTROL Version 37]**, **[!UICONTROL Version 21]** or **[!UICONTROL Version 15]**.

Für dieses externe Konto müssen Sie Salesforce CRM mit dem Konfigurationsassistenten konfigurieren.

Weiterführende Informationen zur Konfiguration finden Sie auf dieser [Seite](../../platform/using/crm-connectors.md#example-for-salesforce-com).

---
product: campaign
title: Externe Konten
description: Erfahren Sie, wie Sie externe Konten erstellen
feature: Installation, Application Settings, External Account
audience: platform
content-type: reference
topic-tags: administration-basics
exl-id: 4a17d5e8-c73f-42e7-b641-0fee6a52c5c0
source-git-commit: 8180f77c2824f9b54ae3c924b1cc45532675cf85
workflow-type: tm+mt
source-wordcount: '1981'
ht-degree: 64%

---

# Externe Konten{#external-accounts}

Adobe Campaign enthält eine Reihe vordefinierter externer Konten. Um Verbindungen zu externen Systemen einzurichten, können Sie neue externe Konten erstellen.

Externe Konten werden von technischen Prozessen, wie technischen Workflows oder Kampagnen-Workflows, verwendet. Beispiel: Bei der Einrichtung eines Dateitransfers in einem Workflow oder bei einem Datenaustausch mit einem anderen Programm (Adobe Target, Experience Manager usw.) müssen Sie ein externes Konto auswählen.

## Erstellen eines externen Kontos {#creating-an-external-account}

Gehen Sie wie folgt vor, um ein neues externes Konto zu erstellen.  Detaillierte Einstellungen hängen vom Typ des externen Kontos ab.

1. Wählen Sie in Campaign **[!UICONTROL Explorer]** die Option **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Plattform]** &#39;>&#39; **[!UICONTROL Externe Konten]** aus.

   ![](assets/ext_account_1.png)

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Neu]**.

   ![](assets/ext_account_2.png)

1. Geben Sie einen **[!UICONTROL Titel]** und einen **[!UICONTROL internen Namen]** ein.
1. Wählen Sie den **[!UICONTROL Typ]** des externen Kontos aus, den Sie erstellen möchten.
1. Konfigurieren Sie den Zugriff auf das Konto, indem Sie die Anmeldedaten entsprechend dem gewählten externen Kontotyp angeben.

   Die nötigen Informationen werden normalerweise vom Anbieter des Servers bereitgestellt, mit dem Sie eine Verbindung herstellen möchten.

1. Aktivieren Sie die Option **[!UICONTROL Aktiviert]** , um die Verbindung zu aktivieren.
1. Klicken Sie auf **[!UICONTROL Speichern]**.

Das externe Konto wird erstellt und der Liste der externen Konten hinzugefügt.

## Kampagnenspezifische externe Konten

### Bounce-E-Mails {#bounce-mails-external-account}

Das externe Konto **Bounce Messages** gibt das externe POP3-Konto an, das für die Verbindung mit dem E-Mail-Service verwendet werden soll. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../workflow/using/inbound-emails.md).

Alle Server, die für den POP3-Zugriff konfiguriert sind, können für den Empfang von Antwortsendungen verwendet werden.

![](assets/ext_account_6.png)

Um das externe Konto für **[!UICONTROL Bounce-Messages (defaultPopAccount)]** zu konfigurieren, benötigen Sie folgende Informationen:

* **[!UICONTROL Server]**

  URL des POP3-Servers

* **[!UICONTROL Port]**

  Nummer des POP3-Verbindungsports. Standardmäßig ist dies der Port 110.

* **[!UICONTROL Konto]**

  Name des Benutzers.

* **[!UICONTROL Passwort]**

  Passwort des Benutzerkontos.

* **[!UICONTROL Verschlüsselung]**

  Typ der gewählten Verschlüsselung: **[!UICONTROL Standardmäßig]**, **[!UICONTROL POP3 + STARTTLS]**, **[!UICONTROL POP3]** oder **[!UICONTROL POP3S]**.

* **[!UICONTROL Funktion]**

  Eingehende E-Mail- oder SOAP-Router

>[!IMPORTANT]
>
>Bevor Sie Ihr externes POP3-Konto mit Microsoft OAuth 2.0 konfigurieren, müssen Sie Ihre Anwendung zunächst im Azure-Portal registrieren. Weitere Informationen hierzu finden Sie auf [dieser Seite](https://docs.microsoft.com/de-de/azure/active-directory/develop/quickstart-register-app).

Um ein externes POP3 mit **Microsoft OAuth 2.0** zu konfigurieren, aktivieren Sie die Option **[!UICONTROL Microsoft OAuth 2.0]** und füllen Sie die folgenden Felder aus:

* **[!UICONTROL Azure-Mandant]**

  Eine Azure ID (oder Verzeichnis-ID bzw. Mandanten-ID) finden Sie in der Dropdown-Liste **Grundlagen** der Anwendungsübersicht im Azure-Portal.

* **[!UICONTROL Azure-Client-ID]**

  Client-ID (oder Anwendungs (Client)-ID) finden Sie in der Dropdown-Liste **Grundlagen** der Anwendungsübersicht im Azure-Portal.

* **[!UICONTROL Azure Client secret]**

  Die Client-Geheimnis-ID finden Sie in der Spalte **Client-Geheimnisse** im Menü **Zertifikate und Geheimnisse** Ihrer Anwendung im Azure-Portal.

* **[!UICONTROL Azure Redirect URL]**

  Die Umleitungs-URL finden Sie im Menü **Authentifizierung** Ihrer Anwendung im Azure-Portal. Sie sollte mit der folgenden Syntax enden: `nl/jsp/oauth.jsp`, z. B. `https://redirect.adobe.net/nl/jsp/oauth.jsp`.

Internet-Zugriff ist für die Einrichtung und die Verwendung der Schaltfläche **[!UICONTROL Verbindung testen]** in der Clientkonsole erforderlich. Nach der Einrichtung kann der InMail-Prozess mit Microsoft-Servern ohne Internet kommunizieren.

Nachdem Sie Ihre unterschiedlichen Anmeldedaten eingegeben haben, können Sie auf **[!UICONTROL Verbindung einrichten]** klicken, um die Konfiguration Ihres externen Kontos abzuschließen.

### Routing{#routing-external-account}

Mit dem externen **[!UICONTROL Routing]**-Konto können Sie jeden in Adobe Campaign verfügbaren Kanal abhängig von den installierten Packages konfigurieren.

![](assets/ext_account_7.png)

Die folgenden Kanäle können konfiguriert werden:

* [E-Mail](#email-routing-external-account)
* [Mobiltelefon (SMS)](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)
* [Telefon](../../delivery/using/communication-channels.md#other-channels)
* [Briefpost](../../delivery/using/about-direct-mail-channel.md)
* [Agentur](../../delivery/using/communication-channels.md#other-channels)
* [X (früher bekannt als Twitter)](../../social/using/about-social-marketing.md)
* [iOS-Kanal](../../delivery/using/configuring-the-mobile-application.md)
* [Android-Kanal](../../delivery/using/configuring-the-mobile-application-android.md)

### E-Mail-Routing {#email-routing-external-account}

Das externe Konto E-Mail-Routing wird standardmäßig bereitgestellt und ist an Ihre Konfiguration angepasst.

Als On-Premise-/Hybrid-Kunde können Sie neue Routing-externe Konten erstellen oder Parameter aktualisieren, wie unten beschrieben. Diese Konfiguration ist erfahrenen Benutzern vorbehalten und kann sich auf Ihre Zustellbarkeit auswirken. Wenden Sie sich bei Fragen an den Kundendienst von Adobe oder Ihren Adobe-Support-Mitarbeiter.

* Sie können einen Routing-Typ vom Typ **Mid-Sourcing**, **Externes** oder **Bulk** für den Versand verwenden.

* Bei den Versandmodi **Bulk** und **Mid-Sourcing** können Sie Ihre Branding-Parameter auf der Registerkarte **Branding** angeben. Diese Parameter werden verwendet, um die [Standardparameter](../../installation/using/deploying-an-instance.md#email-channel-parameters) für die URL der Mirrorseite **und die** Fehleradresse **mit markenspezifischen Einstellungen zu überschreiben.**

  ![](assets/ext-account-branding.png)

* Informationen zum Konfigurieren eines externen Mid-Sourcing-Kontos finden Sie in [diesem Abschnitt](mid-sourcing-server.md)

### Ausführungsinstanz  {#execution-instance-external-account}

Im Falle einer verteilten Architektur müssen in der Kontrollinstanz die ihr zugeordneten Ausführungsinstanzen angegeben und mit dieser verbunden werden. Transaktionsnachrichten-Vorlagen werden in der Ausführungsinstanz bereitgestellt.

![](assets/ext_account_13.png)

* **[!UICONTROL URL]**

  URL des Servers, auf dem die Ausführungsinstanz installiert ist.

* **[!UICONTROL Konto]**

  Name des Kontos, muss mit dem Message Center Agent übereinstimmen, der im Benutzerordner definiert ist

* **[!UICONTROL Passwort]**

  Passwort des Kontos, wie es im Benutzerordner definiert ist

Weiterführende Informationen zur Konfiguration finden Sie auf dieser [Seite](../../message-center/using/configuring-instances.md#control-instance).

## Zugriff auf externe Systemkonten

### FTP {#ftp-external-account}

Mit dem externen FTP-Konto können Sie den Zugriff auf einen Server außerhalb von Adobe Campaign konfigurieren und testen. Um Verbindungen mit externen Systemen wie FTP-Servern 898, die für Dateiübertragungen verwendet werden, einzurichten, können Sie eigene externe Konten erstellen. Weiterführende Informationen hierzu finden Sie auf [dieser Seite](../../workflow/using/file-transfer.md).

Geben Sie dazu in diesem externen Konto die Adresse und die Anmeldedaten für die Verbindungsherstellung zum FTP-Server an.

![](assets/ext_account_8.png)

* **[!UICONTROL Server]**

  Name des FTP-Servers

* **[!UICONTROL Port]**

  Nummer des FTP-Verbindungsports. Standardmäßig ist dies Port 21.

* **[!UICONTROL Konto]**

  Name des Benutzers.

* **[!UICONTROL Passwort]**

  Passwort des Benutzerkontos.

* **[!UICONTROL Verschlüsselung]**

  Typ der gewählten Verschlüsselung: **[!UICONTROL Keine]** oder **[!UICONTROL SSL]**.

Informationen zu diesen Anmeldedaten finden Sie auf dieser [Seite](https://help.dreamhost.com/hc/en-us/articles/115000675027-FTP-overview-and-credentials).

### SFTP {#sftp-external-account}

Mit dem externen SFTP-Konto können Sie den Zugriff auf einen Server außerhalb von Adobe Campaign konfigurieren und testen. Um Verbindungen mit externen Systemen wie SFTP einzurichten, das für Dateiübertragungen verwendet wird, können Sie eigene externe Konten erstellen. Weiterführende Informationen hierzu finden Sie auf [dieser Seite](../../workflow/using/file-transfer.md).

![](assets/ext_account_4.png)

* **[!UICONTROL Server]**

  URL des SFTP-Servers

* **[!UICONTROL Port]**

  Port-Nummer der FTP-Verbindung. Der Standard-Port ist 22.

* **[!UICONTROL Konto]**

  Kontoname, der für die Verbindung zum SFTP-Server verwendet wird

* **[!UICONTROL Passwort]**

  Passwort, das für die Verbindung zum SFTP-Server verwendet wird

<!--To add SSH keys on Windows:

1. Create the **HOME** environment variable with value set as the installation directory.

2. Add your private key to the `/$HOME/.ssh/id_rsa` folder.

3. Restart the Adobe Campaign services.
-->

### Externe Datenbank (FDA) {#external-database-external-account}

Verwenden Sie das externe Konto vom Typ **Externe Datenbank** , um eine Verbindung zu einer externen Datenbank herzustellen. Weitere Informationen zur Option „Federated Data Access“ (FDA) finden Sie in [diesem Abschnitt](../../installation/using/about-fda.md).

Externe Datenbanken, die mit Campaign kompatibel sind, sind in der [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md) aufgeführt.

![](assets/ext_account_11.png)

Die Konfigurationseinstellungen für externe Konten hängen von der Datenbank-Engine ab. Weitere Informationen finden Sie in den folgenden Abschnitten:

* Zugriff auf [Vertica analytics](../../installation/using/configure-fda-vertica.md) konfigurieren
* Zugriff auf [Snowflake](../../installation/using/configure-fda-snowflake.md) konfigurieren
* Zugriff auf [Google BigQuery](../../installation/using/configure-fda-google-big-query.md) konfigurieren
* Zugriff auf [Azure synapse](../../installation/using/configure-fda-synapse.md) konfigurieren
* Zugriff auf [Hadoop](../../installation/using/configure-fda-hadoop.md) konfigurieren
* Zugriff auf [Oracle](../../installation/using/configure-fda-oracle.md) konfigurieren
* Zugriff auf [Netezza](../../installation/using/configure-fda-netezza.md) konfigurieren
* Zugriff auf [SAP HANA](../../installation/using/configure-fda-sap-hana.md) konfigurieren
* Zugriff auf [Snowflake](../../installation/using/configure-fda-snowflake.md) konfigurieren
* Zugriff auf [Sybase IQ](../../installation/using/configure-fda-sybase.md) konfigurieren
* Zugriff auf [Teradata](../../installation/using/configure-fda-teradata.md) konfigurieren


## Externe Konten zur Integration von Adobe-Lösungen

### Adobe Experience Cloud {#adobe-experience-cloud-external-account}

Um über eine Adobe-ID eine Verbindung zur Adobe Campaign-Konsole herzustellen, müssen Sie das externe Konto **[!UICONTROL Adobe Experience Cloud (MAC)]** konfigurieren.

![](assets/ext_account_9.png)

* **[!UICONTROL IMS-Server]**

  URL Ihres IMS-Servers. Stellen Sie sicher, dass sowohl Staging- als auch Produktionsinstanzen auf den gleichen IMS-Produktionsendpunkt verweisen.

* **[!UICONTROL IMS-Umfang]**

  Der hier definierte Umfang muss eine Teilmenge der vom IMS bereitgestellten Perimeter sein.

* **[!UICONTROL Kennung des IMS-Clients]**

  Die ID Ihres IMS-Client

* **[!UICONTROL IMS-Client-Secret]**

  Berechtigung Ihres IMS-Client-Geheimnisses.

* **[!UICONTROL Callback-Server]**

  Zugriff auf die URL Ihrer Adobe Campaign-Instanz.

* **[!UICONTROL Kennung der IMS-Organisation]**

  Kennung Ihres Unternehmens. Informationen zum Auffinden Ihrer Organisations-ID finden Sie auf [dieser Seite](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=de){_blank}.

* **[!UICONTROL Zuordnungsmaske]**

  Syntax, die es ermöglicht, Konfigurationsnamen im Enterprise Dashboard mit den Gruppen in Adobe Campaign zu synchronisieren

* **[!UICONTROL Server]**

  URL Ihrer Adobe Experience Cloud-Instanz

* **[!UICONTROL Mandant]**

  Name Ihres Adobe Experience Cloud-Mandanten

Weitere Informationen zu dieser Konfiguration finden Sie auf [dieser Seite](../../integrations/using/configuring-ims.md).

## Web-Analyse {#web-analytics-external-account}

Mit dem externen Konto **[!UICONTROL Web Analytics]** können Sie Daten von Adobe Analytics an Adobe Campaign in Form von Segmenten weiterleiten. Umgekehrt werden Indikatoren und Attribute von E-Mail-Kampagnen gesendet, die von Adobe Campaign an den Adobe Analytics-Connector gesendet werden.

![](assets/ext_account_10.png)

Für dieses externe Konto muss die Berechnungsformel für getrackte URLs angereichert und die Verbindung zwischen den beiden Lösungen genehmigt werden. Weiterführende Informationen hierzu finden Sie auf [dieser Seite](../../integrations/using/gs-aa.md).

### Adobe Experience Manager {#adobe-experience-manager-external-account}

Mit dem externen Konto **[!UICONTROL AEM (AEM-Instanz)]** können Sie den Inhalt Ihres E-Mail-Versandes und Ihrer Formulare direkt in Adobe Experience Manager verwalten.

![](assets/ext_account_5.png)

* **[!UICONTROL Server]**

  URL des Adobe-Experience-Manager-Servers

* **[!UICONTROL Port]**

  Kontoname, der für die Verbindung mit der Adobe Experience Manager-Authoring-Instanz verwendet wird

* **[!UICONTROL Passwort]**

  Passwort, das für die Verbindung mit der Adobe Experience Manager-Authoring-Instanz verwendet wird

Weiterführende Informationen hierzu finden Sie in diesem [Abschnitt](../../integrations/using/about-adobe-experience-manager.md).

## Externe CRM-Connector-Konten

### Microsoft Dynamics CRM {#microsoft-dynamics-crm-external-account}

>[!NOTE]
>
> Die Bereitstellungstypen **[!UICONTROL On-Premise]** und **[!UICONTROL Office 365]** werden jetzt nicht mehr unterstützt. [Weitere Informationen](../../rn/using/deprecated-features.md).

Das externe **[!UICONTROL Microsoft Dynamics CRM]**-Konto ermöglicht den Import und Export von Microsoft Dynamics-Daten in Adobe Campaign.

Weitere Informationen zum Campaign - Microsoft Dynamics CRM-Connector finden Sie auf dieser [Seite](../../platform/using/crm-ms-dynamics.md).

Beim Bereitstellungstyp **[!UICONTROL Web-API]** und der Authentifizierung mit **[!UICONTROL Passwort]** müssen Sie die folgenden Details angeben:

![](assets/ext_account_14.png)

* **[!UICONTROL Konto]**

  Konto, mit dem die Anmeldung bei Microsoft CRM erfolgt

* **[!UICONTROL Server]**

  URL Ihres Microsoft CRM-Servers

  Um Ihre Microsoft CRM **[!UICONTROL Server-URL]** zu finden, rufen Sie Ihr Microsoft Dynamics CRM-Konto auf, klicken Sie auf **Dynamics 365** und wählen Sie Ihre App aus. Dann finden Sie Ihre **[!UICONTROL Server-URL]** in der Adressleiste Ihres Browsers, z. B. `https://myserver.crm.dynamics.com/`.

* **[!UICONTROL Client-Kennung]**

  Client-ID, die Sie über das Verwaltungsportal von Microsoft Azure in der Kategorie **[!UICONTROL Code aktualisieren]** im Feld **[!UICONTROL Client-ID]** finden.

* **[!UICONTROL CRM-Version]**

  Wählen Sie die CRM-Version **[!UICONTROL Dynamics CRM 365]** aus.

Beim Bereitstellungstyp **[!UICONTROL Web-API]** und der Authentifizierung mit **[!UICONTROL Zertifikat]** müssen Sie die folgenden Details angeben:

![](assets/ext_account_22.png)

* **[!UICONTROL Server]**

  URL Ihres Microsoft CRM-Servers

  Um Ihre Microsoft CRM **[!UICONTROL Server-URL]** zu finden, rufen Sie Ihr Microsoft Dynamics CRM-Konto auf, klicken Sie auf **Dynamics 365** und wählen Sie Ihre App aus. Dann finden Sie Ihre **[!UICONTROL Server-URL]** in der Adressleiste Ihres Browsers, z. B. `https://myserver.crm.dynamics.com/`.

* **[!UICONTROL Privater Schlüssel (Base64-kodiert)]**

  Beachten Sie, dass der private Schlüssel in Base64 kodiert werden muss.

  Dazu können Sie einen Base64-Encoder oder die Befehlszeile `base64 -w0 private.key` für Linux verwenden.

* **[!UICONTROL Benutzerdefinierte Schlüsselkennung]**

* **[!UICONTROL Schlüsselkennung]**

* **[!UICONTROL Client-Kennung]**

  Client-ID, die Sie über das Verwaltungsportal von Microsoft Azure in der Kategorie **[!UICONTROL Code aktualisieren]** im Feld **[!UICONTROL Client-ID]** finden.

* **[!UICONTROL CRM-Version]**

  Version des CRM: **[!UICONTROL Dynamics CRM 2007]**, **[!UICONTROL Dynamics CRM 2015]** oder **[!UICONTROL Dynamics CRM 2016]**

Weiterführende Informationen zur Konfiguration finden Sie auf dieser [Seite](../../platform/using/crm-connectors.md).

### Salesforce.com CRM  {#salesforce-crm-external-account}

Das externe **[!UICONTROL Salesforce CRM]**-Konto ermöglicht den Import und Export von Salesforce-Daten in Adobe Campaign.

![](assets/ext_account_17.png)

Um dieses externe Konto für die gemeinsame Verwendung mit Adobe Campaign zu konfigurieren, müssen Sie die folgenden Informationen eingeben:

* **[!UICONTROL Konto]**

  Konto, mit dem die Anmeldung bei Salesforce CRM erfolgt

* **[!UICONTROL Passwort]**

  Passwort, mit dem die Anmeldung bei Salesforce CRM erfolgt

* **[!UICONTROL Client-Kennung]**

  Informationen darüber, wo Sie Ihre Client-Kennung finden, erfahren Sie auf dieser [Seite](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL Security-Token]**

  Informationen darüber, wo Sie Ihr Security-Token finden, erfahren Sie auf dieser [Seite](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL API-Version]**

  Wählen Sie die Version der API aus.

Für dieses externe Konto müssen Sie Ihr Salesforce CRM mit dem Konfigurationsassistenten konfigurieren.

Weiterführende Informationen zur Konfiguration finden Sie auf dieser [Seite](../../platform/using/crm-connectors.md).

## Externe Datenkonten übertragen

### Amazon Simple Storage Service (S3) {#amazon-simple-storage-service--s3--external-account}

Der Amazon Simple Storage Service (S3) Connector kann zum Importieren oder Exportieren von Daten in Adobe Campaign verwendet werden. Er kann in einer Workflow-Aktivität eingerichtet werden. Weiterführende Informationen hierzu finden Sie auf [dieser Seite](../../workflow/using/file-transfer.md).

![](assets/ext_account_3.png)

Zum Einrichten dieses neuen externen Kontos benötigen Sie die folgenden Informationen:

* **[!UICONTROL AWS-S3-Konto-Server]**

  Die URL Ihres Servers sollte folgendermaßen ausgefüllt werden:

  ```
  <S3bucket name>.s3.amazonaws.com/<s3object path>
  ```

* **[!UICONTROL Kennung des AWS-Zugangsschlüssels]**

  Informationen darüber, wo Sie Ihre Kennung des AWS-Zugangsschlüssels finden, erfahren Sie auf dieser [Seite](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) .

* **[!UICONTROL Geheimer AWS-Zugangsschlüssel]**

  Informationen darüber, wo Sie Ihren geheimen AWS-Zugangsschlüssel finden, erfahren Sie auf dieser [Seite](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/).

* **[!UICONTROL AWS-Region]**

  Weiterführende Informationen zur AWS-Region finden Sie auf dieser [Seite](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/).

* Die Checkbox **[!UICONTROL Serverseitige Verschlüsselung verwenden]** ermöglicht es Ihnen, Ihre Datei in S3 im verschlüsselten Modus zu speichern.

Informationen darüber, wo Sie die Kennung des Zugriffsschlüssels und den geheimen Zugriffsschlüssel finden, finden Sie in der Dokumentation zu Amazon Web Services [Dokumentation](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) .

### Azur Blob-Speicherung {#azure-blob-external-account}

Mit dem externen Konto **Azure Blob Storage** können Daten mithilfe einer Workflow-Aktivität vom Typ **[!UICONTROL Dateiübertragung]** in Adobe Campaign importiert oder exportiert werden. Weitere Informationen hierzu finden Sie in diesem [Abschnitt](../../workflow/using/file-transfer.md).

![](assets/ext_account_23.png)

Um das externe **[!UICONTROL Azure-Konto]** für die Verwendung mit Adobe Campaign zu konfigurieren, müssen Sie die folgenden Details angeben:

* **[!UICONTROL Server]**

  URL Ihres Azure Blob Storage-Servers

* **[!UICONTROL Verschlüsselung]**

  Typ der gewählten Verschlüsselung: **[!UICONTROL Keine]** oder **[!UICONTROL SSL]**.

* **[!UICONTROL Zugriffsschlüssel]**

  Informationen darüber, wo Sie Ihren **[!UICONTROL Zugriffsschlüssel]** finden, erfahren Sie auf dieser [Seite](https://docs.microsoft.com/de-de/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).

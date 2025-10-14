---
product: campaign
title: Externe Konten
description: Erfahren Sie, wie Sie externe Konten erstellen
feature: Installation, Application Settings, External Account
audience: platform
content-type: reference
topic-tags: administration-basics
exl-id: 4a17d5e8-c73f-42e7-b641-0fee6a52c5c0
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '1988'
ht-degree: 68%

---

# Externe Konten{#external-accounts}

Adobe Campaign enthält eine Reihe vordefinierter externer Konten. Um Verbindungen zu externen Systemen einzurichten, können Sie neue externe Konten erstellen.

Externe Konten werden von technischen Prozessen, wie technischen Workflows oder Kampagnen-Workflows, verwendet. Beispiel: Bei der Einrichtung eines Dateitransfers in einem Workflow oder bei einem Datenaustausch mit einem anderen Programm (Adobe Target, Experience Manager usw.) müssen Sie ein externes Konto auswählen.

## Erstellen eines externen Kontos {#creating-an-external-account}

Gehen Sie wie folgt vor, um ein neues externes Konto zu erstellen.  Detaillierte Einstellungen hängen vom Typ des externen Kontos ab.

1. Wählen Sie in **[!UICONTROL Explorer]** die Option **[!UICONTROL Administration]** &quot;>&quot; **[!UICONTROL Plattform]** &quot;>&quot; **[!UICONTROL Externe Konten]**.

   ![](assets/ext_account_1.png)

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Neu]**.

   ![](assets/ext_account_2.png)

1. Geben Sie einen **[!UICONTROL Titel]** und einen **[!UICONTROL internen Namen]** ein.
1. Wählen Sie den **[!UICONTROL Typ]** des externen Kontos aus, den Sie erstellen möchten.
1. Konfigurieren Sie den Zugriff auf das Konto, indem Sie die Anmeldedaten entsprechend dem gewählten externen Kontotyp angeben.

   Die nötigen Informationen werden normalerweise vom Anbieter des Servers bereitgestellt, mit dem Sie eine Verbindung herstellen möchten.

1. Markieren Sie die Option **[!UICONTROL Aktiviert]**, um die Verbindung zu aktivieren.
1. Klicken Sie auf **[!UICONTROL Speichern]**.

Das externe Konto wird erstellt und der Liste der externen Konten hinzugefügt.

## Kampagnenspezifische externe Konten

### Bounce-E-Mails {#bounce-mails-external-account}

Das externe Konto **Bounce Messages** gibt das externe POP3-Konto an, das für die Verbindung mit dem E-Mail-Service verwendet werden soll. Weitere Informationen zu diesem externen Konto finden Sie in der [ zu Campaign v8 ](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/inbound-emails.html?lang=de){target="_blank"}.

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
>Bevor Sie Ihr externes POP3-Konto mit Microsoft OAuth 2.0 konfigurieren, müssen Sie die Anwendung zunächst im Azure-Portal registrieren. Weitere Informationen hierzu finden Sie auf [dieser Seite](https://docs.microsoft.com/de-de/azure/active-directory/develop/quickstart-register-app).

Um ein externes POP3-Programm mit **Microsoft OAuth 2.0** zu konfigurieren, markieren Sie die Option **[!UICONTROL Microsoft OAuth 2.0]** und füllen Sie die folgenden Felder aus:

* **[!UICONTROL Azure-Mandant]**

  Eine Azure ID (oder Verzeichnis-ID bzw. Mandanten-ID) finden Sie in der Dropdown-Liste **Grundlagen** der Anwendungsübersicht im Azure-Portal.

* **[!UICONTROL Azure-Client-ID]**

  Client-ID (oder Anwendungs (Client)-ID) finden Sie in der Dropdown-Liste **Grundlagen** der Anwendungsübersicht im Azure-Portal.

* **[!UICONTROL Azure-Client-Geheimnis]**

  Die Client-Geheimnis-ID finden Sie in der Spalte **Client-Geheimnisse** im Menü **Zertifikate und Geheimnisse** Ihrer Anwendung im Azure-Portal.

* **[!UICONTROL Azure-Umleitungs-URL]**

  Die Umleitungs-URL finden Sie im Menü **Authentifizierung** Ihrer Anwendung im Azure-Portal. Sie sollte mit der folgenden Syntax enden: `nl/jsp/oauth.jsp`, z. B. `https://redirect.adobe.net/nl/jsp/oauth.jsp`.

Zum Einrichten und Verwenden der Schaltfläche **[!UICONTROL Verbindung testen]** in der Client-Konsole ist ein Internetzugang erforderlich. Nach der Einrichtung kann der inMail-Prozess ohne Internet mit Microsoft-Servern kommunizieren.

Nachdem Sie Ihre unterschiedlichen Anmeldedaten eingegeben haben, können Sie auf **[!UICONTROL Verbindung einrichten]** klicken, um die Konfiguration Ihres externen Kontos abzuschließen.

### Routing{#routing-external-account}

Mit dem externen **[!UICONTROL Routing]**-Konto können Sie jeden in Adobe Campaign verfügbaren Kanal abhängig von den installierten Packages konfigurieren.

![](assets/ext_account_7.png)

Die folgenden Kanäle können konfiguriert werden:

* [E-Mail](#email-routing-external-account)
* [Mobiltelefon (SMS)](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)
* [Telefon](../../delivery/using/communication-channels.md#other-channels)
* [Direkt-Mail](../../delivery/using/about-direct-mail-channel.md)
* [Agentur](../../delivery/using/communication-channels.md#other-channels)
* [X (früher bekannt als Twitter)](../../social/using/about-social-marketing.md)
* [iOS- und Android-Kanäle](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html){target="_blank"}

### E-Mail-Routing {#email-routing-external-account}

Das externe E-Mail-Routing-Konto wird standardmäßig bereitgestellt und an Ihre Konfiguration angepasst.

Als On-Premise-/Hybrid-Kunde können Sie neue externe Routing-Konten erstellen oder Parameter aktualisieren, wie unten beschrieben. Diese Konfiguration ist erfahrenen Benutzern vorbehalten und kann sich auf Ihre Zustellbarkeit auswirken. Wenden Sie sich bei Fragen an die Adobe-Kundenunterstützung oder Ihren Adobe-Support-Mitarbeiter.

* Sie können einen Routing **Typ „Mid-Sourcing**, **External** oder **Bulk** Versand verwenden.

* Bei **-** und **Mid-Sourcing**-Versandmodi können Sie Ihre Branding-Parameter auf der Registerkarte **Branding** angeben. Diese Parameter überschreiben die [Standardparameter](../../installation/using/deploying-an-instance.md#email-channel-parameters) für **Mirrorseiten-URL** und **Fehleradresse** mit markenspezifischen Einstellungen.

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

Mit dem externen FTP -Konto können Sie den Zugriff auf einen Server außerhalb von Adobe Campaign konfigurieren und testen. Um Verbindungen mit externen Systemen wie FTP-Servern 898 für Dateiübertragungen einzurichten, können Sie Ihre eigenen externen Konten erstellen. Weitere Informationen hierzu finden Sie in der [ zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/file-transfer.html?lang=de){target="_blank"}.

Geben Sie dazu in diesem externen Konto die Adresse und die Anmeldedaten für die Verbindungsherstellung zum FTP-Server an.

![](assets/ext_account_8.png)

* **[!UICONTROL Server]**

  Name des FTP-Servers

* **[!UICONTROL Port]**

  Port-Nummer der FTP-Verbindung. Der Standard-Port ist 21.

* **[!UICONTROL Konto]**

  Name des Benutzers.

* **[!UICONTROL Passwort]**

  Passwort des Benutzerkontos.

* **[!UICONTROL Verschlüsselung]**

  Typ der gewählten Verschlüsselung: **[!UICONTROL Keine]** oder **[!UICONTROL SSL]**.

Informationen zu diesen Anmeldedaten finden Sie auf dieser [Seite](https://help.dreamhost.com/hc/en-us/articles/115000675027-FTP-overview-and-credentials).

### SFTP {#sftp-external-account}

Mit dem externen SFTP -Konto können Sie den Zugriff auf einen Server außerhalb von Adobe Campaign konfigurieren und testen. Um Verbindungen mit externen Systemen wie SFTP für Dateiübertragungen einzurichten, können Sie Ihre eigenen externen Konten erstellen. Weitere Informationen hierzu finden Sie in der [ zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/file-transfer.html?lang=de){target="_blank"}.

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

### External Database (FDA) {#external-database-external-account}

Verwenden Sie das **Externe Datenbank**-Konto, um eine Verbindung zu einer externen Datenbank herzustellen. Weitere Informationen zur Option „Federated Data Access“ (FDA) finden Sie in [diesem Abschnitt](../../installation/using/about-fda.md).

Externe Datenbanken, die mit Campaign kompatibel sind, sind in der ([) ](../../rn/using/compatibility-matrix.md)

![](assets/ext_account_11.png)

Die Konfigurationseinstellungen für externe Konten hängen von der Datenbank-Engine ab. Weitere Informationen finden Sie in den folgenden Abschnitten:

* Zugriff auf [Vertica Analytics konfigurieren](../../installation/using/configure-fda-vertica.md)
* Zugriff auf [Snowflake konfigurieren](../../installation/using/configure-fda-snowflake.md)
* Zugriff auf [Google BigQuery konfigurieren](../../installation/using/configure-fda-google-big-query.md)
* Zugriff auf [Azure Synapse konfigurieren](../../installation/using/configure-fda-synapse.md)
* Zugriff auf [Hadoop konfigurieren](../../installation/using/configure-fda-hadoop.md)
* Zugriff auf [Oracle konfigurieren](../../installation/using/configure-fda-oracle.md)
* Zugriff auf [Netezza konfigurieren](../../installation/using/configure-fda-netezza.md)
* Zugriff auf [SAP HANA konfigurieren](../../installation/using/configure-fda-sap-hana.md)
* Zugriff auf [Snowflake konfigurieren](../../installation/using/configure-fda-snowflake.md)
* Zugriff auf [Sybase IQ konfigurieren](../../installation/using/configure-fda-sybase.md)
* Zugriff auf [Teradata konfigurieren](../../installation/using/configure-fda-teradata.md)


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

  Anmeldedaten Ihres IMS-Client-Geheimnisses.

* **[!UICONTROL Callback-Server]**

  Zugriffs-URL Ihrer Adobe Campaign-Instanz.

* **[!UICONTROL Kennung der IMS-Organisation]**

  ID Ihrer Organisation. Auf [dieser Seite](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=de){_blank} finden Sie Ihre Organisations-ID.

* **[!UICONTROL Zuordnungsmaske]**

  Syntax, die es ermöglicht, Konfigurationsnamen im Enterprise Dashboard mit den Gruppen in Adobe Campaign zu synchronisieren

* **[!UICONTROL Server]**

  URL Ihrer Adobe Experience Cloud-Instanz

* **[!UICONTROL Mandant]**

  Name Ihres Adobe Experience Cloud-Mandanten

Weitere Informationen zu dieser Konfiguration finden Sie auf [dieser Seite](../../integrations/using/configuring-ims.md).

## Web-Analyse {#web-analytics-external-account}

Mit **[!UICONTROL externen Konto]** Web Analytics) können Sie Daten von Adobe Analytics in Form von Segmenten an Adobe Campaign weiterleiten. Umgekehrt sendet es Indikatoren und Attribute von E-Mail-Kampagnen, die von Adobe Campaign bereitgestellt werden, an den Adobe Analytics-Connector.

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
> **[!UICONTROL On-Premise]**- und **[!UICONTROL Office 365]**-Bereitstellungstypen werden jetzt nicht mehr unterstützt. [Weitere Informationen](../../rn/using/deprecated-features.md).

Das externe **[!UICONTROL Microsoft Dynamics CRM]**-Konto ermöglicht den Import und Export von Microsoft Dynamics-Daten in Adobe Campaign.

Weitere Informationen zum Campaign-Microsoft Dynamics-CRM-Connector finden Sie auf [Seite](../../platform/using/crm-ms-dynamics.md).

Beim Bereitstellungstyp **[!UICONTROL Web-API]** und der Authentifizierung mit **[!UICONTROL Passwort]** müssen Sie die folgenden Details angeben:

![](assets/ext_account_14.png)

* **[!UICONTROL Konto]**

  Konto, mit dem die Anmeldung bei Microsoft CRM erfolgt

* **[!UICONTROL Server]**

  URL Ihres Microsoft CRM-Servers

  Um Ihre Microsoft CRM-**[!UICONTROL Server-URL]** zu finden, rufen Sie Ihr Microsoft Dynamics CRM-Konto auf, klicken Sie dann auf **Dynamics 365** und wählen Sie Ihre Anwendung aus. Ihre **[!UICONTROL Server-URL]** finden Sie dann in der Adressleiste Ihres Browsers, z.B. `https://myserver.crm.dynamics.com/`.

* **[!UICONTROL Client-Kennung]**

  Client-ID, die Sie über das Verwaltungsportal von Microsoft Azure in der Kategorie **[!UICONTROL Code aktualisieren]** im Feld **[!UICONTROL Client-ID]** finden.

* **[!UICONTROL CRM-Version]**

  Wählen Sie **[!UICONTROL Dynamics CRM 365]** CRM-Version.

Beim Bereitstellungstyp **[!UICONTROL Web-API]** und der Authentifizierung mit **[!UICONTROL Zertifikat]** müssen Sie die folgenden Details angeben:

![](assets/ext_account_22.png)

* **[!UICONTROL Server]**

  URL Ihres Microsoft CRM-Servers

  Um Ihre Microsoft CRM-**[!UICONTROL Server-URL]** zu finden, rufen Sie Ihr Microsoft Dynamics CRM-Konto auf, klicken Sie dann auf **Dynamics 365** und wählen Sie Ihre Anwendung aus. Ihre **[!UICONTROL Server-URL]** finden Sie dann in der Adressleiste Ihres Browsers, z.B. `https://myserver.crm.dynamics.com/`.

* **[!UICONTROL Privater Schlüssel (Base64-kodiert)]**

  Beachten Sie, dass der private Schlüssel mit Base64 codiert werden muss.

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

  Informationen darüber, wo Sie Ihre Client-Kennung finden, erfahren Sie auf dieser [Seite](https://help.salesforce.com/articleView?id=000205876&type=1).

* **[!UICONTROL Security-Token]**

  Informationen darüber, wo Sie Ihr Security-Token finden, erfahren Sie auf dieser [Seite](https://help.salesforce.com/articleView?id=000205876&type=1).

* **[!UICONTROL API-Version]**

  Wählen Sie die Version der API aus.

Für dieses externe Konto müssen Sie Salesforce CRM mit dem Konfigurationsassistenten konfigurieren.

Weiterführende Informationen zur Konfiguration finden Sie auf dieser [Seite](../../platform/using/crm-connectors.md).

## Übertragen von Daten mit externen Konten

### Amazon Simple Storage Service (S3) {#amazon-simple-storage-service--s3--external-account}

Der Amazon Simple Storage Service (S3) Connector kann zum Import oder Export von Daten in Adobe Campaign verwendet werden. Er kann in einer Workflow-Aktivität eingerichtet werden. Weitere Informationen finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/file-transfer.html?lang=de){target="_blank"}.

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

Informationen darüber, wo Sie die Kennung des Zugriffsschlüssels und den geheimen Zugriffsschlüssel finden, erhalten Sie in der [Dokumentation](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) zu Amazon Web Services.

### Azur Blob Storage {#azure-blob-external-account}

Das externe **Azure Blob Storage**-Konto kann mithilfe einer Workflow-Aktivität vom Typ **[!UICONTROL Dateiübertragung“ zum Importieren]** Exportieren von Daten in Adobe Campaign verwendet werden. Weitere Informationen finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/file-transfer.html?lang=de){target="_blank"}.

![](assets/ext_account_23.png)

Um das **[!UICONTROL externe Azure-Konto]** für die gemeinsame Verwendung mit Adobe Campaign zu konfigurieren, müssen Sie die folgenden Informationen eingeben:

* **[!UICONTROL Server]**

  URL Ihres Azure Blob Storage-Servers.

* **[!UICONTROL Verschlüsselung]**

  Typ der gewählten Verschlüsselung: **[!UICONTROL Keine]** oder **[!UICONTROL SSL]**.

* **[!UICONTROL Zugriffsschlüssel]**

  Informationen darüber, wo Sie Ihren **[!UICONTROL Zugangsschlüssel]** finden, erhalten Sie auf dieser [Seite](https://docs.microsoft.com/de-de/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).

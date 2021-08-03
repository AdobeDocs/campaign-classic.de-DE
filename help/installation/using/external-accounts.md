---
product: campaign
title: Externe Konten
description: Erfahren Sie, wie Sie externe Konten erstellen
audience: platform
content-type: reference
topic-tags: administration-basics
exl-id: 4a17d5e8-c73f-42e7-b641-0fee6a52c5c0
source-git-commit: 94664ec56d269afef926663c52b84ccaaab02480
workflow-type: tm+mt
source-wordcount: '1827'
ht-degree: 78%

---

# Externe Konten{#external-accounts}

Adobe Campaign enthält eine Reihe vordefinierter externer Konten. Um Verbindungen zu externen Systemen einzurichten, können Sie neue externe Konten erstellen.

Externe Konten werden von technischen Prozessen, wie technischen Workflows oder Kampagnen-Workflows, verwendet. Beispiel: Bei der Einrichtung eines Dateitransfers in einem Workflow oder bei einem Datenaustausch mit einem anderen Programm (Adobe Target, Experience Manager usw.) müssen Sie ein externes Konto auswählen.

## Externes Konto erstellen {#creating-an-external-account}

Gehen Sie wie folgt vor, um ein neues externes Konto zu erstellen. Detaillierte Einstellungen hängen vom Typ des externen Kontos ab.

1. Wählen Sie in Campaign **[!UICONTROL Explorer]** **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Plattform]** &#39;>&#39; **[!UICONTROL Externe Konten]**.

   ![](assets/ext_account_1.png)

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Neu]**.

   ![](assets/ext_account_2.png)

1. Geben Sie einen **[!UICONTROL Titel]** und einen **[!UICONTROL Internen Namen]** ein.
1. Wählen Sie den **[!UICONTROL Typ]** des externen Kontos aus, den Sie erstellen möchten.
1. Konfigurieren Sie den Zugriff auf das Konto, indem Sie die Anmeldeinformationen entsprechend dem gewählten externen Kontotyp angeben.

   Die nötigen Informationen werden normalerweise vom Anbieter des Servers bereitgestellt, mit dem Sie eine Verbindung herstellen möchten.

1. Aktivieren Sie die Option **[!UICONTROL Aktiviert]** , um die Verbindung zu aktivieren.
1. Klicken Sie auf **[!UICONTROL Speichern]**.

Das externe Konto wird erstellt und der Liste der externen Konten hinzugefügt.

## Kampagnenspezifische externe Konten

### Bounce Messages {#bounce-mails-external-account}

Das externe Konto **Bounce Messages** gibt das externe POP3-Konto an, das für die Verbindung mit dem E-Mail-Dienst verwendet werden soll. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../workflow/using/inbound-emails.md).

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

### Routing{#routing-external-account}

Mit dem externen **[!UICONTROL Routing]**-Konto können Sie jeden in Adobe Campaign verfügbaren Kanal abhängig von den installierten Packages konfigurieren.

![](assets/ext_account_7.png)

Die folgenden Kanäle können konfiguriert werden:

* [E-Mail](../../installation/using/deploying-an-instance.md#email-channel-parameters)
* [Mobiltelefon (SMS)](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)
* [Telefon](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)
* [Briefpost](../../delivery/using/about-direct-mail-channel.md)
* [Agentur](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)
* [Facebook](../../social/using/publishing-on-facebook-walls.md#delegating-write-access-to-adobe-campaign)
* [Twitter](../../social/using/configuring-publishing-on-twitter.md)
* [iOS-Kanal](../../delivery/using/configuring-the-mobile-application.md)
* [Android-Kanal](../../delivery/using/configuring-the-mobile-application-android.md)


### Ausführungsinstanz  {#execution-instance-external-account}

Wenn Sie eine aufgegliederte Architektur haben, müssen Sie die mit der Kontrollinstanz verbundenen Ausführungsinstanzen spezifizieren und miteinander verbinden. Transaktionsnachrichtenvorlagen werden in der Ausführungsinstanz bereitgestellt.

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

Mit dem externen FTP-Konto können Sie den Zugriff auf einen Server außerhalb von Adobe Campaign konfigurieren und testen. Um Verbindungen mit externen Systemen wie dem FTP-Server 898, der für Dateiübertragungen verwendet wird, einzurichten, können Sie eigene externe Konten erstellen. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../workflow/using/file-transfer.md).

Geben Sie dazu in diesem externen Konto die Adresse und die Zugangsdaten für die Verbindungsherstellung zum FTP-Server an.

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

Informationen zu diesen Zugangsdaten finden Sie auf dieser [Seite](https://help.dreamhost.com/hc/en-us/articles/115000675027-FTP-overview-and-credentials).

### SFTP {#sftp-external-account}

Mit dem externen SFTP-Konto können Sie den Zugriff auf einen Server außerhalb von Adobe Campaign konfigurieren und testen. Um Verbindungen mit externen Systemen wie dem SFTP-Server einzurichten, der für Dateiübertragungen verwendet wird, können Sie eigene externe Konten erstellen. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../workflow/using/file-transfer.md).

![](assets/ext_account_4.png)

* **[!UICONTROL Server]**

   URL des SFTP-Servers

* **[!UICONTROL Port]**

   Port-Nummer der FTP-Verbindung. Der Standard-Port ist 22.

* **[!UICONTROL Konto]**

   Kontoname, der für die Verbindung zum SFTP-Server verwendet wird

* **[!UICONTROL Passwort]**

   Passwort, das für die Verbindung zum SFTP-Server verwendet wird

### Externe Datenbank (FDA) {#external-database-external-account}

Verwenden Sie das externe Konto **Externe Datenbank**, um eine Verbindung zu einer externen Datenbank herzustellen. Weitere Informationen zur Option Federated Data Access (FDA) finden Sie in [diesem Abschnitt](../../installation/using/about-fda.md).

Externe Datenbanken, die mit Campaign kompatibel sind, sind in der [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md) aufgeführt.

![](assets/ext_account_11.png)

Die Konfigurationseinstellungen für externe Konten hängen von der Datenbank-Engine ab. Weitere Informationen finden Sie in den folgenden Abschnitten:

* Zugriff auf [Vertikal](../../installation/using/configure-fda-vertica.md) konfigurieren
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

### Facebook Connect {#facebook-connect-external-account}

Mit dem externen Konto **[!UICONTROL Facebook Connect]** können Sie in Facebook-Anwendungen personalisierte Inhalte anzeigen. Dadurch wird es einfacher, über dieses soziale Netzwerk potenzielle Kunden zu gewinnen.

Für jede Facebook-Anwendung müssen Sie ein externes Konto vom Typ **[!UICONTROL Facebook Connect]** erstellen. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

![](assets/ext_account_12.png)

* **[!UICONTROL Hosting-Modus]**

   Hosting-Modus der Anwendung: **[!UICONTROL Bei einem Partner gehostet]** oder **[!UICONTROL Auf dieser Instanz gehostet]**

* **[!UICONTROL Anwendungs-ID]**

   App-ID Ihrer Facebook-Anwendung

* **[!UICONTROL Geheimschlüssel]**

   App-Geheimnis Ihrer Facebook-Anwendung.

Wenn Sie den Modus &quot;Auf dieser Instanz gehostet&quot; gewählt haben, muss die Sichere Canvas-URL in das Feld **Facebook Web Games (https)** auf Facebook eingefügt werden.

Informationen zu diesen Zugangsdaten finden Sie auf dieser [Seite](https://developers.facebook.com/docs/facebook-login/access-tokens).

## Adobe Solution Integration - Externe Konten

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

   Ihr IMS-Client-Geheimnisses.

* **[!UICONTROL Callback-Server]**

   Zugriff-URL Ihrer Adobe Campaign-Instanz.

* **[!UICONTROL Kennung der IMS-Organisation]**

   Kennung Ihrer IMS-Organisation. Ihre Organisations-ID finden Sie auf [dieser Seite](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html?lang=de) (**Wo finde ich meine IMS-Organisations-ID?**).

* **[!UICONTROL Zuordnungsmaske]**

   Syntax, die es ermöglicht, Konfigurationsnamen im Enterprise Dashboard mit den Gruppen in Adobe Campaign zu synchronisieren

* **[!UICONTROL Server]**

   URL Ihrer Adobe Experience Cloud-Instanz

* **[!UICONTROL Mandant]**

   Name Ihres Adobe Experience Cloud-Mandanten

Weitere Informationen zu dieser Konfiguration finden Sie auf [dieser Seite](../../integrations/using/configuring-ims.md).

## Web Analytics {#web-analytics-external-account}

Mit dem externen Konto **[!UICONTROL Web Analytics]** können Sie Daten von Adobe Analytics an Adobe Campaign in Form von Segmenten weiterleiten. Umgekehrt werden Indikatoren und Attribute von E-Mail-Kampagnen gesendet, die von Adobe Campaign an den Adobe Analytics-Connector gesendet werden.

![](assets/ext_account_10.png)

Für dieses externe Konto muss die Berechnungsformel für getrackte URLs angereichert und die Verbindung zwischen den beiden Lösungen genehmigt werden. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../platform/using/adobe-analytics-connector.md#external-account-classic).

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
> **[!UICONTROL Die Bereitstellungstypen On-]** Premise und  **[!UICONTROL Office 365]**  sind jetzt veraltet. [Weitere Informationen](../../rn/using/deprecated-features.md).

Das externe **[!UICONTROL Microsoft Dynamics CRM]**-Konto ermöglicht den Import und Export von Microsoft Dynamics-Daten in Adobe Campaign.

Weitere Informationen zum CRM-Connector für Campaign mit Microsoft Dynamics finden Sie auf dieser [Seite](../../platform/using/crm-ms-dynamics.md).

Beim Bereitstellungstyp **[!UICONTROL Web-API]** und der Authentifizierung mit **[!UICONTROL Passwort]** müssen Sie die folgenden Details angeben:

![](assets/ext_account_14.png)

* **[!UICONTROL Konto]**

   Konto, mit dem die Anmeldung bei Microsoft CRM erfolgt

* **[!UICONTROL Server]**

   URL Ihres Microsoft CRM-Servers

   Um Ihre Microsoft CRM **[!UICONTROL Server-URL]** zu finden, rufen Sie Ihr Microsoft Dynamics CRM-Konto auf, klicken Sie dann auf **Dynamics 365** und wählen Sie Ihre App aus. Sie finden dann Ihre **[!UICONTROL Server-URL]** in der Adressleiste Ihres Browsers, z. B. `https://myserver.crm.dynamics.com/`.

* **[!UICONTROL Client-Kennung]**

   Client-ID, die Sie über das Verwaltungsportal von Microsoft Azure in der Kategorie **[!UICONTROL Code aktualisieren]** im Feld **[!UICONTROL Client-ID]** finden.

* **[!UICONTROL CRM-Version]**

   Wählen Sie die CRM-Version **[!UICONTROL Dynamics CRM 365]** aus.

Beim Bereitstellungstyp **[!UICONTROL Web-API]** und der Authentifizierung mit **[!UICONTROL Zertifikat]** müssen Sie die folgenden Details angeben:

![](assets/ext_account_22.png)

* **[!UICONTROL Server]**

   URL Ihres Microsoft CRM-Servers

   Um Ihre Microsoft CRM **[!UICONTROL Server-URL]** zu finden, rufen Sie Ihr Microsoft Dynamics CRM-Konto auf, klicken Sie dann auf **Dynamics 365** und wählen Sie Ihre App aus. Sie finden dann Ihre **[!UICONTROL Server-URL]** in der Adressleiste Ihres Browsers, z. B. `https://myserver.crm.dynamics.com/`.

* **[!UICONTROL Privater Schlüssel (Base64-kodiert)]**

   Beachten Sie, dass der private Schlüssel in Base64 kodiert werden muss.

   Dazu können Sie die Hilfe eines Base64-Encoder verwenden oder die Befehlszeile `base64 -w0 private.key` für Linux verwenden.

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

Für dieses externe Konto müssen Sie Salesforce CRM mit dem Konfigurationsassistenten konfigurieren.

Weiterführende Informationen zur Konfiguration finden Sie auf dieser [Seite](../../platform/using/crm-connectors.md).

## Externe Datenkonten übertragen

### Amazon Simple Storage Service (S3) {#amazon-simple-storage-service--s3--external-account}

Der Amazon Simple Storage Service (S3) Connector kann zum Import oder Export von Daten in Adobe Campaign verwendet werden. Es kann in einer Workflow-Aktivität eingerichtet werden. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../workflow/using/file-transfer.md).

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

Informationen darüber, wo Sie die Kennung des Zugriffsschlüssels und den geheimen Zugriffsschlüssel finden, erfahren Sie im [Handbuch](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) der Amazon-Webdienste.

### Azur Blob-Speicherung {#azure-blob-external-account}

Mit dem externen Konto **Azure Blob Storage** können Daten mithilfe einer Workflow-Aktivität vom Typ **[!UICONTROL Dateiübertragung]** in Adobe Campaign importiert oder exportiert werden. Weitere Informationen hierzu finden Sie in [diesem Abschnitt](../../workflow/using/file-transfer.md).

![](assets/ext_account_23.png)

Um das externe **** Azure-Konto für die gemeinsame Verwendung mit Adobe Campaign zu konfigurieren, müssen Sie die folgenden Informationen eingeben:

* **[!UICONTROL Server]**

   URL Ihres Azure Blob Storage-Servers

* **[!UICONTROL Verschlüsselung]**

   Typ der gewählten Verschlüsselung: **[!UICONTROL Keine]** oder **[!UICONTROL SSL]**.

* **[!UICONTROL Zugriffsschlüssel]**

   Informationen darüber, wo Sie Ihren **[!UICONTROL Zugriffsschlüssel]** finden, erfahren Sie auf dieser [Seite](https://docs.microsoft.com/de-de/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).

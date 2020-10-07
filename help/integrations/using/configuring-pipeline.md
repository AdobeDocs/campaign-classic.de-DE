---
title: Integration konfigurieren
seo-title: Integration konfigurieren
description: Integration konfigurieren
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 100%

---


# Pipeline konfigurieren {#configuring-pipeline}

Authentifizierungsparameter wie die Kunden-ID, der private Schlüssel und der Authentifizierungsendpunkt werden in den Konfigurationsdateien der Instanz konfiguriert.
Die Liste der zu verarbeitenden Auslöser wird in einer Option konfiguriert. Dabei kommt das JSON-Format zum Einsatz.
Der Auslöser wird unmittelbar mit JavaScript-Code verarbeitet. Er wird ohne weitere Verarbeitung in Echtzeit in einer Datenbanktabelle gespeichert.
Die Auslöser werden für das Targeting eines Kampagnen-Workflows verwendet, der E-Mails sendet. Die Kampagne ist so eingerichtet, dass ein Kunde, der beide Auslöserereignisse aufweist, eine E-Mail erhält.

## Voraussetzungen {#prerequisites}

Die Verwendung von [!DNL Experience Cloud Triggers] in Campaign erfordert:

* Adobe Campaign Version 6.11 Build 8705 oder höher.
* Adobe Analytics Ultimate, Premium, Foundation, OD, Select, Prime, Mobile Apps, Select oder Standard.

Vorausgesetzte Konfigurationen sind:

* Erstellen einer privaten Schlüsseldatei und anschließendes Erstellen der OAuth-Anwendung, die mit diesem Schlüssel registriert wird.
* Konfigurieren der Auslöser in Adobe Analytics.

Die Adobe Analytics-Konfiguration wird nicht in diesem Dokument behandelt.

Für Adobe Campaign sind folgende Informationen von Adobe Analytics erforderlich:

* Der Name der OAuth-Anwendung.
* Die IMSOrgId, die Kennung des Experience Cloud-Kunden.
* Die Namen der in Analytics konfigurierten Auslöser.
* Name und Format der Datenfelder, die mit der Marketing-Datenbank abgestimmt werden sollen.

Teil dieser Konfiguration muss vom Benutzer vorgenommen werden und erfordert Folgendes:

* Grundkenntnisse der JSON-, XML- und JavaScript-Analyse in Adobe Campaign.
* Grundkenntnisse der QueryDef- und Writer-APIs.
* Grundverständnis der Verschlüsselung und Authentifizierung mit privaten Schlüsseln.

>[!NOTE]
>
>Da die Bearbeitung des JS-Codes technische Fertigkeiten voraussetzt, sollten Sie es ohne entsprechende Kenntnisse nicht versuchen. <br>Auslöser werden in einer Datenbanktabelle gespeichert. Auf diese Weise können Auslöserdaten von Marketing-Anwendern in Zielgruppen-Workflows sicher verwendet werden.

## Authentifizierungs- und Konfigurationsdateien {#authentication-configuration}

Eine Authentifizierung ist erforderlich, da die Pipeline in Adobe Experience Cloud gehostet wird.
Wenn der Marketing-Server lokal gehostet wird, muss er sich bei der Anmeldung bei der Pipeline für eine sichere Verbindung authentifizieren.
Er verwendet ein Schlüsselpaar aus öffentlichem und privatem Schlüssel. Der Prozess entspricht der Verwendung einer Kombination aus Benutzer und Passwort, ist aber sicherer.

### IMSOrgId {#imsorgid}

Die IMSOrgId ist die Kennung des Kunden in Adobe Experience Cloud.
Legen Sie sie in der Datei &quot;serverConf.xml&quot; der Instanz unter dem Attribut &quot;IMSOrgId&quot; fest.
Beispiel:

```
<redirection IMSOrgId="C5E715(…)98A4@AdobeOrg" (…)
```

### Schlüsselgenerierung {#key-generation}

Der Schlüssel besteht aus einem Dateipaar. Er liegt im RSA-Format vor und ist 4.096 Byte lang. Er kann mit einem Open-Source-Tool wie OpenSSL generiert werden. Bei jeder Ausführung des Tools wird zufällig ein neuer Schlüssel generiert.
Die Schritte werden im Folgenden beschrieben:

* ```openssl genrsa -out <private_key.pem> 4096```

* ```openssl rsa -pubout -in <private_key.pem> -out <public_key.pem>```

Beispiel für die Datei &quot;private_key.pem&quot;:

```
----BEGIN RSA PRIVATE KEY----
MIIEowIBAAKCAQEAtqcYzt5WGGABxUJSfe1Xy8sAALrfVuDYURpdgbBEmS3bQMDb
(…)
64+YQDOSNFTKLNbDd+bdAA+JoYwUCkhFyvrILlgvlSBvwAByQ2Lx
----END RSA PRIVATE KEY----
```

Beispiel für die Datei &quot;public_key.pem&quot;:

```
----BEGIN PUBLIC KEY----
MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAtqcYzt5WGGABxUJSfe1X
(…)
EwIDAQAB
----END PUBLIC KEY----
```

>[!NOTE]
>
>Schlüssel sollten nicht von PuttyGen generiert werden. OpenSSL ist die beste Wahl.

### OAuth-Client-Erstellung in Adobe Experience Cloud {#oauth-client-creation}

Sie müssen eine Anwendung vom Typ &quot;JWT&quot; erstellen, indem Sie sich bei Adobe Analytics unter **[!UICONTROL Admin]** > **[!UICONTROL User Management]** > **[!UICONTROL Veraltete OAuth-Anwendung]** im richtigen Organisationskonto anmelden.

Führen Sie folgende Schritte aus:

1. Wählen Sie das **[!UICONTROL Dienstkonto (JWT Assertion)]**.
1. Geben Sie den **[!UICONTROL Anwendungsnamen]** ein.
1. Registrieren Sie den **[!UICONTROL öffentlichen Schlüssel]**.
1. Wählen Sie die **[!UICONTROL Perimeter]** des Auslösers aus.

   ![](assets/triggers_5.png)

1. Klicken Sie auf **[!UICONTROL Erstellen]** und überprüfen Sie die **[!UICONTROL Anwendungs-ID]** und den erstellten **[!UICONTROL Anwendungs-Geheimcode]**.

   ![](assets/triggers_6.png)

### Registrierung des Anwendungsnamens in Adobe Campaign Classic {#application-name-registration}

Die Anwendungs-ID des erstellten OAuth-Clients muss in Adobe Campaign konfiguriert werden. Bearbeiten Sie dazu die Konfigurationsdatei der Instanz im [!DNL pipelined]-Element, und zwar das Attribut &quot;appName&quot;.

Beispiel:

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### Verschlüsselung des Schlüssels {#key-encription}

Der private Schlüssel muss verschlüsselt werden, damit er von [!DNL pipelined] verwendet werden kann. Die Verschlüsselung erfolgt mit der JavaScript-Funktion &quot;cryptString&quot; und muss auf derselben Instanz wie [!DNL pipelined] vorgenommen werden.

Auf dieser [Seite](../../integrations/using/pipeline-troubleshooting.md) finden Sie ein Beispiel für die Verschlüsselung des privaten Schlüssels mit JavaScript.

Der verschlüsselte private Schlüssel muss in Adobe Campaign registriert werden. Bearbeiten Sie dazu die Konfigurationsdatei der Instanz im [!DNL pipelined]-Element, und zwar das Attribut &quot;authPrivateKey&quot;.

Beispiel:

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### Automatischer Start von Pipelined-Prozess {#pipelined-auto-start}

Der [!DNL pipelined]-Prozess muss automatisch gestartet werden.
Setzen Sie dazu das Element in der Konfigurationsdatei auf autostart=&quot;true&quot;:

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### Neustart von Pipelined-Prozess {#pipelined-restart}

Der Prozess kann über die Befehlszeile auch manuell gestartet werden:

```
nlserver start pipelined@instance
```

Ein Neustart ist erforderlich, damit die Änderungen wirksam werden:

```
nlserver restart pipelined@instance
```

Sollten Fehler auftreten, suchen Sie nach Fehlern in der Standardausgabe (wenn Sie manuell gestartet haben) oder in der [!DNL pipelined]-Log-Datei. Weitere Informationen zum Beheben von Problemen finden Sie im Abschnitt zur Fehlerbehebung in diesem Dokument.

### Optionen für die Pipelined-Konfiguration {#pipelined-configuration-options}

| Option | Beschreibung  |
|:-:|:-:|
| appName | Kennung der OAuth-Anwendung (Anwendungs-ID), in Adobe Analytics registriert (wo der öffentliche Schlüssel hochgeladen wurde): &quot;Admin&quot; > &quot;User Management&quot; > &quot;Veraltete OAuth-Anwendung&quot;. Siehe diesen [Abschnitt](../../integrations/using/configuring-pipeline.md#oauth-client-creation). |
| authGatewayEndpoint | URL zum Abrufen von &quot;Gateway-Tokens&quot;. <br> Standard: https://api.omniture.com |
| authPrivateKey | Privater Schlüssel (öffentlicher Teil wurde in Adobe Analytics hochgeladen (siehe diesen Abschnitt)). AES-Verschlüsselung mit der XtkSecretKey-Option xtk.session.EncryptPassword(&quot;PRIVATE_KEY&quot;); |
| disableAuth | Deaktivieren der Authentifizierung (Verbindungen ohne Gateway-Tokens werden nur von einigen Entwicklungs-Pipeline-Endpunkten akzeptiert) |
| discoverPipelineEndpoint | URL für die Ermittlung des Pipeline-Dienstendpunkts, der für diesen Mandanten verwendet werden soll. Standard: https://producer-pipeline-pnw.adobe.net |
| dumpStatePeriodSec | Der Zeitraum zwischen zwei Dumps des internen Prozessstatus in &quot;var/INSTANCE/pipelined.json&quot;. Der interne Status ist auch bei Bedarf abrufbar unter &quot;http://INSTANCE/pipelined/status&quot; (Port 7781). |
| forcedPipelineEndpoint | Deaktivieren der Erkennung und Erzwingen des PipelineServicesEndpoint |
| monitorServerPort | Der [!DNL pipelined]-Prozess prüft diesen Port, um den internen Prozessstatus unter „http://INSTANCE/pipelined/status“ bereitzustellen (Port 7781). |
| cursorFlushMessageCount | Sobald diese Anzahl von Nachrichten verarbeitet wurde, werden die Versätze in der Datenbank gespeichert. Der Standardwert ist 1.000. |
| cursorFlushPeriodSec | Nach diesem Zeitraum werden die Versätze in der Datenbank gespeichert. Der Standardwert ist 5 (Sekunden). |
| processingJSThreads | Anzahl der dedizierten Threads, die Nachrichten mit benutzerdefinierten JS-Connectoren verarbeiten. Der Standardwert ist 4. |
| processingThreads | Anzahl der dedizierten Threads, die Nachrichten mit nativem Code verarbeiten. Der Standardwert ist 4. |
| retryPeriodSec | Pause zwischen weiteren Zustellversuchen (bei Verarbeitungsfehlern). Der Standardwert ist 30 (Sekunden). |
| retryValiditySec | Verwerfen der Nachricht, wenn sie nach diesem Zeitraum nicht erfolgreich verarbeitet wurde (zu viele weitere Zustellversuche). Der Standardwert ist 300 (Sekunden). |

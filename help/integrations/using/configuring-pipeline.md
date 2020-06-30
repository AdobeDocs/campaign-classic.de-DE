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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 39d6da007d69f81da959660b24b56ba2558a97ba
workflow-type: tm+mt
source-wordcount: '944'
ht-degree: 2%

---


# Konfigurieren der Pipeline {#configuring-pipeline}

Authentifizierungsparameter wie die Kunden-ID, der private Schlüssel und der Authentifizierungs-Endpunkt werden in den Konfigurationsdateien der Instanz konfiguriert.
Die Liste der zu verarbeitenden Auslöser wird in einer Option konfiguriert. Es ist im JSON-Format.
Der Auslöser wird sofort mit JavaScript-Code verarbeitet. Es wird in einer Datenbanktabelle gespeichert, ohne dass die Verarbeitung in Echtzeit erfolgt.
Die Auslöser werden für das Targeting von einem Kampagnen-Workflow verwendet, der E-Mails sendet. Die Kampagne wird so eingerichtet, dass ein Kunde, der beide Ereignis auslöst, eine E-Mail erhält.

## Voraussetzungen {#prerequisites}

Die Verwendung [!DNL Experience Cloud Triggers] in Kampagne erfordert:

* Adobe Campaign Version 6.11 Build 8705 oder höher.
* Adobe Analytics Ultimate, Premium, Foundation, OD, Select, Prime, Mobile Apps, Select oder Standard.

Erforderliche Konfigurationen sind:

* Erstellen einer privaten Schlüsseldatei und dann die Erstellung der oAuth-Anwendung, die mit diesem Schlüssel registriert ist.
* Konfiguration der Auslöser in Adobe Analytics.

Die Adobe Analytics-Konfiguration fällt nicht in den Anwendungsbereich dieses Dokuments.

Für Adobe Campaign sind folgende Informationen von Adobe Analytics erforderlich:

* Der Name der Auth-Anwendung.
* Die IMSOrgId, die Kennung des Experience Cloud-Kunden.
* Die Namen der in Analytics konfigurierten Auslöser.
* Name und Format der Datenfelder, die mit der Marketing-Datenbank abgeglichen werden sollen.

Teil dieser Konfiguration ist eine benutzerdefinierte Entwicklung und erfordert Folgendes:

* Kenntnisse der JSON-, XML- und JavaScript-Analyse in Adobe Campaign.
* Kenntnisse der QueryDef- und Writer-APIs.
* Arbeitsbegriffe der Verschlüsselung und Authentifizierung mit privaten Schlüsseln.

>[!NOTE]
>
>Da die Bearbeitung des JS-Codes technische Fertigkeiten erfordert, sollten Sie ihn nicht ohne das entsprechende Verständnis versuchen. <br>Auslöser werden in einer Datenbanktabelle gespeichert. So können Auslöserdaten von Marketingunternehmen bei der Workflows sicher verwendet werden.

## Authentifizierungs- und Konfigurationsdateien {#authentication-configuration}

Die Authentifizierung ist erforderlich, da Pipeline in der Adobe Experience Cloud gehostet wird.
Wenn der Marketing-Server auf einer lokalen Plattform gehostet wird und sich bei der Pipeline anmeldet, muss er sich für eine sichere Verbindung authentifizieren.
Es verwendet ein Paar öffentlicher und privater Schlüssel. Dieser Vorgang ist dieselbe Funktion wie ein Benutzer/Kennwort, nur sicherer.

### IMSOrgId {#imsorgid}

Die IMSOrgId ist die ID des Kunden in der Adobe Experience Cloud.
Legen Sie sie in der Datei &quot;serverConf.xml&quot;unter dem Attribut &quot;IMSOrgId&quot;fest.
Beispiel:

```
<redirection IMSOrgId="C5E715(…)98A4@AdobeOrg" (…)
```

### Schlüsselgeneration {#key-generation}

Der Schlüssel ist ein Paar Dateien. Es ist im RSA-Format und 4096 Byte lang. Es kann mit einem Open-Source-Tool wie OpenSSL generiert werden. Bei jeder Ausführung des Tools wird ein neuer Schlüssel zufällig generiert.
Aus praktischen Gründen werden die folgenden Schritte beschrieben:

* ```openssl genrsa -out <private_key.pem> 4096```

* ```openssl rsa -pubout -in <private_key.pem> -out <public_key.pem>```

Beispiel für die Datei private_key.pem:

```
----BEGIN RSA PRIVATE KEY----
MIIEowIBAAKCAQEAtqcYzt5WGGABxUJSfe1Xy8sAALrfVuDYURpdgbBEmS3bQMDb
(…)
64+YQDOSNFTKLNbDd+bdAA+JoYwUCkhFyvrILlgvlSBvwAByQ2Lx
----END RSA PRIVATE KEY----
```

Beispiel für die Datei public_key.pem:

```
----BEGIN PUBLIC KEY----
MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAtqcYzt5WGGABxUJSfe1X
(…)
EwIDAQAB
----END PUBLIC KEY----
```

>[!NOTE]
>
>Schlüssel sollten nicht von PuttyGen generiert werden, OpenSSL ist die beste Wahl.

### Auth-Client-Erstellung in Adobe Experience Cloud {#oauth-client-creation}

Eine Anwendung des Typs JWT muss erstellt werden, indem Sie sich beim Adobe Analytics im richtigen Unternehmenskonto unter **[!UICONTROL Admin]** > **[!UICONTROL Benutzerverwaltung]** > **[!UICONTROL Legacy-Pfad-Anwendung]** anmelden.

Führen Sie folgende Schritte aus:

1. Wählen Sie das **[!UICONTROL Dienstkonto aus (JWT-Zusicherung)]**.
1. Geben Sie den **[!UICONTROL Anwendungsnamen]** ein.
1. Registrieren Sie den **[!UICONTROL öffentlichen Schlüssel]**.
1. Wählen Sie die **[!UICONTROL Scopes]** des Auslösers aus.

   ![](assets/triggers_5.png)

1. Klicken Sie auf **[!UICONTROL Erstellen]** und überprüfen Sie die **[!UICONTROL Anwendungs-ID]** und den **[!UICONTROL Anwendungs-Geheimcode]** erstellt.

   ![](assets/triggers_6.png)

### Registrierung des Anwendungsnamens in Adobe Campaign Classic {#application-name-registration}

Die Anwendungs-ID des erstellten Auth-Clients muss in Adobe Campaign konfiguriert werden. Dazu bearbeiten Sie die Konfigurationsdatei der Instanz im Pipeline-Element, insbesondere das Attribut appName.

Beispiel:

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### Schlüsselverschlüsselung {#key-encription}

Der private Schlüssel muss verschlüsselt sein, damit er in Pipelines verwendet werden kann. Die Verschlüsselung erfolgt mit der Javascript-Funktion cryptString und muss auf derselben Instanz wie per Pipeline ausgeführt werden.

Auf dieser [Seite](../../integrations/using/pipeline-troubleshooting.md)finden Sie ein Beispiel für die private Schlüsselverschlüsselung mit JavaScript.

Der verschlüsselte private Schlüssel muss in Adobe Campaign registriert sein. Sie können dies tun, indem Sie die Konfigurationsdatei der Instanz im Pipeline-Element bearbeiten, insbesondere das Attribut authPrivateKey.

Beispiel:

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### Automatischer Beginn für automatisierte Prozesse {#pipelined-auto-start}

Der Pipeline-Prozess muss automatisch gestartet werden.
Legen Sie dazu das Element in der Konfigurationsdatei auf autostart=&quot;true&quot; fest:

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### Wiederaufnahme des Pipelines-Prozesses {#pipelined-restart}

Sie kann auch manuell über die Befehlszeile gestartet werden:

```
nlserver start pipelined@instance
```

Ein Neustart ist erforderlich, damit die Änderungen wirksam werden:

```
nlserver restart pipelined@instance
```

Bei Fehlern suchen Sie nach Fehlern in der Standardausgabe (wenn Sie manuell gestartet haben) oder in der Pipeline-Protokolldatei. Weitere Informationen zum Beheben von Problemen finden Sie im Abschnitt Fehlerbehebung in diesem Dokument.

### Optionen für die geteilte Konfiguration {#pipelined-configuration-options}

| Option | Beschreibung |
|:-:|:-:|
| appName | ID der OAuth-Anwendung (Anwendungs-ID), die in Adobe Analytics registriert ist (wo der öffentliche Schlüssel hochgeladen wurde): Admin > Benutzerverwaltung > Ältere Anwendung. Refer to this [section](../../integrations/using/configuring-pipeline.md#oauth-client-creation). |
| authGatewayEndpoint | URL zum Abrufen von &quot;Gateway-Token&quot;. <br> Standard: https://api.omniture.com |
| authPrivateKey | Privater Schlüssel (öffentlicher Teil, der in Adobe Analytics hochgeladen wurde (siehe diesen Abschnitt). AES-Verschlüsselung mit der Option XtkSecretKey: xtk.session.EncryptPassword(&quot;PRIVATE_KEY&quot;); |
| disableAuth | Deaktivieren der Authentifizierung (die Verbindung ohne Gateway-Token wird nur von einigen Entwicklungs-Pipeline-Endpunkten akzeptiert) |
| discoverPipelineEndpoint | URL, um den Endpunkt der Pipeline-Dienste zu ermitteln, der für diesen Mieter verwendet werden soll. Standard: https://producer-pipeline-pnw.adobe.net |
| dumpStatePeriodSec | Der Zeitraum zwischen 2 Dumps des internen Prozesszustands in var/INSTANCE/pipelined.json Interne Status ist auch auf Abruf verfügbar unter http://INSTANCE/pipelined/status (Port 7781). |
| forcedPipelineEndpoint | Deaktivieren Sie die Erkennung des PipelineServicesEndpunkts und erzwingen Sie ihn |
| monitorServerPort | Der Pipeline-Prozess überwacht diesen Anschluss, um den internen Prozessstatus unter http://INSTANCE/pipelined/status (Port 7781) bereitzustellen. |
| cursorFlushMessageCount | Wenn diese Anzahl von Meldungen verarbeitet wird, werden die Offsets in der Datenbank gespeichert. Der Standardwert ist 1000 |
| cursorFlushPeriodSec | Nach diesem Zeitraum werden die Offsets in der Datenbank gespeichert. Der Standardwert ist 5 (Sekunden) |
| processingJSThreads | Anzahl der dedizierten Threads, die Meldungen mit benutzerdefinierten JS-Connectors verarbeiten. Standardwert ist 4 |
| processingThreads | Anzahl der dedizierten Threads, die Meldungen mit integriertem Code verarbeiten. Standardwert ist 4 |
| retryPeriodSec | Verzögerung zwischen weiteren Zustellversuchen (bei Verarbeitungsfehlern). Der Standardwert ist 30 (Sekunden) |
| retryValiditySec | Verwerfen Sie die Nachricht, wenn sie nach diesem Zeitraum nicht erfolgreich verarbeitet wurde (zu viele weitere Zustellversuche). Der Standardwert ist 300 (Sekunden) |

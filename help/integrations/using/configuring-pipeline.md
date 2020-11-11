---
title: Konfigurieren der Pipeline
description: Erfahren Sie, wie Sie die Pipeline konfigurieren
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
translation-type: tm+mt
source-git-commit: 2d0d2d4eefc67312e1b9a8edc7ae88def2980ef1
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 84%

---


# Pipeline konfigurieren {#configuring-pipeline}

Authentifizierungsparameter wie die Kunden-ID, der private Schlüssel und der Authentifizierungsendpunkt werden in den Konfigurationsdateien der Instanz konfiguriert.
Die Liste der zu verarbeitenden Auslöser wird in einer Option im JSON-Format konfiguriert.
Die Auslöser werden für die Zielgruppenbestimmung eines Kampagnen-Workflows verwendet, der E-Mails sendet. Die Kampagne ist so eingerichtet, dass ein Kunde, der beide Auslöserereignisse aufweist, eine E-Mail erhält.

>[!CAUTION]
>
>Bei Hybrid-Bereitstellungen muss die Pipeline auf einer Mid-Sourcing-Instanz konfiguriert sein.

## Voraussetzungen {#prerequisites}

Bevor Sie diese Konfiguration starten, überprüfen Sie, ob Sie Folgendes verwenden:

* Adobe Campaign 20.3 - Mindestversion
* Adobe Analytics Standard-Version

Sie benötigen außerdem:

* Projektauthentifizierung für Adobe-E/A
* eine gültige IMSOrgID, die Kennung des Experience Cloud-Kunden mit Adobe Analytics hinzugefügt
* einen Entwicklerzugriff auf das IMS-Org
* Triggerkonfiguration in Adobe Analytics ausgeführt

## Authentifizierung und Konfigurationsdateien {#authentication-configuration}

Da das Pipeline-Hosting in Adobe Experience Cloud erfolgt, ist eine Authentifizierung erforderlich.
Hierfür wird ein Schlüsselpaar aus öffentlichem und privatem Schlüssel verwendet. Der Prozess entspricht der Verwendung einer Kombination aus Benutzer und Passwort, ist aber sicherer.
Authentifizierung wird für das Marketing Cloud über das Adobe-I/O-Projekt unterstützt.

## Schritt 1: Erstellen/Aktualisieren des Adoben-E/A-Projekts {#creating-adobe-io-project}

Für gehostete Kunden können Sie ein Kundenbetreuungsticket erstellen, um Ihr Unternehmen mit Adobe-E/A-Token für die Triggerintegration zu aktivieren.

For On Premise customers, refer to the [Configuring Adobe I/O for Adobe Experience Cloud Triggers](../../integrations/using/configuring-adobe-io.md) page. Note that you need to select **[!UICONTROL Adobe Analytics]** while adding API to the Adobe I/O credential.

## Schritt 2: Konfigurieren der Pipeline-Option &quot;NmsPipeline_Config&quot; {#configuring-nmspipeline}

Sobald die Authentifizierung eingerichtet ist, ruft die Pipeline die Ereignisse ab. Sie verarbeitet nur Auslöser, die in Adobe Campaign konfiguriert wurden. Der Auslöser muss in Adobe Analytics generiert und an die Pipeline gesendet worden sein; diese verarbeitet nur Auslöser, die in Adobe Campaign konfiguriert wurden.
Die Option kann auch mit einem Platzhalter konfiguriert werden, um alle Auslöser unabhängig vom Namen zu erfassen.

1. Rufen Sie in Adobe Campaign über **[!UICONTROL Administration]** > **[!UICONTROL Plattform]** > **[!UICONTROL Optionen]** das Optionsmenü im **[!UICONTROL Explorer]** auf.

1. Wählen Sie die Option **[!UICONTROL NmsPipeline_Config]** aus.

1. Im Feld **[!UICONTROL Wert (Memo)]** können Sie den folgenden JSON-Code einfügen, der zwei Auslöser angibt. Die Kommentare müssen Sie dabei entfernen.

   ```
   {
   "topics": [ // list of "topics" that the pipelined is listening to.
      {
           "name": "triggers", // Name of the first topic: triggers.
           "consumer": "customer_dev", // Name of the instance that listens.  This value can be found on the monitoring page of Adobe Campaign.
           "triggers": [ // Array of triggers.
               {
                   "name": "3e8a2ba7-fccc-49bb-bdac-33ee33cf02bf", // TriggerType ID from Analytics 
                   "jsConnector": "cus:triggers.js" // Javascript library holding the processing function.
               }, {
                   "name": "2da3fdff-13af-4c51-8ed0-05802a572e94", // Second TriggerType ID 
                   "jsConnector": "cus:triggers.js" // Can use the same JS for all.
               },
           ]
       }
   ]
   }
   ```

1. Sie können auch folgenden JSON-Code einfügen, der alle Auslöser abdeckt.

   ```
   {
   "topics": [
     {
       "name": "triggers",
       "consumer":  "customer_dev",
       "triggers": [
         {
           "name": "*",
           "jsConnector": "cus:pipeline.js"
         }
       ]
     }
   ]
   }
   ```

### Der Parameter &quot;Consumer&quot; {#consumer-parameter}

Die Pipeline funktioniert wie ein Anbieter-Verbraucher-Modell. Nachrichten werden nur von einem einzelnen Verbraucher &quot;konsumiert&quot;; jeder Verbraucher erhält eine eigene Kopie der Nachrichten.

Der Parameter **Consumer** identifiziert die Instanz als einen dieser Verbraucher. Über die Identität der Instanz wird die Pipeline aufgerufen. Sie können für diese den Instanznamen angeben. Sie finden diesen auf der Seite &quot;Monitoring&quot; der Client-Konsole.

Der Pipeline-Dienst dokumentiert die von jedem Verbraucher abgerufenen Nachrichten. Indem Sie für verschiedene Instanzen jeweils unterschiedliche Verbraucher verwenden, stellen Sie sicher, dass jede Nachricht an jede Instanz gesendet wird.

### Empfehlungen für die Pipeline-Option {#pipeline-option-recommendation}

Für die Konfiguration der Pipeline-Option wird Folgendes empfohlen:

* Wenn Sie Auslöser bearbeiten oder hinzufügen, tun Sie dies unter **[!UICONTROL Auslöser]**; den Rest sollten Sie nicht bearbeiten.
* Vergewissern Sie sich, dass die JSON gültig ist. Verwenden Sie einen JSON-Validator, z. B. den auf dieser [Website](http://jsonlint.com/).
* &quot;name&quot; entspricht der Auslöser-ID. Ein Platzhalter (*) deckt alle Auslöser ab.
* &quot;Consumer&quot; entspricht dem Namen der aufrufenden Instanz oder Anwendung.
* Pipelined unterstützt auch das Thema &quot;Aliases&quot;.
* Starten Sie pipelined grundsätzlich neu, nachdem Sie Änderungen vorgenommen haben.

## Schritt 3: Optionale Konfiguration {#step-optional}

Sie können einige interne Parameter entsprechend Ihren Lastanforderungen ändern; stellen Sie jedoch sicher, dass Sie diese testen, bevor Sie sie in die Produktion übernehmen.

Die Liste der optionalen Parameter ist nachfolgend aufgeführt:

| Option | Beschreibung  |
|:-:|:-:|
| appName(Legacy) | AppID der OAuth-Anwendung, die in der Legacy-Oath-Anwendung registriert ist, in die der öffentliche Schlüssel hochgeladen wurde. Weitere Informationen hierzu finden Sie auf [dieser Seite](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md.). |
| authGatewayEndpoint(Legacy) | URL zum Abrufen von Gateway-Tokens. Standard: ```https://api.omniture.com``` |
| authPrivateKey(Legacy) | Der öffentliche Teil des privaten Schlüssels, der in die Legacy-Oath-Anwendung hochgeladen wurde; AES-verschlüsselt mit der XtkKey-Option: ```cryptString("PRIVATE_KEY")``` |
| disableAuth(Legacy) | Deaktivieren der Authentifizierung; Verbindungen ohne Gateway-Tokens werden nur von einigen Endpunkten der Entwicklungs-Pipeline akzeptiert. |
| discoverPipelineEndpoint | URL zum Auffinden des Pipeline-Dienstendpunkts, der für diesen Mandanten verwendet werden soll. Standard: ```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | Der Zeitraum zwischen der Speicherung zweier Kopien des internen Statusprozesses im ```var/INSTANCE/pipelined.json.``` <br> Der interne Status ist hier auch auf Abruf verfügbar: ```http://INSTANCE:7781/pipelined/status``` |
| forcedPipelineEndpoint | Deaktivieren der Erkennung und Erzwingen des PipelineServicesEndpoint |
| monitorServerPort | Der Pipelined-Prozess überwacht, dass der Port den internen Statusprozess hier bereitstellt: ```http://INSTANCE:PORT/pipelined/status```. <br>Der Standardwert ist 7781. |
| cursorFlushMessageCount | Sobald diese Anzahl von Nachrichten verarbeitet wurde, werden die Versätze in der Datenbank gespeichert. <br>Der Standardwert ist 1000. |
| cursorFlushPeriodSec | Nach diesem Zeitraum werden die Versätze in der Datenbank gespeichert. <br>Der Standardwert ist 5 (Sekunden). |
| processingJSThreads | Anzahl der dedizierten Threads, die Nachrichten mit benutzerdefinierten JS-Connectoren verarbeiten. <br>Der Standardwert ist 4. |
| processingThreads | Anzahl der dedizierten Threads, die Nachrichten mit nativem Code verarbeiten. <br>Der Standardwert ist 4. |
| retryPeriodSec | Verzögerung zwischen weiteren Zustellversuchen im Falle von Verarbeitungsfehlern. <br>Der Standardwert ist 30 (Sekunden). |
| retryValiditySec | Verwerfen der Nachricht, wenn sie nach diesem Zeitraum nicht erfolgreich verarbeitet wurde (zu viele weitere Zustellversuche). <br>Der Standardwert ist 300 (Sekunden). |

### Automatischer Start von Pipelined-Prozess {#pipelined-process-autostart}

Der Pipelined-Prozess muss automatisch gestartet werden.

Legen Sie dazu das Element &lt; pipelined > in der Konfigurationsdatei auf autostart=&quot;true&quot; fest:

```
 <pipelined autoStart="true" ... "/>
```

### Neustart von Pipelined-Prozess {#pipelined-process-restart}

Ein Neustart ist erforderlich, damit die Änderungen wirksam werden:

```
nlserver restart pipelined@instance
```

## Schritt 4: Validierung {#step-validation}

Gehen Sie wie folgt vor, um die Pipeline-Einrichtung für die Bereitstellung zu validieren:

* Vergewissern Sie sich, dass der [!DNL pipelined]-Prozess ausgeführt wird.
* Prüfen Sie die Pipeline-Verbindungsprotokolle in der Datei &quot;pipelined.log&quot;.
* Überprüfen Sie, ob die Verbindung besteht und Pings empfangen werden. Kunden gehosteter Bereitstellungen können über die Client-Konsole &quot;Monitoring&quot; verwenden.

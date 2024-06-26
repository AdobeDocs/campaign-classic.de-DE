---
product: campaign
title: Konfigurieren der Pipeline
description: Erfahren Sie, wie Sie die Pipeline für die Integration von Campaign mit Triggers konfigurieren
feature: Triggers
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: integrations
content-type: reference
exl-id: 2d214c36-8429-4b2b-b1f5-fe2730581bba
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: ht
source-wordcount: '844'
ht-degree: 100%

---

# Konfigurieren der Pipeline {#configuring-pipeline}

Authentifizierungsparameter wie die Kunden-ID, der private Schlüssel und der Authentifizierungsendpunkt werden in den Konfigurationsdateien der Instanz konfiguriert.

Die Liste der zu verarbeitenden Trigger wird in einer Option im JSON-Format konfiguriert.

Die Auslöser werden für die Zielgruppenbestimmung eines Kampagnen-Workflows verwendet, der E-Mails sendet. Die Kampagne ist so eingerichtet, dass ein Kunde, der beide Auslöserereignisse aufweist, eine E-Mail erhält.

## Voraussetzungen {#prerequisites}

Bevor Sie mit der Konfiguration beginnen, überprüfen Sie bitte, ob Folgendes vorhanden ist:

* Ein Adobe Developer-Projekt
* Eine gültige Organisations-ID – auf [dieser Seite](https://experienceleague.adobe.com/de/docs/core-services/interface/administration/organizations#concept_EA8AEE5B02CF46ACBDAD6A8508646255){_blank} erfahren Sie, wie Sie Ihre Organisations-ID finden
* Ein Entwicklerzugriff auf die Organisation
* Eine gültige Trigger-Konfiguration in Adobe Analytics

Da das Pipeline-Hosting in Adobe Experience Cloud erfolgt, ist eine Authentifizierung erforderlich. Es wird eine Authentifizierung verwendet, die über ein Adobe Developer-Projekt unterstützt wird.

## Schritt 1: Erstellen/Aktualisieren Ihres Adobe Developer-Projekts {#creating-adobe-io-project}

Sie müssen Ihre Organisation mit Adobe Developer-Konto-Token aktivieren, um die Triggers-Integration zu ermöglichen.

Auf [dieser Seite](../../integrations/using/oauth-technical-account.md) erfahren Sie, wie Sie Ihr technisches Adobe-Konto erstellen. Beachten Sie, dass Sie beim Hinzufügen einer API zu den Adobe Developer-Anmeldedaten **[!UICONTROL Adobe Analytics]** auswählen müssen.

## Schritt 2: Konfigurieren der Pipeline-Option {#configuring-nmspipeline}

Sobald die Authentifizierung eingerichtet ist, ruft die Pipeline die Ereignisse ab. Sie verarbeitet nur Trigger, die in Adobe Campaign konfiguriert wurden. Der Trigger muss in Adobe Analytics generiert und an die Pipeline gesendet worden sein. Diese verarbeitet nur Trigger, die in Adobe Campaign konfiguriert wurden.

Die Option kann auch mit einem Platzhalter konfiguriert werden, um alle Auslöser unabhängig vom Namen zu erfassen.

1. Rufen Sie in Adobe Campaign über **[!UICONTROL Administration]** > **[!UICONTROL Plattform]** > **[!UICONTROL Optionen]** das Optionsmenü im **[!UICONTROL Explorer]** auf.

1. Wählen Sie die Option **[!UICONTROL NmsPipeline_Config]** aus.

1. Im Feld **[!UICONTROL Wert (Memo)]** können Sie den folgenden JSON-Code einfügen, der zwei Auslöser angibt. Entfernen Sie unbedingt die Kommentare.

   ```json
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

1. Sie können auch folgenden JSON-Code einfügen, der alle Trigger abdeckt.

   ```json
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

### Festlegen des Parameters „Consumer“  {#consumer-parameter}

Die Pipeline funktioniert wie ein Anbieter-Verbraucher-Modell. Nachrichten werden nur von einem einzelnen Verbraucher &quot;konsumiert&quot;; jeder Verbraucher erhält eine eigene Kopie der Nachrichten.

Der Parameter **Consumer** identifiziert die Instanz als einen dieser Verbraucher. Über die Identität der Instanz wird die Pipeline aufgerufen. Sie können für diese den Instanznamen angeben. Sie finden diesen auf der Seite &quot;Monitoring&quot; der Client-Konsole.

Der Pipeline-Dienst dokumentiert die von jedem Verbraucher abgerufenen Nachrichten. Indem Sie für verschiedene Instanzen jeweils unterschiedliche Verbraucher verwenden, stellen Sie sicher, dass jede Nachricht an jede Instanz gesendet wird.

### Empfehlungen für die Pipeline-Option {#pipeline-option-recommendation}

Für die Konfiguration der Pipeline-Option wird Folgendes empfohlen:

* Hinzufügen oder Bearbeiten von Triggern unter **[!UICONTROL Triggers]**.
* Vergewissern Sie sich, dass die JSON gültig ist.
* Der Parameter **Name** entspricht der Trigger-ID. Ein Platzhalter (*) deckt alle Trigger ab.
* Der Parameter **Consumer** entspricht dem Namen der aufrufenden Instanz oder Anwendung.
* Der Prozess `pipelined` unterstützt auch das Thema „Alias“.
* Starten Sie den Prozess `pipelined` grundsätzlich neu, nachdem Sie Änderungen vorgenommen haben.

## Schritt 3 (optional): Zusätzliche Konfiguration {#step-optional}

Sie können einige interne Parameter entsprechend Ihren Lastanforderungen ändern, aber stellen Sie sicher, dass Sie sie testen, bevor Sie sie in Ihrer Produktionsumgebung anwenden.

Die Liste der optionalen Parameter lautet:

| Option | Beschreibung  |
|:-:|:-:|
| appName (frühere Version) | AppID der OAuth-Anwendung, die in der Legacy-Oath-Anwendung registriert ist, in die der öffentliche Schlüssel hochgeladen wurde. Weitere Informationen hierzu finden Sie auf [dieser Seite](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md). |
| authGatewayEndpoint(Legacy) | URL zum Abrufen von Gateway-Tokens. Standard: ```https://api.omniture.com``` |
| authPrivateKey(Legacy) | Der öffentliche Teil des privaten Schlüssels, der in die Legacy-Oath-Anwendung hochgeladen wurde; AES-verschlüsselt mit der XtkKey-Option: ```cryptString("PRIVATE_KEY")``` |
| disableAuth(Legacy) | Deaktivieren der Authentifizierung; Verbindungen ohne Gateway-Tokens werden nur von einigen Endpunkten der Entwicklungs-Pipeline akzeptiert. |
| discoverPipelineEndpoint | URL zum Auffinden des Pipeline-Dienstendpunkts, der für diesen Mandanten verwendet werden soll. Standard: ```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | Der Zeitraum zwischen der Speicherung zweier Kopien des internen Statusprozesses im ```var/INSTANCE/pipelined.json.``` <br> Der interne Status ist hier auch auf Abruf verfügbar: ```http://INSTANCE:7781/pipelined/status``` |
| forcedPipelineEndpoint | Deaktivieren der Erkennung und Erzwingen des PipelineServicesEndpoint |
| monitorServerPort | Der Pipelined-Prozess überwacht, dass der Port den internen Statusprozess hier bereitstellt: ```http://INSTANCE:PORT/pipelined/status```. <br>Der Standardwert ist 7781. |
| pointerFlushMessageCount | Sobald diese Anzahl von Nachrichten verarbeitet wurde, werden die Versätze in der Datenbank gespeichert. <br>Der Standardwert ist 1000. |
| pointerFlushPeriodSec | Nach diesem Zeitraum werden die Versätze in der Datenbank gespeichert. <br>Der Standardwert ist 5 (Sekunden). |
| processingJSThreads | Anzahl der dedizierten Threads, die Nachrichten mit benutzerdefinierten JS-Connectoren verarbeiten. <br>Der Standardwert ist 4. |
| processingThreads | Anzahl der dedizierten Threads, die Nachrichten mit nativem Code verarbeiten. <br>Der Standardwert ist 4. |
| retryPeriodSec | Verzögerung zwischen weiteren Zustellversuchen im Falle von Verarbeitungsfehlern. <br>Der Standardwert ist 30 (Sekunden). |
| retryValiditySec | Verwerfen der Nachricht, wenn sie nach diesem Zeitraum nicht erfolgreich verarbeitet wurde (zu viele weitere Zustellversuche). <br>Der Standardwert ist 300 (Sekunden). |

### Automatischer Start des Pipelined-Prozesses {#pipelined-process-autostart}

Der Prozess `pipelined` muss automatisch gestartet werden.

Legen Sie dazu das Element `<`pipelined`>` in der Konfigurationsdatei auf autostart=&quot;true&quot; fest:

```sql
 <pipelined autoStart="true" ... "/>
```

### Neustart des Pipelined-Prozesses {#pipelined-process-restart}

Ein Neustart ist erforderlich, damit die Änderungen wirksam werden:

```sql
nlserver restart pipelined@instance
```

## Schritt 4: Validierung {#step-validation}

Gehen Sie wie folgt vor, um die Pipeline-Einrichtung für die Bereitstellung zu validieren:

* Vergewissern Sie sich, dass der `pipelined`-Prozess ausgeführt wird.
* Überprüfen Sie die Datei `pipelined.log` auf Pipeline-Verbindungsprotokolle.
* Überprüfen Sie, ob die Verbindung besteht und Pings empfangen werden. Kunden gehosteter Bereitstellungen können über die Client-Konsole &quot;Monitoring&quot; verwenden.

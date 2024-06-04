---
product: campaign
title: Pipeline konfigurieren
description: Erfahren Sie, wie Sie die Pipeline für die Integration von Campaign mit Trigger konfigurieren
feature: Triggers
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: integrations
content-type: reference
exl-id: 2d214c36-8429-4b2b-b1f5-fe2730581bba
source-git-commit: 271e0f9fde0cbfb016e201c8390b26673d8fc696
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 63%

---

# Pipeline konfigurieren {#configuring-pipeline}

Authentifizierungsparameter wie die Kunden-ID, der private Schlüssel und der Authentifizierungsendpunkt werden in den Konfigurationsdateien der Instanz konfiguriert.

Die Liste der zu verarbeitenden Trigger wird in einer Option im JSON-Format konfiguriert.

Die Auslöser werden für die Zielgruppenbestimmung eines Kampagnen-Workflows verwendet, der E-Mails sendet. Die Kampagne ist so eingerichtet, dass ein Kunde, der beide Auslöserereignisse aufweist, eine E-Mail erhält.

## Voraussetzungen {#prerequisites}

Bevor Sie mit dieser Konfiguration beginnen, überprüfen Sie, ob folgende Voraussetzungen gegeben sind:

* Ein Adobe Developer-Projekt
* Eine gültige Organisations-ID - Informationen zum Auffinden Ihrer Organisations-ID finden Sie unter [diese Seite](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/organizations#concept_EA8AEE5B02CF46ACBDAD6A8508646255){_blank}
* Entwicklerzugriff auf Ihre Organisation
* Gültige Trigger-Konfiguration in Adobe Analytics

## Authentifizierung und Konfigurationsdateien {#authentication-configuration}

Die Authentifizierung ist erforderlich, da die Pipeline in der Adobe Experience Cloud gehostet wird. Hierfür wird ein Schlüsselpaar aus öffentlichem und privatem Schlüssel verwendet. Dieser Prozess hat dieselbe Funktion wie ein Benutzer/Kennwort, ist jedoch sicherer. Die Authentifizierung für das Marketing Cloud wird über das Adobe Developer-Projekt unterstützt.

## Schritt 1: Erstellen/Aktualisieren Sie Ihr Adobe Developer-Projekt {#creating-adobe-io-project}

Wenden Sie sich bei gehosteten Kunden an Ihren Adobe-Support-Mitarbeiter/an die Kundenunterstützung, um Ihre Organisation mit Adobe Developer-Konto-Token für die Trigger-Integration zu aktivieren.

On-Premise-/Hybrid-Kunden finden Informationen hierzu im Abschnitt [Adobe I/O für Adobe Experience Cloud Triggers konfigurieren](../../integrations/using/configuring-adobe-io.md) Seite. Beachten Sie, dass Sie **[!UICONTROL Adobe Analytics]** beim Hinzufügen der API zur Adobe Developer-Berechtigung.

## Schritt 2: Pipeline-Option konfigurieren {#configuring-nmspipeline}

Sobald die Authentifizierung eingerichtet ist, ruft die Pipeline die Ereignisse ab. Sie verarbeitet nur Auslöser, die in Adobe Campaign konfiguriert wurden. Der Trigger muss aus Adobe Analytics generiert und an die Pipeline gesendet worden sein, die nur Trigger verarbeitet, die in Adobe Campaign konfiguriert sind.

Die Option kann auch mit einem Platzhalter konfiguriert werden, um alle Auslöser unabhängig vom Namen zu erfassen.

1. Rufen Sie in Adobe Campaign über **[!UICONTROL Administration]** > **[!UICONTROL Plattform]** > **[!UICONTROL Optionen]** das Optionsmenü im **[!UICONTROL Explorer]** auf.

1. Wählen Sie die Option **[!UICONTROL NmsPipeline_Config]** aus.

1. Im Feld **[!UICONTROL Wert (Memo)]** können Sie den folgenden JSON-Code einfügen, der zwei Auslöser angibt. Die Kommentare müssen Sie dabei entfernen.

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

1. Sie können auch folgenden JSON-Code einfügen, der alle Auslöser abdeckt.

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

### Legen Sie den Parameter &quot;Consumer&quot;fest {#consumer-parameter}

Die Pipeline funktioniert wie ein Anbieter-Verbraucher-Modell. Nachrichten werden nur von einem einzelnen Verbraucher &quot;konsumiert&quot;; jeder Verbraucher erhält eine eigene Kopie der Nachrichten.

Der Parameter **Consumer** identifiziert die Instanz als einen dieser Verbraucher. Über die Identität der Instanz wird die Pipeline aufgerufen. Sie können für diese den Instanznamen angeben. Sie finden diesen auf der Seite &quot;Monitoring&quot; der Client-Konsole.

Der Pipeline-Dienst dokumentiert die von jedem Verbraucher abgerufenen Nachrichten. Indem Sie für verschiedene Instanzen jeweils unterschiedliche Verbraucher verwenden, stellen Sie sicher, dass jede Nachricht an jede Instanz gesendet wird.

### Empfehlungen für die Pipeline-Option {#pipeline-option-recommendation}

Für die Konfiguration der Pipeline-Option wird Folgendes empfohlen:

* Hinzufügen oder Bearbeiten von Triggern unter **[!UICONTROL Trigger]**.
* Vergewissern Sie sich, dass die JSON gültig ist.
* Die **Name** -Parameter der Trigger-ID entspricht. Ein Platzhalter (*) deckt alle Auslöser ab.
* Die **Verbraucher** -Parameter dem Namen der aufrufenden Instanz oder Anwendung entspricht.
* die `pipelined`-Prozess unterstützt auch das Thema &quot;Aliase&quot;.
* Sie sollten immer neu starten `pipelined`verarbeiten, nachdem Sie Änderungen vorgenommen haben.

## Schritt 3: Optionale Konfiguration {#step-optional}

Sie können einige interne Parameter entsprechend Ihren Ladeanforderungen ändern. Stellen Sie jedoch sicher, dass Sie diese testen, bevor Sie sie auf Ihre Produktionsumgebung anwenden.

Die Liste optionaler Parameter lautet:

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

Die `pipelined` -Prozess automatisch gestartet werden.

Legen Sie dazu die `<`pipelined`>` -Element in der Konfigurationsdatei zu autostart=&quot;true&quot;:

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
* Überprüfen Sie die `pipelined.log` für Pipeline-Verbindungsprotokolle.
* Überprüfen Sie, ob die Verbindung besteht und Pings empfangen werden. Kunden gehosteter Bereitstellungen können über die Client-Konsole &quot;Monitoring&quot; verwenden.

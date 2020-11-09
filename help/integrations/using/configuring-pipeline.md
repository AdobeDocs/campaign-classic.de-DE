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
source-git-commit: 4f949d8db3aa3082acf1765bf66080b270cc6db4
workflow-type: tm+mt
source-wordcount: '921'
ht-degree: 20%

---


# Pipeline konfigurieren {#configuring-pipeline}

Authentifizierungsparameter wie die Kunden-ID, der private Schlüssel und der Authentifizierungsendpunkt werden in den Konfigurationsdateien der Instanz konfiguriert.
Die Liste der zu verarbeitenden Auslöser wird in einer Option im JSON-Format konfiguriert.
Die Auslöser werden für das Targeting eines Kampagnen-Workflows verwendet, der E-Mails sendet. Die Kampagne ist so eingerichtet, dass ein Kunde, der beide Auslöserereignisse aufweist, eine E-Mail erhält.

>[!CAUTION]
>
>Bei einer Hybrid-Bereitstellung müssen Sie sicherstellen, dass die Pipeline auf einer Mid-Instanz konfiguriert ist.

## Voraussetzungen {#prerequisites}

Bevor Sie diese Konfiguration starten, überprüfen Sie bitte, ob Sie:

* eine aktuelle Version von Adobe Campaign (20.2.1 und höher),
* Adobe Analytics Standard-Version

Sie benötigen außerdem:

* Projektauthentifizierung für Adobe-E/A
* eine gültige IMSOrgID, die Kennung des Experience Cloud-Kunden mit Adobe Analytics hinzugefügt
* einen Entwicklerzugriff auf das IMS-Org
* Triggerkonfiguration in Adobe Analytics ausgeführt

## Authentifizierungs- und Konfigurationsdateien {#authentication-configuration}

Die Authentifizierung ist erforderlich, da die Pipeline im Adobe Experience Cloud gehostet wird.
Er verwendet ein Schlüsselpaar aus öffentlichem und privatem Schlüssel. Dieser Prozess hat die gleiche Funktion wie ein Benutzer/Kennwort, ist aber sicherer.
Authentifizierung wird für das Marketing Cloud über das Adobe-I/O-Projekt unterstützt.

## Schritt 1: Erstellen/Aktualisieren des Adoben-E/A-Projekts {#creating-adobe-io-project}

Für gehostete Kunden können Sie ein Kundenbetreuungsticket erstellen, um Ihr Unternehmen mit Adobe-E/A-Token für die Triggerintegration zu aktivieren.

Kunden, die über On Premise verfügen, finden Informationen auf der Seite [Konfigurieren der Adoben-E/A für Adobe Experience Cloud-Auslöser](../../integrations/using/configuring-adobe-io.md) . Beachten Sie, dass Sie beim Hinzufügen der API zur Adobe-E/A-Berechtigung **[!UICONTROL Adobe Analytics]** auswählen müssen.

## Schritt 2: Konfigurieren der Pipeline-Option &quot;NmsPipeline_Config&quot; {#configuring-nmspipeline}

Sobald die Authentifizierung festgelegt ist, ruft Pipeline die Ereignis ab. Es verarbeitet nur Auslöser, die in Adobe Campaign konfiguriert sind. Der Auslöser muss aus Adobe Analytics generiert und an die Pipeline gesendet worden sein, die nur Auslöser verarbeitet, die in Adobe Campaign konfiguriert sind.
Die Option kann auch mit einer Platzhalterkarte konfiguriert werden, um alle Auslöser unabhängig vom Namen abzurufen.

1. Rufen Sie in Adobe Campaign das Menü &quot;Optionen&quot;unter **[!UICONTROL Administration]** > **[!UICONTROL Plattform]** > **[!UICONTROL Optionen]** im **[!UICONTROL Explorer]** auf.

1. Wählen Sie die Option **[!UICONTROL NmsPipeline_Config]** .

1. Im Feld **[!UICONTROL Wert (langer Text)]** können Sie den folgenden JSON-Code einfügen, der zwei Auslöser angibt. Sie müssen sicherstellen, dass Kommentare entfernt werden.

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

1. Sie können auch den folgenden JSON-Code einfügen, der alle Auslöser erfasst.

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

### The Consumer parameter {#consumer-parameter}

Die Pipeline funktioniert wie ein Lieferant- und Verbrauchermodell. Nachrichten werden nur für einen einzelnen Verbraucher verwendet: jeder Verbraucher erhält seine eigene Kopie der Nachrichten.

The **Consumer** parameter identifies the instance as one of these consumers. Die Identität der Instanz nennt die Pipeline. Sie können ihn mit dem Instanznamen füllen, der auf der Überwachungsseite der Client-Konsole angezeigt wird.

Der Pipeline-Dienst verfolgt die von jedem Verbraucher abgerufenen Nachrichten. Durch die Verwendung unterschiedlicher Konsumenten für verschiedene Instanzen können Sie sicherstellen, dass jede Nachricht an jede Instanz gesendet wird.

### Empfehlungen für Pipeline-Optionen {#pipeline-option-recommendation}

Um die Pipeline-Option zu konfigurieren, sollten Sie folgende Empfehlungen befolgen:

* hinzufügen oder bearbeiten Sie Auslöser unter **[!UICONTROL Auslöser]**, sollten Sie den Rest nicht bearbeiten.
* Vergewissern Sie sich, dass JSON gültig ist. Sie können einen JSON-Validator verwenden, z. B. auf dieser [Website](http://jsonlint.com/) .
* &quot;name&quot;entspricht der Auslöser-ID. Ein Platzhalter (*) erfasst alle Auslöser.
* &quot;Consumer&quot;entspricht dem Namen der aufrufenden Instanz oder Anwendung.
* Pipelinated unterstützt auch das Thema &quot;Aliase&quot;.
* Sie sollten die Pipeline immer neu starten, nachdem Sie Änderungen vorgenommen haben.

## Schritt 3: Optionale Konfiguration {#step-optional}

Sie können einige interne Parameter entsprechend Ihren Ladefehlern ändern, stellen Sie jedoch sicher, dass Sie diese testen, bevor Sie sie in die Produktion übernehmen.

Die Liste der optionalen Parameter ist nachfolgend aufgeführt:

| Option | Beschreibung  |
|:-:|:-:|
| appName(Veraltet) | AppID der OAuth-Anwendung, die in der Legacy Oath-Anwendung registriert ist, in die der öffentliche Schlüssel hochgeladen wurde. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md.). |
| authGatewayEndpoint(Legacy) | URL zum Abrufen von Gateway-Token. Standard: ```https://api.omniture.com``` |
| authPrivateKey(Legacy) | Der private Schlüssel, öffentlicher Teil, der in die Legacy Oath-Anwendung hochgeladen wurde, AES mit der XtkKey-Option verschlüsselt: ```cryptString("PRIVATE_KEY")``` |
| disableAuth(Legacy) | Deaktivieren Sie die Authentifizierung, indem Sie eine Verbindung ohne Gateway-Token herstellen, wird nur von einigen Entwicklungs-Pipeline-Endpunkten akzeptiert. |
| discoverPipelineEndpoint | URL, um den Endpunkt der Pipeline-Dienste zu finden, der für diesen Mieter verwendet werden soll. Standard: ```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | Der Zeitraum zwischen zwei Deponien des internen Zustandsprozesses im ```var/INSTANCE/pipelined.json.```<br> Binnenstaat ist auch auf Abruf verfügbar: ```http://INSTANCE:7781/pipelined/status``` |
| forcedPipelineEndpoint | Deaktivieren Sie die Erkennung des PipelineServicesEndpunkts, um ihn zu erzwingen |
| monitorServerPort | Der Pipeline-Prozess überwacht diesen Anschluss, um den internen Zustandsprozess hier bereitzustellen: ```http://INSTANCE:PORT/pipelined/status```. <br>Der Standardwert ist 7781. |
| cursorFlushMessageCount | Wenn diese Anzahl von Nachrichten verarbeitet wird, werden die Offsets in der Datenbank gespeichert. <br>Der Standardwert ist 1000. |
| cursorFlushPeriodSec | Nach diesem Zeitraum werden die Versätze in der Datenbank gespeichert. <br>Der Standardwert ist 5 (Sekunden). |
| processingJSThreads | Anzahl der dedizierten Threads, die Nachrichten mit benutzerdefinierten JS-Connectoren verarbeiten. <br>Der Standardwert ist 4. |
| processingThreads | Anzahl der dedizierten Threads, die Nachrichten mit nativem Code verarbeiten. <br>Der Standardwert ist 4. |
| retryPeriodSec | Bei Verarbeitungsfehlern kann es zu Verzögerungen zwischen weiteren Zustellversuchen kommen. <br>Der Standardwert ist 30 (Sekunden). |
| retryValiditySec | Verwerfen der Nachricht, wenn sie nach diesem Zeitraum nicht erfolgreich verarbeitet wurde (zu viele weitere Zustellversuche). <br>Der Standardwert ist 300 (Sekunden). |

### Automatischer Start von Pipelined-Prozess {#pipelined-process-autostart}

Der Pipeline-Prozess muss automatisch gestartet werden.

Legen Sie dazu das Element &lt; pipelinated > in der Konfigurationsdatei auf autostart=&quot;true&quot; fest:

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

* Make sure the [!DNL pipelined] process is running.
* Überprüfen Sie die Datei &quot;pipelinated.log&quot;auf Protokolle zur Pipeline-Verbindung.
* Überprüfen Sie die Verbindung und ob Pings empfangen werden. Gehostete Kunden können die Überwachung über die Client-Konsole verwenden.

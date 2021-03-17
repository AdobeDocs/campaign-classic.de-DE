---
solution: Campaign Classic
product: campaign
title: Interaction - Datenpuffer
description: Interaction - Datenpuffer
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: d88815e36f7be1b010dcaeee51013a5da769b4a8
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 7%

---


# Interaction - Datenpuffer{#interaction-data-buffer}

Sie können eine Datenpufferzone konfigurieren, um die Interaktionsleistung zu erhöhen, indem Sie Angebotsvorschlag-Berechnungen deaktivieren. Diese Konfiguration wird in der eigenen Konfigurationsdatei der Instanz (config-Instance.xml) durchgeführt.

In Adobe Campaign wurde eine Datenpufferzone **im Interaktionsmodul eingeführt.** Auf diese Weise können Sie **die Leistung** der eingehenden Interaktion durch Desynchronisierung der Bestand- und Angebot-Berechnungen erhöhen.

Es betrifft nur die eingehende Interaktion, ob durch einen Aufruf (mit oder ohne Aufrufdaten) oder durch ein Statusupdate (updateStatus).

Um eine Warteschlange beim Schreiben von Vorschlägen für einen Empfänger zu vermeiden, generiert ein neuer w-Prozess eine **Datenpufferzone**, die es erlaubt, Vorschläge asynchron zu schreiben **und zu schreiben.** Diese Datenpufferzone wird regelmäßig gelesen und geleert. Der Standardzeitraum liegt bei etwa einer Sekunde. Daher ist das Schreiben von Vorschlägen gruppiert.

>[!NOTE]
>
>Diese Konfiguration ist zwingend erforderlich, wenn Sie Interaction in einer verteilten Architektur verwenden.

Die Datenpufferzone **configuration** kann in der Konfigurationsdatei der Instanz vorgenommen werden (config-Instance.xml).

>[!CAUTION]
>
>Einige Konfigurationen können nur von der Adobe für Bereitstellungen ausgeführt werden, die von der Adobe gehostet werden. So können Sie beispielsweise auf die Konfigurationsdateien des Servers und der Instanz zugreifen. Weitere Informationen zu den verschiedenen Bereitstellungen finden Sie im Abschnitt [Hosting models](../../installation/using/hosting-models.md) oder auf [dieser Seite](../../installation/using/capability-matrix.md).
>
>Änderungen, die an der Konfiguration vorgenommen werden, erfordern einen Neustart des Webservers (Apache:IIS) und der Adobe Campaign-Prozesse.\
>Stellen Sie nach der Konfiguration der Datenpufferzone sicher, dass eine angepasste Hardwarekonfiguration verfügbar ist. (Speicherkapazität vorhanden).


Stellen Sie nach der Konfiguration der Datenpufferzone sicher, dass eine angepasste Hardwarekonfiguration verfügbar ist. (Speicherkapazität vorhanden).

Die Definition für einen SchreibDaemon (Prozess mit dem Namen: Interaktion) wie folgt:

```
<interactiond args="" autoStart="false" callDataSize="0" initScript="" maxProcessMemoryAlertMb="1800"
maxProcessMemoryWarningMb="1600" maxSharedEntries="25000" nextOffersSize="0"
processRestartTime="06:00:00" runLevel="10" targetKeySize="16"/>
```

Wenn Sie Inbound Interaction verwenden, muss das @autostart-Attribut &quot;true&quot;sein, damit der Vorgang beim Starten des Adobe Campaign-Servers automatisch gestartet wird.

Argumentdetails:

```
 args: Start-up parameters 
 autoStart: Automatic start Default: false 
 callDataSize: Max. number of characters stored in the shared memory for call data
 Default: 0 
 initScript: ID of JavaScript to execute when starting the process 
 maxProcessMemoryAlertMb: Alert concerning the amount of RAM consumed (in Mb) by a given process Default: 1800 
 maxProcessMemoryWarningMb: Warning concerning the amount of RAM consumed (in Mb) by a given process Default: 1600 
 maxSharedEntries: Max. number of events stored in the shared memory. Default: 25000 
 nextOffersSize: Maximum number of eligible offers sorted right after propositions, to be stored for statistics Default: 0 
 processRestartTime: Time of the day when the process is automatically restartedDefault: '06:00:00' 
 runLevel: Priority at start Default: 10 
 targetKeySize: Max. number of characters stored in the shared memory for identifying individuals Default: 16 
```


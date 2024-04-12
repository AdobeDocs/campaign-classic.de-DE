---
product: campaign
title: Interaction - Datenpuffer
description: Interaction - Datenpuffer
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 7250b885-0606-466a-bfc2-6dd3cc5a012d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 4%

---

# Interaction - Datenpuffer{#interaction-data-buffer}



Sie können eine Pufferzone konfigurieren, um die Leistung von Interaction in das Eingangspuffersystem zu erhöhen, indem Sie die Synchronisierung der Angebotsvorschlagsberechnungen aufheben. Diese Konfiguration erfolgt in der Konfigurationsdatei der Instanz (config-Instance.xml).

In Adobe Campaign **Pufferspeicher-Zone** wurde im Interaction-Modul eingeführt. Auf diese Weise können Sie **Steigerung der Leistung** der eingehenden Interaction durch die Aufhebung der Synchronisation der Bestands- und Angebotsberechnungen.

Dies betrifft nur eingehende Interaktionen, sei es durch einen Aufruf (mit oder ohne Aufrufdaten) oder durch ein Statusupdate (updateStatus).

Um beim Schreiben von Vorschlägen für einen Empfänger eine Warteschlange zu vermeiden, generiert ein neuer Prozess eine **Pufferspeicher-Zone** , die Vorschläge ermöglicht, **asynchron geschrieben**. Diese Pufferzone wird regelmäßig gelesen und geleert. Der Standardzeitraum beträgt ca. eine Sekunde. Daher wird die Schreibweise des Vorschlags gruppiert.

>[!NOTE]
>
>Diese Konfiguration ist zwingend erforderlich, wenn Sie Interaction in einer verteilten Architektur verwenden.

Pufferspeicher-Zone **Konfiguration** kann in der Konfigurationsdatei der Instanz ausgeführt werden (config-Instance.xml).

>[!CAUTION]
>
>Einige Konfigurationen können nur von Adobe für Bereitstellungen durchgeführt werden, die von Adobe gehostet werden. Beispielsweise um auf die Server- und Instanzkonfigurationsdateien zuzugreifen. Weitere Informationen zu den verschiedenen Implementierungen finden Sie im Abschnitt [Hosting-Modelle](../../installation/using/hosting-models.md) oder [diese Seite](../../installation/using/capability-matrix.md).
>
>Änderungen an der Konfiguration erfordern einen Neustart des Webservers (Apache:IIS) und der Adobe Campaign-Prozesse.\
>Stellen Sie nach der Konfiguration der Pufferzone sicher, dass eine angepasste Hardware-Konfiguration verfügbar ist. (Speicherkapazität vorhanden).


Stellen Sie nach der Konfiguration der Pufferzone sicher, dass eine angepasste Hardware-Konfiguration verfügbar ist. (Speicherkapazität vorhanden).

Die Definition für einen SchreibDaemon (Prozess namens Interaktion) lautet wie folgt:

```
<interactiond args="" autoStart="false" callDataSize="0" initScript="" maxProcessMemoryAlertMb="1800"
maxProcessMemoryWarningMb="1600" maxSharedEntries="25000" nextOffersSize="0"
processRestartTime="06:00:00" runLevel="10" targetKeySize="16"/>
```

Wenn Sie &quot;Eingehende Interaktion&quot;verwenden, muss das Attribut @autostart &quot;true&quot;sein, damit der Prozess beim Start des Adobe Campaign-Servers automatisch gestartet wird.

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

---
product: campaign
title: Interaction - Datenpuffer
description: Interaction - Datenpuffer
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 7250b885-0606-466a-bfc2-6dd3cc5a012d
TQID: https://experienceleague.adobe.com/VzejoXfvy4j-bthB0FrSB-iSipA-oGLd0BmqP2niNrg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 301
ht-degree: 3%

---

# Interaction - Datenpuffer{#interaction-data-buffer}



Sie können eine Datenpufferzone konfigurieren, um die Leistung eingehender Interaktionen zu steigern, indem Sie die Berechnungen von Angebotsvorschlägen desynchronisieren. Diese Konfiguration muss in der eigenen Konfigurationsdatei der Instanz (config-instance.xml) durchgeführt werden.

In Adobe Campaign wurde eine **Datenpufferzone** im Interaction -Modul eingeführt. Auf diese Weise können Sie **Leistung** eingehenden Interaktionen steigern, indem Sie Bestands- und Angebotsberechnungen desynchronisieren.

Sie betrifft nur eingehende Interaktionen, entweder durch einen Aufruf (mit oder ohne Aufrufdaten) oder durch eine Statusaktualisierung (updateStatus).

Um beim Schreiben von Vorschlägen für einen Empfänger eine Warteschlange zu vermeiden, generiert ein neuer Prozess eine **Datenpufferzone** mit der Vorschläge **(asynchron)** werden können. Diese Datenpufferzone wird regelmäßig gelesen und geleert. Der Standardzeitraum beträgt etwa eine Sekunde.Die Vorschlagstexte sind daher gruppiert.

>[!NOTE]
>
>Diese Konfiguration ist zwingend erforderlich, wenn Sie Interaction in einer verteilten Architektur verwenden.

Die Datenpufferzone **configuration** kann in der Konfigurationsdatei der Instanz (config-instance.xml) verwendet werden.

>[!CAUTION]
>
>Einige Konfigurationen können von Adobe nur für Bereitstellungen durchgeführt werden, die von Adobe gehostet werden. Beispielsweise für den Zugriff auf die Konfigurationsdateien des Servers und der Instanz. Weitere Informationen zu den verschiedenen Bereitstellungen finden Sie im Abschnitt [Hosting](../../installation/using/hosting-models.md) oder auf [dieser Seite](../../installation/using/capability-matrix.md).
>
>Alle an der Konfiguration vorgenommenen Änderungen erfordern einen Neustart des Webservers (Apache:IIS) und der Adobe Campaign-Prozesse.\
>Stellen Sie nach der Konfiguration der Datenpufferzone sicher, dass eine angepasste Hardwarekonfiguration verfügbar ist. (Menge des vorhandenen Speichers).


Stellen Sie nach der Konfiguration der Datenpufferzone sicher, dass eine angepasste Hardwarekonfiguration verfügbar ist. (Menge des vorhandenen Speichers).

Die Definition für einen Schreib-Daemon (Prozess namens Interaction) lautet wie folgt:

```
<interactiond args="" autoStart="false" callDataSize="0" initScript="" maxProcessMemoryAlertMb="1800"
maxProcessMemoryWarningMb="1600" maxSharedEntries="25000" nextOffersSize="0"
processRestartTime="06:00:00" runLevel="10" targetKeySize="16"/>
```

Bei Verwendung von Inbound Interaction muss das Attribut @autostart „true“ lauten, damit der Prozess beim Start des Adobe Campaign-Servers automatisch gestartet wird.

Details des Arguments:

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

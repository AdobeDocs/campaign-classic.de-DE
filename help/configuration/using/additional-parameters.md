---
product: campaign
title: Zusätzliche Web-Tracking-Parameter
description: Erfahren Sie mehr über die Parameter für das Web-Tracking
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: d14d94fd-b078-4893-be84-31d37a1d50f5
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Zusätzliche Web-Tracking-Parameter{#additional-parameters}

## Parameter definieren {#definition-of-parameters}

Ihre Adobe Campaign-Plattform bietet standardmäßig zwei Webtrackingparameter vom Typ TRANSACTION :

* **amount**: entspricht dem Transaktionsbetrag;
* **article**: stellt die Anzahl der Elemente in einer Transaktion dar.

Diese Parameter werden im Schema **nms:webTrackingLog** definiert und sind einige der Indikatoren, die in Berichten angezeigt werden.

Um zusätzliche Parameter zu definieren, müssen Sie dieses Schema erweitern.

**Beispiel**:

```
<srcSchema extendedSchema="nms:webTrackingLog" label="Web Tracking"
           mappingType="sql" name="webTrackingLog" 
           namespace="cus" xtkschema="xtk:srcSchema">

  <element name="webTrackingLog">
    <attribute desc="Payment method" label="Payment method" length="10" name="mode" type="string"/>
    <attribute desc="Offer code" label="Offer code" length="5" name="code" type="string"/>
  </element>
</srcSchema>
```

Sie können die Werte dieser Parameter anzeigen, indem Sie die Trackinglog-Liste (eines Versands oder eines Empfängers) konfigurieren.

## Konfiguration des Weiterleitungsservers {#redirection-server-configuration}

In der Serverkonfiguration können Sie die maximale Zeichenanzahl definieren, die für Ihre Webtracking-Parameter berücksichtigt werden soll.

>[!IMPORTANT]
>
>Eine Erhöhung der maximal zu berücksichtigenden Zeichenanzahl kann sich auf die Webtracking-Leistung Ihrer Plattform auswirken.

Ändern Sie dazu das Attribut **webTrackingParamSize** des Elements **`<trackinglogd>`** in der Datei **serverConf.xml**. Diese Datei wird im Unterverzeichnis **conf** des Adobe Campaign-Installationsordners gespeichert.

**Beispiel**:

Der Standardwert ist 64 Zeichen. Mit diesem Wert können Sie die Standardparameter **amount** und **article** (&quot;amount=xxxxxxxxxx&amp;article=xxxxxxxx&quot;) berücksichtigen.

Unter Berücksichtigung der beiden im Beispiel des Erweiterungsschemas angegebenen Parameter (Größe des Namens + Größe des Werts) können Sie die Konfiguration so ändern, dass 100 Zeichen berücksichtigt werden (&quot;amount=xxxxxxxxxx&amp;article=xxxxxxxxxxxx&amp;mode=xxxxxxxxxx&amp;code=xxxxxxx&quot;).

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

Nachdem die Konfiguration geändert wurde, müssen Sie:

* Beenden Sie den Webserver, der das Weiterleitungsmodul hostet (Apache, IIS usw.),
* Beenden Sie den Adobe Campaign-Server: **net stop nlserver6** in Windows, **/etc/init.d/nlserver6 stop** in Linux,

  >[!NOTE]
  >
  >Ab Version 20.1 wird empfohlen, stattdessen den folgenden Befehl zu verwenden (für Linux): **systemctl stop nlserver**

* Löschen Sie unter Linux die freigegebenen Speichersegmente mit dem Befehl **ipcrm**,
* Starten Sie den Adobe Campaign-Server neu: **net start nlserver6** in Windows, **/etc/init.d/nlserver6 start** in Linux,

  >[!NOTE]
  >
  >Ab Version 20.1 wird empfohlen, stattdessen den folgenden Befehl zu verwenden (für Linux): **systemctl start nlserver**

* Starten Sie den Webserver neu.

**Beispiel**: Berücksichtigen Sie die Konfiguration unter Linux.

```
adobe@selma:~$ systemctl stop nlserver
adobe@selma:~$ systemctl stop apache2
adobe@selma:~$ ipcs shm

------ Shared Memory Segments --------
key        shmid      owner      perms      bytes      nattch     status      
0x52020679 2097153    adobe   666        93608      8                       

------ Semaphore Arrays --------
key        semid      owner      perms      nsems     
0x52020678 4227081    adobe   666        1         

------ Message Queues --------
key        msqid      owner      perms      used-bytes   messages    

adobe@selma:~$ ipcrm shm 2097153                             
1 resource(s) deleted
adobe@selma:~$ systemctl start nlserver
adobe@selma:~$ systemctl start apache2
```

>[!NOTE]
>
>Wenn Sie unter Linux die Größe der Parameter **webTrackingParamSize** oder **maxSharedLogs** erhöhen, müssen Sie möglicherweise die Größe des gemeinsamen Speichers (SHM) erhöhen.

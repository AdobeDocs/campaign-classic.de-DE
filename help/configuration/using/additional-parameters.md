---
product: campaign
title: Zusätzliche Webtracking-Parameter
description: Weitere Informationen zu Parametern für das Webtracking
feature: Configuration, Instance Settings
role: Developer
exl-id: d14d94fd-b078-4893-be84-31d37a1d50f5
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# Zusätzliche Webtracking-Parameter{#additional-parameters}

## Definition von Parametern {#definition-of-parameters}

Ihre Adobe Campaign-Plattform bietet standardmäßig zwei Webtrackingparameter vom Typ TRANSAKTION :

* **amount**: gibt den Betrag einer Transaktion an,
* **article**: Gibt die Anzahl der Elemente in einer Transaktion an.

Diese Parameter werden im **nms:webTrackingLog**-Schema definiert und sind einige der Indikatoren, die in Berichten angezeigt werden.

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

Sie können die Werte dieser Parameter anzeigen, indem Sie die Trackinglog-Liste (eines Versands oder Empfängers) konfigurieren.

## Konfiguration des Weiterleitungsservers {#redirection-server-configuration}

In der Server-Konfiguration können Sie die maximale Anzahl von Zeichen definieren, die für Ihre Webtracking-Parameter berücksichtigt werden sollen.

>[!IMPORTANT]
>
>Eine Erhöhung der maximalen Anzahl der zu berücksichtigenden Zeichen kann sich auf die Webtracking-Leistung Ihrer Plattform auswirken.

Ändern Sie dazu das Attribut **webTrackingParamSize** des **`<trackinglogd>`** in der Datei **serverConf.xml**. Diese Datei wird im Unterverzeichnis **conf** des Adobe Campaign-Installationsverzeichnisses gespeichert.

**Beispiel**:

Der Standardwert ist 64 Zeichen. Mit diesem Wert können Sie die Standardparameter **amount** und **article** („amount=xxxxxxxx&amp;article=xxxxxxxx„) berücksichtigen.

Wenn Sie beide Parameter (Größe des Namens + Größe des Werts) berücksichtigen, die im obigen Beispiel für das Erweiterungsschema angegeben sind, können Sie die Konfiguration so ändern, dass 100 Zeichen berücksichtigt werden („amount=xxxxxxx&amp;article=xxxxxxx&amp;mode=xxxxxxx&amp;code=xxxxx„).

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

Wenn die Konfiguration geändert wurde, müssen Sie:

* Beenden Sie den Webserver, der das Umleitungsmodul hostet (Apache, IIS usw.),
* Beenden Sie den Adobe Campaign-Server: **net stop nlserver6** unter Windows, **/etc/init.d/nlserver6 stop** unter Linux,

  >[!NOTE]
  >
  >Ab 20.1 wird stattdessen der folgende Befehl empfohlen (für Linux): **systemctl stop nlserver**

* Löschen Sie unter Linux die Segmente des geteilten Speichers mithilfe des **ipcrm**-Befehls,
* Starten Sie den Adobe Campaign-Server neu: **net start nlserver6** unter Windows, **/etc/init.d/nlserver6 start** unter Linux,

  >[!NOTE]
  >
  >Ab 20.1 wird empfohlen, stattdessen den folgenden Befehl zu verwenden (für Linux): **systemctl start nlserver**

* Starten Sie den Webserver neu.

**Beispiel**: unter Berücksichtigung der Konfiguration unter Linux.

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

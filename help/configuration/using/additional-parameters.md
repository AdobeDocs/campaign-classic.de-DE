---
title: Zusätzliche Parameter
seo-title: Zusätzliche Parameter
description: Zusätzliche Parameter
seo-description: null
page-status-flag: never-activated
uuid: c223c84a-f8fd-43d3-9deb-b1c19d442c65
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 1b2ae224-8406-4506-b589-6e5f6631e87f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Zusätzliche Parameter{#additional-parameters}

## Definition von Parametern {#definition-of-parameters}

Ihre Adobe Campaign-Plattform bietet standardmäßig zwei TRANSACTION-artige Web-Tracking-Parameter:

* **Betrag**: die Höhe einer Transaktion,
* **Artikel**: stellt die Anzahl der Elemente in einer Transaktion dar.

Diese Parameter werden im Schema **nms:webTrackingLog** definiert und sind einige der in der Berichterstellung angezeigten Indikatoren.

Um weitere Parameter zu definieren, müssen Sie dieses Schema erweitern.

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

Sie können die Werte dieser Parameter anzeigen, indem Sie die Verfolgungsprotokollliste (einer Lieferung oder eines Empfängers) konfigurieren.

## Serverkonfiguration umleiten {#redirection-server-configuration}

In der Serverkonfiguration können Sie die maximale Anzahl von Zeichen festlegen, die für Ihre Webverfolgungsparameter berücksichtigt werden sollen.

>[!IMPORTANT]
>
>Die Erhöhung der maximal zu berücksichtigenden Zeichenanzahl kann sich auf die Webverfolgungsleistung Ihrer Plattform auswirken.

Ändern Sie dazu das Attribut **webTrackingParamSize** des **`<trackinglogd>`** Elements in der Datei &quot; **serverConf.xml** &quot;. Diese Datei wird im **conf** -Unterverzeichnis des Adobe Campaign-Installationsordners gespeichert.

**Beispiel**:

Der Standardwert ist 64 Zeichen. Mit diesem Wert können Sie die Standardparameter **für Betrag** und **Artikel** (&quot;amount=xxxxxxxx&amp;article=xxxxxxxx&quot;) berücksichtigen.

Indem Sie beide Parameter (Größe des Namens und Größe des Werts) berücksichtigen, die im Beispiel des Erweiterungsschemas oben angegeben sind, können Sie die Konfiguration so ändern, dass 100 Zeichen berücksichtigt werden (&quot;Betrag=xxxxxxxxxx&amp;article=xxxxxxxxxx&amp;mode=xxxxxxxxxx&amp;code=xxxxxxx&quot;).

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

Nach der Änderung der Konfiguration müssen Sie:

* Beenden Sie den Webserver, der das Umleitungsmodul hostet (Apache, IIS usw.),
* Adobe Campaign-Server beenden: **net stop nlserver6** in Windows, **/etc/init.d/nlserver6 stop** in Linux,

   >[!NOTE]
   >
   >Ab 20.1 wird empfohlen, stattdessen den folgenden Befehl zu verwenden (für Linux): nlserver **systemctl stop**

* Löschen Sie unter Linux die freigegebenen Speichersegmente mit dem **Befehl ipcrm** ,
* Starten Sie den Adobe Campaign-Server neu: **net start nlserver6** in Windows, **/etc/init.d/nlserver6 start** in Linux,

   >[!NOTE]
   >
   >Ab 20.1 wird empfohlen, stattdessen den folgenden Befehl zu verwenden (für Linux): nlserver **systemctl start**

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


---
solution: Campaign Classic
product: campaign
title: Zusätzliche Web-Tracking-Parameter
description: Weitere Informationen zu Parametern für die Web-Verfolgung
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 4%

---


# Zusätzliche Parameter{#additional-parameters}

## Definition von Parametern {#definition-of-parameters}

Ihre Adobe Campaign-Plattform Angebot standardmäßig zwei TRANSACTION-artige Web-Tracking-Parameter:

* **Betrag**: den Betrag einer Transaktion darstellt,
* **Artikel**: stellt die Anzahl der Elemente in einer Transaktion dar.

Diese Parameter werden im Schema **nms:webTrackingLog** definiert und sind einige der in Berichte angezeigten Indikatoren.

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

Sie können die Werte dieser Parameter anzeigen, indem Sie die Verfolgungsprotokoll-Liste (eines Versands oder Empfängers) konfigurieren.

## Serverkonfiguration umleiten {#redirection-server-configuration}

In der Serverkonfiguration können Sie die maximale Anzahl von Zeichen festlegen, die für Ihre Webverfolgungsparameter berücksichtigt werden sollen.

>[!IMPORTANT]
>
>Die Erhöhung der maximal zu berücksichtigenden Zeichenanzahl kann sich auf die Webverfolgungsleistung Ihrer Plattform auswirken.

Ändern Sie dazu das Attribut **webTrackingParamSize** des **`<trackinglogd>`** Elements in der Datei &quot; **serverConf.xml** &quot;. Diese Datei wird im **conf** -Unterverzeichnis des Installationsordners des Adobe Campaigns gespeichert.

**Beispiel**:

Der Standardwert ist 64 Zeichen. Mit diesem Wert können Sie die Standardparameter **für Betrag** und **Artikel** (&quot;amount=xxxxxxxx&amp;article=xxxxxxxx&quot;) berücksichtigen.

Unter Berücksichtigung der beiden im obigen Erweiterungsschema angegebenen Parameter (Größe und Größe des Namens) können Sie die Konfiguration ändern, um 100 Zeichen zu berücksichtigen (&quot;Betrag=xxxxxxxx&amp;article=xxxxxxxxxx&amp;mode=xxxxxxxxxxxx&amp;code=xxxxxxx&quot;).

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
   >Starting 20.1, we recommend using the following command instead (for Linux): **systemctl stop nlserver**

* Löschen Sie unter Linux die freigegebenen Speichersegmente mit dem **Befehl ipcrm** ,
* Starten Sie den Adobe Campaign-Server neu: **net Beginn nlserver6** in Windows, **/etc/init.d/nlserver6 Beginn** in Linux,

   >[!NOTE]
   >
   >Ab 20.1 wird empfohlen, stattdessen den folgenden Befehl zu verwenden (für Linux): **systemctl Beginn nlserver**

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


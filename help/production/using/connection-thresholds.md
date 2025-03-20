---
product: campaign
title: Verbindungsgrenzwerte
description: Verbindungsgrenzwerte
feature: Monitoring
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
source-git-commit: 757e3a5395f24e0bdd04737aba0458881e4ea780
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 10%

---

# Verbindungsgrenzwerte{#connection-thresholds}



Bei stark ausgelasteten Servern kann der Verbindungsschwellenwert überschritten werden. Auf jeden Fall ist es nützlich, die Gründe dafür zu erfahren.

Es gibt drei verschiedene Schwellenwerte:

* Der **Schwellenwert für Webverbindungen**, der auf Ihrem Webserver konfiguriert ist. Wenden Sie sich an Ihren Systemadministrator, um sie zu ändern.

* Der **Schwellenwert für Datenbankverbindungen**. Wenden Sie sich an Ihren Datenbankadministrator, um sie zu ändern.

* Der **Adobe Campaign-Verbindungsschwellenwert**, der an zwei Stellen verfügbar ist:

   * **Tomcat** Seite: Alle Abfragen, die tatsächlich auf dem Adobe Campaign Tomcat-Client ankommen.

     Dieser Schwellenwert wird in der Datei **nl6/tomcat-X/conf/server.xml** konfiguriert. Mit dem **maxThreads**-Attribut können Sie den Schwellenwert für die Anzahl der gleichzeitig verarbeiteten Abfragen erhöhen. Sie kann beispielsweise in 250 geändert werden.

     ```
     <Connector protocol="HTTP/1.1" port="8080"
                    maxThreads="75"
                    minSpareThreads="5"
                    enableLookups="true" redirectPort="8443"
                    acceptCount="100" connectionTimeout="20000"
                    disableUploadTimeout="true" />
         <Engine name="Tomcat-Standalone" defaultHost="localhost">
           <Host name="localhost" appBase="./"
                 unpackWARs="true" autoDeploy="true">
     ```

   * **Datenbank**: Satz aller Verbindungen, die gleichzeitig in der Datenbank von einem Prozess geöffnet sind.

     Dieser Schwellenwert wird in der Datei **nl6/conf/serverConf.xml** konfiguriert. Mit dem **maxCnx**-Attribut im **Datenquellenpool** können Sie den Schwellenwert für gleichzeitig verarbeitete Abfragen erhöhen.

     ```
         <!-- Data source
              -->
           <dataSource name="default">
             <dbcnx NChar="" bulkCopyUtility="" dbSchema="" encrypted="" login="" password="" provider="" server="" timezone="" unicodeData="" useTimestampTZ=""/>
             <sqlParams funcPrefix="">
               <postConnectSQL/>
             </sqlParams>
             <pool aliveTestDelaySec="600" freeCnx="0" maxCnx="90" maxIdleDelaySec="1200"/>
           </dataSource>
     ```

---
title: Verbindungsschwellen
seo-title: Verbindungsschwellen
description: Verbindungsschwellen
seo-description: null
page-status-flag: never-activated
uuid: a4b6959a-0f5b-41a2-b4c3-d7d6613d1a18
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: f3db77db-94cc-4d75-a59b-2dddce776759
translation-type: tm+mt
source-git-commit: d509dc584cd4ae17c6dda85c09fceee8c6162dba
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 5%

---


# Verbindungsschwellen{#connection-thresholds}

Bei hochgeladenen Servern kann der Verbindungsschwellenwert überschritten werden. In jedem Ereignis ist es nützlich herauszufinden, warum.

Es gibt drei verschiedene Schwellenwerte:

1. Der Schwellenwert für die Webverbindung, der auf Ihrem Webserver konfiguriert ist. Wenden Sie sich zum Ändern an Ihren Systemadministrator.
1. Der Schwellenwert für die Datenbankverbindung. Wenden Sie sich zum Ändern an Ihren Datenbankadministrator.
1. Der Schwellenwert für die Adobe Campaign-Verbindung, der an zwei Stellen verfügbar ist:

   * Tomcat-Seite: alle Abfragen, die tatsächlich auf dem Adobe Campaign Tomcat Client ankommen.

      Dieser Schwellenwert wird in der Datei **nl6/tomcat-8/conf/server.xml** konfiguriert. Mit dem **Attribut maxThreads** können Sie den Schwellenwert der Anzahl der gleichzeitig verarbeiteten Abfragen erhöhen. Sie kann beispielsweise in 250 geändert werden.

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

   * Datenbank: alle Verbindungen, die gleichzeitig in der Datenbank geöffnet werden, durch einen Prozess.

      Dieser Schwellenwert wird in der Datei **nl6/conf/serverConf.xml** konfiguriert. Mit dem **Attribut maxCnx** im **Datenquellenpool** können Sie den Schwellenwert für gleichzeitig verarbeitete Abfragen erhöhen.

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


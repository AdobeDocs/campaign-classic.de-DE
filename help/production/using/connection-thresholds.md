---
solution: Campaign Classic
product: campaign
title: Verbindungsschwellen
description: Verbindungsschwellen
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 3%

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


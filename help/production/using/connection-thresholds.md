---
product: campaign
title: Verbindungsgrenzwerte
description: Verbindungsgrenzwerte
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 3%

---

# Verbindungsgrenzwerte{#connection-thresholds}

Bei stark ausgelasteten Servern kann der Verbindungsschwellenwert überschritten werden. Auf jeden Fall ist es nützlich herauszufinden, warum.

Es gibt drei unterschiedliche Schwellenwerte:

* Der **Schwellenwert für Webverbindungen**, der auf Ihrem Webserver konfiguriert ist. Wenden Sie sich zur Änderung an Ihren Systemadministrator.

* Der **Schwellenwert für Datenbankverbindungen**. Wenden Sie sich zur Änderung an Ihren Datenbankadministrator.

* Der **Adobe Campaign-Verbindungsschwellenwert**, der an zwei Stellen verfügbar ist:

   * **** Tomcatside: alle Abfragen, die tatsächlich auf den Adobe Campaign Tomcat-Client gelangen.

      Dieser Schwellenwert wird in der Datei **nl6/tomcat-8/conf/server.xml** konfiguriert. Mit dem Attribut **maxThreads** können Sie den Schwellenwert für die Anzahl der gleichzeitig verarbeiteten Abfragen erhöhen. Sie kann beispielsweise auf 250 geändert werden.

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

   * **Datenbank**: Satz aller Verbindungen, die durch einen Prozess gleichzeitig in der Datenbank geöffnet werden.

      Dieser Schwellenwert wird in der Datei **nl6/conf/serverConf.xml** konfiguriert. Mit dem Attribut **maxConx** im **Datenquellenpool** können Sie den Schwellenwert für gleichzeitig verarbeitete Abfragen erhöhen.

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

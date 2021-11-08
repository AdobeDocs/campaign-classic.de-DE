---
product: campaign
title: Verbindungsgrenzwerte
description: Verbindungsgrenzwerte
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 3%

---

# Verbindungsgrenzwerte{#connection-thresholds}

![](../../assets/v7-only.svg)

Bei stark ausgelasteten Servern kann der Verbindungsschwellenwert überschritten werden. Auf jeden Fall ist es nützlich herauszufinden, warum.

Es gibt drei unterschiedliche Schwellenwerte:

* Die **Schwellenwert für Webverbindungen** auf Ihrem Webserver konfiguriert. Wenden Sie sich zur Änderung an Ihren Systemadministrator.

* Die **Schwellenwert für Datenbankverbindung**. Wenden Sie sich zur Änderung an Ihren Datenbankadministrator.

* Die **Adobe Campaign-Verbindungsschwellen**, verfügbar an zwei Stellen:

   * **Tomcat** side: alle Abfragen, die tatsächlich auf den Adobe Campaign Tomcat-Client gelangen.

      Diese Schwelle wird im **nl6/tomcat-8/conf/server.xml** -Datei. Die **maxThreads** -Attribut können Sie die Schwelle der Anzahl der gleichzeitig verarbeiteten Abfragen erhöhen. Sie kann beispielsweise auf 250 geändert werden.

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

      Dieser Schwellenwert wird in der Datei konfiguriert **nl6/conf/serverConf.xml**. Die **maxCnx** -Attribut in **Datenquellenpool** erhöht die Schwelle für gleichzeitig verarbeitete Abfragen.

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

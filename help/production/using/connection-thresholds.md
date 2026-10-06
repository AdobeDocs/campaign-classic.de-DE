---
product: campaign
title: Verbindungsgrenzwerte
description: Verbindungsgrenzwerte
feature: Monitoring
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 13%
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

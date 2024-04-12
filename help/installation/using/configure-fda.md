---
product: campaign
title: FDA-Connectoren konfigurieren
description: Erfahren Sie mehr über die Konfigurationsschritte für FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0b53b165-a6d8-4604-b3f0-3fa6fce35146
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 50%

---

# FDA-Connectoren konfigurieren {#specific-configurations-by-database-type}



Abhängig von der externen Datenbank, auf die Sie von Adobe Campaign aus zugreifen möchten, müssen Sie bestimmte Konfigurationen vornehmen. Hierzu zählen im Prinzip die Einrichtung von Treibern und die Deklaration von Umgebungsvariablen für jedes DBMS auf dem Adobe-Campaign-Server.

Dazu müssen Sie die jeweilige Client-Ebene in der externen Datenbank auf dem Adobe-Campaign-Server installieren.

>[!NOTE]
>
>Kompatible Versionen sind in der [Campaign-Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA) aufgeführt.
>

## Konfigurationsschritte {#fda-configuration-steps}

Gehen Sie wie folgt vor, um den Zugriff auf eine externe Datenbank mit FDA einzurichten:

1. Installieren Sie die Treiber und richten Sie das externe Konto ein, das Ihrer Datenbank auf dem Adobe Campaign-Server entspricht. Siehe Datenbankspezifische Seiten . [unten aufgeführt](#fda-specific-configuration)
1. Testen Sie das externe Konto oder erstellen Sie eine temporäre Verbindung zwischen Adobe Campaign und der externen Datenbank. [Weitere Informationen](../../installation/using/connecting-to-database.md)
1. Erstellen Sie das Schema der externen Datenbank in Adobe Campaign. Auf diese Weise können Sie die Datenstruktur der externen Datenbank identifizieren. [Weitere Informationen](../../installation/using/creating-data-schema.md)
1. Erstellen Sie bei Bedarf ein neues Zielgruppen-Mapping aus dem zuvor erstellten Schema. Dies ist dann erforderlich, wenn die Empfänger Ihrer Sendungen aus der externen Datenbank stammen. Für diese Implementierung bestehen Einschränkungen bei der Nachrichtenpersonalisierung. [Weitere Informationen](../../installation/using/defining-data-mapping.md)

Nachdem das Schema erstellt wurde, können Daten in Adobe Campaign-Workflows verarbeitet werden. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../workflow/using/accessing-an-external-database-fda.md).

## Datenbankspezifische Konfiguration {#fda-specific-configuration}

Abhängig von den externen Datenbanken, auf die Sie von Adobe Campaign aus zugreifen möchten, müssen Sie bestimmte Konfigurationen vornehmen. Diese Konfigurationen umfassen im Wesentlichen die Installation von Treibern und die Deklarierung von Umgebungsvariablen für jedes RDBMS auf dem Adobe Campaign-Server sowie die Konfiguration des externen Kontos.

Weitere Informationen finden Sie unter den folgenden Links:

* Campaign verbinden und [Amazon Redshift](../../installation/using/configure-fda-redshift.md)
* Campaign verbinden und [Azure synapse](../../installation/using/configure-fda-synapse.md)
* Campaign verbinden und [Google BigQuery](../../installation/using/configure-fda-google-big-query.md)
* Campaign verbinden und [Hadoop](../../installation/using/configure-fda-hadoop.md)
* Campaign verbinden und [Microsoft SQL Server](../../installation/using/configure-fda-sql.md)
* Campaign verbinden und [Netezza](../../installation/using/configure-fda-netezza.md)
* Campaign verbinden und [Oracle](../../installation/using/configure-fda-oracle.md)
* Campaign verbinden und [PostgreSQL](../../installation/using/configure-fda-postgresql.md)
* Campaign verbinden und [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
* Campaign verbinden und [Snowflake](../../installation/using/configure-fda-snowflake.md)
* Campaign verbinden und [Sybase IQ](../../installation/using/configure-fda-sybase.md)
* Campaign verbinden und [Teradata](../../installation/using/configure-fda-teradata.md)
* Campaign verbinden und [Vertica analytics](../../installation/using/configure-fda-vertica.md)

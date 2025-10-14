---
product: campaign
title: Konfigurieren von FDA-Connectoren
description: Konfigurationsschritte für FDA lernen
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0b53b165-a6d8-4604-b3f0-3fa6fce35146
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 55%

---

# FDA-Connectoren konfigurieren {#specific-configurations-by-database-type}



Abhängig von der externen Datenbank, auf die Sie von Adobe Campaign aus zugreifen möchten, müssen Sie bestimmte Konfigurationen vornehmen. Hierzu zählen im Prinzip die Einrichtung von Treibern und die Deklaration von Umgebungsvariablen für jedes DBMS auf dem Adobe Campaign-Server.

Dazu müssen Sie die jeweilige Client-Ebene in der externen Datenbank auf dem Adobe Campaign-Server installieren.

>[!NOTE]
>
>Kompatible Versionen sind in der [Campaign-Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA) aufgeführt.
>

## Konfigurationsschritte {#fda-configuration-steps}

Gehen Sie wie folgt vor, um den Zugriff auf eine externe Datenbank mit FDA einzurichten:

1. Installieren Sie die Treiber und richten Sie das externe Konto ein, das Ihrer Datenbank auf dem Adobe Campaign-Server entspricht. Verweisen Sie auf die datenbankspezifischen Seiten [unten aufgelistet](#fda-specific-configuration)
1. Testen Sie das externe Konto, oder erstellen Sie eine temporäre Verbindung zwischen Adobe Campaign und der externen Datenbank. [Weitere Informationen](../../installation/using/connecting-to-database.md)
1. Erstellen Sie das Schema der externen Datenbank in Adobe Campaign. Auf diese Weise können Sie die Datenstruktur der externen Datenbank identifizieren. [Weitere Informationen](../../installation/using/creating-data-schema.md)
1. Erstellen Sie bei Bedarf ein neues Zielgruppen-Mapping aus dem zuvor erstellten Schema. Dies ist dann erforderlich, wenn die Empfänger Ihrer Sendungen aus der externen Datenbank stammen. Für diese Implementierung bestehen Einschränkungen bei der Nachrichtenpersonalisierung. [Weitere Informationen](../../installation/using/defining-data-mapping.md)

Nachdem das Schema erstellt wurde, können Daten in Adobe Campaign-Workflows verarbeitet werden. Weitere Informationen finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html?lang=de){target="_blank"}.

## Datenbankspezifische Konfiguration {#fda-specific-configuration}

Abhängig von der externen Datenbank, auf die Sie von Adobe Campaign aus zugreifen möchten, müssen Sie bestimmte Konfigurationen vornehmen. Diese Konfigurationen umfassen im Wesentlichen die Installation von Treibern und die Deklaration von Umgebungsvariablen, die zu jedem RDBMS auf dem Adobe Campaign-Server gehören, sowie die Konfiguration des externen Kontos.

Folgen Sie den unten stehenden Links, um mehr zu erfahren:

* Campaign und [Amazon Redshift verbinden](../../installation/using/configure-fda-redshift.md)
* Campaign und [Azure Synapse verbinden](../../installation/using/configure-fda-synapse.md)
* Campaign und [Google BigQuery verbinden](../../installation/using/configure-fda-google-big-query.md)
* Campaign und [Hadoop verbinden](../../installation/using/configure-fda-hadoop.md)
* Campaign und [Microsoft SQL Server verbinden](../../installation/using/configure-fda-sql.md)
* Campaign und [Netezza verbinden](../../installation/using/configure-fda-netezza.md)
* Campaign und [Oracle verbinden](../../installation/using/configure-fda-oracle.md)
* Campaign und [PostgreSQL) ](../../installation/using/configure-fda-postgresql.md)
* Campaign und [SAP HANA verbinden](../../installation/using/configure-fda-sap-hana.md)
* Campaign und [Snowflake verbinden](../../installation/using/configure-fda-snowflake.md)
* Campaign und [Sybase IQ verbinden](../../installation/using/configure-fda-sybase.md)
* Campaign und [Teradata verbinden](../../installation/using/configure-fda-teradata.md)
* Campaign und [Vertica Analytics verbinden](../../installation/using/configure-fda-vertica.md)

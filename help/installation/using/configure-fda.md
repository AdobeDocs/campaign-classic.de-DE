---
product: campaign
title: FDA-Connectoren konfigurieren
description: Erfahren Sie mehr über die Konfigurationsschritte für FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0b53b165-a6d8-4604-b3f0-3fa6fce35146
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 36%

---

# Konfigurieren von FDA-Connectoren {#specific-configurations-by-database-type}

Abhängig von der externen Datenbank, auf die Sie von Adobe Campaign aus zugreifen möchten, müssen Sie bestimmte Konfigurationen vornehmen. Hierzu zählen im Prinzip die Einrichtung von Treibern und die Deklaration von Umgebungsvariablen für jedes RDBMS auf dem Adobe-Campaign-Server.

Dazu müssen Sie die jeweilige Client-Ebene in der externen Datenbank auf dem Adobe-Campaign-Server installieren.

>[!NOTE]
>
>Kompatible Versionen sind in der [Campaign-Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA) aufgeführt.


## Konfigurationsschritte {#fda-configuration-steps}

Gehen Sie wie folgt vor, um den Zugriff auf eine externe Datenbank mit FDA einzurichten:

1. Installieren Sie die Treiber und richten Sie das externe Konto ein, das Ihrer Datenbank auf dem Adobe Campaign-Server entspricht. Siehe Datenbankspezifische Seiten [unten aufgeführt](#fda-specific-configuration)
1. Testen Sie das externe Konto oder erstellen Sie eine temporäre Verbindung zwischen Adobe Campaign und der externen Datenbank. [Mehr dazu](../../installation/using/connecting-to-database.md)
1. Erstellen Sie das Schema der externen Datenbank in Adobe Campaign. Auf diese Weise können Sie die Datenstruktur der externen Datenbank identifizieren. [Mehr dazu](../../installation/using/creating-data-schema.md)
1. Erstellen Sie bei Bedarf ein neues Zielgruppen-Mapping aus dem zuvor erstellten Schema. Dies ist erforderlich, wenn die Empfänger Ihrer Sendungen aus der externen Datenbank stammen. Diese Implementierung weist Einschränkungen bei der Nachrichtenpersonalisierung auf. [Mehr dazu](../../installation/using/defining-data-mapping.md)

Nachdem das Schema erstellt wurde, können Daten in Adobe Campaign-Workflows verarbeitet werden. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../workflow/using/accessing-an-external-database--fda-.md).

## Datenbankspezifische Konfiguration {#fda-specific-configuration}

Abhängig von den externen Datenbanken, auf die Sie von Adobe Campaign aus zugreifen möchten, müssen Sie bestimmte Konfigurationen vornehmen. Diese Konfigurationen umfassen im Wesentlichen die Installation von Treibern und die Deklarierung von Umgebungsvariablen, die zu jedem RDBMS auf dem Adobe Campaign-Server gehören, sowie die Konfiguration des externen Kontos.

Weitere Informationen finden Sie unter den folgenden Links:

* Verbinden von Campaign und [Azure synapse](../../installation/using/configure-fda-synapse.md)

* Verbinden von Campaign und [Snowflake](../../installation/using/configure-fda-snowflake.md)

* Verbinden von Campaign und [Hadoop](../../installation/using/configure-fda-hadoop.md)

* Verbinden von Campaign und [Oracle](../../installation/using/configure-fda-oracle.md)

* Verbinden von Campaign und [Netezza](../../installation/using/configure-fda-netezza.md)

* Verbinden von Campaign und [Sybase IQ](../../installation/using/configure-fda-sybase.md)

* Verbinden von Campaign und [Teradata](../../installation/using/configure-fda-teradata.md)

* Verbinden von Campaign und [SAP HANA](../../installation/using/configure-fda-sap-hana.md)

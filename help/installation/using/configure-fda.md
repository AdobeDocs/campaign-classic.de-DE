---
solution: Campaign Classic
product: campaign
title: FDA-Connectors konfigurieren
description: Konfigurationsschritte für die FDA
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 70%

---


# Konfigurieren von FDA-Connectoren {#specific-configurations-by-database-type}

Abhängig von der externen Datenbank, auf die Sie von Adobe Campaign aus zugreifen möchten, müssen Sie bestimmte Konfigurationen vornehmen. Hierzu zählen im Prinzip die Einrichtung von Treibern und die Deklaration von Umgebungsvariablen für jedes RDBMS auf dem Adobe-Campaign-Server.

Dazu müssen Sie die jeweilige Client-Ebene in der externen Datenbank auf dem Adobe-Campaign-Server installieren.

>[!NOTE]
>
>Kompatible Versionen sind in der [Campaign-Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA) aufgeführt.


## Konfigurationsschritte {#fda-configuration-steps}

So richten Sie den Zugriff auf eine externe Datenbank mit FDA ein:

1. Installieren Sie die entsprechenden Treiber für Ihre Datenbank auf dem Adobe-Campaign-Server. Treiber werden auf den datenbankspezifischen Seiten [aufgelistet, die unten](#fda-specific-configuration) aufgeführt sind.
1. [Erstellen und konfigurieren Sie ein externes Konto](../../installation/using/connecting-to-database.md), über das Sie die Verbindung zwischen Adobe Campaign und der externen Datenbank herstellen können. Weitere Informationen zu Externen Konti in der Kampagne finden Sie auf [dieser Seite](../../installation/using/external-accounts.md).
1. [Erstellen Sie das Schema](../../installation/using/creating-data-schema.md) der externen Datenbank in Adobe Campaign. Auf diese Weise können Sie die Datenstruktur der externen Datenbank identifizieren.
1. Erstellen Sie bei Bedarf ein neues Zielgruppen-Mapping[ aus dem zuvor erstellten Schema. ](../../installation/using/defining-data-mapping.md) Dies ist erforderlich, wenn die Empfänger Ihrer Versand aus der externen Datenbank stammen. Diese Implementierung weist Einschränkungen bei der Personalisierung von Nachrichten auf.

Nachdem das Schema erstellt wurde, können Daten in Adobe Campaign-Workflows verarbeitet werden. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../workflow/using/accessing-an-external-database--fda-.md).

## Datenbankspezifische Konfiguration {#fda-specific-configuration}

Abhängig von der externen Datenbank, auf die Sie von Adobe Campaign aus zugreifen möchten, müssen Sie bestimmte Konfigurationen vornehmen. Hierzu zählen im Prinzip die Einrichtung von Treibern und die Deklaration von Umgebungsvariablen für jedes RDBMS auf dem Adobe-Campaign-Server.

Gehen Sie wie folgt vor, um mehr zu erfahren:

* [azure synapse](../../installation/using/configure-fda-synapse.md)

* [Snowflake](../../installation/using/configure-fda-snowflake.md)

* [Hadoop](../../installation/using/configure-fda-hadoop.md)

* [Oracle](../../installation/using/configure-fda-oracle.md)

* [Netezza](../../installation/using/configure-fda-netezza.md)

* [Sybase IQ](../../installation/using/configure-fda-sybase.md)

* [Teradata](../../installation/using/configure-fda-teradata.md)

* [SAP HANA](../../installation/using/configure-fda-sap-hana.md)

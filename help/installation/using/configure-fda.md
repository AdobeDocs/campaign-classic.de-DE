---
solution: Campaign Classic
product: campaign
title: FDA-Connectors konfigurieren
description: Konfigurationsschritte für die FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0b53b165-a6d8-4604-b3f0-3fa6fce35146
translation-type: tm+mt
source-git-commit: 7ce5a01b57092043b8d9b52761b243f771cf74f2
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

So richten Sie den Zugriff auf eine externe Datenbank mit FDA ein:

1. Installieren Sie die Treiber und richten Sie das Externe Konto ein, das Ihrer Datenbank auf dem Adobe Campaign-Server entspricht. Auf die datenbankspezifischen Seiten [verweisen, die unten](#fda-specific-configuration) aufgelistet sind
1. Testen Sie das Externe Konto oder erstellen Sie eine temporäre Verbindung zwischen Adobe Campaign und der externen Datenbank. [Mehr dazu](../../installation/using/connecting-to-database.md)
1. Erstellen Sie das Schema der externen Datenbank in Adobe Campaign. Auf diese Weise können Sie die Datenstruktur der externen Datenbank identifizieren. [Mehr dazu](../../installation/using/creating-data-schema.md)
1. Erstellen Sie bei Bedarf ein neues Zielgruppen-Mapping aus dem zuvor erstellten Schema. Dies ist erforderlich, wenn die Empfänger Ihrer Versand aus der externen Datenbank stammen. Diese Implementierung weist Einschränkungen bei der Personalisierung von Nachrichten auf. [Mehr dazu](../../installation/using/defining-data-mapping.md)

Nachdem das Schema erstellt wurde, können Daten in Adobe Campaign-Workflows verarbeitet werden. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../workflow/using/accessing-an-external-database--fda-.md).

## Datenbankspezifische Konfiguration {#fda-specific-configuration}

Abhängig von den externen Datenbanken, auf die Sie von Adobe Campaign aus zugreifen möchten, müssen Sie bestimmte Konfigurationen durchführen. Diese Konfigurationen umfassen im Wesentlichen die Installation von Treibern und das Deklarieren von Umgebung-Variablen, die zu den einzelnen RDBMS auf dem Adobe Campaign-Server gehören, sowie die Konfiguration des Externen Kontos.

Gehen Sie wie folgt vor, um mehr zu erfahren:

* Kampagne verbinden und [Azure synapse](../../installation/using/configure-fda-synapse.md)

* Kampagne verbinden und [Snowflake](../../installation/using/configure-fda-snowflake.md)

* Kampagne verbinden und [Hadoop](../../installation/using/configure-fda-hadoop.md)

* Kampagne verbinden und [Oracle](../../installation/using/configure-fda-oracle.md)

* Kampagne verbinden und [Netezza](../../installation/using/configure-fda-netezza.md)

* Kampagne verbinden und [Sybase IQ](../../installation/using/configure-fda-sybase.md)

* Kampagne verbinden und [Teradata](../../installation/using/configure-fda-teradata.md)

* Kampagne verbinden und [SAP HANA](../../installation/using/configure-fda-sap-hana.md)

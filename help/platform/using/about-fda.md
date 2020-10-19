---
title: Zugriff auf externe Datenbanken
description: Erfahren Sie, wie Sie auf Daten in einer externen Datenbank zugreifen und diese verarbeiten können
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: b447e316bed8e0e87d608679c147e6bd7b0815eb
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 98%

---


# Über Federated Data Access - FDA {#about-federated-data-access}

Adobe Campaign bietet die Option **Federated Data Access** (FDA), um in externen Datenbanken gespeicherte Informationen nutzen zu können. Auf diese Weise ist der Zugriff auf externe Daten möglich, ohne die Datenstruktur in Adobe Campaign zu verändern.

>[!CAUTION]
>
>Zugriff auf eine externe Datenbank über FDA ist nur bei On-Premise- oder hybriden Installationen möglich, es sei denn, es gibt Snowflake-Connectoren. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](https://helpx.adobe.com/de/campaign/kb/acc-on-prem-vs-hosted.html).

## Grundprinzip {#operating-principle}

Mit der FDA-Option können Sie Ihr Datenmodell in einer Drittanbieterdatenbank erweitern. Sie erkennt automatisch die Struktur der ausgewählten Tabellen und verwendet Daten aus den SQL-Quellen.

Um diese Funktion zu verwenden, gehen Sie folgendermaßen vor:

1. Sie benötigen eine externe Datenbank, die mit dem FDA-Modul von Adobe Campaign kompatibel ist. Die Liste mit Datenbanksystemen und kompatiblen Versionen finden Sie in der [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html). Benutzer benötigen zudem die [entsprechenden Berechtigungen](../../platform/using/remote-database-access-rights.md) für Adobe Campaign und die externe Datenbank.
1. [Installieren Sie die entsprechenden Treiber](../../platform/using/specific-configuration-database.md) für Ihre Datenbank auf dem Adobe-Campaign-Server.
1. [Erstellen und konfigurieren Sie ein externes Konto](../../platform/using/connecting-to-database.md), über das Sie die Verbindung zwischen Adobe Campaign und der externen Datenbank herstellen können. Weitere Informationen zu verfügbaren externen Konten finden Sie auf dieser [Seite](../../platform/using/external-accounts.md).
1. [Erstellen Sie das Schema](../../platform/using/creating-data-schema.md) der externen Datenbank in Adobe Campaign. Auf diese Weise können Sie die Datenstruktur der externen Datenbank identifizieren.
1. [Erstellen Sie abschließend ein neues Zielgruppen-Mapping](../../platform/using/defining-data-mapping.md) aus dem zuvor erstellten Schema, wenn die Empfänger Ihrer Sendungen aus der externen Datenbank stammen. Dies bringt gewisse Einschränkungen mit sich, vor allem in Bezug auf die Personalisierung der Sendungen.

Nachdem das Schema erstellt wurde, können Daten in Adobe Campaign-Workflows verarbeitet werden. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../workflow/using/accessing-an-external-database--fda-.md).

## Verfügbare externe Datenbanken {#external-database}

Unten finden Sie die Liste aller externen Datenbanken, die mit dem FDA-Modul von Adobe Campaign kompatibel sind:

* Microsoft Azure Synapse Analytics. Weiterführende Informationen hierzu finden Sie in diesem [Abschnitt](../../platform/using/specific-configuration-database.md#azure-external).
* Snowflake. Weiterführende Informationen hierzu finden Sie in diesem [Abschnitt](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake).
* Hadoop. Weiterführende Informationen hierzu finden Sie in diesem [Abschnitt](../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3).
* Oracle. Weiterführende Informationen hierzu finden Sie in diesem [Abschnitt](../../platform/using/specific-configuration-database.md#configure-access-to-oracle).
* Netezza. Weiterführende Informationen hierzu finden Sie in diesem [Abschnitt](../../platform/using/specific-configuration-database.md#configure-access-to-netezza).
* Sybase IQ. Weiterführende Informationen hierzu finden Sie in diesem [Abschnitt](../../platform/using/specific-configuration-database.md#configure-access-to-sybase-iq).
* Teradata. Weiterführende Informationen hierzu finden Sie in diesem [Abschnitt](../../platform/using/specific-configuration-database.md#configure-access-to-teradata).
* SAP HANA. Weiterführende Informationen hierzu finden Sie in diesem [Abschnitt](../../platform/using/specific-configuration-database.md).

## Best Practices und Empfehlungen {#best-practices-and-recommendations}

Die FDA-Option ist so konzipiert, dass Daten in externen Datenbanken mithilfe von Workflows im Batch-Modus bearbeitet werden können. Die Verwendung von FDA für andere Zwecke, z. B. für Einzeloperationen, erfordert besondere Vorsicht (Personalisierung, Interaction, Echtzeit-Sendungen etc.).

Vermeiden Sie möglichst Vorgänge, bei denen sowohl Adobe Campaign als auch die externe Datenbank zum Einsatz kommen. Gehen Sie dazu folgendermaßen vor:

* Exportieren Sie die Adobe-Campaign-Datenbank in die externe Datenbank und führen Sie die Aktionen nur in der externen Datenbank aus. Importieren Sie danach die Ergebnisse wieder in Adobe Campaign.
* Rufen Sie die Daten aus der externen Adobe-Campaign-Datenbank ab und führen Sie die Aktionen lokal durch.

Wenn Sie Ihre Sendungen unter Verwendung von Daten aus der externen Datenbank personalisieren möchten, rufen Sie die entsprechenden Daten über einen Workflow ab und stellen Sie sie in einer temporären Tabelle bereit. Personalisieren Sie dann Ihren Versand mit den Daten aus der temporären Tabelle.

## Einschränkungen {#limitations}

Die FDA-Option unterliegt den Einschränkungen des von Ihnen verwendeten externen Datenbanksystems.

Um die Leistung nicht zu beeinträchtigen, empfehlen wir, diese Funktionalität nicht zur Durchführung von Einzeloperationen zu verwenden (Versandpersonalisierung, Interaction-Modul, Echtzeit).

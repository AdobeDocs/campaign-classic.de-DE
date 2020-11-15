---
title: Zugriff auf externe Datenbanken
description: Erfahren Sie, wie Sie Daten in einer externen Datenbank aufrufen und verarbeiten können
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 99d766cb6234347ea2975f3c08a6ac0496619b41
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 36%

---


# Erste Schritte mit Federated Data Access {#about-federated-data-access}

Adobe Campaign bietet die Option **Federated Data Access** (FDA), um in externen Datenbanken gespeicherte Informationen nutzen zu können. Auf diese Weise ist der Zugriff auf externe Daten möglich, ohne die Datenstruktur in Adobe Campaign zu verändern.

## Voraussetzungen {#operating-principle}

Mit der FDA-Option können Sie Ihr Datenmodell in einer Drittanbieterdatenbank erweitern. Sie erkennt automatisch die Struktur der ausgewählten Tabellen und verwendet Daten aus den SQL-Quellen.

Um diese Funktion nutzen zu können, sind die Voraussetzungen unten aufgeführt:

* **Konfiguration**: außer zum Snowflake benötigen Sie ein **On-Premise** - oder **Hybrid** -Hostmodell, um Federated Data Access einzurichten. [Mehr dazu](../../installation/using/hosting-models.md)
* **Externe Datenbankversion**: Sie benötigen eine externe Datenbank, die mit dem Adobe Campaign FDA Modul kompatibel ist. Die Liste von Datenbanksystemen und kompatiblen Versionen wird in der Kampagne [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA)beschrieben.
* **Berechtigungen**: Die Benutzer müssen auch über die [erforderlichen Berechtigungen](../../installation/using/remote-database-access-rights.md) in Adobe Campaign und in der externen Datenbank verfügen.

## Einschränkungen {#limitations}

Die Option &quot;FDA&quot;wird zur Bearbeitung der Daten in externen Datenbanken im Stapelmodus in Workflows verwendet. Um Leistungsprobleme zu vermeiden, wird die Verwendung des FDA-Moduls im Rahmen eines einheitlichen Betriebs nicht empfohlen, z. B.: Personalisierung, Interaktion, Echtzeit-Nachrichten usw.

Vermeiden Sie möglichst Vorgänge, bei denen sowohl Adobe Campaign als auch die externe Datenbank zum Einsatz kommen. Gehen Sie dazu folgendermaßen vor:

* Exportieren Sie die Adobe-Campaign-Datenbank in die externe Datenbank und führen Sie die Aktionen nur in der externen Datenbank aus. Importieren Sie danach die Ergebnisse wieder in Adobe Campaign.

* Rufen Sie die Daten aus der externen Adobe-Campaign-Datenbank ab und führen Sie die Aktionen lokal durch.

Wenn Sie Ihre Sendungen unter Verwendung von Daten aus der externen Datenbank personalisieren möchten, rufen Sie die entsprechenden Daten über einen Workflow ab und stellen Sie sie in einer temporären Tabelle bereit. Personalisieren Sie dann Ihren Versand mit den Daten aus der temporären Tabelle.

Die Option &quot;FDA&quot;unterliegt den Einschränkungen des von Ihnen verwendeten externen Datenbanksystems.

## Empfehlungen {#recommendations}

### Erstellen von temporären Schemas {#create-temporary-schemas}

Sie können mehrere Zugriffe auf die externe Greenplum-Datenbank über FDA verwalten. Mit einer dedizierten Option können Sie ein funktionierendes Schema direkt beim Konfigurieren des Externen Kontos erstellen.

![](assets/fda_work_table.png)

>[!NOTE]
>
>Diese Option ist nur mit PostgreSQL Greenplum verfügbar.

### Optimize email personalization with external data {#optimizing-email-personalization-with-external-data}

Sie können die Personalisierung von Nachrichten in einem dedizierten Arbeitsablauf vorbereiten. Verwenden Sie dazu die Option **[!UICONTROL Personalisierungsdaten mit einer Workflow]** -Option vorbereiten, die auf der Registerkarte &quot; **[!UICONTROL Analyse]** &quot;der Eigenschaften des Versands verfügbar ist.

Während der Analyse des Versands wird mit dieser Option automatisch ein Workflow erstellt und ausgeführt, in dem alle mit der Zielgruppe verknüpften Daten in einer temporären Tabelle gespeichert werden, einschließlich der Daten aus Tabellen, die in einer externen Datenbank verknüpft sind.

Diese Option verbessert die Leistung beim Ausführen des Personalisierungsschritts erheblich.

### Use data from an external database in a workflow {#using-data-from-an-external-database-in-a-workflow}

In mehreren Adobe Campaign-Workflow-Aktivitäten können Sie die in einer externen Datenbank gespeicherten Daten verwenden.

* **Nach externen Daten** filtern - Mit der Aktivität &quot; [Abfrage](../../workflow/using/targeting-data.md#selecting-data) &quot;können Sie externe Daten hinzufügen und in den definierten Filterkonfigurationen verwenden. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../workflow/using/targeting-data.md#selecting-data).

* **Untergruppen** erstellen - Mit der Aktivität &quot; [Teilen](../../workflow/using/split.md) &quot;können Sie Untergruppen erstellen. Sie können externe Daten verwenden, um die zu verwendenden Filterkriterien zu definieren. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../workflow/using/split.md).

* **Externe Datenbank** laden: Sie können die externen Daten in der Aktivität [Datenladevorgang](../../workflow/using/data-loading--rdbms-.md) (RDBMS) verwenden. Weiterführende Informationen finden Sie auf [dieser Seite](../../workflow/using/data-loading--rdbms-.md).

* **Hinzufügen von Informationen und Links** - Mit der Aktivität &quot; [Anreicherung](../../workflow/using/enrichment.md) &quot;können Sie zusätzliche Daten zur Arbeitstabelle des Workflows hinzufügen und Links zu einer externen Tabelle erstellen. In diesem Zusammenhang kann es Daten aus einer externen Datenbank verwenden. Weiterführende Informationen finden Sie auf [dieser Seite](../../workflow/using/enrichment.md).

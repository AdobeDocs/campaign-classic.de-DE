---
solution: Campaign Classic
product: campaign
title: Best Practices und Einschränkungen der Kampagne FDA
description: Bewährte Verfahren und Einschränkungen beim Arbeiten mit einer externen Datenbank (FDA)
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
translation-type: tm+mt
source-git-commit: 3b5a6e6f03d9cb26ed372c3df069cbada36756a2
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 30%

---

# Best Practices und Einschränkungen

## Erstellen Sie temporäre Schema {#create-temporary-schemas}

Sie können mehrere Zugriffe auf die externe Greenplum-Datenbank über FDA verwalten. Mit einer dedizierten Option können Sie ein funktionierendes Schema direkt beim Konfigurieren des Externen Kontos erstellen.

![](assets/fda_work_table.png)

>[!NOTE]
>
>Diese Option ist nur mit PostgreSQL Greenplum verfügbar.

## Optimieren Sie die E-Mail-Personalisierung mit externen Daten {#optimizing-email-personalization-with-external-data}.

Sie können die Personalisierung von Nachrichten in einem dedizierten Arbeitsablauf vorbereiten. Verwenden Sie dazu die Option **[!UICONTROL Personalisierungsdaten mit einer Workflow]**-Option vorbereiten, die auf der Registerkarte **[!UICONTROL Analyse]** der Eigenschaften des Versands verfügbar ist.

Während der Analyse des Versands wird mit dieser Option automatisch ein Workflow erstellt und ausgeführt, in dem alle mit der Zielgruppe verknüpften Daten in einer temporären Tabelle gespeichert werden, einschließlich der Daten aus Tabellen, die in einer externen Datenbank verknüpft sind.

Diese Option verbessert die Leistung beim Ausführen des Personalisierungsschritts erheblich.

## Daten aus einer externen Datenbank in einem Workflow {#using-data-from-an-external-database-in-a-workflow} verwenden

In mehreren Adobe Campaign-Workflow-Aktivitäten können Sie die in einer externen Datenbank gespeicherten Daten verwenden.

* **Nach externen Daten**  filtern - Die  [](../../workflow/using/targeting-data.md#selecting-data) Queryactivity ermöglicht es Ihnen, externe Daten hinzuzufügen und sie in den definierten Filterkonfigurationen zu verwenden. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../workflow/using/targeting-data.md#selecting-data).

* **Untergruppen**  erstellen - Mit der  [](../../workflow/using/split.md) Splitactivity können Sie Untergruppen erstellen. Sie können externe Daten verwenden, um die zu verwendenden Filterkriterien zu definieren. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../workflow/using/split.md).

* **Externe Datenbank**  laden: Sie können die externen Daten in der Aktivität  [Data loading](../../workflow/using/data-loading--rdbms-.md) (RDBMS) verwenden. Weiterführende Informationen finden Sie auf [dieser Seite](../../workflow/using/data-loading--rdbms-.md).

* **Hinzufügen von Informationen und Links**  - Mit der  [](../../workflow/using/enrichment.md) Anreicherungsaktivität können Sie der Arbeitstabelle des Workflows zusätzliche Daten hinzufügen und Links zu einer externen Tabelle erstellen. In diesem Zusammenhang kann es Daten aus einer externen Datenbank verwenden. Weiterführende Informationen finden Sie auf [dieser Seite](../../workflow/using/enrichment.md).

## Einschränkungen der FDA {#limitations}

Die Option &quot;FDA&quot;wird zur Bearbeitung der Daten in externen Datenbanken im Stapelmodus in Workflows verwendet. Um Leistungsprobleme zu vermeiden, wird die Verwendung des FDA-Moduls im Rahmen eines einheitlichen Betriebs nicht empfohlen, z. B.: Personalisierung, Interaktion, Echtzeit-Nachrichten usw.

Vermeiden Sie möglichst Vorgänge, bei denen sowohl Adobe Campaign als auch die externe Datenbank zum Einsatz kommen. Gehen Sie dazu folgendermaßen vor:

* Exportieren Sie die Adobe-Campaign-Datenbank in die externe Datenbank und führen Sie die Aktionen nur in der externen Datenbank aus. Importieren Sie danach die Ergebnisse wieder in Adobe Campaign.

* Rufen Sie die Daten aus der externen Adobe-Campaign-Datenbank ab und führen Sie die Aktionen lokal durch.

Wenn Sie Ihre Sendungen unter Verwendung von Daten aus der externen Datenbank personalisieren möchten, rufen Sie die entsprechenden Daten über einen Workflow ab und stellen Sie sie in einer temporären Tabelle bereit. Personalisieren Sie dann Ihren Versand mit den Daten aus der temporären Tabelle.

Die Option &quot;FDA&quot;unterliegt den Einschränkungen des von Ihnen verwendeten externen Datenbanksystems.

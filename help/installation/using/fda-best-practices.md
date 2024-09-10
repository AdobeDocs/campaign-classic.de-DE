---
product: campaign
title: Best Practices und Einschränkungen der Campaign FDA
description: Best Practices und Einschränkungen beim Arbeiten mit einer externen Datenbank (FDA)
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
source-git-commit: 586456f27dbc039ecb39cc8bd1f6dbdf8af823be
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 57%

---

# Best Practices und Einschränkungen



## E-Mail-Personalisierung mit externen Daten optimieren {#optimizing-email-personalization-with-external-data}

Sie können die Nachrichtenpersonalisierung in einem speziellen Workflow vorab verarbeiten. Verwenden Sie dazu die Option **[!UICONTROL Personalisierungsdaten mit einem Workflow vorbereiten]**, die auf der Registerkarte **[!UICONTROL Analyse]** der Versandeigenschaften verfügbar ist.

Diese Option ermöglicht es, im Zuge der Versandanalyse automatisch einen Workflow zu erstellen und auszuführen, welcher alle auf eine Zielgruppe bezogenen Daten in einer temporären Tabelle speichert (insbesondere Daten aus verknüpften Tabellen einer externen Datenbank).

Diese Option verbessert die Performance beim Ausführen des Personalisierungsschritts erheblich.

## Daten aus einer externen Datenbank in einem Workflow verwenden {#using-data-from-an-external-database-in-a-workflow}

Bei mehreren Adobe Campaign-Workflow-Aktivitäten können Sie die in einer externen Datenbank gespeicherten Daten verwenden.

* **Nach externen Daten filtern** - Mit der Aktivität [Abfrage](../../workflow/using/targeting-data.md#selecting-data) können Sie externe Daten hinzufügen und in den definierten Filterkonfigurationen verwenden. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../workflow/using/targeting-data.md#selecting-data).

* **Segmente erstellen** – Die Aktivität [Aufspaltung](../../workflow/using/split.md) ermöglicht die Erstellung von Segmenten. Sie können externe Daten verwenden, um die zu verwendenden Filterkriterien zu definieren. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../workflow/using/split.md).

* **Externe Datenbank laden** - Sie können die externen Daten in der Aktivität [Laden der Daten](../../workflow/using/data-loading-rdbms.md) (RDBMS) verwenden. Weitere Informationen finden Sie auf [dieser Seite](../../workflow/using/data-loading-rdbms.md).

* **Informationen und Links hinzufügen** – Die Aktivität [Anreicherung](../../workflow/using/enrichment.md) ermöglicht das Hinzufügen zusätzlicher Daten zur Arbeitstabelle des Workflows sowie von Links zu einer externen Tabelle. In diesem Zusammenhang kann es Daten aus einer externen Datenbank verwenden. Weitere Informationen finden Sie auf [dieser Seite](../../workflow/using/enrichment.md).

## Schutzmechanismen und Einschränkungen {#fda-limitations}

Die FDA-Option wurde entwickelt, um die Daten in externen Datenbanken im Batch-Modus in Workflows zu bearbeiten. Um Performance-Probleme zu vermeiden, wird nicht empfohlen, das FDA-Modul im Kontext von Einzeloperationen zu verwenden, etwa Personalisierung, Interaktion oder Echtzeit-Messaging.

Das Targeting von Daten aus einer Datenbank und das Filtern der Ergebnisse mithilfe einer Filterdimension, die zu einer anderen Datenbank gehört, wird nicht unterstützt. Tabellen, die sich in unterschiedlichen Datenquellen befinden, können nicht in einer Abfrage zusammengefügt werden. Sie können diese Einschränkung mithilfe anderer Workflow-Aktivitäten wie Dimensionsänderung umgehen.

Vermeiden Sie möglichst Vorgänge, bei denen sowohl die Adobe Campaign als auch die externe Datenbank verwendet werden müssen. Best Practice:

* Exportieren Sie die Adobe Campaign-Datenbank in die externe Datenbank und führen Sie die Aktionen nur in der externen Datenbank aus. Importieren Sie danach die Ergebnisse wieder in Adobe Campaign.

* Rufen Sie die Daten aus der externen Adobe Campaign-Datenbank ab und führen Sie die Aktionen lokal durch.

Wenn Sie Ihre Sendungen unter Verwendung von Daten aus der externen Datenbank personalisieren möchten, rufen Sie die entsprechenden Daten über einen Workflow ab und stellen Sie sie in einer temporären Tabelle bereit. Personalisieren Sie dann Ihren Versand mit den Daten aus der temporären Tabelle.

Die FDA-Option unterliegt den Einschränkungen des von Ihnen verwendeten externen Datenbanksystems.

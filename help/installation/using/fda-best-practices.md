---
product: campaign
title: Best Practices und Einschränkungen von Campaign FDA
description: Best Practices und Einschränkungen beim Arbeiten mit einer externen Datenbank (FDA)
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 57%

---

# Best Practices und Einschränkungen



## Optimieren der E-Mail-Personalisierung mit externen Daten {#optimizing-email-personalization-with-external-data}

Sie können die Nachrichtenpersonalisierung in einem speziellen Workflow vorab verarbeiten. Verwenden Sie dazu die Option **[!UICONTROL Personalisierungsdaten mit einem Workflow vorbereiten]**, die auf der Registerkarte **[!UICONTROL Analyse]** der Versandeigenschaften verfügbar ist.

Diese Option ermöglicht es, im Zuge der Versandanalyse automatisch einen Workflow zu erstellen und auszuführen, welcher alle auf eine Zielgruppe bezogenen Daten in einer temporären Tabelle speichert (insbesondere Daten aus verknüpften Tabellen einer externen Datenbank).

Diese Option verbessert die Performance beim Ausführen des Personalisierungsschritts erheblich.

## Verwenden von Daten aus einer externen Datenbank in einem Workflow {#using-data-from-an-external-database-in-a-workflow}

In mehreren Adobe Campaign-Workflow-Aktivitäten können Sie die in einer externen Datenbank gespeicherten Daten verwenden.

* **Filter für externe Daten** - Die Aktivität [Abfrage](../../workflow/using/targeting-data.md#selecting-data) ermöglicht es Ihnen, externe Daten hinzuzufügen und sie in den definierten Filterkonfigurationen zu verwenden. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../workflow/using/targeting-data.md#selecting-data).

* **Segmente erstellen** – Die Aktivität [Aufspaltung](../../workflow/using/split.md) ermöglicht die Erstellung von Segmenten. Sie können externe Daten verwenden, um die zu verwendenden Filterkriterien zu definieren. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../workflow/using/split.md).

* **Externe Datenbank laden** - Sie können die externen Daten in der Aktivität [Laden](../../workflow/using/data-loading-rdbms.md) (RDBMS) verwenden. Weitere Informationen finden Sie auf [dieser Seite](../../workflow/using/data-loading-rdbms.md).

* **Informationen und Links hinzufügen** – Die Aktivität [Anreicherung](../../workflow/using/enrichment.md) ermöglicht das Hinzufügen zusätzlicher Daten zur Arbeitstabelle des Workflows sowie von Links zu einer externen Tabelle. In diesem Kontext können Daten aus einer externen Datenbank verwendet werden. Weitere Informationen finden Sie auf [dieser Seite](../../workflow/using/enrichment.md).

## Schutzmechanismen und Einschränkungen {#fda-limitations}

Die FDA-Option dient zur Bearbeitung der Daten in externen Datenbanken im Batch-Modus in Workflows. Um Performance-Probleme zu vermeiden, wird nicht empfohlen, das FDA-Modul im Kontext von Einzeloperationen zu verwenden, etwa Personalisierung, Interaktion oder Echtzeit-Messaging.

Das Targeting von Daten aus einer Datenbank und das Filtern der Ergebnisse mithilfe einer Filterdimension, die zu einer anderen Datenbank gehört, wird nicht unterstützt. Sie können Tabellen, die sich in verschiedenen Datenquellen befinden, nicht in einer Abfrage verknüpfen. Sie können diese Einschränkung mithilfe anderer Workflow-Aktivitäten wie Dimensionsänderung überwinden.

Vermeiden Sie die Vorgänge, die sowohl die Adobe Campaign als auch die externe Datenbank verwenden müssen, so weit wie möglich. Best Practice ist Folgendes:

* Exportieren Sie die Adobe Campaign-Datenbank in die externe Datenbank und führen Sie die Aktionen nur in der externen Datenbank aus. Importieren Sie danach die Ergebnisse wieder in Adobe Campaign.

* Rufen Sie die Daten aus der externen Adobe Campaign-Datenbank ab und führen Sie die Aktionen lokal durch.

Wenn Sie Ihre Sendungen unter Verwendung von Daten aus der externen Datenbank personalisieren möchten, rufen Sie die entsprechenden Daten über einen Workflow ab und stellen Sie sie in einer temporären Tabelle bereit. Personalisieren Sie dann Ihren Versand mit den Daten aus der temporären Tabelle.

Die FDA-Option unterliegt den Einschränkungen des von Ihnen verwendeten externen Datenbanksystems.

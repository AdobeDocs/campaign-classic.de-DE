---
product: campaign
title: Best Practices und Einschränkungen der Campaign FDA
description: Best Practices und Einschränkungen beim Arbeiten mit einer externen Datenbank (FDA)
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 88%

---

# Best Practices und Einschränkungen



## Optimieren von E-Mail-Personalisierung mit externen Daten {#optimizing-email-personalization-with-external-data}

Sie können die Nachrichtenpersonalisierung in einem speziellen Workflow vorab verarbeiten. Verwenden Sie dazu die Option **[!UICONTROL Personalisierungsdaten mit einem Workflow vorbereiten]**, die auf der Registerkarte **[!UICONTROL Analyse]** der Versandeigenschaften verfügbar ist.

Diese Option ermöglicht es, im Zuge der Versandanalyse automatisch einen Workflow zu erstellen und auszuführen, welcher alle auf eine Zielgruppe bezogenen Daten in einer temporären Tabelle speichert (insbesondere Daten aus verknüpften Tabellen einer externen Datenbank).

Diese Option verbessert die Leistung beim Ausführen des Personalisierungsschritts erheblich.

## Daten aus einer externen Datenbank in einem Workflow verwenden {#using-data-from-an-external-database-in-a-workflow}

Bei mehreren Adobe Campaign-Workflow-Aktivitäten können Sie die in einer externen Datenbank gespeicherten Daten verwenden.

* **Filter für externe Daten** – Die Aktivität [Abfrage](../../workflow/using/targeting-data.md#selecting-data) ermöglicht es Ihnen, externe Daten hinzuzufügen und in den definierten Filterkonfigurationen zu verwenden. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../workflow/using/targeting-data.md#selecting-data).

* **Segmente erstellen** – Die Aktivität [Aufspaltung](../../workflow/using/split.md) ermöglicht die Erstellung von Segmenten. Sie können externe Daten verwenden, um die zu verwendenden Filterkriterien zu definieren. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../workflow/using/split.md).

* **Externe Datenbank laden** – Sie können die externen Daten in der Aktivität [](../../workflow/using/data-loading--rdbms-.md)Laden (DBMS) verwenden. Weitere Informationen finden Sie auf [dieser Seite](../../workflow/using/data-loading--rdbms-.md).

* **Informationen und Links hinzufügen** – Die Aktivität [Anreicherung](../../workflow/using/enrichment.md) ermöglicht das Hinzufügen zusätzlicher Daten zur Arbeitstabelle des Workflows sowie von Links zu einer externen Tabelle. In diesem Kontext können Daten aus einer externen Datenbank verwendet werden. Weitere Informationen finden Sie auf [dieser Seite](../../workflow/using/enrichment.md).

## FDA-Beschränkungen {#limitations}

Die FDA-Option wird zur Bearbeitung der Daten in externen Datenbanken im Batch-Modus in Workflows verwendet. Um Leistungsprobleme zu vermeiden, wird nicht empfohlen, das FDA-Modul im Kontext von Einzeloperationen zu verwenden, etwa Personalisierung, Interaktion oder Echtzeit-Messaging.

Vermeiden Sie möglichst Vorgänge, bei denen sowohl Adobe Campaign als auch die externe Datenbank zum Einsatz kommen. Gehen Sie dazu folgendermaßen vor:

* Exportieren Sie die Adobe Campaign-Datenbank in die externe Datenbank und führen Sie die Aktionen nur in der externen Datenbank aus. Importieren Sie danach die Ergebnisse wieder in Adobe Campaign.

* Rufen Sie die Daten aus der externen Adobe Campaign-Datenbank ab und führen Sie die Aktionen lokal durch.

Wenn Sie Ihre Sendungen mithilfe von Daten aus der externen Datenbank personalisieren möchten, sammeln Sie die Daten zur Verwendung in einem Workflow, um sie in einer temporären Tabelle zur Verfügung zu stellen. Verwenden Sie dann die Daten aus der temporären Tabelle, um Ihren Versand zu personalisieren.

Die FDA-Option unterliegt den Einschränkungen des von Ihnen verwendeten externen Datenbanksystems.

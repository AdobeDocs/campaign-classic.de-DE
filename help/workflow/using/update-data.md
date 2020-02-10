---
title: Daten aktualisieren
seo-title: Daten aktualisieren
description: Daten aktualisieren
seo-description: null
page-status-flag: never-activated
uuid: 5f3ab7c8-175a-4b06-a50c-edc97b226e3c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: c94ce5b7-aa8a-4ea2-845d-68c9c7dc2a7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Daten aktualisieren{#update-data}

Die **Daten-Update**-Aktivität ermöglicht eine gebündelte Aktualisierung von Datenbankfeldern.

## Aktionstyp {#operation-type}

The **[!UICONTROL Operation type]** field lets you choose the process to be carried out on the data in the database:

* **[!UICONTROL Insert or update]**: Daten hinzufügen oder aktualisieren, wenn sie bereits hinzugefügt wurden.
* **[!UICONTROL Insert]**: nur Daten hinzufügen.
* **[!UICONTROL Update]**: nur Daten aktualisieren.
* **[!UICONTROL Update and merge collections]**: aktualisieren Sie die Daten und wählen Sie einen &quot;Master&quot;-Datensatz und verknüpfen Sie dann Elemente, die mit den Duplikaten in diesem Master-Datensatz verknüpft sind. Duplikate können dann gelöscht werden, ohne verwaiste angehängte Elemente zu erstellen.
* **[!UICONTROL Delete]**: Daten löschen.

![](assets/s_advuser_update_data_1.png)

Im **[!UICONTROL Batch size]** Feld können Sie die Anzahl der zu aktualisierenden eingehenden Übergangselemente auswählen. Wenn Sie beispielsweise 500 angeben, werden die ersten 500 verarbeiteten Datensätze aktualisiert.

## Datensatz-Identifizierung {#record-identification}

Geben Sie an, auf welche Weise die Datensätze der Datenbank identifiziert werden können:

* Wenn sich Dateneinträge auf eine vorhandene Targeting-Dimension beziehen, wählen Sie die **[!UICONTROL By directly using the targeting dimension]** Option aus und wählen Sie sie im **[!UICONTROL Updated dimension]** Feld aus.

   You can display the fields for the selected dimension using the **[!UICONTROL Edit this link]** magnifying glass button.

* Wenn die eingehenden Daten keiner existierenden Zielgruppendimension entsprechen, können Sie entweder eine oder mehrere Relationen angeben, die die Identifizierung der Daten ermöglichen, oder Abstimmschlüssel verwenden.

![](assets/s_advuser_update_data_2.png)

## Auswahl der zu aktualisierenden Felder {#selecting-the-fields-to-be-updated}

Verwenden Sie diese **[!UICONTROL Automatically associate fields with the same name]** Option, damit Adobe Campaign die zu aktualisierenden Felder automatisch identifiziert.

![](assets/s_advuser_update_data_3b.png)

You can also use the **[!UICONTROL Insert]** icon to manually select the database fields to be updated.

![](assets/s_advuser_update_data_3.png)

Wählen Sie alle zu aktualisierenden Felder aus und fügen Sie bei Bedarf Bedingungen hinzu, je nachdem, welche Aktualisierung durchgeführt werden soll. Verwenden Sie dazu die **[!UICONTROL Taken into account if]** Spalte. Bedingungen werden nacheinander und in der Reihenfolge in der Liste angewendet. Verwenden Sie die Pfeile auf der rechten Seite, um die Reihenfolge der Updates zu ändern.

Ein Zielfeld kann mehrmals verwendet werden.

Innerhalb eines **[!UICONTROL Insert or update]** Vorgangs können Sie die Kampagne einzeln oder für jedes Feld auswählen. Wählen Sie dazu den gewünschten Wert in der **[!UICONTROL Operation]** Spalte aus.

![](assets/s_advuser_update_data_5.png)

The **[!UICONTROL modifiedDate]**, **[!UICONTROL modifiedBy]**, **[!UICONTROL createdDate]** and **[!UICONTROL createdBy]** fields are updated automatically during data updates, unless their management mode is configured specifically in the field update table.

Nur Datensätze, die mindestens eine Änderung aufweisen, werden aktualisiert. Alle anderen bleiben unverändert.

The **[!UICONTROL Advanced parameters]** link lets you specify additional options to deal with updating data as well as managing duplicates. Sie können auch:

* **[!UICONTROL Disable automatic key management]**.
* **[!UICONTROL Disable audit]**.
* **[!UICONTROL Empty the destination value if the source value is empty (NULL)]**. Diese Option ist standardmäßig automatisch aktiviert.
* **[!UICONTROL Update all columns with matching names]**.
* Specify conditions that consider source elements using an expression in the **[!UICONTROL Enabled if]** field.
* Geben Sie Bedingungen an, bei denen Duplikate mit einem Ausdruck verwendet werden sollen. Wenn Sie die **[!UICONTROL Ignore records which concern the same target]** Option aktivieren, wird nur der erste in der Liste der Ausdrücke berücksichtigt.

**[!UICONTROL Generate an outbound transition]**

Erzeugt eine ausgehende Transition im Anschluss an die Aktivität. Im Allgemeinen bildet die Daten-Update-Aktivität den Schlusspunkt eines Zielgruppen-Workflows. Aus diesem Grund, wird die ausgehende Transition nicht standardmäßig erzeugt.

**[!UICONTROL Generate an outbound transition for the rejects]**

Erzeugt eine ausgehende Transition, welche die Datensätze enthält, die im Zuge der Aktualisierung nicht korrekt verarbeitet werden konnten (z. B. Dubletten). Im Allgemeinen bildet die Daten-Update-Aktivität den Schlusspunkt eines Zielgruppen-Workflows. Aus diesem Grund, wird die ausgehende Transition nicht standardmäßig erzeugt.

## Aktualisierung und Fusion von Kollektionen {#updating-and-merging-collections}

Die Aktualisierung mit Fusion von Kollektionen ermöglicht die Aktualisierung von Daten eines Datensatzes mit Informationen, die aus einem oder mehreren sekundären Datensätzen stammen. Auf diese Weise werden die Datensätze zu einem einzigen verschmolzen. Hierbei sind eine Reihe von Regeln zu beachten.

>[!NOTE]
>
>Diese Option bietet auch die Möglichkeit, Referenzen zu sekundären Datensätzen in Workflow-Arbeitstabellen (targetWorkflow), Sendungen (targetDelivery) und Listen (targetList) zu verarbeiten. Wenn vorhanden, erscheinen diese Relationen in der Auswahlliste der Felder und Kollektionen.

1. Wählen Sie den **[!UICONTROL Update and merge collections]** Vorgang aus.

   ![](assets/update_and_merge_collections1.png)

1. Geben Sie in Reihenfolge der Prioritäten die Relationen an, die die Identifizierung des Hauptdatensatzes ermöglichen. Je nach eingehender Transition können die möglichen Relationen variieren.

   ![](assets/update_and_merge_collections2.png)

1. Geben Sie die in den Hauptdatensatz zu verschiebenden Kollektionen und die zu aktualisierenden Felder an.

   Definieren Sie die Regeln, die im Bezug auf die Felder gelten sollen, wenn ein oder mehrere sekundäre Datensätze identifiziert wurden. Hierzu können Sie sich des Ausdruckseditors bedienen. Weiterführende Informationen dazu finden Sie in diesem [Abschnitt](../../platform/using/defining-filter-conditions.md#building-expressions). Geben Sie beispielsweise an, dass bei Werten aus verschiedenen möglichen Datensätzen jeweils der zuletzt aktualisierte Wert beibehalten werden soll.

   Geben Sie die Bedingungen zur Berücksichtigung der Regel an.

   Geben Sie schließlich den Aktualisierungstyp an. Sie haben beispielsweise die Möglichkeit, die sekundären Datensätze nach der Datenaktualisierung zu löschen.

   Die Kollektionsfusion ermöglicht die Verschmelzung von heterogenen Daten wie z. B. bei der Liste der Abonnements eines Empfängers. Mithilfe der Regeln kann einer neuer, auf den sekundären Datensätzen beruhender Abonnementverlauf erstellt oder die Liste der Abonnements eines sekundären Datensatzes zum primären Datensatz verschoben werden.

1. Specify the order in which you would like the secondary records to be processed, by selecting **[!UICONTROL Advanced parameters]** > **[!UICONTROL Duplicates]**.

   ![](assets/update_and_merge_collections3.png)

Die Daten der sekundären Datensätze werden dem Hauptdatensatz zugeordnet, wenn die definierten Regeln zutreffen. Je nach ausgewähltem Aktualisierungstyp werden die sekundären Datensätze nach der Fusion gegebenenfalls gelöscht.

## Anwendungsbeispiel: Daten-Update nach einer Anreicherung {#example--update-data-following-an-enrichment}

Der [Schritt 2: Das Schreiben von erweiterten Daten in den Tabellenabschnitt](../../workflow/using/creating-a-summary-list.md#step-2--writing-enriched-data-to-the--purchases--table) &quot;Einkäufe&quot;des Anwendungsfalls, in dem die Details zum Erstellen einer Notizliste ein Beispiel für eine Datenaktualisierung nach einer Anreicherungsaktivität bieten.

## Eingabeparameter {#input-parameters}

* tableName
* schema

Jedes eingehende Ereignis muss eine durch diese Parameter definierte Zielgruppe angeben.

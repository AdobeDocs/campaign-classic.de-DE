---
title: Zielgruppendaten
seo-title: Zielgruppendaten
description: Zielgruppendaten
seo-description: null
page-status-flag: never-activated
uuid: 90c46ae9-8f9d-4538-a0fe-92fb3373f863
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 79f1e85a-b5e6-4875-ac57-ab979fc57079
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Zielgruppendaten{#targeting-data}

## Abfragen erstellen {#creating-queries}

### Datenauswahl {#selecting-data}

Mit einer **[!UICONTROL Query]** Aktivität können Sie Grunddaten zum Aufbau der Zielpopulation auswählen. For more on this, refer to [Creating a query](../../workflow/using/query.md#creating-a-query).

You can also use the following activities to query and refine data from the database: [Incremental query](../../workflow/using/incremental-query.md), [Read list](../../workflow/using/read-list.md).

Es ist möglich, zusätzliche Daten zu sammeln, die während des gesamten Arbeitsablaufs weitergeleitet und verarbeitet werden. Weitere Informationen finden Sie unter [Daten](../../workflow/using/query.md#adding-data) hinzufügen und zusätzliche Daten [bearbeiten](#editing-additional-data).

### Zusätzliche Daten bearbeiten {#editing-additional-data}

Nach Hinzufügung der zusätzlichen Daten können Sie diese bearbeiten oder zur Verfeinerung der in der Abfrageaktivität definierten Zielgruppe verwenden.

The **[!UICONTROL Edit additional data...]** link lets you view the added data and modify it or add to it.

![](assets/wf_add_data_edit_link.png)

Um Daten zu den zuvor definierten Ausgabespalten hinzuzufügen, wählen Sie sie in der Liste der verfügbaren Felder aus. Um eine neue Ausgabefalte zu erstellen, klicken Sie auf das **[!UICONTROL Add]** Symbol, wählen Sie das Feld aus und klicken Sie auf **[!UICONTROL Edit expression]**.

![](assets/query_add_an_output_column.png)

Kreuzen Sie den gewünschten Formeltyp an, beispielsweise Aggregat.

![](assets/query_add_an_output_column_formula.png)

Mit dieser **[!UICONTROL Add a sub-item]** Option können Sie berechnete Daten an die Sammlung anhängen. Auf diese Weise können Sie die zusätzlichen Daten aus der Sammlung auswählen oder aggregierte Berechnungen für Sammlungselemente definieren.

![](assets/query_add_columns_subscription_sub-element.png)

Die Unterelemente erscheinen als Unterordner der Kollektion, der sie angehören.

Sammlungen werden auf der **[!UICONTROL Collections]** Unterregisterkarte angezeigt. Sie können die erfassten Elemente filtern, indem Sie auf das Symbol der ausgewählten Sammlung klicken **[!UICONTROL Detail]** . Mit dem Filterassistenten können Sie die erfassten Daten auswählen und die Filterbedingungen festlegen, die auf die Daten in der Sammlung angewendet werden sollen.

![](assets/query_add_columns_collection.png)

### Zielgruppe mithilfe zusätzlicher Daten einschränken {#refining-the-target-using-additional-data}

Die zusätzlichen erfassten Daten ermöglichen Ihnen eine Feinabstimmung der Datenfilterung in der Datenbank. Klicken Sie dazu auf den **[!UICONTROL Refine the target using additional data...]** Link: Dadurch können Sie die hinzugefügten Daten überfiltern.

![](assets/wf_add_data_use_additional_data.png)

### Daten vereinheitlichen {#homogenizing-data}

Bei Aktivitäten **[!UICONTROL Union]** oder **[!UICONTROL Intersection]** Typaktivitäten können Sie festlegen, dass nur freigegebene zusätzliche Daten konsistent bleiben. In diesem Fall enthält die Tabelle für die temporäre Ausgabe dieser Aktivität nur die zusätzlichen Daten, die in allen Inbound-Sets gefunden werden.

![](assets/option-common_additionnal_col_only.png)

### Mit Zusatzdaten abstimmen {#reconciliation-with-additional-data}

Während der Datenabgleichungsphasen (**[!UICONTROL Union]**, **[!UICONTROL Intersection]** usw.) -Aktivitäten) können Sie die Spalten auswählen, die für die Datenversöhnung verwendet werden sollen, aus den zusätzlichen Spalten. Konfigurieren Sie dazu einen Abgleich für eine Auswahl von Spalten und geben Sie den Hauptsatz an. Wählen Sie dann die Spalten in der unteren Spalte des Fensters aus, wie im folgenden Beispiel gezeigt:

![](assets/select-column-and-join.png)

### Teilmengen erstellen {#creating-subsets}

Mit der **[!UICONTROL Split]** Aktivität können Sie Untergruppen zu Kriterien erstellen, die über Extrahierungsanfragen definiert wurden. Wenn Sie für jede Untergruppe eine Filterbedingung für die Population bearbeiten, greifen Sie dann auf die Standardabfrageaktivität zu, mit der Sie die Bedingungen für die Zielsegmentierung definieren können.

Als Filterbedingungen können hier entweder nur die Zusatzdaten oder Zusatzdaten und Zielgruppendaten verwendet werden. Wenn Sie über die Option **Federated Data Access** verfügen, können außerdem externe Daten herangezogen werden.

Weitere Informationen finden Sie unter [Erstellen von Untergruppen mit der Teilungsaktivität](#creating-subsets-using-the-split-activity).

## Daten segmentieren {#segmenting-data}

### Populationen vereinen (Vereinigung) {#combining-several-targets--union-}

Über die Vereinigungsaktivität lassen sich die Ergebnisse verschiedener Aktivitäten in einer Transition zusammenfassen. Dabei müssen die Mengen nicht zwingend homogen sein.

![](assets/join_reconciliation_options.png)

Zur Abstimmung der Daten stehen folgende Optionen zur Verfügung:

* **[!UICONTROL Keys only]**

   Diese Option kann bei homogenen Eingangspopulationen verwendet werden.

* **[!UICONTROL All columns in common]**

   Diese Option ermöglicht die Abstimmung der Datensätze über alle den verschiedenen Zielpopulationen gemeinsamen Spalten.

   Spalten werden in Adobe Campaign anhand der Spaltentitel identifiziert. Dabei werden geringfügige Unterschiede akzeptiert. Der Spaltentitel &#39;Email&#39; wird als identisch mit dem Titel &#39;@email&#39; gewertet.

* **[!UICONTROL A selection of columns]**

   Diese Option ermöglicht die Auswahl der Spalten, die zur Abstimmung herangezogen werden sollen.

   Wählen Sie zunächst die die Quelldaten enthaltende Hauptmenge aus und anschließend die Spalten, die den Join herstellen sollen.

   ![](assets/join_reconciliation_options_01.png)

   >[!CAUTION]
   >
   >Die Populationen werden im Rahmen der Abstimmung nicht auf Dubletten geprüft.

   Sie können die Populationsgröße auf eine gewisse Anzahl an Datensätzen begrenzen. Kreuzen Sie hierfür die entsprechende Option an und geben Sie die Anzahl an beizubehaltenden Datensätzen an.

   Geben Sie außerdem die Priorität der Eingangspopulationen an. Im unteren Bereich des Fensters werden die in die Vereinigungsaktivität eingehenden Transitionen aufgelistet. Die Reihenfolge kann mithilfe der blauen Pfeile rechts verändert werden.

   Die beibehaltenen Datensätze stammen zunächst aus der ersten eingehenden Transition und werden, falls die gewünschte Anzahl noch nicht erreicht ist, durch die Population der folgenden Transitionen ergänzt.

   ![](assets/join_limit_nb_priority.png)

### Gemeinsame Daten aus Populationen extrahieren (Schnittmenge) {#extracting-joint-data--intersection-}

![](assets/traitements.png)

Über die Schnittmengenaktivität lassen sich die Datensätze abrufen, die in allen eingehenden Populationen enthalten sind. Die Abstimmparameter dieser Aktivität sind dieselben wie im Abschnitt für die Vereinigung beschrieben.

Es ist außerdem möglich, nur eine Auswahl an Spalten oder nur die Spalten, die in allen eingehenden Populationen enthalten sind, abzurufen.

The intersection activity is detailed in the [Intersection](../../workflow/using/intersection.md) section.

### Populationen ausschließen (Ausschluss) {#excluding-a-population--exclusion-}

Über die Ausschlussaktivität lassen sich Elemente aus einer Population ausschließen, die auch in mindestens einer anderen Population enthalten sind. Die Zielgruppendimension am Aktivitätsausgang entspricht der der Hauptmenge.

Bei Bedarf können eingehende Tabellen bearbeitet werden. Um ein Ziel von einer anderen Dimension auszuschließen, muss dieses Ziel auf dieselbe Targeting-Dimension zurückgeführt werden wie das Hauptziel. Klicken Sie dazu auf die **[!UICONTROL Add]** Schaltfläche und geben Sie die Bedingungen für die Änderung der Dimension an.

Die Abstimmung der Daten kann über die Kennungen, eine Achsenänderung oder einen Join erfolgen. Ein Beispiel finden Sie unter Daten aus einer Liste [verwenden: Liste](../../workflow/using/importing-data.md#using-data-from-a-list--read-list)lesen

![](assets/exclusion_edit_add_rule_01.png)

### Teilmengen mithilfe der Aufspaltungs-Aktivität erstellen {#creating-subsets-using-the-split-activity}

The **[!UICONTROL Split]** activity is a standard activity which lets you create as many sets as necessary via one or several filtering dimensions, as well as generating either one output transition per subset or a unique transition.

Dabei können von der Transition übermittelte Zusatzdaten in den Filterbedingungen verwendet werden.

Zur Konfiguration wählen Sie zunächst die Bedingungen aus:

1. In your workflow, drag and drop a **[!UICONTROL Split]** activity.
1. Wählen Sie auf der **[!UICONTROL General]** Registerkarte die gewünschte Option aus: **[!UICONTROL Use data from the target and additional data]**, **[!UICONTROL Use the additional data only]** oder **[!UICONTROL Use external data]**.
1. Wenn die **[!UICONTROL Use data from the target and additional data]** Option ausgewählt ist, können Sie mit der Targeting-Dimension alle Daten verwenden, die durch den eingehenden Übergang übertragen werden.

   ![](assets/split-general-tab-options.png)

   Bei der Erstellung von Teilmengen werden die zuvor definierten Filterparameter genutzt.

   Um Filterbedingungen zu definieren, wählen Sie die **[!UICONTROL Add a filtering condition on the inbound population]** Option und klicken Sie auf den **[!UICONTROL Edit...]** Link. Geben Sie dann die Filterbedingungen für die Erstellung dieser Untergruppe an.

   ![](assets/split-subset-config-all-data.png)

   An example showing how to use filtering conditions in the **[!UICONTROL Split]** activity to segment the target into different populations is described in [this section](../../workflow/using/cross-channel-delivery-workflow.md).

   The **[!UICONTROL Label]** field lets you give the newly created subset a name, which will match the outbound transition.

   Sie können der Teilmenge außerdem einen Segment-Code zuweisen, welcher ihre Identifizierung und ihre Verwendung als Zielgruppe ermöglicht.

   Bei Bedarf können Sie die Targeting- und Filterdimensionen für jede Untergruppe, die Sie erstellen möchten, einzeln ändern. Bearbeiten Sie dazu die Filterbedingung der Untergruppe und aktivieren Sie die **[!UICONTROL Use a specific filtering dimension]** Option.

   ![](assets/split-subset-config-specific-filtering.png)

1. Wenn die **[!UICONTROL Use the additional data only]** Option aktiviert ist, werden nur zusätzliche Daten zum Filtern von Untergruppen angeboten.

   ![](assets/split-subset-config-additional-data-only.png)

1. If the **Federated Data Access** option is enabled, the **[!UICONTROL Use external data]** lets you process data in an external database which is already configured, or create a new connection to a database.

   ![](assets/split-subset-config-add_external_data.png)

   Weiterführende Informationen hierzu finden Sie in diesem [Abschnitt](../../platform/using/accessing-an-external-database.md).

Danach müssen neue Teilmengen hinzugefügt werden:

1. Click the **[!UICONTROL Add]** button and define the filtering conditions.

   ![](assets/wf_split_add_a_tab.png)

1. Define the filtering dimension in the **[!UICONTROL General]** tab of the activity (see above).It applies to all subsets by default.

   ![](assets/wf_split_edit_filtering.png)

1. Bei Bedarf können Sie die Filterdimension für jede Untergruppe einzeln ändern. Auf diese Weise können Sie einen Satz für alle Inhaber von Gold-Karten erstellen, einen für alle Empfänger, die im aktuellen Newsletter geklickt haben, und einen dritten für Personen zwischen 18 und 25 Jahren, die innerhalb der letzten 30 Tage im Geschäft einen Kauf getätigt haben, und alle mit derselben aufgeteilten Aktivität. Wählen Sie dazu die **[!UICONTROL Use a specific filtering dimension]** Option und dann den Kontext für die Datenfilterung aus.

   ![](assets/wf_split_change_dimension.png)

   >[!NOTE]
   >
   >Wenn Sie die Option &quot; **Federated Data Access** &quot;aktiviert haben, können Sie auf der Grundlage der Informationen in einer externen Datenbank Untergruppen erstellen. Wählen Sie dazu das Schema der externen Tabelle im **[!UICONTROL Targeting dimension]** Feld aus. For more on this, refer to [Accessing an external database (FDA)](../../workflow/using/accessing-an-external-database--fda-.md).

Standardmäßig erzeugt die Aufspaltungsaktivität für jede Teilmenge eine ausgehende Transition:

![](assets/wf_split_multi_outputs.png)

Sie können alle diese Untergruppen in einem einzigen Ausgabenübergang gruppieren. In diesem Fall ist der Link zu den entsprechenden Untergruppen beispielsweise im Segmentcode sichtbar. To do this, select the **[!UICONTROL Generate all subsets in the same table]** option.

![](assets/wf_split_select_option_single_output.png)

Dies ist beispielsweise dann interessant, wenn Sie eine einzige Versandaktivität anschließen, den Inhalt aber je nach Segment-Code der Teilmenge personalisieren möchten:

![](assets/wf_split_single_output.png)

Untergruppen können auch mithilfe der **[!UICONTROL Cells]** Aktivität erstellt werden. For more on this, refer to the [Cells](../../workflow/using/cells.md) section.

### Verwendung der gefilterten Daten {#using-targeted-data}

Nach Identifizierung und Aufbereitung der Daten können diese in folgenden Kontexten verwendet werden:

* Update der Datenbank im Anschluss an die verschiedenen Workflow-Aktivitäten.

   Weitere Informationen finden Sie unter [Daten](../../workflow/using/update-data.md)aktualisieren.

* Update von existierenden Listen.

   For more on this, refer to [List update](../../workflow/using/list-update.md).

* Vorbereitung und/oder Start von Sendungen direkt im Workflow.

   Weitere Informationen finden Sie unter [Auslieferung](../../workflow/using/delivery.md), [Liefersteuerung](../../workflow/using/delivery-control.md) und [Kontinuierliche Auslieferung](../../workflow/using/continuous-delivery.md).

## Data Management {#data-management}

In Adobe Campaign umfasst das Data Management eine Reihe von Aktivitäten, die mithilfe effizienterer und flexiblerer Tools komplexe Zielgruppenbestimmungen und Anreicherungen ermöglichen. Auf diese Weise ist es möglich, eine kohärente und individuelle Kommunikation mit Kontakten zu gewährleisten, indem beispielsweise Informationen zu Verträgen, Abonnements oder Reaktionen auf vorhergehende Sendungen verwendet werden. Das Data Management erlaubt es darüber hinaus, den Lebenszyklus von Daten während der Segmentierungsprozesse zu verfolgen, insbesondere werden:

* Zielbestimmungen vereinfacht, u. a. durch Einschluss von nicht im Datamart modelisierten Daten (Erstellung neuer Tabellen: lokale Ausdehnung auf jeden Zielgruppen-Workflow in Abhängigkeit von seiner Konfiguration);
* Zwischenergebnisse gespeichert und weitergegeben (interessant im Zuge der Zielbestimmung oder der Datenbankadministration);
* Zugriffe auf externe Datenbanken ermöglicht (optional), was die Berücksichtigung heterogener Datenbanken bei Zielbestimmungsprozessen zulässt.

Hierfür bietet Adobe Campaign:

* Datenerfassungsaktivitäten: [Dateiübertragung](../../workflow/using/file-transfer.md), [Datenladevorgang (Datei)](../../workflow/using/data-loading--file-.md), [Datenladevorgang (RDBMS)](../../workflow/using/data-loading--rdbms-.md), [Datenaktualisierung](../../workflow/using/update-data.md). Dieser erste Schritt der Datenerfassung bereitet die Daten so vor, dass sie in anderen Aktivitäten verarbeitet werden können. Mehrere Parameter müssen überwacht werden, um sicherzustellen, dass der Workflow korrekt ausgeführt wird und die erwarteten Ergebnisse liefert. Wenn Sie beispielsweise Daten importieren, muss der Primärschlüssel (Pkey) für diese Daten für jeden Datensatz eindeutig sein.
* Targeting activities having been enriched with Data Management options: [Query](../../workflow/using/query.md), [Union](../../workflow/using/union.md), [Intersection](../../workflow/using/intersection.md), [Split](../../workflow/using/split.md). This lets you configure a union or an intersection between data from several different targeting dimensions, as long as data reconciliation is possible.
* Datenkonvertierungsaktivitäten: [Anreicherung](../../workflow/using/enrichment.md), Dimension [ändern](../../workflow/using/change-dimension.md).

>[!CAUTION]
>
>In Workflows löst bei in Relation stehenden Tabellen das Löschen eines Elements der Quelltabelle nicht das Löschen der verbundenen Elemente aus.
>  
>Zum Beispiel zieht das Löschen eines Empfängers mithilfe eines Workflows nicht das Löschen seines Versandverlaufs nach sich. Wird ein Empfänger jedoch direkt im &#39;Empfänger&#39;-Ordner des Navigationsbaums gelöscht, werden auch alle anderen auf ihn bezogenen Daten gelöscht.

### Daten anreichern und ändern {#enriching-and-modifying-data}

Zusätzlich zur Targeting-Dimension können Sie mit der Filterdimension die Art der erfassten Daten angeben. Siehe [Targeting- und Filterdimensionen](../../workflow/using/building-a-workflow.md#targeting-and-filtering-dimensions).

Identifizierte und abgerufene Daten können angereichert, zusammengefasst und bearbeitet werden, um die Zielgruppenerstellung zu optimieren. Verwenden Sie dazu zusätzlich zu den Datenbearbeitungsaktivitäten, die im Abschnitt [Segmentierungsdaten](#segmenting-data) beschrieben sind, Folgendes:

* Mit der **[!UICONTROL Enrichment]** Aktivität können Sie vorübergehend Spalten zu einem Schema hinzufügen und Informationen zu bestimmten Elementen hinzufügen. Sie finden Sie im Abschnitt [Anreicherung](../../workflow/using/enrichment.md) des Projektarchivs.
* Mit der **[!UICONTROL Edit schema]** Aktivität können Sie die Struktur eines Schemas ändern. Sie wird im Abschnitt Schema[ ](../../workflow/using/edit-schema.md)bearbeiten des Repository der Aktivitäten beschrieben.
* Mit der **[!UICONTROL Change dimension]** Aktivität können Sie die Targeting-Dimension während des Zielkonstruktionszyklus ändern. Er wird im Abschnitt Dimension [ändern](../../workflow/using/change-dimension.md) detailliert beschrieben.


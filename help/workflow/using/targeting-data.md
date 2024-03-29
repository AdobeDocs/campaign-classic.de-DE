---
product: campaign
title: Zielgruppendaten
description: Weitere Informationen zu Zielgruppendaten in einem Workflow.
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
feature: Query Editor, Data Management, Workflows
exl-id: 74b82019-bdab-4442-84cf-5ad18d0db788
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '2033'
ht-degree: 81%

---

# Zielgruppendaten{#targeting-data}



## Erstellen von Abfragen {#creating-queries}

### Auswählen von Daten {#selecting-data}

Mit einer **[!UICONTROL Abfrageaktivität]** können Sie grundlegende Daten zum Aufbau der Zielpopulation auswählen. Weitere Informationen hierzu finden Sie unter [Abfragen erstellen](query.md#creating-a-query).

Sie können auch mithilfe der folgenden Aktivitäten Daten aus der Datenbank abfragen und weiter filtern: [Inkrementelle Abfrage ](incremental-query.md), [Liste lesen](read-list.md).

Es ist möglich, zusätzliche Daten zu sammeln, die während des gesamten Lebenszyklus des Workflows weitergeleitet und verarbeitet werden. Weitere Informationen hierzu finden Sie unter [Daten hinzufügen ](query.md#adding-data)und [Zusätzliche Daten bearbeiten](#editing-additional-data).

### Bearbeiten zusätzlicher Daten {#editing-additional-data}

Nach Hinzufügung der zusätzlichen Daten können Sie diese bearbeiten oder zur Verfeinerung der in der Abfrageaktivität definierten Zielgruppe verwenden.

Über den Link **[!UICONTROL Zusätzliche Daten bearbeiten...]** können Sie die hinzugefügten Daten anzeigen und sie gegebenenfalls ändern oder ergänzen.

![](assets/wf_add_data_edit_link.png)

Um Daten zu den zuvor definierten Ausgabespalten hinzuzufügen, wählen Sie sie in der Liste der verfügbaren Felder aus. Um eine neue Ausgabespalte zu erstellen, klicken Sie auf das **[!UICONTROL Hinzufügen]** Symbol, wählen Sie das Feld aus und klicken Sie auf **[!UICONTROL Ausdruck bearbeiten]**.

![](assets/query_add_an_output_column.png)

Kreuzen Sie den gewünschten Formeltyp an, beispielsweise Aggregat.

![](assets/query_add_an_output_column_formula.png)

Über die Option **[!UICONTROL Unterelement hinzufügen]** können die berechneten Daten in die Sammlung eingefügt werden. Sie können also aus der Sammlung stammende Zusatzdaten auswählen oder aus den Sammlungselementen Aggregate berechnen.

![](assets/query_add_columns_subscription_sub-element.png)

Die Unterelemente erscheinen als Unterordner der Sammlung, der sie angehören.

Sammlungen werden im **[!UICONTROL Sammlungen]** Unterregisterkarte. Sie können die erfassten Elemente filtern, indem Sie auf die **[!UICONTROL Detail]** Symbol der ausgewählten Sammlung. Im Filterassistenten können Sie die abgerufenen Daten auswählen und die auf die Daten der Kollektion anzuwendenden Filterbedingungen festlegen.

![](assets/query_add_columns_collection.png)

### Einschränken der Zielgruppe mithilfe zusätzlicher Daten {#refining-the-target-using-additional-data}

Die abgerufenen Zusatzdaten können die Filterung der Daten in der Datenbank verfeinern. Klicken Sie dazu auf die Schaltfläche **[!UICONTROL Verfeinern Sie die Zielgruppe mithilfe zusätzlicher Daten...]** -Link: ermöglicht die Überfilterung der hinzugefügten Daten.

![](assets/wf_add_data_use_additional_data.png)

### Vereinheitlichen von Daten {#homogenizing-data}

Mit den Aktivitäten vom Typ **[!UICONTROL Vereinigung]** und **[!UICONTROL Schnittmenge]** haben Sie die Möglichkeit, nur gemeinsame Zusatzdaten auszuwählen, um eine konsistente Datenbasis zu erhalten. In diesem Fall enthält die resultierende temporäre Arbeitstabelle dieser Aktivität nur die Zusatzdaten, die in allen eingehenden Teilmengen vorkommen.

![](assets/option-common_additionnal_col_only.png)

### Mit Zusatzdaten abstimmen {#reconciliation-with-additional-data}

In den Aktivitäten **[!UICONTROL Vereinigung]**, **[!UICONTROL Schnittmenge]** etc. besteht die Möglichkeit, die zur Abstimmung zu verwendenden Spalten aus den Zusatzdaten auszuwählen. Konfigurieren Sie hierzu die Abstimmung über eine Auswahl an Spalten und geben Sie die Hauptmenge an. Wählen Sie dann im unteren Fensterbereich wie dargestellt die entsprechenden Spalten aus:

![](assets/select-column-and-join.png)

### Erstellen von Teilmengen {#creating-subsets}

Über die **[!UICONTROL Aufspaltungsaktivität]** lassen sich gemäß bestimmten Kriterien entsprechende Teilmengen erstellen. Aktivieren Sie hierfür in der Teilmenge die Option zur Erstellung von Filterbedingungen und definieren Sie im sich öffnenden Abfragefenster die Kriterien zur Zielgruppensegmentierung.

Sie können eine Zielgruppe in mehrere Teilmengen unterteilen, indem Sie als Filterbedingungen oder zusätzlich zu den Zielgruppendaten nur Zusatzdaten verwenden. Wenn Sie die **Federated Data Access** -Option.

Weitere Informationen hierzu finden Sie unter [Teilmengen mithilfe der Aufspaltungs-Aktivität erstellen](#creating-subsets-using-the-split-activity).

## Segmentieren von Daten {#segmenting-data}

### Kombinieren mehrerer Zielgruppen (Vereinigung) {#combining-several-targets--union-}

Über die Vereinigungsaktivität lassen sich die Ergebnisse verschiedener Aktivitäten in einer Transition zusammenfassen. Dabei müssen die Mengen nicht zwingend homogen sein.

![](assets/join_reconciliation_options.png)

Zur Abstimmung der Daten stehen folgende Optionen zur Verfügung:

* **[!UICONTROL Nur die Schlüssel]**

  Diese Option kann bei homogenen Eingangspopulationen verwendet werden.

* **[!UICONTROL Alle gemeinsamen Spalten]**

  Diese Option ermöglicht die Abstimmung der Datensätze über alle den verschiedenen Zielpopulationen gemeinsamen Spalten.

  Spalten werden in Adobe Campaign anhand der Spaltentitel identifiziert. Dabei werden geringfügige Unterschiede akzeptiert. Der Spaltentitel &#39;Email&#39; wird als identisch mit dem Titel &#39;@email&#39; gewertet.

* **[!UICONTROL Auswahl an Spalten]**

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

### Extrahieren gemeinsamer Daten (Schnittmenge) {#extracting-joint-data--intersection-}

![](assets/traitements.png)

Über die Schnittmengenaktivität lassen sich die Datensätze abrufen, die in allen eingehenden Populationen enthalten sind. Die Abstimmparameter dieser Aktivität sind dieselben wie im Abschnitt für die Vereinigung beschrieben.

Es ist außerdem möglich, nur eine Auswahl an Spalten oder nur die Spalten, die in allen eingehenden Populationen enthalten sind, abzurufen.

Die Schnittmengenaktivität wird im Abschnitt [Schnittmenge](intersection.md) detailliert beschrieben.

### Ausschließen von Populationen (Ausschluss) {#excluding-a-population--exclusion-}

Über die Ausschlussaktivität lassen sich Elemente aus einer Population ausschließen, die auch in mindestens einer anderen Population enthalten sind. Die Zielgruppendimension am Aktivitätsausgang entspricht der der Hauptmenge.

Bei Bedarf können die eingehenden Tabellen angepasst werden. Um eine Zielgruppe aus einer anderen Dimension auszuschließen, muss diese Zielgruppe auf dieselbe Zielgruppendimension wie die Hauptzielgruppe zurückgesetzt werden. Klicken Sie dazu auf **[!UICONTROL Hinzufügen]** und geben Sie die Bedingungen für die Dimensionsänderung an.

Die Abstimmung der Daten kann über die Kennungen, eine Achsenänderung oder einen Join erfolgen. Ein Beispiel finden Sie unter [Verwendung von Daten aus einer Liste: Liste lesen](../../platform/using/import-export-workflows.md#using-data-from-a-list--read-list).

![](assets/exclusion_edit_add_rule_01.png)

### Erstellen von Teilmengen mithilfe der Aufspaltungs-Aktivität {#creating-subsets-using-the-split-activity}

Bei der Aktivität **[!UICONTROL Aufspaltung]** handelt es sich um eine Standardaktivität, die die unbegrenzte Erstellung von Teilmengen mit einer oder mehreren Filterdimensionen ermöglicht. Es kann eine ausgehende Transition pro Teilmenge oder eine eindeutige Transition erzeugt werden.

Dabei können von der Transition übermittelte Zusatzdaten in den Filterbedingungen verwendet werden.

Zur Konfiguration wählen Sie zunächst die Bedingungen aus:

1. Ziehen Sie in Ihren Workflow die Aktivität **[!UICONTROL Aufspaltung]**.
1. Wählen Sie im Tab **[!UICONTROL Allgemein]** die gewünschte Option aus: **[!UICONTROL Zielgruppendaten und zusätzliche Daten nutzen]**, **[!UICONTROL Nur zusätzliche Daten nutzen]** oder **[!UICONTROL Externe Daten nutzen]**.
1. Bei Auswahl der Option **[!UICONTROL Zielgruppendaten und zusätzliche Daten nutzen]** erlaubt die Zielgruppendimension die Verwendung aller von der eingehenden Transition übermittelten Daten.

   ![](assets/split-general-tab-options.png)

   Bei der Erstellung von Teilmengen werden die zuvor definierten Filterparameter genutzt.

   Kreuzen Sie zur Definition von Filterbedingungen die Option **[!UICONTROL Filterbedingung für Eingangspopulation hinzufügen]** an und klicken Sie auf den Link **[!UICONTROL Bearbeiten...]**. Geben Sie dann die Kriterien zur Erstellung der Teilmenge an.

   ![](assets/split-subset-config-all-data.png)

   Ein Beispiel für die Verwendung der Aktivität **[!UICONTROL Aufspaltung]** zur Segmentierung der Zielgruppe in unterschiedliche Populationen finden Sie in [diesem Abschnitt](cross-channel-delivery-workflow.md).

   Im Feld **[!UICONTROL Titel]** können Sie die erstellte Teilmenge benennen. Der Titel wird auf der ausgehenden Transition angezeigt.

   Sie können der Teilmenge außerdem einen Segment-Code zuweisen, welcher ihre Identifizierung und ihre Verwendung als Zielgruppe ermöglicht.

   Bei Bedarf können die Zielgruppen- und Filterdimensionen für jede zu erstellende Teilmenge einzeln angepasst werden. Bearbeiten Sie dazu die Filterbedingung der Teilmenge und aktivieren Sie die Option **[!UICONTROL Verwenden einer bestimmten Filterdimension]** -Option.

   ![](assets/split-subset-config-specific-filtering.png)

1. Wenn die Option **[!UICONTROL Nur Zusatzdaten verwenden]** aktiviert wurde, stehen nur die zusätzlichen Daten zur Filterung der Teilmengen zur Verfügung.

   ![](assets/split-subset-config-additional-data-only.png)

1. Wenn die Option **Federated Data Access** aktiviert wurde, bietet die Option **[!UICONTROL Externe Daten verwenden]** die Möglichkeit, Daten einer bereits verbundenen externen Datenbank zu verwenden oder eine neue Verbindung herzustellen.

   ![](assets/split-subset-config-add_external_data.png)

   Weitere Informationen hierzu finden Sie je nach Campaign-Version in den folgenden Abschnitten:

   ![](assets/do-not-localize/v7.jpeg)[Dokumentation zu Campaign v7](../../installation/using/about-fda.md)

   ![](assets/do-not-localize/v8.png)[Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/fda.html?lang=de)

Danach müssen neue Teilmengen hinzugefügt werden:

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]** und definieren Sie die Filterbedingungen.

   ![](assets/wf_split_add_a_tab.png)

1. Definieren Sie die Filterdimension im **[!UICONTROL Allgemein]**-Tab (siehe oben). Sie gilt automatisch für alle Teilmengen.

   ![](assets/wf_split_edit_filtering.png)

1. Bei Bedarf können Sie die Filterdimension für jede Teilmenge einzeln ändern. Auf diese Weise können Sie einen Satz für alle Inhaber von Gold-Karten erstellen, einen für alle Empfänger, die im neuesten Newsletter geklickt haben, und einen dritten für Personen zwischen 18 und 25 Jahren, die innerhalb der letzten 30 Tage einen In-Store-Kauf getätigt haben, die alle dieselbe Aufspaltungsaktivität verwenden. Wählen Sie dazu die **[!UICONTROL Verwenden einer bestimmten Filterdimension]** und wählen Sie den Kontext der Datenfilterung aus.

   ![](assets/wf_split_change_dimension.png)

   >[!NOTE]
   >
   >Wenn Sie die **Federated Data Access** -Option können Sie Teilmengen erstellen, die auf Informationen in einer externen Basis basieren. Wählen Sie dazu das Schema der externen Tabelle im **[!UICONTROL Zielgruppendimension]** -Feld. Weitere Informationen hierzu finden Sie unter [Zugriff auf externe Datenbanken (FDA)](accessing-an-external-database-fda.md).

Standardmäßig erzeugt die Aufspaltungsaktivität für jede Teilmenge eine ausgehende Transition:

![](assets/wf_split_multi_outputs.png)

Sie können alle Teilmengen in einer ausgehenden Transition gruppieren. In diesem Fall ist der Link zu den entsprechenden Teilmengen beispielsweise im Segmentcode sichtbar. Wählen Sie dazu die **[!UICONTROL Alle Teilmengen in derselben Tabelle generieren]** -Option.

![](assets/wf_split_select_option_single_output.png)

Dies ist beispielsweise dann interessant, wenn Sie eine einzige Versandaktivität anschließen, den Inhalt aber je nach Segment-Code der Teilmenge personalisieren möchten:

![](assets/wf_split_single_output.png)

Teilmengen können auch mithilfe der Aktivität **[!UICONTROL Segmente]** erstellt werden. Weitere Informationen hierzu finden Sie im Abschnitt [Segmente](cells.md).

### Verwenden von Zielgruppendaten {#using-targeted-data}

Nach Identifizierung und Aufbereitung der Daten können diese in folgenden Kontexten verwendet werden:

* Update der Datenbank im Anschluss an die verschiedenen Workflow-Aktivitäten.

  Weitere Informationen hierzu finden Sie unter [Daten aktualisieren](update-data.md).

* Update von existierenden Listen.

  Weitere Informationen hierzu finden Sie unter [Listen-Update](list-update.md).

* Vorbereitung und/oder Start von Sendungen direkt im Workflow.

  Weitere Informationen hierzu finden Sie unter [Versand](delivery.md), [Versand bearbeiten](delivery-control.md) und [Versand (fortlaufend)](continuous-delivery.md).

## Daten-Management {#data-management}

In Adobe Campaign umfasst das Data Management eine Reihe von Aktivitäten, die mithilfe effizienterer und flexiblerer Tools komplexe Zielgruppenbestimmungen und Anreicherungen ermöglichen. Auf diese Weise ist es möglich, eine kohärente und individuelle Kommunikation mit Kontakten zu gewährleisten, indem beispielsweise Informationen zu Verträgen, Abonnements oder Reaktionen auf vorhergehende Sendungen verwendet werden. Das Data Management erlaubt es darüber hinaus, den Lebenszyklus von Daten während der Segmentierungsprozesse zu verfolgen, insbesondere werden:

* Zielbestimmungen vereinfacht, u. a. durch Einschluss von nicht im Datamart modelisierten Daten (Erstellung neuer Tabellen: lokale Erweiterung auf jeden Zielgruppen-Workflow in Abhängigkeit von seiner Konfiguration);
* Zwischenergebnisse gespeichert und weitergegeben (interessant im Zuge der Zielbestimmung oder der Datenbankadministration);
* Zugriffe auf externe Datenbanken ermöglicht (optional), was die Berücksichtigung heterogener Datenbanken bei Zielbestimmungsprozessen zulässt.

Hierfür bietet Adobe Campaign:

* Datenerfassungsaktivitäten: [Dateiübertragung](file-transfer.md), [Laden (Datei)](data-loading-file.md), [Laden (DBMS)](data-loading-rdbms.md), [Daten-Update](update-data.md). Dieser erste Schritt der Datenerfassung bereitet die Daten so vor, dass sie in anderen Aktivitäten verarbeitet werden können. Mehrere Parameter müssen überwacht werden, um sicherzustellen, dass der Workflow korrekt ausgeführt wird und die erwarteten Ergebnisse liefert. Wenn Sie beispielsweise Daten importieren, muss der Primärschlüssel (Pkey) für diese Daten für jeden Datensatz eindeutig sein.
* Aktivitäten mit Data Management-Optionen ([Abfrage](query.md), [Vereinigung](union.md), [Schnittmenge](intersection.md), [Aufspaltung](split.md)). Dies ermöglicht beispielsweise die Konfiguration einer Vereinigung oder einer Schnittmenge mit Daten, die unterschiedliche Zielgruppendimensionen aufweisen, vorausgesetzt eine Abstimmung der Daten ist möglich.
* Formatierungsaktivitäten: [Anreicherung](enrichment.md), [Dimensionsänderung](change-dimension.md).

>[!CAUTION]
>
>In Workflows löst bei in Relation stehenden Tabellen das Löschen eines Elements der Quelltabelle nicht das Löschen der verbundenen Elemente aus.
>  
>Zum Beispiel zieht das Löschen eines Empfängers mithilfe eines Workflows nicht das Löschen seines Versandverlaufs nach sich. Wird ein Empfänger jedoch direkt im &#39;Empfänger&#39;-Ordner des Navigationsbaums gelöscht, werden auch alle anderen auf ihn bezogenen Daten gelöscht.

### Anreichern und Ändern von Daten {#enriching-and-modifying-data}

Ergänzend zur Zielgruppendimension ermöglicht die Filterdimension, die Art der abgerufenen Daten zu präzisieren. Siehe [Zielgruppen- und Filterdimensionen](building-a-workflow.md#targeting-and-filtering-dimensions).

Identifizierte und abgerufene Daten können angereichert, zusammengefasst und bearbeitet werden, um die Zielgruppenerstellung zu optimieren. Verwenden Sie dazu zusätzlich zu den im Abschnitt [Daten segmentieren](#segmenting-data) beschriebenen Datenbearbeitungstätigkeiten Folgendes:

* Mit der Aktivität **[!UICONTROL Anreicherung]** können Sie vorübergehend Spalten zu einem Schema sowie Informationen zu bestimmten Elementen hinzufügen. Weitere Informationen hierzu finden Sie im Abschnitt [Anreicherung](enrichment.md) des Aktivitäten-Repositorys.
* Mit der Aktivität **[!UICONTROL Schema-Bearbeitung]** können Sie die Struktur eines Schemas ändern. Weitere Informationen hierzu finden Sie im Abschnitt [Schema-Bearbeitung](edit-schema.md) des Aktivitäten-Repositorys.
* Mit der Aktivität **[!UICONTROL Dimensionsänderung]** können Sie die Zielgruppendimension beim Erstellen der Zielgruppe ändern. Weitere Informationen hierzu finden Sie im Abschnitt [Dimensionsänderung](change-dimension.md).

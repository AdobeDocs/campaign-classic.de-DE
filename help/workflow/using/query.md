---
title: Abfrage
description: Weitere Informationen zur Aktivität des Arbeitsablaufs für Abfragen
page-status-flag: never-activated
uuid: 32f4f467-5083-414f-8616-1aa4bf2b5867
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: b53d9810-f61f-4257-b410-e4d30f78429d
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '1685'
ht-degree: 99%

---


# Abfrage{#query}

## Abfragen erstellen {#creating-a-query}

Über Abfragen lassen sich Zielgruppen anhand von Filterkriterien bestimmen. Es besteht die Möglichkeit, dem Abfrageergebnis einen Segment-Code zuzuweisen und es mit Zusatzdaten zu ergänzen.
Weitere Informationen zu Beispielen für Abfragen finden Sie in diesem [Abschnitt](../../workflow/using/querying-recipient-table.md).

>[!NOTE]
>
>Abfrageaktivitäten sind bei Verwendung von Oracle nicht mit CLOB-Feldern kompatibel.

![](assets/s_user_segmentation_wizard_9.png)

Weitere Informationen zum Verwenden und Umgang mit Zusatzdaten finden Sie unter [Daten hinzufügen](#adding-data).

Klicken Sie auf den Link **[!UICONTROL Abfrage bearbeiten...]** und gehen Sie wie folgt vor, um Zielgruppentyp, Beschränkungen und Auswahlkriterien der anzusprechenden Population zu definieren:

1. Wählen Sie zunächst Zielgruppen- und Filterdimension aus. Standardmäßig wird die Zielgruppe aus den Empfängern ausgewählt. Die vorgeschlagenen Einschränkungsfilter sind dieselben wie bei der Zielgruppenbestimmung in einem Versand.

   Die Zielgruppendimension bezeichnet den Elementtyp, der verwendet werden soll, beispielsweise die mit der Kampagne anzusprechende Population.

   Filterdimensionen ermöglichen die spezifische Auswahl der Elemente, beispielsweise nach Kriterien wie Verträgen, Altersgruppen etc.

   Weitere Informationen hierzu finden Sie unter [Zielgruppen- und Filterdimension](../../workflow/using/building-a-workflow.md#targeting-and-filtering-dimensions).

   ![](assets/s_user_segmentation_query_edit.png)

   Eine Abfrage kann sich bei Bedarf auf die Daten der eingehenden Transition beziehen. Aktivieren Sie in diesem Fall bei der Auswahl der Zielgruppen- und Filterdimension die Option **[!UICONTROL Temporäres Schema]**.

   ![](assets/query_temporary_table.png)

1. Definieren Sie mithilfe des Assistenten die Filterkriterien zur Auswahl der gewünschten Population. Je nach Zielgruppentyp können die angezeigten Felder unterschiedlich sein. Im **[!UICONTROL Vorschau]**-Tab können Sie prüfen, ob die angegebenen Kriterien das gewünschte Ergebnis liefern.

   Weiterführende Informationen zur Erstellung und Verwendung von Filtern und zu Abfragen finden Sie in diesem [Abschnitt](../../platform/using/filtering-options.md).

   ![](assets/s_user_segmentation_wizard.png)

1. Fügen Sie gegebenenfalls manuell Filterkriterien hinzu, wenn Sie im ersten Schritt **[!UICONTROL Filterbedingungen]** gewählt haben, oder verwenden Sie die Option **[!UICONTROL Filter]** > **[!UICONTROL Erweiterte Filter...]**.

   Es besteht darüber hinaus die Möglichkeit, die gefilterten Daten zu gruppieren. Dies ist jedoch nur möglich, wenn die Filterdimension nicht mit der Zielgruppendimension identisch ist. Weiterführende Informationen finden Sie in diesem [Abschnitt](../../workflow/using/querying-using-grouping-management.md).

   Mithilfe des Ausdruckseditors können verschiedene Kriterien unter Verwendung der Operatoren UND, ODER und AUSSER kombiniert werden. Bei Bedarf können Sie die **[!UICONTROL Entsprechende SQL-Abfrage...]** anzeigen. Weiterführende Informationen dazu finden Sie in diesem [Abschnitt](../../platform/using/defining-filter-conditions.md#building-expressions).

   Speichern Sie die Abfrage, um sie später erneut verwenden zu können.

   ![](assets/s_user_segmentation_query_advanced.png)

## Daten hinzufügen {#adding-data}

Es besteht die Möglichkeit, in Workflows zusätzliche Informationen über die Zielgruppe zu verwenden. Dies können beispielsweise Versicherungsnummern, Abonnements von bestimmten Newslettern oder die Herkunft der Empfänger sein. Diese Informationen können entweder aus der Adobe-Campaign-Datenbank oder aus externen Datenbanken stammen.

Die Auswahl dieser Zusatzinformationen erfolgt über den Link **[!UICONTROL Daten hinzufügen...]**.

![](assets/wf_add_data_link.png)

Wählen Sie im ersten Fenster des Assistenten zunächst den Typ der hinzuzufügenden Daten aus:

![](assets/wf_add_data_1st_option.png)

* Die Option **[!UICONTROL Daten in Relation mit der Filterdimension]** erlaubt den Zugriff auf Daten aus der Adobe-Campaign-Datenbank.
* Die Option **[!UICONTROL Externe Daten]** erlaubt den Zugriff auf Daten aus einer externen Datenbank. Für diese Option benötigen Sie das optionale Modul **Federated Data Access**. Weitere Informationen hierzu finden Sie unter [Zugriff auf externe Datenbanken (FDA)](../../workflow/using/accessing-an-external-database--fda-.md).
* Die Option **[!UICONTROL Angebotsvorschlag]** erlaubt den Zugriff auf den jeweils besten, vom Angebotsmodul erzeugten Vorschlag. Hierfür benötigen Sie das optionale Modul **Interaction**.

Wenn keines der o. g. Module auf Ihrer Plattform installiert ist, überspringt der Assistent das Auswahlfenster. Sie werden direkt zum nächsten Schritt weitergeleitet.

Gehen Sie folgendermaßen vor, um Daten aus der Adobe-Campaign-Datenbank hinzuzufügen:

1. Wählen Sie den Datentyp aus, der hinzugefügt werden soll. Hierbei kann es sich um Daten der Filterdimension direkt oder Daten aus in Relation zur Filterdimension stehenden Tabellen handeln.

   ![](assets/query_add_columns.png)

1. Wenn die Daten aus der Filterdimension der Abfrage stammen, können Sie sie direkt aus der Liste der verfügbaren Felder auswählen, um sie in den Ausgabespalten anzuzeigen.

   ![](assets/wf_add_data_field_selection.png)

   Hinzugefügt werden können des Weiteren:

   * Aus Daten der Zielpopulation berechnete Felder oder Aggregate (z. B. Anzahl an ausstehenden Käufen im vergangenen Monat, durchschnittlicher Warenkorb usw.). Ein Beispiel finden Sie unter [Datenauswahl](../../workflow/using/targeting-data.md#selecting-data).
   * Neue Felder (über die Schaltfläche **[!UICONTROL Hinzufügen]** rechts von der Liste der Ausgabespalten).

      Es ist darüber hinaus möglich, Informationskollektionen hinzuzufügen, beispielsweise eine Vertragsliste, die letzten fünf Sendungen usw. Kollektionen entsprechen Feldern, die für ein Profil mehrere Werte aufweisen können (1:n-Relation). Weitere Informationen hierzu finden Sie unter [Zusätzliche Daten bearbeiten](../../workflow/using/targeting-data.md#editing-additional-data).

Gehen Sie folgendermaßen vor, um eine mit einer Zielpopulation verknüpfte Informationskollektion hinzuzufügen:

1. Wählen Sie im ersten Schritt des Assistenten die Option **[!UICONTROL Daten in Relation mit der Filterdimension]** aus.
1. Markieren Sie die Tabelle, die die abzurufenden Informationen enthält und klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/wf_add_data_linked_table.png)

1. Geben Sie bei Bedarf die Anzahl an Kollektionselementen an, die Sie beibehalten möchten, indem Sie aus der Dropdown-Liste des Felds **[!UICONTROL Abgerufene Daten]** den gewünschten Wert auswählen. Standardmäßig werden alle Zeilen der Kollektion abgerufen und nach den im nächsten Schritt definierten Bedingungen gefiltert.

   * Wenn nur ein Kollektionselement den Filterbedingungen entspricht, ist die Option **[!UICONTROL Nur eine Zeile]** im Feld **[!UICONTROL Abgerufene Daten]** auszuwählen.

      >[!IMPORTANT]
      >
      >Dieser Modus optimiert die erzeugte SQL-Abfrage, da ein direkter Join auf die Kollektionselemente erstellt wird.
      >
      >Wenn die ursprüngliche Bedingung nicht respektiert wird, kann das Ergebnis falsch sein (fehlende Zeilen oder Dubletten).

   * Wenn Sie mehrere Zeilen abrufen möchten (**[!UICONTROL Zeilenanzahl begrenzen]**), können Sie die Anzahl an abzurufenden Zeilen angeben.
   * Wenn die abgerufenen Spalten Aggregate enthalten, beispielsweise die Anzahl an Versicherungsfällen, der durchschnittliche Warenkorb in einem POS etc., kann die Option **[!UICONTROL Aggregate]** verwendet werden.

   ![](assets/query_add_collection_param.png)

1. Definieren Sie die Unterauswahl der Kollektionselemente. Beispielsweise die Käufe der letzten 15 Tage.

   ![](assets/query_add_columns_collection_filter.png)

1. Wenn Sie die Option **[!UICONTROL Zeilenanzahl begrenzen]** gewählt haben, ist eine Sortierreihenfolge zu definieren. Dies ermöglicht es, die beizubehaltenden Daten zu bezeichnen, wenn die Anzahl an abgerufenen Zeilen die Anzahl an Zeilen übersteigt, die Sie beibehalten möchten.

## Beispiel: Zielgruppenbestimmung anhand einfacher Empfängerattribute {#example--targeting-on-simple-recipient-attributes}

In folgendem Beispiel sollen alle Männer zwischen 18 und 30 Jahre identifiziert werden, die in Deutschland leben. Die Abfrage könnte in einem Workflow Verwendung finden, der ein speziell an diese Zielgruppe gerichtetes Angebot versendet. Gehen Sie wie folgt vor:

>[!NOTE]
>
>Beispiele für zusätzliche Abfragen werden in [diesem Abschnitt](../../workflow/using/querying-recipient-table.md) beschrieben.

1. Benennen Sie die Abfrage und klicken Sie auf den Link **[!UICONTROL Abfrage bearbeiten...]**.
1. Wählen Sie aus der Liste der verfügbaren Filter die Option **[!UICONTROL Filterbedingungen]** aus.
1. Konfigurieren Sie die verschiedenen Kriterien für die gesuchte Zielgruppe. Im vorliegenden Beispiel werden die einzelnen Kriterien mit dem Operator UND verknüpft. Die Empfänger müssen also die vier folgenden Bedingungen erfüllen:

   * Anrede gleich &quot;Herr&quot; (oder **Geschlecht** gleich **Männlich**),
   * Alter kleiner als 30 Jahre.
   * Alter größer als 18 Jahre.
   * Land gleich Deutschland.

   ![](assets/query_example.png)

   Der der Abfrage entsprechende SQL-Code stellt sich wie folgt dar:

   ![](assets/query_example_sql.png)

1. Prüfen Sie das Abfrageergebnis im Vorschau-Tab:

   ![](assets/query_example_preview.png)

1. Speichern Sie bei Bedarf die Abfrage und klicken Sie auf **[!UICONTROL Beenden]** > **[!UICONTROL OK]**.
1. Vervollständigen Sie den Workflow mit weiteren Aktivitäten und starten Sie ihn. Nach Ausführung der Abfrage wird das Ergebnis auf der ausgehenden Transition angezeigt. Sie können das Ergebnis im Detail ansehen, indem Sie einen Rechtsklick auf der Transition machen und im Kontextmenü die Option **[!UICONTROL Ergebnis anzeigen...]** auswählen.

   ![](assets/query_example_result.png)

## Ausgabeparameter {#output-parameters}

* tableName
* schema
* recCount

Anhand der drei Werte lässt sich die durch den Ausschluss ermittelte Zielgruppe identifizieren. **[!UICONTROL tableName]** ist der Name der Tabelle, welche die Kennungen der Zielgruppenempfänger enthält, **[!UICONTROL schema]** ist das Schema der Population, (i. d. R. nms:recipient) und **[!UICONTROL recCount]** ist die Anzahl an Elementen in der Tabelle.

Dieser Wert bezeichnet das Schema der Arbeitstabelle. Dieser Parameter ist für alle Transitionen mit **[!UICONTROL tableName]** und **[!UICONTROL schema]** gültig.

## Abfragen optimieren {#optimizing-queries}

Im folgenden Abschnitt finden Sie Best Practices zur Optimierung der in Adobe Campaign ausgeführten Abfragen, um den Arbeitsaufwand für die Datenbank zu begrenzen und die Benutzerfreundlichkeit zu verbessern.

### Joins und Indizes {#joins-and-indexes}

* Effiziente Abfragen beruhen auf Indizes.
* Verwenden Sie einen Index für alle Joins.
* Durch die Definition von Links im Schema werden die Joinbedingungen festgelegt. Die verknüpfte Tabelle sollte einen eindeutigen Index für den Primärschlüssel haben und der Join sollte sich in diesem Feld befinden.
* Führen Sie Joins durch, indem Sie Schlüssel für numerische Felder anstelle von Zeichenfolgenfeldern definieren.
* Vermeiden Sie äußere Joins. Verwenden Sie nach Möglichkeit den Null-ID-Datensatz, um eine äußere Join-Funktion zu erhalten.
* Verwenden Sie den richtigen Datentyp für Joins.

   Stellen Sie sicher, dass die `where`-Klausel vom gleichen Typ wie das Feld ist.

   Ein häufiger Fehler ist `iBlacklist='3'`, wobei `iBlacklist` ein numerisches Feld und `3` ein Textwert ist.

   Informieren Sie sich über den Ausführungsplan Ihrer Anfrage. Vermeiden Sie vollständige Tabellen-Scans, insbesondere bei Echtzeitabfragen oder Abfragen nahezu in Echtzeit, die jede Minute ausgeführt werden.

Weitere Informationen hierzu finden Sie in den Abschnitten [Best Practices für Datenmodelle](https://helpx.adobe.com/de/campaign/kb/acc-data-model-best-practices.html) und [Datenbank-Mapping](../../configuration/using/database-mapping.md).

### Funktionen {#functions}

* Vorsicht vor Funktionen wie `Lower(...)`. Wenn die Funktion „Lower“ verwendet wird, wird der Index nicht verwendet.
* Überprüfen Sie Abfragen mit der Anweisung „Like“ oder den Anweisungen „Upper“ und „Lower“ sorgfältig. Wenden Sie „Upper“ auf die Benutzereingabe an, nicht auf das Datenbankfeld.

   Weitere Informationen zu Funktionen finden Sie in [diesem Abschnitt](../../platform/using/defining-filter-conditions.md#list-of-functions).

### Filterdimensionen {#filtering-dimensions}

Verwenden Sie die Filterdimension der Abfrage, anstatt den Operator „wie“ zu verwenden.

![](assets/optimize-queries-filtering.png)

In Abfragen sind „wie“-Bedingungen in Filtern nicht effizient. Sie entsprechen einer Subabfrage in SQL:

`select iRecipientId from nmsRecipient where iRecipientId IN (select iRecipientId from nmsBroadLog where (...))`

Am besten verwenden Sie stattdessen die Filterdimension der Abfrage:

![](assets/optimize-queries-filtering2.png)

Das Äquivalent der Filterdimension in SQL ist der innere Join:

`select iRecipientId from nmsRecipient INNER JOIN nmsBroadLog ON (...)`

Weitere Informationen zu Filterdimension finden Sie in [diesem Abschnitt](../../workflow/using/building-a-workflow.md#targeting-and-filtering-dimensions).

### Architektur {#architecture}

* Erstellen Sie eine Entwicklungsplattform mit ähnlichen Umfängen, Parametern und Architekturen wie die Produktionsplattform.
* Verwenden Sie dieselben Werte für die Entwicklungs- und Produktionsumgebungen. Wenn möglich, sollten die folgenden Einstellungen dieselben sein:

   * Betriebssystem,
   * Version,
   * Daten,
   * Anwendung,
   * Umfänge.

   >[!NOTE]
   >
   >Eine Funktion, die in einer Entwicklungsumgebung funktioniert, funktioniert möglicherweise nicht in einer Produktionsumgebung, in der die Daten unterschiedlich sein können. Versuchen Sie, die Hauptunterschiede zu identifizieren, um Risiken vorherzusehen und Lösungen vorzubereiten.

* Bereiten Sie Konfigurationen vor, die mit den Zielgruppenumfängen übereinstimmen. Große Umfänge erfordern spezifische Konfigurationen. Eine Konfiguration, die für 100.000 Empfänger funktionierte, funktioniert möglicherweise nicht für 10.000.000 Empfänger.

   Überlegen Sie, wie das System skaliert wird, wenn es live geschaltet wird. Nur weil etwas in kleinem Maßstab funktioniert, heißt das nicht, dass es sich auch für größere Mengen eignet. Die Tests sollten mit ähnlichen Umfängen wie der Umfang in der Produktion durchgeführt werden. Sie sollten auch die Auswirkungen von Änderungen der Umfänge (Anzahl der Aufrufe, Größe der Datenbank) zu Spitzenzeiten, an Spitzentagen und während der gesamten Projektlaufzeit bewerten.

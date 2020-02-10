---
title: Zu analysierende Daten abrufen
seo-title: Zu analysierende Daten abrufen
description: Zu analysierende Daten abrufen
seo-description: null
page-status-flag: never-activated
uuid: 5a611786-6e56-4fce-b232-dd8428f3a5f2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 594a333d-1fc3-49a0-b3f6-7ea8fa4321e9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0c41cf2f35495a1514642e47f0b7146d8dd50946

---


# Zu analysierende Daten abrufen{#collecting-data-to-analyze}

The data to be used for building the report can be selected directly in the report page (for more on this, refer to [Using the context](../../reporting/using/using-the-context.md)) or collected via one or more queries.

In der Abfrage-Aktivität stehen drei verschiedene Methoden zur Verfügung:

1. Erstellung einer Abfrage zu den Daten der Datenbank;
1. Analyse der Daten aus einer Liste;
1. Verwendung der Daten eines existierenden Cubes.

Die Wahl der einen oder der anderen Methode hängt vom auszuführenden Berechnungstyp, dem zu bewegenden Datenvolumen, ihrer Beständigkeit und mehr ab. Diese Konfigurationen müssen genau durchdacht werden, um die Datenbank nicht zu überlasten und die Erzeugung und Nutzung der erstellten Berichte zu optimieren. Lesen Sie diesbezüglich [diese Seite](../../reporting/using/best-practices.md#optimizing-report-creation).

In all cases, data is collected via a **[!UICONTROL Query]** type activity.

![](assets/reporting_query_edit.png)

Dieser Datenauswahlmodus ist relevant, wenn die Daten im Bericht mithilfe von Daten in der Datenbank erfasst oder erstellt werden müssen. In einigen Fällen können Sie die Daten auch direkt aus den im Bericht verwendeten Elementen auswählen. Wenn Sie beispielsweise ein Diagramm einfügen, können Sie die Quelldaten direkt auswählen. Weitere Informationen finden Sie unter [Verwenden des Kontexts](../../reporting/using/using-the-context.md).

## Datenbankschemata benutzen {#using-the-data-from-a-schema}

Um direkt die mit einem Schema der Datenbank verbundenen Daten zu verwenden, wählen Sie die entsprechende Option im Abfrage-Editor aus und konfigurieren Sie die anzuwendende Abfrage.

Im folgenden Beispiel wird die Empfängeranzahl pro Land aus den Profilen der Datenbank abgerufen. Die Daten können dann in Tabellenform in einem Bericht angezeigt werden.

![](assets/reporting_query_from_schema.png)

## Importierte Listen benutzen {#using-an-imported-list}

Sie haben die Möglichkeit, eine Liste mit importierten Daten als Basis für Ihren Bericht zu verwenden.

To do this, select the **[!UICONTROL Use an imported list]** option in the query box and select the concerned list.

![](assets/reporting_query_from_list.png)

Click the **[!UICONTROL Edit query...]** link to define the data to collect among the elements in this list for building the report.

## Cubes benutzen {#using-a-cube}

Sie können einen Cube zur Definition der Abfrage auswählen.

![](assets/reporting_query_from_cube.png)

Cubes ermöglichen es, die Kapazitäten der Datenexploration und -analyse zu erweitern und gleichzeitig die Konfiguration der Berichte und Tabellen für die Endbenutzer zu vereinfachen: Wählen Sie einfach einen existierenden, vollständig konfigurierten Cube aus, um dessen Berechnungen, Messungen und Statistiken zu nutzen. Weiterführende Informationen zum Erstellen von Cubes finden Sie in [diesem Abschnitt](../../reporting/using/about-cubes.md).

Click the **[!UICONTROL Edit query...]** link and select the indicators that you want to display or use in your report.

![](assets/reporting_query_from_cube_edit_query.png)

## Filteroptionen in Abfragen {#filtering-options-in-the-queries}

Um zu vermeiden, dass die Abfragen sich auf die gesamte Datenbank beziehen, müssen die Daten gefiltert werden.

### Einfache Filter {#simplified-filter}

You can select the **[!UICONTROL Filter automatically with the context]** option to make the report accessible via a specific node of the tree such as a list, a recipient, or a delivery.

Mit der **[!UICONTROL Filter with the folder]** Option können Sie einen Ordner angeben und nur dessen Inhalt berücksichtigen. Auf diese Weise können Sie die Berichtsdaten filtern, sodass nur die Daten aus einem der Ordner in der Struktur angezeigt werden, wie unten dargestellt:

![](assets/reporting_control_folder.png)

### Umfang der abgerufenen Daten begrenzen {#limiting-the-amount-of-data-collected}

Konfigurieren Sie die Anzahl der über eine Abfrage zu extrahierenden Daten mithilfe der Optionen zur Ergebnisbegrenzung:

* **[!UICONTROL Limit to first record]** ein Ergebnis zu extrahieren,
* **[!UICONTROL Size]** um eine bestimmte Anzahl von Datensätzen zu extrahieren.


---
product: campaign
title: Schritte zum Erstellen einer Abfrage
description: Schritte zum Erstellen einer Abfrage
feature: Query Editor
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: platform
content-type: reference
topic-tags: creating-queries
exl-id: cf914366-8bac-4d68-a0cc-2a43d102eef2
hide: true
hidefromtoc: true
source-git-commit: 471018f09e5a14635fcce07aeca1e2cf48d9144f
workflow-type: ht
source-wordcount: '147'
ht-degree: 100%

---

# Schritte zum Erstellen einer Abfrage{#steps-to-create-a-query}



Folgende Schritte sind auszuführen, um eine Abfrage in Adobe Campaign zu erstellen:

1. Wählen Sie die Arbeitstabelle aus. Siehe [1. Schritt - Tabelle auswählen](#step-1---choose-a-table).
1. Wählen Sie die zu extrahierenden Daten aus. Siehe [2. Schritt - Zu extrahierende Daten auswählen](#step-2---choose-data-to-extract).
1. Definieren Sie die Sortierreihenfolge für die Daten. Siehe [3. Schritt - Daten sortieren](#step-3---sort-data).
1. Filtern Sie die Daten. Siehe [4. Schritt - Daten filtern](#step-4---filter-data).
1. Formatieren Sie die Daten. Siehe [5. Schritt - Daten formatieren](#step-5---format-data).
1. Zeigen Sie das Ergebnis an. Siehe [6. Schritt - Vorschau der Daten anzeigen](#step-6---preview-data).

>[!NOTE]
>
>* Alle diese Schritte können im generischen Abfragetool durchgeführt werden. In anderen Anwendungskontexten sind u. U. gewisse Schritte nicht nötig.\
>Das Abfrage-Tool wird in [diesem Abschnitt](../../workflow/using/query.md) beschrieben.
>* Weitere Informationen zu Abfragen und wie diese erstellt werden finden Sie in der [Dokumentation zu Campaign v8](../../workflow/using/query.md).

<!--
## Step 1 - Choose a table {#step-1---choose-a-table}

Select the table containing the data you want to query in the **[!UICONTROL Document type]** window. If necessary, filter the data using the filter field or the **[!UICONTROL Filters]** button.

![](assets/query_editor_nveau_21.png)

## Step 2 - Choose data to extract {#step-2---choose-data-to-extract}

In the **[!UICONTROL Data to extract]** window, select the data to display: these fields will make up the output columns.

For example, select **[!UICONTROL Age]**, **[!UICONTROL Primary key]**, **[!UICONTROL Email domain]** and **[!UICONTROL City]**. The results will be organized based on this selection. Use the blue arrows to the right of the window to change the column order.

![](assets/query_editor_nveau_01.png)

You can edit an expression by inserting a formula into it or running a process on an aggregate function. To do this, click the **[!UICONTROL Expression]** column field, then select **[!UICONTROL Edit expression]**.

![](assets/query_editor_nveau_97.png)

It is possible to group output column data: to do this, check **[!UICONTROL Yes]** in the **[!UICONTROL Group]** column of the **[!UICONTROL Data to extract]** window. This function generates a result around the checked grouping axis. An example of a query with grouping is available in [this section](../../workflow/using/querying-delivery-information.md).

![](assets/query_editor_nveau_56.png)

* The **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** function lets you "group by" and select what has been grouped ("having"). This function applies to all fields in the output column. For example, this option lets you group all choices of an output column and recover a specific type of information, such as recipients between 35 and 50.

  For more on this, refer to [this section](../../workflow/using/querying-using-grouping-management.md).

* The **[!UICONTROL Remove duplicate rows (DISTINCT)]** function lets you deduplicate identical results obtained in the output column. For example, if you take a census by selecting the Last name, First name and Email fields in the output column, those with identical data will be eliminated, since it means the same contact has been entered several times in the database: only one result will be taken into account.

## Step 3 - Sort data {#step-3---sort-data}

The **[!UICONTROL Sorting]** window lets you sort column content. Use the arrows to change the column order:

* The **[!UICONTROL Sorting]** column enables a simple sort and arranges column content from A to Z or in ascending order.
* The **[!UICONTROL Descending sort]** arranges the content from Z to A and in descending order. This is useful for viewing record sales for example: the highest figures are shown at the top of the list.

In this example, the data is sorted in ascending order based on recipient age.

![](assets/query_editor_nveau_57.png)

## Step 4 - Filter data {#step-4---filter-data}

The query editor lets you filter data to refine your search.

The filters offered depend on the table which the query concerns.

![](assets/query_editor_nveau_09.png)

Once you select the **[!UICONTROL Filtering conditions]** you will access the **[!UICONTROL Target elements]** section: this lets you define how to filter the data to collect.

* To create a new filter, select the fields, operators and values required for creating the formula to be verified in order for data to be selected. It's possible to combine several conditions (for more on this, refer to [Defining filter conditions](../../platform/using/defining-filter-conditions.md)).
* To use previously saved filters, open the drop-down list by clicking the **[!UICONTROL Add]** button, click **[!UICONTROL Predefined filter]** and select the one you want.

  ![](assets/query_editor_15.png)

* The filters created in the **[!UICONTROL Generic query editor]** are available in other query applications and vice versa. To save a filter, click the **[!UICONTROL Save]** icon.

  >[!NOTE]
  >
  >For more on creating and using filters, refer to [Filtering options](../../platform/using/filtering-options.md).

As shown in the following example, to recover all English-speaking recipients, select: "recipient language **equal to** EN".

![](assets/query_editor_nveau_89.png)

>[!NOTE]
>
>You can directly access an option by typing the following formula in the **Value** field: **$(options:OPTION_NAME)**.

Click the **[!UICONTROL Preview]** tab to view the result of the filtering condition. In this case, all English-speaking recipients are displayed with their name, first name and email address.

![](assets/query_editor_nveau_98.png)

Users familiar with SQL language can click **[!UICONTROL Generate SQL query]** to view the query in SQL.

![](assets/query_editor_nveau_99.png)

## Step 5 - Format data {#step-5---format-data}

Once you have configured the restriction filters, you will access the **[!UICONTROL Data formatting]** window. This window lets you re-arrange output columns, transform data, and change the upper/lower case of the column labels. It also lets you apply a formula to the final result using a calculated field.

>[!NOTE]
>
>For more information on the types of calculated fields, refer to [Creating calculated fields](../../platform/using/defining-filter-conditions.md#creating-calculated-fields).

Unchecked columns will not be shown in the data preview window.

![](assets/query_editor_nveau_10.png)

The **[!UICONTROL Transformation]** column lets you change a column label to upper or lower case. Select the column and click in the **[!UICONTROL Transformation]** column. You can choose:

* **[!UICONTROL Switch to lower case]**,
* **[!UICONTROL Switch to upper case]**, 
* **[!UICONTROL First letter in upper case]**.

![](assets/query_editor_nveau_42.png)

## Step 6 - Preview data {#step-6---preview-data}

The **[!UICONTROL Data preview]** window is the last stage. Click **[!UICONTROL Start the preview of the data]** to get your query result. It is available in columns or in XML format. Click the **[!UICONTROL Generated SQL queries]** tab to view the query in SQL format.

In this example, data is sorted in ascending order based on recipient age.

![](assets/query_editor_nveau_11.png)

>[!NOTE]
>
>By default, only the first 200 lines are displayed in the **[!UICONTROL Data preview]** window. To change this, enter a number in the **[!UICONTROL Lines to display]** box and click **[!UICONTROL Start the preview of the data]**.

-->
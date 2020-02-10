---
title: Cubes erstellen
seo-title: Cubes erstellen
description: Cubes erstellen
seo-description: null
page-status-flag: never-activated
uuid: 3caaba6b-b6c8-4b64-b123-d7098e9ddc7a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
discoiquuid: a5fc6c78-b4fb-41fd-a072-7be4ece3c554
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Cubes erstellen{#creating-indicators}

Um einen Cube nutzen zu können, müssen zunächst die erforderlichen Dimensionen und Kennzahlen identifiziert und auf Ebene des Cubes erstellt werden.

Ein Cube wird in folgenden Schritten konfiguriert:

1. Wählen Sie die Arbeitstabelle aus. Siehe [Auswählen der Arbeitstabelle](#selecting-the-work-table).
1. Definieren von Dimensionen Siehe [Definieren von Dimensionen](#defining-dimensions).
1. Definieren Sie Maßnahmen. Siehe [Erstellen von Indikatoren](#building-indicators).
1. Erstellen von Aggregaten (optional). Siehe [Berechnen und Verwenden von Aggregaten](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates).

Das nachstehende Beispiel zeigt, wie schnell ein einfacher Cube erstellt und in einem Bericht zur Kennzahlenanalyse verwendet werden kann.

Die Durchführungsschritte werden im Nachstehenden beschrieben, die verschiedenen Optionen und ihre Beschreibungen werden in den anderen Abschnitten dieses Kapitels ausführlich dargestellt.

## Arbeitstabelle auswählen {#selecting-the-work-table}

To create a cube, click the **[!UICONTROL New]** button above the list of cubes.

![](assets/s_advuser_cube_create.png)

Wählen Sie ein Faktenschema aus, d. h. das Schema, das die zu analysierenden Elemente enthält. Im vorliegenden Beispiel wird die **Empfänger**-Tabelle ausgewählt.

![](assets/s_advuser_cube_wz_02.png)

Click **[!UICONTROL Save]** to create the Cube: it will appear on the list of Cubes and may then be configured using the appropriate tabs.

Click the **[!UICONTROL Filter the source data...]** link to apply the calculations of this Cube to a select of data in the database.

![](assets/s_advuser_cube_wz_03.png)

## Dimensionen bestimmen {#defining-dimensions}

Dimensionen sind die Analyseachsen, die für jeden Cube entsprechend dem Faktenschema, auf das er sich bezieht, bestimmt werden. Es handelt sich um die analysierten Dimensionen, wie zum Beispiel die Zeit (Jahr, Monat, Tag etc.), eine Produkt- oder Vertragsnomenklatur (Familie, Referenz etc.), ein Populationssegment (nach Stadt, Altersgruppe, Status etc).

These analysis axes are defined in the **[!UICONTROL Dimension]** tab of the Cube.

Click the **[!UICONTROL Add]** button to create a new dimension, then in the **[!UICONTROL Expression field]**, click the **[!UICONTROL Edit expression]** icon to select the field that contains the concerned data.

![](assets/s_advuser_cube_wz_04.png)

* Wählen Sie zunächst das **Alter** der Empfänger. Für dieses Feld können Sie eine Klassierung bestimmen, um Altersgruppen zusammenzufassen und so die Lesbarkeit der Daten zu vereinfachen. Die Klassierung wird empfohlen, wenn ein Merkmal eine Vielzahl von unterschiedlichen Ausprägungen aufweist.

   Markieren Sie dazu die **[!UICONTROL Enable binning]** Option. Die Binnungsmodi werden im Abschnitt [Datenablage](../../reporting/using/concepts-and-methodology.md#data-binning)detailliert beschrieben.

   ![](assets/s_advuser_cube_wz_05.png)

* Fügen Sie eine Dimension vom Typ **Datum** hinzu. Im Beispiel sollen die Erstellungsdaten der Empfängerprofile angezeigt werden.

   To do this, click **[!UICONTROL Add]** and select the **[!UICONTROL Creation date]** field in the recipient table.

   ![](assets/s_advuser_cube_wz_06.png)

   Sie können den Anzeigemodus der Daten auswählen. Wählen Sie hierzu die zu erzeugenden Ebenen aus:

   ![](assets/s_advuser_cube_wz_07.png)

   Im Beispiel sollen nur Jahre, Monate und Tage angezeigt werden. Es ist nicht möglich, mit Wochen und Quartalen/Monaten zugleich zu arbeiten: Diese Ebenen sind nicht kompatibel.

* Erstellen Sie eine weitere Dimension, um die Informationen in Bezug auf den Ort des Empfängers zu analysieren.

   To do this, add a new dimension and select the city in the **[!UICONTROL Location]** node of the recipient schema.

   ![](assets/s_advuser_cube_wz_08.png)

   Sie können auch hier die Klassierung aktivieren, um die Lesbarkeit der Informationen zu erleichtern, und in diesem Fall die Werte mit einem Auflistungswert verknüpfen.

   ![](assets/s_advuser_cube_wz_09.png)

   Wählen Sie die Auflistung in der Dropdown-Liste aus.

   ![](assets/s_advuser_cube_wz_10.png)

   Nur die Werte in der Aufzählung werden angezeigt. Die anderen werden unter der im **[!UICONTROL Label of the other values]** Feld definierten Beschriftung gruppiert.

   Weitere Informationen finden Sie unter [Dynamisches Verwalten von Ablagen](../../reporting/using/concepts-and-methodology.md#dynamically-managing-bins).

## Kennzahlen erstellen {#building-indicators}

Sobald die Dimensionen definiert sind, müssen Sie einen Berechnungsmodus für die Werte festlegen, die in den Zellen angezeigt werden sollen. Erstellen Sie dazu die entsprechenden Indikatoren auf der **[!UICONTROL Measures]** Registerkarte: Sie können so viele Messwerte wie Spalten erstellen, die im Bericht angezeigt werden, der den Würfel verwendet.

Gehen Sie hierzu wie folgt vor:

1. Click the **[!UICONTROL Add]** button.
1. Wählen Sie den Kennzahltyp und die anzuwendende Formel aus. Im Beispiel wird die Anzahl an Frauen unter den Empfängern gezählt.

   Our measure is based on the fact schema and uses the **[!UICONTROL Count]** operator.

   ![](assets/s_advuser_cube_wz_11.png)

   Über den **[!UICONTROL Filter the measure data...]** Link können Sie nur Frauen auswählen. For more on defining measures and the available options, refer to [Defining measures](../../reporting/using/concepts-and-methodology.md#defining-measures).

   ![](assets/s_advuser_cube_wz_12.png)

1. Geben Sie den Titel der Kennzahl an und speichern Sie sie.

   ![](assets/s_advuser_cube_wz_13.png)

1. Speichern Sie den Cube.

## Cube-basierten Bericht erstellen {#creating-a-report-based-on-a-cube}

Nach der Konfiguration des Cubes kann er als Vorlage für einen neuen Bericht verwendet werden.

Gehen Sie dazu wie folgt vor:

1. Click the **[!UICONTROL Create]** button of the **[!UICONTROL Reports]** universe and select the cube you have just created.

   ![](assets/s_advuser_cube_wz_14.png)

1. Click the **[!UICONTROL Create]** button to confirm: this will take you to the report configuration and viewing page.

   Die ersten beiden verfügbaren Dimensionen werden standardmäßig in Spalten- und Zeilenform angezeigt, die Tabelle enthält jedoch keine Werte. Klicken Sie auf das zentrale Symbol, um sie zu erzeugen:

   ![](assets/s_advuser_cube_wz_15.png)

1. Sie können die Dimensionen von einer Achse in die andere verschieben, sie löschen, neue Kennzahlen hinzufügen etc. Mögliche Vorgänge sind im Folgenden beschrieben: Verwendung [von Würfeln zur Erforschung von Daten](../../reporting/using/using-cubes-to-explore-data.md).

   Verwenden Sie hierzu die entsprechenden Symbole.

   ![](assets/s_advuser_cube_wz_16.png)


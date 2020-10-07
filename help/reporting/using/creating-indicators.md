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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 100%

---


# Cubes erstellen{#creating-indicators}

Um einen Cube nutzen zu können, müssen zunächst die erforderlichen Dimensionen und Kennzahlen identifiziert und auf Ebene des Cubes erstellt werden.

Ein Cube wird in folgenden Schritten konfiguriert:

1. Wählen Sie die Arbeitstabelle aus. Siehe [Arbeitstabelle auswählen](#selecting-the-work-table).
1. Definieren Sie Dimensionen. Siehe [Dimensionen bestimmen](#defining-dimensions).
1. Definieren Sie Kennzahlen. Siehe [Kennzahlen erstellen](#building-indicators).
1. Erstellen Sie Aggregate (optional). Siehe [Aggregate berechnen und verwenden](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates).

Das nachstehende Beispiel zeigt, wie schnell ein einfacher Cube erstellt und in einem Bericht zur Kennzahlenanalyse verwendet werden kann.

Die Durchführungsschritte werden im Nachstehenden beschrieben, die verschiedenen Optionen und ihre Beschreibungen werden in den anderen Abschnitten dieses Kapitels ausführlich dargestellt.

## Arbeitstabelle auswählen {#selecting-the-work-table}

Um einen Cube zu erstellen, klicken Sie auf die oberhalb der Cube-Liste gelegene Schaltfläche **[!UICONTROL Neu]**.

![](assets/s_advuser_cube_create.png)

Wählen Sie ein Faktenschema aus, d. h. das Schema, das die zu analysierenden Elemente enthält. Im vorliegenden Beispiel wird die **Empfänger**-Tabelle ausgewählt.

![](assets/s_advuser_cube_wz_02.png)

Klicken Sie auf **[!UICONTROL Speichern]**, um den Cube zu erstellen: Er erscheint daraufhin in der Liste der Cubes und kann über seine verschiedenen Tabs konfiguriert werden.

Klicken Sie auf den Link **[!UICONTROL Quelldaten filtern...]**, wenn Sie die Berechnungen des Cubes nur auf eine Auswahl von Daten anwenden möchten.

![](assets/s_advuser_cube_wz_03.png)

## Dimensionen bestimmen {#defining-dimensions}

Dimensionen sind die Analyseachsen, die für jeden Cube entsprechend dem Faktenschema, auf das er sich bezieht, bestimmt werden. Es handelt sich um die analysierten Dimensionen, wie zum Beispiel die Zeit (Jahr, Monat, Tag etc.), eine Produkt- oder Vertragsnomenklatur (Familie, Referenz etc.), ein Populationssegment (nach Stadt, Altersgruppe, Status etc).

Diese Analyseachsen werden im Tab **[!UICONTROL Dimensionen]** des Cubes festgelegt.

Klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]**, um eine neue Dimension zu erstellen, und klicken Sie im Feld **[!UICONTROL Ausdruck]** auf das Symbol **[!UICONTROL Ausdruck bearbeiten]**, um das die betroffenen Daten enthaltende Feld auszuwählen.

![](assets/s_advuser_cube_wz_04.png)

* Wählen Sie zunächst das **Alter** der Empfänger. Für dieses Feld können Sie eine Klassierung bestimmen, um Altersgruppen zusammenzufassen und so die Lesbarkeit der Daten zu vereinfachen. Die Klassierung wird empfohlen, wenn ein Merkmal eine Vielzahl von unterschiedlichen Ausprägungen aufweist.

   Kreuzen Sie hierzu die Option **[!UICONTROL Klassierung aktivieren]** an. Klassierungsmodi werden im Abschnitt [Daten klassieren](../../reporting/using/concepts-and-methodology.md#data-binning) detailliert beschrieben.

   ![](assets/s_advuser_cube_wz_05.png)

* Fügen Sie eine Dimension vom Typ **Datum** hinzu. Im Beispiel sollen die Erstellungsdaten der Empfängerprofile angezeigt werden.

   Klicken Sie hierzu auf **[!UICONTROL Hinzufügen]** und wählen Sie das Feld **[!UICONTROL Erstellungsdatum]** in der Empfängertabelle aus.

   ![](assets/s_advuser_cube_wz_06.png)

   Sie können den Anzeigemodus der Daten auswählen. Wählen Sie hierzu die zu erzeugenden Ebenen aus:

   ![](assets/s_advuser_cube_wz_07.png)

   Im Beispiel sollen nur Jahre, Monate und Tage angezeigt werden. Es ist nicht möglich, mit Wochen und Quartalen/Monaten zugleich zu arbeiten: Diese Ebenen sind nicht kompatibel.

* Erstellen Sie eine weitere Dimension, um die Informationen in Bezug auf den Ort des Empfängers zu analysieren.

   Fügen Sie hierzu eine neue Dimension hinzu und wählen Sie im Knoten **[!UICONTROL Geografische Lokalisierung]** des Empfängerschemas das Feld Ort aus.

   ![](assets/s_advuser_cube_wz_08.png)

   Sie können auch hier die Klassierung aktivieren, um die Lesbarkeit der Informationen zu erleichtern, und in diesem Fall die Werte mit einem Auflistungswert verknüpfen.

   ![](assets/s_advuser_cube_wz_09.png)

   Wählen Sie die Auflistung in der Dropdown-Liste aus.

   ![](assets/s_advuser_cube_wz_10.png)

   Nur die in der Auflistung vorhandenen Werte werden angezeigt. Alle anderen werden unter einem Titel zusammengefasst, den Sie im Feld **[!UICONTROL Titel der anderen Werte]** definieren können.

   Weitere Informationen hierzu finden Sie unter [Klassen dynamisch verwalten](../../reporting/using/concepts-and-methodology.md#dynamically-managing-bins).

## Kennzahlen erstellen {#building-indicators}

Nach der Definition der Dimensionen muss der Berechnungsmodus der Werte bestimmt werden, die in den Zellen angezeigt werden sollen. Erstellen Sie hierzu die jeweiligen Kennzahlen im gleichnamigen Tab: Die Anzahl der Kennzahlen muss der Anzahl der Spalten entsprechen, die im Bericht angezeigt werden.****

Gehen Sie hierzu wie folgt vor:

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]**.
1. Wählen Sie den Kennzahltyp und die anzuwendende Formel aus. Im Beispiel wird die Anzahl an Frauen unter den Empfängern gezählt.

   Die Kennzahl basiert auf dem Faktenschema und verwendet die Funktion **[!UICONTROL Zählung]**.

   ![](assets/s_advuser_cube_wz_11.png)

   Über den Link **[!UICONTROL Kennzahldaten filtern...]** gelangen Sie in das Abfragefenster, das die Beschränkung der zu berücksichtigenden Werte auf Frauen ermöglicht. Die Vorgehensweise zur Bestimmung der Kennzahlen und die verfügbaren Optionen werden im Abschnitt [Kennzahlen definieren](../../reporting/using/concepts-and-methodology.md#defining-measures) beschrieben.

   ![](assets/s_advuser_cube_wz_12.png)

1. Geben Sie den Titel der Kennzahl an und speichern Sie sie.

   ![](assets/s_advuser_cube_wz_13.png)

1. Speichern Sie den Cube.

## Cube-basierten Bericht erstellen {#creating-a-report-based-on-a-cube}

Nach der Konfiguration des Cubes kann er als Vorlage für einen neuen Bericht verwendet werden.

Gehen Sie dazu wie folgt vor:

1. Klicken Sie in der Rubrik **[!UICONTROL Berichte]** auf die Schaltfläche **[!UICONTROL Erstellen]** und wählen Sie den zuvor erstellten Cube aus.

   ![](assets/s_advuser_cube_wz_14.png)

1. Klicken Sie zur Bestätigung auf die Schaltfläche **[!UICONTROL Erstellen]**: Der Bildschirm zur Konfiguration und Ansicht des Berichts wird geöffnet.

   Die ersten beiden verfügbaren Dimensionen werden standardmäßig in Spalten- und Zeilenform angezeigt, die Tabelle enthält jedoch keine Werte. Klicken Sie auf das zentrale Symbol, um sie zu erzeugen:

   ![](assets/s_advuser_cube_wz_15.png)

1. Sie können die Dimensionen von einer Achse in die andere verschieben, sie löschen, neue Kennzahlen hinzufügen etc. Mögliche Vorgänge werden unter [Cubes zur Datenanalyse verwenden](../../reporting/using/using-cubes-to-explore-data.md) beschrieben.

   Verwenden Sie hierzu die entsprechenden Symbole.

   ![](assets/s_advuser_cube_wz_16.png)


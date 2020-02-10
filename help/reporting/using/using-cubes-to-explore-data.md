---
title: Cubes zur Datenanalyse verwenden
seo-title: Cubes zur Datenanalyse verwenden
description: Cubes zur Datenanalyse verwenden
seo-description: null
page-status-flag: never-activated
uuid: ba15e7dc-0a3b-48cf-971a-7a89b8b9c9f7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
discoiquuid: e1ab1e82-8194-40a8-8df3-e7cfbaa3e777
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Cubes zur Datenanalyse verwenden{#using-cubes-to-explore-data}

Marketing Analytics ermöglicht es, auf vereinfachte Weise Berichte zu erstellen und Daten aus der Datenbank mithilfe von Cubes zu identifizieren und auszuwählen. Folgende Möglichkeiten stehen zur Verfügung:

* Erstellung von Cube-basierten Berichten. Der Prozess wird hier detailliert beschrieben: [Daten eines Berichts analysieren](#exploring-the-data-in-a-report).
* Abruf von Daten der Datenbank und Gruppierung in Listen, um beispielsweise Ziele und Sendungen zu identifizieren und zu erstellen. Weitere Informationen finden Sie unter [Zielpopulation erstellen](#building-a-target-population).
* Fügen Sie eine Pivot-Tabelle in einen Bericht ein und verweisen Sie auf einen darin vorhandenen Cube. Weitere Informationen finden Sie unter [Pivot-Tabellen in Berichte einfügen](#inserting-a-pivot-table-into-a-report).

>[!NOTE]
>
>Marketing Analytics ist erforderlich, um Cubes zu erstellen oder zu ändern. Weitere Informationen finden Sie unter [Über Cubes](../../reporting/using/about-cubes.md).

## Daten eines Berichts analysieren {#exploring-the-data-in-a-report}

### 1. Schritt - Erstellung eines Cube-basierten Berichts {#step-1---creating-a-report-based-on-a-cube}

To create a report based on a cube, click the **[!UICONTROL Create]** button in the **[!UICONTROL Reports]** universe and select the cube you want to use.

Der Prozess wird hier detailliert beschrieben: [Cube-basierten Bericht erstellen](../../reporting/using/creating-indicators.md#creating-a-report-based-on-a-cube).

### 2. Schritt - Auswahl der Zeilen und Spalten {#step-2---selecting-lines-and-columns}

Die Standardanzeige beinhaltet die ersten beiden Dimensionen des Cubes (in unserem Beispiel: Alter und Stadt).

The **[!UICONTROL Add]** buttons on each axis enable you to add dimensions.

![](assets/s_advuser_cube_in_report_03.png)

1. Um eine Dimension hinzuzufügen, klicken Sie auf die Schaltfläche Hinzufügen der betreffenden Zeile oder Spalte.
1. Wählen Sie die der Tabelle hinzuzufügende Dimension aus den verfügbaren Dimensionen aus:

   ![](assets/s_advuser_cube_in_report_04.png)

1. Legen Sie die Parameter dieser Dimension fest.

   ![](assets/s_advuser_cube_in_report_04b.png)

   Die Parameter hängen vom Datentyp und der gewählten Dimension ab.

   Beispielsweise können für Daten mehrere Ebenen verfügbar sein. Weitere Informationen finden Sie unter [Kennzahlen anzeigen](../../reporting/using/concepts-and-methodology.md#displaying-measures).

   Folgende Optionen stehen zur Verfügung:

   ![](assets/s_advuser_cube_in_report_config2.png)

   Sie können

   * die Daten beim Laden auszuklappen: Die Werte werden bei Aktivierung dieser Option bei jeder Aktualisierung des Berichts angezeigt (Standardwert: Nein);
   * das Ergebnis am Zeilenende anzuzeigen: Für in Spalten angezeigte Daten wird eine zusätzliche Option angeboten, um das Gesamtergebnis am Ende der Zeile anzuzeigen. In diesem Fall wird der Tabelle eine zusätzliche Spalte hinzugefügt (Standardwert: Ja);
   * die Daten zu sortieren: Die Spaltenwerte können nach Wert, Titel oder Kennzahl sortiert werden (Standardwert: Nach Wert);
   * die Werte absteigend (A-Z, 0-9) oder aufsteigend (Z-A, 9-0) anzuzeigen;
   * die Anzahl der beim Laden anzuzeigenden Spalten ändern (Standardwert: 200).

1. Klicken Sie zur Bestätigung auf **[!UICONTROL Ok]**: Die Dimension wird den existierenden Dimensionen hinzugefügt.

   The yellow banner above the table shows that you have made changes: click the **[!UICONTROL Save]** button to save them.

   ![](assets/s_advuser_cube_in_report_04c.png)

### 3. Schritt - Konfiguration der anzuzeigenden Kennzahlen {#step-3---configuring-the-measures-to-display}

Geben Sie nach der Positionierung der Zeilen und Spalten die anzuzeigenden Kennzahlen sowie ihren Anzeigemodus an.

Standardmäßig wird nur eine Kennzahl angezeigt. Um Kennzahlen hinzuzufügen oder zu konfigurieren, gehen Sie wie folgt vor:

1. Click the **[!UICONTROL Measures]** button.

   ![](assets/s_advuser_cube_in_report_05.png)

1. The **[!UICONTROL Use a measure]** button enables you to select one of the existing measures.

   ![](assets/s_advuser_cube_in_report_08.png)

   Wählen Sie die Informationen aus, die Sie anzeigen möchten, und geben Sie den zu verwendenden Formatierungstyp an. Die Liste der Optionen hängt vom konfigurierten Kennzahlentyp ab.

   ![](assets/s_advuser_cube_in_report_09.png)

   Die Gesamtmesskonfiguration ist auch über das **[!UICONTROL Edit the configuration of the pivot table]** Symbol in der Kopfzeile verfügbar.

   ![](assets/s_advuser_cube_in_report_config_02.png)

   Sie können insbesondere bestimmen, ob die Titel der Kennzahlen angezeigt werden sollen. Weitere Informationen finden Sie unter [Anzeige konfigurieren](../../reporting/using/concepts-and-methodology.md#configuring-the-display).

1. Es ist möglich, neue Maßnahmen zu entwickeln, indem man bestehende nutzt. Klicken Sie dazu auf **[!UICONTROL Create a measure]** und konfigurieren Sie es.

   ![](assets/s_advuser_cube_in_report_config_02a.png)

   Folgende Kennzahltypen sind möglich:

   * Kombination von Kennzahlen: ermöglicht die Erstellung der neuen Kennzahl auf Basis von existierenden Kennzahlen.

      Für diese Kennzahlen stehen folgende Funktionen zur Verfügung: Summe, Differenz, Produkt und Rate.

   * Anteil: ermöglicht die Berechnung der Anzahl an für eine gegebene Dimension gemessenen Datensätzen. Der Anteil kann in Bezug auf eine Dimension oder eine Unter-Dimension berechnet werden.
   * Abweichung: ermöglicht die Berechnung der Abweichungen der Werte einer Ebene.
   * Abweichung vom Durchschnitt: ermöglicht die Berechnung der Abweichungen in jeder Gruppe von entsprechenden Zellen in Bezug auf den Wertedurschnitt. Sie können zum Beispiel die jeweilige Einkaufsmenge der existierenden Segmente vergleichen.
   Die erstellte Kennzahl wird dem Bericht hinzugefügt.

   ![](assets/s_advuser_cube_in_report_config_02b.png)

   Nachdem Sie eine Maßnahme erstellt haben, können Sie sie bearbeiten und bei Bedarf ihre Konfiguration ändern. Klicken Sie dazu auf die **[!UICONTROL Measures]** Schaltfläche und dann auf die Registerkarte des zu bearbeitenden Messwerts.

   Klicken Sie dann auf **[!UICONTROL Edit the dynamic measure]** , um das Einstellungsmenü aufzurufen.

## Zielpopulation erstellen {#building-a-target-population}

Die basierend auf Cubes erstellten Berichte ermöglichen den Abruf von Daten aus der Datenbank und deren Speicherung in einer Liste.

Hierzu können Sie diese einem Warenkorb hinzufügen, dessen Inhalt anschließend exportiert wird.

Gehen Sie wie folgt vor, um eine Population in einer Liste zusammenzufassen:

1. Click the cells that contain the population to be collected to select them, then click the **[!UICONTROL Add to cart]** icon.

   ![](assets/s_advuser_cube_in_report_config_02c.png)

   Wiederholen Sie diesen Vorgang so oft wie nötig, um die unterschiedlichen Profile zu sammeln.

1. Click the **[!UICONTROL Show cart]** button to view its content before running the export.

   ![](assets/s_advuser_cube_in_report_config_02d.png)

1. The **[!UICONTROL Export]** button lets you group the items in the cart into a list.

   Geben Sie den Namen der Liste und den Exporttyp an.

   ![](assets/s-advuser_cube_in_report_config_02e.png)

   Click **[!UICONTROL Start]** to run the export.

1. Nach Abschluss des Exports bestätigt eine Nachricht seine korrekte Ausführung und die Anzahl der verarbeiteten Datensätze.

   ![](assets/s_advuser_cube_in_report_config_02f.png)

   Sie können den Inhalt des Warenkorbs beibehalten oder löschen.

   Die entsprechende Liste wird über das **[!UICONTROL Profiles and targets]** Universum aufgerufen.

   ![](assets/s_advuser_cube_in_report_config_02g.png)

## Pivot-Tabellen in Berichte einfügen {#inserting-a-pivot-table-into-a-report}

Gehen Sie wie folgt vor:

1. Erstellen Sie einen neuen Bericht mit einer Seite und fügen Sie eine Pivot-Tabelle ein. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table).

   ![](assets/s_advuser_cube_in_report_01.png)

1. In the **[!UICONTROL Data]** tab of the page, select a cube to process the dimensions it contains and display calculated measures.

   ![](assets/s_advuser_cube_in_report_02.png)

   Auf diese Weise können Sie den anzuzeigenden Bericht erstellen. Weitere Informationen finden Sie unter [2. Schritt - Auswahl der Zeilen und Spalten](#step-2---selecting-lines-and-columns).


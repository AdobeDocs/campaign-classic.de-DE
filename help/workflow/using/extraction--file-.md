---
title: Datenextrahierung (Datei)
description: Erfahren Sie mehr über die Arbeitsablaufaktivität für die Datenextrahierung (Datei).
page-status-flag: never-activated
uuid: c1e3fde3-183c-4602-9cef-760e4648fcf7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: fe4e6f64-eb0a-44bc-8221-6c9bfb99871f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5eb82bb5dae589cb18d42695565b25dad36006bd

---


# Datenextrahierung (Datei){#extraction-file}

You can extract data from a workflow table in an external file using the **[!UICONTROL Data extraction (file)]** activity.

>[!CAUTION]
>
>Diese Aktivität erfordert eine eingehende Transition mit den zu extrahierenden Daten.

Gehen Sie wie folgt vor, um eine Extraktion zu konfigurieren:

1. Benennen Sie die zu extrahierende Datei. Der Name kann Variablen enthalten, die über die Personalisierungsschaltfläche rechts des entsprechenden Felds eingefügt werden können.
1. Klicken Sie auf **[!UICONTROL Edit the file format...]** , um die zu extrahierenden Daten auszuwählen.

   ![](assets/s_advuser_extract_file_param.png)

   The **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** option adds an extra step to filter the final result of the aggregate, for example on a given purchase order type, customers who have ordered more than 10 times, etc.

1. Bei Bedarf können Sie der Ausgabedatei neue Spalten hinzufügen, z. B. Rechenergebnisse oder Verarbeitungsergebnisse. Wählen Sie hierzu das **[!UICONTROL Add]**-Symbol aus

   ![](assets/s_advuser_extract_file_add_col.png)

   In the additional line, click the **[!UICONTROL Edit expression]** icon to define the content of the new column.

   ![](assets/s_advuser_extract_file_add_exp.png)

   Sie greifen dann auf das Auswahlfenster zu. Klicken Sie auf **[!UICONTROL Advanced selection]** , um den Prozess auszuwählen, der auf die Daten angewendet werden soll.

   ![](assets/s_advuser_extract_file_advanced_selection.png)

   Kreuzen Sie den gewünschten Formeltyp an.

   ![](assets/s_advuser_extract_file_agregate_values.png)

## Aggregat-Funktionen {#list-of-aggregate-functions}

Folgende Aggregatfunktionen stehen zur Verfügung:

* **[!UICONTROL Count]** zur Zählung aller nicht null-Werte des zu aggregierenden Felds, einschließlich doppelter Werte (des aggregierten Felds),

   **[!UICONTROL Distinct]** zur Zählung der Gesamtanzahl verschiedener und nicht null Werte des aggregierten Felds (doppelte Werte werden vor der Berechnung ausgeschlossen),

* **[!UICONTROL Sum]** zur Berechnung der Summe der Werte eines numerischen Felds,
* **[!UICONTROL Minimum value]** zur Berechnung der Mindestwerte eines Felds (numerisch oder anderweitig),
* **[!UICONTROL Maximum value]** zur Berechnung der Höchstwerte eines Felds (numerisch oder anderweitig),
* **[!UICONTROL Average]** , um den Durchschnitt der Werte eines numerischen Felds zu berechnen.


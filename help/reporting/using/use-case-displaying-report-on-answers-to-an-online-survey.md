---
product: campaign
title: 'Anwendungsbeispiel: Anzeigen eines Berichts zu Antworten auf eine Online-Umfrage'
description: 'Anwendungsbeispiel: Anzeigen eines Berichts zu Antworten auf eine Online-Umfrage'
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Reporting, Monitoring, Surveys
exl-id: 6be12518-86d1-4a13-bbc2-b2ec5141b505
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 71b1c383-45b9-57e0-b8cd-ea2e98a01a26
    internal-label: Surveys
  - id: c309ee4e-82e4-4f7e-b608-ef345678c34e
    internal-label: Dynamic reporting
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47
    internal-label: Reporting interface
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 100%
---
# Anwendungsfall: Bericht zu Antworten auf eine Online-Umfrage anzeigen{#use-case-displaying-report-on-answers-to-an-online-survey}



Die Antworten auf Adobe Campaign-Fragebögen können abgerufen und in dedizierten Berichten analysiert werden.

Im unten stehenden Beispiel werden die Antworten auf eine Online-Umfrage gesammelt und in einem Bericht in Form einer Pivot-Tabelle angezeigt.

Gehen Sie wie folgt vor:

1. Erstellung eines Workflows zum Abruf der Umfrage-Antworten und ihrer Speicherung in einer Liste.
1. Erstellung eines Cubes, der die Daten der Liste verwendet.
1. Erstellung eines Berichts mit einer Pivot-Tabelle und Anzeige der Antwortenaufschlüsselung.

Voraussetzung für die Durchführung dieses Anwendungsbeispiels sind ein Fragebogen und zu analysierende Antworten auf diesen.

>[!NOTE]
>
>Dieses Anwendungsbeispiel kann nur implementiert werden, wenn Sie die Option **Survey Manager** erworben haben. Prüfen Sie diesbezüglich Ihren Lizenzvertrag.

## Schritt 1: Erstellung des Workflows für Datenabruf und -speicherung {#step-1---creating-the-data-collection-and-storage-workflow}

Gehen Sie wie folgt vor, um die Antworten der Umfrage abzurufen:

1. Erstellen Sie einen Workflow mit der Aktivität **[!UICONTROL Umfrageantworten]**. Weiterführende Informationen zur Verwendung dieser Aktivität finden Sie in [diesem Abschnitt](../../surveys/using/publish-track-and-use-collected-data.md#using-the-collected-data).
1. Öffnen Sie die Aktivität und wählen Sie die Umfrage aus, deren Antworten analysiert werden sollen.
1. Aktivieren Sie die Option **[!UICONTROL Alle Antwortdaten auswählen]**, um alle verfügbaren Informationen abzurufen.

   ![](../../surveys/using/assets/reporting_usecase_1_01.png)

1. Wählen Sie die zu extrahierenden Spalten aus (hier: Alle archivierten Felder). Dies sind die Felder, die die Antworten enthalten.

   ![](../../surveys/using/assets/reporting_usecase_1_02.png)

1. Fügen Sie nach der Konfiguration des Antwortenabrufs eine Aktivität vom Typ **[!UICONTROL Listen-Update]** hinzu, um die abgerufenen Daten zu speichern.

   ![](../../surveys/using/assets/reporting_usecase_1_04.png)

   Geben Sie in dieser Aktivität die zu aktualisierende Liste an und deaktivieren Sie die Option **[!UICONTROL Wenn sie existiert, Liste leeren und erneut verwenden (nicht vervollständigen)]**: Die Antworten werden so der vorhandenen Tabelle hinzugefügt. Mit dieser Option können Sie auf die Liste in einem Cube verweisen. Das mit der Liste verknüpfte Schema wird nicht bei jeder Aktualisierung neu generiert. Dadurch wird die Integrität des Cubes garantiert, der diese Liste verwendet.

   ![](../../surveys/using/assets/reporting_usecase_1_03.png)

1. Speichern und starten Sie den Workflow, um die Konfiguration zu beenden.

   ![](../../surveys/using/assets/reporting_usecase_1_05.png)

   Die angegebene Liste wird daraufhin erstellt und mit dem Schema der Umfrageantworten ergänzt.

1. Fügen Sie eine Planung hinzu, um einen täglichen Abruf der Antworten und die Aktualisierung der Liste zu konfigurieren.

   Die Aktivitäten **[!UICONTROL Listen-Update]** und **[!UICONTROL Planung]** werden erläutert in .

## Schritt 2: Erstellung des Cubes und seiner Kennzahlen {#step-2---creating-the-cube--its-measures-and-its-indicators}

Erstellen Sie anschließend den Cube und konfigurieren Sie seine Kennzahlen: Sie werden bei der Erstellung der Indikatoren verwendet. Die Indikatoren werden später im Bericht angezeigt. Weitere Informationen zur Erstellung und Konfiguration von Cubes finden Sie unter [Über Cubes](../../reporting/using/ac-cubes.md).

Im vorliegenden Beispiel basiert der Cube auf den Daten der Liste, die im zuvor erstellten Workflow angereichert wird.

![](../../surveys/using/assets/reporting_usecase_2_01.png)

Definieren Sie die im Bericht anzuzeigenden Dimensionen und Kennzahlen. Im Beispiel werden das Vertragsdatum und das Land des Antwortenden angezeigt.

![](../../surveys/using/assets/reporting_usecase_2_02.png)

Im **[!UICONTROL Vorschau]**-Tab können Sie die Anzeige des Berichts überprüfen.

## Schritt 3: Berichterstellung und Konfiguration der Datenanzeige in der Tabelle {#step-3---creating-the-report-and-configuring-the-data-layout-within-the-table}

Erstellen Sie anschließend einen auf dem Cube basierenden Bericht, um dessen Informationen zu nutzen.

![](../../surveys/using/assets/reporting_usecase_3_01.png)

Passen Sie die anzuzeigenden Informationen entsprechend Ihren Bedürfnissen an.

![](../../surveys/using/assets/reporting_usecase_3_02.png)

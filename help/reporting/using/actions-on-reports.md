---
product: campaign
title: Mit Berichten arbeiten
description: Mit Berichten arbeiten
feature: Reporting, Monitoring
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
exl-id: b30cdeaf-4ad6-473d-bdbc-91984755b609
TQID: https://experienceleague.adobe.com/ds9tKPie-3bcx7H-4tyN2Naq4SgX1ZXJavXvMTYVu8A
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: c309ee4e-82e4-4f7e-b608-ef345678c34e
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2:
  - id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47
  - id: cfda811a-e413-43a4-adf0-7370888f5cfc
  - id: afe938ea-bc18-44a4-a3fb-03e1031466cb
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 581
ht-degree: 66%

---

# Aktionen mit Berichten{#actions-on-reports}



Wenn Sie einen Bericht anzeigen, können Sie in der Symbolleiste eine bestimmte Anzahl von Aktionen ausführen. Diese sind im Folgenden aufgeführt.

![](assets/s_ncs_advuser_report_wizard_2.png)

Die Symbolleiste bietet die Möglichkeit, den Bericht zu exportieren, zu drucken, in einem Webbrowser anzuzeigen oder einen Verlauf des Berichts zu erstellen.

![](assets/s_ncs_advuser_report_wizard_04.png)

## Exportieren eines Berichts {#exporting-a-report}

Wählen Sie aus der Dropdown-Liste das Format aus, in das Sie Ihren Bericht exportieren möchten. (.xls, .pdf oder .ods).

![](assets/s_ncs_advuser_report_wizard_06.png)

Wenn ein Bericht mehrere Seiten enthält, muss der Vorgang für jede Seite wiederholt werden.

Sie können Ihren Bericht konfigurieren, um ihn im PDF-, Excel- oder OpenOffice-Format zu exportieren. Öffnen Sie den Adobe Campaign Explorer und wählen Sie den betreffenden Bericht aus.

Die Exportoptionen sind über die **[!UICONTROL Seite]**-Aktivität(en) des Berichts im Tab **[!UICONTROL Erweitert]** zugänglich.

Ändern Sie die Einstellungen von **[!UICONTROL Papier]** und **[!UICONTROL Ränder]** Ihren Anforderungen entsprechend. Sie können auch den Export einer Seite nur im PDF-Format autorisieren. Deaktivieren Sie hierzu die Option **[!UICONTROL Export in OpenOffice/Excel aktivieren]**.

![](assets/s_ncs_advuser_report_wizard_021.png)

### Exportieren nach Microsoft Excel {#exporting-into-microsoft-excel}

Für Berichte vom Typ **[!UICONTROL Liste mit Gruppierung]**, die im Excel-Format exportiert werden sollen, gelten folgende Empfehlungen und Einschränkungen:

* Die Berichte dürfen keine leeren Zeilen enthalten.

  ![](assets/export_limitations_remove_empty_line.png)

* Die Legende der Liste muss ausgeblendet sein.

  ![](assets/export_limitations_hide_label.png)

* Die Berichte dürfen keine spezifische Zellenformatierung aufweisen. Es empfiehlt sich, das **[!UICONTROL Formular-Rendering]** zu verwenden, um das Format der Zellen der Tabelle zu definieren. Der Zugriff auf das **[!UICONTROL Formular-Rendering]** erfolgt im Knoten **[!UICONTROL Administration > Konfiguration > Formular-Rendering]**.
* Es wird empfohlen, keinen HTML-Inhalt einzufügen.
* Wenn ein Bericht mehrere Elemente vom Typ Tabelle, Grafik etc. enthält, werden diese untereinander exportiert.
* Sie können den Zeilenumbruch in Zellen erzwingen: Diese Konfiguration wird in Excel beibehalten. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../reporting/using/creating-a-table.md#defining-cell-format).

### Export verzögern {#postpone-the-export}

Sie können den Export eines Berichts aufschieben, um beispielsweise auf asynchrone Aufrufe zu warten. Geben Sie dazu den folgenden Parameter im Initialisierungsskript der Seite ein:

```
document.nl_waitBeforeRender = true;
```

Bedienen Sie sich zur Aktivierung des Exports und zur Konvertierung ins PDF-Format der Funktion **document.nl_renderToPdf()** ohne Parameter.

### Speicher zuteilen {#memory-allocation}

Beim Export von gewissen umfangreichen Berichten kann es zu Problemen bei der Speicherzuteilung kommen.

In bestimmten Fällen ist der Standardwert **maxMB** (**SKMS** für gehostete Instanzen) der JavaScript, der in der Konfigurationsdatei **serverConf.xml** angegeben ist, auf 64 MB festgelegt. Wenn beim Exportieren eines Berichts Speicherfehler auftreten, kann es empfohlen werden, diese Zahl auf 512 MB zu erhöhen:

```
<javaScript maxMB="512" stackSizeKB="8"/>
```

Um die Änderungen der Konfiguration zu übernehmen, ist ein Neustart des **nlserver**-Dienstes erforderlich.

Weiterführende Informationen zur Datei **serverConf.xml** finden Sie in [diesem Abschnitt](../../production/using/configuration-principle.md).

Weiterführende Informationen zum **nlserver**-Service finden Sie in [diesem Abschnitt](../../production/using/administration.md).

## Drucken eines Berichts {#printing-a-report}

Sie haben die Möglichkeit, Ihren Bericht zu drucken. Klicken Sie hierzu auf das Drucker-Symbol. Das Druck-Dialogfenster öffnet sich.

Um das Druckergebnis zu optimieren, öffnen Sie die Druckoptionen von Explorer und aktivieren Sie die Option **[!UICONTROL Farben und Hintergrundbilder drucken]**.

![](assets/s_ncs_advuser_report_print_options.png)

## Erstellen von Berichtsarchiven {#creating-report-archives}

Die Erstellung eines Verlaufs ermöglicht es Ihnen, die Entwicklung der Berichtsdaten über die Zeit zu beobachten. Zudem können Statistiken eines bestimmten Zeitpunkts eingesehen werden.

Um einen Verlauf zu erstellen, öffnen Sie den betreffenden Bericht und klicken Sie auf das Symbol zur Verlaufserstellung.

![](assets/s_ncs_advuser_report_wizard_07.png)

Durch Klick auf das entsprechende Symbol können Sie die existierenden Verläufe aus- oder einblenden.

![](assets/s_ncs_advuser_report_history_06.png)

Die Archivierungsdaten werden unter dem Symbol Einblenden/Ausblenden angezeigt. Klicken Sie auf das Archiv, um es anzuzeigen.

![](assets/s_ncs_advuser_report_history_04.png)

Es ist möglich, ein Berichtsarchiv zu löschen. Wechseln Sie dazu zum Adobe Campaign-Knoten, in dem Ihre Berichte gespeichert sind. Klicken Sie auf den Tab **[!UICONTROL Verläufe]**, markieren Sie den betreffenden Verlauf und klicken Sie auf **[!UICONTROL Löschen]**.

![](assets/s_ncs_advuser_report_history_01.png)

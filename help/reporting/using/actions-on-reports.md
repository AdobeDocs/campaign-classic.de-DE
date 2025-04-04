---
product: campaign
title: Mit Berichten arbeiten
description: Mit Berichten arbeiten
feature: Reporting, Monitoring
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
exl-id: b30cdeaf-4ad6-473d-bdbc-91984755b609
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 100%

---

# Aktionen mit Berichten{#actions-on-reports}



Über die oberhalb der Berichtansicht gelegene Symbolleiste können verschiedene Aktionen ausgeführt werden. Diese werden im Folgenden dargestellt.

![](assets/s_ncs_advuser_report_wizard_2.png)

Die Symbolleiste bietet die Möglichkeit, den Bericht zu exportieren, zu drucken, in einem Webbrowser anzuzeigen oder einen Verlauf des Berichts zu erstellen.

![](assets/s_ncs_advuser_report_wizard_04.png)

## Exportieren eines Berichts {#exporting-a-report}

Wählen Sie in der Dropdown-Liste das Format aus, in dem der Bericht exportiert werden soll: .xls, .pdf oder .ods.

![](assets/s_ncs_advuser_report_wizard_06.png)

Wenn ein Bericht mehrere Seiten enthält, muss der Vorgang für jede Seite wiederholt werden.

Sie können Ihren Bericht für den Export im PDF-, Excel- oder OpenOffice-Format konfigurieren. Öffnen Sie den Adobe Campaign-Explorer und wählen Sie den betreffenden Bericht aus.

Die Exportoptionen sind über die **[!UICONTROL Seite]**-Aktivität(en) des Berichts im Tab **[!UICONTROL Erweitert]** zugänglich.

Ändern Sie die Einstellungen von **[!UICONTROL Papier]** und **[!UICONTROL Ränder]** nach Ihren Bedürfnissen. Sie können auch den Export einer Seite nur im PDF-Format zulassen. Deaktivieren Sie hierzu die Option **[!UICONTROL Export in OpenOffice/Excel aktivieren]**.

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

Sie haben die Möglichkeit, den Export eines Berichts zu verzögern, z. B. um auf asynchrone Aufrufe zu warten. Geben Sie hierzu den folgenden Parameter im Initialisierungsscript der Seite an:

```
document.nl_waitBeforeRender = true;
```

Bedienen Sie sich zur Aktivierung des Exports und zur Konvertierung ins PDF-Format der Funktion **document.nl_renderToPdf()** ohne Parameter.

### Speicher zuteilen {#memory-allocation}

Beim Export von gewissen umfangreichen Berichten kann es zu Problemen bei der Speicherzuteilung kommen.

In einigen Instanzen ist der in der Konfigurationsdatei **serverConf.xml** angegebene Standardwert **maxMB** (**SKMS** bei gehosteten Instanzen) im JavaScript mit 64 MB angegeben. Wenn beim Export von Berichten Fehler bezüglich Speichermangel auftreten, empfiehlt es sich, diesen Wert auf 512 MB zu erhöhen:

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

Die gespeicherten Verläufe können über das Ein-/Ausblende-Symbol angezeigt werden. Klicken Sie auf einen Verlauf, um ihn einzusehen.

![](assets/s_ncs_advuser_report_history_04.png)

Ein Berichtsarchiv kann gelöscht werden. Gehen Sie dazu zum Adobe Campaign-Knoten, in dem Ihre Berichte gespeichert sind. Klicken Sie auf den Tab **[!UICONTROL Verläufe]**, markieren Sie den betreffenden Verlauf und klicken Sie auf **[!UICONTROL Löschen]**.

![](assets/s_ncs_advuser_report_history_01.png)

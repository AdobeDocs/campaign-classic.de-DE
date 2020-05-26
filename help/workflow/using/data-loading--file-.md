---
title: Laden (Datei)
description: Erfahren Sie mehr über die Aktivität „Laden (Datei)“.
page-status-flag: never-activated
uuid: c064aa23-412e-49b4-a51d-b0e8ca572f2e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: dcb5b8e8-be38-4d89-908d-f57c2413a9bc
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e3de6f7b21d912efa4f6faca5e57cb480e8f1805
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 96%

---


# Laden (Datei){#data-loading-file}

## Verwendung {#use}

Mit der **[!UICONTROL Aktivität zum Laden von Daten (Datei)]** können Sie direkt auf eine Quelle externer Daten zugreifen und diese in Adobe Campaign verwenden. Tatsächlich befinden sich nicht immer alle für Targeting-Vorgänge erforderlichen Daten in der Adobe Campaign-Datenbank: es kann in externen Dateien verfügbar gemacht werden.

Die zu ladende Datei kann in der Transition angegeben oder bei Ausführung der Aktivität berechnet werden. Es kann sich beispielsweise um die Liste der zehn meistgekauften Artikel eines Kunden handeln, wobei die Kaufhandlungen in einer separaten, externen Datenbank verwaltet werden.

Im oberen Bereich des Fensters zur Konfiguration dieser Aktivität wird das Dateiformat angegeben. Wählen Sie eine Beispieldatei aus, die das gleiche Format aufweist, wie die zu importierende Datei. Die Datei kann lokal oder auf dem Server gespeichert werden.

>[!CAUTION]
>
>Unterstützt werden ausschließlich Dateiformate mit einfach strukturierten Daten wie beispielsweise .txt, .csv etc. Die Verwendung von XML wird nicht empfohlen.

![](assets/s_advuser_wf_etl_file.png)

Sie können eine Vorab-Bearbeitung definieren, die beim Dateiimport ausgeführt werden soll, z. B. um die Datei nicht auf dem Server entpacken zu müssen (und damit Platz für die entpackte Datei zu sparen), sondern um das Entpacken in die Dateiverarbeitung aufzunehmen. Wählen Sie die Option **[!UICONTROL Vorab-Bearbeitung der Datei vorsehen]** aus und danach Sie dieser drei Optionen: **[!UICONTROL Keine]**, **[!UICONTROL Dekomprimierung]** (zcat) oder **[!UICONTROL Entschlüsseln]** (gpg).

## Datei formatieren {#defining-the-file-format}

Beim Laden einer Datei werden das Spaltenformat automatisch erkannt und Standardparameter für jeden Datentyp angewendet. Diese Standardparameter können angepasst werden, um beispielsweise im Fall von Fehlern oder leeren Werten einen spezifischen Umgang mit Ihren Daten zu definieren.

Verwenden Sie in diesem Fall im Hauptfenster der Aktivität **[!UICONTROL Laden (Datei)]** den Link **[!UICONTROL Zur Formatänderung hier klicken...]**, um das Detailfenster zur Formatbearbeitung zu öffnen.

![](assets/file_loading_columns_format.png)

Sie haben nun die Möglichkeit, allgemeine Formatierungsoptionen der Datei sowie das Format der einzelnen Spalten anzupassen.

In den allgemeinen Formatierungsoptionen kann beispielsweise die Art der Spaltenerkennung definiert werden (Kodierung der Datei, verwendete Trennzeichen etc.).

Verschiedene Optionen zum Umgang mit den Spaltenwerten stehen zur Auswahl:

* **[!UICONTROL Spalte ignorieren]**: Spalte wird beim Laden der Daten nicht berücksichtigt.
* **[!UICONTROL Datentyp]**: Angabe des in der Spalte erwarteten Datentyps.
* **[!UICONTROL NULL erlauben]**: Angabe des Umgangs mit leeren Werten.

   * **[!UICONTROL Adobe-Campaign-Standardeinstellung]**: Erzeugt nur bei numerischen Feldern einen Fehler. Fügt bei anderen Feldern den Wert NULL ein.
   * **[!UICONTROL Leer erlaubt]**: Leere Werte sind zulässig, der Wert NULL wird eingefügt.
   * **[!UICONTROL Leer nicht erlaubt]**: Erzeugung eines Fehlers bei leeren Werten.

* **[!UICONTROL Länge]**: Angabe der maximal zulässigen Anzahl an Zeichen für Daten vom Typ **String**.
* **[!UICONTROL Format]**: Definition des Formats von Uhrzeit und Datum.
* **[!UICONTROL Formatierung]**: Definition der Groß- und Kleinschreibung bei Daten vom Typ **String**.

   * **[!UICONTROL Keine Angabe]**: Der importierte String wird nicht geändert.
   * **[!UICONTROL Ersten Buchstaben großschreiben]**: Der erste Buchstabe aller Worte des Strings wird großgeschrieben.
   * **[!UICONTROL Großbuchstaben]**: Alle Buchstaben des Strings werden großgeschrieben.
   * **[!UICONTROL Kleinbuchstaben]**: Alle Buchstaben des Strings werden kleingeschrieben.

* **[!UICONTROL Umgang mit Leerzeichen]**: Angabe, ob gewisse Leerzeichen in einem String ignoriert werden sollen. Bei Auswahl von **[!UICONTROL Leerzeichen ignorieren]** werden nur Leerzeichen am Anfang und am Ende eines Strings ignoriert.
* **[!UICONTROL Umgang mit Fehlern]**: Definition des Verhaltens beim Auftritt von Fehlern.

   * **[!UICONTROL Wert ignorieren]**: Der Wert wird ignoriert. Im Ausführungsprotokoll des Workflows wird ein Hinweis erzeugt.
   * **[!UICONTROL Zeile zurückweisen]**: Die gesamte Zeile wird nicht verarbeitet.
   * **[!UICONTROL Bei Fehler Standardwert verwenden]**: Der den Fehler verursachende Wert wird durch den im Feld **[!UICONTROL Standardwert]** gespeicherten Wert ersetzt.
   * **[!UICONTROL Bei fehlender Neukodifizierung Zeile zurückweisen]**: Die gesamte Zeile wird nicht verarbeitet, es sei denn, für den fehlerhaften Wert wurde ein Mapping definiert (siehe nachfolgend die Option **[!UICONTROL Mapping]**).
   * **[!UICONTROL Bei fehlender Neukodifizierung Standardwert verwenden]**: Der den Fehler verursachende Wert wird durch den im Feld **[!UICONTROL Standardwert]** gespeicherten Wert ersetzt, es sei denn, für den fehlerhaften Wert wurde ein Mapping definiert (siehe nachfolgend die Option **[!UICONTROL Mapping]**).

* **[!UICONTROL Standardwert]**: Angabe des Standardwerts, der im Bezug auf den jeweils definierten Umgang mit Fehlern zum Tragen kommt.
* **[!UICONTROL Mapping]**: Auf dieses Feld kann nur in der Detailkonfiguration einer Spalte zugegriffen werden (entweder per Doppelklick oder mithilfe der entsprechenden Schaltfläche rechts der Spaltenliste). Es ermöglicht im Zuge des Imports die Umwandlung gewisser Werte. So kann beispielsweise &quot;drei&quot; in &quot;3&quot; umgewandelt werden.

## Anwendungsbeispiel: Daten abrufen und in die Datenbank laden {#example--collecting-data-and-loading-it-in-the-database}

Im vorliegenden Beispiel wird täglich eine Datei vom Server abgerufen, ihr Inhalt geladen und die Datenbank mit den neuen Daten aktualisiert. Die abgerufene Datei enthält Daten von Kunden eines Geschäfts, die Käufe getätigt haben (unter oder über 3000 Euro), denen ein Kauf zurückerstattet wurde oder die das Geschäft besucht haben, ohne einen Kauf zu tätigen. Je nach abgerufener Information werden die Datenbankprofile unterschiedlichen Vorgängen unterzogen.

![](assets/s_advuser_load_file_sample_0.png)

1. Die Datei-Wächter-Aktivität dient dazu, in definierten Zeitabständen die in einem bestimmten Verzeichnis gespeicherten Dateien abzurufen.

   Die Informationen bezüglich des oder der abzurufenden Verzeichnisse werden im **[!UICONTROL Verzeichnis]**-Tab angegeben. Im vorliegenden Beispiel sollen alle Textformat-Dateien abgerufen werden, deren Name das Wort &#39;Kunde&#39; enthält und die im Verzeichnis tmp/Adobe/Data/files des Servers gespeichert sind.

   Weiterführende Informationen zum Thema **[!UICONTROL Datei-Wächter]** finden Sie im Abschnitt [Datei-Wächter](../../workflow/using/file-collector.md).

   ![](assets/s_advuser_load_file_sample_1.png)

   Im **[!UICONTROL Planung]**-Tab wird die Ausführungshäufigkeit des Datei-Wächters konfiguriert, d. h. in welchen Abständen das Vorhandensein derartiger Dateien überprüft wird.

   Hier soll der Datei-Wächter an allen Tagen, an denen die Geschäfte geöffnet haben, um 21 Uhr ausgelöst werden.

   ![](assets/s_advuser_load_file_sample_2.png)

   Klicken Sie auf die Schaltfläche **[!UICONTROL Ändern...]** rechts unten im Editor, um die Planung entsprechend zu konfigurieren.

   Weitere Informationen hierzu finden Sie im Abschnitt [Planung](../../workflow/using/scheduler.md).

1. Konfigurieren Sie anschließend die Datei-Laden-Aktivität, um anzugeben, wie die abgerufenen Dateien zu lesen sind. Wählen Sie hierzu eine Beispieldatei aus, die dieselbe Struktur aufweist, wie die zu ladenden Dateien.

   ![](assets/s_advuser_load_file_sample_3.png)

   Im vorliegenden Beispiel besteht die Datei aus fünf Spalten:

   * Die erste Spalte enthält einen dem Ereignis entsprechenden Code: Kauf (Transaktionsbetrag kleiner oder größer als 3000 Euro), Kein Kauf oder Rückgabe eines oder mehrerer Artikel.
   * Die anderen Spalten enthalten jeweils die Vornamen, Nachnamen und E-Mail-Adressen der Kunden sowie die Kundennummern.
   Die Formatierung der Daten geschieht auf die gleiche Weise wie bei einem Datenimport in Adobe Campaign. Weiterführende Informationen finden Sie in diesem [Abschnitt](../../platform/using/importing-data.md#step-2---source-file-selection).

1. Positionieren Sie im Anschluss eine Aufspaltungsaktivität und geben Sie je nach Wert in der **Ereignis**-Spalte die zu erstellenden Teilmengen an.

   Die Funktionsweise dieser Aktivität wird im Abschnitt beschrieben.

   ![](assets/s_advuser_load_file_sample_4.png)

   Erstellen Sie eine Teilmenge pro Wert in der **Ereignis**-Spalte.

   ![](assets/s_advuser_load_file_sample_5.png)

   Die **[!UICONTROL Aufspaltung]** stellt sich somit wie folgt dar:

   ![](assets/s_advuser_load_file_sample_6.png)

1. Definieren Sie nun für jeden Populationstyp den Anschlussvorgang. Im vorliegenden Beispiel wird die Datenbank aktualisiert. Dies erfolgt im Zuge von **[!UICONTROL Daten-Update]**-Aktivitäten, die jeweils an eine der ausgehenden Transitionen der **[!UICONTROL Aufspaltung]** angeschlossen werden.

   Die Aktivität **[!UICONTROL Daten-Update]** wird im Abschnitt [Daten-Update](../../workflow/using/update-data.md) genauer beschrieben.


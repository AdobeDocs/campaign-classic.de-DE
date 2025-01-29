---
product: campaign
title: HTTP-Übertragung
description: Erfahren Sie mehr über die Workflow-Aktivität "HTTP-Übertragung".
feature: Workflows
exl-id: b6005eae-5fbc-4e22-ab3a-c9b7ed6506f6
source-git-commit: a0c0c7d13704b0155004e578d6739852ceb43c81
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 100%

---

# HTTP-Übertragung{#web-download}



Die **HTTP-Übertragung** lädt Dateien über eine explizite URL, ein externes Konto oder eine Adobe Campaign-Instanz unter Verwendung des Hypertext Transfer Protocols (HTTP). Sowohl die GET- als auch die POST-Methode können zur Anwendung kommen.

## Eigenschaften {#properties}

1. **Auswahl der Webdatei**

   Die Angabe der zu übertragenden Datei kann entweder über eine explizite URL, über ein externes HTTP-Konto oder über eine Adobe Campaign-Instanz erfolgen. Folgende Parameter stehen zur Verfügung:

   * **[!UICONTROL Explizite URL]**: Die URL wird im entsprechenden Feld angegeben. Die URL kann Variablen enthalten.

     ![](assets/download_web_edit.png)

   * Bei Verwendung eines **[!UICONTROL externen Kontos]** wird das Konto aus der Dropdown-Liste ausgewählt und die zu ladende Datei angegeben.

     Externe Konten werden über den Knoten **[!UICONTROL Administration > Plattform > Externe Konten]** im Adobe Campaign-Navigationsbaum konfiguriert. Die Kontoparameter können über das Symbol **[!UICONTROL Link bearbeiten]** bearbeitet werden.

     ![](assets/download_web_edit_external.png)

   * **[!UICONTROL Adobe Campaign-Instanz]**: Die Übertragung erfolgt über eine Adobe Campaign-Instanz.

     ![](assets/download_web_edit_instance.png)

1. **Verlaufserstellung**

   Der Link **[!UICONTROL Verlaufsparameter der Dateien...]** ermöglicht die Angabe des Speicherverzeichnisses für die übertragenen Dateien und der Bereinigungsparameter.

   ![](assets/download_web_edit_hist.png)

   Folgende Optionen stehen zur Verfügung:

   * **[!UICONTROL Standard-Speicherverzeichnis nutzen]**: Die Datei wird immer verschoben, bevor sie verarbeitet wird. Wenn diese Option aktiviert ist, wird die Datei in das Standard-Speicherverzeichnis (das Verzeichnis **vars** im Adobe Campaign-Installationsordner) verschoben. Um ein Speicherverzeichnis anzugeben, deaktivieren Sie das Kontrollkästchen und geben Sie seinen Pfad in das Feld **[!UICONTROL Speicherverzeichnis]** ein.
   * **[!UICONTROL Anzahl Dateien]**: Geben Sie die Anzahl an Dateien an, die maximal im Speicherverzeichnis beibehalten werden soll.
   * **[!UICONTROL Maximale Größe (in MB)]**: Geben Sie die Größe an, die das Speicherverzeichnis nicht überschreiten darf (in Megabytes).

   Jede Datei wird mindestens 24 Stunden aufbewahrt, bevor Sie den Bereinigungsregeln unterzogen wird. Die Bereinigung erfolgt zu Beginn der Aktivität und berücksichtigt daher nicht die Dateien der aktuellen Workflow-Ausführung.

   Die Löschung beginnt jeweils mit den ältesten Dateien und endet mit den neuesten. Die ältesten Dateien werden gelöscht bis beide Bereinigungsregeln geprüft wurden. Wenn beispielsweise die maximale Anzahl auf 100 begrenzt wurde, enthält das Speicherverzeichnis stets die 100 vor Beginn des Workflows neuesten Dateien, zuzüglich der vom laufenden Workflow übertragenen Dateien.

   Wenn Sie für die Optionen **[!UICONTROL Anzahl Dateien]** und **[!UICONTROL Maximale Größe (in MB)]** keine Grenzwerte vorschreiben möchten, können Sie jeweils den Wert 0 angeben.

1. **Erweiterte Parameter**

   Der Link **[!UICONTROL Erweiterte Parameter...]** bietet Zugriff auf folgende Optionen:

   * **[!UICONTROL Den Weiterleitungen folgen]**: Mithilfe der Dateiweiterleitung können Sie Überschreibungen verwenden, um die Dateneingabe oder -ausgabe an ein Gerät eines anderen Typs zu leiten.
   * **[!UICONTROL HTTP-Header zur Datei hinzufügen]**: In einigen Fällen ist es vorteilhaft, einer Datei zusätzliche HTTP-Header hinzuzufügen. In den meisten Fällen werden diese Header verwendet, um zusätzliche Informationen zur Fehlerbehebung zu liefern, oder für [Cross-Origin Resource Sharing (CORS)](https://developer.mozilla.org/docs/Web/HTTP/CORS) oder um bestimmte Caching-Anweisungen festzulegen.
   * **[!UICONTROL HTTP-Ausgabecode ignorieren]**: HTTP-Ausgabe-Codes, auch HTTP-Status-Codes genannt, geben das Ergebnis einer HTTP-Anfrage an.

   ![](assets/download_web_edit_advanced.png)

   Die Option **[!UICONTROL Fehler verarbeiten]** wird im Abschnitt [Verarbeitungsfehler](monitoring-workflow-execution.md#processing-errors) erläutert.

## Ausgabeparameter {#output-parameters}

* filename: Vollständiger Name der übertragenen Datei.

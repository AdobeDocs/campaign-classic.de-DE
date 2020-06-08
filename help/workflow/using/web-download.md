---
title: HTTP-Übertragung
seo-title: HTTP-Übertragung
description: HTTP-Übertragung
seo-description: null
page-status-flag: never-activated
uuid: 44039e9c-0cd8-4d3f-b73f-e01c5343835a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: event-activities
discoiquuid: 8590cc75-11c8-450d-90e8-56744e12ac70
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b1a961822224ab0a9551f51942a5f94cf201c8ee
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 100%

---


# HTTP-Übertragung{#web-download}

Die **HTTP-Übertragung** lädt Dateien über eine explizite URL, ein externes Konto oder eine Adobe-Campaign-Instanz unter Verwendung des Hypertext Transfer Protocols (HTTP). Sowohl die GET- als auch die POST-Methode können zur Anwendung kommen.

## Eigenschaften {#properties}

1. **Auswahl der Webdatei**

   Die Angabe der zu übertragenden Datei kann entweder über eine explizite URL, über ein externes HTTP-Konto oder über eine Adobe-Campaign-Instanz erfolgen. Folgende Parameter stehen zur Verfügung:

   * **[!UICONTROL Explizite URL]**: Die URL wird im entsprechenden Feld angegeben. Die URL kann Variablen enthalten.

      ![](assets/download_web_edit.png)

   * Bei Verwendung eines **[!UICONTROL externen Kontos]** wird das Konto aus der Dropdown-Liste ausgewählt und die zu ladende Datei angegeben.

      Externe Konten werden im Knoten **[!UICONTROL Administration > Plattform > Externe Konten]** des Navigationsbaums konfiguriert. In der Aktivität kann über das Symbol **[!UICONTROL Verknüpftes Element öffnen]** auf die Parameter zugegriffen werden.

      ![](assets/download_web_edit_external.png)

   * **[!UICONTROL Adobe-Campaign-Instanz]**: Die Übertragung erfolgt über eine Adobe-Campaign-Instanz.

      ![](assets/download_web_edit_instance.png)

1. **Verlaufserstellung**

   Der Link **[!UICONTROL Verlaufsparameter der Dateien...]** ermöglicht die Angabe des Speicherverzeichnisses für die übertragenen Dateien und der Bereinigungsparameter.

   ![](assets/download_web_edit_hist.png)

   Folgende Optionen stehen zur Verfügung:

   * **[!UICONTROL Standard-Speicherverzeichnis nutzen]**: Dateien werden systematisch vor der Verarbeitung verschoben. Wenn diese Option angekreuzt ist, werden die Dateien in das Standard-Speicherverzeichnis (Verzeichnis **vars** im Adobe-Campaign-Installationsordner) verschoben. Wenn Sie ein anderes Speicherverzeichnis verwenden möchten, können Sie die Option abwählen und das von Ihnen gewünschte Verzeichnis im dann erscheinenden Feld **[!UICONTROL Speicherverzeichnis]** angeben.
   * **[!UICONTROL Anzahl Dateien]**: Geben Sie die Anzahl an Dateien an, die maximal im Speicherverzeichnis beibehalten werden soll.
   * **[!UICONTROL Maximale Größe (in MB)]**: Geben Sie die Größe an, die das Speicherverzeichnis nicht überschreiten darf (in Megabytes).

   Jede Datei wird mindestens 24 Stunden aufbewahrt, bevor Sie den Bereinigungsregeln unterzogen wird. Die Bereinigung erfolgt zu Beginn der Aktivität und berücksichtigt daher nicht die Dateien der aktuellen Workflow-Ausführung.

   Die Löschung beginnt jeweils mit den ältesten Dateien und endet mit den neuesten. Die ältesten Dateien werden gelöscht bis beide Bereinigungsregeln geprüft wurden. Wenn beispielsweise die maximale Anzahl auf 100 begrenzt wurde, enthält das Speicherverzeichnis stets die 100 vor Beginn des Workflows neuesten Dateien, zuzüglich der vom laufenden Workflow übertragenen Dateien.

   Wenn Sie für die Optionen **[!UICONTROL Anzahl Dateien]** und **[!UICONTROL Maximale Größe (in MB)]** keine Grenzwerte vorschreiben möchten, können Sie jeweils den Wert 0 angeben.

1. **Erweiterte Parameter**

   Der Link **[!UICONTROL Erweiterte Parameter...]** bietet Zugriff auf folgende Optionen:

   ![](assets/download_web_edit_advanced.png)

   Die Option **[!UICONTROL Fehler verarbeiten]** wird im Abschnitt [Verarbeitungsfehler](../../workflow/using/monitoring-workflow-execution.md#processing-errors) erläutert.

## Ausgabeparameter {#output-parameters}

* filename: Vollständiger Name der übertragenen Datei.

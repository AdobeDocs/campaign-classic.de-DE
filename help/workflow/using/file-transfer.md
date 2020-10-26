---
title: Dateiversand
description: Erfahren Sie mehr über die Dateiübertragung.
page-status-flag: never-activated
uuid: 6431d908-a110-4a9a-8848-9abf78ef8157
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: event-activities
discoiquuid: d8b49f68-c783-43fc-9907-e8480ecd28c2
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '621'
ht-degree: 100%

---


# Dateiversand{#file-transfer}

Die **Dateiübertragung** ermöglicht den Empfang, den Versand und die Prüfung auf Existenz von Dateien oder das Listen von Dateien auf einem Server. Als Protokoll wird der Amazon Simple Storage Service (S3), das File Transfer Protocol (FTP) oder das Secure File Transfer Protocol (SFTP) verwendet.
Mit einer S3- oder SFTP-Verbindung können Sie auch Segmentdaten mit der Adobe-Echtzeit-Kundendatenplattform in Adobe Campaign importieren. Weitere Informationen hierzu finden Sie in [dieser Dokumentation](https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html).

>[!NOTE]
>
>Best Practices und Problembehebung bei der Verwendung von SFTP-Servern finden Sie auf [dieser Seite](../../platform/using/sftp-server-usage.md).

## Eigenschaften {#properties}

Wählen Sie im Feld **[!UICONTROL Aktion]** die auszuführende Aktivität aus.

![](assets/file_transfert_action.png)

Die weitere Konfiguration hängt von der gewählten Aktion ab.

1. **Dateiempfang**

   Zum Empfang von auf einem Remote-Server gespeicherten Dateien ist im Feld **[!UICONTROL Aktion]** die Option **[!UICONTROL Dateiempfang]** auszuwählen und die URL anzugeben.

   ![](assets/file_transfert_edit.png)

   Aktivieren Sie die Option **[!UICONTROL Externes Konto verwenden]**, wenn Sie ein im Knoten **[!UICONTROL Administration > Plattform > Externe Konten]** konfiguriertes S3-, FTP- oder SFTP-Konto verwenden möchten. Geben Sie anschließend das Serververzeichnis an, das die zu übertragenden Dateien enthält.

   ![](assets/file_transfert_edit_external.png)

1. **Dateiversand**

   Zum Versand einer Datei an einen Server ist im Feld **[!UICONTROL Aktion]** die Option **[!UICONTROL Dateiversand]** auszuwählen und im Bereich **[!UICONTROL Remote-Server]** die URL des Zielservers anzugeben. Die Parameter sind mit denen des Dateiempfangs identisch (siehe oben).

   Die Quelldatei kann aus einer vorgeschalteten Aktivität stammen. In diesem Fall ist die Option **[!UICONTROL Durch vorhergehende Aktivität erzeugte Datei verwenden]** anzukreuzen.

   ![](assets/file_transfert_edit_send.png)

   Wählen Sie andernfalls die genannte Option ab und klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]**, um eine andere Datei auszuwählen. Geben Sie den Pfad zur Datei an, die versendet werden soll. Klicken Sie gegebenenfalls erneut auf **[!UICONTROL Hinzufügen]**, um weitere Dateien zu versenden. Für jede Datei wird ein separater Tab erstellt.

   ![](assets/file_transfert_source.png)

   Mithilfe der Pfeile kann die Reihenfolge der Tabs angepasst werden. Die Dateien werden in dieser Reihenfolge an den Server übertragen.

   Bei Auswahl der Option **[!UICONTROL Verlauf der übertragenen Dateien speichern]** werden die verschiedenen Übertragungen im Verzeichnis protokolliert.

1. **Existenztest einer Datei**

   Um das Vorhandensein einer Datei zu prüfen, ist im Feld **[!UICONTROL Aktion]** die Option **[!UICONTROL Existenztest einer Datei]** auszuwählen. Die Konfiguration des Remote-Servers entspricht der für den Dateiempfang. Weiterführende Informationen dazu finden Sie in diesem [Abschnitt](#properties).

   ![](assets/file_transfert_edit_test.png)

1. **Dateiauflistung**

   Um eine Liste der vorhandenen Dateien zu erhalten, ist im Feld **[!UICONTROL Aktion]** die Option **[!UICONTROL Dateiauflistung]** auszuwählen. Die Konfiguration des Remote-Servers entspricht der für den Dateiempfang. Weiterführende Informationen dazu finden Sie in diesem [Abschnitt](#properties).

   Die Option **[!UICONTROL Alle Dateien auflisten]**, die bei Auswahl der Aktion **[!UICONTROL Dateiauflistung]** erscheint, ermöglicht es, alle auf dem Server befindlichen Dateien in der Ereignisvariable **vars.filenames** zu erfassen. Die Dateinamen werden durch `\n`-Zeichen getrennt angegeben.

Zwei weitere Optionen stehen generell für die Dateiübertragung zur Verfügung:

* Die Option **[!UICONTROL Fehlen von Dateien bearbeiten]** erzeugt eine Transition, die aktiviert wird, wenn im angegebenen Verzeichnis keine Datei vorhanden ist.
* Die Option **[!UICONTROL Fehler verarbeiten]** wird im Abschnitt [Verarbeitungsfehler](../../workflow/using/monitoring-workflow-execution.md#processing-errors) erläutert.

Der Link **[!UICONTROL Erweiterte Parameter...]** bietet Zugriff auf folgende Optionen:

![](assets/file_transfert_advanced.png)

* **[!UICONTROL Quelldateien nach der Übertragung löschen]**

   Löscht die Dateien auf dem Remote-Server.

* **[!UICONTROL SSL verwenden]**

   Verwendet eine gesicherte Verbindung bei der Dateiübertragung (SSL-Protokoll).

* **[!UICONTROL Sitzungsprotokolle anzeigen]**

   Ruft die S3-, FTP- bzw. SFTP-Übertragungslogs ab und fügt sie in die Workflow-Logs ein.

* **[!UICONTROL Passiven Modus deaktivieren]**

   Ermöglicht es, den für die Übertragung zu verwendenden Verbindungsport anzugeben.

Über den Link **[!UICONTROL Verlaufsparameter der Dateien...]** besteht Zugriff auf Optionen, die im Abschnitt [HTTP-Übertragung](../../workflow/using/web-download.md) (im Schritt **[!UICONTROL Verlaufserstellung]**) beschrieben werden.

## Eingabeparameter {#input-parameters}

* filename

   Vollständiger Name der übertragenen Datei.

## Ausgabeparameter {#output-parameters}

* filename

   Vollständiger Name der empfangenen Datei, wenn die Option **[!UICONTROL Durch vorhergehende Aktivität erzeugte Datei verwenden]** angekreuzt wurde.

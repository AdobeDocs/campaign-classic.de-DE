---
product: campaign
title: Dateiübertragung
description: Erfahren Sie mehr über die Workflow-Aktivität "Dateiübertragung".
feature: Workflows, Data Management
hide: true
exl-id: 8025d207-3bc0-400f-b6a4-a72765e5a9d2
TQID: https://experienceleague.adobe.com/Y8ggbKYhnIg8ncfMNoCG7-9J-GxhVrNQmK-PPFqRk04
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 609
ht-degree: 76%

---

# Dateiübertragung{#file-transfer}



Die Aktivität **Dateiübertragung** ermöglicht das Empfangen oder Senden von Dateien, das Testen auf das Vorhandensein von Dateien oder das Auflisten von Dateien auf einem Server. Als Protokoll wird entweder Azure Blob Storage, Amazon Simple Storage Service (S3), FTP oder SFTP verwendet.
Mit einer S3-, Azure Blob Storage- oder SFTP-Verbindung können Sie mit der Echtzeit-Kundendatenplattform von Adobe auch Segmentdaten in Adobe Campaign importieren. Weitere Informationen hierzu finden Sie in dieser [Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=de).

>[!NOTE]
>
>Best Practices und Problembehebung bei der Verwendung von SFTP-Servern finden Sie auf [dieser Seite](../../platform/using/sftp-server-usage.md).

## Eigenschaften {#properties}

Wählen Sie im Feld **[!UICONTROL Aktion]** die auszuführende Aktivität aus.

![](assets/file_transfert_action.png)

Die weitere Konfiguration hängt von der gewählten Aktion ab.

1. **Dateiempfang**

   Um auf einem Remote-Server gespeicherte Dateien zu empfangen, wählen Sie **[!UICONTROL Datei herunterladen]** im Feld **[!UICONTROL Aktion]** aus. Die URL muss im entsprechenden Feld angegeben werden.

   ![](assets/file_transfert_edit.png)

   Aktivieren Sie das Kontrollkästchen **[!UICONTROL Externes Konto verwenden]**, um ein Konto aus den Azure Blob Storage-, S3-, FTP- oder SFTP-Konten auszuwählen, die im Knoten **[!UICONTROL Administration > Plattform > Externe Konten]** des Navigationsbaums konfiguriert sind. Geben Sie danach an, welches Verzeichnis auf dem Server die Dateien enthält, die heruntergeladen werden sollen.

   ![](assets/file_transfert_edit_external.png)

1. **Dateiübertragung**

   Um eine Datei an einen Server zu senden, wählen Sie **[!UICONTROL Datei-Upload]** im Feld **[!UICONTROL Aktion]**. Sie müssen den Ziel-Server im Abschnitt **[!UICONTROL Remote-Server]** des Editors angeben. Die Parameter sind mit denen für eingehende Dateien identisch. Siehe oben.

   Die Quelldatei kann aus der vorherigen Aktivität stammen. In diesem Fall muss die Option **[!UICONTROL Durch vorhergehende Aktivität erzeugte Datei verwenden]** ausgewählt sein.

   ![](assets/file_transfert_edit_send.png)

   Dies kann sich auch auf eine oder mehrere andere Dateien beziehen. Um sie auszuwählen, deaktivieren Sie die Option und klicken Sie auf **[!UICONTROL Einfügen]**. Geben Sie den Zugriffspfad der zu sendenden Datei an. Um eine weitere Datei hinzuzufügen, klicken Sie erneut auf **[!UICONTROL Einfügen]**. Die Dateien haben nun alle ihre eigenen Registerkarten.

   ![](assets/file_transfert_source.png)

   Mit den Pfeilen können Sie die Reihenfolge der Registerkarten ändern. Dies bezieht sich auf die Reihenfolge, in der Dateien an den Server gesendet werden.

   Mit **[!UICONTROL Option „Verlauf der gesendeten Dateien]**&quot; können Sie die gesendeten Dateien verfolgen. Auf diesen Verlauf kann über das Verzeichnis zugegriffen werden.

1. **Existenztest einer Datei**

   Um das Vorhandensein einer Datei zu testen, wählen Sie die Option **[!UICONTROL Testen, um zu sehen, ob]** Datei vorhanden ist **[!UICONTROL im Feld Aktion]** aus. Die Konfiguration des Remote-Servers entspricht der Konfiguration für den Datei-Download. Weiterführende Informationen hierzu finden Sie in diesem [Abschnitt](#properties).

   ![](assets/file_transfert_edit_test.png)

1. **Dateiauflistung**

   Um die Dateien aufzulisten, wählen Sie die Option **[!UICONTROL Dateiauflistung]** aus dem Feld **[!UICONTROL Aktion]** aus. Die Konfiguration des Remote-Servers entspricht der für den Empfang von Dateien. Weiterführende Informationen hierzu finden Sie in diesem [Abschnitt](#properties).

   Die Option **[!UICONTROL Alle Dateien auflisten]**, die bei Auswahl der Aktion **[!UICONTROL Dateiauflistung]** erscheint, ermöglicht es, alle auf dem Server befindlichen Dateien in der Ereignisvariable **vars.filenames** zu erfassen. Die Dateinamen werden durch `\n`-Zeichen getrennt angegeben.

Zwei weitere Optionen stehen generell für die Dateiübertragung zur Verfügung:

* Die Option **[!UICONTROL Fehlen von Dateien bearbeiten]** erzeugt eine Transition, die aktiviert wird, wenn im angegebenen Verzeichnis keine Datei vorhanden ist.
* Die Option **[!UICONTROL Fehler verarbeiten]** wird im Abschnitt [Verarbeitungsfehler](monitoring-workflow-execution.md#processing-errors) erläutert.

Der Link **[!UICONTROL Erweiterte Parameter...]** bietet Zugriff auf folgende Optionen:

![](assets/file_transfert_advanced.png)

* **[!UICONTROL Quelldateien nach der Übertragung löschen]**

  Löscht die Dateien auf dem Remote-Server. Wenn Sie diese Option deaktiviert lassen, müssen Sie die Größe des archivierten Inhalts im SFTP-Verzeichnis manuell überwachen.

* **[!UICONTROL SSL verwenden]**

  Verwendet eine gesicherte Verbindung bei der Dateiübertragung (SSL-Protokoll).

* **[!UICONTROL Sitzungsprotokolle anzeigen]**

  Ruft die Logs zur Azure Blob Storage-, S3-, FTP- bzw. SFTP-Übertragung ab und fügt sie in die Workflow-Logs ein.

* **[!UICONTROL Passiven Modus deaktivieren]**

  Ermöglicht es, den für die Übertragung zu verwendenden Verbindungsport anzugeben.

Über den Link **[!UICONTROL Verlaufsparameter der Dateien...]** besteht Zugriff auf Optionen, die im Abschnitt [HTTP-Übertragung](web-download.md) (im Schritt **[!UICONTROL Verlaufserstellung]**) beschrieben werden.

## Eingabeparameter {#input-parameters}

* filename

  Vollständiger Name der übertragenen Datei.

## Ausgabeparameter {#output-parameters}

* filename

  Vollständiger Name der empfangenen Datei, wenn die Option **[!UICONTROL Durch vorhergehende Aktivität erzeugte Datei verwenden]** angekreuzt wurde.

---
title: Workflow-Daten verwenden
seo-title: Workflow-Daten verwenden
description: Workflow-Daten verwenden
seo-description: null
page-status-flag: never-activated
uuid: ed03f14b-1b53-426e-9213-22cb2f3deb19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: ec3844ca-8d80-4ddc-b08c-f18a6919bb28
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Workflow-Daten verwenden{#how-to-use-workflow-data}

## Datenbank aktualisieren {#updating-the-database}

Alle in Workflows erhobenen Daten können zur Aktualisierung der Datenbank oder in Sendungen verwendet werden, um beispielsweise die Möglichkeiten der Inhaltspersonalisierung zu ergänzen (Einfügung der Anzahl von Versicherungspolicen, des durchschnittlichen Warenkorbs im vergangenen Jahr etc.) oder die Zielgruppenbestimmung zu verfeinern (eine Nachricht an die Mitversicherten adressieren, die 1000 besten Kunden ansprechen etc.). Diese Daten können auch in eine Liste exportiert oder zur Erstellung eines Verlaufs verwendet werden.

### Listen und direkt Aktualisierungen {#lists-and-direct-updates}

Zur Aktualisierung der Adobe-Campaign-Datenbank und von Listen stehen zwei dedizierte Aktivitäten zur Verfügung:

* The **[!UICONTROL List update]** activity lets you store worktables in a datalist.

   Hierbei kann eine existierende Liste verwendet oder eine neue erstellt werden. In diesem Fall werden ihr Name und gegebenenfalls ihr Speicherverzeichnis berechnet.

   ![](assets/s_user_create_list.png)

   Siehe [Listen-Update](../../workflow/using/list-update.md).

* The **[!UICONTROL Update data]** activity performs a mass update of the fields in the database.

   For more on this, refer to [Update data](../../workflow/using/update-data.md).

### An- und Abmeldungen verwalten {#subscription-unsubscription-management}

To find out about subscribing and unsubscribing recipients to an information service via a workflow, refer to [Subscription Services](../../workflow/using/subscription-services.md).

## Über einen Workflow versenden {#sending-via-a-workflow}

### Versandaktivität {#delivery-activity}

The delivery activity is detailed in [Delivery](../../workflow/using/delivery.md).

### Sendungen anreichern und personalisieren {#enriching-and-targeting-deliveries}

Im Rahmen von Sendungen bieten Workflow-Aktivitäten die Möglichkeit, Daten zur Personalisierung des Inhalts oder zur Konfiguration der Versandzielgruppen bereitzustellen.

Beispielsweise können Sie bei Briefpost-Sendungen Zusatzdaten in die Extraktionsdatei aufnehmen, die mithilfe einer Workflow-Aktivität abgerufen werden:

![](assets/s_advuser_add_data_postal_mail.png)

Ergänzend zu den üblichen Personalisierungsfeldern können Sie den Versandinhalt mit aus einem Workflow stammenden Daten personalisieren. Tatsächlich können die aus Workflow-Aktivitäten gewonnenen Zusatzdaten gespeichert und im Versand-Assistenten verfügbar gemacht werden. Unten stehendes Beispiel verdeutlicht dies anhand des Namens der Ausgabedatei eines Briefpost-Versands:

![](assets/s_advuser_using_additional_data.png)

The data contained in the workflow table is identified by its name: it is always made up of the **targetData** link. For more on this, refer to [Target data](../../workflow/using/executing-a-workflow.md#target-data).

Auch im Rahmen eines E-Mail-Versands können Personalisierungsfelder auf Daten zugreifen, die im Zuge einer Erweiterung des Zieldatensatzes in einem Zielgruppen-Workflow erhoben wurden, wie die folgende Abbildung verdeutlicht:

![](assets/s_advuser_add_data_email.png)

Wenn ein Segmentcode in einer Targeting-Aktivität angegeben ist, wird er einer bestimmten Spalte der Workflow-Tabelle hinzugefügt und zusammen mit den Personalisierungsfeldern angeboten. Um alle Personalisierungsfelder anzuzeigen, klicken Sie auf den **[!UICONTROL Target extension > Other...]** Link, auf den Sie über die Personalisierungsschaltfläche zugreifen können.

![](assets/s_advuser_segment_code_select.png)

## Export von Daten {#exporting-data}

### Datei komprimieren oder verschlüsseln {#zipping-or-encrypting-a-file}

Mit Adobe Campaign können Sie komprimierte oder verschlüsselte Dateien exportieren. Beim Definieren eines Exports durch eine **[!UICONTROL Data extraction (file)]** Aktivität können Sie eine Nachbearbeitung definieren, um die Datei zu komprimieren oder zu verschlüsseln.

Gehen Sie dazu folgendermaßen vor:

* Wenn Ihre Adobe-Campaign-Installation von Adobe gehostet wird: Senden Sie eine Anfrage an [den Support](https://support.neolane.net), damit die nötigen Utilities auf dem Server installiert werden.
* Wenn Sie eine On-Premise-Installation von Adobe Campaign haben: Installieren Sie die gewünschte Utility (z. B.: GPG, GZIP) sowie die nötigen Schlüssel (zur Verschlüsselung) auf dem Anwendungsserver.

Danach können Sie Befehle oder Codes verwenden, wie zum Beispiel:

```
function encryptFile(file) {  
  var systemCommand = “gpg --encrypt --recipient  recipientToEncryptTo ” + file;  
  var result = execCommand(systemCommand, true); 
}
```

Beim Importieren einer Datei können Sie sie auch entpacken oder entschlüsseln. See [Unzipping or decrypting a file before processing](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing).

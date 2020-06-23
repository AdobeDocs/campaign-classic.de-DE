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
source-git-commit: bb35d2ae2d40aaef3bb381675d0c36ffb100b242
workflow-type: tm+mt
source-wordcount: '919'
ht-degree: 52%

---


# Workflow-Daten verwenden{#how-to-use-workflow-data}

## Datenbank aktualisieren {#updating-the-database}

Alle in Workflows erhobenen Daten können zur Aktualisierung der Datenbank oder in Sendungen verwendet werden, um beispielsweise die Möglichkeiten der Inhaltspersonalisierung zu ergänzen (Einfügung der Anzahl von Versicherungspolicen, des durchschnittlichen Warenkorbs im vergangenen Jahr etc.) oder die Zielgruppenbestimmung zu verfeinern (eine Nachricht an die Mitversicherten adressieren, die 1000 besten Kunden ansprechen etc.). Diese Daten können auch in eine Liste exportiert oder zur Erstellung eines Verlaufs verwendet werden.

### Listen und direkt Aktualisierungen {#lists-and-direct-updates}

Zur Aktualisierung der Adobe-Campaign-Datenbank und von Listen stehen zwei dedizierte Aktivitäten zur Verfügung:

* Über die Aktivität **[!UICONTROL Listen-Update]** können Arbeitstabellen in einer Datenliste gespeichert werden.

   Hierbei kann eine existierende Liste verwendet oder eine neue erstellt werden. In diesem Fall werden ihr Name und gegebenenfalls ihr Speicherverzeichnis berechnet.

   ![](assets/s_user_create_list.png)

   Siehe [Listen-Update](../../workflow/using/list-update.md).

* Die **[!UICONTROL Daten-Update]**-Aktivität ermöglicht eine gebündelte Aktualisierung von Datenbankfeldern.

   Weitere Informationen hierzu finden Sie im Abschnitt [Daten-Update](../../workflow/using/update-data.md).

### An- und Abmeldungen verwalten {#subscription-unsubscription-management}

Die An- und Abmeldung von Empfängern für einen Informationsdienst im Rahmen eines Workflows wird im Abschnitt ](../../workflow/using/subscription-services.md)An-/Abmeldedienst[ beschrieben.

## Über einen Workflow versenden {#sending-via-a-workflow}

### Versandaktivität {#delivery-activity}

Die Versandaktivität wird im Abschnitt ](../../workflow/using/delivery.md)Versand[ beschrieben.

### Sendungen anreichern und personalisieren {#enriching-and-targeting-deliveries}

Im Rahmen von Sendungen bieten Workflow-Aktivitäten die Möglichkeit, Daten zur Personalisierung des Inhalts oder zur Konfiguration der Versandzielgruppen bereitzustellen.

Beispielsweise können Sie bei Briefpost-Sendungen Zusatzdaten in die Extraktionsdatei aufnehmen, die mithilfe einer Workflow-Aktivität abgerufen werden:

![](assets/s_advuser_add_data_postal_mail.png)

Ergänzend zu den üblichen Personalisierungsfeldern können Sie den Versandinhalt mit aus einem Workflow stammenden Daten personalisieren. Tatsächlich können die aus Workflow-Aktivitäten gewonnenen Zusatzdaten gespeichert und im Versand-Assistenten verfügbar gemacht werden. Unten stehendes Beispiel verdeutlicht dies anhand des Namens der Ausgabedatei eines Briefpost-Versands:

![](assets/s_advuser_using_additional_data.png)

Aus Workflow-Arbeitstabellen stammende Daten sind über ihren Namen leicht identifizierbar. Er beginnt jeweils mit **targetData**. Weitere Informationen hierzu finden Sie im Abschnitt [Zielgruppendaten](../../workflow/using/data-life-cycle.md#target-data).

Auch im Rahmen eines E-Mail-Versands können Personalisierungsfelder auf Daten zugreifen, die im Zuge einer Erweiterung des Zieldatensatzes in einem Zielgruppen-Workflow erhoben wurden, wie die folgende Abbildung verdeutlicht:

![](assets/s_advuser_add_data_email.png)

Wenn in einer Aktivität zur Zielgruppenbestimmung ein Segment-Code angegeben wird, wird dieser in einer gesonderten Spalte der Workflow-Arbeitstabelle gespeichert und innerhalb der Personalisierungsfelder zur Verfügung gestellt. Klicken Sie zur Anzeige aller Personalisierungsfelder auf die entsprechende Schaltfläche im Versand und wählen Sie die Option **[!UICONTROL Erweiterung des Zieldatensatzes > Sonstige...]** aus.

![](assets/s_advuser_segment_code_select.png)

## Export von Daten {#exporting-data}

### Datei komprimieren oder verschlüsseln {#zipping-or-encrypting-a-file}

Mit Adobe Campaign können Sie komprimierte oder verschlüsselte Dateien exportieren. Wenn Sie einen Export über die Aktivität **[!UICONTROL Extraktion (Datei)]** planen, können Sie eine Nachbearbeitung definieren, um die Datei zu komprimieren oder zu verschlüsseln.

Gehen Sie dazu folgendermaßen vor:

1. Installieren Sie mithilfe der [Systemsteuerung](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data)ein GPG-Schlüsselpaar für Ihre Instanz.

   >[!NOTE]
   >
   >Systemsteuerung steht allen auf AWS gehosteten Kunden zur Verfügung (mit Ausnahme von Kunden, die ihre Marketinginstanzen auf einer lokalen Plattform hosten).

1. Wenn Ihre Installation von Adobe Campaign von Adobe gehostet wird, wenden Sie sich an den Adobe-Kundendienst, um die erforderlichen Hilfsprogramme auf dem Server installieren zu lassen.
1. Wenn die Installation des Adobe Campaigns vor Ort erfolgt, installieren Sie das Dienstprogramm, das Sie verwenden möchten (z. B.: GPG, GZIP) sowie die erforderlichen Schlüssel (Verschlüsselungsschlüssel) auf dem Anwendungsserver.

Sie können dann Befehle oder Code auf der Registerkarte &quot; **[!UICONTROL Skript]** &quot;der Aktivität oder in einer **[!UICONTROL JavaScript-Code]** -Aktivität verwenden. Im folgenden Anwendungsfall wird ein Beispiel vorgestellt.

**Verwandte Themen:**

* [Datei vor der Verarbeitung dekomprimieren oder entschlüsseln](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing)
* [Aktivität](../../workflow/using/extraction--file-.md)der Datendatei

### Verwendungsfall: Verschlüsseln und Exportieren von Daten mit einem in der Systemsteuerung installierten Schlüssel {#use-case-gpg-encrypt}

In diesem Fall erstellen wir einen Workflow, um Daten mithilfe eines in der Systemsteuerung installierten Schlüssels zu verschlüsseln und zu exportieren.

Die Schritte zum Ausführen dieses Anwendungsfalls lauten wie folgt:

1. Generieren Sie ein GPG-Schlüsselpaar (öffentlich/privat) mit einem GPG-Dienstprogramm und installieren Sie dann den öffentlichen Schlüssel in der Systemsteuerung. Ausführliche Anweisungen finden Sie in der Dokumentation zur [Systemsteuerung](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data).

1. Erstellen Sie in Campaign Classic einen Workflow, um die Daten zu exportieren und mit dem privaten Schlüssel zu exportieren, der über die Systemsteuerung installiert wurde. Dazu erstellen wir einen Workflow wie folgt:

   ![](assets/gpg-workflow-encrypt.png)

   * **[!UICONTROL Aktivität der Abfrage]** : In diesem Beispiel möchten wir eine Abfrage ausführen, um die Daten aus der Datenbank, die wir exportieren möchten, Zielgruppe.
   * **[!UICONTROL Extraktion (Datei)]** Aktivität: Extrahiert die Daten in eine Datei.
   * **[!UICONTROL JavaScript-Code]** -Aktivität: Verschlüsselt die zu extrahierenden Daten.
   * **[!UICONTROL Aktivität der Dateiübertragung]** : Sendet die Daten an eine externe Quelle (in diesem Beispiel an einen SFTP-Server).

1. Konfigurieren Sie die Aktivität der **[!UICONTROL Abfrage]** , um die gewünschten Daten aus der Datenbank Zielgruppe. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../workflow/using/query.md).

1. Öffnen Sie die Aktivität **[!UICONTROL Data Extraktion (file)]** und konfigurieren Sie sie dann entsprechend Ihren Anforderungen. Globale Konzepte zur Konfiguration der Aktivität finden Sie in [diesem Abschnitt](../../workflow/using/extraction--file-.md).

   ![](assets/gpg-data-extraction.png)

1. Öffnen Sie die **[!UICONTROL JavaScript-Code]** -Aktivität und kopieren Sie den unten stehenden Befehl, um die zu extrahierenden Daten zu verschlüsseln.

   >[!IMPORTANT]
   >
   >Stellen Sie sicher, dass Sie den **Fingerabdruckwert** des Befehls durch den Fingerabdruck des öffentlichen Schlüssels ersetzen, der in der Systemsteuerung installiert ist.

   ```
   var cmd='gpg ';
   cmd += ' --trust-model always';
   cmd += ' --batch -yes';
   cmd += ' --recipient fingerprint';
   cmd += ' --encrypt --output ' + vars.filename + '.gpg ' + vars.filename;
   execCommand(cmd,true);
   vars.filename=vars.filename + '.gpg'
   ```

   ![](assets/gpg-script.png)

1. Öffnen Sie die Aktivität **[!UICONTROL Dateiübertragung]** und geben Sie dann den SFTP-Server an, an den Sie die Datei senden möchten. Globale Konzepte zur Konfiguration der Aktivität finden Sie in [diesem Abschnitt](../../workflow/using/file-transfer.md).

   ![](assets/gpg-file-transfer.png)

1. Sie können den Workflow jetzt ausführen. Nach der Ausführung wird die Zielgruppe der Daten durch die Abfrage in eine verschlüsselte GPG-Datei exportiert.

   ![](assets/gpg-sftp-encrypt.png)

---
product: campaign
title: Datei komprimieren oder verschlüsseln
description: Erfahren Sie, wie Sie eine Datei in Campaign vor der Verarbeitung komprimieren oder verschlüsseln
feature: Data Management
badge-v7: label="v7" type="Informative" tooltip="Gilt für Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 4596638c-d75a-4e07-a2d8-5befcaad3430
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 98%

---

# Komprimieren oder Verschlüsseln von Dateien {#zipping-or-encrypting-a-file}



Mit Adobe Campaign können Sie komprimierte oder verschlüsselte Dateien exportieren. Wenn Sie einen Export über die Aktivität **[!UICONTROL Extraktion (Datei)]** planen, können Sie eine Nachbearbeitung definieren, um die Datei zu komprimieren oder zu verschlüsseln.

Gehen Sie dazu folgendermaßen vor:

1. Installieren Sie mit dem [Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html?lang=de#encrypting-data) ein GPG-Schlüsselpaar für Ihre Instanz.

   >[!NOTE]
   >
   >Das Control Panel ist auf Administratoren beschränkt und nur für bestimmte Campaign-Versionen verfügbar. [Mehr dazu](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=de)
   >

1. Wenn Ihre Adobe Campaign-Installation von Adobe gehostet wird, wenden Sie sich an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html), damit die nötigen öffentlichen Dienste auf dem Server installiert werden.
1. Wenn Sie eine On-Premise-Installation von Adobe Campaign haben, installieren Sie den gewünschten öffentlichen Dienst (z. B.: GPG, GZIP) sowie die nötigen Schlüssel (zur Verschlüsselung) auf dem Anwendungs-Server.

Sie können dann auf der Registerkarte **[!UICONTROL Script]** der Aktivität oder in einer **[!UICONTROL JavaScript-Code]**-Aktivität Befehle bzw. Code verwenden. Im folgenden Anwendungsfall wird ein Beispiel dargestellt.

**Verwandte Themen:**

* [Entpacken oder Entschlüsseln von Dateien vor der Verarbeitung](../../platform/using/unzip-decrypt.md)
* [Aktivität &quot;Extraktion (Datei)&quot;](../../workflow/using/extraction--file-.md).

## Anwendungsfall: Verschlüsseln und Exportieren von Daten mit einem im Control Panel installierten Schlüssel {#use-case-gpg-encrypt}

In diesem Anwendungsfall wird ein Workflow erstellt, um Daten mit einem im Control Panel installierten Schlüssel zu verschlüsseln und zu exportieren.

![](assets/do-not-localize/how-to-video.png) [Entdecken Sie diese Funktion im Video](#video).

Die Schritte zum Ausführen dieses Anwendungsfalls lauten wie folgt:

1. Generieren Sie ein GPG-Schlüsselpaar (öffentlich/privat) mit einem GPG-Dienstprogramm und installieren Sie dann den öffentlichen Schlüssel im Control Panel. Ausführliche Anweisungen finden Sie in der [Control Panel-Dokumentation](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html?lang=de#encrypting-data).

1. Erstellen Sie einen Workflow in Campaign Classic, um die Daten zu exportieren und mithilfe des über das Control Panel installierten privaten Schlüssels zu verschlüsseln. Zu diesem Zweck wird folgender Workflow erstellt:

   ![](assets/gpg-workflow-encrypt.png)

   * Aktivität **[!UICONTROL Abfrage]**: In diesem Beispiel möchten wir eine Abfrage ausführen, die auf die Daten aus der Datenbank abzielt, die wir exportieren möchten.
   * Aktivität **[!UICONTROL Extraktion (Datei)]**: Extrahiert die Daten in eine Datei.
   * Aktivität **[!UICONTROL JavaScript-Code]**: Verschlüsselt die zu extrahierenden Daten.
   * Aktivität **[!UICONTROL Dateiübertragung]**: Sendet die Daten an eine externe Quelle (in diesem Beispiel an einen SFTP-Server).

1. Konfigurieren Sie die Aktivität **[!UICONTROL Abfrage]** so, dass sie auf die gewünschten Daten aus der Datenbank abzielt. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../workflow/using/query.md).

1. Öffnen Sie die Aktivität **[!UICONTROL Extraktion (Datei)]** und konfigurieren Sie sie entsprechend Ihren Anforderungen. Globale Konzepte zur Konfiguration der Aktivität finden Sie in [diesem Abschnitt](../../workflow/using/extraction--file-.md).

   ![](assets/gpg-data-extraction.png)

1. Öffnen Sie die Aktivität **[!UICONTROL JavaScript-Code]** und fügen Sie den unten stehenden Befehl ein, um die zu extrahierenden Daten zu verschlüsseln.

   >[!IMPORTANT]
   >
   >Vergessen Sie nicht, den Wert **fingerprint** im Befehl durch den Fingerabdruck des öffentlichen, im Control Panel installierten Schlüssels zu ersetzen.

   ```
   var cmd='gpg ';
   cmd += ' --trust-model always';
   cmd += ' --batch --yes';
   cmd += ' --recipient fingerprint';
   cmd += ' --encrypt --output ' + vars.filename + '.gpg ' + vars.filename;
   execCommand(cmd,true);
   vars.filename=vars.filename + '.gpg'
   ```

   ![](assets/gpg-script.png)

1. Öffnen Sie die Aktivität **[!UICONTROL Dateiübertragung]** und geben Sie dann den SFTP-Server an, an den Sie die Datei senden möchten. Globale Konzepte zur Konfiguration der Aktivität finden Sie in [diesem Abschnitt](../../workflow/using/file-transfer.md).

   ![](assets/gpg-file-transfer.png)

1. Sie können den Workflow jetzt ausführen. Nach der Ausführung werden die über die Abfrage abgerufenen Daten in eine verschlüsselte .gpg-Datei für den SFTP-Server exportiert.

## Anleitungsvideo {#video}

In diesem Video wird gezeigt, wie Daten mit einem GPG-Schlüssel verschlüsselt werden können.

>[!VIDEO](https://video.tv.adobe.com/v/36399?quality=12)

Weitere Anleitungsvideos zu Campaign Classic finden Sie [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=de).

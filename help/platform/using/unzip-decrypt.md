---
product: campaign
title: Dekomprimieren oder Entschlüsseln einer Datei
description: Erfahren Sie, wie Sie eine Datei in Campaign vor der Verarbeitung dekomprimieren oder entschlüsseln
feature: Workflows, Encryption
badge-v7: label="v7" type="Informative" tooltip="Gilt für Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 1a79da3b-2abc-4bfc-a0ee-8471c478638d
source-git-commit: a2106e55617209f28da42c50008d16188563b2da
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 100%

---


# Entpacken oder Entschlüsseln von Dateien {#unzipping-or-decrypting-a-file-before-processing}

Mit Adobe Campaign können Sie komprimierte oder verschlüsselte Dateien importieren. Damit diese in der Aktivität [Daten laden (Datei)](../../workflow/using/data-loading--file-.md) gelesen werden können, definieren Sie eine Vorab-Bearbeitung, um die Datei zu dekomprimieren oder zu entschlüsseln.

>[!IMPORTANT]
>
>Sie können keine komprimierte Dateien entpacken, die größer als 4 GB sind.

Gehen Sie dazu folgendermaßen vor:

1. Verwenden Sie das [Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html?lang=de#decrypting-data), um für die Entschlüsselung von Dateien ein Schlüsselpaar aus öffentlichem/privatem Schlüssel zu generieren.

   >[!NOTE]
   >
   >Das Control Panel steht allen Administratoren zur Verfügung. Die Schritte, um einem Benutzer Administratorzugriff zu gewähren, finden Sie auf [dieser Seite](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=de#discover-control-panel).
   >
   >Beachten Sie, dass Ihre Instanz auf AWS gehostet und mit dem [neuesten GA-Build](../../rn/using/rn-overview.md) aktualisiert werden muss. Erfahren Sie in [diesem Abschnitt](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version), wie Sie Ihre Version überprüfen. Um zu überprüfen, ob Ihre Instanz auf AWS gehostet wird, folgen Sie den Schritten auf [dieser Seite](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=de).

1. Wenn Sie eine On-Premise-Installation von Adobe Campaign haben, installieren Sie den gewünschten öffentlichen Dienst (z. B.: GPG, GZIP) sowie die nötigen Schlüssel (Verschlüsselungsschlüssel) auf dem Anwendungs-Server.

   Wenn Ihre Adobe Campaign-Installation von Adobe gehostet wird, wenden Sie sich an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html), damit die nötigen Dienstprogramme auf dem Server installiert werden.

Anschließend können Sie die gewünschten Vorab-Bearbeitungsbefehle in Ihren Workflows nutzen:

1. Fügen Sie in Ihrem Workflow die Aktivität **[!UICONTROL Dateiübertragung]** hinzu und konfigurieren Sie sie.
1. Fügen Sie die Aktivität **[!UICONTROL Laden (Datei)]** hinzu und definieren Sie das Dateiformat.
1. Aktivieren Sie die Option **[!UICONTROL Vorab-Bearbeitung der Datei vorsehen]**.
1. Geben Sie den Vorab-Bearbeitungsbefehl an, den Sie anwenden möchten.
1. Fügen Sie andere Aktivitäten zur Handhabung der Daten in der Datei hinzu.
1. Speichern und starten Sie Ihren Workflow.

Im folgenden Anwendungsfall wird ein Beispiel dargestellt.

**Verwandte Themen:**

* [Aktivität &quot;Laden (Datei)&quot;](../../workflow/using/data-loading--file-.md).
* [Komprimieren oder Verschlüsseln von Dateien](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file).

## Anwendungsfall: Importieren von Daten, die mit einem vom Control Panel generierten Schlüssel verschlüsselt wurden {#use-case-gpg-decrypt}

In diesem Anwendungsfall erstellen wir einen Workflow, um Daten, die in einem externen System verschlüsselt wurden, mithilfe eines im Control Panel generierten Schlüssels zu importieren.

![](assets/do-not-localize/how-to-video.png) [Funktion im Video kennenlernen](#video).

Die Schritte zum Ausführen dieses Anwendungsfalls lauten wie folgt:

1. Verwenden Sie das Control Panel, um ein Schlüsselpaar (öffentlich/privat) zu generieren. Ausführliche Anweisungen finden Sie in der [Control Panel-Dokumentation](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html?lang=de#decrypting-data).

   * Der öffentliche Schlüssel wird mit dem externen System geteilt, das ihn zum Verschlüsseln der an Campaign zu sendenden Daten verwendet.
   * Der private Schlüssel wird von Campaign Classic verwendet, um die eingehenden verschlüsselten Daten zu entschlüsseln.

   ![](assets/gpg_generate.png)

1. Verwenden Sie im externen System den vom Control Panel heruntergeladenen öffentlichen Schlüssel, um die Daten für den Import in Campaign Classic zu verschlüsseln.

1. Erstellen Sie einen Workflow in Campaign Classic, um die verschlüsselten Daten zu importieren und mithilfe des über das Control Panel installierten privaten Schlüssels zu entschlüsseln. Zu diesem Zweck wird folgender Workflow erstellt:

   ![](assets/gpg_import_workflow.png)

   * Aktivität **[!UICONTROL Dateiübertragung]**: Überträgt die Datei von einer externen Quelle an Campaign Classic. In diesem Beispiel soll die Datei von einem SFTP-Server übertragen werden.
   * Aktivität **[!UICONTROL Laden (Datei)]**: Lädt die Daten aus der Datei in die Datenbank und entschlüsselt sie mithilfe des im Control Panel generierten privaten Schlüssels.

1. Öffnen Sie die Aktivität **[!UICONTROL Dateiübertragung]** und geben Sie das externe Konto an, aus dem Sie die verschlüsselte GPG-Datei importieren möchten.

   ![](assets/gpg_key_transfer.png)

   Globale Konzepte zur Konfiguration der Aktivität finden Sie in [diesem Abschnitt](../../workflow/using/file-transfer.md).

1. Öffnen Sie die Aktivität **[!UICONTROL Laden (Datei)]** und konfigurieren Sie sie entsprechend Ihren Anforderungen. Globale Konzepte zur Konfiguration der Aktivität finden Sie in [diesem Abschnitt](../../workflow/using/data-loading--file-.md).

   Fügen Sie der Aktivität eine Vorab-Bearbeitungsetappe hinzu, um die eingehenden Daten zu entschlüsseln. Wählen Sie dazu die Option **[!UICONTROL Vorab-Bearbeitung der Datei vorsehen]** und kopieren Sie den folgenden Entschlüsselungsbefehl in das Feld **[!UICONTROL Befehl]**:

   `gpg --batch --passphrase passphrase --decrypt <%=vars.filename%>`

   ![](assets/gpg_load.png)

   >[!CAUTION]
   >
   >In diesem Beispiel verwenden wir die Passphrase, die das Control Panel standardmäßig nutzt, nämlich &quot;passphrase&quot;.
   >
   >Wenn per Anfrage an die Kundenunterstützung bereits in der Vergangenheit GPG-Schlüssel in Ihrer Instanz installiert wurden, hat sich die Passphrase möglicherweise geändert und unterscheidet sich von der standardmäßigen Passphrase.

1. Wählen Sie **[!UICONTROL OK]** aus, um die Konfiguration der Aktivität zu bestätigen.

1. Sie können den Workflow jetzt ausführen. Nach der Ausführung können Sie in den Workflow-Logs prüfen, ob die Entschlüsselung ausgeführt wurde und Daten aus der Datei importiert wurden.

   ![](assets/gpg_run.png)

## Anleitungsvideo {#video}

In diesem Video wird gezeigt, wie Daten mithilfe eines GPG-Schlüssels entschlüsselt werden.

>[!VIDEO](https://video.tv.adobe.com/v/36482?quality=12)

Weitere Anleitungsvideos zu Campaign Classic finden Sie [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=de).

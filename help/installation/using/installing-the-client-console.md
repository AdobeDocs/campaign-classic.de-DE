---
solution: Campaign Classic
product: campaign
title: Installieren der Client-Konsole
description: Erfahren Sie, wie Sie die Client-Konsole installieren
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: c96a7faf5c65848a3f383a5721bfa45048ecea57
workflow-type: tm+mt
source-wordcount: '962'
ht-degree: 7%

---


# Installieren und Aktualisieren der Client-Konsole der Kampagne{#installing-the-client-console}


Kampagne Client Console ist ein Rich-Client, mit dem Sie eine Verbindung zu den Anwendungsservern Ihrer Kampagne herstellen können.

Bevor Sie beginnen, müssen Sie die Kampagne [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html) überprüfen, um Ihre Kampagnen-Server-URL und Ihre Benutzeranmeldeinformationen abzurufen.

>[!CAUTION]
>
>Kampagne Client-Konsole und Anwendungsserver der Kampagne müssen mit derselben Produktversion ausgeführt werden. Adobe empfiehlt auch, denselben Produktaufbau zu verwenden.

![](assets/do-not-localize/how-to-video.png) Erfahren Sie, wie Sie den Adobe Campaign-Client in  [Video installieren und einrichten](#video)

Die Installation oder Aktualisierung der Client-Konsole hängt von der Implementierung von Adobe Campaign Classic ab.
Bitte lesen Sie die unten stehenden Details, um zu verstehen, was für Ihre Implementierung erforderlich ist.


## Von Adoben gehostete Implementierungen {#hosted-customers}

So installieren oder aktualisieren Sie Ihre Client-Konsole(n):

1. Adobe kann direkt bereitgestellt werden. Nach der Aktualisierung der Konsole werden Benutzer aufgefordert, die neueste Version der Client-Konsole in einem Popup-Fenster herunterzuladen.

1. Sie können von [Software-Distribution](https://experience.adobe.com/#/downloads/content/software-distributsion/de/campaign.html) auf Ihre Client-Konsole(n) herunterladen

   **Benutzer benötigen Administratorzugriff, um die Aktualisierung abzuschließen. Wenn die Benutzer keine Administratorrechte haben, muss ein Systemadministrator auf allen Client-Konsolen bereitstellen**



## Hybrid- und Voll-On-Premise-Implementierungen {#hybrid-onprem-customers}

Damit Adobe Campaign-Benutzer sich bei der von Ihnen erstellten und konfigurierten Instanz anmelden können, müssen sie die Client-Konsole verwenden.

### Bereitstellen der Konsole für Benutzer {#make-console-available}

Wenn der zum Beginn eines Adobe Campaign-Anwendungsservers verwendete Computer (nlserver-Web) Benutzerverbindungen von der Client-Konsole erhält, können Sie ihn so konfigurieren, dass das Setup-Programm für den Rich-Client des Adobe Campaigns über eine HTML-Schnittstelle verfügbar gemacht wird. Sobald eine neue Version der Client-Konsole verfügbar ist, werden Benutzer eingeladen, sie beim Starten ihrer Client-Konsole herunterzuladen.

Dazu müssen Sie:

1. Wählen Sie das Paket aus, das das Programm für die Konsoleninstallation enthält.

   Diese Datei heißt setup-client-7.X.XXXX.exe für v7 oder setup-client-6.X.XXXX.exe für v6.1, wobei X die Unterversion von Adobe Campaign und XXXX der Build ist   Nummer.

1. Kopieren Sie dieses Adobe Campaign und fügen Sie es in den Installationsordner (auf dem Marketing-Server für Hybridinstallationen) unter /datakit/nl/eng/jsp ein.

1. Beginn Adobe Campaign-Server.

>[!CAUTION]
>
>  Adobe empfiehlt, die Option **[!UICONTROL Diese Frage]** nicht mehr auszuwählen, um sicherzustellen, dass alle Benutzer benachrichtigt werden, wenn eine neue Konsolenversion verfügbar ist.  Wenn diese Option aktiviert ist, wird der Benutzer nicht über neue verfügbare Versionen informiert.

Wenn **[!UICONTROL Diese Frage nicht mehr stellen]** ausgewählt wurde, können Sie diese Aufforderung zurücksetzen. Die folgenden Änderungen sollten nur Systemadministratoren vornehmen, die mit der Bearbeitung der Windows-Registrierung vertraut sind:

1. Öffnen Sie den Registrierungs-Editor mit dem Befehl **regedit** aus dem Menü **[!UICONTROL Beginn > Ausführen]**.

1. Suchen Sie nach dem Knoten und erweitern Sie ihn.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Löschen Sie den Eintrag **confAdvisedUpgrade** und schließen Sie den Registrierungs-Editor.

>[!NOTE]
>
>Wenn Sie eine aktualisierte Konsole auf eine vorhandene Implementierung anwenden, erhalten die Benutzer automatisch eine Aufforderung, ihre Client-Konsole zu aktualisieren. Wenn Sie die Kampagne zum ersten Mal implementieren, müssen die Benutzer die Konsole herunterladen. Details zu beiden Optionen finden Sie unten

### Konsole aktualisieren - vorhandene Implementierung{#update-the-client-console}

Sobald die Konsole im Serverordner der Kampagne verfügbar ist, werden die Benutzer aufgefordert, die neueste Clientkonsole in einem Popup-Fenster herunterzuladen.

**Benutzer benötigen Administratorzugriff, um die Aktualisierung abzuschließen. Wenn die Benutzer keine Administratorrechte haben, muss ein Systemadministrator auf allen Client-Konsolen bereitstellen**


### Konsole herunterladen - neue Implementierung{#download-the-client-console}

Die Benutzer sollten nun die Konsole herunterladen und installieren, indem sie die folgenden Schritte ausführen:

1. Öffnen Sie einen Webbrowser und laden Sie die Konsole von der folgenden Adresse herunter:

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://myserver.adobe.com/nl/jsp/logon.jsp).

1. Geben Sie im Identifizierungsfenster Ihren Benutzernamen und Ihr Kennwort ein.

   ![](assets/s_ncs_install_setup_download01.png)

   Verwenden Sie bei Bedarf die Anmeldeinformationen des beim Erstellen der Instanz definierten internen Kontos.

1. Klicken Sie auf der Installationsseite auf den Link **[!UICONTROL Download]**.
1. Laden Sie die Client-Setupdatei herunter und speichern Sie sie.
1. Führen Sie die heruntergeladene Datei auf einem Computer unter Windows aus: Die Installation wird Beginn. Der Standardinstallationspfad der Client-Konsole ist **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, wobei &quot;X&quot;entsprechend Ihrer Adobe Campaign-Version &quot;6&quot;oder &quot;7&quot;ist.

### Verbindung erstellen - erste Benutzer nur{#create-the-connection}

Nachdem die Client-Konsole installiert wurde, führen Sie die folgenden Schritte aus, um die Verbindung zum Anwendungsserver herzustellen:

1. Beginn Sie die Konsole aus dem Menü Windows **[!UICONTROL Beginn]** in der Gruppe **Adobe Campaign** Programm.

1. Klicken Sie auf den Link in der oberen rechten Ecke der Felder mit den Anmeldeinformationen, um das Fenster für die Verbindungskonfiguration aufzurufen.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klicken Sie auf **[!UICONTROL Hinzufügen > Verbindung]** und geben Sie die Bezeichnung und URL des Adobe Campaign-Anwendungsservers ein.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Geben Sie über eine URL eine Verbindung zum Adobe Campaign-Anwendungsserver an. Verwenden Sie entweder ein DNS oder einen Alias des Computers oder Ihre IP-Adresse.

   Sie können beispielsweise die URL [`https://<machine>.<domain>.com`](https://myserver.adobe.com) eingeben.

1. Wenn Adobe-IMS für Ihr Unternehmen konfiguriert ist, aktivieren Sie die Option **[!UICONTROL Verbindung mit einem Adobe ID]**

1. Klicken Sie auf **[!UICONTROL OK]**, um Ihre Einstellungen zu speichern.

Sie können z. B. so viele Verbindungen wie erforderlich hinzufügen, um eine Verbindung zu Ihren Test-, Stage- und Produktionsfunktionen herzustellen.

>[!NOTE]
>
>Die Schaltfläche **[!UICONTROL Hinzufügen]** erlaubt die Erstellung von **[!UICONTROL Ordnern]**, in die Sie Ihre verschiedenen Verbindungen per Drag&amp;Drop verschieben können.

### Bei Adobe Campaign anmelden

Gehen Sie wie folgt vor, um sich bei einer vorhandenen Instanz anzumelden:

1. Beginn Sie die Konsole aus dem Menü Windows **[!UICONTROL Beginn]** in der Gruppe **Adobe Campaign** Programm.

1. Klicken Sie auf den Link in der oberen rechten Ecke der Felder mit den Anmeldeinformationen, um das Fenster für die Verbindungskonfiguration aufzurufen.

1. Wählen Sie die Kampagne aus, bei der Sie sich anmelden müssen.

1. Bestätigen Sie die Aktion mit der Schaltfläche **[!UICONTROL OK]**

1. Geben Sie Ihre Anmeldedaten für den Benutzer ein und klicken Sie auf **[!UICONTROL Anmelden]**



**Verwandte Themen**

* [Erstellen einer Instanz und Anmelden](../../installation/using/creating-an-instance-and-logging-on.md).
* [Kompatibilitätsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

## Tutorial

In diesem Video wird gezeigt, wie der Adobe Campaign-Client installiert und eingerichtet wird.

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

Weitere Anleitungsvideos zu Campaign Classic finden Sie [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=de).

---
product: campaign
title: Client-Konsole installieren
description: Informationen zur Installation der Client-Konsole
feature: Installation, Upgrade
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 7cc78214-92b8-4b1f-a307-96ec6af818d1
source-git-commit: a38d53f4b37aadbc53446b5e399af2eae56c12af
workflow-type: tm+mt
source-wordcount: '1152'
ht-degree: 31%

---

# Installieren und Aktualisieren der Campaign-Client-Konsole{#installing-the-client-console}

Die Client-Konsole in Campaign ist ein Rich-Client, mit dem Sie eine Verbindung zu Ihren Campaign-Anwendungs-Servern herstellen können.

Bevor Sie mit der Installation der Client-Konsole beginnen, müssen Sie:

* Überprüfen Sie die Kompatibilität Ihres Systems und Ihrer Tools mit Adobe Campaign in der [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)
* Ermitteln Sie Ihre Campaign-Server-URL
* Ermitteln Sie Ihre Anwender-Anmeldedaten
* Microsoft Edge Webview2 Runtime auf Ihrem System installieren (ab Campaign Classic 7.3 Build-Version). [Weitere Informationen](#webview)

Der Prozess zum Installieren oder Aktualisieren der Client-Konsole hängt von der Implementierung der Adobe Campaign Classic ab.
Bitte überprüfen Sie die folgenden Details, um zu verstehen, was für Ihre Implementierung erforderlich ist.

![](assets/do-not-localize/how-to-video.png) Erfahren Sie im [, wie Sie den Adobe Campaign-Client installieren und einrichten](#video)

>[!CAUTION]
>
>* Die Campaign-Client-Konsole und der Campaign-Anwendungs **Server müssen auf derselben Produktversion ausgeführt**. Adobe empfiehlt außerdem dringend die Verwendung **desselben Produkt-Builds**. In diesem Abschnitt erfahren Sie, wie Sie Ihre Campaign-Client- und -Server[Versionen ](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).
>
>* Der Zugriff auf den Installationsordner, in dem die Konsole installiert wird, sollte auf den vorgesehenen Benutzer beschränkt sein, sodass Schreibberechtigungen entsprechend eingeschränkt werden.



## Installation der Microsoft Edge Webview2-Laufzeitumgebung {#webview}

Ab der Build-Version 7.3 von Campaign Classic ist die Installation der Microsoft Edge Webview 2-Laufzeitumgebung für jede Konsolen-Installation erforderlich.

WebView wird standardmäßig als Teil des Betriebssystems Windows 11 installiert. Wenn es nicht bereits auf Ihrem System vorhanden ist, werden Sie vom Installationsprogramm der Campaign Classic-Konsole aufgefordert, es von der [Microsoft Developer Website herunterzuladen](https://www.adobe.com/go/acc-ms-webview2-runtime-download_de). Beachten Sie, dass der Download-Link nicht mit Internet Explorer 11 funktioniert, da Microsoft die Unterstützung dieses Browsers eingestellt hat. Stellen Sie sicher, dass Sie einen anderen Browser verwenden, um auf den Link zuzugreifen.

## Gehostete Adobe-Implementierungen {#hosted-customers}

Als gehosteter Kunde haben Sie zwei Möglichkeiten, Ihre Client-Konsole(en) zu installieren oder zu aktualisieren:

1. Adobe kann direkt bereitgestellt werden. Sobald die Konsole aktualisiert wurde, werden Benutzer in einem Popup-Fenster aufgefordert, die neueste Version der Client-Konsole herunterzuladen.

1. Sie können von „Software Distribution“ auf [ Client-Konsole(en) ](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html)

   **Benutzende benötigen Administratorzugriff, um die Aktualisierung abzuschließen. Wenn die Benutzer keine Administratorrechte haben, muss ein Systemadministrator eine Bereitstellung für alle Client-Konsolen durchführen**

## Hybrid- und On-Premise-Implementierungen {#hybrid-onprem-customers}

Damit sich Adobe Campaign-Benutzende bei der von Ihnen erstellten und konfigurierten Instanz anmelden können, müssen sie die Client-Konsole verwenden.

### Konsole für Benutzer verfügbar machen {#make-console-available}

Wenn der Computer, der zum Starten eines Adobe Campaign-Anwendungsservers (nlserver web) verwendet wird, Benutzerverbindungen von der Client-Konsole erhält, können Sie ihn so konfigurieren, dass das Installationsprogramm für den Adobe Campaign Rich-Client über eine HTML-Schnittstelle verfügbar gemacht wird. Wenn eine neue Version der Client-Konsole verfügbar ist, werden Benutzer beim Starten ihrer Client-Konsole aufgefordert, diese herunterzuladen.

Gehen Sie dazu folgendermaßen vor:

1. Wählen Sie das Paket aus, das das Konsolen-Installationsprogramm enthält.

   Diese Datei heißt setup-client-7.X.XXXX.exe, wobei X die Unterversion von Adobe Campaign und XXXX die Build-Nummer ist.

1. Kopieren Sie dieses Paket und fügen Sie es in den Adobe Campaign-Installationsordner (auf dem Marketing-Server für Hybridinstallationen) unter /datakit/nl/eng/jsp ein.

1. Starten Sie den Adobe Campaign-Server.


### Diese Option nicht mehr stellen

Adobe empfiehlt, die Option **[!UICONTROL Diese Frage nicht mehr stellen]** deaktiviert zu lassen, um sicherzustellen, dass alle Benutzenden benachrichtigt werden, wenn eine neue Konsolenversion verfügbar ist.  Wenn diese Option aktiviert ist, wird der Anwender nicht über neue verfügbare Versionen informiert.

Wenn **[!UICONTROL Diese Frage nicht mehr stellen]** ausgewählt wurde, können Sie diese Eingabeaufforderung zurücksetzen. Diese Änderungen sollten nur von Systemadministratoren vorgenommen werden, die mit der Bearbeitung der Windows-Registrierung vertraut sind:

1. Öffnen Sie den Registrierungs-Editor mit dem Befehl **regedit** im Menü **[!UICONTROL Start > Ausführen]**.

1. Suchen Sie nach dem Knoten und erweitern Sie ihn.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Löschen Sie den **confAdvisedUpgrade**-Eintrag und schließen Sie den Registrierungs-Editor.

>[!NOTE]
>
>Wenn Sie eine aktualisierte Konsole auf eine vorhandene Implementierung anwenden, erhalten die Benutzer automatisch eine Aufforderung zur Aktualisierung ihrer Client-Konsole. Wenn Sie Campaign zum ersten Mal implementieren, müssen Benutzerinnen und Benutzer die Konsole herunterladen. Einzelheiten zu beiden Optionen finden Sie unten

### Aktualisieren der Konsole für die vorhandene Implementierung{#update-the-client-console}

Sobald die Konsole im Ordner des Campaign-Servers verfügbar ist, werden Benutzer in einem Popup-Fenster aufgefordert, die neueste Version der Client-Konsole herunterzuladen.

**Benutzende benötigen Administratorzugriff, um die Aktualisierung abzuschließen. Wenn die Benutzer keine Administratorrechte haben, muss ein Systemadministrator eine Bereitstellung für alle Client-Konsolen durchführen**


### Herunterladen der Konsole für eine neue Implementierung{#download-the-client-console}

Benutzer sollten jetzt die Konsole herunterladen und installieren, indem sie die folgenden Schritte ausführen:

1. Öffnen Sie einen Webbrowser und laden Sie die Konsole von der folgenden Adresse herunter:

   `https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`.

1. Geben Sie im Identifikationsfenster Ihren Login und Ihr Passwort ein.

   ![](assets/s_ncs_install_setup_download01.png)

   Verwenden Sie bei Bedarf die Anmeldeinformationen des internen Kontos, die bei der Instanzerstellung definiert wurden.

1. Klicken Sie auf der **[!UICONTROL auf]** Link „Herunterladen“.
1. Laden Sie die Client-Setup-Datei herunter und speichern Sie sie.
1. Führen Sie die heruntergeladene Datei auf einem Computer unter Windows aus: Die Installation wird gestartet. Der Standardinstallationspfad der Client-Konsole lautet **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, wobei „X“ je nach Adobe Campaign-Version „6“ oder „7“ ist.

### Verbindung erstellen - nur erstmalige Benutzer{#create-the-connection}

Sobald die Client-Konsole installiert ist, führen Sie die folgenden Schritte aus, um die Verbindung zum Anwendungs-Server herzustellen:

1. Starten Sie die Konsole über das Windows **[!UICONTROL Start]**-Menü in der **Adobe Campaign**-Programmgruppe.

1. Klicken Sie in der oberen rechten Ecke der Felder mit den Anmeldedaten auf den Link, um das Fenster für die Verbindungskonfiguration aufzurufen.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klicken Sie auf **[!UICONTROL Hinzufügen > Verbindung]** und geben Sie die Bezeichnung und URL des Adobe Campaign-Anwendungs-Servers ein.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Geben Sie per URL eine Verbindung zum Adobe Campaign-Anwendungs-Server an. Verwenden Sie entweder einen DNS oder einen Alias des Computers oder Ihre IP-Adresse.

   Sie können beispielsweise eine URL vom Typ `https://<machine>.<domain>.com` eingeben.

1. Wenn Adobe IMS für Ihr Unternehmen konfiguriert ist, aktivieren Sie die Option **[!UICONTROL Verbindung mit einer Adobe ID herstellen]**

1. Klicken Sie auf **[!UICONTROL OK]**, um Ihre Einstellungen zu speichern.

Sie können so viele Verbindungen wie erforderlich hinzufügen, um z. B. Verbindungen zu Ihren Test-, Staging- und Produktionsumgebungen herzustellen.

>[!NOTE]
>
>Die Schaltfläche **[!UICONTROL Hinzufügen]** erlaubt die Erstellung von **[!UICONTROL Ordnern]**, in die Sie Ihre verschiedenen Verbindungen per Drag-and-Drop verschieben können.

### Bei Adobe Campaign anmelden

Gehen Sie wie folgt vor, um sich bei einer vorhandenen Instanz anzumelden:

1. Starten Sie die Konsole über das Windows **[!UICONTROL Start]**-Menü in der **Adobe Campaign**-Programmgruppe.

1. Klicken Sie in der oberen rechten Ecke der Felder mit den Anmeldedaten auf den Link, um das Fenster für die Verbindungskonfiguration aufzurufen.

1. Wählen Sie die Campaign-Instanz aus, bei der Sie sich anmelden möchten.

1. Klicken Sie auf **[!UICONTROL OK]**

1. Geben Sie Ihre Benutzer-Anmeldedaten ein und klicken Sie auf **[!UICONTROL Anmelden]**

>[!NOTE]
>
>Bei den Build-Versionen 7.3 von Campaign Classic kann es vorkommen, dass die Adobe Campaign-Client-Konsole während der Proxy-Authentifizierung zweimal nach den Proxy-Anmeldedaten fragt. Dies liegt daran, dass Microsoft Edge WebView2 im Gegensatz zum Internet Explorer keine Proxy-Anmeldedaten im Cache/Kennwortspeicher speichert.

**Verwandte Themen** 

* [Instanz erstellen und anmelden](../../installation/using/creating-an-instance-and-logging-on.md).
* [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html)

## Anleitungsvideo

In diesem Video wird gezeigt, wie Sie den Adobe Campaign-Client installieren und einrichten.

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

Weitere Anleitungsvideos zu Campaign Classic finden Sie [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=de).

---
product: campaign
title: Installieren der Clientkonsole
description: Erfahren Sie, wie Sie die Client-Konsole installieren
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

# Installieren und Aktualisieren der Campaign-Clientkonsole{#installing-the-client-console}

Die Client-Konsole in Campaign ist ein Rich-Client, mit dem Sie eine Verbindung zu Ihren Campaign-Anwendungs-Servern herstellen können.

Bevor Sie mit der Installation der Client Console beginnen, müssen Sie Folgendes tun:

* Überprüfen Sie die Kompatibilität Ihres Systems und Ihrer Tools mit Adobe Campaign in der [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)
* Ermitteln Sie Ihre Campaign-Server-URL
* Ermitteln Sie Ihre Anwender-Anmeldedaten
* Lassen Sie die Microsoft Edge Webview2-Laufzeit auf Ihrem System installiert (von der Campaign Classic 7.3 Build-Version). [Weitere Informationen](#webview)

Die Installation oder Aktualisierung der Clientkonsole hängt von Ihrer Implementierung von Adobe Campaign Classic ab.
Lesen Sie die folgenden Details, um zu verstehen, was für Ihre Implementierung erforderlich ist.

![](assets/do-not-localize/how-to-video.png) Erfahren Sie, wie Sie den Adobe Campaign-Client in [video](#video) installieren und einrichten.

>[!CAUTION]
>
>* Die Campaign Client-Konsole und der Campaign-Anwendungsserver müssen **auf derselben Produktversion ausführen**. Adobe empfiehlt außerdem dringend die Verwendung von **demselben Produkt-Build**. In [diesem Abschnitt](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) erfahren Sie, wie Sie Ihre Campaign-Client- und -Server-Versionen überprüfen.
>
>* Der Zugriff auf den Installationsordner, in dem die Konsole installiert ist, sollte auf den vorgesehenen Benutzer beschränkt sein, um sicherzustellen, dass die Schreibberechtigungen entsprechend eingeschränkt sind.



## Installation der Microsoft Edge Webview2-Laufzeitumgebung {#webview}

Ab der Build-Version 7.3 von Campaign Classic ist die Installation der Microsoft Edge Webview 2-Laufzeitumgebung für jede Konsolen-Installation erforderlich.

WebView wird standardmäßig als Teil des Betriebssystems Windows 11 installiert. Wenn es nicht bereits auf Ihrem System vorhanden ist, werden Sie vom Campaign Classic Console-Installationsprogramm aufgefordert, es von der [Microsoft Developer-Website](https://www.adobe.com/go/acc-ms-webview2-runtime-download_de) herunterzuladen. Beachten Sie, dass der Download-Link nicht mit Internet Explorer 11 funktioniert, da Microsoft die Unterstützung dieses Browsers eingestellt hat. Stellen Sie sicher, dass Sie einen anderen Browser verwenden, um auf den Link zuzugreifen.

## Adobe gehostete Implementierungen {#hosted-customers}

Als gehosteter Kunde haben Sie zwei Möglichkeiten, Ihre Client-Konsole(n) zu installieren oder zu aktualisieren:

1. Adobe kann direkt bereitgestellt werden. Nach der Aktualisierung der Konsole werden Benutzer aufgefordert, die neueste Clientkonsolenversion in einem Popup-Fenster herunterzuladen.

1. Sie können von [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html) auf Ihre Client-Konsole(n) herunterladen

   **Benutzer benötigen Administratorzugriff, um die Aktualisierung abzuschließen. Wenn die Benutzer keine Administratorrechte haben, muss ein Systemadministrator für alle Clientkonsolen bereitstellen**

## Hybrid- und On-Premise-Implementierungen {#hybrid-onprem-customers}

Damit sich Adobe Campaign-Benutzer bei der von Ihnen erstellten und konfigurierten Instanz anmelden können, müssen sie die Clientkonsole verwenden.

### Bereitstellen der Konsole für Benutzer {#make-console-available}

Wenn der zum Starten eines Adobe Campaign-Anwendungsservers verwendete Computer (nlserver web) Benutzerverbindungen von der Clientkonsole erhält, können Sie ihn so konfigurieren, dass das Installationsprogramm für den Rich-Client von Adobe Campaign über eine HTML-Schnittstelle verfügbar gemacht wird. Sobald eine neue Version der Client-Konsole verfügbar ist, werden Benutzer aufgefordert, sie beim Start ihrer Client-Konsole herunterzuladen.

Gehen Sie dazu folgendermaßen vor:

1. Wählen Sie das Paket aus, das das Konsoleninstallationsprogramm enthält.

   Diese Datei wird als setup-client-7.X.XXXX.exe bezeichnet, wobei X die Unterversion von Adobe Campaign und XXXX die Build-Nummer ist.

1. Kopieren Sie dieses Paket und fügen Sie es in den Adobe Campaign-Installationsordner (auf dem Marketing-Server für hybride Installationen) unter /datakit/nl/eng/jsp ein.

1. Starten Sie den Adobe Campaign-Server.


### Option &quot;Frage nicht mehr stellen&quot;

Adobe empfiehlt, die Option **[!UICONTROL Diese Frage nicht mehr stellen]** nicht auszuwählen, um sicherzustellen, dass alle Benutzer benachrichtigt werden, wenn eine neue Konsolenversion verfügbar ist.  Wenn diese Option aktiviert ist, wird der Anwender nicht über neue verfügbare Versionen informiert.

Wenn **[!UICONTROL Diese Frage nicht mehr stellen]** ausgewählt wurde, können Sie diese Aufforderung zurücksetzen. Nur Systemadministratoren, die mit der Bearbeitung von Windows Registry vertraut sind, sollten diese Änderungen vornehmen:

1. Öffnen Sie den Registrierungs-Editor mit dem Befehl **regedit** im Menü **[!UICONTROL Start > Ausführen]** .

1. Suchen Sie nach dem Knoten und erweitern Sie ihn.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Löschen Sie den Eintrag **confAdvisedUpgrade** und schließen Sie den Registrierungs-Editor.

>[!NOTE]
>
>Wenn Sie eine aktualisierte Konsole auf eine vorhandene Implementierung anwenden, erhalten die Benutzer automatisch eine Aufforderung, ihre Client-Konsole zu aktualisieren. Wenn Sie Campaign zum ersten Mal implementieren, müssen Benutzer die Konsole herunterladen. Weitere Informationen zu beiden Optionen finden Sie unten

### Aktualisieren der Konsole für die vorhandene Implementierung{#update-the-client-console}

Sobald die Konsole im Ordner Campaign-Server verfügbar ist, werden die Benutzer aufgefordert, die neueste Clientkonsoleversion in einem Popup-Fenster herunterzuladen.

**Benutzer benötigen Administratorzugriff, um die Aktualisierung abzuschließen. Wenn die Benutzer keine Administratorrechte haben, muss ein Systemadministrator für alle Clientkonsolen bereitstellen**


### Herunterladen der Konsole für eine neue Implementierung{#download-the-client-console}

Benutzer sollten jetzt die Konsole herunterladen und installieren, indem sie die folgenden Schritte ausführen:

1. Öffnen Sie einen Webbrowser und laden Sie die Konsole von der folgenden Adresse herunter:

   `https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`.

1. Geben Sie im Identifizierungsfenster Ihren Login und Ihr Passwort ein.

   ![](assets/s_ncs_install_setup_download01.png)

   Verwenden Sie bei Bedarf die Anmeldeinformationen des bei der Instanzerstellung definierten internen Kontos.

1. Klicken Sie auf der Installationsseite auf den Link **[!UICONTROL Download]** .
1. Laden Sie die Client-Setup-Datei herunter und speichern Sie sie.
1. Führen Sie die heruntergeladene Datei auf einem Computer unter Windows aus: Die Installation wird gestartet. Der Standardinstallationspfad der Clientkonsole ist **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, wobei &quot;X&quot;entsprechend Ihrer Adobe Campaign-Version &quot;6&quot;oder &quot;7&quot;ist.

### Erstellen der Verbindung - nur Erstbenutzer{#create-the-connection}

Sobald die Client-Konsole installiert ist, führen Sie die folgenden Schritte aus, um die Verbindung zum Anwendungs-Server herzustellen:

1. Starten Sie die Konsole über das Menü Windows **[!UICONTROL Start]** in der Programmgruppe **Adobe Campaign**.

1. Klicken Sie in der oberen rechten Ecke der Felder mit den Anmeldedaten auf den Link, um das Fenster für die Verbindungskonfiguration aufzurufen.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klicken Sie auf **[!UICONTROL Hinzufügen > Verbindung]** und geben Sie die Bezeichnung und URL des Adobe Campaign-Anwendungs-Servers ein.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Geben Sie per URL eine Verbindung zum Adobe Campaign-Anwendungs-Server an. Verwenden Sie entweder einen DNS oder einen Alias des Computers oder Ihre IP-Adresse.

   Sie können beispielsweise die URL vom Typ `https://<machine>.<domain>.com` verwenden.

1. Wenn Adobe IMS für Ihr Unternehmen konfiguriert ist, aktivieren Sie die Option **[!UICONTROL Verbindung mit einer Adobe ID herstellen]** .

1. Klicken Sie auf **[!UICONTROL OK]**, um Ihre Einstellungen zu speichern.

Sie können so viele Verbindungen wie erforderlich hinzufügen, um z. B. Verbindungen zu Ihren Test-, Staging- und Produktionsumgebungen herzustellen.

>[!NOTE]
>
>Die Schaltfläche **[!UICONTROL Hinzufügen]** erlaubt die Erstellung von **[!UICONTROL Ordnern]**, in die Sie Ihre verschiedenen Verbindungen per Drag-and-Drop verschieben können.

### Bei Adobe Campaign anmelden

Gehen Sie wie folgt vor, um sich bei einer vorhandenen Instanz anzumelden:

1. Starten Sie die Konsole über das Menü Windows **[!UICONTROL Start]** in der Programmgruppe **Adobe Campaign**.

1. Klicken Sie in der oberen rechten Ecke der Felder mit den Anmeldedaten auf den Link, um das Fenster für die Verbindungskonfiguration aufzurufen.

1. Wählen Sie die Campaign-Instanz aus, bei der Sie sich anmelden möchten.

1. Klicken Sie auf **[!UICONTROL OK]**

1. Geben Sie Ihre Anmeldedaten für den Benutzer ein und klicken Sie auf **[!UICONTROL Anmelden]**

>[!NOTE]
>
>Bei den Build-Versionen 7.3 von Campaign Classic kann es vorkommen, dass die Adobe Campaign-Client-Konsole während der Proxy-Authentifizierung zweimal nach den Proxy-Anmeldedaten fragt. Dies liegt daran, dass Microsoft Edge WebView2 im Gegensatz zum Internet Explorer keine Proxy-Anmeldedaten im Cache/Kennwortspeicher speichert.

**Verwandte Themen** 

* [Erstellen einer Instanz und Anmelden bei](../../installation/using/creating-an-instance-and-logging-on.md).
* [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html)

## Anleitungsvideo

In diesem Video wird gezeigt, wie der Adobe Campaign-Client installiert und eingerichtet wird.

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

Weitere Anleitungsvideos zu Campaign Classic finden Sie [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=de).

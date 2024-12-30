---
product: campaign
title: Integration in einen Webserver für Windows
description: Integration in einen Webserver für Windows
feature: Installation, Instance Settings
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 041c4431-baae-4e64-9e9a-0daa5123bd8a
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 3%

---

# Integration in einen Webserver für Windows {#integration-into-a-web-server-for-windows}

Adobe Campaign enthält Apache Tomcat, das über HTTP (und SOAP) als Einstiegspunkt im Anwendungsserver fungiert.

Sie können diesen integrierten Tomcat-Server verwenden, um HTTP-Anfragen zu bearbeiten.

In diesem Fall:

* Der standardmäßige Überwachungs-Port ist 8080. Informationen zu Änderungen finden Sie [diesem Abschnitt](../../installation/using/configure-tomcat.md).
* Die Client-Konsolen stellen dann über eine URL wie ```https:// `<computer>`:8080``` eine Verbindung her.

Aus Sicherheits- und Verwaltungsgründen empfehlen wir jedoch die Verwendung eines dedizierten Webservers als Haupteinstiegspunkt für den HTTP-Traffic, wenn der Computer, auf dem Adobe Campaign ausgeführt wird, im Internet verfügbar ist und Sie den Zugriff auf die Konsole außerhalb Ihres Netzwerks öffnen möchten.

Mit einem Webserver können Sie auch die Vertraulichkeit der Daten mit dem HTTPs-Protokoll gewährleisten.

Ebenso müssen Sie einen Webserver verwenden, wenn Sie die Tracking-Funktion verwenden möchten, die nur als Webserver-Erweiterungsmodul verfügbar ist.

## Konfigurieren des IIS-Webservers {#configuring-the-iis-web-server}

Das Konfigurationsverfahren für einen Microsoft IIS-Webserver ist größtenteils grafisch. Dazu gehört die Verwendung einer Website für den Zugriff auf die Ressourcen des Adobe Campaign-Servers: Java-Dateien (.jsp), Stylesheets (.css, .xsl), Bilder (.png), die ISAPI-DLL für die Umleitung usw.


### Konfigurationsschritte {#configuration-steps}

Gehen Sie wie folgt vor, um Adobe Campaign mit dem Microsoft IIS-Webserver zu integrieren:

1. Öffnen Sie Microsoft IIS.
1. Erstellen und konfigurieren Sie die Site (z. B. Adobe Campaign) in Abhängigkeit von den Parametern Ihres Netzwerks (TCP-Verbindungsport, DNS-Host, IP-Adresse).

   Sie müssen mindestens den Namen der Site und den Zugriffspfad zum virtuellen Verzeichnis angeben. Da der Pfad für den Zugriff auf das Website-Verzeichnis nicht verwendet wird, können Sie das folgende Verzeichnis verwenden.

   ```
   C:\inetpub\wwwroot
   ```

   ![](assets/s_ncs_install_iis7_parameters_step1.png)

1. Ein **VBS**-Skript ermöglicht es Ihnen, die vom Adobe Campaign-Server verwendeten Ressourcen automatisch für das soeben erstellte virtuelle Verzeichnis zu konfigurieren. Doppelklicken Sie zum Starten auf die Datei **iis_neolane_setup.vbs** im `[INSTALL]\conf`, wobei `[INSTALL]` der Pfad für den Zugriff auf den Adobe Campaign-Installationsordner ist.

   >[!NOTE]
   >
   >Sie müssen als Administrator angemeldet sein, um das VBS-Skript ausführen zu können oder das Skript als Administrator auszuführen.

   Klicken Sie **[!UICONTROL OK]** wenn der Webserver als Tracking-Weiterleitungsserver verwendet wird, oder klicken Sie andernfalls auf **[!UICONTROL Abbrechen]**.

   Wenn mehrere Websites bereits auf dem Webserver konfiguriert sind, wird eine Zwischenseite angezeigt, um anzugeben, für welche Website die Installation gilt: Geben Sie die mit der Website verknüpfte Nummer ein und klicken Sie auf **[!UICONTROL OK]**.

1. Stellen Sie auf der **[!UICONTROL Inhaltsansicht]** sicher, dass die Website mit den Adobe Campaign-Ressourcen korrekt konfiguriert ist:

   Wenn die Baumstruktur nicht angezeigt wird, starten Sie Microsoft IIS neu.

### Rechte {#managing-rights}

Als Nächstes müssen Sie die Sicherheitseinstellungen für die ISAPI-DLL und für die Ressourcen im Adobe Campaign-Installationsverzeichnis konfigurieren.

Gehen Sie hierzu wie folgt vor:

1. Wählen Sie die Registerkarte **[!UICONTROL Funktionsansicht]** aus und doppelklicken Sie auf den Link **Authentifizierung**.

   ![](assets/s_ncs_install_iis7_parameters_step8.png)

1. Stellen Sie auf der Registerkarte **Verzeichnissicherheit** der Website sicher, dass der anonyme Zugriff aktiviert ist. Klicken Sie ggf. auf den Link **[!UICONTROL Bearbeiten]**, um die Einstellungen zu ändern.

   ![](assets/s_ncs_install_iis7_parameters_step9.png)

### Starten des Webservers und Testen der Konfiguration {#launching-the-web-server-and-testing-the-configuration}

Jetzt müssen Sie testen, ob die Konfiguration korrekt ist.

Gehen Sie dazu wie folgt vor:

1. Starten Sie den Microsoft-IIS-Server mithilfe der **iisreset**-Befehlszeile neu.

1. Starten Sie den Adobe Campaign-Service und stellen Sie sicher, dass er ausgeführt wird.

1. Testen Sie das Tracking-Modul, indem Sie die folgende URL in einen Webbrowser einfügen:

   ```
   https://<computer>/r/test
   ```

   Der Browser sollte die folgende Antwort anzeigen:

   ```
   <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='myserver.mydomain.com' localHost='localhost'/>
   ```

Um zu testen, ob das Umleitungsmodul vorhanden ist, führen Sie die folgende Befehlszeile aus:

```
nlserver pdump
```

Sie muss die folgenden Informationen zurückgeben:

```sql
HH:MM:SS >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
webmdl@default (1644) - 18.2 Mo
```

Sie können auch sicherstellen, dass die ISAPI-DLL korrekt geladen wird.

Gehen Sie hierzu wie folgt vor:

1. Bearbeiten Sie die ISAPI-Filter für die Adobe Campaign-Site, indem Sie auf das Symbol **[!UICONTROL Treiberzuordnung]** klicken.
1. Überprüfen Sie den Inhalt des ISAPI-Filters.


## Ändern der Größenbeschränkung für Upload-Dateien {#changing-the-upload-file-size-limit}

Beim Konfigurieren des IIS-Webservers wird automatisch eine Beschränkung von etwa 28 MB für Dateien festgelegt, die auf den Server hochgeladen werden.

Dies kann sich auf Adobe Campaign auswirken, insbesondere wenn Sie Dateien hochladen möchten, die größer sind als diese Beschränkung.

Wenn Sie z. B. eine Aktivität vom Typ **Laden (Datei)** in einem Workflow zum Importieren einer 50-MB-Datei verwenden, führt ein Fehler dazu, dass der Workflow nicht ordnungsgemäß ausgeführt wird.

In diesem Fall müssen Sie diese Grenze erhöhen.

Weitere Informationen zu dieser Microsoft IIS-Option finden Sie im Abschnitt „Vorgehensweise“ der [Microsoft-Dokumentation](https://learn.microsoft.com/en-us/iis/configuration/system.webServer/security/requestFiltering/requestLimits/){target="_blank"}.


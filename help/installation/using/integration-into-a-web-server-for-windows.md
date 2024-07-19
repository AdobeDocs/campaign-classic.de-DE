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

Adobe Campaign enthält Apache Tomcat, der über HTTP (und SOAP) als Einstiegspunkt im Anwendungsserver fungiert.

Sie können diesen integrierten Tomcat-Server verwenden, um HTTP-Anforderungen zu erfüllen.

In diesem Fall:

* Der standardmäßige Listening-Anschluss ist 8080. Informationen zum Ändern finden Sie in [diesem Abschnitt](../../installation/using/configure-tomcat.md).
* Der Client Konsolen stellt dann die Verbindung über eine URL wie ```https:// `<computer>`:8080``` her.

Aus Sicherheits- und Verwaltungsgründen empfehlen wir jedoch die Verwendung eines dedizierten Webservers als Haupteinstiegspunkt für HTTP-Traffic, wenn der Computer, auf dem Adobe Campaign ausgeführt wird, im Internet verfügbar ist und Sie den Zugriff auf die Konsole außerhalb Ihres Netzwerks öffnen möchten.

Mit einem Webserver können Sie auch die Vertraulichkeit von Daten mit dem HTTP-Protokoll gewährleisten.

Ebenso müssen Sie einen Webserver verwenden, wenn Sie die Tracking-Funktion verwenden möchten, die nur als Webserver-Erweiterungsmodul verfügbar ist.

## Konfigurieren des IIS-Webservers {#configuring-the-iis-web-server}

Das Konfigurationsverfahren für einen Microsoft IIS-Webserver ist größtenteils grafisch. Dazu gehört die Verwendung einer Website für den Zugriff auf die Ressourcen des Adobe Campaign-Servers: Java-Dateien (.jsp), Stylesheets (.css, .xsl), Bilder (.png), die ISAPI-DLL für die Weiterleitung usw.


### Konfigurationsschritte {#configuration-steps}

Gehen Sie wie folgt vor, um Adobe Campaign mit dem Microsoft IIS-Webserver zu integrieren:

1. Öffnen Sie Microsoft IIS.
1. Erstellen und konfigurieren Sie die Site (z. B. Adobe Campaign) entsprechend den Netzwerkparametern (TCP-Verbindungsport, DNS-Host, IP-Adresse).

   Sie müssen mindestens den Namen der Site und den Zugriffspfad zum virtuellen Verzeichnis angeben. Da der Pfad für den Zugriff auf das Website-Verzeichnis nicht verwendet wird, können Sie das folgende Verzeichnis verwenden.

   ```
   C:\inetpub\wwwroot
   ```

   ![](assets/s_ncs_install_iis7_parameters_step1.png)

1. Mit einem **VBS** -Skript können Sie die vom Adobe Campaign-Server verwendeten Ressourcen automatisch in dem virtuellen Verzeichnis konfigurieren, das wir gerade erstellt haben. Doppelklicken Sie zum Starten auf die Datei **is_neolane_setup.vbs** im Ordner `[INSTALL]\conf` , wobei `[INSTALL]` der Pfad für den Zugriff auf den Adobe Campaign-Installationsordner ist.

   >[!NOTE]
   >
   >Sie müssen als Administrator angemeldet sein, um das VBS-Skript auszuführen oder das Skript als Administrator auszuführen.

   Klicken Sie auf **[!UICONTROL OK]** , wenn der Webserver als Tracking-Weiterleitungsserver verwendet wird, klicken Sie andernfalls auf **[!UICONTROL Abbrechen]**.

   Wenn auf dem Webserver bereits mehrere Sites konfiguriert sind, wird eine Zwischenseite angezeigt, auf der angegeben wird, für welche Website die Installation gilt: Geben Sie die mit der Site verknüpfte Nummer ein und klicken Sie auf **[!UICONTROL OK]**.

1. Stellen Sie auf der Registerkarte **[!UICONTROL Inhaltsansicht]** sicher, dass die Website korrekt mit den Adobe Campaign-Ressourcen konfiguriert ist:

   Wenn die Baumstruktur nicht angezeigt wird, starten Sie Microsoft IIS neu.

### Rechte {#managing-rights}

Als Nächstes müssen Sie die Sicherheitseinstellungen für die ISAPI-DLL und die Ressourcen im Adobe Campaign-Installationsverzeichnis konfigurieren.

Gehen Sie hierzu wie folgt vor:

1. Wählen Sie die Registerkarte **[!UICONTROL Ansicht der Funktionen]** aus und doppelklicken Sie auf den Link **Authentifizierung** .

   ![](assets/s_ncs_install_iis7_parameters_step8.png)

1. Stellen Sie auf der Registerkarte **Ordnersicherheit** der Website sicher, dass der anonyme Zugriff aktiviert ist. Klicken Sie bei Bedarf auf den Link **[!UICONTROL Bearbeiten]** , um die Einstellungen zu ändern.

   ![](assets/s_ncs_install_iis7_parameters_step9.png)

### Webserver starten und Konfiguration testen {#launching-the-web-server-and-testing-the-configuration}

Sie müssen nun testen, ob die Konfiguration korrekt ist.

Gehen Sie dazu wie folgt vor:

1. Starten Sie den Microsoft IIS-Server mit der Befehlszeile **iisreset** neu.

1. Starten Sie den Adobe Campaign-Dienst und stellen Sie sicher, dass er ausgeführt wird.

1. Testen Sie das Tracking-Modul, indem Sie die folgende URL in einen Webbrowser einfügen:

   ```
   https://<computer>/r/test
   ```

   Der Browser sollte die folgende Antwort anzeigen:

   ```
   <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='myserver.mydomain.com' localHost='localhost'/>
   ```

Führen Sie die folgende Befehlszeile aus, um auf das Vorhandensein des Weiterleitungsmoduls zu testen:

```
nlserver pdump
```

Sie muss die folgenden Informationen zurückgeben:

```sql
HH:MM:SS >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
webmdl@default (1644) - 18.2 Mo
```

Sie können auch sicherstellen, dass die ISAPI-DLL richtig geladen ist.

Gehen Sie hierzu wie folgt vor:

1. Bearbeiten Sie die ISAPI-Filter für die Adobe Campaign-Site, indem Sie auf das Symbol **[!UICONTROL Treiberzuordnung]** klicken.
1. Überprüfen Sie den Inhalt des ISAPI-Filters.


## Größenbeschränkung für Upload-Dateien ändern {#changing-the-upload-file-size-limit}

Beim Konfigurieren des IIS-Webservers wird für bestimmte Dateien, die auf den Server hochgeladen werden, automatisch eine Beschränkung von ca. 28 MB festgelegt.

Dies kann sich auf Adobe Campaign auswirken, insbesondere wenn Sie Dateien hochladen möchten, die diese Beschränkung überschreiten.

Wenn Sie beispielsweise die Aktivität **Laden (Datei)** in einem Workflow verwenden, um eine 50-MB-Datei zu importieren, wird die ordnungsgemäße Ausführung des Workflows durch einen Fehler verhindert.

In diesem Fall müssen Sie diese Grenze erhöhen.

Weitere Informationen zu dieser Microsoft IIS-Option finden Sie im Abschnitt &quot;HowTo&quot;der [Microsoft-Dokumentation](https://learn.microsoft.com/en-us/iis/configuration/system.webServer/security/requestFiltering/requestLimits/){target="_blank"}.


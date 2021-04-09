---
solution: Campaign Classic
product: campaign
title: Integration in einen Web-Server für Windows
description: Integration in einen Web-Server für Windows
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 041c4431-baae-4e64-9e9a-0daa5123bd8a
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '994'
ht-degree: 4%

---

# Integration in einen Web-Server für Windows{#integration-into-a-web-server-for-windows}

Adobe Campaign enthält Apache Tomcat, der als Einstiegspunkt im Anwendungsserver über HTTP (und SOAP) fungiert.

Sie können diesen integrierten Tomcat-Server verwenden, um HTTP-Anforderungen zu erfüllen.

In diesem Fall:

* Der standardmäßige Listening-Anschluss ist 8080. Um sie zu ändern, lesen Sie [diesen Abschnitt](../../installation/using/configure-tomcat.md).
* Der Client Konsolen verbindet sich dann mit einer URL wie [https:// `<computer>`:8080](https://myserver.adobe.com:8080).

Aus Sicherheits- und Verwaltungsgründen sollten Sie jedoch einen dedizierten Webserver als Haupteinstiegspunkt für HTTP-Traffic verwenden, wenn der Computer, auf dem Adobe Campaign ausgeführt wird, im Internet verfügbar ist und Sie den Zugriff auf die Konsole außerhalb Ihres Netzwerks öffnen möchten.

Mit einem Webserver können Sie auch die Vertraulichkeit von Daten mit dem HTTP-Protokoll gewährleisten.

Ebenso müssen Sie einen Webserver verwenden, wenn Sie die Verfolgungsfunktion verwenden möchten, die nur als Webserver-Erweiterungsmodul verfügbar ist.

>[!NOTE]
>
>Wenn Sie die Verfolgungsfunktion nicht verwenden, können Sie eine Standardinstallation von Apache oder IIS mit einer Weiterleitung zur Kampagne durchführen. Das Tracking-Webserver-Erweiterungsmodul ist nicht erforderlich.

## IIS-Webserver {#configuring-the-iis-web-server} konfigurieren

Die Konfigurationsmethode für einen IIS-Webserver ist meist grafisch. Hierzu gehört die Verwendung einer Website (bereits erstellt oder noch nicht erstellt) zum Zugriff auf die Ressourcen des Adobe Campaign-Servers: Java-Dateien (.jsp), Stylesheets (.css, .xsl), Bilder (.png), die ISAPI-DLL für die Weiterleitung usw.

Die folgenden Abschnitte enthalten eine Detailkonfiguration in IIS 7. Die Konfiguration für IIS8 ist im Grunde gleich.

Wenn der Web IIS-Server noch nicht auf Ihrem Computer installiert ist, können Sie ihn über das Menü **[!UICONTROL Hinzufügen > Programm entfernen > Windows-Funktionen aktivieren oder deaktivieren.]**

In IIS 7 müssen Sie zusätzlich zu den Standarddiensten die ISAPI-Erweiterungen und ISAPI-Filter installieren.

![](assets/s_ncs_install_iis7_isapi.png)

### Konfigurationsschritte {#configuration-steps}

Befolgen Sie zur Konfiguration die nachstehenden Etappen:

1. Öffnen Sie IIS über das Menü **[!UICONTROL Systemsteuerung > Verwaltung > Dienste]**.
1. Erstellen und konfigurieren Sie die Site (z. B. Adobe Campaign) abhängig von den Parametern Ihres Netzwerks (TCP-Verbindungsanschluss, DNS-Host, IP-Adresse).

   ![](assets/s_ncs_install_iis7_add_site.png)

   Sie müssen mindestens den Namen der Site und den Zugriffspfad zum virtuellen Verzeichnis angeben. Da der Pfad für den Zugriff auf den Website-Ordner nicht verwendet wird, können Sie den folgenden Ordner verwenden.

   ```
   C:\inetpub\wwwroot
   ```

   ![](assets/s_ncs_install_iis7_parameters_step1.png)

1. Mit einem **VBS**-Skript können Sie die vom Adobe Campaign-Server verwendeten Ressourcen automatisch im soeben erstellten virtuellen Verzeichnis konfigurieren. Klicken Sie zum Starten des Programms auf die Dublette **is_neolane_setup.vbs** im Ordner `[INSTALL]\conf`, wobei `[INSTALL]` der Pfad für den Zugriff auf den Installationsordner des Adobe Campaigns ist.

   ![](assets/s_ncs_install_iis7_parameters_step2.png)

   >[!NOTE]
   >
   >Bei einer Installation des Windows-Servers 2008/IIS7 müssen Sie als Administrator angemeldet sein, um das VBS-Skript auszuführen oder das Skript als Administrator auszuführen.

   Klicken Sie auf **[!UICONTROL OK]**, wenn der Webserver als Tracking-Umleitungsserver verwendet wird, andernfalls auf **[!UICONTROL Abbrechen]**.

   Wenn auf dem Webserver bereits mehrere Sites konfiguriert sind, wird eine Zwischenseite angezeigt, auf der angegeben wird, für welche Website die Installation gilt: Geben Sie die mit der Site verknüpfte Nummer ein und klicken Sie auf **[!UICONTROL OK]**.

   ![](assets/s_ncs_install_iis7_parameters_step3.png)

   Eine Bestätigungsmeldung sollte angezeigt werden:

   ![](assets/s_ncs_install_iis7_parameters_step7.png)

1. Vergewissern Sie sich auf der Registerkarte **[!UICONTROL Content Ansicht]**, dass die Website mit den Adobe Campaign-Ressourcen richtig konfiguriert ist:

   ![](assets/s_ncs_install_iis7_parameters_step6.png)

   Wenn die Struktur nicht angezeigt wird, starten Sie den IIS neu.

### Rechte {#managing-rights}

Als Nächstes müssen Sie die Sicherheitseinstellungen für die ISAPI-DLL und für die Ressourcen im Installationsordner des Adobe Campaigns konfigurieren.

Gehen Sie hierzu wie folgt vor:

1. Wählen Sie die Registerkarte **[!UICONTROL Ansicht Funktionen]** und klicken Sie bei Dublette auf den Link **Authentifizierung**.

   ![](assets/s_ncs_install_iis7_parameters_step8.png)

1. Vergewissern Sie sich auf der Registerkarte **Ordnersicherheit** der Website, dass der anonyme Zugriff aktiviert ist. Klicken Sie bei Bedarf auf den Link **[!UICONTROL Bearbeiten]**, um die Einstellungen zu ändern.

   ![](assets/s_ncs_install_iis7_parameters_step9.png)

### Webserver starten und die Konfiguration {#launching-the-web-server-and-testing-the-configuration} testen

Sie müssen jetzt testen, ob die Konfiguration korrekt ist.

Gehen Sie dazu wie folgt vor:

1. Starten Sie den IIS-Server mit der Befehlszeile **iisreset** neu.
1. Testen Sie das Verfolgungsmodul, indem Sie die folgende URL in einen Webbrowser einfügen:

   ```
   https://<computer>/r/test
   ```

   Der Browser sollte die folgende Antwort anzeigen:

   ```
   <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='myserver.mydomain.com' localHost='localhost'/>
   ```

Führen Sie die folgende Befehlszeile aus, um zu prüfen, ob das Umleitungsmodul vorhanden ist:

```
nlserver pdump
```

Es muss die folgenden Informationen zurückgeben:

```
12:00:33 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
webmdl@default (1644) - 18.2 Mo
```

Sie können auch sicherstellen, dass die ISAPI-DLL korrekt geladen ist.

Gehen Sie hierzu wie folgt vor:

1. Bearbeiten Sie die ISAPI-Filter für die Adobe Campaign-Site, indem Sie auf das Symbol **[!UICONTROL Treiberzuordnung]** klicken.
1. Überprüfen des Inhalts des ISAPI-Filters:

   ![](assets/s_ncs_install_iis7_parameters_step11.png)

## Ergänzende Konfigurationen {#additional-configurations}

### Ändern der maximale Dateigröße für das Hochladen {#changing-the-upload-file-size-limit}

Beim Konfigurieren des IIS-Webservers wird für bestimmte Dateien, die auf den Server hochgeladen werden, automatisch eine Grenze von ca. 28 MB festgelegt.

Dies kann sich auf das Adobe Campaign auswirken, insbesondere wenn Sie Dateien hochladen möchten, die diese Grenze überschreiten.

Wenn Sie zum Beispiel eine Aktivität **Datenladedatei (Datei)** in einem Workflow verwenden, um eine 50-MB-Datei zu importieren, verhindert ein Fehler die ordnungsgemäße Ausführung des Workflows.

In diesem Fall müssen Sie diese Grenze erhöhen:

1. Öffnen Sie IIS über das Menü **[!UICONTROL Beginn > (Systemsteuerung) > Administrationstools]**.
1. Wählen Sie im Bereich **Verbindungen** die für die Installation der Adobe erstellte Site aus und klicken Sie dann bei Dublette auf **Anforderungsfilter** im Hauptbereich.
1. Wählen Sie im Bereich **Aktionen** die Option **Funktionseinstellungen bearbeiten** aus, um den Wert im Feld **Maximale zulässige Inhaltsgröße (Byte)** bearbeiten zu können.

   Um beispielsweise das Hochladen von Dateien mit einer Größe von 50 MB zu genehmigen, müssen Sie einen Wert von mehr als &quot;52428800&quot;Byte angeben.

>[!NOTE]
>
>Weitere Informationen zu dieser IIS-Option finden Sie im Abschnitt &quot;Verfahren&quot;der [offiziellen Dokumentation](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits).

### HTTP-Fehlermeldung konfigurieren {#configuring-http-error-message-display}

Wenn Sie einen IIS-Server der Version 6.1 verwenden, sind die erzeugten Fehlermeldungen möglicherweise schwer lesbar, da ein unerwünschter HTML-Code in der Meldung angezeigt wird.

Um dies zu beheben und den Fehler korrekt anzuzeigen, wenden Sie die folgende Konfiguration an:

1. Öffnen Sie IIS über das Menü **[!UICONTROL Beginn > Systemsteuerung > Verwaltung]**.
1. Wählen Sie im Bereich **Verbindungen** die für die Installation des Adobe Campaigns erstellte Site aus und klicken Sie dann bei Dublette auf **Konfigurationseditor** im Hauptbereich.
1. Wählen Sie in der Dropdown-Liste **section** **system.webServer** > **httpErrors**.
1. Wählen Sie den Wert **PassThrough** in der Zeile **existingResponse** aus.

![](assets/ins_iis_httperrors.png)

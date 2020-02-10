---
title: Server installieren
seo-title: Server installieren
description: Server installieren
seo-description: null
page-status-flag: never-activated
uuid: 02534211-c267-490d-b9c1-78f56f1284e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: d1510fd9-995b-46c6-8d57-e1fe3999235e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Server installieren{#installing-the-server}

## Ausführen des Installationsprogramms {#executing-the-installation-program}

Installieren Sie für eine Windows 32-Bit-Plattform Adobe Campaign 32 Bit. Installieren Sie für eine Windows 64-Bit-Plattform Adobe Campaign 64 Bit.

Die Installationsschritte für den Adobe Campaign-Server lauten wie folgt:

1. Führen Sie die Datei **setup.exe** aus.

   ![](assets/s_ncs_install_installer_01.png)

1. Wählen Sie den Installationstyp.

   ![](assets/s_ncs_install_installer_01a.png)

   Es stehen verschiedene Installationstypen zur Verfügung:

   * **[!UICONTROL Installation of an application server]** : Installieren Sie den Adobe Campaign-Anwendungsserver und die Client-Konsole.
   * **[!UICONTROL Minimal installation (Network)]** : Installation des Client-Computers über das Netzwerk. Falls nötig, wird nur eine begrenzte Anzahl von DLLs auf dem Computer installiert, und alle anderen Komponenten werden von einem Netzlaufwerk verwendet.
   * **[!UICONTROL Installation of a client]** : Installation der erforderlichen Komponenten für den Adobe Campaign-Client.
   * **[!UICONTROL Custom installation]** : Der Benutzer wählt die zu installierenden Elemente aus.
   Wählen Sie **Installation eines Anwendungsservers** und gehen Sie wie folgt vor:

   ![](assets/s_ncs_install_installer_02.png)

1. Wählen Sie den Installationsordner aus:

   ![](assets/s_ncs_install_installer_03.png)

1. Click **[!UICONTROL Finish]** to start the installation:

   ![](assets/s_ncs_install_installer_04.png)

   Die Fortschrittsleiste zeigt an, wie weit die Installation geht:

   ![](assets/s_ncs_install_installer_05.png)

   Nach Abschluss der Installation wird eine Meldung angezeigt, die Sie darüber informiert:

   ![](assets/s_ncs_install_installer_06.png)

   >[!NOTE]
   >
   >Sobald die Serverinstallation abgeschlossen ist, muss der Server neu gestartet werden, um ein mögliches Netzwerkproblem zu vermeiden.

   Starten Sie nach Abschluss der Installation Adobe Campaign, um die Konfigurationsdateien zu erstellen. Siehe [Erststart des Servers](#first-start-up-of-the-server).

## Übersicht über die Installation {#summary-installation-testing}

Sie können die Erstinstallation mit dem folgenden Befehl testen:

```
nlserver pdump
```

Wenn Adobe Campaign nicht gestartet wird, lautet die Antwort:

```
No task
```

## Erststart des Servers {#first-start-up-of-the-server}

Nachdem der Installationstest abgeschlossen ist, öffnen Sie über das **[!UICONTROL Start > Programs > Adobe Campaign]** Menü eine Eingabeaufforderung und geben Sie den folgenden Befehl ein:

```
nlserver web
```

![](assets/s_ncs_install_cmd_nlserverweb.png)

Die Dateien im Installationsordner werden zum Konfigurieren der Adobe Campaign-Servermodule verwendet.

Die folgenden Informationen werden angezeigt:

```
15:30:12 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
15:30:12 >   Web server start (pid=664, tid=4188)...
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confserverConf.xml' server via '[INSTALL]bin..conffraserverConf.xml.sample
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confconfig-default.xml' server via '[INSTALL]bin..confmodelsconfig-default.xml
15:30:12 >   Server started
15:30:12 >   Stop requested (pid=664)
15:30:12 >   Web server stop (pid=664, tid=4188)...
```

Drücken Sie **Strg+C** , um den Prozess zu beenden, und geben Sie dann den folgenden Befehl ein:

```
nlserver start web
```

Die folgenden Informationen werden angezeigt:

```
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Start of the 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') task in a new process 
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Generation of configuration changes '[INSTALL]bin..confserverConf.xml.diff' between '[INSTALL]bin..confserverConf.xml' and '[INSTALL]bin..conffraserverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

Geben Sie zum Beenden Folgendes ein:

```
nlserver stop web
```

Die folgenden Informationen werden angezeigt:

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Kennwort für die interne ID {#password-for-the-internal-identifier}

Der Adobe Campaign-Server definiert eine technische Anmeldung, die als **intern** bezeichnet wird und alle Rechte auf allen Instanzen hat. Kurz nach der Installation hat die Anmeldung kein Passwort. Es ist obligatorisch, eine zu definieren.

Siehe Abschnitt [Interne Kennung](../../installation/using/campaign-server-configuration.md#internal-identifier).

## Starten von Adobe Campaign-Diensten {#starting-adobe-campaign-services}

Um die Adobe Campaign-Dienste zu starten, können Sie den Service Manager verwenden oder in die Befehlszeile (mit den entsprechenden Rechten) Folgendes eingeben:

```
net start nlserver6
```

Wenn Sie die Adobe Campaign-Prozesse später beenden müssen, verwenden Sie den folgenden Befehl:

```
net stop nlserver6
```

## Installieren von LibreOffice {#installing-libreoffice}

Laden Sie LibreOffice herunter, z. B. von [https://www.libreoffice.org/download/libreoffice-fresh/](https://www.libreoffice.org/download/libreoffice-fresh/) , und befolgen Sie die regulären Installationsschritte.

Fügen Sie die folgende Umgebungsvariable hinzu:

```
OOO_BASIS_INSTALL_DIR="C:\Program Files (x86)\LibreOffice 5\"
```


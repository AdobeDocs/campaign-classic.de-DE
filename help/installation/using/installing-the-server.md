---
product: campaign
title: Installieren des Servers
description: Installieren des Servers
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: c0cb4efa-cae9-4312-88fb-738857a89595
source-git-commit: e88ed7a5710f9ec8713d9e7151d2fd4904097990
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 3%

---

# Installieren des Servers{#installing-the-server}

![](../../assets/v7-only.svg)

## Ausführen des Installationsprogramms {#executing-the-installation-program}

Installieren Sie für eine Windows-32-Bit-Plattform Adobe Campaign 32 Bit. Installieren Sie für eine Windows 64-Bit-Plattform Adobe Campaign 64 Bit.

Die Installationsschritte für den Adobe Campaign-Server lauten wie folgt:

1. Datei ausführen **setup.exe**.

   ![](assets/s_ncs_install_installer_01.png)

1. Wählen Sie den Installationstyp aus.

   ![](assets/s_ncs_install_installer_01a.png)

   Es stehen verschiedene Installationstypen zur Verfügung:

   * **[!UICONTROL Installation eines Anwendungsservers]** : Installieren Sie den Adobe Campaign-Anwendungsserver und die Clientkonsole.
   * **[!UICONTROL Minimale Installation (Netzwerk)]** : Installation des Client-Computers aus dem Netzwerk. Nur eine begrenzte Anzahl von DLLs wird auf dem Computer installiert, wenn nötig, und alle anderen Komponenten werden von einem Netzlaufwerk verwendet.
   * **[!UICONTROL Installation eines Clients]** : Installation der erforderlichen Komponenten für den Adobe Campaign-Client.
   * **[!UICONTROL Benutzerdefinierte Installation]** : Der Benutzer wählt die zu installierenden Elemente aus.

   Auswählen **Installation eines Anwendungsservers** und führen Sie die verschiedenen Schritte durch, wie unten dargestellt:

   ![](assets/s_ncs_install_installer_02.png)

1. Wählen Sie den Installationsordner aus:

   ![](assets/s_ncs_install_installer_03.png)

1. Klicken **[!UICONTROL Beenden]** um die Installation zu starten:

   ![](assets/s_ncs_install_installer_04.png)

   Der Fortschrittsbalken zeigt an, wie weit die Installation fortgeschritten ist:

   ![](assets/s_ncs_install_installer_05.png)

   Nach Abschluss der Installation erscheint eine Meldung, die Sie darüber informiert:

   ![](assets/s_ncs_install_installer_06.png)

   >[!NOTE]
   >
   >Nach Abschluss der Serverinstallation ist ein Neustart des Servers erforderlich, um mögliche Netzwerkprobleme zu vermeiden.

   Starten Sie nach Abschluss der Installation Adobe Campaign, um die Konfigurationsdateien zu erstellen. Siehe [Erstmaliger Start des Servers](#first-start-up-of-the-server).

## Zusammenfassungstests {#summary-installation-testing}

Sie können die Erstinstallation mit dem folgenden Befehl testen:

```
nlserver pdump
```

Wenn Adobe Campaign nicht gestartet wird, lautet die Antwort:

```
No task
```

## Erstmaliger Start des Servers {#first-start-up-of-the-server}

Sobald der Installationstest abgeschlossen ist, öffnen Sie eine Eingabeaufforderung über die **[!UICONTROL Start > Programme > Adobe Campaign]** und geben Sie den folgenden Befehl ein:

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

Presse **Strg+C** um den Prozess zu beenden, geben Sie folgenden Befehl ein:

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

Geben Sie zum Anhalten Folgendes ein:

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

## Kennwort für die interne Kennung {#password-for-the-internal-identifier}

Der Adobe Campaign-Server definiert eine technische Anmeldung mit dem Namen **intern** , das alle Rechte für alle Instanzen hat. Kurz nach der Installation hat die Anmeldung kein Passwort. Es ist erforderlich, eine zu definieren.

Weiterführende Informationen finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

## Starten von Adobe Campaign-Diensten {#starting-adobe-campaign-services}

Um die Adobe Campaign-Dienste zu starten, können Sie den Service Manager verwenden oder Folgendes in die Befehlszeile eingeben (mit den entsprechenden Berechtigungen):

```
net start nlserver6
```

Wenn Sie die Adobe Campaign-Prozesse später anhalten müssen, verwenden Sie den folgenden Befehl:

```
net stop nlserver6
```

## Installieren von LibreOffice {#installing-libreoffice}

Laden Sie LibreOffice herunter und führen Sie die regulären Installationsschritte aus.

Fügen Sie die folgende Umgebungsvariable hinzu:

```
OOO_BASIS_INSTALL_DIR="C:\Program Files (x86)\LibreOffice 6\"
```

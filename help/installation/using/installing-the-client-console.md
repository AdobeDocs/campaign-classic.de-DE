---
title: Installieren der Client-Konsole
description: Erfahren Sie, wie Sie die Client-Konsole installieren
page-status-flag: never-activated
uuid: 1279c0d8-bf27-4a58-ae94-796d6147231a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: d1069b23-e08d-43c5-bbfb-3158ac40dc7e
translation-type: tm+mt
source-git-commit: 48176ebb19689855f3ee5e61fa6492be5a682291
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 13%

---


# Installieren der Kampagne Client Console{#installing-the-client-console}

Die Clientkonsole in Campaign ist ein Rich-Client, mit dem Sie eine Verbindung zu Ihren Campaign-Anwendungs-Servern herstellen können. 

Bevor Sie beginnen, müssen Sie die [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html)der Kampagne überprüfen, die URL des Kampagne-Servers und die Benutzerdaten abrufen.

>[!CAUTION]
>
>Kampagne Client-Konsole und Anwendungsserver der Kampagne müssen mit derselben Produktversion ausgeführt werden. Adobe empfiehlt auch, denselben Produktaufbau zu verwenden.

## Konsole herunterladen{#download-the-client-console}

Gehen Sie wie folgt vor, um die Adobe Campaign-Client-Konsole herunterzuladen und zu installieren:

1. Öffnen Sie einen Webbrowser und laden Sie die Konsole von der folgenden Adresse herunter:

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://machine/nl/jsp/logon.jsp).

1. Geben Sie im Identifizierungsfenster Ihren Benutzernamen und Ihr Kennwort ein.

   ![](assets/s_ncs_install_setup_download01.png)

   Verwenden Sie bei Bedarf die Anmeldeinformationen des beim Erstellen der Instanz definierten internen Kontos.

1. Klicken Sie auf der Installationsseite auf den Link **[!UICONTROL Herunterladen]** .
1. Laden Sie die Client-Setupdatei herunter und speichern Sie sie.
1. Führen Sie die heruntergeladene Datei auf einem Computer unter Windows aus: Die Installation wird Beginn. Der Standardinstallationspfad der Client-Konsole ist **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, wobei &quot;X&quot;entsprechend Ihrer Adobe Campaign-Version &quot;6&quot;oder &quot;7&quot;ist.

>[!NOTE]
>
>Unter Windows können Sie die Datei &quot; **nlclient.exe** &quot;direkt aus dem `[INSTALL]/bin` Ordner auf einem Windows-Server starten, wobei `[INSTALL]` der Zugriffspfad für den Installationsordner des Adobe Campaigns angegeben ist.

## Verbindung erstellen{#create-the-connection}

Nachdem die Client-Konsole installiert wurde, führen Sie die folgenden Schritte aus, um die Verbindung zum Anwendungsserver herzustellen:

1. Beginn der Konsole über das Menü &quot;Windows- **[!UICONTROL Beginn]** &quot;in der Gruppe &quot; **Adobe Campaign** -Programm&quot;.

1. Klicken Sie auf den Link in der oberen rechten Ecke der Felder mit den Anmeldeinformationen, um das Fenster für die Verbindungskonfiguration aufzurufen.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klicken Sie auf **[!UICONTROL Hinzufügen > Verbindung]** und geben Sie die Bezeichnung und die URL des Adobe Campaign-Anwendungsservers ein.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Geben Sie über eine URL eine Verbindung zum Adobe Campaign-Anwendungsserver an. Verwenden Sie entweder ein DNS oder einen Alias des Computers oder Ihre IP-Adresse.

   Sie können beispielsweise die URL des [`https://<machine>.<domain>.com`](https://machine) Typs verwenden.

1. Wenn Adobe IMS für Ihr Unternehmen konfiguriert ist, aktivieren Sie die Option Mit Adobe ID **[!UICONTROL verbinden]**

1. Klicken Sie auf **[!UICONTROL OK]** , um Ihre Einstellungen zu speichern.

Sie können z. B. so viele Verbindungen wie erforderlich hinzufügen, um eine Verbindung zu Ihren Test-, Stage- und Produktionsfunktionen herzustellen.

>[!NOTE]
>
>Die Schaltfläche **[!UICONTROL Hinzufügen]** erlaubt die Erstellung von **[!UICONTROL Ordnern]**, in die Sie Ihre verschiedenen Verbindungen per Drag&amp;Drop verschieben können.

## Bei Adobe Campaign anmelden

Gehen Sie wie folgt vor, um sich bei einer vorhandenen Instanz anzumelden:

1. Beginn der Konsole über das Menü &quot;Windows- **[!UICONTROL Beginn]** &quot;in der Gruppe &quot; **Adobe Campaign** -Programm&quot;.

1. Klicken Sie auf den Link in der oberen rechten Ecke der Felder mit den Anmeldeinformationen, um das Fenster für die Verbindungskonfiguration aufzurufen.

1. Wählen Sie die Kampagne aus, bei der Sie sich anmelden müssen.

1. Bestätigen Sie die Aktion mit der Schaltfläche **[!UICONTROL OK]**

1. Geben Sie Ihre Anmeldedaten für den Benutzer ein und klicken Sie auf **[!UICONTROL Anmelden]**

**Verwandte Themen**

* [Erstellen einer Instanz und Anmelden](../../installation/using/creating-an-instance-and-logging-on.md).
* [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html)
* [Installieren und Einrichten des Adobe Campaign-Client](https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/getting-started/install-and-setup-the-adobe-campaign-client.html) (Video)

---
title: Installieren der Clientkonsole
seo-title: Installieren der Clientkonsole
description: Installieren der Clientkonsole
seo-description: null
page-status-flag: never-activated
uuid: 1279c0d8-bf27-4a58-ae94-796d6147231a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: d1069b23-e08d-43c5-bbfb-3158ac40dc7e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be590c6d993eecacf51736e3c3e415addae5c6bd

---


# Installieren der Clientkonsole{#installing-the-client-console}

Die Installationsanleitung für die Adobe Campaign-Konsole ist nachfolgend beschrieben.

Bevor Sie die Adobe Campaign-Konsole installieren, überprüfen Sie die in der [Kompatibilitätsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)aufgelisteten Voraussetzungen.

Um die Adobe Campaign-Konsole zu installieren, führen Sie die folgenden Schritte aus:

1. Öffnen Sie einen Webbrowser und laden Sie die Konsole von der folgenden Adresse herunter:

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://machine/nl/jsp/logon.jsp).

1. Geben Sie im Identifizierungsfenster Ihren Benutzernamen und Ihr Kennwort ein.

   ![](assets/s_ncs_install_setup_download01.png)

   Verwenden Sie bei Bedarf die Anmeldeinformationen des beim Erstellen der Instanz definierten internen Kontos.

1. Klicken Sie auf der Installationsseite auf den **[!UICONTROL Download]** Link.
1. Laden Sie die Client-Setupdatei herunter und speichern Sie sie.
1. Führen Sie die heruntergeladene Datei auf einem Computer unter Windows aus: Die Installation wird gestartet. Der Standardinstallationspfad der Client-Konsole ist **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, wobei &quot;X&quot;entsprechend Ihrer Adobe Campaign-Version &quot;6&quot;oder &quot;7&quot;ist.
1. Starten Sie nach Abschluss des Installationsprogramms die Konsole über das Windows- **[!UICONTROL Start]** Menü (in der **Adobe Campaign** -Programmgruppe).

>[!NOTE]
>
>Unter Windows können Sie die Datei &quot; **nlclient.exe** &quot;direkt aus dem `[INSTALL]/bin` Ordner auf einem Windows-Server starten, wobei `[INSTALL]` der Zugriffspfad für den Adobe Campaign-Installationsordner angegeben ist.\
>Informationen zum Erstellen einer neuen Verbindung finden Sie unter [Erstellen einer Instanz und Anmelden](../../installation/using/creating-an-instance-and-logging-on.md).


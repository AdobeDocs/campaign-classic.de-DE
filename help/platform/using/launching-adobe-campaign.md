---
title: Start von Adobe Campaign
seo-title: Start von Adobe Campaign
description: Start von Adobe Campaign
seo-description: null
page-status-flag: never-activated
uuid: c1c5bb0d-ae8e-4b0e-ab39-8b2291162557
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 6652b081-66b6-47a8-97e5-383e3251647e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 51e4d72abf3a1f48700ca38566dbf06dd24594b8

---


# Start von Adobe Campaign{#launching-adobe-campaign}

## Adobe Campaign starten {#starting-adobe-campaign}

Sie können Adobe Campaign starten, indem Sie **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]** auswählen.

Im Clientkonsole-Verbindungsfenster können Sie mithilfe Ihrer Benutzerkennung und Ihres Passworts eine existierende Datenbank auswählen oder konfigurieren und eine Verbindung mit dieser Datenbank herstellen:

![](assets/s_ncs_user_login.png)

## Verbindung mit Adobe Campaign herstellen {#connecting-to-adobe-campaign}

Sie können über ihre Adobe ID eine Verbindung mit Adobe Campaign herstellen. Weiterführende Informationen hierzu finden Sie auf [dieser Seite](../../integrations/using/about-adobe-id.md).

Die Verbindung kann auch mit einem spezifischen Login/Passwort hergestellt werden:

1. Geben Sie im Feld **[!UICONTROL login]** die Benutzerkennung ein.

   Diese wird vom Administrator der Adobe-Campaign-Plattform vergeben.

1. Enter your password in the **[!UICONTROL Password]** field.

   Wenn Sie zum ersten Mal auf die Datenbank zugreifen, ist Ihr Kennwort das vom Administrator angegebene. Nachdem Sie eine Verbindung hergestellt haben, können Sie Ihr Passwort über das **[!UICONTROL Tools > Change password...]** Menü ändern. Details zu Operatoren und Verbindungen finden Sie unter [Zugriffsverwaltung](../../platform/using/access-management.md).

1. Klicken Sie **[!UICONTROL Log in]** zur Bestätigung.

Jetzt haben Sie Zugriff auf den [Adobe-Campaign-Arbeitsbereich](../../platform/using/adobe-campaign-workspace.md).

## Verbindungen einrichten {#setting-up-connections}

Auf die Verbindungseinstellungen des Servers können Sie über den Link über dem Eingabefeld zugreifen.

![](assets/s_ncs_user_connections_management.png)

Klicken Sie im **[!UICONTROL Connections]** Fenster auf **[!UICONTROL Add > Connection]**.

![](assets/s_ncs_user_add_connexion.png)

Anschließend sind die Verbindungsparameter wie folgt zu konfigurieren:

* Enter a **[!UICONTROL Label]** to assign a name to your database connection.
* Fügen Sie die Adresse des Anwendungsservers in das **[!UICONTROL URL]** Feld ein. Wenn Sie die Verbindungs-URL nicht kennen, wenden Sie sich an den Administrator.
* Überprüfen Sie, **[!UICONTROL Connect with an Adobe ID]** ob die Operatoren mit ihrer Adobe ID eine Verbindung zur Konsole herstellen. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../integrations/using/about-adobe-id.md).
* Click **[!UICONTROL OK]** to validate.

>[!NOTE]
>
>Über die **[!UICONTROL Add]** Schaltfläche können Sie alle Verbindungen **[!UICONTROL folders]** organisieren. Ziehen Sie einfach jede Verbindung in einen Ordner.

## Benutzer und Berechtigungen {#operators-and-permissions}

The identifiers and passwords of operators with access to the software and their respective permissions are defined by your Adobe Campaign system administrator in the **[!UICONTROL Administration > Access management > Operators]** node of the Adobe Campaign tree.

This functionality is detailed in the [Access management](../../platform/using/access-management.md) section.

## Verbindung zu Adobe Campaign unterbrechen {#disconnecting-from-adobe-campaign}

Um die Verbindung zu Adobe Campaign zu unterbrechen, verwenden Sie das erste Symbol in der Symbolleiste.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>Alternativ ist es möglich, die Anwendung ohne vorheriges Abmelden direkt zu verlassen.

## Campaign-Version abrufen {#getting-your-campaign-version}

The **[!UICONTROL Help > About...]** menu lets you access the following information:

* Nummer der installierten **Software-Version**,
* **Build**-Nummer,
* einen Link zum Adobe-Campaign-Support.

   >[!CAUTION]
   >
   >Wenn Sie das Adobe-Support-Team kontaktieren, benötigen Sie die Versionsnummer und die Build-Nummer Ihrer Campaign-Clientkonsole und des Anwendungsservers.


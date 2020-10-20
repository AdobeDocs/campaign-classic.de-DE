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
translation-type: tm+mt
source-git-commit: 87ad4d4fc69d75e4367e7467ce27de29f58f9445
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 75%

---


# Start von Adobe Campaign{#launching-adobe-campaign}

Die Clientkonsole in Campaign ist ein Rich-Client, mit dem Sie eine Verbindung zu Ihren Campaign-Anwendungs-Servern herstellen können. Auf [dieser Seite](../../installation/using/installing-the-client-console.md) erfahren Sie, wie Sie die Clientkonsole herunterladen und konfigurieren.

## Adobe Campaign starten {#starting-adobe-campaign}

Sie können Adobe Campaign ausgehend vom Menü **[!UICONTROL Start > Alle Programme > Adobe Campaign v.X > Adobe Campaign Clientkonsole]** starten.

Im Clientkonsole-Verbindungsfenster können Sie mithilfe Ihrer Benutzerkennung und Ihres Passworts eine existierende Datenbank auswählen oder konfigurieren und eine Verbindung mit dieser Datenbank herstellen:

![](assets/s_ncs_user_login.png)

## Verbindung mit Adobe Campaign herstellen {#connecting-to-adobe-campaign}

Sie können über ihre Adobe ID eine Verbindung mit Adobe Campaign herstellen. Weiterführende Informationen hierzu finden Sie auf [dieser Seite](../../integrations/using/about-adobe-id.md).

Die Verbindung kann auch mit einem spezifischen Login/Passwort hergestellt werden:

1. Geben Sie im Feld **[!UICONTROL Login]** die Benutzerkennung ein.

   Diese wird vom Administrator der Adobe-Campaign-Plattform vergeben.

1. Geben Sie im Feld **[!UICONTROL Passwort]** Ihr Passwort ein.

   Beim ersten Zugriff auf die Datenbank ist das vom Administrator festgelegte Passwort zu verwenden. Anschließend kann es über das Menü **[!UICONTROL Werkzeuge > Passwort ändern...]** angepasst werden. Details zu Benutzern und Verbindungen finden Sie unter [Zugriffsverwaltung](../../platform/using/access-management.md).

1. Wählen Sie zur Bestätigung **[!UICONTROL Anmelden]** aus.

Jetzt haben Sie Zugriff auf den [Adobe-Campaign-Arbeitsbereich](../../platform/using/adobe-campaign-workspace.md).

## Verbindungen einrichten {#setting-up-connections}

Auf die Verbindungseinstellungen des Servers können Sie über den Link über dem Eingabefeld zugreifen.

![](assets/s_ncs_user_connections_management.png)

Wählen Sie im Fenster **[!UICONTROL Verbindungen]** die Option **[!UICONTROL Hinzufügen > Verbindung]** aus.

![](assets/s_ncs_user_add_connexion.png)

Anschließend sind die Verbindungsparameter wie folgt zu konfigurieren:

1. Erfassen Sie den **[!UICONTROL Namen]** der neuen Verbindung zur Datenbank.

1. Geben Sie im Feld **[!UICONTROL URL]** die Adresse des Anwendungsservers ein. Sollten Sie diese nicht kennen, kontaktieren Sie Ihren Administrator.

1. Aktivieren Sie die Option **[!UICONTROL Anmeldung mit einer Adobe ID]**, damit sich Benutzer über ihre Adobe ID mit der Konsole verbinden können. Weiterführende Informationen hierzu finden Sie [auf dieser Seite](../../integrations/using/about-adobe-id.md).

1. Wählen Sie zur Bestätigung **[!UICONTROL OK]** aus.

## Benutzer und Berechtigungen {#operators-and-permissions}

Kennungen, Passwörter und Zugriffsberechtigungen werden vom Adobe-Campaign-Systemadministrator im Verzeichnisknoten **[!UICONTROL Administration > Zugriffe > Benutzer]** des Adobe-Campaign-Navigationsbaums festgelegt.

Diese Funktionen werden im Abschnitt [Zugriffsverwaltung](../../platform/using/access-management.md) beschrieben.

## Verbindung zu Adobe Campaign unterbrechen {#disconnecting-from-adobe-campaign}

Um die Verbindung zu Adobe Campaign zu unterbrechen, verwenden Sie das erste Symbol in der Symbolleiste.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>Alternativ ist es möglich, die Anwendung ohne vorheriges Abmelden direkt zu verlassen.

## Getting your Adobe Campaign version {#getting-your-campaign-version}

Das Menü **[!UICONTROL Hilfe > Versionsinformationen…]** liefert folgende Informationen:

* **Versionsnummer** für Kampagne Client Console und Anwendungsserver
* **Build** -Nummer für Kampagne Client Console und Anwendungsserver
* Link zur Kundenunterstützung der Adobe
* Links zu den Datenschutzrichtlinien für Adoben, Nutzungsbedingungen und Cookies-Richtlinien

![](assets/about-acc.png)

Bei jedem Kontakt mit dem Kundenservice-Team der Adobe müssen Sie die Versionsnummer und die Buildnummer Ihrer Kampagne-Client-Konsole und des Anwendungsservers angeben.

Wenn Sie mit der [Kampagne Gold Standard-Version](../../rn/using/gold-standard.md)arbeiten, müssen Sie auch die SHA/1-Zeichen freigeben, die im Feld **[!UICONTROL Info]** angezeigt werden. Beispiel: In Gold **Standard 10-Version** zeigt die Buildnummer den **Build 9032@efd8a94** an, wie nachfolgend gezeigt:

![](assets/about-acc-gs.png)

Learn more about Gold Standard [in this article](https://helpx.adobe.com/de/campaign/kb/gold-standard.html).

**Verwandte Themen**:

* [Optionen zur Unterstützung von Kampagnen](https://helpx.adobe.com/de/campaign/kb/ac-support.html#acc-support)
* [Softwareverteilung](https://docs.adobe.com/content/help/de-DE/experience-cloud/software-distribution/home.html)
* [Experience Cloud- und Expertensitzungen](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)

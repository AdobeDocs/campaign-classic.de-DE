---
solution: Campaign Classic
product: campaign
title: Start von Adobe Campaign
description: Start von Adobe Campaign
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 7b1e6dd00943e10dff693d78b3aa7cf2ad3e6727
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 91%

---


# Starten von Adobe Campaign{#launching-adobe-campaign}

Die Clientkonsole in Campaign ist ein Rich-Client, mit dem Sie eine Verbindung zu Ihren Campaign-Anwendungs-Servern herstellen können. Auf [dieser Seite](../../installation/using/installing-the-client-console.md) erfahren Sie, wie Sie die Clientkonsole herunterladen und konfigurieren.

## Beginn-Adobe Campaign {#starting-adobe-campaign}

Sie können Adobe Campaign ausgehend vom Menü **[!UICONTROL Start > Alle Programme > Adobe Campaign v.X > Adobe Campaign Clientkonsole]** starten.

Im Clientkonsole-Verbindungsfenster können Sie mithilfe Ihrer Benutzerkennung und Ihres Passworts eine existierende Datenbank auswählen oder konfigurieren und eine Verbindung mit dieser Datenbank herstellen:

![](assets/acc-logon.png)

## Verbinden mit Adobe Campaign {#connecting-to-adobe-campaign}

Sie können über ihre Adobe ID eine Verbindung mit Adobe Campaign herstellen. Weiterführende Informationen hierzu finden Sie auf [dieser Seite](../../integrations/using/about-adobe-id.md).

Die Verbindung kann auch mit einem spezifischen Login/Passwort hergestellt werden:

1. Geben Sie im Feld **[!UICONTROL Login]** die Kontokennung des Benutzers ein.

   Diese wird vom Administrator der Adobe-Campaign-Plattform vergeben.

1. Geben Sie im Feld **[!UICONTROL Passwort]** Ihr Passwort ein.

   Beim ersten Zugriff auf die Datenbank ist das vom Administrator festgelegte Passwort zu verwenden. Anschließend kann es über das Menü **[!UICONTROL Werkzeuge > Passwort ändern...]** angepasst werden. Details zu Benutzern und Verbindungen finden Sie unter [Zugriffsverwaltung](../../platform/using/access-management.md).

1. Klicken Sie zum Bestätigen auf **[!UICONTROL ANMELDEN]**.<!--You can also press the **Enter** key to launch connection.-->

Jetzt haben Sie Zugriff auf den [Adobe Campaign-Arbeitsbereich](../../platform/using/adobe-campaign-workspace.md).

Auf dem **[!UICONTROL Anmeldebildschirm]** sind einige Tastaturbefehle verfügbar:
* Alle aktionsfähigen Elemente können über die **Tabulatortaste** (von oben nach unten) oder die **Tabulatortaste** + **Umschalttaste** (von unten nach oben) ausgewählt werden.
* Um die Verbindung zu starten, können Sie auch die **Eingabetaste** drücken.
* Mit der **Escape**-Taste können Sie die Felder **[!UICONTROL Login]** und **[!UICONTROL Kennwort]** auf die letzten erfolgreichen Verbindungswerte zurücksetzen.

## Einrichten von Verbindungen {#setting-up-connections}

Auf die Verbindungseinstellungen des Servers können Sie über den Link über dem Eingabefeld zugreifen.

![](assets/s_ncs_user_connections_management.png)

Wählen Sie im Fenster **[!UICONTROL Verbindungen]** die Option **[!UICONTROL Hinzufügen > Verbindung]** aus.

Anschließend sind die Verbindungsparameter wie folgt zu konfigurieren:

1. Erfassen Sie den **[!UICONTROL Namen]** der neuen Verbindung zur Datenbank.

1. Geben Sie im Feld **[!UICONTROL URL]** die Adresse des Anwendungsservers ein. Sollten Sie diese nicht kennen, kontaktieren Sie Ihren Administrator.

1. Aktivieren Sie die Option **[!UICONTROL Anmeldung mit einer Adobe ID]**, damit sich Benutzer über ihre Adobe ID mit der Konsole verbinden können. Weiterführende Informationen hierzu finden Sie [auf dieser Seite](../../integrations/using/about-adobe-id.md).

1. Wählen Sie zur Bestätigung **[!UICONTROL OK]** aus.

## Benutzer und Berechtigungen {#operators-and-permissions}

Kennungen, Passwörter und Zugriffsberechtigungen werden vom Adobe-Campaign-Systemadministrator im Verzeichnisknoten **[!UICONTROL Administration > Zugriffe > Benutzer]** des Adobe-Campaign-Navigationsbaums festgelegt.

Diese Funktionen werden im Abschnitt [Zugriffsverwaltung](../../platform/using/access-management.md) beschrieben.

## Trennen von Adobe Campaign {#disconnecting-from-adobe-campaign}

Um die Verbindung zu Adobe Campaign zu unterbrechen, verwenden Sie das erste Symbol in der Symbolleiste.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>Alternativ ist es möglich, die Anwendung ohne vorheriges Abmelden direkt zu verlassen.

## Adobe Campaign-Version {#getting-your-campaign-version} abrufen

Das Menü **[!UICONTROL Hilfe > Versionsinformationen…]** liefert folgende Informationen:

* **Versionsnummer** der Campaign-Client-Konsole und des Anwendungs-Servers
* **Build-Nummer** der Campaign-Client-Konsole und des Anwendungs-Servers
* Link zur Adobe-Kundenunterstützung
* Links zur Adobe-Datenschutzrichtlinie sowie zu Nutzungsbedingungen und Bestimmungen zu Cookies

![](assets/about-acc.png)

Wenn Sie mit dem Team der Adobe-Kundenunterstützung Kontakt aufnehmen, müssen Sie die Versionsnummer und die Build-Nummer Ihrer Adobe Campaign-Client-Konsole und des Anwendungs-Servers angeben.

Wenn Sie mit [Kampagne [!DNL Gold Standard] Version](../../rn/using/gold-standard.md) arbeiten, müssen Sie auch die SHA/1-Zeichen freigeben, die im Feld **[!UICONTROL Info]** angezeigt werden. Beispiel: In der Gold **Standard 10-Version** zeigt die Build-Nummer **build 9032@efd8a94** an, wie nachfolgend gezeigt:

![](assets/about-acc-gs.png)

Weitere Informationen zu [!DNL Gold Standard] [in diesem Artikel](../../rn/using/gs-overview.md)).

**Verwandte Themen**:

* [Hilfe- und Support-Optionen für Adobe Campaign](../../support.md)
* [Adobe Campaign-Software-Verteilung](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html)
* [Support für Adobe Experience Cloud und Expertensitzungen](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)

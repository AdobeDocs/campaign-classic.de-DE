---
solution: Campaign Classic
product: campaign
title: Erste Schritte mit dem Tracking
description: Weitere Informationen finden Sie in den allgemeinen Richtlinien zum Tracking in Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: e52d1963b72593c5dab8ced9e459d25b05044022
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 100%

---


# Erste Schritte mit dem Tracking von Nachrichten {#get-started-tracking}

Dank der Tracking-Funktionen können Sie mit Adobe Campaign die versendeten Nachrichten verfolgen und das Verhalten der Empfänger überprüfen: Öffnung, Klicks auf Links, Abmeldung usw.

Diese Informationen werden auf der Registerkarte **[!UICONTROL Tracking]** des Profils jedes Versandempfängers abgerufen. Auf dieser Registerkarte werden alle verfolgten URL-Links angezeigt, auf die der in der Liste ausgewählte Empfänger geklickt hat. Dies ist die Akkumulation aller URLs, die in den Sendungen verfolgt werden, die noch im Versandbildschirm vorhanden sind. Die Liste kann konfiguriert werden und enthält normalerweise die angeklickte URL, das Datum und die Uhrzeit des Klicks sowie das Dokument, in dem die URL gefunden wurde. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../platform/using/editing-a-profile.md#tracking-tab).

Im **Versand-Dashboard** können Sie Sendungen überwachen und etwaige Probleme beim Nachrichtenversand erkennen. Weitere Informationen dazu finden Sie in [diesem Abschnitt](../../delivery/using/delivery-dashboard.md).

Das folgende Diagramm zeigt die Phasen des Dialogs zwischen dem Benutzer und den verschiedenen Servern.

![](assets/tracking-diagram.png)

## Tracking konfigurieren {#configure-tracking}

<img src="assets/do-not-localize/icon-configure.svg" width="60px">

**Grundprinzip**

Bevor Sie das Tracking verwenden, müssen Sie es zunächst für Ihre Instanz konfigurieren. [Mehr dazu](../../installation/using/deploying-an-instance.md#operating-principle)

**Tracking-Server**

Für die Konfiguration von Tracking muss Ihre Instanz deklariert und bei dem/den Tracking-Server(n) registriert werden. [Mehr dazu](../../installation/using/deploying-an-instance.md#tracking-server)

**Tracking speichern**

Sobald das Tracking konfiguriert und Ihre URLs ausgefüllt sind, muss der Tracking-Server registriert werden. [Mehr dazu](../../installation/using/deploying-an-instance.md#saving-tracking)

## Nachrichten-Tracking {#message-tracking}

<img src="assets/do-not-localize/icon-message-tracking.svg" width="60px">

**Getrackte Links**

Sie können den Empfang von Nachrichten und die Aktivierung der im Nachrichteninhalt eingefügten Links verfolgen, um das Verhalten der Empfänger besser zu verstehen. [Mehr dazu](../../delivery/using/how-to-configure-tracked-links.md)

**URL-Tracking**

Tracking-Optionen können durch Aktivieren oder Deaktivieren von Tracking-URLs konfiguriert werden. [Mehr dazu](../../delivery/using/personalizing-url-tracking.md)

**Personalisierung getrackter Links**

Mit den Tracking-Funktionen von Campaign Classic können Sie Links in E-Mails einfügen, die personalisiert werden können und das Tracking unterstützen. [Mehr dazu](../../delivery/using/tracking-personalized-links.md)

**Trackinglogs**

Der technische Tracking-Workflow verfolgt die Tracking-Daten, sobald der Versand ausgeführt und das Tracking aktiviert wurde. Diese Daten finden Sie auf der Registerkarte &quot;Tracking&quot; Ihres Versands. [Mehr dazu](../../delivery/using/accessing-the-tracking-logs.md)

**Tracking testen**

Bevor Sie Ihre Nachrichten mit Ihrem Tracking senden, können Sie das Tracking auf Ihrer Mirror-Seite, in Ihren E-Mail-Protokollen und Links testen. [Mehr dazu](../../delivery/using/testing-tracking.md)

## Web-Anwendungs-Tracking {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

**Web-Anwendung tracken**

Sie können auch Besuche auf Web-Anwendungsseiten mit Trackingtags verfolgen und messen. Diese Funktionalität kann für alle Web-Anwendungstypen wie Formulare und Online-Umfragen verwendet werden. [Mehr dazu](../../web/using/tracking-a-web-application.md)

**Opt-out vom Web-Anwendungs-Tracking**

Mit der Opt-Out-Funktion für das Web-Anwendungs-Tracking können Sie das Tracking des Web-Verhaltens von Endbenutzern beenden, die sich gegen das Tracking ihres Verhaltens entschieden haben. Sie können ermöglichen, ein Banner in Web-Anwendungen oder Zielseiten anzuzeigen, damit Benutzer sich abmelden können. [Mehr dazu](../../web/using/web-application-tracking-opt-out.md)

## Tracking-Berichte {#tracking-reports}

<img src="assets/do-not-localize/icon_monitor.svg" width="60px">

**Tracking-Statistiken**

Dieser Bericht enthält Statistiken zu Öffnungen, Klicks und Transaktionen und ermöglicht es Ihnen, die Marketing-Wirkung des Versands zu verfolgen. [Mehr dazu](../../reporting/using/delivery-reports.md#tracking-statistics)

**URLs und Clickstreams**

Dieser Bericht zeigt die Rangfolge der infolge eines Versands besuchten Web-Seiten. [Mehr dazu](../../reporting/using/delivery-reports.md#urls-and-click-streams)

**Personen und Empfänger**

Anhand dieses Beispiels können Sie den Unterschied beim Tracking zwischen einer Person/Personen und einem Empfänger in Adobe Campaign besser verstehen. [Mehr dazu](../../reporting/using/person-people-recipients.md)

**Tracking-Indikatoren**

In diesem Bericht werden die Schlüsselindikatoren zum Tracking des Verhaltens der Empfänger beim Empfang der Sendung zusammengefasst, z. B. Öffnungsraten, Clickthrough-Raten und Clickstreams. [Mehr dazu](../../reporting/using/delivery-reports.md#tracking-indicators)

**Indikatorberechnung**

In den verschiedenen Tabellen finden Sie nach Versandtyp geordnet die Liste der Indikatoren, die in Berichten verwendet werden, sowie ihre Berechnungsformeln. [Mehr dazu](../../reporting/using/indicator-calculation.md)

## Fehlerbehebung beim Tracking {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

Die folgenden Tipps zur Fehlerbehebung helfen Ihnen, die häufigsten Probleme zu lösen, die bei der Verwendung von Tracking in Adobe Campaign Classic auftreten. Informationen zur erweiterten Fehlerbehebung finden Sie in [diesem Abschnitt](../../delivery/using/tracking-troubleshooting.md).

* Überprüfen, ob der trackinglogd-Prozess ausgeführt wird

   Dieser Prozess liest aus dem gemeinsam genutzten IIS/Webserver-Speicher und schreibt die Weiterleitungsprotokolle.

   Sie können von der Startseite aus darauf zugreifen, indem Sie in Ihrer Instanz die Registerkarte &quot;Tracking&quot; auswählen. Sie können auch den folgenden Befehl für die Instanz ausführen: `<user>@<instance>:~$ nlserver pdump`

   Wenn der trackinglogd-Prozess nicht in der Liste angezeigt wird, starten Sie ihn mit dem folgenden Befehl für die Instanz: `<user>@<instance>:~$ nlserver start trackinglogd`

* Überprüfen Sie, ob der technische Tracking-Workflow kürzlich ausgeführt wurde.

   Sie finden den technischen Tracking-Workflow in den Ordnern &quot;Administration&quot; > &quot;Produktion&quot; > &quot;Technische Workflows&quot;. 

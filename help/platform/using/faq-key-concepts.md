---
product: campaign
title: Schlüsselkonzepte
description: Häufig gestellte Fragen zu Campaign Classic
feature: Troubleshooting
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: f0d884ae-0789-4ad9-a8fa-adeffbb560ea
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '828'
ht-degree: 95%

---

# Schlüsselkonzepte {#key-concepts}



Hier finden Sie die wichtigsten Schritte, um mit der Nutzung von Adobe Campaign zu beginnen.

## Kann ich mich mit einer Adobe ID bei Campaign Classic anmelden? {#can-i-connect-to-campaign-classic-with-an-adobe-id-}

Dank der Integration mit IMS (Adobe Identity Management System) können Benutzer über ihre Adobe ID eine Verbindung zur Adobe Campaign-Konsole herstellen. Diese Integration bringt die folgenden Vorteile mit sich:

* Verwendung ein und derselben ID für alle Adobe Experience Cloud-Lösungen;
* Speicherung der Verbindung bei der Verwendung von Adobe Campaign mit den verschiedenen Integrationen;
* Optimierte Sicherheitsrichtlinien für die Kennwortverwaltung;
* Verwendung von Konten des Typs Federated ID (externer Identity Provider).

[Hier erfahren Sie mehr](../../integrations/using/about-adobe-id.md) über den Zugriff auf Campaign Classic mit einer Adobe ID.

## Welche Version von Campaign habe ich? {#what-is-my-version-of-campaign-}

Ihre [Version und Build-Nummer](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) können Sie in der Client-Konsole von Campaign über das Menü **Hilfe > Versionsinformationen...** abrufen.

## Was sind die Unterschiede zwischen der On-Premise- und der gehosteten Version? {#what-are-the-differences-when-working-on-premise-vs--in-a-hosted-environment-}

Adobe Campaign Classic bietet verschiedene Module und Optionen. Die Verfügbarkeit dieser Module und ihre Konfiguration können von der [Art der Bereitstellung](../../installation/using/hosting-models.md) Ihrer Installation abhängen: gehostet (Managed Services), hybrid oder On-Premise.

[Hier erfahren Sie mehr darüber](../../installation/using/capability-matrix.md).

## Wie kann ich Benutzerberechtigungen erteilen? {#how-can-i-set-up-user-permissions-}

Campaign-Administratoren können Berechtigungen für Benutzer im Unternehmen vergeben.

Die damit einhergehenden Rechte und Einschränkungen ermöglichen dem Benutzer Folgendes:

* Zugriff auf bestimmte Funktionen,
* Zugriff auf bestimmte Daten,
* Das Erstellen, Ändern und/oder Löschen von Daten.

[Hier erfahren Sie mehr](../../platform/using/access-management.md) zu Benutzerberechtigungen.

## Wie kann ich mit Campaign Datenschutzbestimmungen einhalten? {#how-to-be-gdpr-compliant-with-campaign-}

Adobe Campaign bietet eine Reihe von Tools, die Sie bei der Einhaltung von Datenschutzbestimmungen wie DSGVO und CCPA unterstützen.

In [diesem Dokument](privacy-and-recommendations.md) finden Sie alle in Adobe Campaign verfügbaren Tools und Funktionen sowie Best Practices, die Ihnen helfen, die DSGVO bei der Nutzung unseres Dienstes einzuhalten. Implementierungsschritte für Campaign Classic werden in [diesem Artikel](https://helpx.adobe.com/de/campaign/kb/acc-privacy.html) beschrieben.

## Über welche Benutzeroberflächen-Konzepte von Campaign sollte ich Bescheid wissen? {#what-are-campaign-user-interface-concepts-i-should-know-}

Erfahren Sie in [diesen Abschnitt](../../platform/using/adobe-campaign-workspace.md) mehr über die Grundlagen des Arbeitsbereichs von Adobe Campaign.

![](assets/do-not-localize/how-to-video.png) [Campaign-Arbeitsbereich im Video kennenlernen](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/getting-started/exploring-the-adobe-campaign-classic-user-interface.html?lang=de)

## Wie kann ich die Audience für meine Nachrichten auswählen? {#how-can-i-select-the-target-population-of-my-messages-}

Bei Adobe Campaign stehen Ihnen für die Erstellung von Audiences und die Auswahl von Empfängern unterschiedliche Strategien zur Verfügung.

[Hier erfahren Sie mehr darüber](../../delivery/using/steps-defining-the-target-population.md).

## Was ist ein Workflow? {#what-is-a-workflow-}

Mit Adobe Campaign verfügen Sie über ein integriertes Workflow-Management-System, welches die zentrale Steuerung aller Prozesse und Vorgänge der Anwendung ermöglicht. Die Workflow-Engine dient der Modellierung und Automatisierung der verschiedenen Aufgaben der Anwendungs-Server-Module. Mithilfe der grafischen Oberfläche lassen sich vollständige Arbeitsabläufe zur Segmentierung von Zielgruppen, zur Ausführung von Kampagnen, zum Umgang mit Dateien etc. gestalten.

So bieten Workflows beispielsweise die Möglichkeit, Dateien von einem Server herunterladen, sie zu entkomprimieren und die Datensätze in die Adobe Campaign-Datenbank zu importieren.

Oder benachrichtigen Sie andere Benutzer und fordern Sie sie dazu auf, Vorgänge zu validieren oder an Abstimmungen teilzunehmen. Auf diese Weise können Versandaktionen erstellt und anderen Benutzern vor dem Nachrichtenversand Aufgaben wie die Gestaltung des Inhalts, die Bestimmung der Zielgruppe und die Validierung von Testsendungen zugewiesen werden.

[Hier erfahren Sie mehr dazu](../../workflow/using/about-workflows.md) über Workflows. Sie können auch [Best Practices für Workflows](../../workflow/using/building-a-workflow.md).

## Wie erstelle und sende ich die erste E-Mail? {#how-to-create-and-send-a-first-email-}

[Hier erfahren Sie mehr darüber](../../delivery/using/about-email-channel.md).

![](assets/do-not-localize/how-to-video.png) [Video zum Thema](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/getting-started/creating-a-campaign-and-an-email.html?lang=de)

## Wie kann ich SMS-Nachrichten senden? {#how-to-send-sms-messages-}

[In diesem Abschnitt](../../delivery/using/sms-channel.md) erfahren Sie, wie Sie Ihre Plattform konfigurieren und SMS-Nachrichten senden.

## Wie kann ich Push-Benachrichtigungen senden? {#how-to-send-push-notifications-}

Hier erfahren Sie, wie Sie mit Adobe Campaign [eine personalisierte Push-Benachrichtigung](../../delivery/using/create-notifications-ios.md) über Mobile Apps an iOS- und Android-Geräte senden.

## Wie erstelle und teile ich eine Online-Umfrage? {#how-to-design-and-share-an-online-survey-}

Hier erfahren Sie, wie Sie [eine Online-Umfrage erstellen](../../surveys/using/getting-started-with-surveys.md), einschließlich der wichtigsten Schritte zur Konzeption und Veröffentlichung mit Campaign Classic.

## Wie erstelle ich eine Landingpage? {#how-to-create-landing-page-}

Mit dem Digital Content Editor von Adobe Campaign können Sie Landingpages entwerfen und das Mapping mit Datenbankfeldern definieren.

[Hier erfahren Sie mehr darüber](../../web/using/creating-a-landing-page.md).

## Wie kann ich Sendungen nachverfolgen? {#how-can-i-track-deliveries-}

Sie können in Campaign Classic gesendete Nachrichten mithilfe von speziellen [Versandberichten](../../reporting/using/delivery-reports.md) nachverfolgen und Ihre Sendungen beobachten.

Erfahren Sie mehr über die Tracking-Verwaltung in Campaign auf [dieser Seite](https://helpx.adobe.com/de/campaign/kb/acc-tracking.html).

## Was sind die Best Practices für die Sicherheit (On-Premise)? {#what-are-security-best-practices--on-premise--}

Lesen Sie die [Checkliste zur Sicherheitskonfiguration](https://helpx.adobe.com/de/campaign/kb/acc-security.html), um zu erfahren, welche Schlüsselelemente geprüft werden müssen, um eine sichere Konfiguration für On-Premise-Bereitstellungen zu gewährleisten.

## Wie übersetze ich eine Fehlermeldung? {#how-to-translate-an-error-message-}

Eine Fehlermeldung wird in einer Fremdsprache angezeigt? Alle Fehlermeldungen und deren Übersetzung werden in [diese Seite](https://experienceleague.adobe.com/developer/campaign-errors/error_codes.html?lang=de).

## Kann ich in Campaign ein Web-Formular erstellen und Antworten sammeln? {#can-i-create-a-webform-and-collect-answers-in-campaign-}

Hier erfahren Sie, wie Sie ein [Web-Formular erstellen](../../web/using/about-web-forms.md) können: Entwerfen, testen und veröffentlichen Sie ein Web-Formular und sammeln Sie Antworten.

## Gibt es eine Auflistung von veralteten Funktionen und Versionen? {#is-there-a-list-of-deprecated-features-and-versions-}

Adobe wertet laufend die Funktionen des Produkts aus. Manche Funktionen werden durch leistungsfähigere Versionen ersetzt, bei anderen werden ausgewählte Komponenten erneut implementiert, um besser für künftige Anforderungen oder Erweiterungen gerüstet zu sein. Da Campaign Drittanbieter-Tools verwendet, wird die Kompatibilität regelmäßig aktualisiert, damit nur unterstützte Versionen implementiert werden.

[Hier erfahren Sie mehr darüber](../../rn/using/deprecated-features.md).

## Gibt es neue Dokumentationsaktualisierungen und Hilfematerialien? {#are-there-new-documentation-updates-and-help-materials-released-}

Die letzten Aktualisierungen der Campaign Classic-Dokumentation finden Sie [auf dieser Seite](https://experienceleague.adobe.com/docs/campaign-classic/using/documentation-updates.html?lang=de).

Die aktuellen Technotes finden Sie [auf dieser Seite](https://helpx.adobe.com/de/campaign/kb/article-list.html).

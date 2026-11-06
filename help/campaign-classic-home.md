---
keywords: Campaign Classic;Startseite;beliebte Themen
product: campaign
title: Produktdokumentation zu Adobe Campaign Classic v7
exl-id: 6b3f1689-80de-49fd-b7ee-7a2a1931d157
TQID: 'https://experienceleague.adobe.com/Q6Oc24mo-1qDAxCWu2lGT4UvRLXB78Tr5X4sb2kHFw8'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
    internal-label: APIs
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: c1f8b6661065c8d5c75e38d80f6986e0c6fbdfa8
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 62%
---
# Campaign Classic v7 – Dokumentation {#campaign-classic-documentation}

Diese Dokumentation behandelt Campaign Classic v7 für **On-Premise- und Hybrid**-Bereitstellungen: Installation, Konfiguration, Upgrades, Vorgänge und die für v7 spezifischen Funktionen. Wenn Ihre Instanz von Adobe (Managed Cloud Services) gehostet wird, lesen Sie die [Campaign v8-Dokumentation](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/campaign-home){target="_blank"}. Inhalte, die Campaign v8 auf dieselbe Weise dokumentiert, werden hier nicht mehr dupliziert: siehe [Von v7 zu v8](#from-v7-to-v8).

<!--![](platform/using/assets/do-not-localize/banner_acc_doc.jpg) -->

## Neue Funktionen

Hier erhalten Sie einen Einblick in die neuesten Produktverbesserungen bei Adobe Campaign Classic v7 und die Dokumentation! Eine umfassende Liste der Funktionen, Verbesserungen und Fehlerbehebungen finden Sie in den detaillierten [Versionshinweisen](rn/using/latest-release.md).

>[!BEGINTABS]


>[!TAB Version Oktober 2026 ist live!]

Campaign Classic v7.4.5 - Build 26 vom Oktober (Build 9420) liefert Fehlerbehebungen für das externe Analytics-Konto, Sendungen, die im Status „Personalisierung ausstehend“ hängen, die Nutzung der Server-CPU, zeitweise auftretende Fehler bei der Aktualisierung des Datenmodells, den Spam-Überprüfungsfehler bei der Versanderstellung und die Quarantäne wiederkehrender Softbounces.

[![Bild](assets/do-not-localize/learn-more-button.svg)](rn/using/latest-release.md)

>[!TAB Verschieben zu Adobe IMS]

Um die Sicherheit und den Authentifizierungsprozess zu verbessern, empfiehlt Adobe Campaign dringend, den Authentifizierungsmodus für Endbenutzende von der nativen Authentifizierung mit Login/Passwort auf das Adobe-Identitäts-Management-System (IMS) zu migrieren.

[![Bild](assets/do-not-localize/learn-more-button.svg)](technotes/using/ac-ims.md)


>[!ENDTABS]

## Beginnen Sie mit den Grundlagen

<table style="table-layout:fixed">
  <tr style="border: 0;">
    <td>
    <a href="platform/using/launching-adobe-campaign.md"><img src="assets/do-not-localize/start-launch.png"></a></a>
    <div><strong>Adobe Campaign starten</strong><br/>Erfahren Sie, wie Sie die Campaign-Client-Konsole starten und eine Verbindung zu Ihren Campaign-Anwendungs-Servern herstellen.</div>
    </td>
    <td>
    <a href="platform/using/about-profiles.md"><img src="assets/do-not-localize/start-profiles.png"></a>
    <div><strong>Profile hinzufügen und verwalten</strong><br/>Testen Sie bequem die Profilverwaltung in der Adobe Campaign v7-Datenbank. Fügen Sie Profile manuell oder durch Importieren hinzu, verfeinern Sie Kundendaten und passen Sie Kampagnen mühelos an.</div>
    </td>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/introduction/about-workflows" target="_blank"><img src="assets/do-not-localize/start-workflows.jpeg"></a>
    <div><strong>Mit Workflows automatisieren</strong><br/>Erfahren Sie, wie Sie Workflows nutzen können, um Prozesse wie Segmentierung, Kampagnenausführung, Dateiverarbeitung, Beteiligung von Personen usw. auszuführen.
    </div></td>
    <td>
    <a href="delivery/using/communication-channels.md"><img src="assets/do-not-localize/start-deliveries.jpeg"></a>
    <div><strong>Sendungen erstellen</strong><br/>Hier erfahren Sie, wie Sie Nachrichten über verschiedene Kanäle senden, z. B. E-Mail, SMS, Push-Benachrichtigungen usw.</div>
    </td>
  </tr>
  <tr style="border: 0;">
    <td align="center"><a href="platform/using/launching-adobe-campaign.md"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    <td align="center"><a href="platform/using/about-profiles.md"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    <td align="center"><a href="https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/introduction/about-workflows" target="_blank"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    <td align="center"><a href="delivery/using/communication-channels.md"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    </tr>
</table>

## Erkunden Sie die Dokumentation

<table style="table-layout:auto">
  <tr style="border: 0;">
    <td>
      <img src="assets/do-not-localize/icon-start.svg" width="35px">
    <br/>
      <strong>Erste Schritte</strong><br/><a href="https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/new/campaign-ui" target="_blank">Benutzeroberfläche</a> (Dokumentation zu Campaign v8) – <a href="platform/using/launching-adobe-campaign.md">Herstellen einer Verbindung zu Campaign</a> – <a href="https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/data/import" target="_blank">Import und Export von Daten</a> (Dokumentation zu Campaign v8) – <a href="platform/using/access-management.md">Berechtigungen</a>
    </td>
    <td>
      <img src="assets/do-not-localize/icon-experience.svg" width="35px">
    <br/>
      <strong>Kundenerlebnis:</strong><br/><a href="https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/introduction/about-workflows" target="_blank"> mit Workflows</a> (Dokumentation zu Campaign v8) - <a href="https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html?lang=de" target="_blank">Marketing-Kampagne</a> - <a href="interaction/using/interaction-and-offer-management.md">Interaction und Angebotsverwaltung</a> - <a href="delivery/using/about-personalization.md">Personalization</a> - <a href="https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/analytics/reports/gs-reporting" target="_blank">Reporting</a> (Dokumentation zu Campaign v8)
    </td>
    <td>
      <img src="assets/do-not-localize/icon-send.svg" width="35px">
    <br/>
      <strong>Nachrichten senden</strong><br/><a href="delivery/using/communication-channels.md">Kommunikationskanäle</a> – <a href="https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/create-message" target="_blank">Testversand durchführen</a> (Dokumentation zu Campaign v8) – <a href="delivery/using/get-started-a-b-testing.md">A/B-Tests</a> – <a href="https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/analytics/tracking/tracking" target="_blank">Nachrichten-Tracking</a> – <a href="delivery/using/about-deliverability.md">Zustellbarkeit</a> – <a href="message-center/using/about-transactional-messaging.md">Transaktionsnachrichten</a>
    </td>
  </tr>
  <tr style="border: 0;">
    <td>
      <img src="assets/do-not-localize/icon_profile-audience.svg" width="35px">
      <br/> <strong>Profile und Zielgruppen</strong><br/> <a href="https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/audience/create-audiences/create-audiences" target="_blank">Listen erstellen</a> (Dokumentation zu Campaign v8) – <a href="delivery/using/about-services-and-subscriptions.md">Services und Abonnements</a> – <a href="platform/using/privacy-management.md">Datenschutz und Einverständnis</a>
    </td>
    <td>
      <img src="assets/do-not-localize/icon-configure.svg" width="35px">
      <br/>
      <strong>Architektur und Konfiguration</strong><br/><a href="production/using/general-architecture.md">Architekturgrundsätze</a> – <a href="production/using/build-upgrade.md">Build-Aktualisierung durchführen</a> – <a href="production/using/configuration.md">Kampagne konfigurieren</a> – <a href="installation/using/external-accounts.md">Verbindung zu externen Systemen herstellen</a>
    </td>
    <td>
      <img src="assets/do-not-localize/icon-dev.svg" width="35px">
      <br/>
      <strong>Entwicklungsressourcen</strong><br/><a href="https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/developer/datamodel" target="_blank">Datenmodellbeschreibung</a> (Dokumentation zu Campaign v8) - <a href="configuration/using/about-schema-reference.md">Schemastruktur</a> - <a href="configuration/using/editing-forms.md">Eingabeformulare</a> - <a href="configuration/using/about-web-services.md">APIs</a> - <a href="https://experienceleague.adobe.com/de/tools/campaign-api">JSAPI-Referenzdokumentation</a> - <a href="configuration/using/about-custom-recipient-table.md">Benutzerdefinierte Empfängertabelle</a>
    </td>
  </tr>
</table>

## Von v7 zu v8 {#from-v7-to-v8}

Inhalte, die in der Campaign v8-Dokumentation dokumentiert sind, wurden aus der v7-Dokumentation entfernt. Diese Tabelle verwenden, um sie zu finden.

| Wenn Sie auf der Suche nach… | Weitere Informationen finden Sie in der Dokumentation zu Campaign v8 |
| --- | --- |
| Die Benutzeroberfläche | [Erkunden der Benutzeroberfläche](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/new/campaign-ui){target="_blank"} |
| Profile, Listen, Import und Export | [Profile und Daten importieren](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/data/import){target="_blank"} |
| Workflows | [Über Workflows](https://experienceleague.adobe.com/en/docs/campaign/automation/workflows/introduction/about-workflows){target="_blank"} |
| Marketing-Kampagnen | [Erste Schritte mit Marketing-Kampagnen](https://experienceleague.adobe.com/en/docs/campaign/automation/campaign-orchestration/set-up-campaigns){target="_blank"} |
| Sendungen erstellen und versenden | [Erstellen einer Nachricht](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/create-message){target="_blank"} |
| Integrierte Berichte | [Erste Schritte mit Reporting](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/analytics/reports/gs-reporting){target="_blank"} |
| Berechtigungen | [Erste Schritte mit Berechtigungen](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/permissions/gs-permissions){target="_blank"} |
| Eingabeformulare | [Erste Schritte mit Formularen](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/developer/schemas-forms/forms){target="_blank"} |

## Zusätzliche Ressourcen

[Adobe Campaign – Produktbeschreibung](https://helpx.adobe.com/de/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"} – [Kompatibilitätsmatrix](rn/using/compatibility-matrix.md) – [Tutorials](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=de){target="_blank"} – [Control Panel für Campaign](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=de){target="_blank"} – [E-Mail-Tracking-Pixel und CNIL-Anleitung](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/new/cnil-pixel-tracking){target="_blank"}

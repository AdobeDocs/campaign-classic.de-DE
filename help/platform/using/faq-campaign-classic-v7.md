---
product: campaign
title: Häufig gestellte Fragen zu Campaign Classic
description: Spezifische Fragen zur Architektur, Bereitstellung und den Funktionen von Adobe Campaign Classic v7
feature: Overview, Troubleshooting
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
source-git-commit: 295e3596d9291cbcc55e2d264309141526c3806b
workflow-type: tm+mt
source-wordcount: '1535'
ht-degree: 6%

---

# Häufig gestellte Fragen zu Campaign Classic v7 {#campaign-classic-v7-faq}

In diesen häufig gestellten Fragen werden spezifische Fragen zur Architektur von Adobe Campaign Classic v7, zu Bereitstellungsmodellen und zu v7-spezifischen Funktionen behandelt.

**Umfassende Antworten auf häufig gestellte Fragen zu Campaign** (Workflows, Sendungen, Audiences, Reporting, Personalisierung usw.) finden Sie in den häufig gestellten Fragen zu [**Campaign v8**](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}, die detaillierte Antworten nach Thema enthalten.

## Architektur und Bereitstellung von Campaign Classic v7 {#v7-architecture}

### Welche Hosting-Modelle sind in Campaign Classic v7 verfügbar? {#what-are-the-hosting-models-available-in-campaign-classic-v7}

Adobe Campaign Classic v7 bietet drei Bereitstellungsmodelle:

* **Gehostet (Managed Services)** - Vollständig von Adobe verwaltet auf Adobe Infrastructure
* **On-Premise** - In Ihrer eigenen Infrastruktur installiert und verwaltet
* **Hybrid** - Mid-Sourcing-Architektur mit einer Mischung aus Cloud- und On-Premise-Komponenten

Jedes Bereitstellungsmodell verfügt über verschiedene Funktionen und Managementaufgaben. Die Verfügbarkeit von Modulen, Optionen und Konfigurationen hängt von Ihrem Bereitstellungstyp ab.

[Hier erfahren Sie mehr &#x200B;](../../installation/using/hosting-models.md) Hosting-Modelle und ihre Unterschiede.

**Hinweis:** Campaign v8 ist ausschließlich als Managed Cloud Services verfügbar. [Informationen zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html?lang=de){target="_blank"}.

### Was sind die Unterschiede zwischen der On-Premise- und der gehosteten Version? {#what-are-the-differences-when-working-on-premise-vs-in-a-hosted-environment}

Adobe Campaign Classic v7 enthält eine Reihe von Modulen und Optionen. Die Verfügbarkeit dieser Module und ihre Konfiguration hängen vom [Bereitstellungstyp](../../installation/using/hosting-models.md) Ihrer Installation ab: gehostet (Managed Services), hybrid oder On-Premise.

Die wichtigsten Unterschiede:

* **On-Premise** - Vollständige Kontrolle über Installation, Infrastruktur und Konfiguration. Erfordert interne IT-Ressourcen für Wartung, Upgrades und Sicherheit.
* **Hosted/Managed Services** - Infrastruktur und Wartung werden von Adobe verwaltet. Automatische Upgrades und erhöhte Sicherheit. Begrenzter direkter Serverzugriff.
* **Hybrid** - Kombiniert die Vorteile beider Modelle. Von Adobe gehostete Marketing-Instanz, Ausführung/Mid-Sourcing separat verwaltet.

[Klicken Sie hier für die vollständige Funktionsmatrix](../../installation/using/capability-matrix.md).

### Wie migriere ich von On-Premise/Hybrid zu Adobe Managed Services? {#how-do-i-migrate-from-on-premise-hybrid-to-adobe-managed-services}

Die Migration zu Adobe Managed Services bietet mehr Skalierbarkeit, Sicherheit und einen geringeren IT-Overhead. Vor der Umstellung auf Campaign v8 ist dies oft ein Sprungbrett.

**Wichtigste Punkte:**

* Kein automatisiertes Migrationswerkzeug verfügbar - manuelle Planung und Ausführung erforderlich
* Adobe Professional Services-Support wird dringend empfohlen
* Zu den Vorteilen gehören Cloud-Infrastruktur, automatische Sicherheits-Patches, Expertensupport und der einfachere Weg zu v8
* Die Migration umfasst Due Diligence, Umgebungsprüfung, Datenbereinigung, Staging-Migration und Produktionsumstellung

**Erste Schritte:** Wenden Sie sich an Ihren Adobe-Support-Mitarbeiter, um Ihre Umgebung zu bewerten und einen detaillierten Migrationsplan mit Adobe Professional Services zu erstellen.

Weitere Informationen über [Migration zu Managed Services](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic-blogs/migrate-your-adobe-campaign-v7-onprem-hybrid-environment-to/ba-p/681605?profile.language=de){target="_blank"}.

## Build-Upgrades (Campaign Classic v7) {#build-upgrades-v7}

### Was ist ein Build-Upgrade in Campaign Classic v7? {#what-is-a-build-upgrade-v7}

Ein Build-Upgrade ist erforderlich, wenn die Adobe Campaign Classic v7-Software auf die neueste sichere Build-Nummer aktualisiert wird, während die Versionsnummer unverändert bleibt. Beispiel: Campaign Classic v7 Build 9026 auf Campaign v7 Build 9032.

Adobe Campaign wird regelmäßig aktualisiert. Nebenversionen werden mit neuen Funktionen, Verbesserungen und Fehlerbehebungen veröffentlicht. Darüber hinaus werden Builds mit kumulativen Fehlerbehebungen nur regelmäßig veröffentlicht.

Weitere Informationen finden Sie in [diesem Abschnitt](../../rn/using/rn-overview.md).

### Wie kann ich Campaign Classic v7 auf die neueste Version aktualisieren? {#how-can-i-upgrade-campaign-classic-v7}

Adobe Campaign Classic nutzt eine Reihe von Technologien, um Mehrwert zu erzielen. Diese Kombination von Technologien erfordert eine regelmäßige Aktualisierung Ihrer Campaign Classic v7-Instanzen, um sicherzustellen, dass die aktuellen Versionen verwendet werden, um überlegene Sicherheit, Stabilität und Leistung zu bieten.

**Für gehostete Kunden:** Sie profitieren automatisch von einer jährlichen Campaign-Aktualisierung mit der neuesten stabilen Version. Adobe verwaltet den Upgrade-Prozess und koordiniert den Zeitablauf mit Ihnen.

**Für On-Premise-/Hybrid-Kunden** Sie sind für die Durchführung von Upgrades verantwortlich. Adobe empfiehlt dringend, mindestens einmal pro Jahr ein Upgrade durchzuführen.

[Lesen Sie diesen Abschnitt](../../production/using/build-upgrade.md) um zu erfahren, wie Sie Ihre Umgebung aktualisieren, und lesen Sie [Häufig gestellte Fragen &#x200B;](../../platform/using/faq-build-upgrade.md) Build-Upgrades), um detaillierte Fragen zu diesem speziellen Thema zu erhalten.

### Was ist die neueste Version von Adobe Campaign Classic v7? {#what-is-the-latest-version-v7}

Die neueste Version von Campaign Classic v7, einschließlich neuer Funktionen und Dokumentation, wird in den neuesten [Versionshinweisen](../../rn/using/latest-release.md) beschrieben.

### Woher weiß ich, welche Version von Campaign Classic v7 ich verwende? {#how-do-i-know-which-version-v7}

Überprüfen Sie Ihre Version und Build-Nummer über das Menü **[!UICONTROL Hilfe > Versionsinformationen…]** in der Client-Konsole von Adobe Campaign. Das Feld **[!UICONTROL Info]** enthält detaillierte Informationen über die Version und den Build, den Sie sowohl für die Konsole als auch für den Server ausführen.

Weitere Informationen finden Sie in [diesem Abschnitt](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

### Ist ein Build-Upgrade mit einem Versions-Upgrade identisch? {#is-build-upgrade-same-as-version-upgrade}

Nein. Ein Build-Upgrade ist eine schrittweise Aktualisierung innerhalb einer Version. Ein Upgrade einer Version ist hingegen der Wechsel von einer Version zu einer anderen. Build-Upgrades sind unkompliziert und erfordern in der Regel keine größeren Änderungen an Architektur, Technik oder Datenmodell.

Versionsaktualisierungen (z. B. von v7 auf v8) sind in der Regel mit erheblichen technischen Änderungen verbunden und erfordern je nach Ihren Anpassungen möglicherweise Konfigurationsänderungen oder eine teilweise Neuimplementierung.

## Konfiguration von Campaign Classic v7 {#v7-configuration}

### Kann ich die Sprache der Benutzeroberfläche von Campaign Classic v7 ändern? {#can-i-change-language-v7}

Die Sprache Campaign Classic v7 wird beim Erstellen der Instanz ausgewählt. **Sie können sie später nicht mehr ändern.**

Die Benutzeroberfläche von Adobe Campaign v7 ist in vier Sprachen verfügbar: Deutsch, Englisch, Französisch und Japanisch. Die Client-Konsole und der Server müssen in derselben Sprache eingestellt werden. Jede Campaign Classic v7-Instanz kann nur in einer Sprache ausgeführt werden.

Bei der Installation von Campaign v7 auf Englisch können Sie entweder Englisch (USA) oder Englisch (Großbritannien) auswählen. Die Formate unterscheiden sich in Datum und Uhrzeit.

[Weitere Informationen finden Sie in diesem Abschnitt](../../installation/using/creating-an-instance-and-logging-on.md).

**Hinweis:** Die Web-Benutzeroberfläche von Campaign v8 ermöglicht es Benutzern, die Sprache der Benutzeroberfläche unabhängig zu ändern. [Weitere Informationen](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/connect.html#language-pref){target="_blank"}.

### Wie kann ich Sicherheitszonen in Campaign Classic v7 konfigurieren? {#how-can-i-configure-security-zones-v7}

Die Self-Service-Schnittstelle für Sicherheitszonen kann verwendet werden, um Einträge in der VPN-Sicherheitszonenkonfiguration einer Adobe Campaign Classic v7-Bereitstellung zu verwalten. Dies ist in erster Linie für On-Premise- und Hybridbereitstellungen relevant.

In [&#x200B; Abschnitt &#x200B;](../../installation/using/security-zones.md) Sie mehr über Sicherheitszonen in Campaign v7.

[Klicken Sie hier, um mehr über &#x200B;](https://helpx.adobe.com/de/campaign/kb/configuring-security-zones-self-service.html){target="_blank"} Self-Service-Benutzeroberfläche der Sicherheitszone zu erfahren.

**Hinweis:** Kunden von Hosted/Managed Services sollten sich an Adobe wenden, um Sicherheitszonen zu konfigurieren.

### Kann Adobe Campaign Classic v7 mit LDAP integriert werden? {#can-campaign-classic-integrate-with-ldap}

Ja. Als **On-Premise/Hybrid-Kunde** können Sie Campaign Classic v7 für zentralisierte Authentifizierung und Benutzerverwaltung in Ihr LDAP-Verzeichnis integrieren.

Diese Integration ermöglicht Folgendes:

* Benutzer, die sich über Ihr Unternehmens-LDAP-Verzeichnis authentifizieren
* Zentralisierte Benutzer- und Rechteverwaltung
* Automatische Synchronisierung von Benutzergruppen und Berechtigungen
* Single Sign-On-Funktionen

[Klicken Sie hier, um zu erfahren](../../installation/using/connecting-through-ldap.md) wie Sie die LDAP-Integration in Campaign Classic v7 einrichten.

**Hinweis:** LDAP-Integration ist für On-Premise- und Hybridbereitstellungen verfügbar. Gehostete Kundinnen und Kunden verwenden Adobe IMS zur Authentifizierung.

### Was sind die Best Practices für die Sicherheit bei On-Premise-Bereitstellungen? {#security-best-practices-on-premise}

On-Premise- und Hybridbereitstellungen erfordern im Vergleich zu gehosteten Umgebungen eine zusätzliche Sicherheitskonfiguration und Härtung.

**Wichtige Sicherheitsbereiche:**

* Netzwerksicherheit und Firewall-Konfiguration
* Datenbankzugriff und -sicherheit
* Härtung des Betriebssystems
* Dateiberechtigungen und Zugriffssteuerungen
* Konfiguration von Sicherheitszonen
* Verschlüsselung (Daten im Ruhezustand und bei der Übertragung)
* Benutzerzugriffsverwaltung
* Regelmäßiges Sicherheits-Patchen
* Auditprotokollierung und -überwachung

Lesen Sie die [Checkliste zur Sicherheitskonfiguration](https://experienceleague.adobe.com/de/docs/campaign-classic/using/installing-campaign-classic/security-privacy/get-started-security-privacy){target="_blank"}, um zu erfahren, welche Schlüsselelemente geprüft werden müssen, um eine sichere Konfiguration für On-Premise-Bereitstellungen zu gewährleisten.

### Wie lösche ich den Cache der Client-Konsole? {#how-do-i-clear-console-cache}

Durch Löschen des Caches der Campaign-Client-Konsole werden viele gängige Anzeige- und Funktionsprobleme behoben. Der Cache speichert lokale Konfigurationsdateien, die gelegentlich beschädigt oder veraltet sein können.

**Wann der Cache gelöscht werden soll:**

* Neue Branding-Elemente werden nicht korrekt angezeigt
* Export-/Importfunktionen schlagen unerwartet fehl
* Elemente der Benutzeroberfläche werden nach Konfigurationsänderungen nicht aktualisiert
* Leistungsprobleme oder langsame Konsolenreaktion
* Nach der Aktualisierung auf eine neue Version der Client-Konsole

**Löschen des Cache:**

1. **Soft-Cache löschen (zuerst versuchen):**
   * Öffnen der Campaign-Client-Konsole
   * Zum Menü **[!UICONTROL Datei]** wechseln
   * Wählen **[!UICONTROL Löschen des lokalen Cache…]**
   * Bestätigen der Aktion bei Aufforderung
   * Starten Sie die Client-Konsole neu

2. **Hard Cache Clear (wenn das Problem nicht durch Soft-Clear behoben werden kann):**
   * Soft Cache zuerst löschen
   * Abmelden und Client-Konsole vollständig schließen
   * Navigieren Sie zu:
      * Windows 7/10: `C:\Users\<Username>\AppData\Roaming\Neolane\NL_5\`
      * Windows XP: `C:\Documents and Settings\<Username>\Application Data\Neolane\NL_5\`
   * Löschen Sie alle XML-Dateien mit dem Namen `nlclient-config-<alphanumerical value>.xml` und die zugehörigen Ordner
   * **Wichtig:** Löschen Sie `nlclient_cnx.xml` Datei NICHT
   * Client-Konsole neu starten

Weitere Informationen finden Sie in [Dokumentation zur Campaign-Client-Konsole](../../platform/using/launching-adobe-campaign.md).

## Hilfe wird abgerufen {#getting-help}

### Wo finde ich weitere Informationen zu Campaign Classic v7? {#where-to-find-more-info-v7}

**Dokumentation und Ressourcen:**

* [Campaign Classic v7-](https://experienceleague.adobe.com/docs/campaign-classic/using/campaign-classic-home.html?lang=de){target="_blank"} - Vollständige Dokumentation
* [Versionshinweise zu Campaign Classic v7](../../rn/using/latest-release.md) - aktuelle Versionsinformationen
* [Campaign Classic-Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md) - Unterstützte Systeme und Versionen
* [Campaign Classic-](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=de){target="_blank"} - Video-Tutorials

**Für häufige Fragen zu Campaign:**

Weitere Informationen finden Sie in den [**häufig gestellten Fragen zu**](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}Campaign v8“, die ausführliche Antworten zu folgenden Themen enthalten:

* Erste Schritte mit Campaign
* Profile und Zielgruppen
* Nachrichtendesign und -versand
* Workflows und Automatisierung
* Reporting und Analysen
* Einstellungen und Konfiguration der Kampagne
* Ressourcen für Entwickler
* Datenschutz und Compliance

**Community und Unterstützung:**

* [Campaign-Community-Foren](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic/ct-p/adobe-campaign-classic-community?profile.language=de){target="_blank"}
* [Adobe-Unterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}
* [Control Panel (gehostete Kunden)](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=de){target="_blank"}

### Sollte ich von Campaign Classic v7 zu Campaign v8 migrieren? {#should-i-migrate-to-v8}

Campaign v8 ist die strategische Plattform von Adobe, die sich ideal für Unternehmen eignet, die Kampagnen mit hohem Volumen, eine moderne Web-Benutzeroberfläche, Cloud-native Vorteile und langfristigen Support benötigen. Campaign Classic v7 wird in den nächsten Jahren das Ende der Unterstützung erreichen.

**Ziehen Sie die Migration zu Campaign v8 in Betracht, wenn Sie:**

* Bewältigung großer Datenmengen oder Erlebnis-Performance-Probleme
* Möchten Sie den IT-Overhead und die Infrastrukturverwaltung reduzieren (v8 ist nur Managed Cloud Services)
* Moderne Benutzeroberfläche und Adobe Experience Platform-Integration erforderlich
* Zukunftssichere Technologie mit automatischen Updates
* befinden sich derzeit auf gehosteten/verwalteten Diensten (einfacherer Migrationspfad)

**Wichtige Überlegungen:**

* Campaign v8 ist ausschließlich als Managed Cloud Services verfügbar (keine On-Premise-/Hybrid-Optionen)
* Erfordert Planung für die Migration von Anpassungen und Integrationen
* Die FFDA-Architektur bietet Leistung, erfordert jedoch einige Workflow-/API-Anpassungen

**Nächste Schritte:** Wenden Sie sich an den Adobe-Support, um die Migrationsbereitschaft zu bewerten und auf die Migrationstools zuzugreifen.

Mehr dazu:

* [Übersicht über Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html?lang=de){target="_blank"}
* [Wechsel von Campaign Classic v7 zu v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/v7-to-v8.html){target="_blank"}
* [Umfassende häufig gestellte Fragen zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}

**Ausführliche Antworten auf häufig gestellte Fragen zu Campaign zu Workflows, Sendungen, Audiences, Reporting, Personalisierung und mehr finden** in den häufig gestellten Fragen zu [Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}.

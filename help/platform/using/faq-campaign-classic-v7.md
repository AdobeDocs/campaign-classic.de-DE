---
product: campaign
title: Häufig gestellte Fragen zu Campaign Classic
description: Spezifische Fragen zur Architektur, Bereitstellung und zu den Funktionen von Adobe Campaign Classic v7
feature: Overview, Troubleshooting
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
source-git-commit: 295e3596d9291cbcc55e2d264309141526c3806b
workflow-type: ht
source-wordcount: '1535'
ht-degree: 100%

---

# Häufig gestellte Fragen zu Campaign Classic v7 {#campaign-classic-v7-faq}

In diesen häufig gestellten Fragen werden spezifische Fragen zur Architektur von Adobe Campaign Classic v7, zu Bereitstellungsmodellen und zu v7-spezifischen Funktionen behandelt.

**Umfassende Antworten auf häufig gestellte Fragen zu Campaign** (Workflows, Sendungen, Zielgruppen, Berichte, Personalisierung usw.) finden Sie in der [**ausführlichen Sammlung häufig gestellter Fragen zu Campaign v8**](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html?lang=de){target="_blank"}, die detaillierte Antworten nach Thema gruppiert enthalten.

## Architektur und Bereitstellung von Campaign Classic v7 {#v7-architecture}

### Welche Hosting-Modelle sind in Campaign Classic v7 verfügbar? {#what-are-the-hosting-models-available-in-campaign-classic-v7}

Adobe Campaign Classic v7 bietet drei Bereitstellungsmodelle:

* **Gehostet (Managed Services)**: Vollständig von Adobe auf Adobe-Infrastruktur verwaltet 
* **On-Premise**: In Ihrer eigenen Infrastruktur installiert und verwaltet
* **Hybrid**: Mid-Sourcing-Architektur mit einer Mischung aus Cloud- und On-Premise-Komponenten

Jedes Bereitstellungsmodell verfügt über verschiedene Funktionen und Management-Aufgaben. Die Verfügbarkeit von Modulen, Optionen und Konfigurationen hängt von Ihrem Bereitstellungstyp ab.

[Hier erfahren Sie mehr](../../installation/using/hosting-models.md) über Hosting-Modelle und ihre Unterschiede.

**Hinweis:** Campaign v8 ist ausschließlich als Managed Cloud Services verfügbar. [Erfahren Sie mehr zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html?lang=de){target="_blank"}.

### Was sind die Unterschiede zwischen der On-Premise- und der gehosteten Version? {#what-are-the-differences-when-working-on-premise-vs-in-a-hosted-environment}

Adobe Campaign Classic v7 verfügt über eine Reihe von Modulen und Optionen. Die Verfügbarkeit dieser Module und ihre Konfiguration können von der [Art der Bereitstellung](../../installation/using/hosting-models.md) Ihrer Installation abhängen: gehostet (Managed Services), hybrid oder On-Premise.

Hauptunterschiede:

* **On-Premise**: Vollständige Kontrolle über Installation, Infrastruktur und Konfiguration. Erfordert interne IT-Ressourcen für Wartung, Upgrades und Sicherheit.
* **Hosted/Managed Services**: Infrastruktur und Wartung werden von Adobe verwaltet. Automatische Upgrades und erhöhte Sicherheit. Begrenzter direkter Server-Zugriff.
* **Hybrid**: Kombiniert Vorteile beider Modelle. Von Adobe gehostete Marketing-Instanz, Ausführung/Mid-Sourcing separat verwaltet.

[Klicken Sie hier für die vollständige Funktionsmatrix](../../installation/using/capability-matrix.md).

### Wie migriere ich von On-Premise/Hybrid zu Adobe Managed Services? {#how-do-i-migrate-from-on-premise-hybrid-to-adobe-managed-services}

Die Migration zu Adobe Managed Services bietet mehr Skalierbarkeit und Sicherheit und einen geringeren IT-Overhead. Häufig ist dies ein Sprungbrett vor der Umstellung auf Campaign v8.

**Wichtigste Punkte:**

* Kein automatisiertes Migrationswerkzeug verfügbar, manuelle Planung und Ausführung erforderlich
* Adobe Professional Services-Support wird dringend empfohlen
* Zu den Vorteilen gehören Cloud-Infrastruktur, automatische Sicherheits-Patches, Experten-Support und der einfachere Pfad zu v8
* Die Migration erfordert die gebührende Sorgfalt, Umgebungsprüfung, Datenbereinigung, Staging-Migration und Produktionsumstellung

**Erste Schritte:** Wenden Sie sich an Ihre Adobe-Support-Fachkraft, die Ihre Umgebung bewertet und einen detaillierten Migrationsplan mit Adobe Professional Services erstellt.

Erfahren Sie mehr zur [Migration zu Managed Services](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic-blogs/migrate-your-adobe-campaign-v7-onprem-hybrid-environment-to/ba-p/681605){target="_blank"}.

## Build-Upgrades (Campaign Classic v7) {#build-upgrades-v7}

### Was ist ein Build-Upgrade in Campaign Classic v7? {#what-is-a-build-upgrade-v7}

Bei einem Build-Upgrade wird die Adobe Campaign Classic v7-Software auf die aktuelle, sichere Build-Nummer aktualisiert, wobei die Versionsnummer unverändert bleibt. Beispiel: Campaign Classic v7 Build 9026 auf Campaign v7 Build 9032.

Adobe Campaign wird regelmäßig aktualisiert. Kleinere Versionen werden mit neuen Funktionen, Verbesserungen und Fehlerbehebungen veröffentlicht. Darüber hinaus werden regelmäßig Builds mit kumulativen Fehlerbehebungen veröffentlicht.

Weitere Informationen finden Sie in [diesem Abschnitt](../../rn/using/rn-overview.md).

### Wie kann ich Campaign Classic v7 auf die neuste Version aktualisieren? {#how-can-i-upgrade-campaign-classic-v7}

Auch Adobe Campaign Classic enthält eine Reihe von Technologien zur Erzielung von Mehrwert. Diese Kombination von Technologien erfordert eine regelmäßige Aktualisierung Ihrer Instanzen von Campaign Classic v7, um sicherzustellen, dass Sie die jeweils aktuellen Versionen verwenden und über maximale Sicherheit, Stabilität und Leistung verfügen.

**Für gehostete Kundschaft:** Sie profitieren automatisch von einer jährlichen Campaign-Aktualisierung auf die neueste stabile Version. Adobe verwaltet den Upgrade-Prozess und koordiniert den Zeitablauf mit Ihnen.

**Für On-Premise-/Hybrid-Kundschaft** Sie sind für die Durchführung von Upgrades verantwortlich. Adobe empfiehlt dringend, mindestens einmal pro Jahr ein Upgrade durchzuführen.

[Lesen Sie diesen Abschnitt](../../production/using/build-upgrade.md), um zu erfahren, wie Sie Ihre Umgebung aktualisieren können, und konsultieren Sie die [häufig gestellten Fragen zu Build-Upgrades](../../platform/using/faq-build-upgrade.md), wenn Sie weitere Fragen speziell zu diesem Thema haben.

### Was ist die aktuelle Version von Adobe Campaign Classic v7? {#what-is-the-latest-version-v7}

Die aktuelle Version von Campaign Classic v7, einschließlich neuer Funktionen und der Dokumentation, wird in den [Versionshinweisen](../../rn/using/latest-release.md) näher beschrieben.

### Woher weiß ich, welche Version von Campaign Classic v7 ich verwende? {#how-do-i-know-which-version-v7}

Ihre Version und Build-Nummer können Sie in der Adobe Campaign-Client-Konsole über das Menü **[!UICONTROL Hilfe > Versionsinformationen…]** abrufen. Das Feld **[!UICONTROL Versionsinformationen]** enthält Details zur Version und zum Build der Client-Konsole und des Servers.

Weitere Informationen finden Sie in [diesem Abschnitt](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

### Ist ein Build-Upgrade dasselbe wie ein Versions-Upgrade? {#is-build-upgrade-same-as-version-upgrade}

Nein. Ein Build-Upgrade ist eine schrittweise Aktualisierung innerhalb einer Version. Ein Upgrade einer Version ist hingegen der Wechsel von einer Version zu einer anderen. Build-Upgrades sind unkompliziert und erfordern normalerweise keine Änderungen an der Architektur, den technischen Gegebenheiten oder dem Datenmodell.

Versions-Upgrades (z. B. von v7 auf v8) sind in der Regel mit erheblichen technischen Änderungen verbunden und erfordern je nach Ihren Anpassungen möglicherweise Konfigurationsänderungen oder eine teilweise Neuimplementierung.

## Campaign Classic v7-Konfiguration {#v7-configuration}

### Kann ich die Sprache der Benutzeroberfläche von Campaign Classic v7 ändern? {#can-i-change-language-v7}

Die Sprache von Campaign Classic v7 wird zum Zeitpunkt der Instanzerstellung ausgewählt. **Anschließend kann sie nicht mehr geändert werden.**

Die Benutzeroberfläche von Adobe Campaign v7 ist in vier Sprachen verfügbar: Deutsch, Englisch, Französisch und Japanisch. Für die Client-Konsole und den Server muss dieselbe Sprache eingestellt werden. Jede Campaign Classic v7-Instanz kann nur in einer einzigen Sprache ausgeführt werden.

Für Englisch können Sie bei der Installation von Campaign v7 entweder amerikanisches oder britisches Englisch auswählen: Sie unterscheiden sich in den Formaten von Datum und Uhrzeit.

[Weitere Informationen finden Sie in diesem Abschnitt](../../installation/using/creating-an-instance-and-logging-on.md).

**Hinweis:** Die Web-Benutzeroberfläche von Campaign v8 ermöglicht es Benutzenden, die Sprache der Benutzeroberfläche unabhängig von anderen Komponenten zu ändern. [Weitere Informationen](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/connect.html?lang=de#language-pref){target="_blank"}.

### Wie kann ich Sicherheitszonen in Campaign Classic v7 konfigurieren? {#how-can-i-configure-security-zones-v7}

Die Konfiguration der VPN-Sicherheitszone in Adobe Campaign Classic v7 kann über die Self-Service-Benutzeroberfläche durch die oder den Admin erfolgen. Dies ist vor allem für On-Premise- und Hybridbereitstellungen relevant.

Lesen Sie [diesen Abschnitt](../../installation/using/security-zones.md), um mehr über Sicherheitszonen in Campaign v7 zu erfahren.

[Hier erfahren Sie mehr](https://helpx.adobe.com/de/campaign/kb/configuring-security-zones-self-service.html){target="_blank"} über die Self-Service-Benutzeroberfläche für Sicherheitszonen.

**Hinweis:** Gehostete/Managed Services-Kundschaft sollte sich für die Konfiguration von Sicherheitszonen an Adobe wenden.

### Kann Adobe Campaign Classic v7 mit LDAP integriert werden? {#can-campaign-classic-integrate-with-ldap}

Ja. **On-Premise/Hybrid-Kundschaft** kann Campaign Classic v7 für zentralisierte Authentifizierung und Benutzerverwaltung in ihr LDAP-Verzeichnis integrieren.

Diese Integration ermöglicht Folgendes:

* Benutzende können sich über Ihr Unternehmens-LDAP-Verzeichnis authentifizieren
* Zentralisierte Benutzer- und Rechteverwaltung
* Automatische Synchronisierung von Benutzergruppen und Berechtigungen
* Single Sign-On-Funktionen

[Hier erfahren Sie](../../installation/using/connecting-through-ldap.md), wie Sie die LDAP-Integration in Campaign Classic v7 einrichten.

**Hinweis:** LDAP-Integration ist für On-Premise- und Hybridbereitstellungen verfügbar. Gehostete Kundinnen und Kunden verwenden Adobe IMS zur Authentifizierung.

### Was sind die Best Practices für Sicherheit bei On-Premise-Bereitstellungen? {#security-best-practices-on-premise}

On-Premise- und Hybridbereitstellungen erfordern im Vergleich zu gehosteten Umgebungen eine zusätzliche Sicherheitskonfiguration und Absicherung.

**Wichtige Sicherheitsbereiche:**

* Netzwerksicherheit und Firewall-Konfiguration
* Datenbankzugriff und -sicherheit
* Betriebssystemabsicherung
* Dateiberechtigungen und Zugriffssteuerungen
* Konfiguration von Sicherheitszonen
* Verschlüsselung (Daten im Ruhezustand und bei der Übertragung)
* Benutzerzugriffsverwaltung
* Regelmäßige Sicherheits-Patches
* Audit-Protokollierung und -Monitoring

Lesen Sie die [Checkliste zur Sicherheitskonfiguration](https://experienceleague.adobe.com/de/docs/campaign-classic/using/installing-campaign-classic/security-privacy/get-started-security-privacy){target="_blank"}, um zu erfahren, welche wichtigen Elemente geprüft werden müssen, um eine sichere Konfiguration für On-Premise-Bereitstellungen zu gewährleisten.

### Wie leere ich den Cache der Client-Konsole? {#how-do-i-clear-console-cache}

Durch Leeren des Cache der Campaign-Client-Konsole werden viele gängige Anzeige- und Funktionsprobleme behoben. Der Cache speichert lokale Konfigurationsdateien, die gelegentlich beschädigt oder veraltet sein können.

**In folgenden Fällen sollte der Cache geleert werden:**

* Neue Branding-Elemente werden nicht korrekt angezeigt
* Export-/Importfunktionen schlagen unerwartet fehl
* Elemente der Benutzeroberfläche werden nach Konfigurationsänderungen nicht aktualisiert
* Leistungsprobleme oder langsame Konsolenreaktion
* Nach dem Upgrade auf eine neue Version der Client-Konsole

**So leeren Sie den Cache:**

1. **Leeren des Soft-Cache (zuerst versuchen):**
   * Öffnen Sie die Campaign-Client-Konsole
   * Öffnen Sie das Menü **[!UICONTROL Datei]**
   * Wählen Sie **[!UICONTROL Lokalen Cache leeren…]** aus
   * Bestätigen Sie die Aktion bei Aufforderung
   * Starten Sie die Client-Konsole neu

2. **Leeren des Hard-Cache (wenn das Problem nicht durch Leeren des Soft-Cache behoben werden kann):**
   * Leeren Sie zuerst den Soft-Cache
   * Melden Sie sich ab und schließen Sie die Client-Konsole vollständig
   * Navigieren Sie zu:
      * Windows 7/10: `C:\Users\<Username>\AppData\Roaming\Neolane\NL_5\`
      * Windows XP: `C:\Documents and Settings\<Username>\Application Data\Neolane\NL_5\`
   * Löschen Sie alle XML-Dateien mit dem Namen `nlclient-config-<alphanumerical value>.xml` und die zugehörigen Ordner
   * **Wichtig:** Löschen Sie NICHT die Datei `nlclient_cnx.xml`
   * Starten Sie die Client-Konsole neu

Weitere Informationen finden Sie in der [Dokumentation zur Campaign-Client-Konsole](../../platform/using/launching-adobe-campaign.md).

## Anfordern von Hilfe {#getting-help}

### Wo finde ich weitere Informationen zu Campaign Classic v7? {#where-to-find-more-info-v7}

**Dokumentation und Ressourcen:**

* [Dokumentation zu Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/campaign-classic-home.html?lang=de){target="_blank"} – Vollständige Dokumentation
* [Versionshinweise zu Campaign Classic v7](../../rn/using/latest-release.md) – Aktuelle Versionsinformationen
* [Campaign Classic-Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md) – Unterstützte Systeme und Versionen
* [Campaign Classic-Tutorials](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=de){target="_blank"} – Video-Tutorials

**Für häufige Fragen zu Campaign:**

In der [**ausführlichen Sammlung häufig gestellter Fragen zu Campaign v8**](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html?lang=de){target="_blank"} finden Sie detaillierte Antworten zu folgenden Themen:

* Erste Schritte mit Campaign
* Profile und Zielgruppen
* Design und Versand von Nachrichten
* Workflows und Automatisierung
* Reporting und Analysen
* Campaign-Einstellungen und -Konfiguration
* Entwicklerressourcen
* Datenschutz und Compliance

**Community und Support:**

* [Campaign-Community-Foren](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic/ct-p/adobe-campaign-classic-community){target="_blank"}
* [Adobe-Support](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}
* [Control Panel (gehostete Kundschaft)](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=de){target="_blank"}

### Soll ich von Campaign Classic v7 zu Campaign v8 migrieren? {#should-i-migrate-to-v8}

Campaign v8 ist die strategische Plattform von Adobe, die sich ideal für Unternehmen eignet, die Kampagnen mit hohem Volumen, eine moderne Web-Benutzeroberfläche, Cloud-native Vorteile und langfristigen Support benötigen. Der Support für Campaign Classic v7 wird in den nächsten Jahren enden.

**Erwägen Sie die Migration zu Campaign v8 in folgenden Fällen:**

* Sie verarbeiten große Datenmengen oder es treten Leistungsprobleme auf
* Sie möchten den IT-Overhead und die Infrastrukturverwaltung reduzieren (v8 hat ausschließlich das Managed Cloud Services-Modell)
* Sie brauchen eine moderne Benutzeroberfläche und Adobe Experience Platform-Integration
* Sie möchten zukunftssichere Technologie mit automatischen Updates
* Sie arbeiten bereits mit einem gehosteten/Managed Services-Modell (einfacherer Migrationspfad)

**Wichtige Überlegungen:**

* Campaign v8 ist ausschließlich als Managed Cloud Services-Modell verfügbar (keine On-Premise-/Hybrid-Optionen)
* Für die Migration von Anpassungen und Integrationen ist Planung erforderlich
* Die FFDA-Architektur bietet Leistung, erfordert jedoch einige Anpassungen bei Workflows/APIs

**Nächste Schritte:** Wenden Sie sich an den Adobe-Support, um die Migrationsbereitschaft zu bewerten und auf die Migrationswerkzeuge zuzugreifen.

Mehr dazu:

* [Campaign v8 – Überblick](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html?lang=de){target="_blank"}
* [Wechseln von Campaign Classic v7 zu v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/v7-to-v8.html?lang=de){target="_blank"}
* [Ausführliche Sammlung häufig gestellter Fragen zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html?lang=de){target="_blank"}

**Ausführliche Antworten auf häufig gestellte Fragen zu Campaign bezüglich Workflows, Sendungen, Zielgruppen, Berichten, Personalisierung und mehr** finden Sie in der [ausführlichen Sammlung häufig gestellter Fragen zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html?lang=de){target="_blank"}.

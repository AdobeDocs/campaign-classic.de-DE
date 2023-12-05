---
title: Migrieren von Campaign-Benutzenden zum Adobe Identity Management System (IMS)
description: Erfahren Sie, wie Sie Campaign-Benutzende zum Adobe Identity Management System (IMS) migrieren
source-git-commit: 18166dd389847d6b844ed478e19c42e457abeb80
workflow-type: tm+mt
source-wordcount: '1153'
ht-degree: 40%

---

# Migrieren von Campaign-Benutzenden zum Adobe Identity Management System (IMS) {#migrate-users-to-ims}

Im Rahmen der Bemühungen, die Sicherheit und den Authentifizierungsprozess zu verbessern, empfiehlt Adobe Campaign dringend, den Authentifizierungsmodus für Endbenutzer vom nativen Login-/Passwort-Authentifizierungs-Modus zum Adobe Identity Management-System (IMS) zu migrieren. Alle Betreiber sollten [Adobe Identity Management System (IMS)](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"} , um eine Verbindung mit Campaign herzustellen.

Beachten Sie, dass in Campaign v8 die Verbindung mit Benutzer/Kennwort (auch als native Authentifizierung bezeichnet) nicht mehr zulässig ist. **Adobe empfiehlt, diese Migration in Campaign v7.3.5 durchzuführen, um eine reibungslose Migration zu Campaign v8 zu ermöglichen.**

In diesem Artikel werden die Schritte beschrieben, die zum Migrieren einer technischen Benutzerin bzw. eines technischen Benutzers zu einem technischen Konto in der Adobe Developer Console erforderlich sind.

## Was hat sich geändert?{#move-to-ims-changes}

Mit Campaign Classic können alle normalen Benutzer über das Adobe Identity Management System (IMS) bereits über ihre Adobe ID eine Verbindung zur Adobe Campaign-Clientkonsole herstellen. Benutzer-/Kennwortverbindungen sind jedoch weiterhin verfügbar. Dies ist ab Campaign v8 nicht mehr zulässig.

Darüber hinaus ruft die Adobe Campaign-Client-Anwendung zur Verbesserung der Sicherheit und des Authentifizierungsprozesses die Campaign-APIs jetzt direkt über das technische IMS-Konto-Token auf. Die Migration für technische Benutzende wird in einem speziellen Artikel beschrieben, der auf [dieser Seite](ims-migration.md) zu finden ist.

Diese Änderung ist bereits auf Campaign Classic v7 anwendbar und wird **mandatory** , um zu Campaign v8 zu wechseln.

## Sind Sie betroffen?{#migrate-ims-impacts}

Dieses Verfahren gilt für alle Campaign-Benutzer, die noch keine Verbindung zu Campaign mit ihrer Adobe ID herstellen.

Wenn Benutzende Ihrer Organisation über ihr Login/Kennwort eine Verbindung zur Campaign-Client-Konsole herstellen (auch bekannt als nativer Authentifizierung), sind Sie betroffen und sollten diese Operatoren wie unten beschrieben zu Adobe IMS migrieren.

Die Migration zum [Adobe Identity Management System (IMS)](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"} ist ein Sicherheitskriterium, um Ihre Umgebungen sicher und standardisiert zu gestalten, da die meisten anderen Adobe Experience Cloud-Lösungen und -Anwendungen bereits auf IMS laufen.

## Wie migriert man gehostete und Managed Services-Umgebungen? {#ims-migration-procedure}

### Voraussetzungen {#ims-migration-prerequisites}

Bevor Sie mit dem Migrationsprozess beginnen, müssen Sie sich an Ihren Adobe Transition Manager (für Managed Services-Kunden) oder an die Adobe-Kundenunterstützung (für andere gehostete Kunden) wenden, damit Adobe-Techniker Ihre bestehenden Benutzergruppen und spezifischen Berechtigungen auf Adobe Identity Management System (IMS) migrieren können.

### Die wichtigsten Schritte {#ims-migration-steps}

Die wichtigsten Schritte für diese Migration sind unten aufgeführt:

1. Adobe aktualisiert Ihre Umgebungen auf Campaign v7.3.5.
1. Nach dem Upgrade können Sie weiterhin neue Benutzende mit beiden Methoden erstellen, als native Benutzerin bzw. nativen Benutzer oder mit IMS.
1. Ihr interner Campaign-Administrator muss allen nativen Benutzern in der Campaign-Clientkonsole eindeutige E-Mails hinzufügen und nach Abschluss dieses Vorgangs Ihrem Adobe-Support-Mitarbeiter/Ihrer Kundenunterstützung bestätigen.  Dieser Schritt wird in [diesem Abschnitt](#ims-migration-id) beschrieben.
1. Arbeiten Sie mit Ihrem Adobe-Support-Mitarbeiter/Kundendienst zusammen, um ein Datum für Adobe zu sichern, an dem Sie die automatisierte Migration für Ihre nicht-technischen Anwender (Benutzer) und Produktprofile durchführen können. Für diesen Schritt ist ein Stundenfenster ohne Ausfallzeiten für einen Ihrer Dienste erforderlich.
1. Ihre internen Campaign-Admins validieren diese Änderungen und geben sie frei. Nach dieser Migration dürfen Sie keinen weiteren Benutzenden mehr erstellen, die sich mit deren Login und Passwort authentifizieren.

Sie können Ihren/Ihre technischen Benutzer auch zur Adobe Developer Console migrieren, wie im Abschnitt [diese Technote](ims-migration.md).

Bestätigen Sie nach Abschluss dieser Migration Ihren Adobe Transition Manager (für Managed Services-Benutzer) oder die Adobe-Kundenunterstützung (für gehostete Kunden). Adobe markiert dann die Migration als abgeschlossen. Ihre Umgebung ist dann gesichert und standardisiert.


## Migrieren von Hybrid- und On-Premise-Umgebungen {#ims-migration-procedure-on-prem}

Die wichtigsten Schritte für diese Migration sind unten aufgeführt:

1. Aktualisieren Sie Ihre Umgebungen auf Campaign v7.3.5.
1. Nach dem Upgrade können Sie weiterhin neue Benutzende mit beiden Methoden erstellen, als native Benutzerin bzw. nativen Benutzer oder mit IMS.
1. Ihr interner Campaign-Administrator muss Adobe IMS wie im Abschnitt [diesem Abschnitt](../../integrations/using/configuring-ims.md).
1. Fügen Sie dann allen nativen Benutzern eindeutige E-Mails in der Campaign-Clientkonsole hinzu. Dieser Schritt wird in [diesem Abschnitt](#ims-migration-id) beschrieben.
1. Erstellen Sie Benutzer und Produktprofile in Adobe Admin Console, wie im Abschnitt [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/manage-permissions.html){target="_blank"}.
1. Aktivieren Sie die **Verbindung mit Adobe ID herstellen** für alle Operatoren.
1. Implementieren Sie Adobe IMS für Ihre Verbindung, wie im Abschnitt [diese Seite](../../integrations/using/implementing-ims.md).

Sie können Ihren/Ihre technischen Benutzer auch zur Adobe Developer Console migrieren, wie im Abschnitt [diese Technote](ims-migration.md).


## Häufig gestellte Fragen {#ims-migration-faq}

### Wann kann ich die Migration starten? {#ims-migration-start}

Eine Empfehlung für die Migration auf [Adobe Identity Management System (IMS)](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"} ist, Ihre Umgebung auf Campaign Classic v7.3.5 zu aktualisieren.

Sie können die IMS-Migration in Ihrer Staging-Umgebung starten, nachdem sie auf Campaign Classic v7.3.5 aktualisiert wurde, und entsprechend für die Produktionsumgebung planen.

### Was passiert nach der Build-Aktualisierung auf Campaign Classic v7.3.5? {#ims-migration-after-upgrade}

Nachdem Ihre Umgebungen auf Campaign Classic v7.3.5 aktualisiert wurden, können Sie den Übergang zu [Adobe Identity Management System (IMS)](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"}.

### Wann ist die Migration abgeschlossen? {#ims-migration-end}

Sobald die Migration der Endbenutzer und die technische Benutzermigration zum Adobe Identity Management System (IMS) abgeschlossen sind, müssen Sie sich an Ihren Adobe-Support wenden, damit Adobe Ihre Migration als abgeschlossen kennzeichnen kann.

### Wie werden nach der Migration Benutzende erstellt? {#ims-migration-native}

Adobe empfiehlt, nach der Aktualisierung auf Campaign Classic v7.3.5 nur IMS-Benutzer zu erstellen.

Als Campaign-Admin können Sie den Benutzenden Ihrer Organisation über die Adobe Admin Console und die Campaign Client-Konsole Berechtigungen erteilen. Benutzende melden sich mit ihrer Adobe ID bei Adobe Campaign an. Erfahren Sie, wie Sie Berechtigungen mit IMS einrichten in [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=de){target="_blank"}.

### Wie kann ich E-Mails für aktuelle native Benutzende hinzufügen? {#ims-migration-id}

Als Campaign-Admin müssen Sie allen nativen Benutzenden über die Client-Konsole E-Mail-IDs hinzufügen. Gehen Sie dazu wie folgt vor:

1. Stellen Sie eine Verbindung zur Client-Konsole her und wechseln Sie zu **Administration > Verwaltung der Zugriffsberechtigungen > Benutzende**.
1. Wählen Sie in der Benutzerliste die zu aktualisierenden Benutzenden aus.
1. Geben Sie die E-Mail-Adresse der jeweiligen Personen im Abschnitt **Kontaktmöglichkeiten** des Benutzerformulars ein.
1. Speichern Sie Ihre Änderungen.

<!--You can also import a CSV file to update all your operator profiles with their email.-->


### Wie meldet man sich über IMS bei Campaign an? {#ims-migration-log}

In [diesem Abschnitt](../../integrations/using/implementing-ims.md) erfahren Sie, wie Sie eine Verbindung zu Campaign mit Ihrer Adobe ID herstellen.

### Wird es während dieser Migration zu Ausfallzeiten kommen? {#ims-migration-downtime}

Für gehostete und Managed Services-Kunden ist zum Abschließen der Migration (Migrieren von Benutzern und Produktprofilen) ein einstündiges Adobe-Fenster ohne Ausfallzeiten zu einer Ihrer Instanzen (Workflows usw.) erforderlich.

Während dieses Zeitrahmens müssen sich alle Campaign-Benutzenden abmelden und sich nach Abschluss der Migration zu IMS erneut mit ihrer Adobe ID anmelden.

Adobe empfiehlt dringend, dass alle Benutzenden während des Migrationsfensters abgemeldet sind.

### Benutzer in meinem Unternehmen verwenden IMS bereits. Muss ich trotzdem IMS-Migrationen durchführen?{#ims-migration-needed}

Diese Migration umfasst zwei Aspekte: die Migration von Endbenutzern (plus Produktprofile) und die Migration technischer Benutzer (in APIs in Ihrem benutzerspezifischen Code verwendet).

Wenn alle Ihre Benutzer (Campaign-Benutzer) IMS verwenden, müssen Sie sich dennoch an Ihren Adobe-Support wenden, um die Migration von Produktprofilen zu planen. Sie müssen auch technische Benutzer migrieren, die Sie möglicherweise in benutzerdefiniertem Code verwendet haben. Weitere Informationen finden Sie auf [dieser Seite](ims-migration.md).

## Nützliche Links {#ims-useful-links}

* [Migration von technischen Benutzenden zur Adobe Developer Console](ims-migration.md)
* [Versionshinweise von Adobe Campaign v8](../../rn/using/latest-release.md)
* [Was ist das Adobe Identity Management System (IMS)?](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"}

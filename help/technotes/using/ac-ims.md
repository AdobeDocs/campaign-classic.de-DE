---
title: Migrieren zum Adobe Identity Management System (IMS)
description: Erfahren Sie, wie Sie Ihren Authentifizierungsprozess auf das Adobe Identity Management System (IMS) migrieren.
source-git-commit: 106f0409f452595209f0e2aa2fa187a2e04338a9
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 27%

---

# Migrieren zum Adobe Identity Management System (IMS) {#migrate-to-ims}

Im Rahmen der Bemühungen, die Sicherheit und den Authentifizierungsprozess zu verbessern, empfiehlt Adobe Campaign dringend, den Authentifizierungsmodus für Endbenutzer von der nativen Authentifizierung für Login/Passwort zu migrieren [Adobe Identity Management System (IMS)](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"}.

Darüber hinaus ruft die Adobe Campaign-Clientanwendung jetzt Campaign-APIs direkt mithilfe des Tokens für das technische IMS-Konto auf. Sie müssen Ihre technischen Benutzer zur Adobe Developer Console migrieren.

>[!CAUTION]
>
>Diese Änderung ist bereits auf Campaign Classic v7 anwendbar und wird **mandatory** , um zu Campaign v8 zu wechseln. Die native Benutzer-/Kennwortauthentifizierung ist in Campaign v8 nicht zulässig. **Adobe empfiehlt, diese Migration ab Campaign v7.3.5 durchzuführen, um eine reibungslose Migration zu Campaign v8 zu ermöglichen.**
>

## Migrationsschritte {#ims-steps}

Die Migration zum [Adobe Identity Management System (IMS)](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"} ist ein Sicherheitskriterium, um Ihre Umgebungen sicher und standardisiert zu gestalten, da die meisten anderen Adobe Experience Cloud-Lösungen und -Anwendungen bereits mit IMS laufen.

Adobe unterstützt Sie bei dieser Migration. In den folgenden Artikeln finden Sie detaillierte Kontexte und Schritt-für-Schritt-Richtlinien:

* Die Migration für die Authentifizierung von Endbenutzern wird im Abschnitt [diese Seite](migrate-users-to-ims.md).
* Die Migration zur Authentifizierung technischer Operatoren wird im Abschnitt beschrieben. [diese Seite](ims-migration.md).
* Aktivieren Sie ab Campaign v7.4.1 die Benutzeroberfläche und API-Beschränkungen, um Optionen und Funktionen zu entfernen, die für die native Authentifizierung spezifisch sind, wie im Abschnitt [diese Seite](impact-ims-migration.md).


## Mit der IMS-Migration kompatible Versionen {#ims-versions}

Voraussetzung für diese Migration ist die Aktualisierung Ihrer Umgebung auf eine der folgenden Produktversionen:

* Campaign v7.4.1 (empfohlen)
* Campaign v7.3.5
* Campaign v7.3.3.IMS
* Campaign v7.3.2.IMS

Diese Campaign-Versionen werden im Abschnitt [Versionshinweise](../../rn/using/latest-release.md) detailliert behandelt.

## Häufig gestellte Fragen {#ims-migration-faq}

### Wann kann ich die Migration starten? {#ims-migration-start}

Eine Empfehlung für die Migration auf [Adobe Identity Management System (IMS)](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"} eine Aktualisierung Ihrer Umgebung auf Campaign Classic v7.4.1 (oder eine [Kompatible Version der IMS-Migration](#ims-versions)).

Sie können die IMS-Migration in Ihrer Staging-Umgebung starten, sobald sie auf Campaign Classic v7.3.5 aktualisiert wurde, und entsprechend für die Produktionsumgebung planen.

### Was passiert nach der Build-Aktualisierung auf Campaign Classic v7.4.1? {#ims-migration-after-upgrade}

Nachdem Ihre Umgebungen auf Campaign Classic v7.4.1 (oder eine [Kompatible Version der IMS-Migration](#ims-versions)), können Sie Ihre Umstellung auf [Adobe Identity Management System (IMS)](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"}.

### Wann ist die Migration abgeschlossen? {#ims-migration-end}

Nachdem die Migration der Endbenutzer und die Migration der technischen Benutzer auf das Adobe Identity Management-System (IMS) abgeschlossen sind, müssen Sie Ihre Umgebung aktualisieren, um Optionen zu entfernen, die für die native Authentifizierung spezifisch und bei der IMS-Authentifizierung nicht mehr anwendbar sind. Dieses Update ist erst ab Campaign v7.4.1 verfügbar. [Weitere Infos](impact-ims-migration.md)



## Nützliche Links {#ims-useful-links}

* [Migration von Endbenutzern zu IMS](migrate-users-to-ims.md)
* [Migration technischer Benutzer zur Adobe Developer-Konsole](ims-migration.md)
* [Versionshinweise zu Adobe Campaign Classic v7](../../rn/using/latest-release.md)
* [Was ist das Adobe Identity Management System (IMS)?](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"}

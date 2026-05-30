---
title: Migrieren zum Adobe Identity Management System (IMS)
description: Informationen zur Migration Ihres Authentifizierungsprozesses zum Adobe Identity Management System (IMS)
exl-id: 84853dbe-8b6f-4875-b29a-c1b755423a3c
TQID: https://experienceleague.adobe.com/DKwv-rLrgm0ce9cycT1QMtBgQP-2pnMNhqHlH1xJWvo
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 479
ht-degree: 72%

---

# Migrieren zum Adobe Identity Management System (IMS) {#migrate-to-ims}

Im Rahmen der Bemühungen um eine Verbesserung des Sicherheits- und Authentifizierungsprozesses empfiehlt Adobe Campaign dringend, den Authentifizierungsmodus für Endbenutzer von der nativen Anmelde-/Kennwortauthentifizierung zum [Adobe Identity Management System (IMS) zu &#x200B;](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"}.

Darüber hinaus ruft die Adobe Campaign-Client-Anwendung die Campaign-APIs jetzt direkt über das technische IMS-Konto-Token auf. Sie müssen Ihre technischen Benutzenden zur Adobe Developer Console migrieren.

>[!CAUTION]
>
>Diese Änderung ist bereits in Campaign Classic v7 möglich und wird für den Wechsel zu Campaign v8 **obligatorisch** sein. Die native Benutzer-/Passwortauthentifizierung ist in Campaign v8 nicht zulässig. **Adobe empfiehlt, diese Migration ab Campaign v7.3.5 durchzuführen, um eine reibungslose Migration zu Campaign v8 zu ermöglichen.**
>

## Migrationsschritte {#ims-steps}

Die Migration auf das [Adobe Identity Management System (IMS](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"} ist eine Sicherheitsanforderung, um Ihre Umgebungen sicher und standardisiert zu gestalten, da die meisten anderen Adobe Experience Cloud-Lösungen und -Apps bereits auf IMS installiert sind.

Adobe unterstützt Sie bei dieser Migration. In den folgenden Artikeln finden Sie detaillierten Kontext und Schritt-für-Schritt-Anweisungen:

* Die Migration für die Authentifizierung von Endbenutzenden wird auf [dieser Seite](migrate-users-to-ims.md) beschrieben.
* Die Migration zur Authentifizierung von technischen Benutzenden wird auf [dieser Seite](ims-migration.md) beschrieben.
* Aktivieren Sie ab Campaign v7.4.1 die Benutzeroberfläche und API-Einschränkungen, um die Optionen und Funktionen zu entfernen, die für die native Authentifizierung spezifisch sind, wie auf [dieser Seite](impact-ims-migration.md) beschrieben.


## Mit der IMS-Migration kompatible Versionen {#ims-versions}

Voraussetzung für diese Migration ist die Aktualisierung Ihrer Umgebung auf eine der folgenden Produktversionen:

* Campaign v7.4.1 (empfohlen)
* Campaign v7.3.5
* Campaign v7.3.3.IMS
* Campaign v7.3.2.IMS

Diese Campaign-Versionen werden in den [Versionshinweisen](../../rn/using/latest-release.md) detailliert behandelt.

## Häufig gestellte Fragen {#ims-migration-faq}

### Wann kann ich die Migration starten? {#ims-migration-start}

Eine Empfehlung für die Migration auf [Adobe Identity Management System (IMS)](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"} besteht darin, Ihre Umgebung auf Campaign Classic v7.4.1 (oder eine mit der IMS[Migration kompatible Version) &#x200B;](#ims-versions) aktualisieren.

Sie können die IMS-Migration in Ihrer Staging-Umgebung starten, sobald sie auf Campaign Classic v7.3.5 aktualisiert wurde, und entsprechend für die Produktionsumgebung planen.

### Was passiert nach einem Build-Upgrade auf Campaign Classic v7.4.1? {#ims-migration-after-upgrade}

Nachdem Ihre Umgebungen auf Campaign Classic v7.4.1 (oder eine mit der [IMS-Migration kompatible Version](#ims-versions)) aktualisiert wurden, können Sie den Wechsel zu [Adobe Identity Management System (IMS) &#x200B;](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"}.

### Wann ist die Migration abgeschlossen? {#ims-migration-end}

Nachdem die Migration der Endbenutzenden und der technischen Benutzenden auf das Adobe Identity Management System (IMS) abgeschlossen ist, müssen Sie Ihre Umgebung aktualisieren, um die Optionen zu entfernen, die für die native Authentifizierung spezifisch und bei der IMS-Authentifizierung nicht mehr anwendbar sind. Dieses Update ist nur ab Campaign v7.4.1 verfügbar. [Weitere Informationen](impact-ims-migration.md)



## Nützliche Links {#ims-useful-links}

* [Migration von Endbenutzenden zu IMS](migrate-users-to-ims.md)
* [Migration von technischen Benutzenden zur Adobe Developer Console](ims-migration.md)
* [Neueste Versionshinweise zu Adobe Campaign Classic v7](../../rn/using/latest-release.md)
* [Was ist Adobe Identity Management System (IMS)?](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"}

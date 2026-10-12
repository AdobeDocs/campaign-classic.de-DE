---
title: Migrieren von Campaign-Benutzenden zum Adobe Identity Management System (IMS)
description: Erfahren Sie, wie Sie Campaign-Benutzende zum Adobe Identity Management System (IMS) migrieren
exl-id: f01948c7-b523-492d-a4e8-67f4adde5fc5
TQID: 'https://experienceleague.adobe.com/drpNkA9cj7Prid--GixHMQ48CO7ZC9qqX4w5fnTiD88'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
    internal-label: APIs
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
subfeature_v2:
  - id: efa38731-2723-4334-8d8b-a778af834835
    internal-label: Access management
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Analytics integration
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: 4bc1e76d129c6a6aa15b7e3915232043bd6f4286
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 87%
---
# Migrieren von Campaign-Benutzenden zum Adobe Identity Management System (IMS) {#migrate-users-to-ims}

Im Rahmen der Bemühungen, die Sicherheit und den Authentifizierungsprozess zu verbessern, empfiehlt Adobe Campaign dringend, den Authentifizierungsmodus für Endbenutzende von der nativen Authentifizierung mit Login/Passwort auf das Adobe Identity Management System (IMS) zu migrieren. Alle Benutzenden sollten das [Identitäts-Management-System (IMS) von Adobe](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"} implementieren, um eine Verbindung mit Campaign herzustellen.

Weitere Informationen zu dieser Migration finden Sie auf [dieser Seite](ac-ims.md).

## Was hat sich geändert? {#move-to-ims-changes}

Mit Campaign Classic können sich alle regulären Anwenderinnen und Anwender bereits mit ihrer Adobe ID über das Adobe Identity Management System (IMS) mit der Adobe Campaign Client-Konsole verbinden. Verbindungen mit Benutzername/Passwort sind jedoch noch weiterhin verfügbar. Dies ist ab Campaign v8 nicht mehr zulässig.

Darüber hinaus ruft die Adobe Campaign-Client-Anwendung zur Verbesserung der Sicherheit und des Authentifizierungsprozesses die Campaign-APIs jetzt direkt über das technische IMS-Konto-Token auf. Die Migration für technische Benutzende wird in einem speziellen Artikel beschrieben, der auf [dieser Seite](ims-migration.md) zu finden ist.

Diese Änderung ist bereits in Campaign Classic v7 möglich und wird für den Wechsel zu Campaign v8 **obligatorisch** sein.

Adobe unterstützt Sie bei dieser Migration. Im folgenden Artikel finden Sie detaillierten Kontext und Schritt-für-Schritt-Anweisungen.

## Sind Sie betroffen?{#migrate-ims-impacts}

Dieses Verfahren gilt für alle Benutzerinnen und Benutzer von Campaign, die noch keine Verbindung zu Campaign mit ihrer Adobe ID herstellen.

Wenn Benutzende Ihrer Organisation über ihr Login/Passwort eine Verbindung zur Campaign-Client-Konsole herstellen (auch bekannt als native Authentifizierung), sind Sie betroffen und sollten diese Benutzenden wie unten beschrieben zu Adobe IMS migrieren.

Die Migration zum [Identitäts-Management-System (IMS) von Adobe](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"} ist eine Sicherheitsanforderung, um Ihre Umgebungen sicher und standardisiert zu gestalten, da die meisten anderen Adobe Experience Cloud-Lösungen und -Anwendungen bereits auf IMS installiert sind.

Diese Änderung gilt ab Campaign Classic v7.4.1 (und für die neuesten [mit der IMS-Migration kompatiblen Versionen](ac-ims.md#ims-versions)) und ist **obligatorisch** für den Wechsel zu Adobe Campaign v8.

>[!IMPORTANT]
>
>**Auswirkung auf Control Panel-Zugriff**
>
>Beachten Sie, dass nach der Migration Ihrer Benutzenden zu IMS jedes Produktprofil in der Adobe Admin Console, das das Wort „admin“ im Namen enthält (z. B. „Administratoren“, „Admin“, „Admins“, „Validierungsadmin“ usw.), automatisch Zugriff auf das Control Panel von Campaign gewährt. Das Control Panel ist ein Self-Service-Tool, mit dem Sie wesentliche Änderungen an Campaign-Instanzen vornehmen können.
>
>Überprüfen Sie die Namenskonventionen der Produktprofile sorgfältig, um sicherzustellen, dass nur autorisierte Benutzende Zugriff auf das Control Panel haben. Weitere Informationen zum Verwalten von Control Panel-Berechtigungen finden Sie in der [Dokumentation zum Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=de){target="_blank"}.


## Wie wird die Migration von Hybrid- und On-Premise-Umgebungen durchgeführt? {#ims-migration-procedure-on-prem}

Die wichtigsten Schritte für diese Migration sind unten aufgeführt:

1. Aktualisieren Sie Ihre Umgebungen auf Campaign v7.4.1 (oder eine [mit der IMS-Migration kompatible Version](#ims-versions)).
1. Nach dem Upgrade können Sie weiterhin neue Benutzende mit beiden Methoden erstellen, als native Benutzerin bzw. nativen Benutzer oder mit IMS.
1. Ihre internen Campaign-Admins müssen Adobe IMS wie in [diesem Abschnitt](../../integrations/using/configuring-ims.md) beschrieben konfigurieren.
1. Fügen Sie dann allen nativen Benutzerinnen und Benutzern eindeutige E-Mails in der Campaign-Client-Konsole hinzu. Dieser Schritt wird in [diesem Abschnitt) beschrieben](https://experienceleague.adobe.com/en/docs/campaign/technotes-ac/tn-new/migrate-users-to-ims#ims-migration-id){target="_blank"} (Dokumentation zu Campaign v8).
1. Erstellen Sie Benutzende und Produktprofile in der Adobe Admin Console, wie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/manage-permissions.html?lang=de){target="_blank"} beschrieben.
1. Aktivieren Sie die Option **Verbindung mit Adobe ID** für alle Benutzenden.
1. Implementieren Sie Adobe IMS für Ihre Verbindung, wie auf [dieser Seite](../../integrations/using/implementing-ims.md) beschrieben.

Sie können auch Ihre technischen Benutzenden zur Adobe Developer Console migrieren, wie in [dieser Technote](ims-migration.md) beschrieben.

## Häufig gestellte Fragen {#ims-migration-faq}

Antworten auf häufige Fragen zur Migration (Erstellen von Benutzern nach der Migration, Hinzufügen von E-Mails für native Benutzer, Anmelden über IMS, Ausfallzeiten, Organisationen, die bereits IMS verwenden, Anzeigen des Authentifizierungstyps der Benutzer) finden Sie in der Technote zu [Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/technotes-ac/tn-new/migrate-users-to-ims#ims-migration-faq){target=_blank} (Dokumentation zu Campaign v8).

>[!MORELIKETHIS]
>
>* [Migration von technischen Benutzenden zur Adobe Developer Console](ims-migration.md)
>* [Versionshinweise zu Adobe Campaign Classic v7](../../rn/using/latest-release.md)
>* [Was ist das Identitäts-Management-System (IMS) von Adobe](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"}

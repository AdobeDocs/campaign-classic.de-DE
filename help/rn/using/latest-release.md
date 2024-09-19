---
product: campaign
title: Aktuelle Version
description: Aktuelle Versionshinweise von Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 4be5bf54362240aac1b77298b08b14d3e5542f52
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 93%

---

# Aktuelle Version {#latest-release}

Auf dieser Seite werden neue Funktionen, Verbesserungen und Fehlerbehebungen der **aktuellen Version Campaign Classic v7** aufgelistet. Jeder neue Build weist einen Status auf, der durch eine bestimmte Farbe dargestellt wird. Sie erfahren mehr über den Build-Status von Campaign Classic v7 auf [dieser Seite](rn-overview.md).

## Version 7.4.1 – Build 9383 {#release-7-4-1}

[!BADGE Allgemeine Verfügbarkeit]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=de#rn-statuses" tooltip="Allgemeine Verfügbarkeit"}

_18. Juni 2024_

### Änderungen und Verbesserungen {#release-7-4-1-changes}

* Ausgehende Campaign-Integrationen in Adobe-Lösungen und -Apps sind nun auf OAuth-Server-zu-Server-Anmeldedaten angewiesen, da die Anmeldedatenoption „Service-Konto (JWT)“ eingestellt wurde. Wenn Sie ausgehende Integrationen wie die Campaign-Analytics-Integration oder die Experience Cloud Triggers-Integration implementiert haben, müssen Sie Ihre Campaign-Umgebung auf Version 7.4.1 aktualisieren und Ihr technisches Konto vor dem 27. Januar 2025 auf OAuth migrieren. [Weitere Informationen](../../integrations/using/oauth-technical-account.md)

* Nachdem Sie [Ihre technischen Campaign- Benutzenden in die Developer Console migriert](../../technotes/using/ims-migration.md) und [für die Endbenutzer-Authentifizierung auf IMS umgestellt haben](../../technotes/using/migrate-users-to-ims.md), können Sie nun die Benutzeroberfläche und API-Einschränkungen aktivieren, um Optionen und Funktionen zu entfernen, die für die native Authentifizierung spezifisch sind. [Weitere Informationen](../../technotes/using/impact-ims-migration.md)


### Kompatibilitätsaktualisierungen {#release-7-4-1-compat}

Die [Kompatibilitätsmatrix für Adobe Campaign](compatibility-matrix.md) wurde mit Änderungen aktualisiert, die mit dieser neuen Version eingeführt wurden und unten aufgeführt sind.

* Adobe Campaign ist jetzt mit den Betriebssystemen **Microsoft Server 2022** und **RHEL 9** kompatibel.

* Adobe Campaign ist jetzt mit **Microsoft SQL Server 2022** und **Oracle 23c** als relationale Datenbank-Management-Systeme und in Federated Data Access (FDA) kompatibel.

* Adobe Campaign erfordert jetzt mindestens ein Java Development Kit (JDK) 11. Unter Windows muss das JRE verfügbar sein, wie in [diesem Abschnitt](../../installation/using/application-server.md#jdk) beschrieben.

* Das Campaign-SDK (Neolane) für mobile Anwendungen wird jetzt nicht mehr unterstützt. Sie müssen jetzt zum Adobe Experience Platform SDK wechseln. [Weitere Informationen](deprecated-features.md).

  Um die Kontinuität der Dienste sicherzustellen, ist Campaign v7.4 mit folgenden Funktionen ausgestattet:

   * ein neues Campaign SDK 1.0.27 für iOS, kompatibel mit iOS 16 und 17, und die neuesten [Anforderungen für Apple iOS-Datenschutzanfragen](https://developer.apple.com/news/?id=r1henawx){target="_blank"}.
   * ein neues Campaign SDK für Android 14.

### Sonstige Änderungen  {#release-7-4-1-other}

Ab Version 7.4.1 sind XML-Bibliotheken für RPM Linux-Pakete nicht mehr in Campaign enthalten. Als On-Premise- oder Hybrid-Kunde muss Ihr Administrator diese Bibliotheken installieren.

### Patches {#release-7-4-1-patches}

Diese Version enthält die folgenden Fehlerbehebungen:

NEO-74754, NEO-73174, NEO-72504, NEO-71534, NEO-71473, NEO-70195, NEO-69663, NEO-696 51, NEO-67620, NEO-67235, NEO-66797, NEO-64680, NEO-63706, NEO-63657, NEO-62964, NEO-6 NEO-58734, NEO-40531, NEO-36189, NEO-29592


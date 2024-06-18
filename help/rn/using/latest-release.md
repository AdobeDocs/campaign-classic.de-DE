---
product: campaign
title: Aktuelle Version
description: Aktuelle Versionshinweise von Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 18%

---

# Aktuelle Version {#latest-release}

Auf dieser Seite werden neue Funktionen, Verbesserungen und Fehlerbehebungen der **aktuellen Version Campaign Classic v7** aufgelistet. Jeder neue Build weist einen Status auf, der durch eine bestimmte Farbe dargestellt wird. Sie erfahren mehr über den Build-Status von Campaign Classic v7 auf [dieser Seite](rn-overview.md).

## Version 7.4.1 - Build XXX {#release-7-4-1}

[!BADGE Allgemeine Verfügbarkeit]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=de#rn-statuses" tooltip="Allgemeine Verfügbarkeit"}


_Mittwoch, 18. Juni 2024_

### Änderungen und Verbesserungen {#release-7-4-1-changes}

* Da die Berechtigung für das Dienstkonto (JWT) von Adobe veraltet ist, sind ausgehende Campaign-Integrationen mit Adobe-Lösungen und Apps jetzt auf OAuth-Server-zu-Server-Anmeldedaten angewiesen. Wenn Sie ausgehende Integrationen wie die Campaign-Analytics-Integration oder die Experience Cloud Trigger-Integration implementiert haben, müssen Sie Ihre Campaign-Umgebung auf Version 7.4.1 aktualisieren und Ihr technisches Konto vor dem 27. Januar 2025 auf oAuth migrieren. [Weitere Informationen](../../integrations/using/oauth-technical-account.md)

* Einmal [die technischen Campaign-Benutzer in die Developer Console migriert haben](../../technotes/using/ims-migration.md) und [zur Authentifizierung des Endbenutzers auf IMS umgestellt](../../technotes/using/migrate-users-to-ims.md)können Sie jetzt die Benutzeroberfläche und API-Beschränkungen aktivieren, um Optionen und Funktionen zu entfernen, die für die native Authentifizierung spezifisch sind. [Weitere Informationen](../../technotes/using/impact-ims-migration.md)



### Aktualisierungen zur Kompatibilität {#release-7-4-1-compat}

Die [Kompatibilitätsmatrix für Adobe Campaign](compatibility-matrix.md) wurde mit Änderungen aktualisiert, die mit dieser neuen Version eingeführt wurden und unten aufgeführt sind.

* Adobe Campaign ist jetzt kompatibel mit **Microsoft Server 2022** und **RHEL 9** als Betriebssysteme.

* Adobe Campaign ist jetzt kompatibel mit **Microsoft SQL Server 2022** und **Oracle 23c** als Relation Database Management Systems und in Federated Data Access (FDA).

* Adobe Campaign erfordert jetzt mindestens ein Java Development Kit (JDK) 11. Unter Windows muss JRE verfügbar sein, wie unter [diesem Abschnitt](../../installation/using/application-server.md#jdk).

* Das Campaign-SDK (Neolane) für mobile Anwendungen wird jetzt nicht mehr unterstützt. Sie müssen jetzt zum Adobe Experience Platform SDK wechseln. [Weitere Informationen](deprecated-features.md).

  Um die Kontinuität der Dienste sicherzustellen, ist Campaign v7.4 mit folgenden Funktionen ausgestattet:

   * ein neues Campaign SDK 1.0.27 für iOS, kompatibel mit iOS 16 und 17, und die neueste Version [Apple iOS - Datenschutzanfragen](https://developer.apple.com/news/?id=r1henawx){target="_blank"}.
   * ein neues Campaign SDK für Android 14.


### Patches  {#release-7-4-1-patches}

Diese Version enthält die folgenden Fehlerbehebungen:

NEO-74754, NEO-73174, NEO-72504, NEO-71534, NEO-71473, NEO-70195, NEO-69663, NEO-696 51, NEO-67620, NEO-67235, NEO-66797, NEO-64680, NEO-63706, NEO-63657, NEO-62964, NEO-6 NEO-58734, NEO-40531, NEO-36189, NEO-29592


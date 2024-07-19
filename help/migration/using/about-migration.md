---
product: campaign
title: Migration zu Campaign Classic
description: Erfahren Sie, wie Sie von einer früheren Campaign-Version zu Campaign Classic migrieren
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migration-overview
hide: true
hidefromtoc: true
exl-id: 3050238d-6f77-4ffa-9aef-677ab8009388
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 2%

---

# Erste Schritte mit der Migration{#about-migration}



In diesem Dokument werden die Voraussetzungen für eine Migration sowie die Schritte für eine Migration zu Adobe Campaign Classic v7 beschrieben. Schritte und optionale Einstellungen hängen von Ihrer Konfiguration ab.

Der Migrationsprozess muss mit Vorsicht durchgeführt werden, seine Auswirkungen müssen vorher umfassend berücksichtigt werden und das Verfahren muss streng durchgeführt werden. Sie darf nur von einem erfahrenen Benutzer durchgeführt werden. Wir empfehlen dringend, Kontakt mit der [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) aufzunehmen, bevor Sie mit einem Migrationsverfahren beginnen.

Die Migration muss zuvor in der Test-/Staging-Umgebung getestet werden, um sicherzustellen, dass sie reibungslos und fehlerfrei ausgeführt wird. Die Migration der Produktionsumgebung darf erst durchgeführt werden, nachdem die migrierte Testumgebung vollständig validiert wurde.

>[!NOTE]
>
>Die neuen Funktionen und Verbesserungen von Adobe Campaign v7 werden in den [Versionshinweisen](../../rn/using/latest-release.md) beschrieben.


## Voraussetzungen

* Der Migrationsprozess muss von erfahrenen Benutzern durchgeführt werden. Sie müssen von mindestens einem Datenbankexperten, einem Systemadministrator und einem Anwendungsentwickler von Adobe Campaign unterstützt werden.
* Bevor Sie mit der Migration beginnen, überprüfen Sie, ob die verwendeten Systeme und Systemkomponenten mit v7 kompatibel sind. [Weitere Informationen](../../rn/using/compatibility-matrix.md).
* Wenn Sie Adobe Campaign Cloud Messaging (Mid-Sourcing-Bereitstellung) verwenden, wenden Sie sich vor dem Start an die Adobe-Kundenunterstützung.
* Bevor Sie einen Migrationsprozess starten, müssen Sie **** Ihre Daten sichern.
* Der Migrationsprozess kann mehrere Tage in Anspruch nehmen.
* Adobe Campaign v7 ist eine sicherere Version als die vorherigen: Dies wirkt sich auf Konfigurationsrichtlinien aus, um Probleme wie Datenbeschädigung zu vermeiden und die Datenintegrität in der Datenbank zu erhalten. Als Kunde sind Sie für das Testen aller Konfigurationen verantwortlich, einschließlich Workflows.

Weitere Voraussetzungen sind auf [dieser Seite](../../migration/using/before-starting-migration.md) verfügbar.


## Modernisierte Umgebung {#modernizing-your-environment}

Die Durchführung einer Migration kann eine Chance sein, Ihre Umgebung (Datenbank-Engines, Betriebssysteme) zu aktualisieren. Adobe Campaign empfiehlt dringend, Ihre Produktionsumgebungen auf die neuesten Versionen zu aktualisieren.

>[!CAUTION]
>
>Weitere Informationen zu den von Adobe Campaign v7 unterstützten Versionen finden Sie in der [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md).

## Wichtige Migrationsschritte {#key-migration-steps}

Das allgemeine Verfahren für die Migration zu Adobe Campaign v7 wird auf [dieser Seite](../../migration/using/before-starting-migration.md) beschrieben.


## Spezifische Konfigurationen {#specific-configurations}

Die von Adobe Campaign v7 vorgenommenen Änderungen können auch bedeuten, dass Sie bestimmte spezifische Konfigurationen anpassen müssen, die in früheren Versionen entwickelt wurden. Daher kann es vor der Migration erforderlich sein, alle Ihre Konfigurationen zu prüfen: Wenden Sie sich für Unterstützung an Adobe Campaign.

Besondere Aufmerksamkeit sollte beispielsweise auf bestimmte Einstellungen für Webanwendungen, Schemaerweiterungen mit SQLdata oder natives Schema-Klonen gelegt werden. Weitere Informationen dazu finden Sie auf [dieser Seite](../../migration/using/configuring-your-platform.md).

Um auf die erhöhte Sicherheit in Adobe Campaign zu reagieren, wurden einige interne Mechanismen ebenfalls geändert: Sie müssen diese Konfigurationen entsprechend anpassen.


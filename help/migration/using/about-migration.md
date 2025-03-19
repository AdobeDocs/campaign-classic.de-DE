---
product: campaign
title: Migration zu Campaign Classic
description: Erfahren Sie, wie Sie von einer früheren Campaign-Version zu Campaign Classic migrieren.
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migration-overview
hide: true
hidefromtoc: true
exl-id: 3050238d-6f77-4ffa-9aef-677ab8009388
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 2%

---

# Erste Schritte mit der Migration{#about-migration}



In diesem Dokument werden die Voraussetzungen für eine Migration und die Schritte für eine Migration auf Adobe Campaign Classic v7 beschrieben. Die Schritte und optionalen Einstellungen hängen von Ihrer Konfiguration ab.

Der Migrationsprozess muss mit Vorsicht durchgeführt werden, seine Auswirkungen müssen zuvor umfassend berücksichtigt werden und das Verfahren muss rigoros durchgeführt werden. Sie darf nur von einem erfahrenen Benutzer durchgeführt werden. Es wird dringend empfohlen, sich vor Beginn eines Migrationsprozesses an die [](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) Adobe-Kundenunterstützung zu wenden.

Die Migration muss zuvor in der Test-/Staging-Umgebung getestet werden, um sicherzustellen, dass sie reibungslos und ohne Fehler verläuft. Die Migration der Produktionsumgebung muss erst durchgeführt werden, nachdem die migrierte Testumgebung vollständig validiert wurde.

>[!NOTE]
>
>Neue Funktionen und Verbesserungen in Adobe Campaign v7 werden in den [ Versionshinweisen ](../../rn/using/latest-release.md).


## Voraussetzungen

* Der Migrationsprozess muss von erfahrenen Benutzern durchgeführt werden. Sie benötigen mindestens einen Datenbankexperten, einen Systemadministrator und einen Anwendungsentwickler aus Adobe Campaign.
* Bevor Sie mit der Migration beginnen, überprüfen Sie, ob die verwendeten Systeme und Systemkomponenten mit v7 kompatibel sind. [Weitere Informationen](../../rn/using/compatibility-matrix.md).
* Wenn Sie Adobe Campaign Cloud Messaging (Mid-Sourcing-Bereitstellung) verwenden, wenden Sie sich vor dem Start an die Adobe-Kundenunterstützung.
* Bevor Sie mit dem Migrationsprozess beginnen, **müssen** Sie Ihre Daten sichern.
* Es kann mehrere Tage dauern, bis der Migrationsprozess abgeschlossen ist.
* Adobe Campaign v7 ist eine sicherere Version als die vorherigen: Dies wirkt sich auf Konfigurationsrichtlinien aus, um Probleme wie Datenbeschädigungen zu vermeiden und die Datenintegrität in der Datenbank zu wahren. Als Kunde sind Sie für das Testen aller Konfigurationen, einschließlich Workflows, verantwortlich.

Weitere Voraussetzungen finden Sie auf [dieser Seite](../../migration/using/before-starting-migration.md).


## Modernisierte Umgebung {#modernizing-your-environment}

Die Durchführung einer Migration kann eine Chance sein, Ihre Umgebung (Datenbank-Engines, Betriebssysteme) zu aktualisieren. Adobe Campaign empfiehlt dringend, Ihre Produktionsumgebungen auf die neuesten Versionen zu aktualisieren.

>[!CAUTION]
>
>Weitere Informationen zu den von Adobe Campaign v7 unterstützten Versionen finden Sie in der [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md).

## Wichtige Migrationsschritte {#key-migration-steps}

Das allgemeine Verfahren zur Migration zu Adobe Campaign v7 wird auf [ Seite beschrieben](../../migration/using/before-starting-migration.md).


## Spezifische Konfigurationen {#specific-configurations}

Die durch Adobe Campaign v7 vorgenommenen Änderungen können auch bedeuten, dass Sie bestimmte in früheren Versionen entwickelte Konfigurationen anpassen müssen. Daher kann es erforderlich sein, alle Konfigurationen vor der Migration einem Audit zu unterziehen: Wenden Sie sich für weitere Unterstützung an Adobe Campaign.

Besondere Aufmerksamkeit sollte beispielsweise spezifischen Einstellungen für Web-Anwendungen, Schemaerweiterungen mit SQL-Daten oder dem Klonen vordefinierter Schemata gewidmet werden. Weitere Informationen dazu finden Sie auf [dieser Seite](../../migration/using/configuring-your-platform.md).

Um auf die erhöhte Sicherheit in Adobe Campaign zu reagieren, wurden einige interne Mechanismen geändert: Sie müssen diese Konfigurationen entsprechend anpassen.


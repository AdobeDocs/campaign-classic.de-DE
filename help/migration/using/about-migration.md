---
product: campaign
title: Migration zu Campaign Classic
description: Erfahren Sie, wie Sie von einer früheren Campaign-Version zu Campaign Classic migrieren
audience: migration
content-type: reference
topic-tags: migration-overview
hide: true
hidefromtoc: true
exl-id: 3050238d-6f77-4ffa-9aef-677ab8009388
source-git-commit: 80cf56e330731237d5e7b394381b737f30f8b350
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 4%

---

# Erste Schritte mit der Migration{#about-migration}

![](../../assets/v7-only.svg)

In diesem Dokument werden die Voraussetzungen für eine Migration sowie die Schritte für eine Migration zu Adobe Campaign Classic v7 beschrieben. Schritte und optionale Einstellungen hängen von Ihrer Konfiguration ab.

Der Migrationsprozess muss mit Vorsicht durchgeführt werden, seine Auswirkungen müssen vorher umfassend berücksichtigt werden und das Verfahren muss streng durchgeführt werden. Sie darf nur von einem erfahrenen Benutzer durchgeführt werden. Wir empfehlen dringend, Kontakt aufzunehmen mit [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) vor Beginn eines Migrationsvorgangs.

Die Migration muss zuvor in der Test-/Staging-Umgebung getestet werden, um sicherzustellen, dass sie reibungslos und fehlerfrei ausgeführt wird. Die Migration der Produktionsumgebung darf erst durchgeführt werden, nachdem die migrierte Testumgebung vollständig validiert wurde.

>[!NOTE]
>
>Die neuen Funktionen und Verbesserungen von Adobe Campaign v7 werden im Abschnitt [Versionshinweise](../../rn/using/latest-release.md).


## Voraussetzungen

* Der Migrationsprozess muss von erfahrenen Benutzern durchgeführt werden. Sie müssen von mindestens einem Datenbankexperten, einem Systemadministrator und einem Anwendungsentwickler aus Adobe Campaign unterstützt werden.
* Bevor Sie mit der Migration beginnen, überprüfen Sie, ob die von Ihnen verwendeten Systeme und Systemkomponenten mit v7 kompatibel sind. [Weitere Informationen](../../rn/using/compatibility-matrix.md).
* Wenn Sie Adobe Campaign Cloud Messaging (Mid-Sourcing-Bereitstellung) verwenden, wenden Sie sich vor dem Start an die Kundenunterstützung von Adobe.
* Bevor Sie einen Migrationsprozess starten, **must** Sichern Sie Ihre Daten.
* Der Migrationsprozess kann mehrere Tage in Anspruch nehmen.
* Adobe Campaign v7 ist eine sicherere Version als die vorherigen. Dies wirkt sich auf Konfigurationsrichtlinien aus, um Probleme wie Datenbeschädigung zu vermeiden und die Datenintegrität in der Datenbank zu wahren. Als Kunde sind Sie für das Testen aller Konfigurationen verantwortlich, einschließlich Workflows.

Weitere Voraussetzungen sind verfügbar unter [diese Seite](../../migration/using/before-starting-migration.md).


## Modernisierte Umgebung {#modernizing-your-environment}

Die Durchführung einer Migration kann eine Chance sein, Ihre Umgebung (Datenbank-Engines, Betriebssysteme) zu aktualisieren. Adobe Campaign empfiehlt dringend, Ihre Produktionsumgebungen auf die neuesten Versionen zu aktualisieren.

>[!CAUTION]
>
>Weitere Informationen zu den von Adobe Campaign v7 unterstützten Versionen finden Sie im Abschnitt [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md).

## Wichtige Migrationsschritte {#key-migration-steps}

Das allgemeine Verfahren für die Migration zu Adobe Campaign v7 wird im Abschnitt [diese Seite](../../migration/using/before-starting-migration.md).


## Spezifische Konfigurationen {#specific-configurations}

Die von Adobe Campaign v7 vorgenommenen Änderungen können auch bedeuten, dass Sie bestimmte spezifische Konfigurationen anpassen müssen, die in früheren Versionen entwickelt wurden. Daher kann es erforderlich sein, vor der Migration eine Prüfung aller Ihrer Konfigurationen durchzuführen: Wenden Sie sich für Unterstützung an Adobe Campaign.

Besondere Aufmerksamkeit sollte beispielsweise auf bestimmte Einstellungen für Webanwendungen, Schemaerweiterungen mit SQLdata oder natives Schema-Klonen gelegt werden. Weitere Informationen dazu finden Sie auf [dieser Seite](../../migration/using/configuring-your-platform.md).

Ebenso wurden einige interne Mechanismen geändert, um auf die erhöhte Sicherheit in Adobe Campaign zu reagieren: müssen Sie diese Konfigurationen entsprechend anpassen.


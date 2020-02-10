---
title: Migrationsmethode
seo-title: Migrationsmethode
description: Migrationsmethode
seo-description: null
page-status-flag: never-activated
uuid: 6b954d5b-cfa3-43c6-ac3d-da9185e9e9d1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-overview
discoiquuid: 3ac779a7-1f91-4c1c-a439-10d01697326a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4437d2ea4e4044245a2b9a5a870267cd1f1c0bc9

---


# Migrationsmethode{#migration-method}

## Modernisierung Ihrer Umgebung {#modernizing-your-environment}

Eine Migration kann eine Möglichkeit sein, Ihre Umgebung (Datenbankmaschinen, Betriebssysteme) zu aktualisieren. Adobe Campaign empfiehlt dringend, Ihre Produktionsumgebungen auf die neuesten Versionen zu aktualisieren.

Datenbanken und Betriebssysteme mit 32-Bit-Version werden in Version 7 weiterhin unterstützt, werden aber in zukünftigen Versionen von Adobe Campaign nicht mehr unterstützt. Wir empfehlen Ihnen dringend, Ihre Plattform so bald wie möglich auf 64 Bit zu aktualisieren.

In Version 6.02 war der &quot;multi timezone&quot;-Modus nur für PostgreSQL-Datenbankmaschinen verfügbar. Es wird nun unabhängig vom verwendeten Datenbanktyp angeboten. Wir empfehlen dringend, dass Sie Ihre Basis in eine &quot;Multi-Zeitzone&quot;-Basis umwandeln. Weitere Informationen hierzu finden Sie im Abschnitt [Zeitzonen](../../migration/using/general-configurations.md#time-zones) .

>[!CAUTION]
>
>Einige in Adobe Campaign 5.11 und 6.02 unterstützte Softwareversionen werden in Adobe Campaign v7 nicht mehr unterstützt.
>
>Weitere Informationen zu den von Adobe Campaign unterstützten Versionen finden Sie in der [Kompatibilitätsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

## Wichtige Migrationsschritte {#key-migration-steps}

Das allgemeine Verfahren für die Migration zu Adobe Campaign v7 wird im Abschnitt [Vor Beginn der Migration](../../migration/using/before-starting-migration.md) beschrieben.

Implementierungsschritte für die Migration zu Adobe Campaign v7 finden Sie im Abschnitt [Voraussetzungen für die Migration zu Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) .

Die erforderlichen Konfigurationen hängen von Ihren vorhandenen Konfigurationen und der Ausgangsversion der Plattform ab. Diese werden im Abschnitt [Allgemeine Konfigurationen](../../migration/using/general-configurations.md) beschrieben.

## Spezifische Konfigurationen {#specific-configurations}

Die durch Adobe Campaign v7 verursachten Änderungen können auch bedeuten, dass Sie bestimmte spezifische Konfigurationen anpassen müssen, die in früheren Versionen entwickelt wurden. Daher kann es erforderlich sein, vor der Migration eine Prüfung aller Konfigurationen durchzuführen: Wenden Sie sich an Adobe Campaign, wenn Sie Hilfe benötigen.

So sollte beispielsweise bestimmten Einstellungen für Webanwendungen, Schemaerweiterungen mit SQLdata oder dem vordefinierten Schema-Klonen besondere Aufmerksamkeit gewidmet werden. Weitere Informationen finden Sie im Abschnitt [Plattformkonfiguration](../../migration/using/configuring-your-platform.md) .

Entsprechend wurden einige interne Mechanismen geändert, um auf die erhöhte Sicherheit in Adobe Campaign zu reagieren: Sie müssen diese Konfigurationen anpassen.

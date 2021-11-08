---
product: campaign
title: Migrationsmethode
description: Migrationsmethode
audience: migration
content-type: reference
topic-tags: migration-overview
exl-id: dd4d068b-f414-448f-8d9a-eedf44e7b6e6
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 2%

---

# Migrationsmethode{#migration-method}

![](../../assets/v7-only.svg)

## Modernisierung der Umgebung {#modernizing-your-environment}

Die Durchführung einer Migration kann eine Chance sein, Ihre Umgebung (Datenbank-Engines, Betriebssysteme) zu aktualisieren. Adobe Campaign empfiehlt dringend, Ihre Produktionsumgebungen auf die neuesten Versionen zu aktualisieren.

Datenbanken und Betriebssysteme der 32-Bit-Version werden in v7 weiterhin unterstützt, werden aber in zukünftigen Versionen von Adobe Campaign nicht mehr unterstützt. Wir empfehlen dringend, Ihre Plattform so bald wie möglich auf 64 Bit zu aktualisieren.

In v6.02 war der Modus &quot;Multi Timezone&quot;nur für PostgreSQL-Datenbank-Engines verfügbar. Es wird nun unabhängig vom verwendeten Datenbankmodul angeboten. Wir empfehlen dringend, Ihre Basis in eine &quot;Zeitzone mit mehreren Zeitzonen&quot;umzuwandeln. Weitere Informationen hierzu finden Sie im Abschnitt [Zeitzonen](../../migration/using/general-configurations.md#time-zones) Abschnitt.

>[!IMPORTANT]
>
>Einige in Adobe Campaign 5.11 und 6.02 unterstützte Softwareversionen werden in Adobe Campaign v7 nicht mehr unterstützt.
>
>Weitere Informationen zu den von Adobe Campaign unterstützten Versionen finden Sie im [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md).

## Wichtige Migrationsschritte {#key-migration-steps}

Das allgemeine Verfahren für die Migration zu Adobe Campaign v7 wird im Abschnitt [Vor Beginn der Migration](../../migration/using/before-starting-migration.md) Abschnitt.

Die Implementierungsschritte für die Migration zu Adobe Campaign v7 werden im Abschnitt [Voraussetzungen für die Migration auf Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) Abschnitt.

Die erforderlichen Konfigurationen hängen von Ihren vorhandenen Konfigurationen und der ursprünglichen Version der Plattform ab. Diese werden im Abschnitt [Allgemeine Konfigurationen](../../migration/using/general-configurations.md) Abschnitt.

## Spezifische Konfigurationen {#specific-configurations}

Die von Adobe Campaign v7 vorgenommenen Änderungen können auch bedeuten, dass Sie bestimmte spezifische Konfigurationen anpassen müssen, die in früheren Versionen entwickelt wurden. Daher kann es erforderlich sein, vor der Migration eine Prüfung aller Ihrer Konfigurationen durchzuführen: Wenden Sie sich für Unterstützung an Adobe Campaign.

Besondere Aufmerksamkeit sollte beispielsweise auf bestimmte Einstellungen für Webanwendungen, Schemaerweiterungen mit SQLdata oder natives Schema-Klonen gelegt werden. Weitere Informationen finden Sie im Abschnitt [Plattform konfigurieren](../../migration/using/configuring-your-platform.md) Abschnitt.

Ebenso wurden einige interne Mechanismen geändert, um auf die erhöhte Sicherheit in Adobe Campaign zu reagieren: müssen Sie diese Konfigurationen anpassen.

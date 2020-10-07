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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 4%

---


# Migrationsmethode{#migration-method}

## Modernisierung Ihrer Umgebung {#modernizing-your-environment}

Eine Migration kann eine Möglichkeit sein, Ihre Umgebung zu aktualisieren (Datenbankmaschinen, Betriebssysteme). Adobe Campaign empfiehlt dringend, Ihre Produktions-Umgebung auf die neuesten Versionen zu aktualisieren.

Datenbanken und Betriebssysteme mit 32-Bit-Version werden in Version 7 weiterhin unterstützt, werden aber in zukünftigen Versionen von Adobe Campaign nicht mehr unterstützt. Wir empfehlen Ihnen dringend, Ihre Plattform so bald wie möglich auf 64 Bit zu aktualisieren.

In Version 6.02 war der &quot;multi timezone&quot;-Modus nur für PostgreSQL-Datenbankmaschinen verfügbar. Es wird nun unabhängig vom verwendeten Datenbanktyp angeboten. Wir empfehlen dringend, dass Sie Ihre Basis in eine &quot;Multi-Zeitzone&quot;-Basis umwandeln. Weitere Informationen hierzu finden Sie im Abschnitt [Zeitzonen](../../migration/using/general-configurations.md#time-zones) .

>[!IMPORTANT]
>
>Einige in Adobe Campaign 5.11 und 6.02 unterstützte Softwareversionen werden in Adobe Campaign 7 nicht mehr unterstützt.
>
>Weitere Informationen zu den von Adobe Campaign unterstützten Versionen finden Sie in der [Kompatibilitätsmatrix](https://helpx.adobe.com/de/campaign/kb/compatibility-matrix.html).

## Wichtige Migrationsschritte {#key-migration-steps}

Das allgemeine Verfahren für die Migration zu Adobe Campaign v7 wird im Abschnitt [Vor Beginn der Migration](../../migration/using/before-starting-migration.md) beschrieben.

Die Implementierungsschritte für die Migration zu Adobe Campaign v7 finden Sie im Abschnitt [Voraussetzungen für die Migration zu Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) .

Die erforderlichen Konfigurationen hängen von Ihren vorhandenen Konfigurationen und der Ausgangsversion der Plattform ab. Diese werden im Abschnitt [Allgemeine Konfigurationen](../../migration/using/general-configurations.md) beschrieben.

## Spezifische Konfigurationen {#specific-configurations}

Die durch Adobe Campaign v7 verursachten Änderungen können auch bedeuten, dass Sie bestimmte spezielle Konfigurationen anpassen müssen, die in früheren Versionen entwickelt wurden. Daher kann es erforderlich sein, vor der Migration eine Prüfung aller Konfigurationen durchzuführen: Kontaktieren Sie das Adobe Campaign, um Hilfe zu erhalten.

Besondere Aufmerksamkeit sollte beispielsweise bestimmten Einstellungen für Webanwendungen, Schema-Erweiterungen mit SQLdata oder dem vordefinierten Schema-Klonen gewidmet werden. Weitere Informationen finden Sie im Abschnitt [Plattformkonfiguration](../../migration/using/configuring-your-platform.md) .

Ebenso wurden einige interne Mechanismen geändert, um auf die erhöhte Sicherheit in Adobe Campaign zu reagieren: Sie müssen diese entsprechenden Konfigurationen anpassen.

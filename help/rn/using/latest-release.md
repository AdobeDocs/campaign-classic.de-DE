---
product: campaign
title: Aktuelle Version
description: Aktuelle Versionshinweise von Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 631188b5974eaa4cd1bf667c5df9f2ff0f983cf0
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 27%

---

# Aktuelle Version {#latest-release}

Auf dieser Seite werden neue Funktionen, Verbesserungen und Fehlerbehebungen der **aktuellen Version Campaign Classic v7** aufgelistet. Jeder neue Build weist einen Status auf, der durch eine bestimmte Farbe dargestellt wird. Sie erfahren mehr über den Build-Status von Campaign Classic v7 auf [dieser Seite](rn-overview.md).

## Version 7.4.2 – Build 9390 {#release-7-4-2}

[!BADGE Eingeschränkte Verfügbarkeit]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=de#rn-statuses" tooltip="Eingeschränkte Verfügbarkeit"}

_Samstag, 21. März 2025_

>[!AVAILABILITY]
>
>Diese Version ist nur **eingeschränkt verfügbar**. Sie ist auf Benutzer von Hosted/Managed Services beschränkt. Diese Version wird bald für Hybrid- und On-Premise-Kunden verfügbar sein.

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

-->

### Verbesserungen bezüglich der Sicherheit {#security-7-4-2}

Diese Version enthält mehrere Sicherheitskorrekturen.

Die Verbindung mit Adobe-Lösungen und -Apps über das externe Konto **[!UICONTROL Adobe Experience Cloud]** wurde aktualisiert, um die Sicherheit zu erhöhen.

### Fehlerbehebungen {#release-7-4-2-fixes}

Diese Version enthält die folgenden Hauptkorrekturen:

* TLS-/SMPP-Verbindung - Es wurden SMPP-Stabilitätsprobleme behoben

* Google BigQuery-Fehlerbehebungen:

   * Fehlerkorrektur - Regressionen bei BOOLESCHEN Datentypen
   * Probleme mit Proxy-Einstellungen wurden behoben
   * Fehlerkorrektur - Regressionen bei Datentypen vom Typ „DATETIME“ werden korrigiert
   * Feste Stabilität der Massenladung
   * Verbesserte interne Tests bei ODBC-Versionen
   * Es wurde ein Problem mit Sonderzeichen in der Verbindungszeichenfolge behoben
   * Standard-Timeout (5 Min.) für Google BigQuery-Abfragen entfernt

* Mail Transfer Agent (MTA) - Es wurde ein verwaistes untergeordnetes MTA-Element korrigiert, das im Status **[!UICONTROL Start ausstehend]** hängen bleibt.

In dieser Version werden außerdem die folgenden Probleme behoben:

NEO-47269, NEO-59059, NEO-62455, NEO-65774, NEO-66462, NEO-66989, NEO-77898, NEO-78843, NEO-79373, NEO-79598, NEO-80145, NEO-80245, NEO-80434, NEO-80683, NEO-81433, NEO-81864, NEO-82351, NEO-82781, NEO-82838, NEO-81222, NEO-82923, NEO-83252, NEO-83809, NEO-83826, NEO-84024, NEO-84553, NEO-85150


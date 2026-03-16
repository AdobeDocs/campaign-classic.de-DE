---
product: campaign
title: Aktuelle Version
description: Aktuelle Versionshinweise von Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 66387e2e008051901fe3385f571d7fe798829100
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 28%

---

# Aktuelle Version {#latest-release}

Auf dieser Seite werden neue Funktionen, Verbesserungen und Fehlerbehebungen der **aktuellen Version Campaign Classic v7** aufgelistet. Jeder neue Build weist einen Status auf, der durch eine bestimmte Farbe dargestellt wird. Sie erfahren mehr über den Build-Status von Campaign Classic v7 auf [dieser Seite](rn-overview.md).

## Version 7.4.3 – Build 9392 {#release-7-4-3}

[!BADGE Allgemeine Verfügbarkeit]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=de#rn-statuses" tooltip="Allgemeine Verfügbarkeit"}

_Dienstag, 16. März 2026_

>[!CAUTION]
>
> Die Aktualisierung der Client-Konsole ist obligatorisch.

### Verbesserungen bezüglich der Sicherheit {#security-7-4-3}

* Um optimale Sicherheit, Stabilität und Compliance zu gewährleisten, wurde Debian auf Version 13 und PostgreSQL auf Version 17 aktualisiert. Siehe die [Kompatibilitätsmatrix](compatibility-matrix.md).

### Fehlerbehebungen {#fixes-7-4-3}

* Es wurde ein Problem behoben, bei dem die Barcode-Komponente einen unbegrenzten Höhenparameter zuließ, was zu einer Sicherheitslücke führen konnte. (NEO-89984)
* Es wurde ein Problem behoben, bei dem Auflistungsfelder in Listen, die über Workflows erstellt wurden, temporäre Namensattribute fehlten, was dazu führte, dass falsche oder leere Aufzählungsbeschriftungen in der Benutzeroberfläche angezeigt wurden. (NEO-91158)
* Fehlerkorrektur - Die Versandstatistiken werden für einige Sendungen jetzt vollständig neu berechnet, was sich insbesondere auf die Erfolgsindikatoren auswirkt. (NEO-88106)
* Fehlerkorrektur - Die Versandvorbereitung schlägt jetzt nicht mehr mit Personalisierungsfehlern fehl, wenn TargetData-Felder in Workflows mit Deduplizierungsaktivitäten verwendet werden. (NEO-87693)
* Fehlerkorrektur - Das Verketten von Zeichenfolgenfeldern mit einzelnen Zeichen mit anderen Zeichenfolgen schlägt in PostgreSQL 15 aufgrund von Typumwandlungsanforderungen nicht mehr fehl. (NEO-88028)
* Es wurde ein Problem behoben, bei dem Trackinglogs für partizipative Kampagnen im verteilten Marketing aufgrund einer Diskrepanz zwischen übergeordneten und untergeordneten Versand-IDs nicht in die Datenbank geschrieben wurden. (NEO-86836)
* Fehlerkorrektur - In Versandlogs werden Nachrichten jetzt nicht mehr als abgebrochen angezeigt, obwohl sie erfolgreich gesendet wurden. Dies betrifft insbesondere Sendungen mit Waveplanung. (NEO-78933)
* Es wurde ein Problem behoben, bei dem der Datenbankbereinigungs-Workflow Daten nicht effizient bereinigte, was sich auf die Leistung auswirken konnte. (NEO-76439)


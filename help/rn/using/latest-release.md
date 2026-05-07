---
product: campaign
title: Aktuelle Version
description: Aktuelle Versionshinweise von Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: b9a716f327b8fdd68c3bf36dbe864535308def30
workflow-type: ht
source-wordcount: '294'
ht-degree: 100%

---

# Aktuelle Version {#latest-release}

Auf dieser Seite werden neue Funktionen, Verbesserungen und Fehlerbehebungen der **aktuellen Version Campaign Classic v7** aufgelistet. Jeder neue Build weist einen Status auf, der durch eine bestimmte Farbe dargestellt wird. Sie erfahren mehr über den Build-Status von Campaign Classic v7 auf [dieser Seite](rn-overview.md).

## Version 7.4.3 – Build 9394 {#release-7-4-3}

[!BADGE Allgemeine Verfügbarkeit]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=de#rn-statuses" tooltip="Allgemeine Verfügbarkeit"}

_16. März 2026_

>[!CAUTION]
>
> Die Aktualisierung der Client-Konsole ist obligatorisch.

### Verbesserungen bezüglich der Sicherheit {#security-7-4-3}

* Um optimale Sicherheit, Stabilität und Compliance zu gewährleisten, wurde Debian auf Version 13 und PostgreSQL auf Version 17 aktualisiert. Weitere Informationen finden Sie in der [Kompatibilitätsmatrix](compatibility-matrix.md).

### Fehlerbehebungen {#fixes-7-4-3}

* Es wurde ein Problem behoben, bei dem die Barcode-Komponente einen unbegrenzten Höhenparameter zuließ, was zu einer Sicherheitslücke führen konnte. (NEO-89984)
* Es wurde ein Problem behoben, bei dem über Workflows erstellten Auflistungsfeldern in Listen temporäre Namensattribute fehlten, was dazu führte, dass falsche oder leere Auflistungstitel in der Benutzeroberfläche angezeigt wurden. (NEO-91158)
* Es wurde ein Problem behoben, bei dem die Versandstatistiken für einige Sendungen nicht vollständig neu berechnet wurden, was sich insbesondere auf die Erfolgsindikatoren auswirkte. (NEO-88106)
* Es wurde ein Problem behoben, bei dem die Versandvorbereitung mit Personalisierungsfehlern fehlschlug, wenn targetData-Felder in Workflows mit Deduplizierungsaktivitäten verwendet wurden. (NEO-87693)
* Es wurde ein Problem behoben, bei dem das Verketten von String-Feldern mit einzelnen Zeichen mit anderen Strings in PostgreSQL 15 aufgrund von Typumwandlungsanforderungen fehlschlug. (NEO-88028)
* Es wurde ein Problem behoben, bei dem Trackinglogs für partizipative Kampagnen im verteilten Marketing aufgrund einer Diskrepanz zwischen übergeordneten und untergeordneten Versand-IDs nicht in die Datenbank geschrieben wurden. (NEO-86836)
* Es wurde ein Problem behoben, bei dem Nachrichten in Versandprotokollen als abgebrochen angezeigt wurden, obwohl sie erfolgreich gesendet wurden. Dies betraf insbesondere Sendungen mit Schubplanung. (NEO-78933)
* Es wurde ein Problem behoben, bei dem der Datenbankbereinigungs-Workflow Daten nicht effizient bereinigte, was sich auf die Leistung auswirken konnte. (NEO-76439)


---
solution: Campaign Classic
product: campaign
title: Häufige Fragen
description: Häufig gestellte Fragen zu Campaign Classic
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 100%

---


# Häufige Fragen für Entwickler{#dev-faq}

Adobe Campaign ist eine offene Lösung, die die benutzerdefinierte Nutzung und die Weiterentwicklung der Anwendung ermöglicht.

## Was ist das Campaign-Datenmodell? {#what-is-the-campaign-data-model}

Das konzeptionelle Datenmodell der Adobe Campaign-Datenbank besteht aus einer Reihe integrierter Tabellen und deren Interaktion. Die physische und logische Struktur der in der Anwendung übertragenen Daten wird in XML beschrieben. Sie folgt einer Adobe Campaign-spezifischen Grammatik namens „Schema“. Weiterführende Informationen zu Adobe Campaign-Schemata [finden Sie in diesem Abschnitt](../../configuration/using/about-schema-edition.md).

[Hier erfahren Sie mehr zum Datenmodell von Campaign](https://helpx.adobe.com/de/campaign/kb/acc-datamodel.html).

Best Practices werden [in diesem Artikel](https://helpx.adobe.com/de/campaign/kb/acc-data-model-best-practices.html) beschrieben.

## Wie funktionieren Schemata in Campaign? {#how-to-work-with-campaign-schemas-}

In Adobe Campaign werden Datenschemata folgendermaßen genutzt:

* Definieren der Verknüpfung zwischen den Datenobjekten in der Anwendung mit den zugrunde liegenden Datenbanktabellen
* Definieren von Beziehungen zwischen den unterschiedlichen Datenobjekten in der Campaign-Anwendung
* Definieren und Beschreiben der einzelnen Felder eines jeden Objekts

Lesen Sie das [Erste-Schritte-Handbuch zu Tabellen und Schemata](../../configuration/using/about-schema-edition.md), um zu erfahren, wie Datenschemata genutzt werden und wie Campaign an Ihre Anforderungen angepasst werden kann.

## Wie wird eine benutzerdefinierte Empfängertabelle verwendet? {#how-to-use-a-custom-recipient-table-}

Sie können eine benutzerdefinierte Empfängertabelle in Campaign erstellen und implementieren, um Nachrichten zu senden.

[Hier erfahren Sie mehr darüber](../../configuration/using/about-custom-recipient-table.md)

## Was sind die Best Practices zum Definieren von Abfragen in Campaign? {#what-are-the-best-practices-to-define-queries-in-campaign-}

Das Abfragetool von Adobe Campaign ermöglicht das leistungsstarke Analysieren von Daten und Erstellen von Segmenten.

Die Adobe-Campaign-Plattform bietet ein leistungsstarkes Abfragetool, das bei der Erfüllung verschiedener Funktionen wie Zielgruppenbestimmung, Segmentation des Kundenstamms, Extraktion und Filterung von Trackinglogs sowie Erstellung von Filtern zur Anwendung kommt.

Sie können mit diesem generischen Abfragetool Daten aus der Campaign-Datenbank abrufen. Der Zugriff darauf erfolgt über das Menü **Werkzeuge > Generisches Abfragetool...** Das Abfragetool ermöglicht Ihnen, in der Datenbank gespeicherte Daten abzurufen, zu organisieren, zu gruppieren, zu sortieren etc. So kann ein Benutzer beispielsweise die Empfänger abrufen, die innerhalb eines bestimmten Zeitraums mehr als x-mal auf einen Link in einem Newsletter geklickt haben. Die Ergebnisliste kann nach Bedarf sortiert und die Anzeige angepasst werden. Alle Abfrageoptionen in Adobe Campaign werden über dieses Tool gesteuert. So lassen sich z. B. Einschränkungsfilter im Tool erstellen und speichern. Derart angelegte Benutzerfilter sind dadurch auch in der Abfrageaktivität eines Zielgruppen-Workflows verfügbar.

Abfragen werden entweder mit den in der ausgewählten Tabelle enthaltenen Feldern oder mithilfe einer Formel durchgeführt. Die wichtigsten Grundsätze bei der Erstellung einer Abfrage in der Campaign-Datenbank werden auf [dieser Seite](../../platform/using/about-queries-in-campaign.md) beschrieben.

[Klicken Sie hier](../../workflow/using/query.md), um mehr über den Campaign-Abfrageeditor zu erfahren.

## Wie kann ich Datenpackages importieren? {#how-can-i-import-a-data-package-}

Adobe Campaign ermöglicht über ein Package-System den Export oder Import von Plattformkonfigurationen und Daten. Mithilfe von Datenpackages können Entitäten in der Adobe Campaign-Datenbank als Dateien im XML-Format dargestellt werden. Dies umfasst alle Daten einer in einem Package enthaltenen Entität.

Das Prinzip der Datenpackages besteht darin, eine Datenkonfiguration zu exportieren und in ein anderes Adobe-Campaign-System zu integrieren.

[Hier erfahren Sie](../../platform/using/working-with-data-packages.md), wie Sie Datenpackages zum Importieren und Exportieren von Campaign-Konfigurationen verwenden.

## Wo finde ich die Liste der Campaign Classic-APIs? {#where-can-i-find-the-list-of-campaign-classic-apis}

Alle Campaign-APIs inklusive vollständiger Beschreibung finden Sie in dieser speziellen [Dokumentation](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).

---
solution: Campaign Classic
product: campaign
title: Erste Schritte mit dem Datenimport und -export
description: Weitere Informationen zum Datenimport und -export in Campaign Classic.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 37cc6cd8b71ec82cd4e6a910d6664a51ed5c091e
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 13%

---


# Erste Schritte mit dem Datenimport und -export {#get-started-data-import-export}

Adobe Campaign Classic bietet Data Management-Funktionen, mit denen Sie Daten importieren und exportieren können. Diese Vorgänge können entweder mit Workflows- oder generischen Ein- und Ausfuhren durchgeführt werden.

>[!IMPORTANT]
>
>Beachten Sie bei der Verwendung dieser Funktion die SFTP-Datenspeicherung, die Datenbankeinschränkung und die Einschränkungen des aktiven Profils gemäß Ihrem Adobe Campaign-Vertrag.

## Workflows {#workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**Mit** Workflows können Sie Ihre Importprozesse automatisieren. Unabhängig davon, ob Sie Daten aus einer lokalen Datei oder aus einem SFTP importieren, können Sie damit Ihre Data Management-Verfahren standardisieren.

Mit Workflows können Import- und Exportvorgänge automatisch nach einem Zeitplan wiederholt werden, um beispielsweise den Datenaustausch zwischen verschiedenen Informationssystemen zu automatisieren.

Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../platform/using/import-export-workflows.md).

## Allgemeine Importe und Exporte {#generic-import-export}

<img src="assets/do-not-localize/icon_templates.svg" width="60px">

Darüber hinaus stellt Campaign Classic **generische Importe und Exporte** bereit, mit denen Sie gelegentliche Import- oder Exportaufträge erstellen können.

Importe und Exporte werden in dedizierten Vorlagen konfiguriert, die Sie konfigurieren und zum Starten und Überwachen von Import- und Exportaufträgen verwenden können.

Weitere Informationen zu allgemeinen Ein- und Ausfuhren finden Sie in [diesem Abschnitt](../../platform/using/about-generic-imports-exports.md).

>[!IMPORTANT]
>Generische Ein- und Ausfuhren sollten nur für gelegentliche Geschäfte verwendet werden. Zur Gewährleistung der Datenkonsistenz und zur Verbesserung der Effizienz wird empfohlen, Ihre Import- und Exportvorgänge mit Workflows durchzuführen.

## Datenverschlüsselung und -komprimierung {#data-encryption-compression}

<img src="assets/do-not-localize/icon_encrypt.svg" width="60px">

Mit Campaign Classic können Sie komprimierte oder verschlüsselte Dateien importieren und komprimierte oder verschlüsselte Dateien exportieren.

Diese Vorgänge werden innerhalb von Workflows ausgeführt, indem die Vorverarbeitungsschritte auf die Daten angewendet werden, die Sie nutzen möchten.

Lesen Sie diesbezüglich auch diese Abschnitte:

* [Entzippen oder Entschlüsseln einer Datei](../../platform/using/unzip-decrypt.md)
* [Datei komprimieren oder verschlüsseln](../../platform/using/zip-encrypt.md)

## Best Practices und Fehlerbehebung {#best-practices-troubleshooting}

<img src="assets/do-not-localize/icon_bestpractices.svg" width="60px">

Bei Import- und Exportvorgängen sollten verschiedene [Best Practices](../../platform/using/import-export-best-practices.md) befolgt werden, um die Datenkonsistenz innerhalb der Datenbank sicherzustellen und häufige Fehler während der Aktualisierung oder des Exports zu vermeiden.

Darüber hinaus finden Sie in [diesem Abschnitt](../../platform/using/sftp-server-usage.md) Empfehlungen und allgemeine Probleme im Zusammenhang mit der Verwendung von SFTP-Servern.

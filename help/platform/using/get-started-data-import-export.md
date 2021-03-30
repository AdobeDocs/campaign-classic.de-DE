---
solution: Campaign Classic
product: campaign
title: Erste Schritte mit dem Datenimport und -export
description: Erfahren Sie mehr über den Datenimport und -export in Campaign Classic.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: b05b8daad449aeb1f5226fdd76744776c6553b63
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 96%

---


# Erste Schritte mit dem Datenimport und -export {#get-started-data-import-export}

Adobe Campaign Classic bietet Daten-Management-Funktionen, mit denen Sie Daten importieren und exportieren können. Diese Vorgänge können entweder über Workflows oder allgemeine Importe und Exporte durchgeführt werden.

>[!IMPORTANT]
>
>Beachten Sie bei Verwendung dieser Funktionalität die Einschränkungen für SFTP-Datenspeicherung, Datenbank-Datenspeicherung und aktive Profile gemäß Ihrem Adobe Campaign-Vertrag.

## Workflows {#workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

Mit **Workflows** können Sie Ihre Importprozesse automatisieren. Unabhängig davon, ob Sie Daten aus einer lokalen Datei oder einem SFTP importieren, können Sie damit Ihre Daten-Management-Verfahren standardisieren.

Mit Workflows können Import- und Exportvorgänge anhand eines Zeitplans automatisch wiederholt werden, um beispielsweise den Datenaustausch zwischen verschiedenen Informationssystemen zu automatisieren.

Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../platform/using/import-export-workflows.md).

## Allgemeine Importe und Exporte {#generic-import-export}

<img src="assets/do-not-localize/icon_templates.svg" width="60px">

Darüber hinaus bietet Campaign Classic **allgemeine Importe und Exporte**, mit denen Sie gelegentliche Import- oder Exportvorgänge erstellen können.

Importe und Exporte werden in eigenen Vorlagen konfiguriert, die Sie konfigurieren und zum Starten und Überwachen von Import- und Exportvorgängen verwenden können.

Weitere Informationen zu allgemeinen Importen und Exporten finden Sie in [diesem Abschnitt](../../platform/using/about-generic-imports-exports.md).

>[!IMPORTANT]
>Allgemeine Importe und Exporte sollten nur für gelegentliche Vorgänge verwendet werden. Zur Gewährleistung der Datenkonsistenz und einer besseren Effizienz wird empfohlen, Import- und Exportvorgänge mithilfe von Workflows durchzuführen.

## Datenverschlüsselung und -komprimierung {#data-encryption-compression}

<img src="assets/do-not-localize/icon_encrypt.svg" width="60px">

Mit Campaign Classic können Sie komprimierte oder verschlüsselte Dateien importieren und exportieren.

Diese Vorgänge erfolgen innerhalb von Workflows, indem die Daten, die Sie nutzen möchten, Vorab-Bearbeitungsprozessen unterzogen werden.

Lesen Sie diesbezüglich auch diese Abschnitte:

* [Entpacken oder Entschlüsseln einer Datei](../../platform/using/unzip-decrypt.md)
* [Eine Datei komprimieren oder verschlüsseln](../../platform/using/zip-encrypt.md)

## Best Practices und Fehlerbehebung {#best-practices-troubleshooting}

<img src="assets/do-not-localize/icon_bestpractices.svg" width="60px">

Bei Import- und Exportvorgängen sollten verschiedene [Best Practices](../../platform/using/import-export-best-practices.md) beachtet werden, um Datenkonsistenz innerhalb der Datenbank zu gewährleisten und häufige Fehler beim Aktualisieren oder Exportieren zu verhindern.

Darüber hinaus finden Sie in [diesem Abschnitt](../../platform/using/sftp-server-usage.md) Empfehlungen und Informationen über allgemeine Probleme im Zusammenhang mit der Verwendung von SFTP-Servern.

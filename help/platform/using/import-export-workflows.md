---
solution: Campaign Classic
product: campaign
title: Importieren und Exportieren von Daten mit Workflows
description: Erfahren Sie, wie Sie Daten mit Workflows in Campaign Classic importieren und exportieren.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: ba460d8347c987291681641a1be208027acf1d2f
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 68%

---


# Importieren und Exportieren von Daten mit Workflows {#import-export-workflows}

## Daten erheben {#collecting-data-workflows}

Workflows sind eine nützliche Methode, Importverfahren zu automatisieren. Sie helfen Ihnen bei der Standardisierung Ihrer Datenverwaltungsaufgaben, egal ob Sie Daten von einer lokalen Datei oder von einem SFTP-Server importieren.

### Verwendung von Daten aus einer Liste: Liste lesen {#using-data-from-a-list--read-list}

In Workflows genutzte Daten können aus Listen stammen, deren Daten zuvor aufbereitet und strukturiert wurden.

Dabei kann es sich um Listen aus Adobe Campaign oder über die Option **[!UICONTROL Liste importieren]** eingespeiste Daten handeln. Weiterführende Informationen zu dieser Option finden Sie auf dieser [Seite](../../platform/using/about-generic-imports-exports.md).

Weitere Informationen zur Verwendung der Aktivität zum Lesen der Liste in einem Workflow finden Sie auf [dieser Seite](../../workflow/using/read-list.md).

### Laden von Daten aus einer Datei: Laden (Datei){#loading-data-from-a-file}

Die im Workflow verarbeiteten Daten können aus einer strukturierten Datei stammen, die in Adobe Campaign importiert wird.

Weiterführende Informationen finden Sie im Abschnitt [Laden (Datei)](../../workflow/using/data-loading--file-.md).

Beispiel einer zu importierenden strukturierten Datei:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

Nachdem die Daten gesammelt wurden, können Sie sie in Ihrer Workflows verwenden, um beispielsweise einen Versand zu bereichern oder die Datenbank zu aktualisieren. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../workflow/using/how-to-use-workflow-data.md).

## Export von Daten {#exporting-data-via-a-workflow}

Workflows sind eine nützliche Methode, einige Ihrer Exportverfahren zu automatisieren oder spezifische Datensätze zu exportieren, nachdem die verfügbaren Datenverwaltungsaktivitäten zur Transformation Ihrer Daten angewendet wurden.

Exportvorgänge werden mit der Aktivität **[!UICONTROL Data Extraktion (file)]** ausgeführt. Weitere Informationen zum Konfigurieren und Verwenden der Aktivität finden Sie auf [dieser Seite](../../workflow/using/extraction--file-.md).

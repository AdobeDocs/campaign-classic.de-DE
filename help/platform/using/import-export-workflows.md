---
product: campaign
title: Importieren und Exportieren von Daten mithilfe von Workflows
description: Erfahren Sie, wie Sie Daten mithilfe von Workflows in Campaign importieren und exportieren.
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 266ecd49-7101-4ff1-941f-1f9b39b44955
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: ht
source-wordcount: '267'
ht-degree: 100%

---

# Daten mit Workflows importieren und exportieren {#import-export-workflows}



## Daten erheben {#collecting-data-workflows}

Workflows sind eine nützliche Methode, um Importverfahren zu automatisieren. Sie helfen Ihnen bei der Standardisierung Ihrer Datenverwaltungsaufgaben, egal ob Sie Daten von einer lokalen Datei oder von einem SFTP-Server importieren.

### Daten aus einer Liste verwenden: Liste lesen {#using-data-from-a-list--read-list}

In Workflows genutzte Daten können aus Listen stammen, deren Daten zuvor aufbereitet und strukturiert wurden.

Dabei kann es sich um Listen aus Adobe Campaign oder über die Option **[!UICONTROL Liste importieren]** eingespeiste Daten handeln. Weiterführende Informationen zu dieser Option finden Sie auf dieser [Seite](../../platform/using/about-generic-imports-exports.md).

Weitere Informationen zum Gebrauch der Aktivität &quot;Liste lesen&quot; in Workflows finden Sie auf [dieser Seite](../../workflow/using/read-list.md).

### Daten aus einer Datei laden {#loading-data-from-a-file}

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

Nachdem die Daten erfasst wurden, können Sie sie in Ihren Workflows verwenden, um beispielsweise einen Versand anzureichern oder die Datenbank zu aktualisieren. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../workflow/using/how-to-use-workflow-data.md).

## Daten exportieren {#exporting-data-via-a-workflow}

Workflows sind eine nützliche Methode, einige Ihrer Exportverfahren zu automatisieren oder spezifische Datensätze zu exportieren, nachdem die verfügbaren Datenverwaltungsaktivitäten zur Transformation Ihrer Daten angewendet wurden.

Exportvorgänge werden mit der Aktivität **[!UICONTROL Extraktion (Datei)]** ausgeführt. Weitere Informationen zur Konfiguration und Verwendung der Aktivität finden Sie auf [dieser Seite](../../workflow/using/extraction--file-.md).

---
product: campaign
title: Lebenszyklus der Arbeitsdaten
description: Erfahren Sie mehr über den Lebenszyklus der Arbeitsdaten in Workflows
feature: Workflows, Data Management
exl-id: 366acc1e-d769-4053-9fa1-f47182627c07
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 80%

---

# Lebenszyklus der Arbeitsdaten {#data-life-cycle}



## Arbeitstabellen {#work-table}

In einem Workflow werden die von einer Aktivität zur anderen übertragenen Daten in temporären Arbeitstabellen gespeichert.

Die Daten können durch Rechtsklick auf die entsprechende Transition angezeigt und analysiert werden.

![](assets/wf-right-click-analyze.png)

Wählen Sie im Kontextmenü die entsprechende Option aus:

* Ergebnis anzeigen...

  Diese Option ermöglicht die Anzeige der Zielgruppendaten und der Struktur der Arbeitstabelle (Tab **[!UICONTROL Schema]**).

  ![](assets/wf-right-click-display.png)

  Weitere Informationen finden Sie unter [Arbeitstabellen und Workflow-Schemata](monitoring-workflow-execution.md#worktables-and-workflow-schema).

* Ergebnis analysieren...

  Diese Option bietet Zugriff auf den Assistenten zur beschreibenden Analyse, welcher die Erstellung von Statistiken und Berichten über die in der Transition übermittelten Daten ermöglicht.

  Weiterführende Informationen hierzu finden Sie in diesem [Abschnitt](../../reporting/using/using-the-descriptive-analysis-wizard.md).

Die Zielgruppendaten werden bei Ausführung des Workflows bereinigt. Nur die letzte Arbeitstabelle ist zugänglich. Sie können den Workflow so konfigurieren, dass alle Arbeitstabellen zugänglich bleiben: Überprüfen Sie die **[!UICONTROL Zwischen zwei Ausführungen die ermittelte Population beibehalten]** in den Workflow-Eigenschaften.

Bei großen Datenmengen sollte diese Option jedoch nicht aktiviert werden.

![](assets/wf-purge-data-option.png)

## Zielgruppendaten {#target-data}

Die in den Arbeitstabellen gespeicherten Daten können insbesondere in Personalisierungsfeldern verwendet werden.

Auf diese Weise können Sie in einem Versand mithilfe einer Liste gesammelte oder aus Umfrageantworten stammende Informationen verwenden. Dies geschieht über folgende Syntax:

```
%= targetData.FIELD %
```

Personalisierungsinformationen vom Typ **[!UICONTROL Erweiterung des Zieldatensatzes]** (targetData) stehen nur in Zielgruppen-Workflows zur Verfügung. Dies bedeutet, dass die Versandzielgruppe im Workflow zu bestimmen und in der in den Versand eingehenden Transition zu übermitteln ist.

Wenn Sie Testsendungen erstellen möchten, muss die Testversand-Zielgruppe auf der Basis der Variablen **[!UICONTROL Adressersetzung]** , damit die Personalisierungsdaten eingegeben werden können. Weitere Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/steps-defining-the-target-population.md#using-address-substitution-in-proof).

Im folgenden Anwendungsbeispiel sollen Kundeninformationen in einer Liste gesammelt und dann in einer personalisierten E-mail verwendet werden.

Gehen Sie wie folgt vor:

1. Erstellen Sie einen Workflow, um die Informationen zu sammeln, sie mit der Datenbank abzustimmen und den Versand zu starten.

   ![](assets/wf-targetdata-sample-1.png)

   Im vorliegenden Beispiel enthält die Datei folgende Informationen:

   ```
   Music,First name,Last name,Account,CD/DVD,Card
   Pop,David,BLAIR,4323,CD,0
   Rock,Daniel,ARCARI,3222,DVD,1
   Disco,Uma,ALTON,0488,DVD,0
   Jazz,Paul,BOLES,6475,CD,1
   Jazz,David,BOUKHARI,0841,DVD,1
   [...]
   ```

   Die Aktivität zum Laden der Datei wird folgendermaßen konfiguriert:

   ![](assets/wf-targetdata-sample-2.png)

1. Konfigurieren Sie nun die Aktivität vom Typ **[!UICONTROL Anreicherung]**, um die geladenen Daten mit denen der Datenbank abzustimmen.

   Hier dient die Kundennummer als Abstimmschlüssel:

   ![](assets/wf-targetdata-sample-3.png)

1. Konfigurieren Sie dann die **[!UICONTROL Versandaktivität]**. Sie wird basierend auf einer Vorlage erstellt und die Empfänger werden durch die eingehende Transition bestimmt.

   ![](assets/wf-targetdata-sample-4.png)

   >[!CAUTION]
   >
   >Nur die in der Transition enthaltenen Daten können zur Personalisierung des Versands verwendet werden. **targetData** Personalisierungsfelder sind nur für die Eingangspopulation der **[!UICONTROL Versand]** -Aktivität.

1. Verwenden Sie in der Versandvorlage die im Workflow gesammelten Daten.

   Fügen Sie hierfür Personalisierungsfelder vom Typ **[!UICONTROL Erweiterung des Zieldatensatzes]** ein.

   ![](assets/wf-targetdata-sample-5.png)

   Im vorliegenden Beispiel wird der bevorzugte Musikstil des Kunden und der bevorzugte Datenträger (CD oder DVD) - gemäß den Informationen der geladenen Datei - eingefügt.

   Des Weiteren enthält der Versand ein Angebot für Kunden mit Kundenkarte, d. h. für Kunden, bei denen der Wert &#39;Kundenkarte&#39; gleich 1 ist.

   ![](assets/wf-targetdata-sample-6.png)

   Daten vom Typ **[!UICONTROL Erweiterung des Zieldatensatzes]** (targetData) werden wie andere Personalisierungsfelder auch in Sendungen eingefügt. D. h. sie können u. a. in Nachrichtenbetreffs, Linktiteln oder Links selbst verwendet werden.

   Die in der ersten Aktivität des Workflows erhobenen Empfänger erhalten somit die folgende Nachricht:

   ![](assets/wf-targetdata-sample-7.png)

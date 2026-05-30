---
product: campaign
title: Lebenszyklus der Arbeitsdaten
description: Erfahren Sie mehr über den Lebenszyklus der Arbeitsdaten in Workflows
feature: Workflows, Data Management
hide: true
exl-id: 366acc1e-d769-4053-9fa1-f47182627c07
TQID: https://experienceleague.adobe.com/eRSi9Eu1u9pMtMiiMZI9kZLjZ1JAWCt5B4HFc4FAm3U
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 548
ht-degree: 82%

---

# Lebenszyklus der Arbeitsdaten {#data-life-cycle}



## Arbeitstabellen {#work-table}

In einem Workflow werden die von einer Aktivität zur anderen übertragenen Daten in temporären Arbeitstabellen gespeichert.

Die Daten können durch Rechtsklick auf die entsprechende Transition angezeigt und analysiert werden.

![](assets/wf-right-click-analyze.png)

Wählen Sie im Kontextmenü die entsprechende Option aus:

* Ergebnis anzeigen...

  Diese Option ermöglicht die Anzeige der Zielpopulationsdaten und der Struktur der Arbeitstabelle (Tab **[!UICONTROL Schema]**).

  ![](assets/wf-right-click-display.png)

  Weitere Informationen finden Sie unter [Arbeitstabellen und Workflow-Schemata](monitoring-workflow-execution.md#worktables-and-workflow-schema).

* Ergebnis analysieren...

  Diese Option bietet Zugriff auf den Assistenten für deskriptive Analysen, welcher die Erstellung von Statistiken und Berichten über die in der Transition übermittelten Daten ermöglicht.

  Weitere Informationen hierzu finden Sie in diesem [Abschnitt](../../reporting/using/using-the-descriptive-analysis-wizard.md).

Die Zielgruppendaten werden bei Ausführung des Workflows gelöscht. Nur die letzte Arbeitstabelle ist zugänglich. Sie haben die Möglichkeit, den Workflow dahingehend zu konfigurieren, dass alle Arbeitstabellen beibehalten werden. Aktivieren Sie hierzu in den Workflow-Eigenschaften die Option **[!UICONTROL Zwischen zwei Ausführungen die ermittelte Population festhalten]**.

Bei großen Datenmengen sollte diese Option jedoch nicht aktiviert werden.

![](assets/wf-purge-data-option.png)

## Zielgruppendaten {#target-data}

Die in den Arbeitstabellen des Workflows gespeicherten Daten können insbesondere in Personalisierungsfeldern verwendet werden.

Auf diese Weise können Sie Daten verwenden, die über eine Liste oder auf der Grundlage von Antworten auf eine Umfrage in einem Versand erfasst wurden. Verwenden Sie dazu die folgende Syntax:

```
%= targetData.FIELD %
```

Personalisierungselemente vom **[!UICONTROL Erweiterung des Zieldatensatzes]** (targetData) sind für Zielgruppen-Workflows nicht verfügbar. Die Versandzielgruppe muss im Workflow erstellt und in der eingehenden Transition des Versands spezifiziert werden.

Wenn Sie Testsendungen durchführen möchten, muss die Testversand-Zielgruppe daher im Modus **[!UICONTROL Adressersetzung]** konzipiert werden, damit die Personalisierungsdaten ausgefüllt werden können. Weitere Informationen finden Sie in diesem Abschnitt der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=de#target-population){target="_blank"}.

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
   >Nur die von der Transition übermittelten Daten können für die Versandpersonalisierung verwendet werden. Personalisierungsfelder vom Typ **targetData** stehen nur für die in die **[!UICONTROL Versandaktivität]** eingehende Population zur Verfügung.

1. Verwenden Sie in der Versandvorlage die im Workflow gesammelten Daten.

   Fügen Sie hierfür Personalisierungsfelder vom Typ **[!UICONTROL Erweiterung des Zieldatensatzes]** ein.

   ![](assets/wf-targetdata-sample-5.png)

   Im vorliegenden Beispiel wird der bevorzugte Musikstil des Kunden und der bevorzugte Datenträger (CD oder DVD) - gemäß den Informationen der durch den Workflow geladenen Datei - eingefügt.

   Des Weiteren enthält der Versand ein Angebot für Kunden mit Kundenkarte, d. h. für Kunden, bei denen der Wert &#39;Kundenkarte&#39; gleich 1 ist.

   ![](assets/wf-targetdata-sample-6.png)

   **[!UICONTROL Erweiterung des Zieldatensatzes]** (targetData) werden Daten mit denselben Eigenschaften wie bei allen Personalisierungsfeldern in Sendungen eingefügt. Sie können auch im Betreff, in Link-Kennzeichnungen oder in den Links selbst verwendet werden.

   Die in der ersten Aktivität des Workflows erhobenen Empfänger erhalten somit die folgende Nachricht:

   ![](assets/wf-targetdata-sample-7.png)

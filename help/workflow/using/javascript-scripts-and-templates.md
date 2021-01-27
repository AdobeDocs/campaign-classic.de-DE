---
solution: Campaign Classic
product: campaign
title: Scripts/JavaScript-Templates
description: Scripts/JavaScript-Templates
audience: workflow
content-type: reference
topic-tags: advanced-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1255'
ht-degree: 100%

---


# Scripts/JavaScript-Templates{#javascript-scripts-and-templates}

Scripts dienen zur Berechnung von Werten, dem Austausch von Daten zwischen verschiedenen Aufgaben des Prozesses und der Ausführung von spezifischen Aktionen mithilfe von SOAP-Calls.

In einem Workflow-Diagramm sind Scripts allgegenwärtig:

* Jede Aktivität verfügt über ein Initialisierungscript. Dieses wird bei Aktivierung der Aktivität ausgeführt. Es initialisiert die Variablen oder ändert die Eigenschaften der Aktivität.
* Die &#39;JavaScript-Code&#39;-Aktivität dient einzig der Ausführung eines Scripts.
* Die &#39;Test&#39;-Aktivität evaluiert JavaScript-Ausdrücke, um die richtige Transition zu aktivieren.
* Die meisten Textfelder sind JavaScript-Templates: Sie können zwischen &lt;%= und %> JavaScript-Ausdrücke enthalten. Darüber hinaus besteht Zugriff auf eine Dropdown-Liste, die die Erstellung der Ausdrücke erleichtert.

   ![](assets/script-button.png)

## Script-Objekte {#objects-exposed}

Jedes im Rahmen des Workflows ausgeführte JavaScript greift auf eine Reihe von globalen Objekten zu.

* **instance**: Stellt den Workflow dar, der ausgeführt wird. Das Schema dieses Objekts ist **xtk:workflow**.
* **task**: Stellt die ausgeführten Aufgaben dar. Das Schema dieses Objekts ist **xtk:workflowTask**.
* **event**: Stellt die Ereignisse dar, die die ausgeführte Aufgabe aktiviert haben. Das Schema dieses Objekts ist **xtk:workflowEvent**. Dieses Objekt wird nicht für Aktivitäten vom Typ **Und-Verknüpfung** initialisiert, die von mehreren Transitionen aktiviert wurden.
* **events**: Stellt die Liste der Ereignisse dar, die die aktuelle Aufgabe aktiviert haben. Das Schema dieses Objekts ist **xtk:workflowEvent**. Diese Tabelle enthält in der Regel ein Element, kann jedoch mehrere Aktivitäten vom Typ **Und-Verknüpfung** enthalten, die anhand mehrerer Transitionen aktiviert wurden.
* **activity**: Stellt das Modell der ausgeführten Aufgabe dar. Das Schema dieses Objekts hängt vom Aktivitätstyp ab. Das Objekt kann vom Initialisierungs-Script geändert werden; in anderen Scripten werden Änderungen unbestimmbare Folgen haben.

Die verfügbaren Eigenschaften dieser Objekte sind über die Dropdown-Liste rechts in der Symbolleiste des Scripts abrufbar.

>[!CAUTION]
>
>Die Objekteigenschaften sind schreibgeschützt mit Ausnahme der Unter-Eigenschaften der vars-Eigenschaft.
>  
>Die meisten Eigenschaften werden erst nach Ausführung einer elementaren Aufgabe oder zum Zeitpunkt der Instanzpassivierung aktualisiert. Daher entsprechen die abgerufenen Werte nicht unbedingt dem aktuellen, sondern in der Regel dem vorangegangenen Status.

**Beispiel**

Für das vorliegende Beispiel und die folgenden wird wie unten dargestellt ein Workflow mit einer **JavaScript-Code**-Aktivität und einem **Ende** benötigt.

![](assets/script-1.png)

Öffnen Sie die **JavaScript-Code**-Aktivität und fügen Sie das folgende Script ein:

```
logInfo("Label: " + instance.label)
logInfo("Start date: " + task.creationDate)
```

Die Funktion **[!UICONTROL logInfo(message)]** erstellt einen Eintrag im Protokoll.

Klicken Sie auf **[!UICONTROL OK]**, um den Assistenten zu schließen und starten Sie den Workflow mithilfe der Aktionsschaltflächen oben rechts der Workflow-Liste. Rufen Sie nach Ende der Ausführung das Protokoll auf. Bei korrekter Ausführung werden zwei dem Script entsprechende Nachrichten angezeigt: Ein Eintrag zeigt den Workflow-Titel, der zweite das Datum der Script-Aktivierung.

## Variablen {#variables}

Variablen sind freie Eigenschaften der Objekte **[!UICONTROL instance]**, **[!UICONTROL task]** und **[!UICONTROL event]**. Die für diese Variablen zulässigen JavaScript-Typen sind **[!UICONTROL string]**,**[!UICONTROL number]** und **[!UICONTROL Date]**.

### Instanzvariablen {#instance-variables}

Instanzvariablen (**[!UICONTROL instance.vars.xxx]**) sind mit allgemeinen Variablen vergleichbar und gelten für alle Aktivitäten.

### Aufgabenvariablen {#task-variables}

Aufgabenvariablen (**[!UICONTROL task.vars.xxx]**) sind mit lokalen Variablen vergleichbar. Nur die laufende Aufgabe kann auf sie zugreifen. Sie werden für persistente Aktivitäten verwendet, um Daten beizubehalten, und gegebenenfalls zum Austausch von Werten zwischen verschiedenen Skripts innerhalb einer Aktivität.

### Ereignisvariablen {#event-variables}

Ereignisvariablen (**[!UICONTROL vars.xxx]**) ermöglichen den Austausch von Daten zwischen elementaren Aufgaben eines Workflow-Prozesses. Sie werden von der Aufgabe übermittelt, die die laufende Aufgabe aktiviert hat. Es besteht die Möglichkeit, sie zu ändern oder neue Ereignisvariablen zu definieren, die dann an die anschließenden Aktivitäten übermittelt werden.

>[!CAUTION]
>
>Bei Verwendung einer [UND-Verknüpfung](../../workflow/using/and-join.md) fusionieren die Variablen. Wenn eine Variable mehrmals definiert wurde entsteht ein Konflikt und es wird ein unbestimmter Wert ausgegeben.

Ereignisvariablen sind die am häufigsten verwendeten Variablen und sind Instanzvariablen vorzuziehen.

Bestimmte Ereignisvariablen werden von den verschiedenen Aktivitäten geändert oder gelesen. Dies sind alle Zeichenfolgenvariablen. Beispiel: Ein Export definiert die Variable **[!UICONTROL vars.filename]** mit dem vollständigen Namen der Datei, die gerade exportiert wurde. Alle diese gelesenen oder geänderten Variablen werden in [Über Aktivitäten](../../workflow/using/about-activities.md) in den Abschnitten **Eingabeparameter** und **Ausgabeparameter** der Aktivitäten beschrieben.

### Anwendungsbeispiele {#example}

>[!NOTE]
>
>Weitere Anwendungsbeispiele für Workflows sind in [diesem Abschnitt](../../workflow/using/about-workflow-use-cases.md) verfügbar.

**Beispiel 1**

In diesem Beispiel wird eine Instanzvariable verwendet, um den auf eine Population anzuwendenden Aufspaltungsprozentsatz dynamisch zu berechnen.

1. Erstellen Sie einen Workflow und fügen Sie eine Startaktivität hinzu.

1. Fügen Sie eine JavaScript-Code-Aktivität hinzu und konfigurieren Sie sie, um eine Instanzvariable zu erstellen.

   Beispiel: `instance.vars.segmentpercent = 10;`

   ![](assets/js_ex1.png)

1. Fügen Sie eine Abfrageaktivität hinzu und wählen Sie entsprechend Ihren Anforderungen Empfänger für die Zielgruppe aus.

1. Fügen Sie eine Aufspaltungsaktivität hinzu und konfigurieren Sie sie so, dass eine Stichprobe für die eingehende Population vorgenommen wird. Der Stichprobenprozentsatz kann beliebig sein. In diesem Beispiel ist er auf 50 % festgelegt.

   Dieser Prozentsatz wird dank der zuvor definierten Instanzvariablen dynamisch aktualisiert.

   ![](assets/js_ex2.png)

1. Definieren Sie im Abschnitt „Initialisierungs-Script“ auf dem Tab „Erweitert“ der Aufspaltungsaktivität eine JS-Bedingung. Die JS-Bedingung wählt den zufälligen Stichprobenprozentsatz der ersten Transition aus der Aufspaltungsaktivität aus und aktualisiert ihn auf einen Wert, der von der zuvor erstellten Instanzvariablen festgelegt wurde.

   ```
   activity.transitions.extractOutput[0].limiter.percent = instance.vars.segmentpercent;
   ```

   ![](assets/js_ex3.png)

1. Stellen Sie sicher, dass das Komplement in einer separaten Transition der Aufspaltungsaktivität generiert wird, und fügen Sie nach jeder der ausgehenden Transitionen Endaktivitäten hinzu.

1. Speichern und starten Sie den Workflow. Das dynamische Sampling wird entsprechend der Instanzvariablen angewendet.

   ![](assets/js_ex4.png)

**Beispiel 2**

1. Ausgehend vom Workflow des vorangehenden Beispiels wird das Script der **JavaScript-Code**-Aktivität durch folgendes Script ersetzt:

   ```
   instance.vars.foo = "bar1"
   vars.foo = "bar2"
   task.vars.foo = "bar3"
   ```

1. Ergänzen Sie dann das Initialisierungsscript der **Ende**-Aktivität um folgendes Script:

   ```
   logInfo("instance.vars.foo = " + instance.vars.foo)
   logInfo("vars.foo = " + vars.foo)
   logInfo("task.vars.foo = " + task.vars.foo)
   ```

1. Starten Sie den Workflow und rufen Sie das Protokoll auf:

   ```
   Workflow finished
   task.vars.foo = undefined
   vars.foo = bar2
   instance.vars.foo = bar1
   Starting workflow (operator 'admin')
   ```

Das Beispiel zeigt, dass die Aktivität **JavaScript-Code** auf die Instanz- und Ereignisvariablen zugreift, während die Aufgabenvariablen ausserhalb der Aufgaben nicht verfügbar sind (&#39;undefined&#39;).

### Instanzvariablen in Abfragen aufrufen {#calling-an-instance-variable-in-a-query}

In Aktivitäten definierte Instanzvariablen können in Workflow-Abfragen wiederverwendet werden.

Geben Sie beispielsweise zum Abruf der Variablen **instance.vars.xxx = &quot;yyy&quot;** folgende Filterbedingung an: **$(instance/vars/xxx)**.

Beispiel:

1. Erstellen Sie eine Instanzvariable, die über die **[!UICONTROL JavaScript-Code]**-Aktivität den internen Namen eines Versands definiert: **instance.vars.deliveryIN = &quot;DM42&quot;**

   ![](assets/wkf_js_activity_1.png)

1. Erstellen Sie eine Abfrage mit den Empfängern als Zielgruppen- und als Filterdimension. Geben Sie in den Bedingungen an, alle Empfänger zu suchen, an die der von der Variablen bezeichnete Versand gerichtet war.

   Hinweis: Diese Informationen werden in den Versandlogs gespeichert.

   Geben Sie in der Spalte **[!UICONTROL Wert]** **$(instance/vars/@deliveryIN)** an, um sich auf die Instanzvariable zu beziehen.

   Der Workflow gibt die Empfänger aus, die den Versand DM42 erhalten haben.

   ![](assets/wkf_var_in_query.png)

## Erweiterte Funktionen {#advanced-functions}

Neben den Standard-JavaScript-Funkionen stehen spezifische Funktionen zur Verfügung, um Dateien zu bearbeiten, Daten der Datenbank zu lesen oder zu ändern oder Nachrichten in das Protokoll einzutragen.

### Protokoll {#journal}

**[!UICONTROL logInfo(message)]** wurde bereits weiter oben erläutert. Diese Funktion fügt einen Eintrag zum Protokoll hinzu.

**[!UICONTROL logError(message)]** fügt eine Fehlernachricht zum Protokoll hinzu. Die Ausführung des Scripts wird unterbrochen und der Workflow wechselt in den Fehlerstatus (standardmäßig wird die Instanz ausgesetzt).

## Initialisierungsscript {#initialization-script}

Eine Aktivitätseigenschaft kann unter bestimmten Bedingungen zum Zeitpunkt der Ausführung geändert werden.

Die Mehrzahl der Aktivitätseigenschaften kann dynamisch berechnet werden, entweder unter Verwendung eines JavaScript-Templates oder weil die Workflow-Eigenschaften die Berechnung des Werts durch ein Script explizit erlauben.

Für andere Eigenschaften ist jedoch das Initialisierungsscript zu verwenden. Dieses Script wird vor Ausführung der Aufgabe ausgewertet. Die Variable **[!UICONTROL activity]** referenziert die der Aufgabe entsprechende Aktivität. Die Eigenschaften dieses Objekts können geändert werden und betreffen nur diese Aufgabe.

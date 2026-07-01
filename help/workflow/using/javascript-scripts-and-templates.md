---
product: campaign
title: Scripts/JavaScript-Templates
description: Scripts/JavaScript-Templates
feature: Workflows
hide: true
exl-id: 4a3647d1-cf8c-4867-871e-472287be7c6a
TQID: https://experienceleague.adobe.com/QIVkWmrdq0Xk58lIqvcDqdAPQTk6w6OaAIui6FnnSLE
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 1272
ht-degree: 100%

---

# Scripts/JavaScript-Templates{#javascript-scripts-and-templates}



Scripts dienen zur Berechnung von Werten, dem Austausch von Daten zwischen verschiedenen Aufgaben des Prozesses und der Ausführung von spezifischen Aktionen mithilfe von SOAP-Calls.

In einem Workflow-Diagramm sind Scripts allgegenwärtig:

* Alle Aktivitäten verfügen über Initialisierungsskripte. Ein Initialisierungsskript wird ausgeführt, wenn die Aktivität aktiviert wird, und kann zum Initialisieren von Variablen und Anpassen der Eigenschaften verwendet werden.
* Die &#39;JavaScript-Code&#39;-Aktivität dient einzig der Ausführung eines Scripts.
* Die &#39;Test&#39;-Aktivität wertet JavaScript-Ausdrücke aus, um die richtige Transition zu aktivieren.
* Die meisten Textfelder sind JavaScript-Vorlagen: JavaScript-Ausdrücke können zwischen &lt;%= und %> eingefügt werden. Diese Felder enthalten eine Schaltfläche, über die eine Dropdown-Liste zum Eingeben von Ausdrücken geöffnet werden kann.

  ![](assets/script-button.png)

## Script-Objekte {#objects-exposed}

Jedes im Rahmen des Workflows ausgeführte JavaScript greift auf eine Reihe von globalen Objekten zu.

* **instance**: Stellt den Workflow dar, der ausgeführt wird. Das Schema dieses Objekts lautet **xtk:workflow**.
* **task**: Stellt die ausgeführten Aufgaben dar. Das Schema dieses Objekts lautet **xtk:workflowTask**.
* **event**: Stellt die Ereignisse dar, die die ausgeführte Aufgabe aktiviert haben. Das Schema dieses Objekts lautet **xtk:workflowEvent**. Dieses Objekt wird nicht für Aktivitäten vom Typ **Und-Verknüpfung** initialisiert, die von mehreren Transitionen aktiviert wurden.
* **events**: Stellt die Liste der Ereignisse dar, die die aktuelle Aufgabe aktiviert haben. Das Schema dieses Objekts lautet **xtk:workflowEvent**. Diese Tabelle enthält in der Regel ein Element, kann jedoch mehrere Aktivitäten vom Typ **Und-Verknüpfung** enthalten, die anhand mehrerer Transitionen aktiviert wurden.
* **activity**: Stellt das Modell der ausgeführten Aufgabe dar. Das Schema dieses Objekts hängt vom Aktivitätstyp ab. Das Objekt kann vom Initialisierungs-Script geändert werden; in anderen Scripten werden Änderungen unbestimmbare Folgen haben.

Die verfügbaren Eigenschaften dieser Objekte sind über die Dropdown-Liste rechts in der Symbolleiste des Scripts abrufbar.

>[!CAUTION]
>
>Die Objekteigenschaften sind schreibgeschützt mit Ausnahme der Unter-Eigenschaften der vars-Eigenschaft.
>  
>Die meisten dieser Eigenschaften werden erst nach Ausführung einer elementaren Aufgabe aktualisiert, oder wenn die Instanz passiviert ist.Die gelesenen Werte stimmen womöglich nicht mit dem aktuellen Status überein, sondern mit dem vorherigen Status.

**Beispiel**

Für das vorliegende Beispiel und die folgenden wird wie unten dargestellt ein Workflow mit einer **JavaScript-Code**-Aktivität und einem **Ende** benötigt.

![](assets/script-1.png)

Öffnen Sie die **JavaScript-Code**-Aktivität und fügen Sie das folgende Script ein:

```
logInfo("Label: " + instance.label)
logInfo("Start date: " + task.creationDate)
```

Die Funktion **[!UICONTROL logInfo(message)]** erstellt einen Eintrag im Protokoll.

Klicken Sie auf **[!UICONTROL OK]**, um den Erstellungsassistenten zu schließen, und starten Sie dann den Workflow mithilfe der Aktionsschaltflächen oben rechts in der Workflow-Liste. Rufen Sie am Ende der Ausführung das Protokoll auf. Bei korrekter Ausführung werden zwei dem Script entsprechende Nachrichten angezeigt: Ein Eintrag zeigt den Workflow-Titel, der zweite das Datum der Script-Aktivierung.

## Variablen {#variables}

Variablen sind freie Eigenschaften der Objekte **[!UICONTROL instance]**, **[!UICONTROL task]** und **[!UICONTROL event]**. Die für diese Variablen zulässigen JavaScript-Typen sind **[!UICONTROL string]**,**[!UICONTROL number]** und **[!UICONTROL Date]**.

### Instanzvariablen {#instance-variables}

Instanzvariablen (**[!UICONTROL instance.vars.xxx]**) sind mit globalen Variablen vergleichbar. Sie werden von allen Aktivitäten geteilt.

### Aufgabenvariablen {#task-variables}

Aufgabenvariablen (**[!UICONTROL task.vars.xxx]**) sind mit lokalen Variablen vergleichbar. Sie werden nur von der aktuellen Aufgabe verwendet. Diese Variablen werden von persistenten Aktivitäten zum Aufbewahren von Daten verwendet und manchmal genutzt, um Daten zwischen den verschiedenen Skripten derselben Aktivität auszutauschen.

### Ereignisvariablen {#event-variables}

Ereignisvariablen (**[!UICONTROL vars.xxx]**) ermöglichen den Austausch von Daten zwischen den elementaren Aufgaben eines Workflow-Prozesses. Diese Variablen werden von der Aufgabe übergeben, die die in Bearbeitung befindliche Aufgabe aktiviert hat. Es ist möglich, sie zu ändern und neue zu definieren. Sie werden dann an die folgenden Aktivitäten weitergeleitet.

>[!CAUTION]
>
>Bei Verwendung einer [UND-Verknüpfung](and-join.md) werden die Variablen zusammengeführt. Wenn eine Variable mehrmals definiert wurde entsteht ein Konflikt und es wird ein unbestimmter Wert ausgegeben.

Ereignisvariablen sind die am häufigsten verwendeten Variablen und sind Instanzvariablen vorzuziehen.

Bestimmte Ereignisvariablen werden von den verschiedenen Aktivitäten geändert oder gelesen. Dies sind alles String-Variablen. Beispiel: Ein Export definiert die Variable **[!UICONTROL vars.filename]** mit dem vollständigen Namen der Datei, die gerade exportiert wurde. Alle diese gelesenen oder geänderten Variablen werden in [Über Aktivitäten](about-activities.md) in den Abschnitten **Eingabeparameter** und **Ausgabeparameter** der Aktivitäten beschrieben.

### Anwendungsfälle {#example}

>[!NOTE]
>
>Weitere Anwendungsbeispiele für Workflows sind in [diesem Abschnitt](about-workflow-use-cases.md) verfügbar.

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

### Aufrufen von Instanzvariablen in Abfragen {#calling-an-instance-variable-in-a-query}

In Aktivitäten definierte Instanzvariablen können in Workflow-Abfragen wiederverwendet werden.

Geben Sie beispielsweise zum Abruf der Variablen **instance.vars.xxx = &quot;yyy&quot;** folgende Filterbedingung ein: **$(instance/vars/@xxx)**.

Beispiel:

1. Erstellen Sie eine Instanzvariable, die über die **[!UICONTROL JavaScript-Code]**-Aktivität den internen Namen eines Versands definiert: **instance.vars.deliveryIN = &quot;DM42&quot;**

   ![](assets/wkf_js_activity_1.png)

1. Erstellen Sie eine Abfrage, deren Zielgruppenbestimmungs- und Filterdimensionen die Empfängerinnen und Empfänger sind. Geben Sie in den Bedingungen an, dass Sie alle Empfängerinnen und Empfänger suchen möchten, denen der durch die Variable spezifizierte Versand gesendet wurde.

   Hinweis: Diese Informationen werden in den Versandlogs gespeichert.

   Geben Sie in der Spalte **[!UICONTROL Wert]** **$(instance/vars/@deliveryIN)** an, um sich auf die Instanzvariable zu beziehen.

   Der Workflow gibt die Empfänger aus, die den Versand DM42 erhalten haben.

   ![](assets/wkf_var_in_query.png)

## Erweiterte Funktionen {#advanced-functions}

Neben den Standard-JavaScript-Funkionen stehen spezifische Funktionen zur Verfügung, um Dateien zu bearbeiten, Daten der Datenbank zu lesen oder zu ändern oder Nachrichten in das Protokoll einzutragen.

### Protokoll {#journal}

**[!UICONTROL logInfo(message)]** wurde bereits in den obigen Beispielen erläutert. Diese Funktion fügt dem Protokoll eine Informationsnachricht hinzu.

**[!UICONTROL logError(message)]** fügt dem Protokoll eine Fehlermeldung hinzu. Die Ausführung des Skripts wird unterbrochen und der Workflow wechselt in den Fehlerstatus (standardmäßig wird die Instanz pausiert).

## Initialisierungsskript {#initialization-script}

Eine Aktivitätseigenschaft kann unter bestimmten Bedingungen zum Zeitpunkt der Ausführung geändert werden.

Die Mehrzahl der Aktivitätseigenschaften kann dynamisch berechnet werden, entweder unter Verwendung eines JavaScript-Templates oder weil die Workflow-Eigenschaften die Berechnung des Werts durch ein Script explizit erlauben.

Für andere Eigenschaften müssen Sie jedoch das Initialisierungsskript verwenden. Dieses Skript wird vor Ausführung der Aufgabe ausgewertet. Die Variable **[!UICONTROL activity]** verweist auf die der Aufgabe entsprechende Aktivität. Die Eigenschaften dieses Objekts können geändert werden und betreffen nur diese Aufgabe.

**Verwandte Themen**
[Beispiele für JavaScript-Code in Workflows](javascript-in-workflows.md)

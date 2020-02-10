---
title: Best Practices für Workflows
seo-title: Best Practices für Workflows
description: Best Practices für Workflows
seo-description: null
page-status-flag: never-activated
uuid: 56b04004-5d96-4169-9494-3d04284d5a3d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 3da951ef-5775-4593-8301-f143c71edc19
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4b4ec97e52a494dd88b2516650ae514294f00934

---


# Best Practices für Workflows{#workflow-best-practices}

## Erfüllung und Leistung {#execution-and-performance}

Im Folgenden finden Sie allgemeine Richtlinien zur Optimierung der Kampagnenleistung, einschließlich Best Practices zur Anwendung auf Ihre Arbeitsabläufe.

Richtlinien zur Fehlerbehebung in Bezug auf die Ausführung von Workflows sind auch in [diesem Abschnitt](../../production/using/workflow-execution.md)verfügbar.

### Logs {#logs}

Die JavaScript-Methode **[!UICONTROL logInfo()]** ist eine großartige Lösung zum Debugging eines Workflows. Es ist nützlich, muss aber sorgfältig verwendet werden, insbesondere für häufig ausgeführte Aktivitäten: Es kann die Protokolle überladen und die Größe der Protokolltabelle erheblich erhöhen. Aber vielleicht brauchen Sie auch mehr als **[!UICONTROL logInfo()]**.

Zwei zusätzliche Lösungen sind verfügbar:

* **Zwischen zwei Ausführungen die ermittelte Population festhalten**

   Diese Option speichert temporäre Tabellen zwischen zwei Ausführungen eines Workflows. Sie ist auf der Registerkarte &quot;Workflow-Eigenschaften&quot; **[!UICONTROL General]** verfügbar und kann für Entwicklungs- und Testzwecke zur Überwachung von Daten und zur Überprüfung der Ergebnisse verwendet werden. Sie können diese Option in Entwicklungsumgebungen verwenden, sie jedoch nie in Produktionsumgebungen verwenden. Die Beibehaltung von temporären Tabellen könnte dazu führen, dass die Größe der Datenbank erheblich zunimmt und die Größenbeschränkung erreicht wird. Darüber hinaus wird es die Sicherung verlangsamen.

   Nur die Arbeitstabellen der letzten Ausführung des Workflows werden beibehalten. Arbeitstabellen aus früheren Ausführungen werden durch den **[!UICONTROL cleanup]** Workflow bereinigt, der täglich ausgeführt wird.

   >[!CAUTION]
   >
   >Diese Option darf in einem Produktions-Workflow niemals aktiviert sein. Diese Option wird zur Analyse der Ergebnisse verwendet und ist nur für Testzwecke konzipiert und darf daher nur in Entwicklungs- oder Staging-Umgebungen verwendet werden.

* **SQL-Abfragen im Protokoll speichern**

   Diese Option ist auf der **[!UICONTROL Execution]** Registerkarte der Workflow-Eigenschaften verfügbar und protokolliert alle SQL-Abfragen, die vom Tool aus den verschiedenen Aktivitäten generiert wurden. Es ist eine gute Möglichkeit zu sehen, was tatsächlich von der Plattform ausgeführt wird. Diese Option sollte jedoch nur vorübergehend während der Entwicklung verwendet und nicht bei der Produktion aktiviert werden.

Bereinigen Sie die Protokolle, wenn sie nicht mehr benötigt werden. Workflow-Verlauf wird nicht automatisch bereinigt: alle Nachrichten werden standardmäßig gespeichert. Der Verlauf kann über das **[!UICONTROL File > Actions]** Menü oder durch Klicken auf die Schaltfläche Aktionen in der Symbolleiste oberhalb der Liste bereinigt werden. Wählen Sie Verlauf löschen.
Informationen zum Bereinigen der Protokolle finden Sie in dieser [Dokumentation](../../workflow/using/executing-a-workflow.md#actions-toolbar).

### Workflow-Planung {#workflow-planning}

* Versuchen Sie, ein stabiles Aktivitätsniveau während des Tages aufrechtzuerhalten und Spitzen zu vermeiden, um eine Überlastung der Instanz zu verhindern. Verteilen Sie dazu die Startzeiten des Workflows gleichmäßig über den Tag.
* Planen Sie das Laden der Daten für die Nacht, um Ressourcenkonflikte zu reduzieren.
* Lange Workflows können sich auf die Server- und Datenbankressourcen auswirken. Teilen Sie die längsten Workflows auf, um die Bearbeitungszeit zu verkürzen.
* Um die Gesamtlaufzeit zu verkürzen, ersetzen Sie zeitaufwändige Aktivitäten durch einfachere und schnellere Aktivitäten.
* Vermeiden Sie die gleichzeitige Ausführung von mehr als 20 Workflows. Wenn zu viele Workflows gleichzeitig ausgeführt werden, könnte das System nicht mehr über genügend Ressourcen verfügen und instabil werden. Weitere Informationen darüber, warum Ihr Workflow möglicherweise nicht gestartet wird, finden Sie in diesem [Artikel](https://helpx.adobe.com/ie/campaign/kb/workflows-not-starting-in-a-campaign-technical-workflows.html).

### Workflow-Ausführung {#workflow-execution}

Es wird empfohlen, Workflows nicht öfter als alle 15 Minuten auszuführen, da die Gesamtleistung des Systems beeinträchtigt werden kann und Blöcke in der Datenbank entstehen können.

Vermeiden Sie es, Ihre Workflows in einem angehaltenen Zustand zu belassen. Wenn Sie einen temporären Workflow erstellen, stellen Sie sicher, dass dieser ordnungsgemäß abgeschlossen werden kann und nicht im **[!UICONTROL paused]** Status verbleibt. Wenn sie angehalten wird, bedeutet dies, dass Sie die temporären Tabellen beibehalten und somit die Größe der Datenbank erhöhen müssen. Weisen Sie Workflow-Aufseher unter &quot;Workflow-Eigenschaften&quot;zu, um eine Warnung zu senden, wenn ein Workflow fehlschlägt oder vom System angehalten wird.

So vermeiden Sie, dass Workflows ausgesetzt werden:

* Prüfen Sie Ihre Workflows regelmäßig, um sicherzustellen, dass keine unerwarteten Fehler auftreten.
* Halten Sie Ihre Arbeitsabläufe so einfach wie möglich, indem Sie beispielsweise große Arbeitsabläufe in verschiedene Arbeitsabläufe aufteilen. Sie können **[!UICONTROL External signal]** Aktivitäten verwenden, die ihre Ausführung auf der Grundlage der Ausführung anderer Workflows auslösen.
* Vermeiden Sie es, Aktivitäten mit Flüssen in Ihren Workflows zu deaktivieren, sodass Threads geöffnet bleiben und viele temporäre Tabellen entstehen, die viel Platz beanspruchen können. Behalten Sie Aktivitäten nicht in **[!UICONTROL Do not enable]** oder **[!UICONTROL Enable but do not execute]** Status in Ihren Workflows bei.

Beenden Sie außerdem nicht verwendete Workflows. Workflows, die weiterhin ausgeführt werden, halten Verbindungen zur Datenbank aufrecht.

Verwenden Sie in den seltensten Fällen nur den bedingungslosen Stopp. Verwenden Sie diese Aktion nicht regelmäßig. Das NichtDurchführen eines sauberen Schließens von Verbindungen, die durch Workflows zur Datenbank generiert wurden, hat Auswirkungen auf die Leistung.

### In der Engine ausführen {#execute-in-the-engine-option}

Aktivieren Sie im **[!UICONTROL Workflow properties]** Fenster niemals die **[!UICONTROL Execute in the engine]** Option. Wenn diese Option aktiviert ist, hat der Workflow Priorität, und alle anderen Workflows werden von der Workflow-Engine gestoppt, bis diese abgeschlossen ist.

![](assets/wf-execute-in-engine.png)

## Workflow-Eigenschaften  {#workflow-properties}

### Workflow-Ordner {#workflow-folders}

Adobe empfiehlt, Ihre Workflows in einem eigenen Ordner zu erstellen.

If the workflow affects the whole platform (cleansing processes for example), you can consider adding a sub-folder in the built-in **[!UICONTROL Technical Workflows]** folder.

### Workflow-Name {#workflow-naming}

Um die Suche und Fehlerbehebung zu vereinfachen, empfiehlt Adobe, Ihre Workflows mit eigenen Namen und Titeln zu versehen: Erläutern Sie im Beschreibungsfeld des Workflows kurz den jeweiligen Prozess, damit dessen Zweck für den Benutzer leicht ersichtlich ist.

Wenn der Workflow Teil eines mehrere Workflows umfassenden Prozesses ist, können Sie jeden Workflow durch die Angabe eines Titels exakt benennen. Zahlen sind beispielsweise eine gute Möglichkeit, Workflows zu ordnen.

Beispiel:

* 001 - Import - Empfänger importieren
* 002 - Import - Einfuhrverkäufe
* 003 - Import - Verkaufsdetails importieren
* 010 - Export - Exportauslieferungsprotokolle
* 011 - Export - Export-Verfolgungsprotokolle

### Workflow-Schweregrad {#workflow-severity}

You can configure the severity of a workflow in the workflow properties, in the **[!UICONTROL Execution]** tab:

* Normal
* Produktion
* Kritisch

Durch Angabe dieser Informationen bei der Erstellung eines Workflows ist die Prioritätsstufe des konfigurierten Prozesses besser ersichtlich.

Diese Option beeinflusst nur Kampagnen-Workflows.

Kampagnen-Workflows (Workflows, die als Teil einer Kampagne erstellt werden) mit höherer Prioritätsstufe werden vorgezogen, wenn die Kampagne mehrere Prozesse enthält, die gleichzeitig ausgeführt werden müssen. Standardmäßig können entsprechend der Option NmsOperation_LimitConcurrency maximal zehn Prozesse einer Kampagnen gleichzeitig ausgeführt werden. Wenn eine Kampagne beispielsweise aus 25 Workflows besteht, werden Workflows mit einer höheren Prioritätsstufe in der ersten Gruppe von zehn Prozessen ausgeführt.

### Workflow-Monitoring {#workflow-monitoring}

Alle Ihre terminierten in Produktionsumgebungen ausgeführten Workflows sollten überwacht werden, damit Sie bei Auftreten eines Fehlers benachrichtigt werden.

Wählen Sie in den Workflow-Eigenschaften eine Supervisor-Gruppe aus, entweder die Standard- **[!UICONTROL Workflow supervisors]** oder eine benutzerspezifische Gruppe. Achten Sie darauf, dass mindestens ein Operator zu dieser Gruppe gehört und eine E-Mail eingerichtet ist.

Bevor Sie mit dem Erstellen eines Workflows beginnen, sollten Sie daran denken, Workflow-Aufsichtsbehörden zu definieren. Bei Fehlern werden sie per E-Mail benachrichtigt. For more on this, refer to [Managing errors](../../workflow/using/monitoring-workflow-execution.md#managing-errors).

Prüfen Sie regelmäßig das **[!UICONTROL Monitoring]** Universum, um den Gesamtstatus der aktiven Arbeitsabläufe anzuzeigen. For more on this, refer to [Instance supervision](../../workflow/using/monitoring-workflow-execution.md#instance-supervision).

Die Workflow-Heatmap ermöglicht den Administratoren der Adobe Campaign-Plattform, die Auslastung der Instanz zu überwachen und Workflows entsprechend zu planen. Weitere Informationen dazu finden Sie unter [Workflow-Monitoring](../../workflow/using/heatmap.md).

## Aktivitäten verwenden {#using-activities}

>[!CAUTION]
>
>Sie können Aktivitäten in einem Workflow kopieren und einfügen. Es wird jedoch nicht empfohlen, Einfügeaktivitäten über verschiedene Workflows hinweg zu kopieren. Einige Einstellungen, die an Aktivitäten wie Auslieferungen und Zeitplaner angehängt sind, können zu Konflikten und Fehlern beim Ausführen des Ziel-Workflows führen. Stattdessen haben wir empfohlen, Arbeitsabläufe zu **duplizieren** . Weitere Informationen finden Sie unter [Duplizieren von Workflows](../../workflow/using/building-a-workflow.md#duplicating-workflows).

### Name der Aktivität {#name-of-the-activity}

Bei der Entwicklung Ihres Workflows erhalten alle Aktivitäten sowie alle Adobe Campaign-Objekte einen Namen. Diese Namen werden zwar vom Tool erstellt, wir empfehlen jedoch, sie bei der Konfiguration zu ändern. Geschieht dies erst zu einem späteren Zeitpunkt, besteht die Gefahr, dass dadurch der Workflow durch Aktivitäten mit Namen einer anderen früheren Aktivität unterbrochen wird. Deshalb wäre die nachträgliche Aktualisierung der Namen eine schwierige Aufgabe.

Der Aktivitätsname befindet sich auf der **[!UICONTROL Advanced]** Registerkarte. Belassen Sie sie nicht mit Namen **[!UICONTROL query]**, **[!UICONTROL query1]**, **[!UICONTROL query11]** sondern geben Sie ihnen explizite Namen wie **[!UICONTROL querySubscribedRecipients]**. Dieser Name wird im Journal und gegebenenfalls in den SQL-Protokollen angezeigt. Dies hilft beim Debugging des Workflows beim Konfigurieren.

### Erste und letzte Aktivitäten {#first-and-last-activities}

* Starten Sie Ihren Workflow immer mit einer **[!UICONTROL Start]** Aktivität oder einer **[!UICONTROL Scheduler]** Aktivität. Falls relevant, können Sie auch eine **[!UICONTROL External signal]** Aktivität verwenden.
* When building your workflow, only use one **[!UICONTROL Scheduler]** activity per branch. Wenn dieselbe Verzweigung eines Workflows mehrere Planungen enthält, die miteinander verknüpft sind, steigt die Anzahl der auszuführenden Aufgaben exponentiell an, wodurch die Datenbank überlastet würde. Diese Regel gilt auch für alle Aktivitäten mit einer **[!UICONTROL Scheduling & History]** Registerkarte. Weitere Informationen zur [Planung](../../workflow/using/scheduler.md).

   ![](assets/wf-scheduler.png)

* Verwenden Sie **[!UICONTROL End]** Aktivitäten für jeden Workflow. Dadurch kann Adobe Campaign temporären Speicherplatz für Berechnungen in Workflows freigeben. Weitere Informationen finden Sie unter: [Start und Ende](../../workflow/using/start-and-end.md).

### JavaScript innerhalb einer Aktivität {#javascript-within-an-activity}

Sie können JavaScript hinzufügen, wenn Sie eine Workflow-Aktivität initialisieren. Dies kann auf der **[!UICONTROL Advanced]** Registerkarte einer Aktivität erfolgen.

Um den Workflow leichter erkennbar zu machen, empfehlen wir, am Anfang und Ende des Titels der Aktivität doppelte Bindestriche zu setzen, z. B.: -- Mein Titel --.

### Signal {#signal}

Meistens wissen Sie nicht, woher das Signal aufgerufen wird. Um dieses Problem zu vermeiden, verwenden Sie das **[!UICONTROL Comment]** Feld auf der **[!UICONTROL Advanced]** Registerkarte der Signalaktivität, um den erwarteten Ursprung eines Signals für diese Aktivität zu dokumentieren.

![](assets/workflow-signal-bp.png)

## Workflow-Update {#workflow-update}

Ein Produktions-Workflow sollte nicht direkt aktualisiert werden. Prozesse sollten zuerst in einer Entwicklungsumgebung getestet werden, außer der Prozess besteht aus einer Kampagne mit Vorlagen-Workflows. Nach der Validierung kann der Workflow für die Produktion bereitgestellt werden.

Führen Sie alle Tests in Entwicklungs- oder Staging-Umgebungen, nicht in Produktionsumgebungen durch. Die Leistung kann in einem solchen Fall nicht gewährleistet werden.

Während Workflows in einem Archivordner auf Entwicklungs- oder Testplattformen aufbewahrt werden können, sollte die Produktionsumgebung möglichst sauber gehalten werden. Entfernen Sie deshalb alte, inaktive Workflows aus der Produktionsumgebung.

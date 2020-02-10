---
title: Workflow-Ausführung
seo-title: Workflow-Ausführung
description: Workflow-Ausführung
seo-description: null
page-status-flag: never-activated
uuid: 115256f6-bdf2-4594-885c-e90d02a25b80
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 7d8828c5-5776-49ca-b4f7-a4a6aaaa9db1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 69b562979f3b32a4d30dfed0695cf3cf6c0fd26a

---


# Workflow-Ausführung{#workflow-execution}

Im folgenden Abschnitt finden Sie Informationen zu häufigen Problemen im Zusammenhang mit der Ausführung von Workflows und wie diese behoben werden können.

Weitere Informationen zu Workflows finden Sie in den folgenden Abschnitten:

* [Über Workflows](../../workflow/using/about-workflows.md)
* [Workflow ausführen](../../workflow/using/executing-a-workflow.md)
* [Bewährte Verfahren bei der Verwendung von Workflows](../../workflow/using/workflow-best-practices.md)

## So bald wie möglich in Kampagnen beginnen {#start-as-soon-as-possible-in-campaigns}

In einigen Fällen starten Arbeitsabläufe, die von einer Kampagne ausgeführt werden, nicht, wenn auf die **[!UICONTROL Start]** Schaltfläche geklickt wird. Anstatt zu beginnen, wird der Status &quot;sobald wie möglich starten&quot;angezeigt.

Das Problem kann verschiedene Ursachen haben. Gehen Sie wie folgt vor, um es zu beheben:

1. Überprüfen Sie den Status des [**[!UICONTROL operationMgt]**](../../workflow/using/campaign.md) technischen Workflows. Dieser Workflow verwaltet Aufträge oder Arbeitsabläufe innerhalb einer Kampagne. Schlägt dies fehl, führt dies dazu, dass Workflows nicht starten/beenden. Starten Sie es neu, um die Ausführung der Kampagnen-Workflows fortzusetzen.

   Weitere Informationen zur Überwachung der technischen Arbeitsabläufe finden Sie auf [dieser Seite](../../workflow/using/monitoring-technical-workflows.md).

   >[HINWEIS]
   >
   >Nachdem der Workflow neu gestartet wurde, stellen Sie sicher, dass Sie die ausstehenden Aufgaben ausführen (klicken Sie mit der rechten Maustaste auf die **[!UICONTROL Scheduler]** Aktivität / **[!UICONTROL Execute pending task(s) now]**), um zu prüfen, ob sie bei einer der Aktivitäten erneut fehlschlägt.

   Wenn der Workflow weiterhin fehlschlägt, überprüfen Sie das Prüfprotokoll auf einen bestimmten Fehler, führen Sie eine entsprechende Fehlerbehebung durch und starten Sie den Workflow erneut neu.

1. Überprüfen Sie den **[!UICONTROL wfserver]** Modulstatus auf der **[!UICONTROL Monitoring]** Registerkarte, auf den Sie von der Campaign Classic-Homepage aus zugreifen können (siehe [Überwachungsprozesse](../../production/using/monitoring-processes.md)). Dieser Prozess ist für die Ausführung aller Workflows verantwortlich.

   Ein Admin-Benutzer kann auch überprüfen, ob das Modul **wfserver@`<instance>`**mit dem folgenden Befehl auf Ihrem Hauptanwendungsserver gestartet wird.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   Wenn das Modul nicht ausgeführt wird, wenden Sie sich an den Adobe-Kundendienst. Wenn Sie über eine lokale Installation verfügen, muss ein Administrator den Dienst mit dem folgenden Befehl neu starten.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Ersetzen Sie **`<instancename>`** dies durch den Namen Ihrer Instanz (Produktion, Entwicklung usw.). Der Instanzname wird über die Konfigurationsdateien identifiziert:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Weitere Informationen zum Neustart von Modulen finden Sie in [diesem Abschnitt](../../production/using/usual-commands.md#module-launch-commands).

1. Überprüfen Sie, ob die **Anzahl der Kampagnenprozesse, die auf der Instanz ausgeführt** werden, über dem Schwellenwert liegt. Es gibt eine Beschränkung, die durch die [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) Option definiert wird, wie viele Kampagnenprozesse parallel auf der Instanz ausgeführt werden können. Wenn diese Grenze erreicht ist, bleibt der Workflow im Status &quot;Sofort wie möglich starten&quot;, solange die Anzahl der ausgeführten Workflows über der Grenze liegt.

   Um dieses Problem zu lösen, beenden Sie unerwünschte Workflows und löschen Sie fehlgeschlagene Auslieferungen. Wenn der Schwellenwert erreicht wurde, können neue Prozesse ausgeführt werden.

   Zur Überprüfung der Anzahl der Workflows, die in Ihrer Instanz ausgeführt werden, empfehlen wir die Verwendung der vordefinierten Ansichten, die standardmäßig im Ordner **[!UICONTROL Administration]** / **[!UICONTROL Audit]** verfügbar sind. For more information, refer to [this page](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[VORSICHT]
   >
   >Das Erhöhen des **[!UICONTROL NmsOperation_LimitConcurrency]** Optionsschwellenwerts kann zu Leistungsproblemen in Ihrer Instanz führen. Führen Sie dies in jedem Fall nicht selbst aus und wenden Sie sich an Ihren Adobe Campaign-Kontakt.

Weitere Informationen zur Überwachung der Workflows finden Sie in [diesem Abschnitt](../../workflow/using/monitoring-workflow-execution.md).

## Wird gestartet {#start-in-progress}

Wenn Workflows nicht ausgeführt werden und der Status &quot; **Start&quot;in Bearbeitung** ist, bedeutet dies möglicherweise, dass das Workflow-Modul nicht gestartet wird.

Um dies zu überprüfen und bei Bedarf das Modul zu starten, gehen Sie wie folgt vor:

1. Überprüfen Sie den **[!UICONTROL wfserver]** Modulstatus auf der **[!UICONTROL Monitoring]** Registerkarte, auf den Sie von der Campaign Classic-Homepage aus zugreifen können (siehe [Überwachungsprozesse](../../production/using/monitoring-processes.md)).

   Ein Admin-Benutzer kann auch überprüfen, ob das Modul **wfserver@`<instance>`**mit dem folgenden Befehl auf Ihrem Hauptanwendungsserver gestartet wird.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   Weitere Informationen zum Überwachen von Modulen finden Sie in [diesem Abschnitt](../../production/using/usual-commands.md#monitoring-commands-).

1. Wenn das Modul nicht ausgeführt wird, wenden Sie sich an den Adobe-Kundendienst. Wenn Sie über eine lokale Installation verfügen, muss ein Administrator diese mithilfe des folgenden Befehls neu starten.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Ersetzen Sie **`<instancename>`** dies durch den Namen Ihrer Instanz (Produktion, Entwicklung usw.). Der Instanzname wird über die Konfigurationsdateien identifiziert:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Weitere Informationen zum Neustart von Modulen finden Sie in [diesem Abschnitt](../../production/using/usual-commands.md#module-launch-commands).

## Fehlgeschlagener Workflow {#failed-workflow}

Wenn ein Workflow fehlschlägt, gehen Sie wie folgt vor:

1. Überprüfen Sie das Workflow-Journal. Weitere Informationen dazu finden Sie in den Abschnitten [Überwachung der Workflow-Ausführung](../../workflow/using/monitoring-workflow-execution.md) und [Anzeigen von Protokollen](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) .
1. Überwachung der technischen Arbeitsabläufe. For more on this refer to the [this section](../../workflow/using/monitoring-technical-workflows.md).
1. Suchen Sie nach Fehlern bei den einzelnen Workflow-Aktivitäten.

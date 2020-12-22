---
solution: Campaign Classic
product: campaign
title: Workflow-Ausführung
description: Workflow-Ausführung
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: a9d58e25ab17baaabf4ff8c109b53e83c7d93218
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 13%

---


# Workflow-Ausführung{#workflow-execution}

Im folgenden Abschnitt finden Sie Informationen zu häufigen Problemen im Zusammenhang mit Workflows Ausführung und wie diese behoben werden können.

Weitere Informationen zu Workflows finden Sie in den folgenden Abschnitten:

* [Über Workflows](../../workflow/using/about-workflows.md)
* [Workflow starten](../../workflow/using/starting-a-workflow.md)
* [Lebenszyklus eines Workflows](../../workflow/using/workflow-life-cycle.md)
* [Bewährte Verfahren bei der Verwendung von Workflows](../../workflow/using/workflow-best-practices.md)

## Beginn so bald wie möglich in Kampagnen {#start-as-soon-as-possible-in-campaigns}

In einigen Fällen werden Workflows, die von einer Kampagne ausgeführt werden, beim Klicken auf die Schaltfläche **[!UICONTROL Beginn]** nicht Beginn. Anstatt zu beginnen, wird der Status &quot;Beginn so bald wie möglich&quot;angezeigt.

Das Problem kann verschiedene Ursachen haben. Gehen Sie wie folgt vor, um es zu beheben:

1. Überprüfen Sie den Status des technischen Workflows. [****](../../workflow/using/about-technical-workflows.md) Dieser Workflow verwaltet Aufträge oder Workflows in einer Kampagne. Wenn es fehlschlägt, führt dies dazu, dass Workflows nicht Beginn/Stopp. Starten Sie es neu, um die Kampagnen-Workflows fortzusetzen.

   Weitere Informationen zur Überwachung von Technischen Workflows finden Sie auf [dieser Seite](../../workflow/using/monitoring-technical-workflows.md).

   >[!NOTE]
   >
   >Vergewissern Sie sich nach dem Neustart des Workflows, dass Sie die ausstehenden Aufgaben ausführen (klicken Sie mit der rechten Maustaste auf die Aktivität **[!UICONTROL Planung]** / **[!UICONTROL Ausstehende Aufgabe(n) jetzt ausführen]**), um zu prüfen, ob sie auf einer der Aktivitäten erneut fehlschlägt.

   Wenn der Workflow weiterhin fehlschlägt, überprüfen Sie das Prüfprotokoll auf einen bestimmten Fehler, führen Sie eine entsprechende Fehlerbehebung durch und starten Sie den Workflow erneut neu.

1. Überprüfen Sie den Modulstatus **[!UICONTROL wfserver]** auf der Registerkarte **[!UICONTROL Monitoring]**, auf die von der Campaign Classic-Homepage zugegriffen werden kann (siehe [Überwachungsprozesse](../../production/using/monitoring-processes.md)). Dieser Prozess ist für die Ausführung aller Workflows verantwortlich.

   Ein Admin-Benutzer kann auch überprüfen, ob das Modul **wfserver@`<instance>`** mithilfe des folgenden Befehls auf Ihrem Hauptanwendungsserver gestartet wird.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   Wenn das Modul nicht ausgeführt wird, wenden Sie sich an den Kundendienst der Adobe. Wenn Sie über eine lokale Installation verfügen, muss ein Administrator den Dienst mithilfe des folgenden Befehls neu starten.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Ersetzen Sie **`<instancename>`** durch den Namen Ihrer Instanz (Produktion, Entwicklung usw.). Der Instanzname wird über die Konfigurationsdateien identifiziert:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Weitere Informationen zum Neustart von Modulen finden Sie in [diesem Abschnitt](../../production/using/usual-commands.md#module-launch-commands).

1. Überprüfen Sie, ob die **Anzahl der Kampagnen, die auf der Instanz ausgeführt werden, mehr als der Schwellenwert beträgt.** Es gibt eine Beschränkung, die durch die Option [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) definiert wird, wie viele Kampagnen parallel auf der Instanz ausgeführt werden können. Wenn diese Grenze erreicht ist, bleibt der Workflow im Status &quot;Beginn so bald wie möglich&quot;erhalten, solange die Anzahl der Workflows, die ausgeführt wird, über der Grenze liegt.

   Um dieses Problem zu lösen, beenden Sie unerwünschte Workflows und löschen Sie fehlgeschlagene Versand. Wenn der Schwellenwert erreicht wurde, können neue Prozesse ausgeführt werden.

   Um die Anzahl der Workflows zu überprüfen, die Ihre Instanz ausführt, sollten Sie die vordefinierten Ansichten verwenden, die standardmäßig im Ordner **[!UICONTROL Administration]** / **[!UICONTROL Audit]** verfügbar sind. Weitere Informationen dazu finden Sie auf dieser [Seite](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[!IMPORTANT]
   >
   >Das Erhöhen des Optionsschwellenwerts **[!UICONTROL NmsOperation_LimitConcurrency]** kann zu Leistungsproblemen in Ihrer Instanz führen. Führen Sie dies in jedem Fall nicht selbst aus und wenden Sie sich an Ihren Ansprechpartner bei Ihrem Adobe Campaign.

Weitere Informationen zur Überwachung Ihrer Workflows finden Sie in [diesem Abschnitt](../../workflow/using/monitoring-workflow-execution.md).

## Beginn läuft {#start-in-progress}

Wenn Workflows nicht ausgeführt werden und ihr Status **Beginn in Bearbeitung ist**, kann dies bedeuten, dass das Workflow-Modul nicht gestartet wird.

Um dies zu überprüfen und bei Bedarf das Modul zu starten, gehen Sie wie folgt vor:

1. Überprüfen Sie den Modulstatus **[!UICONTROL wfserver]** auf der Registerkarte **[!UICONTROL Monitoring]**, auf die von der Campaign Classic-Homepage zugegriffen werden kann (siehe [Überwachungsprozesse](../../production/using/monitoring-processes.md)).

   Ein Admin-Benutzer kann auch überprüfen, ob das Modul **wfserver@`<instance>`** mithilfe des folgenden Befehls auf Ihrem Hauptanwendungsserver gestartet wird.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   Weitere Informationen zum Überwachen von Modulen finden Sie in [diesem Abschnitt](../../production/using/usual-commands.md#monitoring-commands-).

1. Wenn das Modul nicht ausgeführt wird, wenden Sie sich an den Kundendienst der Adobe. Wenn Sie über eine lokale Installation verfügen, muss ein Administrator diese mithilfe des folgenden Befehls neu starten.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Ersetzen Sie **`<instancename>`** durch den Namen Ihrer Instanz (Produktion, Entwicklung usw.). Der Instanzname wird über die Konfigurationsdateien identifiziert:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Weitere Informationen zum Neustart von Modulen finden Sie in [diesem Abschnitt](../../production/using/usual-commands.md#module-launch-commands).

## Fehlgeschlagener Workflow {#failed-workflow}

Wenn ein Workflow fehlschlägt, gehen Sie wie folgt vor:

1. Überprüfen Sie das Workflow-Protokoll. Weitere Informationen finden Sie in den Abschnitten [Ausführen des Überwachungs-Workflows](../../workflow/using/monitoring-workflow-execution.md) und [Protokolle anzeigen](../../workflow/using/monitoring-workflow-execution.md#displaying-logs).
1. Technischen Workflows überwachen. Weitere Informationen finden Sie in diesem Abschnitt [unter ](../../workflow/using/monitoring-technical-workflows.md).
1. Suchen Sie nach Fehlern in den einzelnen Workflow-Aktivitäten.

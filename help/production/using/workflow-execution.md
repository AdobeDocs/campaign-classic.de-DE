---
product: campaign
title: Workflow-Ausführung
description: Workflow-Ausführung
feature: Monitoring, Workflows
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: b5aa5663-1902-4f50-9202-783e73a28838
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 11%

---

# Workflow-Ausführung{#workflow-execution}



Im folgenden Abschnitt finden Sie Informationen zu häufigen Problemen bei der Ausführung von Workflows und deren Fehlerbehebung.

Weiterführende Informationen zu Workflows finden Sie in den folgenden Abschnitten:

* [Über Workflows](../../workflow/using/about-workflows.md)
* [Workflow starten](../../workflow/using/starting-a-workflow.md)
* [Lebenszyklus eines Workflows](../../workflow/using/workflow-life-cycle.md)
* [Best Practices bei der Verwendung von Workflows](../../workflow/using/workflow-best-practices.md)

## Schnellstmöglicher Start in Kampagnen {#start-as-soon-as-possible-in-campaigns}

In einigen Fällen werden Workflows, die von einer Kampagne ausgeführt werden, nicht gestartet, wenn auf die Schaltfläche **[!UICONTROL Starten]** geklickt wird. Anstatt zu starten, wechselt er in den Status „So bald wie möglich starten“.

Dieses Problem kann mehrere Ursachen haben. Gehen Sie zur Lösung des Problems wie folgt vor:

1. Überprüfen Sie den [**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md) des technischen Workflows. Dieser Workflow verwaltet Vorgänge oder Workflows innerhalb einer Kampagne. Wenn dies fehlschlägt, führt dies dazu, dass Workflows nicht gestartet/angehalten werden. Starten Sie ihn neu, um die Ausführung der Kampagnen-Workflows fortzusetzen.

   Weiterführende Informationen zur Überwachung technischer Workflows finden Sie auf [dieser Seite](../../workflow/using/monitoring-technical-workflows.md).

   >[!NOTE]
   >
   >Nachdem der Workflow neu gestartet wurde, stellen Sie sicher, dass Sie die ausstehenden Aufgaben ausführen (klicken Sie mit der rechten Maustaste auf die Aktivität **[!UICONTROL Planung]** / **[!UICONTROL Ausstehende Aufgabe(n) jetzt]**), um zu überprüfen, ob er bei einer der Aktivitäten erneut fehlschlägt.

   Wenn der Workflow weiterhin fehlschlägt, überprüfen Sie das Administratorprotokoll auf bestimmte Fehler, beheben Sie die Fehler und starten Sie den Workflow erneut.

1. Überprüfen Sie den **[!UICONTROL wfserver]** auf der Registerkarte **[!UICONTROL Monitoring]**, auf die über die Campaign Classic-Homepage zugegriffen werden kann (siehe [Überwachungsprozesse](../../production/using/monitoring-processes.md)). Dieser Prozess ist für die Ausführung aller Workflows verantwortlich.

   Ein Administrator kann mit dem folgenden Befehl auch überprüfen **ob das Modul &quot;@`<instance>`**&quot; auf Ihrem Hauptanwendungsserver gestartet wurde.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   Wenn das Modul nicht ausgeführt wird, wenden Sie sich an die Adobe-Kundenunterstützung. Wenn Sie über eine On-Premise-Installation verfügen, muss ein Administrator bzw. eine Administratorin den Service mit dem folgenden Befehl neu starten.

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >Ersetzen Sie **`<instance-name>`** durch den Namen Ihrer Instanz (Produktion, Entwicklung usw.). Der Instanzname wird über die Konfigurationsdateien identifiziert:
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   Weiterführende Informationen zum Neustart von Modulen finden Sie [diesem Abschnitt](../../production/using/usual-commands.md#module-launch-commands).

1. Überprüfen Sie, ob **Anzahl der in der Instanz ausgeführten Kampagnenprozesse** größer als der Schwellenwert ist. Durch die Option [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) wird ein Limit dafür definiert, wie viele Kampagnenprozesse parallel auf der Instanz ausgeführt werden können. Wenn dieses Limit erreicht ist, bleibt der Workflow im Status „So bald wie möglich starten“, solange die Anzahl der ausgeführten Workflows das Limit überschreitet.

   Um dieses Problem zu beheben, stoppen Sie unerwünschte Workflows und löschen Sie fehlgeschlagene Sendungen. Wenn der Schwellenwert erreicht wurde, können neue Prozesse ausgeführt werden.

   Um die Anzahl der in Ihrer Instanz ausgeführten Workflows zu überprüfen, empfehlen wir die Verwendung der vordefinierten Ansichten, auf die standardmäßig im Ordner **[!UICONTROL Administration]** / **[!UICONTROL Audit]** zugegriffen werden kann. Weitere Informationen dazu finden Sie auf [dieser Seite](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[!IMPORTANT]
   >
   >Eine Erhöhung des **[!UICONTROL NmsOperation_LimitConcurrency]**-Schwellenwerts kann zu Leistungsproblemen in Ihrer Instanz führen. Führen Sie dies auf keinen Fall eigenständig durch und wenden Sie sich an Ihren Adobe Campaign-Ansprechpartner.

Weitere Informationen zum Überwachen Ihrer Workflows finden Sie in [diesem Abschnitt](../../workflow/using/monitoring-workflow-execution.md).

## Start in progress {#start-in-progress}

Wenn Workflows nicht ausgeführt werden und ihr Status **Start in Bearbeitung** lautet, kann dies bedeuten, dass das Workflow-Modul nicht gestartet wird.

Um dies zu überprüfen und bei Bedarf das Modul zu starten, gehen Sie wie folgt vor:

1. Überprüfen Sie den **[!UICONTROL wfserver]** auf der Registerkarte **[!UICONTROL Monitoring]**, auf die über die Campaign Classic-Homepage zugegriffen werden kann (siehe [Überwachungsprozesse](../../production/using/monitoring-processes.md)).

   Ein Administrator kann mit dem folgenden Befehl auch überprüfen **ob das Modul &quot;@`<instance>`**&quot; auf Ihrem Hauptanwendungsserver gestartet wurde.

   ```sql
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   Weiterführende Informationen zum Überwachen von Modulen finden Sie [diesem Abschnitt](../../production/using/usual-commands.md#monitoring-commands-).

1. Wenn das Modul nicht ausgeführt wird, wenden Sie sich an die Adobe-Kundenunterstützung. Wenn Sie über eine On-Premise-Installation verfügen, muss sie ein Administrator mithilfe des folgenden Befehls neu starten.

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >Ersetzen Sie **`<instance-name>`** durch den Namen Ihrer Instanz (Produktion, Entwicklung usw.). Der Instanzname wird über die Konfigurationsdateien identifiziert:
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   Weiterführende Informationen zum Neustart von Modulen finden Sie [diesem Abschnitt](../../production/using/usual-commands.md#module-launch-commands).

## Fehlgeschlagener Workflow {#failed-workflow}

Wenn ein Workflow fehlschlägt, führen Sie die folgenden Schritte aus:

1. Überprüfen Sie das Workflow-Journal. Weitere Informationen hierzu finden Sie in den Abschnitten [Ausführung des ](../../workflow/using/monitoring-workflow-execution.md) überwachen[ und ](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) anzeigen.
1. Überwachen technischer Workflows. Weiterführende Informationen hierzu finden Sie [ diesem Abschnitt](../../workflow/using/monitoring-technical-workflows.md).
1. Suchen Sie nach Fehlern bei den einzelnen Workflow-Aktivitäten.

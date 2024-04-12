---
product: campaign
title: Workflow-Ausführung
description: Workflow-Ausführung
feature: Monitoring, Workflows
badge-v7-prem: label="On-Premise und Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: b5aa5663-1902-4f50-9202-783e73a28838
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 11%

---

# Workflow-Ausführung{#workflow-execution}



Im folgenden Abschnitt finden Sie Informationen zu häufigen Problemen bei der Ausführung von Workflows und zur Fehlerbehebung.

Weiterführende Informationen zu Workflows finden Sie in den folgenden Abschnitten:

* [Über Workflows](../../workflow/using/about-workflows.md)
* [Workflow starten](../../workflow/using/starting-a-workflow.md)
* [Lebenszyklus eines Workflows](../../workflow/using/workflow-life-cycle.md)
* [Best Practices bei der Verwendung von Workflows](../../workflow/using/workflow-best-practices.md)

## So bald wie möglich in Kampagnen starten {#start-as-soon-as-possible-in-campaigns}

In einigen Fällen starten von einer Kampagne aus ausgeführte Workflows nicht, wenn Sie auf die **[!UICONTROL Starten]** Schaltfläche. Statt zu beginnen, wird der Status &quot;Schnellstmöglich starten&quot;angezeigt.

Es kann mehrere Ursachen für dieses Problem geben. Gehen Sie zur Lösung des Problems wie folgt vor:

1. Überprüfen Sie die [**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md) Status des technischen Workflows. Dieser Workflow verwaltet Aufträge oder Workflows innerhalb einer Kampagne. Schlägt dies fehl, werden Workflows nicht gestartet/angehalten. Starten Sie es neu, um die Ausführung der Kampagnen-Workflows wiederaufzunehmen.

   Weitere Informationen zur Überwachung technischer Workflows finden Sie unter [diese Seite](../../workflow/using/monitoring-technical-workflows.md).

   >[!NOTE]
   >
   >Nachdem der Workflow neu gestartet wurde, müssen Sie die ausstehenden Aufgaben ausführen (klicken Sie mit der rechten Maustaste auf die **[!UICONTROL Planung]** activity / **[!UICONTROL Ausstehende Aufgabe(n) jetzt ausführen]**), um zu überprüfen, ob es bei einer der Aktivitäten erneut fehlschlägt.

   Wenn der Workflow weiterhin fehlschlägt, überprüfen Sie das Auditprotokoll auf einen bestimmten Fehler, führen Sie eine entsprechende Fehlerbehebung durch und starten Sie den Workflow dann erneut neu.

1. Überprüfen Sie die **[!UICONTROL wfserver]** Modulstatus in der **[!UICONTROL Überwachung]** Registerkarte, auf die über die Campaign Classic-Homepage zugegriffen werden kann (siehe [Überwachungsverfahren](../../production/using/monitoring-processes.md)). Dieser Prozess ist für die Ausführung aller Workflows verantwortlich.

   Ein Admin-Benutzer kann auch überprüfen, ob die Variable **wfserver@`<instance>`** auf Ihrem Hauptanwendungsserver mithilfe des folgenden Befehls gestartet.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   Wenn das Modul nicht ausgeführt wird, wenden Sie sich an die Adobe-Kundenunterstützung. Wenn Sie über eine On-Premise-Installation verfügen, muss ein Administrator den Dienst mit dem folgenden Befehl neu starten.

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >Ersetzen Sie **`<instance-name>`** durch den Namen Ihrer Instanz (Produktion, Entwicklung usw.). Der Instanzname wird über die Konfigurationsdateien identifiziert:
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   Weitere Informationen zum Neustart von Modulen finden Sie unter [diesem Abschnitt](../../production/using/usual-commands.md#module-launch-commands).

1. Überprüfen Sie, ob die **Anzahl der ausgeführten Kampagnenprozesse** auf der Instanz größer als der Schwellenwert ist. Es gibt eine Begrenzung, die durch die Variable [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) Option zur Angabe, wie viele Kampagnenprozesse parallel auf der Instanz ausgeführt werden können. Wenn diese Grenze erreicht ist, bleibt der Workflow im Status &quot;Schnellstmöglicher Start&quot;, solange die Anzahl der ausgeführten Workflows über der Grenze liegt.

   Um dieses Problem zu beheben, stoppen Sie unerwünschte Workflows und löschen Sie fehlgeschlagene Sendungen. Wenn der Schwellenwert erreicht wurde, ermöglicht dies die Ausführung neuer Prozesse.

   Um die Anzahl der ausgeführten Workflows Ihrer Instanz zu überprüfen, empfehlen wir die Verwendung der vordefinierten Ansichten, auf die standardmäßig im **[!UICONTROL Administration]** / **[!UICONTROL Prüfung]** Ordner. Weitere Informationen dazu finden Sie auf [dieser Seite](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[!IMPORTANT]
   >
   >Erhöhen Sie die **[!UICONTROL NmsOperation_LimitConcurrency]** -Optionsschwellenwert kann zu Leistungsproblemen in Ihrer Instanz führen. Führen Sie dies auf keinen Fall allein durch und kontaktieren Sie Ihren Ansprechpartner bei Adobe Campaign.

Weitere Informationen zur Überwachung Ihrer Workflows finden Sie in [diesem Abschnitt](../../workflow/using/monitoring-workflow-execution.md).

## In Bearbeitung {#start-in-progress}

Wenn Workflows nicht ausgeführt werden und ihr Status lautet **In Bearbeitung** kann dies bedeuten, dass das Workflow-Modul nicht gestartet wird.

Um dies zu überprüfen und bei Bedarf das Modul zu starten, gehen Sie wie folgt vor:

1. Überprüfen Sie die **[!UICONTROL wfserver]** Modulstatus in der **[!UICONTROL Überwachung]** Registerkarte, auf die über die Campaign Classic-Homepage zugegriffen werden kann (siehe [Überwachungsverfahren](../../production/using/monitoring-processes.md)).

   Ein Admin-Benutzer kann auch überprüfen, ob die Variable **wfserver@`<instance>`** auf Ihrem Hauptanwendungsserver mithilfe des folgenden Befehls gestartet.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   Weitere Informationen zum Überwachen von Modulen finden Sie unter [diesem Abschnitt](../../production/using/usual-commands.md#monitoring-commands-).

1. Wenn das Modul nicht ausgeführt wird, wenden Sie sich an die Adobe-Kundenunterstützung. Wenn Sie über eine On-Premise-Installation verfügen, muss ein Administrator sie mit dem folgenden Befehl neu starten.

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >Ersetzen Sie **`<instance-name>`** durch den Namen Ihrer Instanz (Produktion, Entwicklung usw.). Der Instanzname wird über die Konfigurationsdateien identifiziert:
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   Weitere Informationen zum Neustart von Modulen finden Sie unter [diesem Abschnitt](../../production/using/usual-commands.md#module-launch-commands).

## Fehlgeschlagener Workflow {#failed-workflow}

Wenn ein Workflow fehlschlägt, führen Sie die folgenden Schritte aus:

1. Überprüfen Sie das Workflow-Protokoll. Weitere Informationen hierzu finden Sie im Abschnitt [Ausführung des Workflows überwachen](../../workflow/using/monitoring-workflow-execution.md) und [Protokoll anzeigen](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) Abschnitte.
1. Technische Workflows überwachen Weitere Informationen hierzu finden Sie unter [diesem Abschnitt](../../workflow/using/monitoring-technical-workflows.md).
1. Suchen Sie nach Fehlern bei den einzelnen Workflow-Aktivitäten.

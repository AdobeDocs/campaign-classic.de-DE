---
product: campaign
title: Datenbankbereinigungs-Workflow
description: Erfahren Sie, wie veraltete Daten automatisch bereinigt werden
feature: Monitoring, Workflows
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 75d3a0af-9a14-4083-b1da-2c1b22f57cbe
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '2916'
ht-degree: 1%

---

# Datenbankbereinigungs-Workflow{#database-cleanup-workflow}



## Einleitung {#introduction}

Der Workflow **[!UICONTROL Datenbankbereinigung]**, auf den Sie über den Knoten **[!UICONTROL Administration > Produktion > Technische Workflows]** zugreifen können, ermöglicht das Löschen veralteter Daten, um das exponentielle Anwachsen der Datenbank zu verhindern. Der Workflow wird automatisch ohne das Eingreifen der benutzenden Person ausgelöst.

![Bereinigung](assets/ncs_cleanup_workflow.png)

## Konfiguration {#configuration}

Die Datenbankbereinigung wird auf zwei Ebenen konfiguriert: im Workflow-Planer und im Bereitstellungsassistenten.

### Workflow-Planung {#the-scheduler}

>[!NOTE]
>
>Weitere Informationen zur Planung finden Sie in der [ zu Campaign v8 ](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/flow-control-activities/scheduler.html?lang=de){target="_blank"}.

Standardmäßig ist der Workflow **[!UICONTROL Datenbankbereinigung]** so konfiguriert, dass er täglich um 4 Uhr morgens startet. Mit der -Planung können Sie die Häufigkeit der Workflow-Auslösung ändern. Die folgenden Häufigkeiten sind verfügbar:

* **[!UICONTROL Mehrmals täglich]**
* **[!UICONTROL Täglich]**
* **[!UICONTROL Wöchentlich]**
* **[!UICONTROL Einmal]**

![Planung](assets/ncs_cleanup_scheduler.png)

>[!IMPORTANT]
>
>Damit der Workflow **[!UICONTROL Datenbankbereinigung]** an dem in der Planung definierten Datum und zu der in der Planung definierten Uhrzeit gestartet wird, muss die Workflow-Engine (wfserver) gestartet werden.

### Bereitstellungsassistent {#deployment-assistant}

Über **[!UICONTROL Menü]** Tools > Erweitert **[!UICONTROL können Sie mit dem Bereitstellungsassistenten]**, wie lange Daten gespeichert werden sollen. Werte werden in Tagen ausgedrückt. Wenn diese Werte nicht geändert werden, verwendet der Workflow die Standardwerte.

![](assets/ncs_cleanup_deployment-wizard.png)

Die Felder des Fensters **[!UICONTROL Bereinigen von Daten]** entsprechen den folgenden Optionen. Diese werden von einigen der Aufgaben verwendet, die vom Workflow **[!UICONTROL Datenbankbereinigung]** ausgeführt werden:

* Konsolidiertes Tracking: **NmsCleanup_TrackingStatPurgeDelay** (siehe [Bereinigung von Trackinglogs](#cleanup-of-tracking-logs))
* Versandlogs: **NmsCleanup_BroadLogPurgeDelay** (siehe [Bereinigung von Versandlogs](#cleanup-of-delivery-logs))
* Trackinglogs: **NmsCleanup_TrackingLogPurgeDelay** (siehe &quot;[ von Trackinglogs](#cleanup-of-tracking-logs))
* Gelöschte Sendungen: **NmsCleanup_RecycledDeliveryPurgeDelay** (siehe [Bereinigung von zu löschenden oder wiederzuverwendenden Sendungen](#cleanup-of-deliveries-to-be-deleted-or-recycled))
* Importzurückweisungen: **NmsCleanup_RejectsPurgeDelay** (siehe [Bereinigung von durch Importe generierten Zurückweisungen](#cleanup-of-rejects-generated-by-imports-))
* Besucherprofile: **NmsCleanup_VisitorPurgeDelay** (siehe &quot;[ von Besuchern](#cleanup-of-visitors))
* Angebotsvorschläge: **NmsCleanup_PropositionPurgeDelay** (siehe [Bereinigung von Vorschlägen](#cleanup-of-propositions))

  >[!NOTE]
  >
  >Das Feld **[!UICONTROL Angebotsvorschläge]** ist nur verfügbar, wenn das Modul **Interaction** installiert ist.

* Ereignisse: **NmsCleanup_EventPurgeDelay** (siehe [Löschen abgelaufener Ereignisse](#cleansing-expired-events))
* Archivierte Ereignisse: **NmsCleanup_EventHistoPurgeDelay** (siehe [Bereinigen abgelaufener Ereignisse](#cleansing-expired-events))

  >[!NOTE]
  >
  >Die Felder **[!UICONTROL Ereignisse]** und **[!UICONTROL Ereignisse mit Verlauf]** sind nur verfügbar, wenn das Modul **Message Center** installiert ist.

* Audit-Protokoll: **XtkCleanup_AuditTrailPurgeDelay** (siehe &quot;[ des Audit-Protokolls](#cleanup-of-audit-trail))

Alle Aufgaben, die vom Workflow **[!UICONTROL Datenbankbereinigung]** ausgeführt werden, werden im folgenden Abschnitt beschrieben.

## Aufgaben, die vom Datenbankbereinigungs-Workflow ausgeführt werden {#tasks-carried-out-by-the-database-cleanup-workflow}

Die Workflow-Engine startet den Datenbankbereinigungsprozess zu dem in der Workflow-Planung [siehe &quot;](#the-scheduler)„) festgelegten Zeitpunkt. Die Datenbankbereinigung stellt eine Verbindung zur Datenbank her und führt die Aufgaben in der unten gezeigten Reihenfolge aus.

>[!IMPORTANT]
>
>Wenn eine dieser Aufgaben fehlschlägt, werden die nächsten nicht ausgeführt.
>
>SQL-Abfragen mit **LIMIT**-Attribut werden wiederholt ausgeführt, bis alle Informationen verarbeitet werden.


### Zu löschende Listen {#lists-to-delete-cleanup}

Die erste Aufgabe, die vom Workflow **[!UICONTROL Datenbankbereinigung]** ausgeführt wird, löscht alle Gruppen mit dem **deleteStatus != 0** Attribut aus der **NmsGroup**. Mit diesen Gruppen verknüpfte Datensätze, die in anderen Tabellen vorhanden sind, werden ebenfalls gelöscht.

1. Zu löschende Listen werden mithilfe der folgenden SQL-Abfrage wiederhergestellt:

   ```sql
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. Jede Liste enthält mehrere Verknüpfungen zu anderen Tabellen. Alle diese Links werden mithilfe der folgenden Abfrage stapelweise gelöscht:

   ```sql
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   Dabei ist `$(relatedTable)` eine mit **NmsGroup** verknüpfte Tabelle und `$(l)` die Listenkennung.

1. Wenn es sich bei der Liste um eine Liste vom Typ „Liste“ handelt, wird die zugehörige Tabelle mithilfe der folgenden Abfrage gelöscht:

   ```sql
   DROP TABLE grp$(l)
   ```

1. Jede **vom Vorgang** Select“ wiederhergestellte Liste wird mithilfe der folgenden Abfrage gelöscht:

   ```sql
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   wobei `$(l)` die Listenkennung ist

### Bereinigung der zu löschenden oder wiederzuverwertenden Sendungen {#cleanup-of-deliveries-to-be-deleted-or-recycled}

Diese Aufgabe löscht alle Sendungen, die gelöscht oder recycelt werden sollen.

1. Der Workflow **[!UICONTROL Datenbankbereinigung]** wählt alle Sendungen aus, für die das Feld **deleteStatus** den Wert **[!UICONTROL Ja]** oder **[!UICONTROL Recycled]** aufweist und deren Löschdatum vor dem Zeitraum liegt, der im Feld **[!UICONTROL Gelöschte Sendungen]** (**NmsCleanup_RecycledDeliveryPurgeDelay**) des Bereitstellungsassistenten definiert ist. Weitere Informationen hierzu finden Sie unter [Bereitstellungsassistent](#deployment-assistant). Dieser Zeitraum wird in Bezug auf das aktuelle Serverdatum berechnet.
1. Für jeden Mid-Sourcing-Server wählt die Aufgabe die Liste der zu löschenden Sendungen aus.
1. Der **[!UICONTROL Datenbankbereinigung]** löscht Versandlogs, Anhänge, Informationen zur Mirrorseite und alle anderen damit verbundenen Daten.
1. Bevor der Versand endgültig gelöscht wird, löscht der Workflow verknüpfte Informationen aus den folgenden Tabellen:

   * In der Versandausschlusstabelle (**NmsDlvExclusion**) wird die folgende Abfrage verwendet:

     ```sql
     DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
     ```

     wobei **$(l)** die Kennung des Versands ist.

   * In der Coupontabelle (**NmsCouponValue**) wird die folgende Abfrage verwendet (bei Massenlöschungen):

     ```sql
     DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
     ```

     wobei `$(l)` die Kennung des Versands ist.

   * In den Versandlog-Tabellen **NmsBroadlogXxx**) werden Massenlöschungen in Batches mit 20.000 Datensätzen ausgeführt.
   * In den Angebotsvorschlags-Tabellen (**NmsPropositionXxx**) werden Massenlöschungen in Batches mit 20.000 Datensätzen ausgeführt.
   * In den Trackinglog-Tabellen (**NmsTrackinglogXxx**) werden Massenlöschungen in Batches mit 20.000 Datensätzen ausgeführt.
   * In der Versandfragmenttabelle (**NmsDeliveryPart**) werden Massenlöschungen in Batches mit 500.000 Datensätzen ausgeführt. Diese Tabelle enthält Personalisierungsinformationen zu den verbleibenden zu versendenden Nachrichten.
   * In der Datenfragmenttabelle der Mirrorseite (**NmsMirrorPageInfo**) werden Massenlöschungen in Batches mit 20.000 Datensätzen für abgelaufene Versandkontingente sowie für fertige oder abgebrochene Versandkontingente ausgeführt. Diese Tabelle enthält Personalisierungsinformationen zu allen Nachrichten, die für die Erstellung von Mirrorseiten verwendet werden.
   * In der Suchtabelle für die Mirrorseite **NmsMirrorPageSearch**) werden Löschvorgänge für große Datenmengen in Batches mit 20.000 Datensätzen ausgeführt. Diese Tabelle ist ein Suchindex, der Zugriff auf Personalisierungsinformationen bietet, die in der Tabelle **NmsMirrorPageInfo** gespeichert sind.
   * In der Protokolltabelle für Batch-Prozesse **XtkJobLog**) werden Massenlöschungen in Batches mit 20.000 Datensätzen ausgeführt. Diese Tabelle enthält das Protokoll der zu löschenden Sendungen.
   * In der Tracking-Tabelle der Versand **URL (NmsTrackingUrl**) wird die folgende Abfrage verwendet:

     ```sql
     DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
     ```

     wobei `$(l)` die Kennung des Versands ist.

     Diese Tabelle enthält die URLs, die in den zu löschenden Sendungen gefunden wurden, um deren Tracking zu aktivieren.

1. Der Versand wird aus der Versandtabelle gelöscht (**NmsDelivery**):

   ```sql
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   wobei `$(l)` die Kennung des Versands ist.

#### Sendungen im Mid-Sourcing-Modus {#deliveries-using-mid-sourcing}

Der **[!UICONTROL Datenbankbereinigung]** löscht auch Sendungen auf dem/den Mid-Sourcing-Server(n).

1. Zu diesem Zweck prüft der Workflow (anhand des Status), ob jeder Versand inaktiv ist. Wenn ein Versand aktiv ist, wird er gestoppt, bevor er gelöscht wird. Die Prüfung wird durch Ausführen der folgenden Abfrage ausgeführt:

   ```sql
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   wobei **$(l)** die Kennung des Versands ist.

1. Wenn der Wert des Status **[!UICONTROL Start ausstehend]** , **[!UICONTROL In Bearbeitung]** , **[!UICONTROL Wiederherstellung ausstehend]** , **[!UICONTROL Wiederherstellung läuft]** , **[!UICONTROL Pause angefordert]** , **[!UICONTROL Pause in Bearbeitung]** oder **[!UICONTROL Paused]** (Werte 51, 55, 61, 62, 71, 72, 75) ist, wird der Versand gestoppt und die Aufgabe löscht die verknüpften Informationen.

### Bereinigung abgelaufener Sendungen {#cleanup-of-expired-deliveries}

Diese Aufgabe stoppt Sendungen, deren Gültigkeitszeitraum abgelaufen ist.

1. Der **[!UICONTROL Datenbankbereinigung]** erstellt die Liste der Sendungen, die abgelaufen sind. Diese Liste enthält alle abgelaufenen Sendungen mit einem anderen Status als **[!UICONTROL Abgeschlossen]** sowie kürzlich gestoppte Sendungen mit über 10.000 nicht verarbeiteten Nachrichten. Die folgende Abfrage wird verwendet:

   ```sql
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   wobei `delivery mode 1` dem Modus **[!UICONTROL Massenversand]** entspricht, `state 51` dem Status **[!UICONTROL Start ausstehend]** entspricht, `state 85` dem Status **[!UICONTROL Gestoppt]** entspricht und die höchste Anzahl von Versandlogs, die auf dem Versand-Server massenweise aktualisiert wurde, 10.000 beträgt.

1. Der Workflow enthält dann die Liste der kürzlich abgelaufenen Sendungen, die Mid-Sourcing verwenden. Sendungen, für die noch keine Versandlogs über den Mid-Sourcing-Server wiederhergestellt wurden, sind ausgeschlossen.

   Die folgende Abfrage wird verwendet:

   ```sql
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. Die folgende Abfrage wird verwendet, um zu ermitteln, ob das externe Konto noch aktiv ist, und um Sendungen nach Datum zu filtern:

   ```sql
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. In der Liste der abgelaufenen Sendungen wechseln Versandlogs mit dem Status **[!UICONTROL Ausstehend]** , zu **[!UICONTROL Versand abgebrochen]** und alle Sendungen in dieser Liste zu **[!UICONTROL Beendet]** .

   Die folgenden Abfragen werden verwendet:

   ```sql
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   wobei `$(curdate)`das aktuelle Datum des Datenbank-Servers ist, `$(bl)` die Kennung der Versandlogmeldung ist, `$(dl)` die Versandkennung ist, `delivery status 6` mit dem Status **[!UICONTROL Ausstehend]** übereinstimmt und `delivery status 7` mit dem Status **[!UICONTROL Versand abgebrochen]** übereinstimmt.

   ```sql
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   `delivery state 95` entspricht dem Status **[!UICONTROL Abgeschlossen]** und `$(dl)` ist die Kennung des Versands.

1. Alle Fragmente (**deliveryParts**) von veralteten Sendungen werden gelöscht und alle veralteten Fragmente von laufenden Benachrichtigungs-Sendungen werden gelöscht. Für diese beiden Aufgaben wird das Löschen großer Datenmengen verwendet.

   Die folgenden Abfragen werden verwendet:

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   wobei `delivery state 95` mit dem **[!UICONTROL Beendet]**-Status übereinstimmt, `delivery state 85` mit dem **[!UICONTROL Angehalten]**-Status übereinstimmt und `$(curDate)` das aktuelle Server-Datum ist.

### Bereinigung der Mirrorseiten {#cleanup-of-mirror-pages}

Diese Aufgabe löscht die Web-Ressourcen (Mirrorseiten), die von Sendungen verwendet werden.

1. Zunächst wird die Liste der zu bereinigenden Sendungen mithilfe der folgenden Abfrage abgerufen:

   ```sql
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)
   ```

   wobei `$(curDate)` das aktuelle Serverdatum ist.

1. Die **NmsMirrorPageInfo**-Tabelle wird dann bereinigt, falls erforderlich unter Verwendung der Kennung des zuvor wiederhergestellten Versands. Die Massenlöschung wird verwendet, um die folgenden Abfragen zu generieren:

   ```sql
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000
   ```

   ```sql
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000
   ```

   wobei `$(dl)` die Kennung des Versands ist.

1. Dem Versandlog wird dann ein Eintrag hinzugefügt.
1. Bereinigte Sendungen werden dann identifiziert, um zu vermeiden, dass sie später erneut verarbeitet werden müssen. Die folgende Abfrage wird ausgeführt:

   ```sql
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   wobei `$(strIn)` die Liste der Versandkennungen ist.

### Bereinigung der Arbeitstabellen {#cleanup-of-work-tables}

Diese Aufgabe löscht aus der Datenbank alle Arbeitstabellen, die mit Sendungen übereinstimmen, deren Status **[!UICONTROL In Bearbeitung]** , **[!UICONTROL Angehalten]** oder **[!UICONTROL Gelöscht]** lautet.

1. Die Liste der Tabellen mit Namen, die mit **wkDlv_** beginnen, wird zuerst mit der folgenden Abfrage (PostgreSQL) abgerufen:

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. Die von laufenden Workflows verwendeten Tabellen werden dann ausgeschlossen. Hierfür wird die Liste der laufenden Sendungen mithilfe der folgenden Abfrage abgerufen:

   ```sql
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   wobei `0` der Wert ist, der mit dem Versandstatus **[!UICONTROL wird bearbeitet]** übereinstimmt, `85` mit dem Status **[!UICONTROL Gestoppt]** übereinstimmt und `100` mit dem Status **[!UICONTROL Gelöscht]** übereinstimmt.

1. Nicht mehr verwendete Tabellen werden mithilfe der folgenden Abfrage gelöscht:

   ```sql
   DROP TABLE wkDlv_15487_1;
   ```

### Bereinigung der durch Importe erzeugten Zurückweisungen {#cleanup-of-rejects-generated-by-imports-}

In diesem Schritt können Sie Datensätze löschen, für die nicht alle Daten beim Import verarbeitet wurden.

1. Das Löschen großer Datenmengen wird für die Tabelle **XtkReject** mit der folgenden Abfrage ausgeführt:

   ```sql
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l)
   ```

   wobei `$(curDate)` das aktuelle Serverdatum ist, von dem der für die Option **NmsCleanup_RejectsPurgeDelay** definierte Zeitraum abgezogen wird (siehe [Bereitstellungsassistent](#deployment-assistant)) und `$(l)` die maximale Anzahl von Datensätzen ist, die massenweise gelöscht werden sollen.

1. Alle verwaisten Zurückweisungen werden dann mithilfe der folgenden Abfrage gelöscht:

   ```sql
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### Bereinigung von Workflow-Instanzen {#cleanup-of-workflow-instances}

Diese Aufgabe löscht jede Workflow-Instanz mithilfe ihrer Kennung (**lWorkflowId**) und ihres Verlaufs (**lHistory**). Inaktive Tabellen werden gelöscht, indem die Bereinigung der Arbeitstabelle erneut ausgeführt wird. Die Bereinigung löscht auch alle verwaisten Arbeitstabellen (wkf% und wkhisto%) gelöschter Workflows.

>[!NOTE]
>
>Die Bereinigungshäufigkeit des Verlaufs wird für jeden Workflow im Feld &quot;**in Tagen“** Standardwert 30 Tage). Dieses Feld befindet sich auf der Registerkarte **Ausführung** der Workflow-Eigenschaften. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../workflow/using/workflow-properties.md#execution).

1. Um die Liste der zu löschenden Workflows abzurufen, wird die folgende Abfrage verwendet:

   ```sql
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. Diese Abfrage generiert die Liste der Workflows, die zum Löschen aller verknüpften Protokolle, abgeschlossenen Aufgaben und abgeschlossenen Ereignisse verwendet werden, indem die folgenden Abfragen verwendet werden:

   ```sql
   DELETE FROM XtkWorkflowLog WHERE iWorkflowId=$(lworkflow) AND tsLog < DateMinusDays($(lhistory))
   ```

   ```sql
   DELETE FROM XtkWorkflowTask WHERE iWorkflowId=$(lworkflow) AND iStatus<>0 AND tsCompletion < DateMinusDays($(lhistory)) 
   ```

   ```sql
   DELETE FROM XtkWorkflowEvent WHERE iWorkflowId=$(l) AND iStatus>2 AND tsProcessing < DateMinusDays($(lHistory))
   ```

   Dabei ist `$(lworkflow)` die Kennung des Workflows und `$(lhistory)` die Kennung des Verlaufs.

1. Alle nicht verwendeten Tabellen werden gelöscht. Zu diesem Zweck werden alle Tabellen mithilfe einer Maske vom Typ **wkf%** mithilfe der folgenden Abfrage (PostgreSQL) erfasst:

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. Dann werden alle Tabellen ausgeschlossen, die von einer ausstehenden Workflow-Instanz verwendet werden. Die Liste der aktiven Workflows wird mithilfe der folgenden Abfrage abgerufen:

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. Jede Workflow-Kennung wird dann wiederhergestellt, um den Namen der von laufenden Workflows verwendeten Tabellen zu finden. Diese Namen sind von der Liste der zuvor wiederhergestellten Tabellen ausgeschlossen.
1. Aktivitätshistorientabellen vom Typ „Inkrementelle Abfrage“ werden mithilfe der folgenden Abfragen ausgeschlossen:

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   Dabei `$(strcondition)` die Liste der Tabellen, die der **wkfhisto%** entsprechen.

1. Die verbleibenden Tabellen werden mithilfe der folgenden Abfrage gelöscht:

   ```sql
   DROP TABLE wkf15487_12;
   ```

### Bereinigung von Workflow-Anmeldungen {#cleanup-of-workflow-logins}

Diese Aufgabe löscht Workflow-Anmeldungen mithilfe der folgenden Abfrage:

```sql
DELETE FROM XtkWorkflowLogin WHERE iWorkflowId NOT IN (SELECT iWorkflowId FROM XtkWorkflow)
```

### Bereinigung verwaister Arbeitstabellen {#cleanup-of-orphan-work-tables}

Diese Aufgabe löscht verwaiste Arbeitstabellen, die mit Gruppen verknüpft sind. Die **NmsGroup**-Tabelle speichert die zu bereinigenden Gruppen (mit einem anderen Typ als 0). Das Präfix der Tabellennamen lautet **grp**. Um die zu bereinigenden Gruppen zu identifizieren, wird die folgende Abfrage verwendet:

```sql
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### Bereinigung von Besuchern {#cleanup-of-visitors}

Diese Aufgabe löscht veraltete Datensätze aus der Besuchertabelle mithilfe von Massenlöschung. Veraltete Datensätze sind diejenigen, bei denen die letzte Änderung vor dem im Bereitstellungsassistenten definierten Erhaltungszeitraum liegt (siehe [Bereitstellungsassistent](#deployment-assistant)). Die folgende Abfrage wird verwendet:

```sql
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < AddDays(GetDate(), -30) AND iOrigin = 0 LIMIT 20000)
```

wobei `$(tsDate)` das aktuelle Serverdatum ist, von dem der für die Option **NmsCleanup_VisitorPurgeDelay** definierte Zeitraum abgezogen wird.

### Bereinigung von NPAI {#cleanup-of-npai}

Mit dieser Aufgabe können Sie Datensätze, die mit gültigen Adressen übereinstimmen, aus der Tabelle **NmsAddress** löschen. Die folgende Abfrage wird verwendet, um eine Massenlöschung durchzuführen:

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

wobei `status 2` mit dem Status **[!UICONTROL Valid]** übereinstimmt, `$(tsDate1)` das aktuelle Serverdatum ist und `$(tsDate2)` mit der Option **NmsCleanup_LastCleanup** übereinstimmt.

### Bereinigung von Abonnements {#cleanup-of-subscriptions-}

Diese Aufgabe löscht alle Abonnements, die vom Benutzer aus der Tabelle **NmsSubscription** gelöscht wurden, mithilfe der Massenlöschung. Die folgende Abfrage wird verwendet:

```sql
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### Bereinigung der Trackinglogs {#cleanup-of-tracking-logs}

Diese Aufgabe löscht veraltete Datensätze aus den Trackinglog- und Webtrackinglog-Tabellen. Veraltete Datensätze liegen vor dem im Bereitstellungsassistenten definierten Erhaltungszeitraum (siehe &quot;[-Assistent](#deployment-assistant)).

1. Zunächst wird die Liste der Trackinglog-Tabellen mithilfe der folgenden Abfrage abgerufen:

   ```sql
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. Die Massenlöschung wird verwendet, um alle Tabellen in der Liste der zuvor wiederhergestellten Tabellen zu bereinigen. Die folgende Abfrage wird verwendet:

   ```sql
   DELETE FROM NmsTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM NmsTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   wobei `$(tsDate)` das aktuelle Serverdatum ist, von dem der für die Option **NmsCleanup_TrackingLogPurgeDelay** definierte Zeitraum abgezogen wird.

1. Die Tracking-Statistiktabelle wird mithilfe der Massenlöschung gelöscht. Die folgende Abfrage wird verwendet:

   ```sql
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   wobei `$(tsDate)` das aktuelle Serverdatum ist, von dem der für die Option **NmsCleanup_TrackingStatPurgeDelay** definierte Zeitraum abgezogen wird.

### Bereinigung der Versandlogs {#cleanup-of-delivery-logs}

Mit dieser Aufgabe können Sie die in verschiedenen Tabellen gespeicherten Versandlogs bereinigen.

1. Zu diesem Zweck wird die Liste der Versandlog-Schemata mithilfe der folgenden Abfrage abgerufen:

   ```sql
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. Bei Verwendung von Mid-Sourcing wird die **NmsBroadLogMid**-Tabelle in Versandzuordnungen nicht referenziert. Das **nms:broadLogMid**-Schema wird der Liste hinzugefügt, die von der vorherigen Abfrage abgerufen wurde.
1. Der **Datenbankbereinigung** löscht dann veraltete Daten aus zuvor wiederhergestellten Tabellen. Die folgende Abfrage wird verwendet:

   ```sql
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   wobei `$(tableName)` der Name jeder Tabelle in der Liste der Schemata ist und `$(option)` das Datum ist, das für die Option **NmsCleanup_BroadLogPurgeDelay** definiert ist (siehe [Bereitstellungsassistent](#deployment-assistant)).

1. Schließlich prüft der Workflow, ob die **NmsProviderMsgId** vorhanden ist. Wenn ja, werden alle veralteten Daten mithilfe der folgenden Abfrage gelöscht:

   ```sql
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   wobei `$(option)` mit dem für die Option **NmsCleanup_BroadLogPurgeDelay** definierten Datum übereinstimmt (siehe [Bereitstellungsassistent](#deployment-assistant)).

### Bereinigung der NmsEmailErrorStat-Tabelle {#cleanup-of-the-nmsemailerrorstat-table-}

Diese Aufgabe bereinigt die Tabelle **NmsEmailErrorStat**. Das Hauptprogramm (**coalesceErrors**) definiert zwei Daten:

* **Startdatum**: Datum des nächsten Prozesses, der mit der Option **NmsLastErrorStatCoalesce** oder dem neuesten Datum in der Tabelle übereinstimmt.
* **Enddatum**: Aktuelles Serverdatum.

Wenn das Startdatum größer oder gleich dem Enddatum ist, findet kein Prozess statt. In diesem Fall wird die Meldung **coalesceUpToDate** angezeigt.

Wenn das Startdatum vor dem Enddatum liegt, wird die Tabelle **NmsEmailErrorStat** bereinigt.

Die Gesamtzahl der Fehler in der Tabelle **NmsEmailErrorStat** zwischen dem Start- und dem Enddatum wird mithilfe der folgenden Abfrage wiederhergestellt:

```sql
SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)
```

wobei `$end` und `$start` die zuvor definierten Start- und Enddaten sind.

Wenn die Gesamtzahl größer als 0 ist:

1. Die folgende Abfrage wird ausgeführt, um nur Fehler über einen bestimmten Schwellenwert (gleich 20) hinaus zu speichern:

   ```sql
   SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20
   ```

1. Die **coalescingErrors** wird angezeigt.
1. Eine neue Verbindung wird erstellt, um alle Fehler zu löschen, die zwischen dem Start- und Enddatum aufgetreten sind. Die folgende Abfrage wird verwendet:

   ```sql
   DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)
   ```

1. Jeder Fehler wird mithilfe **folgenden Abfrage in der** „NmsEmailErrorStat“ gespeichert:

   ```sql
   INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))
   ```

   wobei jede Variable mit einem Wert übereinstimmt, der von der vorherigen Abfrage abgerufen wurde.

1. Die **start**-Variable wird mit den Werten des vorherigen Prozesses aktualisiert, um die Schleife zu beenden.

Die Schleife und die Aufgabe stoppen.

Bereinigungen werden für die Tabellen **NmsEmailError** und **cleanupNmsMxDomain** ausgeführt.

### Bereinigung der NmsEmailError-Tabelle {#cleanup-of-the-nmsemailerror-table-}

Die folgende Abfrage wird verwendet:

```sql
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Diese Abfrage löscht alle Zeilen ohne verknüpfte Datensätze in **NmsEmailErrorStat** aus der Tabelle **NmsEmailError**.

### Bereinigung der NmsMxDomain-Tabelle {#cleanup-of-the-nmsmxdomain-table-}

Die folgende Abfrage wird verwendet:

```sql
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Diese Abfrage löscht alle Zeilen ohne verknüpften Datensatz in der Tabelle **NmsEmailErrorStat** aus der Tabelle **NmsMxDomain**.

### Vorschlagsbereinigung {#cleanup-of-propositions}

Wenn das **Interaction**-Modul installiert ist, wird diese Aufgabe ausgeführt, um die **NmsPropositionXxx**-Tabellen zu bereinigen.

Die Liste der Vorschlagstabellen wird abgerufen und die Massenlöschung wird für jede Tabelle mithilfe der folgenden Abfrage durchgeführt:

```sql
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

wobei `$(option)` das für die Option **NmsCleanup_PropositionPurgeDelay** definierte Datum ist (siehe [Bereitstellungsassistent](#deployment-assistant)).

### Bereinigung der Simulationstabellen {#cleanup-of-simulation-tables}

Diese Aufgabe bereinigt verwaiste Simulationstabellen (die nicht mehr mit einer Angebotssimulation oder Versandsimulation verknüpft sind).

1. Um die Liste der Simulationen abzurufen, für die eine Bereinigung erforderlich ist, wird die folgende Abfrage verwendet:

   ```sql
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. Der Name der zu löschenden Tabellen besteht aus dem Präfix **wkSimu_**, gefolgt von der Kennung der Simulation (zum Beispiel: **wkSimu_456831_aggr**):

   ```sql
   DROP TABLE wkSimu_456831_aggr
   ```

### Bereinigung des Audit-Protokolls {#cleanup-of-audit-trail}

Die folgende Abfrage wird verwendet:

```sql
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

wobei **$(tsDate)** das aktuelle Serverdatum ist, von dem der für die Option **XtkCleanup_AuditTrailPurgeDelay** definierte Zeitraum abgezogen wird.

### Bereinigung von NmsAddress {#cleanup-of-nmsaddress}

Die folgende Abfrage wird verwendet:

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=STATUS_QUARANTINE AND tsLastModified < $(NmsCleanup_AppSubscriptionRcpPurgeDelay + 5d) AND iType IN (MESSAGETYPE_IOS, MESSAGETYPE_ANDROID ) LIMIT 5000)
```

Diese Abfrage löscht alle Einträge im Zusammenhang mit iOS und Android.

### Statistikaktualisierung und Speicheroptimierung {#statistics-update}

Mit **Option „XtkCleanup_NoStats** können Sie das Verhalten des Speicheroptimierungsschritts des Bereinigungs-Workflows steuern.

Wenn die Option **XtkCleanup_NoStats** nicht vorhanden ist oder ihr Wert 0 ist, wird die Speicheroptimierung im Verbose-Modus (VACUUM VERBOSE ANALYZE) auf PostgreSQL ausgeführt und die Statistiken für alle anderen Datenbanken werden aktualisiert. Um sicherzustellen, dass dieser Befehl ausgeführt wird, überprüfen Sie die PostgreSQL-Protokolle. VACUUM gibt Zeilen im folgenden Format aus: `INFO: vacuuming "public.nmsactivecontact"` und ANALYZE gibt Zeilen im folgenden Format aus: `INFO: analyzing "public.nmsactivecontact"`.

Wenn der Wert der Option 1 ist, wird die Statistikaktualisierung in keiner Datenbank ausgeführt. Die folgende Protokollzeile wird in den Workflow-Protokollen angezeigt: `Option 'XtkCleanup_NoStats' is set to '1'`.

Wenn der Wert der Option 2 ist, wird die Speicheranalyse im Verbose-Modus (ANALYZE VERBOSE) auf PostgreSQL ausgeführt und die Statistiken für alle anderen Datenbanken werden aktualisiert. Um sicherzustellen, dass dieser Befehl ausgeführt wird, überprüfen Sie die PostgreSQL-Protokolle. ANALYZE gibt Zeilen im folgenden Format aus: `INFO: analyzing "public.nmsactivecontact"`.

### Abonnement-Bereinigung (NMAC) {#subscription-cleanup--nmac-}

Diese Aufgabe löscht alle Abonnements, die sich auf gelöschte Services oder Mobile Apps beziehen.

Um die Liste der Broadlog-Schemata abzurufen, wird die folgende Abfrage verwendet:

```sql
SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
```

Die Aufgabe ruft dann die Namen der mit der Relation „appSubscription **verknüpften Tabellen ab** löscht diese Tabellen.

Dieser Bereinigungs-Workflow löscht auch alle Einträge, bei denen idisabled = 1 ist und die seit der in der Option **NmsCleanup_AppSubscriptionRcpPurgeDelay** festgelegten Zeit nicht aktualisiert wurden.

### Informationen zur Cleansing-Sitzung {#cleansing-session-information}

Diese Aufgabe bereinigt Informationen aus der **sessionInfo**-Tabelle. Die folgende Abfrage wird verwendet:

```sql
DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### Bereinigung abgelaufener Ereignisse {#cleansing-expired-events}

Diese Aufgabe bereinigt die in den Ausführungsinstanzen empfangenen und gespeicherten Ereignisse sowie die in einer Kontrollinstanz archivierten Ereignisse.

### Reinigungsreaktionen {#cleansing-reactions}

Diese Aufgabe bereinigt die Reaktionen (Tabelle **NmsRemaMatchRcp**), in denen die Hypothesen selbst gelöscht wurden.

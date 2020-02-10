---
title: Arbeitsablauf für die Datenbankbereinigung
seo-title: Arbeitsablauf für die Datenbankbereinigung
description: Arbeitsablauf für die Datenbankbereinigung
seo-description: null
page-status-flag: never-activated
uuid: a7478641-cdf6-4bd4-9dd7-0c84416c9de6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 6b188d78-abb4-4f03-80b9-051ce960f43c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d5813af76e3cad16d9094a19509dcb855e36c01f

---


# Database cleanup workflow{#database-cleanup-workflow}

## Einleitung {#introduction}

Der **[!UICONTROL Database cleanup]** Arbeitsablauf, auf den über die **[!UICONTROL Administration > Production > Technical workflows]** Node zugegriffen werden kann, ermöglicht das Löschen veralteter Daten, um ein exponentielles Wachstum der Datenbank zu vermeiden. Der Workflow wird automatisch ohne Benutzereingriff ausgelöst.

![](assets/ncs_cleanup_workflow.png)

## Konfiguration {#configuration}

Die Datenbankbereinigung wird auf zwei Ebenen konfiguriert: im Workflow Scheduler und im Bereitstellungsassistenten.

### Der Scheduler {#the-scheduler}

>[!NOTE]
>
>For more on the scheduler, refer to [this section](../../workflow/using/scheduler.md).

Standardmäßig ist der **[!UICONTROL Database cleanup]** Workflow so konfiguriert, dass er täglich um 4 Uhr beginnt. Mit dem Scheduler können Sie den Workflow ändern, der die Frequenz auslöst. Die folgenden Frequenzen stehen zur Verfügung:

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![](assets/ncs_cleanup_scheduler.png)

>[!CAUTION]
>
>Damit der **[!UICONTROL Database cleanup]** Workflow zu dem im Scheduler festgelegten Datum und zur festgelegten Uhrzeit beginnt, muss die Workflow-Engine (wfserver) gestartet werden. Ist dies nicht der Fall, erfolgt die Datenbankbereinigung erst nach dem nächsten Starten der Workflow-Engine.

### Bereitstellungsassistent {#deployment-wizard}

Mit der **[!UICONTROL Deployment wizard]** , auf die über das **[!UICONTROL Tools > Advanced]** Menü zugegriffen wird, können Sie konfigurieren, wie lange Daten gespeichert werden. Die Werte werden in Tagen angegeben. Wenn diese Werte nicht geändert werden, verwendet der Workflow die Standardwerte.

![](assets/ncs_cleanup_deployment-wizard.png)

Die Felder des **[!UICONTROL Purge of data]** Fensters entsprechen den folgenden Optionen. Diese werden von einigen der vom **[!UICONTROL Database cleanup]** Workflow ausgeführten Aufgaben verwendet:

* Konsolidierte Verfolgung: **NmsCleanup_TrackingStatPurgeDelay** (siehe [Bereinigen von Verfolgungsprotokollen](#cleanup-of-tracking-logs))
* Lieferprotokolle: **NmsCleanup_BroadLogPurgeDelay** (siehe [Bereinigen der Lieferprotokolle](#cleanup-of-delivery-logs))
* Verfolgungsprotokolle: **NmsCleanup_TrackingLogPurgeDelay** (siehe [Bereinigen von Verfolgungsprotokollen](#cleanup-of-tracking-logs))
* Gelöschte Lieferungen: **NmsCleanup_RecycledDeliveryPurgeDelay** (bezieht sich auf die [Bereinigung von zu löschenden oder zu recycelenden](#cleanup-of-deliveries-to-be-deleted-or-recycled)Lieferungen)
* Ablehnungen importieren: **NmsCleanup_RejectsPurgeDelay** (siehe [Bereinigung von durch Importe](#cleanup-of-rejects-generated-by-imports-)erzeugten Ablehnungen)
* Besucherprofile: **NmsCleanup_VisitorPurgeDelay** (siehe [Bereinigung der Besucher](#cleanup-of-visitors))
* Angebote: **NmsCleanup_PropositionPurgeDelay** (siehe [Bereinigen von Vorschlägen](#cleanup-of-propositions))

   >[!NOTE]
   >
   >Das **[!UICONTROL Offer propositions]** Feld ist nur verfügbar, wenn das **Interaktionsmodul** installiert ist.

* Ereignisse: **NmsCleanup_EventPurgeDelay** (siehe [Bereinigen abgelaufener Ereignisse](#cleansing-expired-events))
* Archivierte Ereignisse: **NmsCleanup_EventHistoPurgeDelay** (siehe [Bereinigen abgelaufener Ereignisse](#cleansing-expired-events))

   >[!NOTE]
   >
   >Die **[!UICONTROL Events]** Felder und **[!UICONTROL Archived events]** Felder sind nur verfügbar, wenn das Modul **Nachrichtencenter** installiert ist.

* Prüfpfad: **XtkCleanup_AuditTrailPurgeDelay** (siehe [Bereinigung des Audit-Protokolls](#cleanup-of-audit-trail))

Alle vom **[!UICONTROL Database cleanup]** Workflow ausgeführten Aufgaben werden im folgenden Abschnitt beschrieben.

## Aufgaben, die vom Arbeitsablauf für die Datenbankbereinigung ausgeführt werden {#tasks-carried-out-by-the-database-cleanup-workflow}

Zu dem im Workflow Scheduler definierten Datum und der im Workflow Scheduler definierten Zeit (siehe [Der Scheduler](#the-scheduler)) startet die Workflow-Engine den Datenbankbereinigungsprozess. Die Datenbankbereinigung stellt eine Verbindung zur Datenbank her und führt die Aufgaben in der unten gezeigten Reihenfolge aus.

>[!CAUTION]
>
>Wenn eine dieser Aufgaben fehlschlägt, werden die folgenden nicht ausgeführt.\
>SQL-Abfragen mit einem **LIMIT** -Attribut werden wiederholt ausgeführt, bis alle Informationen verarbeitet sind.

>[!NOTE]
>
>Die folgenden Abschnitte, die die Aufgaben des Arbeitsablaufs für die Datenbankbereinigung beschreiben, sind für Datenbankadministratoren oder Benutzer reserviert, die mit der SQL-Sprache vertraut sind.

### Listen zum Löschen der Bereinigung {#lists-to-delete-cleanup}

Die erste vom **[!UICONTROL Database cleanup]** Workflow ausgeführte Aufgabe löscht alle Gruppen mit dem **deleteStatus != 0** Attribut aus der **NmsGroup**. Die mit diesen Gruppen verknüpften und in anderen Tabellen vorhandenen Datensätze werden ebenfalls gelöscht.

1. Zu löschende Listen werden mithilfe der folgenden SQL-Abfrage wiederhergestellt:

   ```
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. Jede Liste enthält mehrere Links zu anderen Tabellen. Alle diese Links werden mit der folgenden Abfrage stapelweise gelöscht:

   ```
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   wobei **$(relatedTable)** eine Tabelle ist, die sich auf **NmsGroup** bezieht, und **$(l)** die Listenkennung.

1. Wenn es sich bei der Liste um eine Liste vom Typ &quot;Liste&quot;handelt, wird die zugehörige Tabelle mit der folgenden Abfrage gelöscht:

   ```
   DROP TABLE grp$(l)
   ```

1. Jede durch den Vorgang wiederhergestellte **Auswahl** -Typliste wird mithilfe der folgenden Abfrage gelöscht:

   ```
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   wobei **$(l)** die Listen-ID ist

### Beseitigung der zu löschenden oder zu recycelenden Lieferungen {#cleanup-of-deliveries-to-be-deleted-or-recycled}

Diese Aufgabe löscht alle zu löschenden oder wiederverwertenden Lieferungen.

1. Der **[!UICONTROL Database cleanup]** Arbeitsablauf wählt alle Lieferungen aus, für die das Feld &quot; **deleteStatus** &quot;den Wert **[!UICONTROL Yes]** oder **[!UICONTROL Recycled]** den Löschtermin vor dem im Feld **[!UICONTROL Deleted deliveries]** (**NmsCleanup_RecycledDeliveryPurgeDelay**) des Bereitstellungsassistenten definierten Zeitraum hat. For more on this, refer to [Deployment wizard](#deployment-wizard). Dieser Zeitraum wird im Verhältnis zum aktuellen Serverdatum berechnet.
1. Für jeden Server mit mittlerer Quelle wählt die Aufgabe die Liste der zu löschenden Auslieferungen aus.
1. Der **[!UICONTROL Database cleanup]** Workflow löscht Auslieferungsprotokolle, Anlagen, Spiegelseiteninformationen und alle anderen damit zusammenhängenden Daten.
1. Bevor die Bereitstellung endgültig gelöscht wird, werden die verknüpften Informationen aus den folgenden Tabellen entfernt:

   * In der Ausschlusstabelle (**NmsDlvExclusion**) wird die folgende Abfrage verwendet:

      ```
      DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
      ```

      wobei **$(l)** die Kennung der Lieferung ist.

   * In der Coupon-Tabelle (**NmsCouponValue**) wird die folgende Abfrage verwendet (mit Massenlöschungen):

      ```
      DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
      ```

      wobei **$(l)** die Kennung der Lieferung ist.

   * In den Lieferprotokolltabellen (**NmsBroadlogXxx**) werden Massenlöschungen in Stapeln von 10.000 Datensätzen ausgeführt.
   * In den Angebotstabellen (**NmsPropositionXxx**) werden Massenlöschungen in Stapeln von 10.000 Datensätzen ausgeführt.
   * In den Verfolgungsprotokolltabellen (**NmsTrackinglogXxx**) werden Massenlöschungen in Stapeln von 5.000 Datensätzen ausgeführt.
   * In der Fragment-Tabelle (**NmsDeliveryPart**) werden Massenlöschungen in Stapeln von 5.000 Datensätzen ausgeführt. Diese Tabelle enthält Personalisierungsinformationen zu den verbleibenden zu liefernden Nachrichten.
   * In der Tabelle mit dem Datenfragment für die Spiegelseite (**NmsMirrorPageInfo**) werden Massenlöschungen in Stapeln von 5.000 Datensätzen ausgeführt. Diese Tabelle enthält Personalisierungsinformationen zu allen Nachrichten, die zum Generieren von Spiegelseiten verwendet werden.
   * In der Suchtabelle der Spiegelseiten (**NmsMirrorPageSearch**) werden Massenlöschungen in Stapeln von 5.000 Datensätzen ausgeführt. Diese Tabelle ist ein Suchindex, der Zugriff auf Personalisierungsinformationen bietet, die in der Tabelle **NmsMirrorPageInfo** gespeichert sind.
   * In der Stapelverarbeitungsprotokolltabelle (**XtkJobLog**) werden Massenlöschungen in Stapeln von 5.000 Datensätzen ausgeführt. Diese Tabelle enthält das Protokoll der zu löschenden Lieferungen.
   * In der Verfolgungstabelle für die Liefer-URL (**NmsTrackingUrl**) wird die folgende Abfrage verwendet:

      ```
      DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
      ```

      wobei **$(l)** die Kennung der Lieferung ist.

      Diese Tabelle enthält die URLs, die in den zu löschenden Auslieferungen gefunden wurden, um deren Verfolgung zu ermöglichen.

1. Die Lieferung wird aus der Liefertabelle (**NmsDelivery**) gelöscht:

   ```
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   wobei **$(l)** die Kennung der Lieferung ist.

#### Lieferungen mit mittlerer Quelle {#deliveries-using-mid-sourcing}

Der **[!UICONTROL Database cleanup]** Workflow löscht auch Auslieferungen auf den/den mid-sourcing-Servern.

1. Dazu prüft der Workflow, ob jede Bereitstellung inaktiv ist (je nach Status). Wenn eine Bereitstellung aktiv ist, wird sie vor dem Löschen beendet. Die Prüfung wird durch Ausführung der folgenden Abfrage durchgeführt:

   ```
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   wobei **$(l)** die Kennung der Lieferung ist.

1. Wenn der Wert des Status **[!UICONTROL Start pending]** , **[!UICONTROL In progress]** , **[!UICONTROL Recovery pending]** , **[!UICONTROL Recovery in progress]** , **[!UICONTROL Pause requested]** , **[!UICONTROL Pause in progress]** oder **[!UICONTROL Paused]** (Werte 51, 55, 61, 62, 71, 72, 75) lautet, wird die Bereitstellung gestoppt und die Aufgabe löscht die verknüpften Informationen.

### Bereinigung abgelaufener Lieferungen {#cleanup-of-expired-deliveries}

Diese Aufgabe beendet Auslieferungen, deren Gültigkeitsdauer abgelaufen ist.

1. Der **[!UICONTROL Database cleanup]** Workflow erstellt die Liste der abgelaufenen Auslieferungen. Diese Liste enthält alle abgelaufenen Auslieferungen mit einem anderen Status als **[!UICONTROL Finished]** , sowie kürzlich abgeschlossene Auslieferungen mit über 10.000 nicht verarbeiteten Nachrichten. Die folgende Abfrage wird verwendet:

   ```
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   Wenn der **Bereitstellungsmodus 1** mit dem **[!UICONTROL Mass delivery]** -Modus übereinstimmt, stimmt **der Status 51** mit dem **[!UICONTROL Start pending]** Status überein, der **Status 85** stimmt mit dem **[!UICONTROL Stopped]** Status überein, und die höchste Anzahl an auf dem Lieferserver massenaktualisierten Lieferprotokollen entspricht 10.000.

1. Der Workflow enthält dann die Liste der kürzlich abgelaufenen Auslieferungen, die Mid-Sourcing verwenden. Lieferungen, für die noch keine Lieferprotokolle über den mid-sourcing-Server wiederhergestellt wurden, sind ausgeschlossen.

   Die folgende Abfrage wird verwendet:

   ```
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. Die folgende Abfrage wird verwendet, um festzustellen, ob das externe Konto noch aktiv ist oder nicht, um Auslieferungen nach Datum zu filtern:

   ```
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. In der Liste der abgelaufenen Auslieferungen wechseln die Lieferprotokolle mit dem Status **[!UICONTROL Pending]** , Umschalten zu **[!UICONTROL Delivery cancelled]** und alle Auslieferungen in dieser Liste zu **[!UICONTROL Finished]** .

   Die folgenden Abfragen werden verwendet:

   ```
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   Dabei ist **$(curdate)** das aktuelle Datum des Datenbankservers, **$(bl)** der Bezeichner der Meldung über die Lieferprotokolle, **$(dl)** der Lieferbezeichner, **Lieferstatus 6** stimmt mit **[!UICONTROL Pending]** Status und **** **[!UICONTROL Delivery cancelled]** Bereitstellungsstatus 7 mit dem Status der überein.

   ```
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   wobei der **Lieferstatus 95** mit dem **[!UICONTROL Finished]** Status übereinstimmt und **$(dl)** der Bezeichner der Lieferung ist.

1. Alle Fragmente (**Lieferteile**) veralteter Lieferungen werden gelöscht und alle veralteten Fragmente der in Bearbeitung befindlichen Zustellungen werden gelöscht. Massenlöschung wird für beide Aufgaben verwendet.

   Die folgenden Abfragen werden verwendet:

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   Wenn der **Bereitstellungsstatus 95** mit dem **[!UICONTROL Finished]** Status übereinstimmt, stimmt der **Bereitstellungsstatus 85** mit dem **[!UICONTROL Stopped]** Status überein und **$(curDate)** ist das aktuelle Serverdatum.

### Bereinigen von Spiegelseiten {#cleanup-of-mirror-pages}

Diese Aufgabe löscht die von Auslieferungen verwendeten Webressourcen (Spiegelseiten).

1. Zunächst wird die Liste der zu bereinigenden Lieferungen mithilfe der folgenden Abfrage wiederhergestellt:

   ```
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)"
   ```

   wobei **$(curDate)** das aktuelle Serverdatum ist.

1. Die Tabelle **NmsMirrorPageInfo** wird dann bereinigt, gegebenenfalls unter Verwendung der Kennung der zuvor wiederhergestellten Bereitstellung. Der Massenlöschvorgang wird verwendet, um die folgenden Abfragen zu generieren:

   ```
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   wobei **$(dl)** die Kennung der Lieferung ist.

1. Dem Lieferprotokoll wird dann ein Eintrag hinzugefügt.
1. Danach werden die entlegenen Lieferungen identifiziert, damit sie nicht später erneut verarbeitet werden müssen. Die folgende Abfrage wird ausgeführt:

   ```
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   Dabei ist **$(strIn)** die Liste der Lieferkennung.

### Aufräumen von Arbeitstischen {#cleanup-of-work-tables}

Diese Aufgabe löscht aus der Datenbank alle Arbeitstabellen, deren Status identisch ist **[!UICONTROL Being edited]** , **[!UICONTROL Stopped]** oder **[!UICONTROL Deleted]** .

1. Die Liste der Tabellen mit Namen, die mit **wkDlv_** beginnen, wird zuerst mit der folgenden Abfrage (postgresql) wiederhergestellt:

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. Die Tabellen, die von in Verarbeitung befindlichen Workflows verwendet werden, werden dann ausgeschlossen. Zu diesem Zweck wird die Liste der ausgeführten Lieferungen mithilfe der folgenden Abfrage wiederhergestellt:

   ```
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   wobei 0 der Wert ist, der dem **[!UICONTROL Being edited]** Lieferstatus entspricht, 85 mit dem **[!UICONTROL Stopped]** Status und 100 mit dem **[!UICONTROL Deleted]** Status übereinstimmt.

1. Nicht mehr verwendete Tabellen werden mit der folgenden Abfrage gelöscht:

   ```
   DROP TABLE wkDlv_15487_1;
   ```

### Aufräumung der durch Importe entstehenden Ablehnungen {#cleanup-of-rejects-generated-by-imports-}

Mit diesem Schritt können Sie Datensätze löschen, für die während des Imports nicht alle Daten verarbeitet wurden.

1. Massenlöschung wird mit der folgenden Abfrage an der **XtkReject** -Tabelle vorgenommen:

   ```
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l))
   ```

   wobei **$(curDate)** das aktuelle Serverdatum ist, ab dem der für die Option **NmsCleanup_RejectsPurgeDelay** definierte Zeitraum abgezogen wird (siehe [Bereitstellungsassistent](#deployment-wizard)), und **$(l)** die maximale Anzahl der zu löschenden Datensätze ist.

1. Alle verwaisten Ablehnungen werden dann mit der folgenden Abfrage gelöscht:

   ```
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### Bereinigen von Workflow-Instanzen {#cleanup-of-workflow-instances}

Diese Aufgabe löscht jede Workflow-Instanz mit ihrem Identifer (**lWorkflowId**) und dem Verlauf (**lHistory**). Dadurch werden inaktive Tabellen gelöscht, indem der Arbeitstischbereinigungsvorgang erneut ausgeführt wird.

>[!NOTE]
>
>Die Bereinigungshäufigkeit des Verlaufs wird für jeden Workflow im Feld **Verlauf in Tagen** angegeben (Standardwert 30 Tage). Dieses Feld finden Sie in den Workflow-Eigenschaften auf der Registerkarte &quot; **Ausführung** &quot;. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../workflow/using/workflow-properties.md#execution).

1. Zur Wiederherstellung der Liste der zu löschenden Workflows wird die folgende Abfrage verwendet:

   ```
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. Diese Abfrage generiert die Liste der Arbeitsabläufe, die zum Löschen aller verknüpften Protokolle, fertig gestellten Aufgaben und fertigen Ereignisse verwendet werden. Dabei werden folgende Abfragen verwendet:

   ```
   DELETE FROM XtkWorkflowLog WHERE iWorkflowId=$(lworkflow) AND tsLog < DateMinusDays($(lhistory))
   ```

   ```
   DELETE FROM XtkWorkflowTask WHERE iWorkflowId=$(lworkflow) AND iStatus<>0 AND tsCompletion < DateMinusDays($(lhistory)) 
   ```

   ```
   DELETE FROM XtkWorkflowEvent WHERE iWorkflowId=$(l) AND iStatus>2 AND tsProcessing < DateMinusDays($(lHistory))
   ```

   wobei **$(lworkflow)** die Kennung des Workflows und **$(history)** die Kennung des Verlaufs ist.

1. Alle nicht verwendeten Tabellen werden gelöscht. Zu diesem Zweck werden alle Tabellen mithilfe einer **Maske vom Typ &quot;wkf%** &quot;mithilfe der folgenden Abfrage (postgresql) erfasst:

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. Anschließend werden alle Tabellen, die von einer ausstehenden Workflow-Instanz verwendet werden, ausgeschlossen. Die Liste der aktiven Arbeitsabläufe wird mithilfe der folgenden Abfrage wiederhergestellt:

   ```
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. Jeder Workflow-Bezeichner wird anschließend wiederhergestellt, um den Namen der Tabellen zu finden, die von den in Verarbeitung befindlichen Workflows verwendet werden. Diese Namen werden aus der Liste der zuvor wiederhergestellten Tabellen ausgeschlossen.
1. Aktivitätstabellen des Typs &quot;inkrementelle Abfrage&quot;werden bei folgenden Abfragen ausgeschlossen:

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   wobei **$(strbedingung)** die Liste der Tabellen ist, die mit der **wkfhisto%** -Maske übereinstimmen.

1. Die verbleibenden Tabellen werden mithilfe der folgenden Abfrage gelöscht:

   ```
   DROP TABLE wkf15487_12;
   ```

### Bereinigen von Workflow-Anmeldungen {#cleanup-of-workflow-logins}

Diese Aufgabe löscht Workflow-Anmeldungen mit der folgenden Abfrage:

```
DELETE FROM XtkWorkflowLogin WHERE iWorkflowId NOT IN (SELECT iWorkflowId FROM XtkWorkflow)
```

### Aufräumen verwaister Arbeitstische {#cleanup-of-orphan-work-tables}

Diese Aufgabe löscht verwaiste Arbeitstabellen, die mit Gruppen verknüpft sind. Die Tabelle **NmsGroup** speichert die zu bereinigenden Gruppen (mit einem anderen Typ als 0). Das Präfix der Tabellennamen ist **grp**. Zur Identifizierung der zu bereinigenden Gruppen wird die folgende Abfrage verwendet:

```
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### Bereinigung der Besucher {#cleanup-of-visitors}

Diese Aufgabe löscht veraltete Datensätze aus der Besuchstabelle, indem sie Massenlöschung verwendet. Veraltete Datensätze sind solche, deren letzte Änderung vor dem im Bereitstellungsassistenten festgelegten Erhaltungszeitraum liegt (siehe [Bereitstellungsassistent](#deployment-wizard)). Die folgende Abfrage wird verwendet:

```
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < $(tsDate) LIMIT 5000)
```

wobei **$(tsDate)** das aktuelle Serverdatum ist, von dem der für die Option **NmsCleanup_VisitorPurgeDelay** definierte Zeitraum abgezogen wird.

### Säuberung von NPAI {#cleanup-of-npai}

Mit dieser Aufgabe können Sie Datensätze löschen, die gültigen Adressen entsprechen, aus der Tabelle **NmsAddress** . Die folgende Abfrage dient zum Durchführen eines Massenlöschens:

```
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

wobei **status 2** mit dem **[!UICONTROL Valid]** Status übereinstimmt, **$(tsDate1)** das aktuelle Serverdatum und **$(tsDate2)** mit der Option **NmsCleanup_LastCleanup** übereinstimmt.

### Bereinigung von Abonnements {#cleanup-of-subscriptions-}

Diese Aufgabe löscht alle Abonnements, die vom Benutzer aus der **NmsSubscription** -Tabelle gelöscht wurden, und zwar durch Massenlöschung. Die folgende Abfrage wird verwendet:

```
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### Bereinigen von Verfolgungsprotokollen {#cleanup-of-tracking-logs}

Diese Aufgabe löscht veraltete Datensätze aus den Protokolltabellen für Verfolgung und Webtracking. Veraltete Datensätze sind solche, die vor dem im Bereitstellungsassistenten festgelegten Erhaltungszeitraum liegen (siehe [Bereitstellungsassistent](#deployment-wizard)).

1. Zunächst wird die Liste der Verfolgungsprotokolltabellen mithilfe der folgenden Abfrage wiederhergestellt:

   ```
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. Der Massenlöschvorgang wird zum Löschen aller Tabellen in der Liste der zuvor wiederhergestellten Tabellen verwendet. Die folgende Abfrage wird verwendet:

   ```
   DELETE FROM XtkTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM XtkTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   wobei **$(tsDate)** das aktuelle Serverdatum ist, ab dem der für die Option **NmsCleanup_TrackingLogPurgeDelay** definierte Zeitraum abgezogen wird.

1. Die Tabelle der Verfolgungsstatistiken wird mithilfe des Massenlöschens bereinigt. Die folgende Abfrage wird verwendet:

   ```
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   wobei **$(tsDate)** das aktuelle Serverdatum ist, ab dem der für die Option **NmsCleanup_TrackingStatPurgeDelay** definierte Zeitraum abgezogen wird.

### Bereinigung der Lieferprotokolle {#cleanup-of-delivery-logs}

Mit dieser Aufgabe können Sie die in verschiedenen Tabellen gespeicherten Bereitstellungsprotokolle bereinigen.

1. Zu diesem Zweck wird die Liste der Bereitstellungsprotokollschemas mithilfe der folgenden Abfrage wiederhergestellt:

   ```
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. Bei Verwendung von Mid-Sourcing wird die **NmsBroadLogMid** -Tabelle bei Zuordnungen von Auslieferungen nicht referenziert. Das Schema **nms:wideLogMid** wird der Liste hinzugefügt, die durch die vorherige Abfrage wiederhergestellt wurde.
1. Der Arbeitsablauf für die **Datenbankbereinigung** bereinigt dann veraltete Daten aus zuvor wiederhergestellten Tabellen. Die folgende Abfrage wird verwendet:

   ```
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   wobei **$(tableName)** der Name jeder Tabelle in der Schemasliste und **$(option)** das für die Option **NmsCleanup_BroadLogPurgeDelay** definierte Datum ist (siehe [Bereitstellungsassistent](#deployment-wizard)).

1. Schließlich prüft der Workflow, ob die Tabelle **NmsProviderMsgId** vorhanden ist. Wenn ja, werden alle veralteten Daten mithilfe der folgenden Abfrage gelöscht:

   ```
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   wobei **$(Option)** mit dem für die Option **NmsCleanup_BroadLogPurgeDelay** definierten Datum übereinstimmt (siehe [Bereitstellungsassistent](#deployment-wizard)).

### Bereinigen der NmsEmailErrorStat-Tabelle {#cleanup-of-the-nmsemailerrorstat-table-}

Diese Aufgabe löscht die **Tabelle NmsEmailErrorStat** . Das Hauptprogramm (**coalesceErrors**) legt zwei Daten fest:

* **Startdatum**: Datum des nächsten Prozesses, der mit der Option **NmsLastErrorStatCoalesce** oder dem neuesten Datum in der Tabelle übereinstimmt.
* **Enddatum**: aktuelles Serverdatum.

Wenn das Startdatum größer oder gleich dem Enddatum ist, findet kein Prozess statt. In diesem Fall wird die **Meldung &quot;BildungUpToDate** &quot;angezeigt.

Wenn das Startdatum vor dem Enddatum liegt, wird die **Tabelle NmsEmailErrorStat** gelöscht.

Die Gesamtanzahl der Fehler in der **NmsEmailErrorStat** -Tabelle zwischen Start- und Enddatum wird mithilfe der folgenden Abfrage wiederhergestellt:

```
"SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)"
```

Dabei sind **$end** und **$start** die zuvor definierten Start- und Enddaten.

Wenn die Summe größer als 0 ist:

1. Die folgende Abfrage wird ausgeführt, um nur Fehler über einen bestimmten Schwellenwert (der 20 entspricht) hinaus zu halten:

   ```
   "SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20"
   ```

1. Die Meldung **coalescingErrors** wird angezeigt.
1. Es wird eine neue Verbindung erstellt, um alle Fehler zu löschen, die zwischen dem Start- und dem Enddatum aufgetreten sind. Die folgende Abfrage wird verwendet:

   ```
   "DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)"
   ```

1. Jeder Fehler wird mithilfe der folgenden Abfrage in der **Tabelle NmsEmailErrorStat** gespeichert:

   ```
   "INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))"
   ```

   wobei jede Variable mit einem Wert übereinstimmt, der durch die vorherige Abfrage wiederhergestellt wurde.

1. Die **Variable start** wird mit den Werten des vorherigen Prozesses aktualisiert, um die Schleife zu beenden.

Die Schleife und der Task-Stopp.

Bereinigungen werden auf den Tabellen **NmsEmailError** und **cleanupNmsMxDomain** ausgeführt.

### Bereinigen der NmsEmailError-Tabelle {#cleanup-of-the-nmsemailerror-table-}

Die folgende Abfrage wird verwendet:

```
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Diese Abfrage löscht alle Zeilen ohne verknüpfte Datensätze in der **NmsEmailErrorStat** -Tabelle **NmsEmailError** .

### Bereinigen der NmsMxDomain-Tabelle {#cleanup-of-the-nmsmxdomain-table-}

Die folgende Abfrage wird verwendet:

```
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Diese Abfrage löscht alle Zeilen ohne verknüpften Datensatz in der Tabelle **NmsEmailErrorStat** aus der Tabelle **NmsMxDomain** .

### Bereinigung der Vorschläge {#cleanup-of-propositions}

Wenn das **Interaktionsmodul** installiert ist, wird diese Aufgabe ausgeführt, um die **NmsPropositionXxx** -Tabellen zu bereinigen.

Die Liste der Tabelle &quot;Vorschläge&quot;wird wiederhergestellt und für jede der Tabellen eine Massenlöschung durchgeführt, wobei folgende Abfrage verwendet wird:

```
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

wobei **$(Option)** das für die Option **NmsCleanup_PropositionPurgeDelay** definierte Datum ist (siehe [Bereitstellungsassistent](#deployment-wizard)).

### Bereinigen von Simulationstabellen {#cleanup-of-simulation-tables}

Diese Aufgabe bereinigt verwaiste Simulationstabellen (die nicht mehr mit einer Angebotssimulation oder einer Bereitstellungssimulation verknüpft sind).

1. Zur Wiederherstellung der Liste der Simulationen, die bereinigt werden müssen, wird die folgende Abfrage verwendet:

   ```
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. Der Name der zu löschenden Tabellen besteht aus dem **wkSimu_** -Präfix, gefolgt vom Bezeichner der Simulation (z. B.: **wkSimu_456831_aggr**):

   ```
   DROP TABLE wkSimu_456831_aggr
   ```

### Optimierung der Statistikaktualisierung und -speicherung {#statistics-update}

Mit der Option **XtkCleanup_NoStats** können Sie das Verhalten des Speicheroptimierungsschritts des Bereinigungs-Workflows steuern.

Wenn die Option **XtkCleanup_NoStats** nicht vorhanden ist oder der Wert 0 ist, wird die Speicheroptimierung im ausführlichen Modus (VACUUM VERBOSE ANALYZE) auf PostgreSQL ausgeführt und Statistiken für alle anderen Datenbanken aktualisiert. Um sicherzustellen, dass dieser Befehl ausgeführt wird, überprüfen Sie die PostgreSQL-Protokolle. VACUUM gibt Zeilen im Format aus: `INFO: vacuuming "public.nmsactivecontact"` und ANALYZE geben Zeilen im Format aus: `INFO: analyzing "public.nmsactivecontact"`.

Wenn der Wert der Option 1 ist, werden keine statistischen Aktualisierungen in einer Datenbank durchgeführt. Die folgende Protokollzeile wird in den Workflow-Protokollen angezeigt: `Option 'XtkCleanup_NoStats' is set to '1'`.

Wenn der Wert der Option 2 ist, wird die Speicheranalyse im ausführlichen Modus (ANALYZE VERBOSE) auf PostgreSQL ausgeführt und die Statistik für alle anderen Datenbanken aktualisiert. Um sicherzustellen, dass dieser Befehl ausgeführt wird, überprüfen Sie die PostgreSQL-Protokolle. ANALYZE gibt Zeilen im Format aus: `INFO: analyzing "public.nmsactivecontact"`.

### Abonnementbereinigung (NMAC) {#subscription-cleanup--nmac-}

Diese Aufgabe löscht alle Abonnements im Zusammenhang mit gelöschten Diensten oder mobilen Anwendungen.

1. Um die Liste der Breitbandschemata wiederherzustellen, wird die folgende Abfrage verwendet:

   ```
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
   ```

1. Die Aufgabe stellt dann die Namen der Tabellen wieder her, die mit dem Link &quot; **appSubscription** &quot;verknüpft sind, und löscht diese Tabellen.

### Sitzungsinformationen löschen {#cleansing-session-information}

Diese Aufgabe löscht Informationen aus der **Tabelle sessionInfo** . Es wird folgende Abfrage verwendet:

```
 DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### Löschen abgelaufener Ereignisse {#cleansing-expired-events}

Diese Aufgabe löscht die Ereignisse, die in den Ausführungsinstanzen empfangen und gespeichert wurden, sowie die in einer Steuerelementinstanz archivierten Ereignisse.

### Reinigungsreaktionen {#cleansing-reactions}

Diese Aufgabe bereinigt die Reaktionen (Tabelle **NmsRemaMatchRcp**), in denen die Hypothesen selbst gelöscht wurden.

### Bereinigung des Prüfpfads {#cleanup-of-audit-trail}

Die folgende Abfrage wird verwendet:

```
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

wobei **$(tsDate)** das aktuelle Serverdatum ist, ab dem der für die Option **XtkCleanup_AuditTrailPurgeDelay** definierte Zeitraum ersetzt wird.

---
product: campaign
title: Datenbankbereinigungs-Workflow
description: Erfahren Sie, wie veraltete Daten automatisch bereinigt werden.
feature: Monitoring, Workflows
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 75d3a0af-9a14-4083-b1da-2c1b22f57cbe
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '2914'
ht-degree: 1%

---

# Datenbankbereinigungs-Workflow{#database-cleanup-workflow}



## Einleitung {#introduction}

Der Workflow **[!UICONTROL Datenbankbereinigung]**, auf den Sie über den Knoten **[!UICONTROL Administration > Produktion > Technische Workflows]** zugreifen können, ermöglicht das Löschen veralteter Daten, um das exponentielle Anwachsen der Datenbank zu verhindern. Der Workflow wird automatisch ohne das Eingreifen der benutzenden Person ausgelöst.

![cleanup](assets/ncs_cleanup_workflow.png)

## Konfiguration {#configuration}

Die Datenbankbereinigung wird auf zwei Ebenen konfiguriert: im Workflow-Planer und im Softwareverteilungs-Assistenten.

### Workflow-Planung {#the-scheduler}

>[!NOTE]
>
>Weiterführende Informationen zur Planung finden Sie in [diesem Abschnitt](../../workflow/using/scheduler.md).

Standardmäßig ist der Workflow **[!UICONTROL Datenbankbereinigung]** so konfiguriert, dass er täglich um 4 Uhr gestartet wird. Die Planung ermöglicht es, die Häufigkeit der Auslösung des Workflows zu ändern. Die folgenden Häufigkeiten sind verfügbar:

* **[!UICONTROL Mehrmals pro Tag]**
* **[!UICONTROL Täglich]**
* **[!UICONTROL Wöchentlich]**
* **[!UICONTROL Once]**

![scheduler](assets/ncs_cleanup_scheduler.png)

>[!IMPORTANT]
>
>Damit der Workflow **[!UICONTROL Datenbankbereinigung]** an dem in der Planung definierten Datum und zu der dort definierten Uhrzeit gestartet werden kann, muss die Workflow-Engine (wfserver) gestartet werden.

### Implementierungsassistent {#deployment-wizard}

Mit dem über das Menü **[!UICONTROL Tools > Erweitert]** verfügbaren **[!UICONTROL Softwareverteilungs-Assistenten]** können Sie konfigurieren, wie lange Daten gespeichert werden sollen. Die Werte werden in Tagen ausgedrückt. Wenn diese Werte nicht geändert werden, verwendet der Workflow die Standardwerte.

![](assets/ncs_cleanup_deployment-wizard.png)

Die Felder des Fensters **[!UICONTROL Datenbereinigung]** entsprechen den folgenden Optionen. Diese werden von einigen der Aufgaben verwendet, die vom Workflow **[!UICONTROL Datenbankbereinigung]** ausgeführt werden:

* Konsolidiertes Tracking: **NmsCleanup_TrackingStatPurgeDelay** (siehe [Bereinigung der Trackinglogs](#cleanup-of-tracking-logs))
* Versandlogs: **NmsCleanup_BroadLogPurgeDelay** (siehe [Bereinigung der Versandlogs](#cleanup-of-delivery-logs))
* Trackinglogs: **NmsCleanup_TrackingLogPurgeDelay** (siehe [Bereinigung der Trackinglogs](#cleanup-of-tracking-logs))
* Gelöschte Sendungen: **NmsCleanup_RecycledDeliveryPurgeDelay** (siehe [Bereinigung der zu löschenden oder zu recycelenden Sendungen](#cleanup-of-deliveries-to-be-deleted-or-recycled))
* Importabweisungen: **NmsCleanup_RejectsPurgeDelay** (siehe [Bereinigung der durch Importe generierten Zurückweisungen](#cleanup-of-rejects-generated-by-imports-))
* Besucherprofile: **NmsCleanup_VisitorPurgeDelay** (siehe [Bereinigung der Besucher](#cleanup-of-visitors))
* Angebotsvorschläge: **NmsCleanup_PropositionPurgeDelay** (siehe [Bereinigung der Vorschläge](#cleanup-of-propositions))

  >[!NOTE]
  >
  >Das Feld **[!UICONTROL Angebotsvorschläge]** ist nur verfügbar, wenn das Modul **Interaction** installiert ist.

* Ereignisse: **NmsCleanup_EventPurgeDelay** (siehe [Bereinigen abgelaufener Ereignisse](#cleansing-expired-events))
* Archivierte Ereignisse: **NmsCleanup_EventHistoPurgeDelay** (siehe [Bereinigen abgelaufener Ereignisse](#cleansing-expired-events))

  >[!NOTE]
  >
  >Die Felder **[!UICONTROL Ereignisse]** und **[!UICONTROL Ereignisse mit Verlauf]** sind nur verfügbar, wenn das Modul **Message Center** installiert ist.

* Audit-Protokoll: **XtkCleanup_AuditTrailPurgeDelay** (siehe [Bereinigen des Audit-Protokolls](#cleanup-of-audit-trail))

Alle vom Workflow **[!UICONTROL Datenbankbereinigung]** ausgeführten Aufgaben werden im folgenden Abschnitt beschrieben.

## Vom Datenbankbereinigungs-Workflow durchgeführte Aufgaben {#tasks-carried-out-by-the-database-cleanup-workflow}

Zu dem in der Workflow-Planung definierten Zeitpunkt (siehe [Planer](#the-scheduler)) startet die Workflow-Engine den Datenbankbereinigungsprozess. Die Datenbankbereinigung stellt eine Verbindung zur Datenbank her und führt die Aufgaben in der unten gezeigten Reihenfolge aus.

>[!IMPORTANT]
>
>Wenn eine dieser Aufgaben fehlschlägt, werden die nächsten nicht ausgeführt.
>
>SQL-Abfragen mit dem Attribut **LIMIT** werden wiederholt ausgeführt, bis alle Informationen verarbeitet werden.


### Listen zum Löschen der Bereinigung {#lists-to-delete-cleanup}

Die erste Aufgabe, die vom Workflow **[!UICONTROL Datenbankbereinigung]** ausgeführt wird, löscht alle Gruppen mit dem Wert **deleteStatus != 0** Attribut aus der **NmsGroup**. Die mit diesen Gruppen verknüpften und in anderen Tabellen vorhandenen Datensätze werden ebenfalls gelöscht.

1. Zu löschende Listen werden mithilfe der folgenden SQL-Abfrage abgerufen:

   ```sql
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. Jede Liste enthält mehrere Links zu anderen Tabellen. Alle diese Links werden mithilfe der folgenden Abfrage stapelweise gelöscht:

   ```sql
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   wobei `$(relatedTable)` eine Tabelle ist, die sich auf **NmsGroup** und `$(l)` auf die Listenkennung bezieht.

1. Wenn es sich bei der Liste um eine Liste vom Typ &quot;Liste&quot; handelt, wird die zugeordnete Tabelle mithilfe der folgenden Abfrage gelöscht:

   ```sql
   DROP TABLE grp$(l)
   ```

1. Jede vom Vorgang abgerufene Liste vom Typ **Select** wird mithilfe der folgenden Abfrage gelöscht:

   ```sql
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   wobei `$(l)` die Listenkennung ist

### Bereinigung der zu löschenden oder zu recycelenden Sendungen {#cleanup-of-deliveries-to-be-deleted-or-recycled}

Diese Aufgabe löscht alle zu löschenden oder recycelten Sendungen.

1. Der Workflow **[!UICONTROL Datenbankbereinigung]** wählt alle Sendungen aus, für die das Feld **deleteStatus** den Wert **[!UICONTROL Ja]** oder **[!UICONTROL Recycled]** aufweist und deren Löschdatum vor dem in den **[!UICONTROL gelöschten Sendungen]** definierten Zeitraum liegt (**NmsCleanup_RecycledDeliveryDelay**) im Softwareverteilungs-Assistenten. Weitere Informationen hierzu finden Sie unter [Implementierungsassistent](#deployment-wizard). Dieser Zeitraum wird in Bezug auf das aktuelle Server-Datum berechnet.
1. Für jeden Mid-Sourcing-Server wählt die Aufgabe die Liste der zu löschenden Sendungen aus.
1. Der Workflow **[!UICONTROL Datenbankbereinigung]** löscht Versandlogs, Anhänge, Informationen zur Mirrorseite und alle anderen damit verbundenen Daten.
1. Vor dem endgültigen Löschen des Versands löscht der Workflow verknüpfte Informationen aus den folgenden Tabellen:

   * In der Ausschlusstabelle des Versands (**NmsDlvExclusion**) wird die folgende Abfrage verwendet:

     ```sql
     DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
     ```

     wobei **$(l)** die Kennung des Versands ist.

   * In der Coupontabelle (**NmsCouponValue**) wird die folgende Abfrage verwendet (mit Massenlöschungen):

     ```sql
     DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
     ```

     wobei `$(l)` die Kennung des Versands ist.

   * In den Versandlog-Tabellen (**NmsBroadlogXxx**) werden Massenlöschungen in Stapeln von 20.000 Datensätzen ausgeführt.
   * In den Vorschlagstabellen (**NmsPropositionXxx**) werden Massenlöschungen in Stapeln von 20.000 Datensätzen ausgeführt.
   * In den Trackinglog-Tabellen (**NmsTrackingLogXxx**) werden Massenlöschungen in Stapeln von 20.000 Datensätzen ausgeführt.
   * In der Versandfragmenttabelle (**NmsDeliveryPart**) werden Massenlöschungen in Stapeln von 500.000 Datensätzen ausgeführt. Diese Tabelle enthält Personalisierungsinformationen zu den restlichen zu versendenden Nachrichten.
   * In der Tabelle der Mirrorseiten-Datenfragmente (**NmsMirrorPageInfo**) werden Massenlöschungen in Stapeln von 20.000 Datensätzen für abgelaufene Versandteile und für fertige oder abgebrochene Teile ausgeführt. Diese Tabelle enthält Personalisierungsinformationen zu allen Nachrichten, die zum Generieren von Mirrorseiten verwendet werden.
   * In der Suchtabelle für die Mirrorseite (**NmsMirrorPageSearch**) werden Massenlöschungen in Stapeln von 20.000 Datensätzen ausgeführt. Diese Tabelle ist ein Suchindex, der Zugriff auf Personalisierungsinformationen bietet, die in der Tabelle **NmsMirrorPageInfo** gespeichert sind.
   * In der Stapelverarbeitungsprotokolltabelle (**XtkJobLog**) werden Massenlöschungen in Stapeln von 20.000 Datensätzen ausgeführt. Diese Tabelle enthält das Protokoll der zu löschenden Sendungen.
   * In der Versand-URL-Tracking-Tabelle (**NmsTrackingUrl**) wird die folgende Abfrage verwendet:

     ```sql
     DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
     ```

     wobei `$(l)` die Kennung des Versands ist.

     Diese Tabelle enthält die URLs in den zu löschenden Sendungen, um deren Tracking zu ermöglichen.

1. Der Versand wird aus der Versandtabelle (**NmsDelivery**) gelöscht:

   ```sql
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   wobei `$(l)` die Kennung des Versands ist.

#### Sendungen mit Mid-Sourcing {#deliveries-using-mid-sourcing}

Der Workflow **[!UICONTROL Datenbankbereinigung]** löscht auch Sendungen auf Mid-Sourcing-Servern.

1. Dazu prüft der Workflow, ob jeder Versand inaktiv ist (je nach Status). Wenn ein Versand aktiv ist, wird er vor dem Löschen angehalten. Die Überprüfung wird durch Ausführung der folgenden Abfrage durchgeführt:

   ```sql
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   wobei **$(l)** die Kennung des Versands ist.

1. Wenn der Wert des Status &quot;**[!UICONTROL Start ausstehend]** &quot;, &quot;**[!UICONTROL Gestartet]** &quot;, &quot;**[!UICONTROL Wiederherstellung ausstehend]**&quot;, &quot;**[!UICONTROL Wiederherstellung in Gang&quot;]** , &quot;**[!UICONTROL Pause angefordert]**&quot;, &quot;**[!UICONTROL In Bearbeitung anhalten&quot;]** oder &quot;**[!UICONTROL Ausgesetzt]**&quot; lautet (Werte 51, 5, 6, 71, 72, 75), wird der Versand angehalten und die Aufgabe löscht die verknüpften Informationen.

### Bereinigung abgelaufener Sendungen {#cleanup-of-expired-deliveries}

Diese Aufgabe beendet Sendungen, deren Gültigkeitszeitraum abgelaufen ist.

1. Der Workflow **[!UICONTROL Datenbankbereinigung]** erstellt die Liste der abgelaufenen Sendungen. Diese Liste enthält alle abgelaufenen Sendungen mit einem anderen Status als **[!UICONTROL Abgeschlossen]** sowie kürzlich angehaltene Sendungen mit über 10.000 nicht verarbeiteten Nachrichten. Die folgende Abfrage wird verwendet:

   ```sql
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   wobei `delivery mode 1` mit dem Modus **[!UICONTROL Massenversand]** übereinstimmt, `state 51` mit dem Status **[!UICONTROL Start ausstehend]** übereinstimmt, `state 85` mit dem Status **[!UICONTROL Angehalten]** und die höchste Anzahl an Versandlogs, die auf dem Versandserver gebündelt aktualisiert werden, 10.000 entspricht.

1. Der Workflow enthält dann die Liste der kürzlich abgelaufenen Sendungen, die Mid-Sourcing verwenden. Sendungen, für die noch keine Versandlogs über den Mid-Sourcing-Server abgerufen wurden, sind ausgeschlossen.

   Die folgende Abfrage wird verwendet:

   ```sql
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. Mithilfe der folgenden Abfrage wird ermittelt, ob das externe Konto noch aktiv ist, um Sendungen nach Datum zu filtern:

   ```sql
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. In der Liste der abgelaufenen Sendungen wechseln die Versandlogs mit dem Status **[!UICONTROL Ausstehend]** zu **[!UICONTROL Versand abgebrochen]** und alle in dieser Liste enthaltenen Sendungen zu **[!UICONTROL Abgeschlossen]** .

   Die folgenden Abfragen werden verwendet:

   ```sql
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   wobei `$(curdate)`das aktuelle Datum des Datenbankservers ist, `$(bl)` die Kennung der Versandlogs-Nachricht ist, `$(dl)` die Versandkennung, `delivery status 6` den Status **[!UICONTROL Ausstehend]** und `delivery status 7` den Status **[!UICONTROL Versand abgebrochen]** aufweist.

   ```sql
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   wobei `delivery state 95` dem Status **[!UICONTROL Abgeschlossen]** und `$(dl)` der Kennung des Versands entspricht.

1. Alle Fragmente (**deliveryparts**) veralteter Sendungen werden gelöscht und alle veralteten Fragmente der laufenden Benachrichtigungsversand-Vorgänge werden gelöscht. Für beide Aufgaben wird Massenlöschung verwendet.

   Die folgenden Abfragen werden verwendet:

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   wobei `delivery state 95` mit dem Status **[!UICONTROL Abgeschlossen]** übereinstimmt, `delivery state 85` mit dem Status **[!UICONTROL Angehalten]** und `$(curDate)` mit dem aktuellen Server-Datum übereinstimmt.

### Bereinigung der Mirrorseiten {#cleanup-of-mirror-pages}

Bei dieser Aufgabe werden die von Sendungen verwendeten Web-Ressourcen (Mirrorseiten) gelöscht.

1. Zunächst wird die Liste der zu löschenden Sendungen mithilfe der folgenden Abfrage abgerufen:

   ```sql
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)
   ```

   wobei `$(curDate)` das aktuelle Server-Datum ist.

1. Die Tabelle **NmsMirrorPageInfo** wird dann bereinigt, gegebenenfalls unter Verwendung der Kennung des zuvor wiederhergestellten Versands. Das gebündelte Löschen wird verwendet, um die folgenden Abfragen zu generieren:

   ```sql
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000
   ```

   ```sql
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000
   ```

   wobei `$(dl)` die Kennung des Versands ist.

1. Im Versandlog wird dann ein Eintrag hinzugefügt.
1. Die bereinigten Sendungen werden dann identifiziert, um zu vermeiden, dass sie später erneut verarbeitet werden. Die folgende Abfrage wird ausgeführt:

   ```sql
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   wobei `$(strIn)` die Liste der Versandkennungen ist.

### Bereinigen von Arbeitstabellen {#cleanup-of-work-tables}

Diese Aufgabe löscht aus der Datenbank alle Arbeitstabellen, die Sendungen entsprechen, deren Status **[!UICONTROL In Bearbeitung ist]** , **[!UICONTROL Angehalten]** oder **[!UICONTROL Gelöscht]** lautet.

1. Die Liste der Tabellen mit Namen, die mit **wkDlv_** beginnen, wird zuerst mit der folgenden Abfrage abgerufen (postgresql):

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. Die von laufenden Workflows verwendeten Tabellen werden dann ausgeschlossen. Die Liste der ausgeführten Sendungen wird mithilfe der folgenden Abfrage abgerufen:

   ```sql
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   wobei `0` der Wert ist, der dem Versandstatus **[!UICONTROL In Bearbeitung]** entspricht, entspricht `85` dem Status **[!UICONTROL Angehalten]** und `100` dem Status **[!UICONTROL Gelöscht]** .

1. Nicht mehr verwendete Tabellen werden mithilfe der folgenden Abfrage gelöscht:

   ```sql
   DROP TABLE wkDlv_15487_1;
   ```

### Bereinigung der durch Importe erzeugten Zurückweisungen {#cleanup-of-rejects-generated-by-imports-}

In diesem Schritt können Sie Datensätze löschen, für die während des Imports nicht alle Daten verarbeitet wurden.

1. Die Massenlöschung erfolgt für die Tabelle **XtkReject** mit der folgenden Abfrage:

   ```sql
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l)
   ```

   wobei `$(curDate)` das aktuelle Server-Datum ist, von dem aus der für die Option **NmsCleanup_RejectsPurgeDelay** definierte Zeitraum abgezogen wird (siehe [Softwareverteilungs-Assistent](#deployment-wizard)), und `$(l)` die maximale Anzahl der zu löschenden Datensätze für die Masse ist.

1. Alle verwaisten Zurückweisungen werden dann mithilfe der folgenden Abfrage gelöscht:

   ```sql
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### Bereinigen von Workflow-Instanzen {#cleanup-of-workflow-instances}

Diese Aufgabe löscht jede Workflow-Instanz mit ihrem Identifer (**lWorkflowId**) und dem Verlauf (**lHistory**). Löscht inaktive Tabellen, indem die Aufgabe zur Bereinigung der Arbeitstabelle erneut ausgeführt wird. Die Bereinigung löscht auch alle verwaisten Arbeitstabellen (wkf% und wkfhisto%) der gelöschten Workflows.

>[!NOTE]
>
>Die Bereinigungshäufigkeit des Verlaufs wird für jeden Workflow im Feld **Verlauf in Tagen** angegeben (Standardwert: 30 Tage). Dieses Feld finden Sie in den Workflow-Eigenschaften auf der Registerkarte **Ausführung** . Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../workflow/using/workflow-properties.md#execution).

1. Um die Liste der zu löschenden Workflows abzurufen, wird die folgende Abfrage verwendet:

   ```sql
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. Diese Abfrage erzeugt mithilfe der folgenden Abfragen die Liste der Workflows, die zum Löschen aller verknüpften Logs, abgeschlossenen Aufgaben und abgeschlossenen Ereignisse verwendet werden:

   ```sql
   DELETE FROM XtkWorkflowLog WHERE iWorkflowId=$(lworkflow) AND tsLog < DateMinusDays($(lhistory))
   ```

   ```sql
   DELETE FROM XtkWorkflowTask WHERE iWorkflowId=$(lworkflow) AND iStatus<>0 AND tsCompletion < DateMinusDays($(lhistory)) 
   ```

   ```sql
   DELETE FROM XtkWorkflowEvent WHERE iWorkflowId=$(l) AND iStatus>2 AND tsProcessing < DateMinusDays($(lHistory))
   ```

   wobei `$(lworkflow)` die Kennung des Workflows und `$(lhistory)` die Kennung des Verlaufs ist.

1. Alle nicht verwendeten Tabellen werden gelöscht. Zu diesem Zweck werden alle Tabellen mithilfe einer Maske vom Typ **wkf%** mit der folgenden Abfrage (postgresql) erfasst:

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. Dann werden alle Tabellen ausgeschlossen, die von einer ausstehenden Workflow-Instanz verwendet werden. Die Liste der aktiven Workflows wird mithilfe der folgenden Abfrage abgerufen:

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. Jede Workflow-Kennung wird dann abgerufen, um den Namen der Tabellen zu ermitteln, die von laufenden Workflows verwendet werden. Diese Namen werden aus der Liste der zuvor wiederhergestellten Tabellen ausgeschlossen.
1. Verlaufstabellen vom Typ &quot;inkrementelle Abfrage&quot; werden mithilfe der folgenden Abfragen ausgeschlossen:

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   wobei `$(strcondition)` die Liste der Tabellen ist, die mit der Maske **wkfhisto%** übereinstimmen.

1. Die verbleibenden Tabellen werden mithilfe der folgenden Abfrage gelöscht:

   ```sql
   DROP TABLE wkf15487_12;
   ```

### Bereinigung der Workflow-Anmeldungen {#cleanup-of-workflow-logins}

Diese Aufgabe löscht Workflow-Anmeldungen mit der folgenden Abfrage:

```sql
DELETE FROM XtkWorkflowLogin WHERE iWorkflowId NOT IN (SELECT iWorkflowId FROM XtkWorkflow)
```

### Bereinigung verwaister Arbeitstabellen {#cleanup-of-orphan-work-tables}

Diese Aufgabe löscht verwaiste Arbeitstabellen, die mit Gruppen verknüpft sind. Die Tabelle **NmsGroup** speichert die zu bereinigenden Gruppen (mit einem anderen Typ als 0). Das Präfix der Tabellennamen ist **grp**. Um die zu bereinigenden Gruppen zu identifizieren, wird die folgende Abfrage verwendet:

```sql
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### Besucherbereinigung {#cleanup-of-visitors}

Durch Massenlöschung werden veraltete Datensätze aus der Besuchertabelle gelöscht. Veraltete Datensätze sind jene, deren letzte Änderung vor dem im Softwareverteilungs-Assistenten festgelegten Erhaltungszeitraum liegt (siehe [Softwareverteilungs-Assistent](#deployment-wizard)). Die folgende Abfrage wird verwendet:

```sql
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < AddDays(GetDate(), -30) AND iOrigin = 0 LIMIT 20000)
```

wobei `$(tsDate)` das aktuelle Server-Datum ist, von dem aus der für die Option **NmsCleanup_VisitorPurgeDelay** definierte Zeitraum abgezogen wird.

### Bereinigung der NPAI {#cleanup-of-npai}

Mithilfe dieser Aufgabe können Sie Datensätze, die gültigen Adressen entsprechen, aus der Tabelle **NmsAddress** löschen. Die folgende Abfrage wird verwendet, um eine Massenlöschung durchzuführen:

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

wobei `status 2` mit dem Status **[!UICONTROL Gültig]** übereinstimmt, `$(tsDate1)` das aktuelle Serverdatum und `$(tsDate2)` mit der Option **NmsCleanup_LastCleanup** übereinstimmt.

### Bereinigung der Abonnements {#cleanup-of-subscriptions-}

Diese Aufgabe löscht alle vom Benutzer aus der Tabelle **NmsSubscription** gelöschten Abonnements mithilfe einer Massenlöschung. Die folgende Abfrage wird verwendet:

```sql
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### Bereinigung der Trackinglogs {#cleanup-of-tracking-logs}

Diese Aufgabe löscht veraltete Datensätze aus den Tracking- und Webtracking-Log-Tabellen. Veraltete Datensätze sind jene, die vor dem im Softwareverteilungs-Assistenten festgelegten Erhaltungszeitraum liegen (siehe [Softwareverteilungs-Assistent](#deployment-wizard)).

1. Zunächst wird die Liste der Trackinglog-Tabellen mithilfe der folgenden Abfrage abgerufen:

   ```sql
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. Die Massenlöschung dient der Bereinigung aller Tabellen in der Liste der zuvor wiederhergestellten Tabellen. Die folgende Abfrage wird verwendet:

   ```sql
   DELETE FROM NmsTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM NmsTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   wobei `$(tsDate)` das aktuelle Server-Datum ist, von dem aus der für die Option **NmsCleanup_TrackingLogPurgeDelay** definierte Zeitraum abgezogen wird.

1. Die Trackingstatistiken werden mithilfe einer Massenlöschung bereinigt. Die folgende Abfrage wird verwendet:

   ```sql
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   wobei `$(tsDate)` das aktuelle Server-Datum ist, von dem wir den für die Option **NmsCleanup_TrackingStatPurgeDelay** definierten Zeitraum subtrahieren.

### Bereinigung der Versandlogs {#cleanup-of-delivery-logs}

Auf diese Weise können die in verschiedenen Tabellen gespeicherten Versandlogs bereinigt werden.

1. Zu diesem Zweck wird die Liste der Versandlog-Schemata mithilfe der folgenden Abfrage abgerufen:

   ```sql
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. Bei Verwendung der Mid-Sourcing-Methode wird die Tabelle **NmsBroadLogMid** nicht in Versandzuordnungen referenziert. Das Schema **nms:broadLogMid** wird der Liste hinzugefügt, die von der vorherigen Abfrage abgerufen wurde.
1. Der Workflow **Datenbankbereinigung** löscht dann veraltete Daten aus zuvor wiederhergestellten Tabellen. Die folgende Abfrage wird verwendet:

   ```sql
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   wobei `$(tableName)` der Name jeder Tabelle in der Schemakarte und `$(option)` das für die Option **NmsCleanup_BroadLogPurgeDelay** definierte Datum ist (siehe [Softwareverteilungs-Assistent](#deployment-wizard)).

1. Schließlich prüft der Workflow, ob die Tabelle **NmsProviderMsgId** vorhanden ist. Wenn ja, werden alle veralteten Daten mithilfe der folgenden Abfrage gelöscht:

   ```sql
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   wobei `$(option)` dem für die Option **NmsCleanup_BroadLogPurgeDelay** definierten Datum entspricht (siehe [Implementierungsassistent](#deployment-wizard)).

### Bereinigung der Tabelle &quot;NmsEmailErrorStat&quot; {#cleanup-of-the-nmsemailerrorstat-table-}

Diese Aufgabe bereinigt die Tabelle **NmsEmailErrorStat**. Das Hauptprogramm (**coalesceErrors**) definiert zwei Daten:

* **Startdatum**: Datum des nächsten Prozesses, der mit der Option **NmsLastErrorStatCoalesce** oder dem neuesten Datum in der Tabelle übereinstimmt.
* **Enddatum**: aktuelles Server-Datum.

Wenn das Startdatum größer oder gleich dem Enddatum ist, wird kein Prozess durchgeführt. In diesem Fall wird die Meldung **coalesceUpToDate** angezeigt.

Wenn das Startdatum vor dem Enddatum liegt, wird die Tabelle **NmsEmailErrorStat** bereinigt.

Die Gesamtzahl der Fehler in der Tabelle **NmsEmailErrorStat** zwischen dem Start- und dem Enddatum wird mithilfe der folgenden Abfrage abgerufen:

```sql
SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)
```

wobei `$end` und `$start` das zuvor definierte Start- und Enddatum sind.

Wenn die Summe größer als 0 ist:

1. Die folgende Abfrage wird ausgeführt, um nur Fehler über einen bestimmten Schwellenwert (der 20 entspricht) hinaus zu halten:

   ```sql
   SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20
   ```

1. Die Meldung **coalescingErrors** wird angezeigt.
1. Es wird eine neue Verbindung erstellt, um alle zwischen dem Start- und dem Enddatum aufgetretenen Fehler zu löschen. Die folgende Abfrage wird verwendet:

   ```sql
   DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)
   ```

1. Jeder Fehler wird mithilfe der folgenden Abfrage in der Tabelle **NmsEmailErrorStat** gespeichert:

   ```sql
   INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))
   ```

   wobei jede Variable mit einem Wert übereinstimmt, der von der vorherigen Abfrage abgerufen wurde.

1. Die Variable **start** wird mit den Werten des vorherigen Prozesses aktualisiert, um die Schleife abzuschließen.

Die Schleife und die Aufgabe werden beendet.

Bereinigungen werden für die Tabellen **NmsEmailError** und **cleanupNmsMxDomain** ausgeführt.

### Bereinigung der NmsEmailError -Tabelle {#cleanup-of-the-nmsemailerror-table-}

Die folgende Abfrage wird verwendet:

```sql
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Diese Abfrage löscht alle Zeilen ohne verknüpfte Datensätze in der Tabelle **NmsEmailErrorStat** aus der Tabelle **NmsEmailError**.

### Bereinigung der NmsMxDomain-Tabelle {#cleanup-of-the-nmsmxdomain-table-}

Die folgende Abfrage wird verwendet:

```sql
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Diese Abfrage löscht alle Zeilen ohne verknüpften Datensatz in der Tabelle **NmsEmailErrorStat** aus der Tabelle **NmsMxDomain**.

### Bereinigung der Vorschläge {#cleanup-of-propositions}

Wenn das Modul **Interaction** installiert ist, wird diese Aufgabe ausgeführt, um die Tabellen **NmsPropositionXxx** zu bereinigen.

Die Liste der Vorschlagstabellen wird abgerufen und gebündelt gelöscht, indem die folgende Abfrage verwendet wird:

```sql
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

wobei `$(option)` das für die Option **NmsCleanup_PropositionPurgeDelay** definierte Datum ist (siehe [Softwareverteilungs-Assistent](#deployment-wizard)).

### Bereinigung der Simulationstabellen {#cleanup-of-simulation-tables}

Diese Aufgabe bereinigt verwaiste Simulationstabellen (die nicht mehr mit einer Angebotssimulation oder einer Versandsimulation verknüpft sind).

1. Um die Liste der Simulationen abzurufen, die bereinigt werden müssen, wird die folgende Abfrage verwendet:

   ```sql
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. Der Name der zu löschenden Tabellen besteht aus dem Präfix **wkSimu_** , gefolgt von der Kennung der Simulation (z. B. **wkSimu_456831_aggr**):

   ```sql
   DROP TABLE wkSimu_456831_aggr
   ```

### Bereinigung des Audit-Protokolls {#cleanup-of-audit-trail}

Die folgende Abfrage wird verwendet:

```sql
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

wobei **$(tsDate)** das aktuelle Serverdatum ist, ab dem der für die Option **XtkCleanup_AuditTrailPurgeDelay** definierte Zeitraum abgezogen wird.

### Bereinigung von Nmsaddress {#cleanup-of-nmsaddress}

Die folgende Abfrage wird verwendet:

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=STATUS_QUARANTINE AND tsLastModified < $(NmsCleanup_AppSubscriptionRcpPurgeDelay + 5d) AND iType IN (MESSAGETYPE_IOS, MESSAGETYPE_ANDROID ) LIMIT 5000)
```

Diese Abfrage löscht alle Einträge, die sich auf iOS und Android beziehen.

### Optimierung der Statistikaktualisierung und -speicherung {#statistics-update}

Mit der Option **XtkCleanup_NoStats** können Sie das Verhalten des Speicheroptimierungsschritts des Bereinigungs-Workflows steuern.

Wenn die Option **XtkCleanup_NoStats** nicht vorhanden ist oder der Wert 0 beträgt, wird die Speicheroptimierung im ausführlichen Modus (VACUUM VERBOSE ANALYZE) auf PostgreSQL ausgeführt und die Statistiken auf allen anderen Datenbanken aktualisiert. Um sicherzustellen, dass dieser Befehl ausgeführt wird, überprüfen Sie die PostgreSQL-Protokolle. VACUUM gibt die Ausgabezeilen im Format `INFO: vacuuming "public.nmsactivecontact"` aus und ANALYZE gibt die Ausgabezeilen im Format `INFO: analyzing "public.nmsactivecontact"` aus.

Wenn der Wert der Option 1 ist, werden die Statistiken in keiner Datenbank aktualisiert. Die folgende Protokollzeile wird in den Workflow-Logs angezeigt: `Option 'XtkCleanup_NoStats' is set to '1'`.

Wenn der Wert der Option 2 ist, wird die Speicheranalyse im Ausführlichen Modus (ANALYZE VERBOSE) auf PostgreSQL ausgeführt und die Statistiken auf allen anderen Datenbanken aktualisiert. Um sicherzustellen, dass dieser Befehl ausgeführt wird, überprüfen Sie die PostgreSQL-Protokolle. ANALYZE gibt die Ausgabezeilen im Format `INFO: analyzing "public.nmsactivecontact"` aus.

### Abonnement-Bereinigung (NMAC) {#subscription-cleanup--nmac-}

Diese Aufgabe löscht alle Abonnements im Zusammenhang mit gelöschten Diensten oder Mobile Apps.

Um die Liste der Broadlog-Schemata abzurufen, wird die folgende Abfrage verwendet:

```sql
SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
```

Die Aufgabe ruft dann die Namen der mit dem Link **appSubscription** verknüpften Tabellen ab und löscht diese Tabellen.

Dieser Bereinigungs-Workflow löscht auch alle Einträge, bei denen disabled = 1 ist und die seit der in der Option **NmsCleanup_AppSubscriptionRcpPurgeDelay** festgelegten Zeit nicht aktualisiert wurden.

### Sitzungsinformationen bereinigen {#cleansing-session-information}

Diese Aufgabe bereinigt Informationen aus der Tabelle **sessionInfo**. Die folgende Abfrage wird verwendet:

```sql
DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### Bereinigen abgelaufener Ereignisse {#cleansing-expired-events}

Diese Aufgabe bereinigt die in den Ausführungsinstanzen empfangenen und gespeicherten Ereignisse sowie die in einer Kontrollinstanz archivierten Ereignisse.

### Bereinigungsreaktionen {#cleansing-reactions}

Diese Aufgabe bereinigt die Reaktionen (Tabelle **NmsRemaMatchRcp**), in denen die Hypothesen selbst gelöscht wurden.

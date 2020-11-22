---
solution: Campaign Classic
product: campaign
title: Datenbankbereinigungs-Workflow
description: Erfahren Sie, wie veraltete Daten automatisch bereinigt werden.
audience: production
content-type: reference
topic-tags: data-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2997'
ht-degree: 1%

---


# Datenbankbereinigungs-Workflow{#database-cleanup-workflow}

## Einleitung {#introduction}

The **[!UICONTROL Database cleanup]** workflow accessible via the **[!UICONTROL Administration > Production > Technical workflows]** node, lets you delete obsolete data to avoid exponential growth of the database. The workflow is triggered automatically without user intervention.

![](assets/ncs_cleanup_workflow.png)

## Konfiguration {#configuration}

Die Datenbankbereinigung wird auf zwei Ebenen konfiguriert: in der Workflow-Planung und im Bereitstellungsassistenten.

### Workflow-Planung {#the-scheduler}

>[!NOTE]
>
>Weiterführende Informationen zur Planung finden Sie in [diesem Abschnitt](../../workflow/using/scheduler.md).

Standardmäßig ist der Arbeitsablauf für die **[!UICONTROL Datenbankbereinigung]** so konfiguriert, dass er täglich um 4 Uhr Beginn wird. Mit der Planung können Sie den Workflow ändern, der die Häufigkeit auslöst. Die folgenden Frequenzen stehen zur Verfügung:

* **[!UICONTROL Mehrmals täglich]**
* **[!UICONTROL Täglich]**
* **[!UICONTROL Wöchentlich]**
* **[!UICONTROL Einmal]**

![](assets/ncs_cleanup_scheduler.png)

>[!IMPORTANT]
>
>Damit der Arbeitsablauf für die **[!UICONTROL Datenbankbereinigung]** zu dem in der Planung festgelegten Zeitpunkt und Zeitpunkt Beginn werden kann, muss das Workflow-Engine (wfserver) gestartet werden. Ist dies nicht der Fall, erfolgt die Datenbereingung der Datenbank erst nach dem nächsten Starten des Workflow-Engine.

### Bereitstellungsassistent {#deployment-wizard}

Mit dem **[!UICONTROL Bereitstellungsassistenten]**, der über das Menü &quot; **[!UICONTROL Werkzeuge&quot;> &quot;Erweitert]** &quot;aufgerufen wird, können Sie konfigurieren, wie lange Daten gespeichert werden. Die Werte werden in Tagen angegeben. Wenn diese Werte nicht geändert werden, verwendet der Workflow die Standardwerte.

![](assets/ncs_cleanup_deployment-wizard.png)

Die Felder im Fenster **[!UICONTROL Datenbereinigung]** stimmen mit den folgenden Optionen überein. Diese werden von einigen der Aufgaben verwendet, die vom **[!UICONTROL Datenbankbereinigungs]** -Arbeitsablauf ausgeführt werden:

* Konsolidierte Verfolgung: **NmsCleanup_TrackingStatPurgeDelay** (siehe [Bereinigen von Trackinglogs](#cleanup-of-tracking-logs))
* Versandlogs: **NmsCleanup_BroadLogPurgeDelay** (siehe [Bereinigen von Versandlogs](#cleanup-of-delivery-logs))
* Trackinglogs: **NmsCleanup_TrackingLogPurgeDelay** (siehe [Bereinigen von Trackinglogs](#cleanup-of-tracking-logs))
* Gelöschte Versand: **NmsCleanup_RecycledDeliveryPurgeDelay** (siehe [Bereinigen von Versänden, die gelöscht oder recycelt](#cleanup-of-deliveries-to-be-deleted-or-recycled)werden sollen)
* Ablehnungen importieren: **NmsCleanup_RejectsPurgeDelay** (siehe [Bereinigung von durch Importe](#cleanup-of-rejects-generated-by-imports-)generierten Ablehnungen)
* Besucher-Profil: **NmsCleanup_VisitorPurgeDelay** (siehe [Bereinigen von Besuchern](#cleanup-of-visitors))
* Angebotsvorschlag: **NmsCleanup_PropositionPurgeDelay** (siehe [Bereinigen von Vorschlägen](#cleanup-of-propositions))

   >[!NOTE]
   >
   >Das Feld **[!UICONTROL Angebotsvorschlag]** ist nur verfügbar, wenn das **Interaktionsmodul** installiert ist.

* Ereignisse: **NmsCleanup_EventPurgeDelay** (siehe [Datenbereingung abgelaufene Ereignis](#cleansing-expired-events))
* Archivierte Ereignis: **NmsCleanup_EventHistoPurgeDelay** (siehe abgelaufene [Datenbereingung-Ereignis](#cleansing-expired-events))

   >[!NOTE]
   >
   >Die **[!UICONTROL Felder &quot;Ereignisse]** &quot;und &quot; **[!UICONTROL Archivierte Ereignis]** &quot;stehen nur zur Verfügung, wenn das **Message Center** -Modul installiert ist.

* Prüfpfad: **XtkCleanup_AuditTrailPurgeDelay** (siehe [Bereinigung des Prüfpfads](#cleanup-of-audit-trail))

Alle vom **[!UICONTROL Datenbankbereinigungs]** -Workflow ausgeführten Aufgaben werden im folgenden Abschnitt beschrieben.

## Aufgaben des Arbeitsablaufs für die Datenbankbereinigung {#tasks-carried-out-by-the-database-cleanup-workflow}

Zu dem in der Workflow-Planung definierten Zeitpunkt (siehe Planung [) wird](#the-scheduler)das Workflow-Engine für den Datenbankbereinigungsprozess Beginn. Die Datenbankbereinigung stellt eine Verbindung zur Datenbank her und führt die Aufgaben in der unten gezeigten Reihenfolge aus.

>[!IMPORTANT]
>
>Wenn eine dieser Aufgaben fehlschlägt, werden die folgenden nicht ausgeführt.\
>SQL-Abfragen mit einem **LIMIT** -Attribut werden wiederholt ausgeführt, bis alle Informationen verarbeitet sind.

>[!NOTE]
>
>Die folgenden Abschnitte, die die Aufgaben des Arbeitsablaufs für die Datenbankbereinigung beschreiben, sind für Datenbankadministratoren oder Benutzer mit SQL-Kenntnissen vorbehalten.

### Listen zum Löschen der Bereinigung {#lists-to-delete-cleanup}

Die erste vom **[!UICONTROL Datenbank-Bereinigungs]** -Arbeitsablauf ausgeführte Aufgabe löscht alle Gruppen mit **deleteStatus != 0** Attribut aus der **NmsGroup**. Die mit diesen Gruppen verknüpften und in anderen Tabellen vorhandenen Datensätze werden ebenfalls gelöscht.

1. Zu löschende Listen werden mithilfe der folgenden SQL-Abfrage wiederhergestellt:

   ```
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. Jede Liste enthält mehrere Links zu anderen Tabellen. Alle diese Links werden mit der folgenden Abfrage stapelweise gelöscht:

   ```
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   wobei **$(relatedTable)** eine Tabelle ist, die sich auf **NmsGroup** bezieht, und **$(l)** die Liste-ID.

1. Wenn es sich bei der Liste um eine Liste vom Typ &quot;Liste&quot;handelt, wird die zugehörige Tabelle mit der folgenden Abfrage gelöscht:

   ```
   DROP TABLE grp$(l)
   ```

1. Jede durch den Vorgang wiederhergestellte **Select** Type-Liste wird mit der folgenden Abfrage gelöscht:

   ```
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   wobei **$(l)** die Kennung der Liste ist

### Bereinigung der zu löschenden oder zu recycelenden Versand {#cleanup-of-deliveries-to-be-deleted-or-recycled}

Mit dieser Aufgabe werden alle zu löschenden oder zu recycelnden Versand bereinigt.

1. Der Arbeitsablauf für die **[!UICONTROL Datenbankbereinigung]** wählt alle Versand aus, für die das Feld &quot; **deleteStatus** &quot;den Wert &quot; **[!UICONTROL Yes]** &quot;oder &quot; **[!UICONTROL Recycled]** &quot;hat und deren Löschtermin älter ist als der im Feld **[!UICONTROL Gelöschte Versand]******(NmsCleanup_RecycledDeliveryPurgeDelay) des Bereitstellungsassistenten definierte Zeitraum. For more on this, refer to [Deployment wizard](#deployment-wizard). Dieser Zeitraum wird im Verhältnis zum aktuellen Serverdatum berechnet.
1. Für jeden Mid-Sourcing-Server wählt die Aufgabe die Liste der zu löschenden Versand aus.
1. Der Arbeitsablauf für die **[!UICONTROL Datenbankbereinigung]** löscht Versandlogs, Anlagen, Informationen zur Mirrorseite und alle anderen damit zusammenhängenden Daten.
1. Bevor Sie den Versand endgültig löschen, werden die verknüpften Informationen aus den folgenden Tabellen entfernt:

   * In der Ausschlusstabelle des Versands (**NmsDlvExclusion**) wird die folgende Abfrage verwendet:

      ```
      DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
      ```

      wobei **$(l)** die Kennung des Versands ist.

   * In der Coupon-Tabelle (**NmsCouponValue**) wird die folgende Abfrage verwendet (mit Massenlöschungen):

      ```
      DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
      ```

      wobei **$(l)** die Kennung des Versands ist.

   * In den Versand-Protokolltabellen (**NmsBroadlogXxx**) werden Massenlöschungen in Stapeln von 20.000 Datensätzen ausgeführt.
   * In den Angebotsvorschlag-Tabellen (**NmsPropositionXxx**) werden Massenlöschungen in Stapeln von 20.000 Datensätzen ausgeführt.
   * In den Verfolgungsprotokolltabellen (**NmsTrackinglogXxx**) werden Massenlöschungen in Stapeln von 20.000 Datensätzen ausgeführt.
   * In der Fragment-Tabelle des Versands (**NmsDeliveryPart**) werden Massenlöschungen in Stapeln von 500.000 Datensätzen ausgeführt. Diese Tabelle enthält Personalisierungsinformationen zu den verbleibenden zu liefernden Nachrichten.
   * In der Datenfragmenttabelle der Mirrorseite (**NmsMirrorPageInfo**) werden Massenlöschungen in Stapeln von 20.000 Datensätzen für abgelaufene Versand und für fertige oder abgebrochene Teile ausgeführt. Diese Tabelle enthält Personalisierungsinformationen zu allen Nachrichten, die zum Generieren von Mirrorseiten verwendet werden.
   * In der Suchtabelle der Mirrorseite (**NmsMirrorPageSearch**) werden Massenlöschungen in Stapeln von 20.000 Datensätzen ausgeführt. Diese Tabelle ist ein Suchindex, der Zugriff auf Personalisierungsinformationen bietet, die in der Tabelle **NmsMirrorPageInfo** gespeichert sind.
   * In der Stapelverarbeitungsprotokolltabelle (**XtkJobLog**) werden Massenlöschungen in Stapeln von 20.000 Datensätzen ausgeführt. Diese Tabelle enthält das Protokoll der zu löschenden Versand.
   * In der Versand-URL-Verfolgungstabelle (**NmsTrackingUrl**) wird die folgende Abfrage verwendet:

      ```
      DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
      ```

      wobei **$(l)** die Kennung des Versands ist.

      Diese Tabelle enthält die URLs in den zu löschenden Versänden, um deren Verfolgung zu aktivieren.

1. Der Versand wird aus der Tabelle &quot;Versand&quot;(**NmsDelivery**) gelöscht:

   ```
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   wobei **$(l)** die Kennung des Versands ist.

#### Versand mit Mid-Sourcing {#deliveries-using-mid-sourcing}

Der Arbeitsablauf für die **[!UICONTROL Datenbankbereinigung]** löscht auch Versand auf den Mid-Sourcing-Servern.

1. Dazu prüft der Workflow, ob jeder Versand inaktiv ist (je nach Status). Wenn ein Versand aktiv ist, wird er vor dem Löschen beendet. Die Kontrolle wird wie folgt durchgeführt:

   ```
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   wobei **$(l)** die Kennung des Versands ist.

1. Wenn der Wert des Status **[!UICONTROL Beginn ausstehend]** ist, **[!UICONTROL Wird ausgeführt]** , **[!UICONTROL Wiederherstellung ausstehend]** , **[!UICONTROL Wiederherstellung läuft]** , **[!UICONTROL Pause angefordert]** **** **** ,Pause in progressoderPaused(Werte 51, 55, 61, 62, 71, 72, 75), wird der Versand gestoppt und der Aufgabe bereinigt die verknüpften Informationen.

### Bereinigung abgelaufener Versand {#cleanup-of-expired-deliveries}

Diese Aufgabe beendet Versand, deren Gültigkeitsdauer abgelaufen ist.

1. Der Arbeitsablauf für die **[!UICONTROL Datenbankbereinigung]** erstellt die Liste der Versand, die abgelaufen sind. Diese Liste umfasst alle abgelaufenen Versand mit einem anderen Status als &quot; **[!UICONTROL Fertig]** &quot;sowie Versand, die kürzlich beendet wurden und über 10.000 nicht verarbeitete Nachrichten enthalten. Die folgende Abfrage wird verwendet:

   ```
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   Wenn **Versand-Modus 1** mit dem **[!UICONTROL Massenmodus]** übereinstimmt, stimmt **state 51** mit dem Status &quot; **[!UICONTROL Beginn ausstehend]** &quot;überein, **state 85** **** stimmt mit dem Status &quot;VersandStopped&quot;überein, und die höchste Anzahl an Versandlogs, die auf dem Versand-Server serienmäßig aktualisiert wurden, entspricht 10.000000.

1. Der Workflow umfasst dann die Liste der zuletzt abgelaufenen Versand, die Mid-Sourcing verwenden. Versand, für die noch keine Versandlogs über den Mid-Sourcing-Server wiederhergestellt wurden, werden ausgeschlossen.

   Die folgende Abfrage wird verwendet:

   ```
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. Mit der folgenden Abfrage wird ermittelt, ob das Externe Konto noch aktiv ist, um Versand nach Datum zu filtern:

   ```
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. In Liste abgelaufener Versand wechseln Versandlogs, deren Status **[!UICONTROL Ausstehend]** lautet, zu **[!UICONTROL Versand abgebrochen]** , und alle Versand in dieser Liste zu **[!UICONTROL Fertig]** .

   Die folgenden Abfragen werden verwendet:

   ```
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   wobei **$(curdate)** das aktuelle Datum des Datenbankservers, **$(bl)** der Bezeichner der Meldung &quot;Versandlogs&quot;ist, **$(dl)** der Versand-Bezeichner, **Versand-Status 6** den Status &quot; **[!UICONTROL Ausstehend]** **** **** &quot;und der Status &quot; Versand 7canceledVersand&quot;erfüllt.

   ```
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   wobei der **Versand-Status 95** mit dem Status &quot; **[!UICONTROL Fertig]** &quot;übereinstimmt und **$(dl)** der Bezeichner des Versands.

1. Alle Fragmente (**DeliveryParts**) veralteter Versand werden gelöscht und alle veralteten Fragmente der in Bearbeitung befindlichen Benachrichtigungs-Versand werden gelöscht. Massenlöschung wird für beide Aufgaben verwendet.

   Die folgenden Abfragen werden verwendet:

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   wobei der **Versand-Status 95** mit dem Status &quot; **[!UICONTROL Fertig]** &quot;übereinstimmt, stimmt der Status &quot; **Versand&quot;85** mit dem Status &quot; **[!UICONTROL Angehalten]** &quot;überein und **$(curDate)** ist das aktuelle Serverdatum.

### Beseitigung von Mirrorseiten {#cleanup-of-mirror-pages}

Diese Aufgabe löscht die von Versänden verwendeten Webressourcen (Mirrorseiten).

1. Zunächst wird die Liste der zu bereinigenden Versand mithilfe der folgenden Abfrage wiederhergestellt:

   ```
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)"
   ```

   wobei **$(curDate)** das aktuelle Serverdatum ist.

1. Die Tabelle **NmsMirrorPageInfo** wird dann bereinigt, gegebenenfalls unter Verwendung der Kennung des zuvor wiederhergestellten Versands. Massenlöschung wird verwendet, um die folgenden Abfragen zu generieren:

   ```
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   wobei **$(dl)** die Kennung des Versands ist.

1. Dem Versand-Protokoll wird dann ein Eintrag hinzugefügt.
1. Gereinigte Versand werden dann identifiziert, um zu vermeiden, dass sie später erneut verarbeitet werden müssen. Die folgende Abfrage wird ausgeführt:

   ```
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   wobei **$(strIn)** die Liste der Versand-IDs ist.

### Aufräumen von Arbeitstischen {#cleanup-of-work-tables}

Diese Aufgabe löscht alle Arbeitstabellen, die Versänden entsprechen, deren Status **[!UICONTROL bearbeitet]** , **[!UICONTROL angehalten]** oder **[!UICONTROL gelöscht]** wird.

1. Die Liste von Tabellen, deren Namen mit **wkDlv_** beginnen, wird zuerst mit der folgenden Abfrage (postgresql) wiederhergestellt:

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. Die von Workflows verwendeten Tabellen werden dann ausgeschlossen. Zu diesem Zweck wird die Liste der ausgeführten Versand mithilfe der folgenden Abfrage wiederhergestellt:

   ```
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   wobei 0 der Wert ist, der mit dem Status **[!UICONTROL Bearbeitung]** des Versands übereinstimmt, 85 mit dem Status **[!UICONTROL Gestoppt]** und 100 mit dem Status **[!UICONTROL Gelöscht]** übereinstimmt.

1. Nicht mehr verwendete Tabellen werden mit der folgenden Abfrage gelöscht:

   ```
   DROP TABLE wkDlv_15487_1;
   ```

### Aufräumung der durch Importe entstandenen Ablehnungen {#cleanup-of-rejects-generated-by-imports-}

Mit diesem Schritt können Sie Datensätze löschen, für die während des Imports nicht alle Daten verarbeitet wurden.

1. Massenlöschung erfolgt auf der **XtkReject** -Tabelle mit der folgenden Abfrage:

   ```
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l))
   ```

   wobei **$(curDate)** das aktuelle Serverdatum ist, ab dem der für die Option **NmsCleanup_RejectsPurgeDelay** definierte Zeitraum abgezogen wird (siehe [Bereitstellungsassistent](#deployment-wizard)), und **$(l)** die maximale Anzahl der zu löschenden Datensätze ist.

1. Alle verwaisten Ablehnungen werden dann mit der folgenden Abfrage gelöscht:

   ```
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### Bereinigen von Workflow-Instanzen {#cleanup-of-workflow-instances}

Diese Aufgabe bereinigt jede Workflow-Instanz mit ihrem Identifer (**lWorkflowId**) und dem Verlauf (**lHistory**). Dadurch werden inaktive Tabellen gelöscht, indem die Aufgabe zur Bereinigung der Tabelle erneut ausgeführt wird. Die Bereinigung löscht auch alle verwaisten Arbeitstische (wkf% und wkfhisto%) der gelöschten Workflows.

>[!NOTE]
>
>Die Bereinigungshäufigkeit des Verlaufs wird für jeden Workflow im Feld **Verlauf in Tagen** angegeben (Standardwert 30 Tage). Dieses Feld finden Sie in den Workflow-Eigenschaften auf der Registerkarte &quot; **Ausführung** &quot;. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../workflow/using/workflow-properties.md#execution).

1. Um die Liste der zu löschenden Workflows wiederherzustellen, wird die folgende Abfrage verwendet:

   ```
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. Diese Abfrage generiert die Liste von Workflows, die zum Löschen aller verknüpften Protokolle, fertigen Aufgaben und fertigen Ereignis verwendet wird. Dabei werden folgende Abfragen verwendet:

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

1. Alle nicht verwendeten Tabellen werden gelöscht. Zu diesem Zweck werden alle Tabellen mithilfe einer **wkf%** -Typmaske mit der folgenden Abfrage (postgresql) erfasst:

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. Anschließend werden alle Tabellen, die von einer ausstehenden Workflow-Instanz verwendet werden, ausgeschlossen. Die Liste aktiver Workflows wird mithilfe der folgenden Abfrage wiederhergestellt:

   ```
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. Jeder Workflow-Bezeichner wird dann wiederhergestellt, um den Namen der Tabellen zu finden, die von Workflows in Bearbeitung sind. Diese Namen werden von der Liste zuvor wiederhergestellter Tabellen ausgeschlossen.
1. Verlaufstabellen vom Typ &quot;inkrementelle Abfrage&quot;werden mit den folgenden Abfragen ausgeschlossen:

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   wobei **$(strbedingung)** die Liste von Tabellen ist, die mit der **wkfhisto%** -Maske übereinstimmen.

1. Die übrigen Tabellen werden mit der folgenden Abfrage gelöscht:

   ```
   DROP TABLE wkf15487_12;
   ```

### Bereinigen von Workflow-Anmeldungen {#cleanup-of-workflow-logins}

Diese Aufgabe löscht Workflow-Anmeldungen mit der folgenden Abfrage:

```
DELETE FROM XtkWorkflowLogin WHERE iWorkflowId NOT IN (SELECT iWorkflowId FROM XtkWorkflow)
```

### Aufräumen verwaister Arbeitstische {#cleanup-of-orphan-work-tables}

Diese Aufgabe löscht verwaiste Arbeitstabellen, die mit Gruppen verknüpft sind. Die Tabelle **NmsGroup** speichert die zu bereinigenden Gruppen (mit einem anderen Typ als 0). Das Präfix der Tabellennamen ist **grp**. Zur Identifizierung der zu reinigenden Gruppen wird folgende Abfrage verwendet:

```
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### Aufräumarbeiten von Besuchern {#cleanup-of-visitors}

Diese Aufgabe löscht veraltete Datensätze mithilfe des Massenlöschens aus der Besucher-Tabelle. Veraltete Datensätze sind solche, deren letzte Änderung vor dem im Bereitstellungsassistenten festgelegten Erhaltungszeitraum liegt (siehe [Bereitstellungsassistent](#deployment-wizard)). Die folgende Abfrage wird verwendet:

```
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < AddDays(GetDate(), -30) AND iOrigin = 0 LIMIT 20000)
```

wobei **$(tsDate)** das aktuelle Serverdatum ist, von dem der für die Option **NmsCleanup_VisitorPurgeDelay** definierte Zeitraum abgezogen wird.

### Säuberung von NPAI {#cleanup-of-npai}

Mit dieser Aufgabe können Sie Datensätze, die gültige Adressen enthalten, aus der **NmsAddress** -Tabelle löschen. Die folgende Abfrage dient zum Durchführen des Massenlöschens:

```
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

wobei **Status 2** mit dem **[!UICONTROL Gültigen]** -Status übereinstimmt, ist **$(tsDate1)** das aktuelle Serverdatum und **$(tsDate2)** mit der Option **NmsCleanup_LastCleanup** übereinstimmt.

### Säuberung von Abonnements {#cleanup-of-subscriptions-}

Mit dieser Aufgabe werden alle vom Benutzer aus der **NmsSubscription** -Tabelle gelöschten Abonnement entfernt, indem eine Massenlöschung erfolgt. Die folgende Abfrage wird verwendet:

```
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### Säuberung von Trackinglogs {#cleanup-of-tracking-logs}

Diese Aufgabe löscht veraltete Datensätze aus den Protokolltabellen für Verfolgung und Webtracking. Veraltete Datensätze sind solche, die vor dem im Bereitstellungsassistenten festgelegten Erhaltungszeitraum liegen (siehe [Bereitstellungsassistent](#deployment-wizard)).

1. Erstens wird die Liste der Verfolgungstabellen mithilfe der folgenden Abfrage wiederhergestellt:

   ```
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. Massenlöschung wird verwendet, um alle Tabellen in Liste zuvor wiederhergestellter Tabellen zu bereinigen. Die folgende Abfrage wird verwendet:

   ```
   DELETE FROM XtkTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM XtkTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   wobei **$(tsDate)** das aktuelle Serverdatum ist, ab dem der für die Option **NmsCleanup_TrackingLogPurgeDelay** definierte Zeitraum abgezogen wird.

1. Die Tabelle der Verfolgungsstatistiken wird mithilfe des Massenlöschens bereinigt. Die folgende Abfrage wird verwendet:

   ```
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   wobei **$(tsDate)** das aktuelle Serverdatum ist, ab dem der für die Option **NmsCleanup_TrackingStatPurgeDelay** definierte Zeitraum abgezogen wird.

### Säuberung von Versandlogs {#cleanup-of-delivery-logs}

Mit dieser Aufgabe können Sie die in verschiedenen Tabellen gespeicherten Versandlogs bereinigen.

1. Zu diesem Zweck wird die Liste der Versand-Protokoll-Schema mithilfe der folgenden Abfrage wiederhergestellt:

   ```
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. Bei der Verwendung von Mid-Sourcing wird in Versand-Zuordnungen nicht auf die **NmsBroadLogMid** -Tabelle verwiesen. Das **nms:wideLogMid** -Schema wird zur Liste hinzugefügt, die von der vorherigen Abfrage wiederhergestellt wurde.
1. Der Arbeitsablauf für die **Datenbankbereinigung** bereinigt dann veraltete Daten aus zuvor wiederhergestellten Tabellen. Die folgende Abfrage wird verwendet:

   ```
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   wobei **$(tableName)** der Name der einzelnen Tabellen in der Liste der Schema und **$(option)** das für die Option **NmsCleanup_BroadLogPurgeDelay** definierte Datum ist (siehe [Bereitstellungsassistent](#deployment-wizard)).

1. Schließlich prüft der Workflow, ob die Tabelle **NmsProviderMsgId** vorhanden ist. Wenn ja, werden alle veralteten Daten mit der folgenden Abfrage gelöscht:

   ```
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   wobei **$(Option)** mit dem für die Option **NmsCleanup_BroadLogPurgeDelay** definierten Datum übereinstimmt (siehe [Bereitstellungsassistent](#deployment-wizard)).

### Bereinigen der NmsEmailErrorStat-Tabelle {#cleanup-of-the-nmsemailerrorstat-table-}

Diese Aufgabe löscht die **Tabelle NmsEmailErrorStat** . Das wichtigste Programm (**coalesceErrors**) definiert zwei Daten:

* **Beginn**: Datum des nächsten Prozesses, der mit der Option **NmsLastErrorStatCoalesce** oder dem neuesten Datum in der Tabelle übereinstimmt.
* **Enddatum**: aktuelles Serverdatum.

Wenn das Enddatum des Beginns größer oder gleich dem Enddatum ist, findet kein Prozess statt. In diesem Fall wird die **Meldung &quot;BildungUpToDate** &quot;angezeigt.

Wenn das Enddatum des Beginns vor dem Enddatum liegt, wird die **NmsEmailErrorStat** -Tabelle bereinigt.

Die Gesamtzahl der Fehler in der **NmsEmailErrorStat** -Tabelle zwischen Beginns- und Enddatum wird mithilfe der folgenden Abfrage wiederhergestellt:

```
"SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)"
```

Dabei sind **$end** und **$Beginn** die zuvor definierten Beginns- und Enddaten.

Wenn die Summe größer als 0 ist:

1. Die folgende Abfrage wird ausgeführt, um nur Fehler über einen bestimmten Schwellenwert (der 20 entspricht) hinaus zu halten:

   ```
   "SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20"
   ```

1. Die Meldung **coalescingErrors** wird angezeigt.
1. Eine neue Verbindung wird erstellt, um alle zwischen dem Beginns- und dem Enddatum auftretenden Fehler zu löschen. Die folgende Abfrage wird verwendet:

   ```
   "DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)"
   ```

1. Jeder Fehler wird mithilfe der folgenden Abfrage in der **Tabelle NmsEmailErrorStat** gespeichert:

   ```
   "INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))"
   ```

   wobei jede Variable mit einem durch die vorherige Abfrage wiederhergestellten Wert übereinstimmt.

1. Die Variable &quot; **Beginn** &quot;wird mit den Werten des vorherigen Prozesses aktualisiert, um die Schleife zu beenden.

Die Schleife und die Aufgabe halten an.

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

Die Liste der Propositionstabellen wird wiederhergestellt, und die Massenlöschung erfolgt auf jeder der folgenden Abfragen:

```
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

wobei **$(Option)** das für die Option **NmsCleanup_PropositionPurgeDelay** definierte Datum ist (siehe [Bereitstellungsassistent](#deployment-wizard)).

### Bereinigen von Simulationen {#cleanup-of-simulation-tables}

Diese Aufgabe bereinigt verwaiste Simulationen (die nicht mehr mit einer Angebot-Simulation oder einer Versand-Simulation verknüpft sind).

1. Zur Wiederherstellung der Liste von Simulationen, die bereinigt werden müssen, wird folgende Abfrage verwendet:

   ```
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. Der Name der zu löschenden Tabellen besteht aus dem **wkSimu_** -Präfix, gefolgt vom Bezeichner der Simulation (z. B.: **wkSimu_456831_aggr**):

   ```
   DROP TABLE wkSimu_456831_aggr
   ```

### Bereinigung des Prüfpfads {#cleanup-of-audit-trail}

Die folgende Abfrage wird verwendet:

```
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

wobei **$(tsDate)** das aktuelle Serverdatum ist, ab dem der für die Option **XtkCleanup_AuditTrailPurgeDelay** definierte Zeitraum ersetzt wird.

### Bereinigung von Nmsaddress {#cleanup-of-nmsaddress}

Die folgende Abfrage wird verwendet:

```
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=STATUS_QUARANTINE AND tsLastModified < $(NmsCleanup_AppSubscriptionRcpPurgeDelay + 5d) AND iType IN (MESSAGETYPE_IOS, MESSAGETYPE_ANDROID ) LIMIT 5000)
```

Diese Abfrage löscht alle Einträge im Zusammenhang mit iOS und Android.

### Aktualisierung und Datenspeicherung von Statistiken {#statistics-update}

Mit der **Option &quot;XtkCleanup_NoStats** &quot;können Sie das Verhalten des Datenspeicherung-Optimierungsschritts des Bereinigungs-Workflows steuern.

Wenn die Option **XtkCleanup_NoStats** nicht vorhanden ist oder der Wert 0 ist, wird die Datenspeicherung-Optimierung im Ausführlichen Modus (VACUUM VERBOSE ANALYZE) auf PostgreSQL ausgeführt und die Statistik für alle anderen Datenbanken aktualisiert. Um sicherzustellen, dass dieser Befehl ausgeführt wird, überprüfen Sie die PostgreSQL-Protokolle. VACUUM gibt Zeilen im Format aus: `INFO: vacuuming "public.nmsactivecontact"` und ANALYZE gibt Zeilen im Format aus: `INFO: analyzing "public.nmsactivecontact"`.

Wenn der Wert der Option 1 ist, werden keine statistischen Aktualisierungen in einer Datenbank durchgeführt. Die folgende Protokollzeile wird in den Workflow-Protokollen angezeigt: `Option 'XtkCleanup_NoStats' is set to '1'`.

Wenn der Wert der Option 2 ist, wird die Datenspeicherung Analyse im ausführlichen Modus (ANALYZE VERBOSE) auf PostgreSQL ausgeführt und die Statistik für alle anderen Datenbanken aktualisiert. Um sicherzustellen, dass dieser Befehl ausgeführt wird, überprüfen Sie die PostgreSQL-Protokolle. ANALYZE gibt Zeilen im Format aus: `INFO: analyzing "public.nmsactivecontact"`.

### Abonnement-Bereinigung (NMAC) {#subscription-cleanup--nmac-}

Diese Aufgabe löscht alle Abonnement im Zusammenhang mit gelöschten Diensten oder Mobilanwendungen.

Zur Wiederherstellung der Liste von Broadlog-Schemas wird folgende Abfrage verwendet:

```
SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
```

Die Aufgabe stellt dann die mit dem **appSubscription** -Link verknüpften Tabellennamen wieder her und löscht diese.

Dieser Bereinigungsarbeitsablauf löscht auch alle Einträge, bei denen deaktiviert = 1 ist und die seit dem in der Option **NmsCleanup_AppSubscriptionRcpPurgeDelay** festgelegten Zeitraum nicht aktualisiert wurden.

### Sitzungsinformationen der Datenbereingung {#cleansing-session-information}

Diese Aufgabe löscht Informationen aus der **Tabelle sessionInfo** . Es wird folgende Abfrage verwendet:

```
 DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### Datenbereingung abgelaufen Ereignis {#cleansing-expired-events}

Mit dieser Aufgabe werden die auf den Ausführungsinstanzen und auf einer Kontrollinstanz archivierten Ereignis gereinigt.

### Datenbereingungen {#cleansing-reactions}

Diese Aufgabe bereinigt die Reaktionen (Tabelle **NmsRemaMatchRcp**), in denen die Hypothesen selbst gelöscht wurden.

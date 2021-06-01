---
solution: Campaign Classic
product: campaign
title: Ergänzende Konfigurationen
description: Erfahren Sie, wie Sie zusätzliche Konfigurationen für Transaktionsnachrichten in Adobe Campaign Classic einrichten.
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 4d25d740-db57-4d18-8cae-2dd49c4a786e
source-git-commit: a9054fb8e10bef37675922b2f81c7615cd04c1bb
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 82%

---

# Ergänzende Konfigurationen {#mc-additional-configurations}

## Schwellenwerte überwachen {#monitoring-thresholds}

Sie können die Hinweis- und Warnschwellen der Kennzahlen konfigurieren (orange bzw. rot), die in den Berichten **Message Center Dienstqualität** und **Message Center Verarbeitungsdauer** angezeigt werden (siehe [Über Transaktionsnachrichten-Berichte](../../message-center/using/about-transactional-messaging-reports.md)).

Gehen Sie dazu wie folgt vor:

1. Öffnen Sie den Softwareverteilungs-Assistenten auf der Ausführungsinstanz **a1/>.**

1. Gehen Sie zur Seite **[!UICONTROL Message Center]** .

1. Verwenden Sie die Pfeile, um die Schwellenwerte zu ändern.

   ![](assets/messagecenter_monitor_events_001.png)

>[!NOTE]
>
>Die Anzahl der Ereignisse in der Warteschlange wird im Bereich [Systemindikator](../../production/using/monitoring-processes.md#system-indicators) der Prozessüberwachungsseite von Adobe Campaign angezeigt. Weiterführende Informationen zum Softwareverteilungs-Assistenten finden Sie in [diesem Abschnitt](../../installation/using/deploying-an-instance.md#deployment-wizard).

## Ereignisse bereinigen {#purging-events}

Die Dauer der Speicherung der Ereignisse in der Datenbank kann über den [Implementierungsassistenten](../../production/using/database-cleanup-workflow.md#deployment-wizard) konfiguriert werden.

Die Bereinigung der Ereignisse wird automatisch vom [Datenbankbereinigungs-Workflow](../../production/using/database-cleanup-workflow.md) durchgeführt. Gelöscht werden dabei die in den Ausführungsinstanzen empfangenen und gespeicherten Ereignisse sowie die in der Kontrollinstanz archivierten Ereignisse.

Um die Bereinigungsparameter zu ändern, nutzen Sie die aufsteigenden und absteigenden Pfeile.

Bereinigungsparameter in Kontrollinstanzen:

![](assets/messagecenter_delete_events_001.png)

Bereinigungsparamter in Ausführungsinstanzen:

![](assets/messagecenter_delete_events_002.png)

Weitere Informationen zum Datenbankbereinigungs-Workflow finden Sie in [diesem Abschnitt](../../production/using/database-cleanup-workflow.md).


## Technische Workflows {#technical-workflows}

Die technischen Workflows für Message Center sind teils in der Kontrollinstanz, teils in der oder den Ausführungsinstanz(en) enthalten.

Vor Freigabe der Transaktionsnachrichten-Vorlagen muss sichergestellt werden, dass die mit Transaktionsnachrichten in Verbindung stehenden technischen Workflows (Message Center) der Kontrollinstanz und der verschiedenen Ausführungsinstanzen erstellt und gestartet sind.

### Workflows der Kontrollinstanz {#control-instance-workflows}

In der Kontrollinstanz müssen Sie, unabhängig davon, ob Sie eine oder mehrere Ausführungsinstanzen registriert haben, für jedes externe **[!UICONTROL Message Center Ausführungs-Instanz]**-Konto einen Archivierungs-Workflow erstellen. Klicken Sie auf die Schaltfläche **[!UICONTROL Archivierungs-Workflow erstellen]**, um den Workflow zu erstellen und zu starten.

![](assets/messagecenter_archiving_002.png)

Diese Workflows können Sie dann über den Ordner **Administration > Betreibung > Message Center** aufrufen. Nach der Erstellung werden die Archivierungs-Workflows automatisch gestartet.

<!--**Minimal architecture**

Once the control and execution modules are installed on the same instance, you must create the archiving workflow using the deployment wizard. Click the **[!UICONTROL Create the archiving workflow]** button to create and start the workflow.

![](assets/messagecenter_archiving_001.png)-->

### Workflows der Ausführungsinstanz {#execution-instance-workflows}

Der Zugriff auf die Transaktionsnachrichten-spezifischen, technischen Workflows erfolgt in der oder den Ausführungsinstanz(en) im Knoten **Administration > Betreibung > Message Center**. Stellen Sie sicher, dass alle Workflows gestartet wurden. Folgende Workflows stehen zur Verfügung:

* **[!UICONTROL Verarbeitung der Batch-Ereignisse]** (interner Name **[!UICONTROL batchEventsProcessing]**): teilt die Batch-Ereignisse einer Warteschlange zu, bis sie einer Nachrichtenvorlage zugeordnet werden.
* **[!UICONTROL Verarbeitung der Echtzeit-Ereignisse]** (interner Name **[!UICONTROL rtEventsProcessing]**): teilt die Echtzeit-Ereignisse einer Warteschlange zu, bis sie einer Nachrichtenvorlage zugeordnet werden.
* **[!UICONTROL Update des Ereignisstatus]** (interner Name **[!UICONTROL updateEventStatus]**): ordnet jedem Ereignis einen Status zu.

   Folgende Status sind möglich:

   * **[!UICONTROL Ausstehend]**: Das Ereignis befindet sich in der Warteschlange und wurde noch keiner Nachrichtenvorlage zugeteilt.
   * **[!UICONTROL Versand ausstehend]**: Das Ereignis befindet sich in der Warteschlange, wurde einer Nachrichtenvorlage zugeordnet und wird vom Versand verarbeitet.
   * **[!UICONTROL Gesendet]**: Dieser Status wird aus den Versandlogs übernommen. Er bedeutet, dass die Nachricht gesendet wurde.
   * **[!UICONTROL Vom Versand ignoriert]**: Der Versand konnte nicht erfolgen, z. B. aufgrund einer Quarantäne (Status wird den Versandlogs entnommen).
   * **[!UICONTROL Versandfehler]**: Der Versand ist fehlgeschlagen (Status wird den Versandlogs entnommen).
   * **[!UICONTROL Ereignis wurde nicht berücksichtigt]**: Das Ereignis konnte keiner Vorlage zugeordnet werden. Das Ereignis wird nicht erneut verarbeitet.

## Multibranding konfigurieren {#configuring-multibranding}

In diesem Abschnitt wird eine Lösung beschrieben, mit der Tracking- und Mirrorseiten-URLs für jede Marke für Transaktionsnachrichten in Adobe Campaign konfiguriert werden können.

### Voraussetzungen {#prerequisites}

* Alle Hosts müssen der Konfigurationsdatei der Instanz (`config-<instance>.xml`) hinzugefügt werden.
* Jeder Marke muss eine Sub-Domain zugewiesen werden.
* Wenn das Webtracking auf HTTPS-Seiten erfolgt, müssen Sie für alle Marken über ein HTTPS-Zertifikat verfügen.

Um Multibranding zu konfigurieren, müssen Sie sowohl Ausführungsinstanzen als auch Kontrollinstanzen konfigurieren.

### Ausführungsinstanz konfigurieren {#execution-instance}

Gehen Sie in den Ausführungsinstanzen wie folgt vor:

1. Erstellen Sie für jede Marke ein externes Konto.

   >[!NOTE]
   >
   >Erfahren Sie im Abschnitt [Kontrollinstanz](../../message-center/using/configuring-instances.md#control-instance) , wie Sie ein externes Konto vom Typ Ausführungsinstanz erstellen.

1. Erweitern Sie das Schema nms:extAccount, um die Tracking-URL hinzuzufügen:

   ```
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   ```

   >[!NOTE]
   >
   >Erfahren Sie im Abschnitt [Erweitern eines Schemas](../../configuration/using/extending-a-schema.md) , wie Sie ein vorhandenes Schema erweitern.

1. Passen Sie das Formular nms:extAccount an:

   ```
   <container label="Message domain branding" type="frame">
        <static type="help"> These parameters are used to override the DNS alias and addresses used during message delivery. When not populated, the values of the 'NmsServer_MirrorPageUrl' and 'NmsEmail_DefaultErrorAddr' options are used.</static>
        <input xpath="@mirrorURL"/>
        <input xpath="@trackingURL"/>
        <input img="nms:sendemail.png" menuId="deliveryMenuBuilder" type="scriptEdit">
               xpath="errorAddress"/>
      </container>
   ```

1. Passen Sie die Optionen NmsTracking_OpenFormula und NmsTracking_ClickFormula so an, dass das externe Konto anstelle einer globalen Option verwendet wird.

   Ersetzen Sie zu diesem Zweck:

   ```
   <%@ include option='NmsTracking_ServerUrl' %>
   ```

   durch:

   ```
   <%@ value object="provider" xpath="@trackingURL" %>
   ```

   >[!IMPORTANT]
   >
   >Diese Änderungen könnten beim Upgrade Konflikte verursachen. Möglicherweise müssen Sie diese Formeln manuell in ihre neue Version einbinden.

### Kontrollinstanz konfigurieren {#control-instance}

In der Kontrollinstanz müssen Versandvorlagen mit externen Konten verknüpft werden.

Gehen Sie dazu wie folgt vor:

1. Erstellen Sie für jede Marke ein externes Konto mit demselben internen Namen wie in der [Ausführungsinstanz](#execution-instance) (Schritt 1) definiert.

1. Erstellen Sie für jede Marke eine Standard-Versandvorlage.

   >[!NOTE]
   >
   >    In [diesem Abschnitt](../../delivery/using/creating-a-delivery-template.md#creating-a-new-template) erfahren Sie, wie Sie eine Versandvorlage erstellen.

1. Konfigurieren Sie in den **[!UICONTROL Eigenschaften]** der Versandvorlage das Routing zum externen Konto der Marke.

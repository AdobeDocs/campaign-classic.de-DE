---
product: campaign
title: Audit-Protokoll
description: Erfahren Sie, wie Sie Ihre Instanz mit dem Audit-Protokoll von Campaign überwachen.
feature: Audit Trail, Monitoring, Workflows
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 64%

---

# Audit-Protokoll{#audit-trail}



In Adobe Campaign erhalten Sie über das **[!UICONTROL Audit-Protokoll]** Zugriff auf den vollständigen Verlauf der in Ihrer Instanz vorgenommenen Änderungen.

**[!UICONTROL Audit-Protokoll]** erfasst in Echtzeit eine umfassende Liste von Aktionen und Ereignissen, die in Ihrer Adobe Campaign-Instanz auftreten. Es bietet eine Möglichkeit für den Zugriff auf einen Datenverlauf, um zum Beispiel folgende Fragen zu beantworten: Was ist mit Ihren Workflows passiert und wer hat sie zuletzt aktualisiert? Was haben Ihre Benutzenden in der Instanz getan?

>[!NOTE]
>
>Adobe Campaign prüft keine Änderungen an Benutzerrechten, Vorlagen, Personalisierungen oder Kampagnen.\
>Das Audit-Protokoll kann nur von Admins der Instanz verwaltet werden.

Audit-Protokoll besteht aus drei Komponenten:

* **Schema-Audit-Protokoll**: Überprüfen Sie die Aktivitäten und letzten Änderungen an Ihren Schemas.

  Weiterführende Informationen zu Schemata finden Sie auf dieser [Seite](../../configuration/using/data-schemas.md).

* **Workflow-Audit-Protokoll**: Überprüfen Sie Aktivitäten und letzte Änderungen an Workflows sowie zusätzlich den Status Ihrer Workflows, z. B.:

   * Starten
   * Aussetzen
   * Stoppen
   * Neu starten
   * Bereinigen, was der Aktion „Verlauf bereinigen“ entspricht
   * Simulieren, was der Aktion „Starten“ im Simulationsmodus entspricht
   * Wecken, was der Aktion „Vorgezogene Ausführung der ausstehenden Aufgaben“ entspricht
   * Unbedingter Stopp

  Weiterführende Informationen zu Workflows finden Sie auf [dieser Seite](../../workflow/using/about-workflows.md).

  Weiterführende Informationen zur Überwachung Workflows finden Sie im [entsprechenden Abschnitt](../../workflow/using/monitoring-workflow-execution.md).

* **Option-Audit-Protokoll**: Überprüfen Sie die Aktivitäten und letzten Änderungen an Ihren Optionen.

  Weiterführende Informationen zu Optionen finden Sie auf [dieser Seite](../../installation/using/configuring-campaign-options.md).

## Zugriff auf das Audit-Protokoll {#accessing-audit-trail}

So greifen Sie auf das **[!UICONTROL Audit-Protokoll]** Ihrer Instanz zu:

1. Greifen Sie auf das Menü **[!UICONTROL Explorer]** Ihrer Instanz zu.
1. Wählen Sie im Menü **[!UICONTROL Administration]** die Option **[!UICONTROL Audit]** aus.

   ![](assets/audit_trail_1.png)

1. Das Fenster **[!UICONTROL Audit-Protokoll]** wird mit der Liste Ihrer Entitäten geöffnet. Adobe Campaign prüft die Erstellungs-, Bearbeitungs- und Löschaktionen für Workflows, Optionen und Schemata.

   Wählen Sie eine der Entitäten aus, um mehr über die letzten Änderungen zu erfahren.

   ![](assets/audit_trail_2.png)

1. Im Fenster **[!UICONTROL Audit-Entität]** erhalten Sie detailliertere Informationen zu der ausgewählten Entität, z. B.:

   * **[!UICONTROL Typ]** : Workflow, Optionen oder Schemas.
   * **[!UICONTROL Entität]**: Interner Name Ihrer Aktivitäten.
   * **[!UICONTROL Geändert von]**: Benutzername der Person, die diese Entität zuletzt geändert hat.
   * **[!UICONTROL Aktion]** : Letzte Aktion, die für diese Entität ausgeführt wurde, entweder erstellt, bearbeitet oder gelöscht.
   * **[!UICONTROL Änderungsdatum]**: Datum der letzten Aktion, die an dieser Entität durchgeführt wurde.

   Der Code-Block liefert Ihnen weitere Informationen darüber, was in Ihrer Entität genau geändert wurde.

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>Standardmäßig ist die Aufbewahrungsfrist für **[!UICONTROL Auditprotokolle]** auf 180 Tage festgelegt. Weiterführende Informationen zur Änderung des Aufbewahrungszeitraums finden Sie auf dieser [Seite](../../production/using/database-cleanup-workflow.md#deployment-wizard).

## Aktivieren/Deaktivieren des Audit-Protokolls {#enable-disable-audit-trail}

Das Audit-Protokoll kann für eine bestimmte Aktivität einfach aktiviert oder deaktiviert werden, beispielsweise wenn Sie Speicherplatz in der Datenbank sparen möchten.

Gehen Sie dabei folgendermaßen vor:

1. Greifen Sie auf das Menü **[!UICONTROL Explorer]** Ihrer Instanz zu.
1. Wählen Sie im Menü **[!UICONTROL Administration]** die Option **[!UICONTROL Plattform]** und dann die Option **[!UICONTROL Optionen]** aus.

   ![](assets/audit_trail_4.png)

1. Wählen Sie je nach zu aktivierender/deaktivierender Entität eine der folgenden Optionen aus:

   * Für Workflow: **[!UICONTROL XtkAudit_Workflows]**
   * Für Schemata: **[!UICONTROL XtkAudit_DataSchema]**
   * Für Optionen: **[!UICONTROL XtkAudit_Option]**
   * Für jede Entität: **[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. Ändern Sie den **[!UICONTROL Wert]** in „1“, wenn Sie die Entität aktivieren möchten, oder in „0“, wenn Sie sie deaktivieren möchten.

   ![](assets/audit_trail_6.png)

1. Wählen Sie **[!UICONTROL Speichern]** aus .

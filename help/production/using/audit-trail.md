---
product: campaign
title: Audit-Protokoll
description: Erfahren Sie, wie Sie Ihre Instanz mit dem Campaign Audit-Protokoll überwachen.
feature: Audit Trail, Monitoring, Workflows
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 17%

---

# Audit-Protokoll{#audit-trail}



In Adobe Campaign wird die **[!UICONTROL Audit-Protokoll]** gibt Ihnen Zugriff auf den vollständigen Verlauf der Änderungen, die in Ihrer Instanz vorgenommen wurden.

**[!UICONTROL Audit-Protokoll]** erfasst in Echtzeit eine umfassende Liste von Aktionen und Ereignissen, die in Ihrer Adobe Campaign-Instanz auftreten. Es bietet eine Möglichkeit für den Zugriff auf einen Datenverlauf, um zum Beispiel folgende Fragen zu beantworten: Was ist mit Ihren Workflows passiert und wer hat sie zuletzt aktualisiert? Was haben Ihre Benutzenden in der Instanz getan?

>[!NOTE]
>
>Adobe Campaign prüft keine Änderungen an Benutzerrechten, Vorlagen, Personalisierungen oder Kampagnen.\
>Das Audit-Protokoll kann nur von Administratoren der Instanz verwaltet werden.

Audit-Protokoll besteht aus drei Komponenten:

* **Schema-Audit-Protokoll**: Überprüfen Sie die Aktivitäten und letzten Änderungen an Ihren Schemas.

  Weiterführende Informationen zu Schemata finden Sie in diesem Abschnitt [page](../../configuration/using/data-schemas.md).

* **Workflow-Audit-Protokoll**: Überprüfen Sie Aktivitäten und letzte Änderungen an Workflows sowie zusätzlich den Status Ihrer Workflows, z. B.:

   * Starten
   * Aussetzen
   * Stoppen
   * Neu starten
   * Bereinigung, die dem Aktionsbereinigungsverlauf entspricht
   * Simulieren, welche der Aktion Start im Simulationsmodus entspricht
   * Wakeup, der der Aktion Ausstehende Aufgaben jetzt ausführen entspricht
   * Unbedingter Stopp

  Weiterführende Informationen zu Workflows finden Sie in diesem Abschnitt [page](../../workflow/using/about-workflows.md).

  Weiterführende Informationen zur Überwachung von Workflows finden Sie im Abschnitt [dedizierter Abschnitt](../../workflow/using/monitoring-workflow-execution.md).

* **Option-Audit-Protokoll**: Überprüfen Sie die Aktivitäten und letzten Änderungen an Ihren Optionen.

  Weiterführende Informationen zu Optionen finden Sie in diesem Abschnitt [page](../../installation/using/configuring-campaign-options.md).

## Zugriff auf das Audit-Protokoll {#accessing-audit-trail}

So greifen Sie auf die **[!UICONTROL Audit-Protokoll]** :

1. Zugriff auf **[!UICONTROL Explorer]** -Menü Ihrer Instanz.
1. Unter dem **[!UICONTROL Administration]** Menü auswählen **[!UICONTROL Prüfung]** .

   ![](assets/audit_trail_1.png)

1. Das Fenster **[!UICONTROL Audit-Protokoll]** wird mit der Liste Ihrer Entitäten geöffnet. Adobe Campaign prüft die Erstellungs-, Bearbeitungs- und Löschaktionen für Workflows, Optionen und Schemata.

   Wählen Sie eine der Entitäten aus, um mehr über die letzten Änderungen zu erfahren.

   ![](assets/audit_trail_2.png)

1. Die **[!UICONTROL Auditstelle]** enthält detailliertere Informationen zur ausgewählten Entität, z. B.:

   * **[!UICONTROL Typ]** : Workflow, Optionen oder Schemata.
   * **[!UICONTROL Entität]** : Interner Name Ihrer Aktivitäten.
   * **[!UICONTROL Geändert von]** : Benutzername der letzten Person, die diese Entität zuletzt geändert hat.
   * **[!UICONTROL Aktion]** : Letzte Aktion, die für diese Entität ausgeführt wurde, entweder &quot;Erstellt&quot;, &quot;Bearbeitet&quot;oder &quot;Gelöscht&quot;.
   * **[!UICONTROL Änderungsdatum]** : Datum der letzten Aktion, die für diese Entität durchgeführt wurde.

   Der Codeblock liefert weitere Informationen darüber, was genau in Ihrer Entität geändert wurde.

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>Standardmäßig ist die Aufbewahrungsfrist auf 180 Tage für **[!UICONTROL Auditprotokolle]** . Weiterführende Informationen zur Änderung des Aufbewahrungszeitraums finden Sie in diesem [page](../../production/using/database-cleanup-workflow.md#deployment-wizard).

## Audit-Protokoll aktivieren/deaktivieren {#enable-disable-audit-trail}

Das Audit-Protokoll kann für eine bestimmte Aktivität einfach aktiviert oder deaktiviert werden, wenn Sie beispielsweise Speicherplatz in der Datenbank sparen möchten.

Gehen Sie dabei folgendermaßen vor:

1. Zugriff auf **[!UICONTROL Explorer]** -Menü Ihrer Instanz.
1. Unter dem **[!UICONTROL Administration]** Menü auswählen **[!UICONTROL Plattform]** then **[!UICONTROL Optionen]** .

   ![](assets/audit_trail_4.png)

1. Wählen Sie je nach Entität, die Sie aktivieren/deaktivieren möchten, eine der folgenden Optionen aus:

   * Für Workflow: **[!UICONTROL XtkAudit_Workflows]**
   * Für Schemas: **[!UICONTROL XtkAudit_DataSchema]**
   * Für Optionen: **[!UICONTROL XtkAudit_Option]**
   * Für jede Entität: **[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. Ändern Sie die **[!UICONTROL Wert]** auf 1 gesetzt, wenn Sie die Entität aktivieren möchten, oder auf 0, wenn Sie sie deaktivieren möchten.

   ![](assets/audit_trail_6.png)

1. Wählen Sie **[!UICONTROL Speichern]** aus .

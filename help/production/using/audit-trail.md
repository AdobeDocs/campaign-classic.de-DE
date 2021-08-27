---
product: campaign
title: Audit-Protokoll
description: Audit-Protokoll
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 7%

---

# Audit-Protokoll{#audit-trail}

![](../../assets/v7-only.svg)

In Adobe Campaign erhalten Sie über das **[!UICONTROL Audit-Protokoll]** Zugriff auf den vollständigen Verlauf der in Ihrer Instanz vorgenommenen Änderungen.

**[!UICONTROL Das Audit-Protokoll erfasst in Echtzeit eine umfassende Liste von Aktionen und Ereignissen, die in Ihrer Adobe Campaign-Instanz auftreten.]** Es bietet eine Self-Service-Möglichkeit, auf einen Datenverlauf zuzugreifen, um Fragen zu beantworten, z. B.: was mit Ihren Workflows passiert ist und wer sie zuletzt aktualisiert hat oder was Ihre Benutzer in der Instanz getan haben.

>[!NOTE]
>
>Adobe Campaign prüft keine Änderungen an Benutzerrechten, Vorlagen, Personalisierungen oder Kampagnen.\
>Das Audit-Protokoll kann nur von Administratoren der Instanz verwaltet werden.

Audit-Protokoll besteht aus drei Komponenten:

* **Schema-Audit-Protokoll**: Überprüfen Sie die Aktivitäten und letzten Änderungen an Ihren Schemas.

   Weiterführende Informationen zu Schemata finden Sie auf dieser [Seite](../../configuration/using/data-schemas.md).

* **Workflow-Audit-Protokoll**: Überprüfen Sie Aktivitäten und letzte Änderungen an Workflows sowie zusätzlich den Status Ihrer Workflows, z. B.:

   * Starten
   * Aussetzen
   * Stoppen
   * Neu starten
   * Bereinigen entspricht dem Aktionsbereinigungsverlauf
   * Simulieren, welche der Aktion Start im Simulationsmodus entspricht
   * Wakeup, der der Aktion Ausstehende Aufgaben jetzt ausführen entspricht
   * Unbedingter Stopp

   Weiterführende Informationen zu Workflows finden Sie auf dieser [Seite](../../workflow/using/about-workflows.md).

   Weiterführende Informationen zur Überwachung von Workflows finden Sie im Abschnitt [Dediziertes ](../../workflow/using/monitoring-workflow-execution.md).

* **Option-Audit-Protokoll**: Überprüfen Sie die Aktivitäten und zuletzt vorgenommenen Änderungen an Ihren Optionen.

   Weiterführende Informationen zu den Optionen finden Sie auf dieser [Seite](../../installation/using/configuring-campaign-options.md).

## Zugriff auf das Audit-Protokoll {#accessing-audit-trail}

So greifen Sie auf das **[!UICONTROL Audit-Protokoll]** Ihrer Instanz zu:

1. Rufen Sie das Menü **[!UICONTROL Explorer]** Ihrer Instanz auf.
1. Wählen Sie im Menü **[!UICONTROL Administration]** die Option **[!UICONTROL Audit]** .

   ![](assets/audit_trail_1.png)

1. Das Fenster **[!UICONTROL Audit trail]** wird mit der Liste Ihrer Entitäten geöffnet. Adobe Campaign prüft die Aktionen zum Erstellen, Bearbeiten und Löschen von Workflows, Optionen und Schemata.

   Wählen Sie eine der Entitäten aus, um mehr über die letzten Änderungen zu erfahren.

   ![](assets/audit_trail_2.png)

1. Das Fenster **[!UICONTROL Auditstelle]** enthält detailliertere Informationen zur ausgewählten Entität, z. B.:

   * **[!UICONTROL Typ]** : Workflow, Optionen oder Schemas.
   * **[!UICONTROL Entität]** : Interner Name Ihrer Aktivitäten.
   * **[!UICONTROL Geändert von]** : Benutzername der letzten Person, die diese Entität zuletzt geändert hat.
   * **[!UICONTROL Aktion]** : Letzte Aktion, die für diese Entität ausgeführt wurde, entweder &quot;Erstellt&quot;, &quot;Bearbeitet&quot;oder &quot;Gelöscht&quot;.
   * **[!UICONTROL Änderungsdatum]** : Datum der letzten Aktion, die für diese Entität durchgeführt wurde.

   Der Codeblock liefert weitere Informationen darüber, was genau in Ihrer Entität geändert wurde.

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>Standardmäßig ist die Aufbewahrungsfrist für **[!UICONTROL Auditprotokolle]** auf 180 Tage eingestellt. Weiterführende Informationen zur Änderung des Aufbewahrungszeitraums finden Sie auf dieser [Seite](../../production/using/database-cleanup-workflow.md#deployment-wizard).

## Audit-Protokoll aktivieren/deaktivieren {#enable-disable-audit-trail}

Das Audit-Protokoll kann für eine bestimmte Aktivität einfach aktiviert oder deaktiviert werden, wenn Sie beispielsweise Speicherplatz in der Datenbank sparen möchten.

Gehen Sie dabei folgendermaßen vor:

1. Rufen Sie das Menü **[!UICONTROL Explorer]** Ihrer Instanz auf.
1. Wählen Sie im Menü **[!UICONTROL Administration]** **[!UICONTROL Plattform]** und dann **[!UICONTROL Optionen]** aus.

   ![](assets/audit_trail_4.png)

1. Wählen Sie je nach Entität, die Sie aktivieren/deaktivieren möchten, eine der folgenden Optionen aus:

   * Für Workflow: **[!UICONTROL XtkAudit_Workflows]**
   * Für Schemas: **[!UICONTROL XtkAudit_DataSchema]**
   * Für Optionen: **[!UICONTROL XtkAudit_Option]**
   * Für jede Entität: **[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. Ändern Sie den Wert **[!UICONTROL Wert]** in 1, wenn Sie die Entität aktivieren möchten, oder in 0 , wenn Sie sie deaktivieren möchten.

   ![](assets/audit_trail_6.png)

1. Klicken Sie auf **[!UICONTROL Speichern]** .

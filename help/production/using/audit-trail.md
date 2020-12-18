---
solution: Campaign Classic
product: campaign
title: Audit-Protokoll
description: Audit-Protokoll
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 3%

---


# Audit-Protokoll{#audit-trail}

In Adobe Campaign gibt Ihnen der **[!UICONTROL Prüfpfad]** Zugriff auf den vollständigen Verlauf der in Ihrer Instanz vorgenommenen Änderungen.

**[!UICONTROL Prüfen Sie]** TrailCaptures in Echtzeit auf eine umfassende Liste von Aktionen und Ereignissen, die in Ihrer Adobe Campaign-Instanz auftreten. Es bietet eine Self-Service-Möglichkeit zum Zugriff auf einen Verlauf von Daten, um Antworten zu erhalten, z. B.: was mit Ihrer Workflows passiert ist und wer sie zuletzt aktualisiert hat oder was Ihre Benutzer in der Instanz getan haben.

>[!NOTE]
>
>Adobe Campaign prüft keine Änderungen an Benutzerrechten, Vorlagen, Personalisierungen oder Kampagnen.\
>Prüfpfad kann nur von Administratoren der Instanz verwaltet werden.

Prüfpfad besteht aus drei Komponenten:

* **Schema-Prüfpfad**: Überprüfen Sie die Aktivitäten und zuletzt vorgenommenen Änderungen an Ihren Schemas.

   Weitere Informationen zu Schemas finden Sie auf dieser [Seite](../../configuration/using/data-schemas.md).

* **Workflow-Prüfpfad**: Überprüfen Sie die Aktivitäten und zuletzt vorgenommenen Änderungen Workflows und zusätzlich den Status Ihrer Workflows, z. B.:

   * Starten
   * Aussetzen
   * Anhalten
   * Neu starten
   * Bereinigen was der Aktion Purge History entspricht
   * Simulieren, was dem Beginn Aktion im Modus Simulation entspricht
   * Wakeup, der der Aktion entspricht, Ausstehende Aufgaben jetzt ausführen
   * Unbedingter Stopp

   Weitere Informationen zu Workflows finden Sie auf dieser [Seite](../../workflow/using/about-workflows.md).

   Weitere Informationen zum Überwachen von Workflows finden Sie im Abschnitt [dediziertes ](../../workflow/using/monitoring-workflow-execution.md).

* **Optionsprüfungspfad**: Überprüfen Sie die Aktivitäten und zuletzt vorgenommenen Änderungen an Ihren Optionen.

   Weitere Informationen zu den Optionen finden Sie auf dieser [Seite](../../installation/using/configuring-campaign-options.md).

## Zugriff auf Audit-Protokoll {#accessing-audit-trail}

So greifen Sie auf den **[!UICONTROL Prüfpfad]** Ihrer Instanz zu:

1. Rufen Sie das Menü **[!UICONTROL Explorer]** Ihrer Instanz auf.
1. Wählen Sie im Menü **[!UICONTROL Administration]** **[!UICONTROL Audit]** .

   ![](assets/audit_trail_1.png)

1. Das Fenster **[!UICONTROL Prüfpfad]** wird mit der Liste Ihrer Entitäten geöffnet. Adobe Campaign prüft die Aktionen zum Erstellen, Bearbeiten und Löschen von Workflows, Optionen und Schemas.

   Wählen Sie eine der Entitäten aus, um mehr über die letzten Änderungen zu erfahren.

   ![](assets/audit_trail_2.png)

1. Das Fenster **[!UICONTROL Prüfungsentität]** enthält detailliertere Informationen zu der ausgewählten Entität, z. B.:

   * **[!UICONTROL Typ]** : Arbeitsablauf, Optionen oder Schema.
   * **[!UICONTROL Entität]** : Interner Name Ihrer Aktivitäten.
   * **[!UICONTROL Geändert von]** : Benutzername der letzten Person, die diese Entität zuletzt geändert hat.
   * **[!UICONTROL Aktion]** : Letzte Aktion, die für diese Entität ausgeführt wurde, entweder &quot;Erstellt&quot;, &quot;Bearbeitet&quot;oder &quot;Gelöscht&quot;.
   * **[!UICONTROL Änderungsdatum]** : Datum der letzten Aktion, die für diese Entität durchgeführt wurde.

   Der Codeblock enthält weitere Informationen darüber, was genau in Ihrer Entität geändert wurde.

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>Standardmäßig ist die Aufbewahrungszeit für **[!UICONTROL Prüfprotokolle]** auf 180 Tage eingestellt. Weitere Informationen zum Ändern der Retentionszeit finden Sie auf dieser [Seite](../../production/using/database-cleanup-workflow.md#deployment-wizard).

## Prüfpfad {#enable-disable-audit-trail} aktivieren/deaktivieren

Prüfpfad kann für eine bestimmte Aktivität einfach aktiviert oder deaktiviert werden, wenn Sie z. B. Speicherplatz in der Datenbank speichern möchten.

Gehen Sie dabei folgendermaßen vor:

1. Rufen Sie das Menü **[!UICONTROL Explorer]** Ihrer Instanz auf.
1. Wählen Sie im Menü **[!UICONTROL Administration]** **[!UICONTROL Platform]** und dann **[!UICONTROL Options]** aus.

   ![](assets/audit_trail_4.png)

1. Wählen Sie je nach Entität, die Sie aktivieren/deaktivieren möchten, eine der folgenden Optionen aus:

   * Für Workflow: **[!UICONTROL XtkAudit_Workflows]**
   * Schemas: **[!UICONTROL XtkAudit_DataSchema]**
   * Für Optionen: **[!UICONTROL XtkAudit_Option]**
   * Für jede Entität: **[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. Ändern Sie **[!UICONTROL Wert]** in 1, wenn Sie die Entität aktivieren möchten, oder in 0, wenn Sie sie deaktivieren möchten.

   ![](assets/audit_trail_6.png)

1. Wählen Sie **[!UICONTROL Speichern]** aus .


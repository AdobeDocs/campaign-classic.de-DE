---
product: campaign
title: Erstellen von Marketing-Kampagnen
description: Erfahren Sie, wie Sie Marketing-Kampagnen erstellen und ausführen.
role: User
feature: Campaigns, Cross Channel Orchestration, Programs
hide: true
exl-id: a8fce21f-ffe3-4819-87ca-ac0ad9f21e41
TQID: https://experienceleague.adobe.com/5gH9cUkeJNozk9f14AAn6C3wUTt48329f-OIa4EVV0g
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 1300
ht-degree: 75%

---

# Erste Schritte mit Marketing-Kampagnen{#setting-up-marketing-campaigns}

Kampagnen umfassen Aktionen (Sendungen) und Prozesse (Importieren oder Extrahieren von Dateien) sowie Ressourcen (Marketing-Dokumente, Versandentwürfe). Sie werden in Marketing-Kampagnen verwendet. Kampagnen sind Teil eines Programms und Programme Teil eines Kampagnenplans.

![](assets/do-not-localize/how-to-video.png) [Im Video](#video) erfahren Sie, wie man einen Marketing-Plan, Programme und Kampagnen erstellt.

So erstellen Sie eine Marketing-Kampagne:

1. Erstellung einer Kampagne: Ermittlung von Kampagnen und deren Eigenschaften: Titel, Typ, Anfangs- und Enddatum, Budget, zugehörige Ressourcen, Verantwortliche und Teilnehmer. [Weitere Informationen](#creating-a-campaign).

1. Bestimmung der Zielpopulation(en): Erstellung eines Workflows mit Zielgruppenbestimmungs-Abfragen. [Weitere Informationen](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population).

1. Erstellen von Sendungen: Auswahl von Kanälen und Definition des zu sendenden Inhalts. [Weitere Informationen](../../campaign/using/marketing-campaign-deliveries.md#creating-deliveries).

1. Validieren von Sendungen. [Weitere Informationen](../../campaign/using/marketing-campaign-approval.md).

1. Überwachen von Sendungen. [Weitere Informationen](../../campaign/using/marketing-campaign-monitoring.md).

1. Planen von Kampagnen und der damit verbundenen Kosten. [Weitere Informationen](../../campaign/using/providers-stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).

Nach Abschluss dieser Schritte können Sie den Versand starten (siehe [diesen Abschnitt](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)), die Daten, Prozesse und Informationen zu den Sendungen überprüfen und bei Bedarf die zugehörigen Dokumente verwalten (siehe [diesen Abschnitt](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents)). Außerdem können Sie die Ausführung der Verarbeitungsphasen von Kampagnen und Sendungen verfolgen (siehe [diesen Abschnitt](../../campaign/using/marketing-campaign-monitoring.md)).

## Erstellung einer Plan- und Programmhierarchie {#creating-plan-and-program-hierarchy}

Um Ihre Ordnerhierarchie für Marketing-Pläne und -Programme zu konfigurieren, gehen Sie folgendermaßen vor:

1. Klicken Sie auf das **Explorer-** Symbol auf der Startseite.
1. Klicken Sie mit der rechten Maustaste auf den Ordner, in dem Sie Ihren Plan erstellen möchten.
1. Wählen Sie **Ordner hinzufügen > Kampagnenverwaltung > Plan** aus.

   ![](assets/create_plan_1.png)

1. Benennen Sie den Plan.
1. Klicken Sie mit der rechten Maustaste auf den neu erstellen Plan und wählen Sie **Eigenschaften...**.

   ![](assets/create_plan_2.png)

1. Passen Sie im Tab **Allgemein** die Option **Interner Name** an, um bei Package-Exporten Duplikate zu vermeiden.
1. Klicken Sie auf **Speichern**.
1. Klicken Sie mit der rechten Maustaste auf den neu erstellen Plan und wählen Sie **Programm-Ordner hinzufügen**.
1. Wiederholen Sie die obigen Schritte, um Ihren neuen Programmordner und seinen internen Namen umzubenennen.

## Erstellen einer Kampagne {#creating-a-campaign}

### Hinzufügen einer Kampagne {#adding-a-campaign}

Sie können eine Kampagne über die Kampagnenliste erstellen. Klicken Sie auf den Link **[!UICONTROL Kampagnen]** in der gleichnamigen Dashbord-Rubrik, um zu dieser Übersicht zu gelangen.**&#x200B;**

![](assets/s_ncs_user_add_an_op_from_list.png)

Im Feld **[!UICONTROL Programm]** können Sie das Programm auswählen, dem die Kampagne zugeordnet werden soll. Diese Informationen sind obligatorisch.

![](assets/s_ncs_user_new_op_wz_a.png)

Kampagnen können auch von einem Programm aus erstellt werden. Klicken Sie hierzu auf die Schaltfläche **[!UICONTROL Hinzufügen]** im Tab **[!UICONTROL Planung]** des jeweiligen Programms.

![](assets/s_ncs_user_add_an_op.png)

Wenn Sie eine Kampagne über die Registerkarte **[!UICONTROL Planung]** eines Programms erstellen, wird die Kampagne dem jeweiligen Programm automatisch hinzugefügt. Das Feld **[!UICONTROL Programm]** wird in diesem Fall ausgeblendet.

Wählen Sie im Fenster zur Kampagnenerstellung die Kampagnenvorlage aus und fügen Sie einen Namen und eine Beschreibung der Kampagne hinzu. Sie können auch das Anfangs- und Enddatum der Kampagne angeben.

Klicken Sie auf **[!UICONTROL OK]**, um die Kampagne zu erstellen. Sie wird daraufhin der Programmplanung hinzugefügt.

![](assets/s_ncs_user_program_planning_with_op.png)

>[!NOTE]
>
>Um nur bestimmte Kampagnen anzuzeigen, klicken Sie auf **[!UICONTROL Filtern]** und wählen Sie den Status der gesuchten Kampagnen aus.

![](assets/s_ncs_user_program_planning_filter.png)

### Bearbeiten und Konfigurieren einer Kampagne {#editing-and-configuring-a-campaign}

Sie können anschließend die gerade erstellte Kampagne bearbeiten und ihre Parameter festlegen.

Wählen Sie sie hierzu im Kalender aus und klicken Sie auf den Link **[!UICONTROL Öffnen]**.

![](assets/s_ncs_user_new_op_edit.png)

Das Dashboard der Kampagne wird angezeigt.

## Wiederkehrende und periodische Kampagnen {#recurring-and-periodic-campaigns}

Eine wiederkehrende Kampagne ist eine auf einer bestimmten Vorlage basierende Kampagne, deren Workflows so konfiguriert sind, dass sie entsprechend einem verknüpften Zeitplan ausgeführt werden. Die Workflows werden daher innerhalb einer Kampagne wiederkehrend. Die Zielgruppenbestimmung wird bei jeder Ausführung dupliziert, und die verschiedenen Prozesse und Zielpopulationen werden verfolgt. Es ist auch möglich, zukünftige Zielgruppen im Voraus auszuführen, und zwar über den Erfassungszeitraum während der automatischen Workflow-Erstellung, um Simulationen mit Zielschätzungen zu starten.

Eine periodische Kampagne erstellt sich automatisch entsprechend der Ausführungsplanung ihrer Vorlage.

### Erstellen einer wiederkehrenden Kampagne {#creating-a-recurring-campaign}

Wiederkehrende Kampagnen werden anhand einer bestimmten Vorlage erstellt, die die auszuführende Workflow-Vorlage und die Ausführungsplanung definiert.

#### Erstellen einer Vorlage für wiederkehrende Kampagnen {#creating-the-campaign-template}

1. Wählen Sie den Kampagnentyp **[!UICONTROL Wiederkehrend]**.

   >[!NOTE]
   >
   >Es empfiehlt sich, die Standardvorlage zu duplizieren, statt eine leere Vorlage zu erstellen.

   ![](assets/s_ncs_user_op_template_recur_tab.png)

1. Geben Sie den Titel der Vorlage sowie die Dauer der Kampagne an.

   ![](assets/s_ncs_user_op_template_recur_duplicate.png)

1. Legen Sie im für diesen Kampagnentyp vorgesehenen Tab **[!UICONTROL Planung]** die Zeitpunkte der wiederholten Ausführungen fest.

Geben Sie in diesem Tab die geplanten Ausführungsdaten der Kampagnen auf der Basis dieser Vorlage an.

![](assets/s_ncs_user_op_template_recur_planning.png)

Der Konfigurationsmodus der Ausführungsplanung entspricht dem Objekt **[!UICONTROL Planung]** des Workflows. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../workflow/using/architecture.md).

>[!IMPORTANT]
>
>Die Konfiguration der Ausführungsplanung muss sorgfältig durchgeführt werden, um eine Überlastung der Datenbank zu vermeiden. Wiederkehrende Kampagnen duplizieren die Workflows ihrer Vorlage je nach angegebenem Zeitplan. Die Implementierung übermäßig häufiger Workflow-Erstellung kann den Betrieb der Datenbank behindern.

1. Geben Sie u. U. einen Wert im Feld **[!UICONTROL Im Voraus erstellen für]** an, um die entsprechenden Workflows für den angegebenen Zeitraum zu erstellen.
1. Erstellen Sie schließlich die Workflow-Vorlage, die in den auf dieser Kampagnenvorlage basierenden Kampagnen verwendet werden soll, mit den Parametern der Zielgruppenbestimmung sowie einer oder mehreren generischen Sendungen.

   >[!NOTE]
   >
   >Dieser Workflow muss als Vorlage für einen wiederkehrenden Workflow gespeichert werden. Öffnen Sie hierzu die Eigenschaften des Workflows und wählen Sie die Option **[!UICONTROL Vorlage für einen wiederkehrenden Workflow]** im Tab **[!UICONTROL Ausführung]** aus.

   ![](assets/s_ncs_user_op_template_recur_wf_option.png)

#### Erstellen einer wiederkehrenden Kampagne {#create-the-recurring-campaign}

Um eine wiederkehrende Kampagne zu erstellen und ihre Workflows der festgelegten Planung entsprechend auszuführen, gehen Sie wie folgt vor:

1. Erstellen Sie eine neue Kampagne basierend auf der zuvor erstellten Vorlage einer wiederkehrenden Kampagne.
1. Geben Sie die Ausführungsplanung der Workflows ein, falls diese nicht in der Vorlage definiert wurde.

   ![](assets/s_ncs_user_op_recur_planning.png)

1. Die Kampagnenplanung ermöglicht es, jeweils ein Datum anzugeben, an dem der Workflow automatisch erstellt oder gestartet wird.

   Für jede Zeile können die folgenden ergänzenden Optionen hinzugefügt werden:

   * **[!UICONTROL Zu validieren]**: forciert den Versand der Validierungsanfragen für die im Workflow vorgesehenen Sendungen;
   * **[!UICONTROL Zu starten]**: startet den Workflow automatisch bei Erreichen des geplanten Startdatums.

   Das Feld **[!UICONTROL Im Voraus erstellen für]** ermöglicht es, alle Workflows für den angegebenen Zeitraum zu erstellen.

   Bei der Ausführung des Workflows **[!UICONTROL Vorgänge bei Kampagnen]** werden die dedizierten Workflows auf der Grundlage der im Kampagnenkalender definierten Vorfälle erstellt. Somit wird für jedes Ausführungsdatum ein Workflow erstellt.

1. Wiederkehrende Workflows werden automatisch über die Workflow-Vorlage in der Kampagne erstellt. Sie werden im Tab **[!UICONTROL Zielbestimmungen und Workflows]** der Kampagne angezeigt.

   ![](assets/s_ncs_user_op_recur_planning_wfs.png)

   Der Titel der Instanz eines wiederkehrenden Workflows setzt sich aus dem Titel seiner Vorlage sowie der Workflow-Nummer zusammen, getrennt durch eine Raute.

   Die basierend auf der Planung erstellten Workflows werden dieser automatisch in der Spalte **[!UICONTROL Workflow]** des Tabs **[!UICONTROL Planung]** zugeordnet.

   ![](assets/s_ncs_user_op_recur_planning_wfs_1.png)

   Jeder Workflow kann von diesem Tab aus bearbeitet werden.

   ![](assets/s_ncs_user_op_recur_planning_wf_edit.png)

   >[!NOTE]
   >
   >Das Startdatum der dem Workflow zugeordneten Planungszeile ist über eine Variable des Workflows mit der folgenden Syntax verfügbar:\
   >`$date(instance/vars/@startPlanningDate)`

### Erstellen einer periodischen Kampagne {#creating-a-periodic-campaign}

Eine periodische Kampagne ist eine auf einer bestimmten Vorlage basierende Kampagne, mit der Sie Kampagneninstanzen auf der Grundlage einer Ausführungsplanung erstellen können. Kampagneninstanzen werden automatisch auf der Grundlage einer Vorlage für periodische Kampagnen und abhängig von der in der Vorlagenplanung definierten Häufigkeit erstellt.

#### Erstellen der Kampagnenvorlage {#creating-the-campaign-template-1}

1. Wählen Sie den Kampagnentyp **[!UICONTROL Periodisch]**

   ![](assets/s_ncs_user_op_template_period_create.png)

1. Konfigurieren Sie die Vorlage.

   >[!NOTE]
   >
   >Der der Vorlage zugeordnete Benutzer muss über die notwendigen Berechtigungen zur Erstellung von Kampagnen im ausgewählten Programm verfügen.

1. Erstellen Sie den mit dieser Vorlage verknüpften Workflow. Sie wird in jeder periodischen Kampagne dupliziert, die von der Vorlage erstellt wird.

   ![](assets/s_ncs_user_op_template_period_wf.png)

   >[!NOTE]
   >
   >Dieser Workflow ist eine Workflow-Vorlage. Sie kann nicht über die Kampagnenvorlage ausgeführt werden.

1. Gehen Sie zur Eingabe der Ausführungsplanung wie in der Vorlage für wiederkehrende Kampagnen vor: Klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]** und bestimmen Sie Start- und Enddatum oder ergänzen Sie die Ausführungsplanung über den entsprechenden Link.

   ![](assets/s_ncs_user_op_template_period_planning_add.png)

   >[!IMPORTANT]
   >
   >Vorlagen für periodische Kampagnen erstellen neue Kampagnen gemäß dem oben definierten Zeitplan. Sie muss daher sorgfältig ausgefüllt werden, um eine Überlastung der Adobe Campaign-Datenbank zu vermeiden.

1. Nach Erreichen des Ausführungsstartdatums wird automatisch die passende Kampagne erstellt. Es übernimmt alle Eigenschaften seiner Vorlage.

   Jede Kampagne kann über die Ausführungsplanung in der Vorlage bearbeitet werden.

   ![](assets/s_ncs_user_op_template_period_planning.png)

Jede periodische Kampagne enthält dieselben Elemente. Nach der Erstellung wird sie als Standardkampagne verwaltet.

## Anleitungsvideo {#video}

In diesem Video wird erklärt, wie man einen Marketing-Plan, Programme und Kampagnen erstellt.

>[!VIDEO](https://video.tv.adobe.com/v/326556?captions=ger&quality=12)

Weitere Anleitungsvideos zu Campaign finden Sie [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=de).

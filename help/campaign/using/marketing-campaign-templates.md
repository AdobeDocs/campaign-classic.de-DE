---
title: Marketing-Kampagnenvorlagen
seo-title: Marketing-Kampagnenvorlagen
description: Marketing-Kampagnenvorlagen
seo-description: Marketing-Kampagnenvorlagen
page-status-flag: never-activated
uuid: 842b501f-7d65-4450-b7ab-aff3942fb96f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
discoiquuid: 8d076211-10a6-4a98-b0d2-29dad154158c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# Marketing-Kampagnenvorlagen {#campaign-templates}

Kampagnenvorlagen werden im **[!UICONTROL Resources > Templates > Campaign templates]** Knoten zentralisiert. Eine Standardvorlage wird als Standard bereitgestellt. Damit können Sie eine neue Kampagne mit allen verfügbaren Modulen (Dokumente, Aufgaben, Saatgutadressen usw.) erstellen, aber die angebotenen Module hängen von Ihren Rechten und der Konfiguration Ihrer Adobe Campaign-Plattform ab.

## Erstellung oder Duplizierung einer Kampagnenvorlage {#creating-or-duplicating-a-campaign-template}

Gehen Sie zur Erstellung einer neuen Vorlage wie folgt vor:

1. Öffnen Sie den Campaign-**Explorer**.
1. Klicken Sie in **Ressourcen > Vorlagen> Kampagnenvorlagen** auf die Option **Neu** in der Symbolleiste über der Liste mit Vorlagen.

   ![](assets/create_campaign_template_1.png)

1. Geben Sie den Titel der neuen Kampagnenvorlage ein.
1. Klicken Sie auf **Speichern** und öffnen Sie die Vorlage erneut.
1. Füllen Sie bei Bedarf im **Bearbeiten**-Tab das Feld **Interner Name** aus und und ergänzen Sie andere erforderliche Angaben.
1. Wählen Sie **Erweiterte Kampagnenparameter**, um Ihrer Kampagnenvorlage einen Workflow hinzuzufügen.

   ![](assets/create_campaign_template_2.png)

1. Ändern Sie den Wert für **Zielbestimmungen und Workflows** auf **Ja**.

   ![](assets/create_campaign_template_3.png)

1. Klicken Sie im Tab **Zielbestimmungen und Workflows** auf die Option **Workflow hinzufügen...**.

   ![](assets/create_campaign_template_4.png)

1. Füllen Sie das Feld **Titel** aus und klicken Sie auf **Ok**.
1. Erstellen Sie Ihren Workflow entsprechend Ihren Anforderungen.
1. Klicken Sie auf **Speicher** n. Ihre Vorlage kann jetzt in einer Kampagne verwendet werden.

Es besteht auch die Möglichkeit, die Standardvorlage zu duplizieren und die bestehende Konfiguration zu verwenden und anzupassen.

The various tabs and sub-tabs of the campaign template allow you to access its settings, described in [General configuration](#general-configuration).

![](assets/s_ncs_user_new_op_template_duplicate.png)

## Konfigurieren einer Kampagnenvorlage {#configuring-a-campaign-template}

Kampagnen basieren auf Modellen, die einen Satz vordefinierter Parameter gemeinsam haben.

In a default configuration, the campaign templates are centralized in the **[!UICONTROL Resources > Templates > Campaign templates]** node of the Adobe Campaign tree.

![](assets/s_ncs_user_campaign_op_template_node.png)

>[!NOTE]
>
>Um den Navigationsbaum anzuzeigen, klicken Sie auf das Symbol **[!UICONTROL Explorer]** oberhalb der Startseite.

Es wird eine vordefinierte Vorlage bereitgestellt, um eine Kampagne zu erstellen, für die keine bestimmte Konfiguration definiert wurde. Sie können Ihre Kampagnenvorlagen erstellen und konfigurieren und dann Kampagnen aus diesen Vorlagen erstellen.

The creation and configuration of campaign templates are presented in [Campaign templates](#campaign-templates).

Mehr zur Erstellung von Kampagnen erfahren Sie im Video [Creating a campaign and an email](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html).

## Konfiguration der verfügbaren Module {#configuration-of-the-available-modules}

### Modulauswahl {#module-selection}

Über den **[!UICONTROL Advanced campaign settings...]** Link können Sie auf der Grundlage dieser Vorlage Aufträge für die Kampagnen aktivieren und deaktivieren. Wählen Sie die Funktionen aus, die Sie in den auf der Grundlage dieser Vorlage erstellten Kampagnen aktivieren möchten.

![](assets/s_ncs_user_op_template_tab1.3.png)

Wenn keine Funktion ausgewählt ist, werden die Elemente, die den Prozess betreffen (Menüs, Symbole, Optionen, Registerkarten, Unterregisterkarten usw.) nicht in der Oberfläche der Vorlage oder in Kampagnen angezeigt, die auf dieser Vorlage basieren. Die Registerkarten links neben den Kampagnendetails stimmen in der Regel mit den in der Vorlage ausgewählten Prozessen überein. Wenn beispielsweise **Ausgaben und Ziele** nicht ausgewählt sind, wird die entsprechende **[!UICONTROL Budget]** Registerkarte nicht in Kampagnen angezeigt, die auf dieser Vorlage basieren.

Im Dashboard der Kampagne werden zudem Verknüpfungen zu den Konfigurationsfenstern hinzugefügt: Wenn eine Funktionalität aktiviert ist, besteht über einen Link im Dashboard direkter Zugriff auf diese.

Beispielsweise werden mit dieser Konfiguration:

![](assets/s_ncs_user_op_template_tab1.4.png)

The following links are displayed in the campaign dashboard (the **[!UICONTROL Add a task]** link is missing):

![](assets/s_ncs_user_op_template_tab1.3ex.png)

Es werden nur die folgenden Registerkarten angezeigt:

![](assets/s_ncs_user_op_template_tab1.4ex.png)

Mit folgender Konfiguration dagegen:

![](assets/s_ncs_user_op_template_tab2.2ex.png)

werden diese Links und Tabs angezeigt:

![](assets/s_ncs_user_op_template_tab2.3ex.png)

### Typologie der aktivierten Module {#typology-of-enabled-modules}

* **Kontrollgruppe**

   Wenn dieses Modul ausgewählt wird, wird ein zusätzlicher Tab in den erweiterten Parametern der Vorlage und der auf dieser Vorlage basierenden Kampagnen hinzugefügt. Die Konfiguration kann in der Vorlage oder direkt in den einzelnen Kampagnen erfolgen.

   ![](assets/s_ncs_user_op_template_activate_1.png)

* **Testadressen**

   Wenn dieses Modul ausgewählt wird, wird ein zusätzlicher Tab in den erweiterten Parametern der Vorlage und der auf dieser Vorlage basierenden Kampagnen hinzugefügt. Die Konfiguration kann in der Vorlage oder direkt in den einzelnen Kampagnen erfolgen.

   ![](assets/s_ncs_user_op_template_activate_2.png)

* **Dokumente**

   Wenn dieses Modul ausgewählt ist, wird der Registerkarte der Vorlage und den auf dieser Vorlage basierenden Kampagnen eine zusätzliche Registerkarte hinzugefügt. **[!UICONTROL Edition]** Angehängte Dokumente können aus der Vorlage oder einzeln für jede Kampagne hinzugefügt werden.

   ![](assets/s_ncs_user_op_template_activate_3.png)

* **Versandentwurf**

   When this module is selected, a **[!UICONTROL Delivery outlines]** sub-tab is added to the **[!UICONTROL Documents]** tab in order to define delivery outlines for the campaign.

   ![](assets/s_ncs_user_op_template_activate_4.png)

* **Zielbestimmungen und Workflows**

   Wenn Sie das **[!UICONTROL Targeting and workflows]** Modul auswählen, wird eine Registerkarte hinzugefügt, mit der Sie einen oder mehrere Arbeitsabläufe für Kampagnen erstellen können, die auf dieser Vorlage basieren. Workflows können auch einzeln für jede Kampagne auf der Grundlage dieser Vorlage konfiguriert werden.

   ![](assets/s_ncs_user_op_template_activate_5.png)

   Darüber hinaus wird mit Aktivierung dieses Moduls in den erweiterten Parametern der Kampagne ein zusätzlicher Tab hinzugefügt, in dem die Ausführungsprioritäten der Prozesse bestimmt werden können.

   ![](assets/s_ncs_user_op_template_activate_5a.png)

* **Validierung**

   If you select the **[!UICONTROL Approval]**, you can select the processes to approve as well as the operators in charge of approvals.

   ![](assets/s_ncs_user_op_template_activate_5b.png)

* **Ausgaben und Budget**

   Wenn dieses Modul ausgewählt wird, wird der Tab **[!UICONTROL Budget]** den Details der Vorlage und der auf dieser Vorlage basierenden Kampagnen hinzugefügt, um das übergeordnete Budget auszuwählen.

   ![](assets/s_ncs_user_op_template_activate_7.png)

### Vorgangsvalidierungen {#approval-of-jobs}

Sie können wählen, ob die Prozessgenehmigung aktiviert werden soll oder nicht, indem Sie auf der **[!UICONTROL Approvals]** Registerkarte des Bereichs &quot;Erweiterte Einstellungen&quot;der Vorlagen klicken. Die Aufträge, für die eine Genehmigung ausgewählt wurde, müssen genehmigt werden, damit die Nachrichtenübermittlung genehmigt werden kann.

Jeder aktivierten Validierung muss ein validierender Benutzer oder eine validierende Benutzergruppe zugewiesen werden.

## Allgemeine Konfiguration {#general-configuration}

### Vorlageneigenschaften {#template-properties}

![](assets/s_ncs_user_op_new_template.png)

Bei der Erstellung einer Kampagnenvorlage ist die Angabe folgender Informationen notwendig:

* **Titel** der Vorlage: Dieser Titel wird allen auf dieser Vorlage basierenden Kampagnen automatisch zugewiesen.
* Wählen Sie die **Kampagnenart** aus der Dropdownliste. Die in dieser Liste verfügbaren Werte sind die in der **[!UICONTROL natureOp]** Aufzählung gespeicherten Werte.

   >[!NOTE]
   >
   >Weitere Informationen zu Auflistungen finden Sie im Abschnitt [Erste Schritte](../../platform/using/managing-enumerations.md).

* Wählen Sie den **Kampagnentyp** aus: eindeutig, wiederkehrend oder regelmäßig. Standardmäßig gelten die Kampagnenvorlagen für eindeutige Kampagnen. Wiederkehrende und periodische Kampagnen finden Sie hier: [Wiederholte und periodische Kampagnen](../../campaign/using/setting-up-marketing-campaigns.md#recurring-and-periodic-campaigns).
* Dauer der Kampagne an: Gemeint ist der Zeitraum, über den sich die Kampagne erstrecken wird. Bei Erstellung einer auf einer Vorlage basierenden Kampagne werden Beginn und Ende somit automatisch ausgefüllt.

   Handelt es sich um eine wiederkehrende Kampagne, müssen Beginn und Ende direkt in der Vorlage angegeben werden.

* **Zugehörigkeitsprogramm** der Vorlage: Die auf der Vorlage basierenden Kampagnen werden dem ausgewählten Programm zugeordnet.

### Ausführungsparameter der Vorlage {#template-execution-parameters}

Über den **[!UICONTROL Advanced campaign settings...]** Link können Sie die erweiterten Optionen der Vorlage für die Verarbeitung des Bereitstellungsziels (Kontrollgruppe, Startadressen usw.) konfigurieren. und die Konfiguration der Kampagnenmessung und Workflow-Ausführung.

![](assets/s_ncs_user_op_template_tab1.2.png)

## Kampagnen-Vorausplanung {#campaign-reverse-scheduling}

Sie können die Umkehrung der Planung einer Kampagne ausführen, um beispielsweise ein Event vorzubereiten, dessen Datum im Voraus bekannt ist. In den Kampagnenvorlagen besteht die Möglichkeit, das Beginndatum einer Aufgabe abhängig vom Enddatum einer Kampagne zu berechnen.

Wechseln Sie im Feld Aufgabenkonfiguration zum **[!UICONTROL Implementation schedule]** Bereich und markieren Sie das **[!UICONTROL The start date is calculated based on the campaign end date]** Kontrollkästchen. (Hier ist &quot;Startdatum&quot;das Startdatum der Aufgabe). Wechseln Sie zum **[!UICONTROL Start]** Feld und geben Sie ein Intervall ein: Die Aufgabe beginnt so lange vor dem Enddatum der Kampagne. Wenn Sie einen Zeitraum eingeben, der länger ist als der Zeitraum, für den die Kampagne auf &quot;last&quot;festgelegt ist, beginnt die Aufgabe vor der Kampagne.

![](assets/mrm_task_in_template_start_date.png)

Wenn Sie eine Kampagne mit dieser Vorlage erstellen, wird der Beginn der Aufgabe automatisch berechnet. Sie haben jedoch die Möglichkeit, das Datum zu verändern.

---
product: campaign
title: Marketing-Kampagnenvorlagen
description: Marketing-Kampagnenvorlagen
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Campaigns, Templates
exl-id: d272d4b9-f1b2-4fb2-9ed9-91a4aea7eca3
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: ht
source-wordcount: '1168'
ht-degree: 100%

---

# Erstellen und Konfigurieren von Kampagnenvorlagen {#campaign-templates}

Alle Marketing-Kampagnen basieren auf einer Vorlage, in der die Hauptmerkmale und -funktionen gespeichert sind. Kampagnenvorlagen werden im Knoten **[!UICONTROL Ressourcen > Vorlagen > Kampagnenvorlagen]** gespeichert. Hierbei handelt es sich um Standardvorlagen. Sie ermöglichen die Erstellung einer neuen Kampagne unter Verwendung aller verfügbarer Module (Dokumente, Aufgaben, Testadressen usw.). Die vorgeschlagenen Module hängen von Ihren Berechtigungen und der Konfiguration Ihrer Adobe Campaign-Plattform ab.

![](assets/s_ncs_user_campaign_op_template_node.png)

>[!NOTE]
>
>Um den Navigationsbaum anzuzeigen, klicken Sie auf das Symbol **[!UICONTROL Explorer]** auf der Startseite.

Es wird eine native Vorlage bereitgestellt, mit der Sie eine Kampagne erstellen können, für die keine bestimmte Konfiguration definiert wurde. Sie können Ihre Kampagnenvorlagen erstellen und konfigurieren und dann Kampagnen aus diesen Vorlagen erstellen.

![](assets/do-not-localize/how-to-video.png) Weitere Informationen zur Erstellung von Kampagnen finden Sie in [diesem Video](../../campaign/using/marketing-campaign-deliveries.md#create-email-video).

## Erstellen einer Kampagnenvorlage {#creating-or-duplicating-a-campaign-template}

Gehen Sie wie folgt vor, um eine Kampagnenvorlage zu erstellen:

1. Öffnen Sie den Campaign-**Explorer**.
1. Klicken Sie in **Ressourcen > Vorlagen> Kampagnenvorlagen** auf die Option **Neu** in der Symbolleiste über der Liste mit Vorlagen.

   ![](assets/create_campaign_template_1.png)

1. Geben Sie den Titel der neuen Kampagnenvorlage ein.
1. Klicken Sie auf **Speichern** und öffnen Sie die Vorlage erneut.
1. Füllen Sie bei Bedarf im **Bearbeiten**-Tab das Feld **Interner Name** aus und ergänzen Sie andere erforderliche Angaben.
1. Wählen Sie **Erweiterte Kampagnenparameter**, um Ihrer Kampagnenvorlage einen Workflow hinzuzufügen.

   ![](assets/create_campaign_template_2.png)

1. Ändern Sie den Wert für **Zielbestimmungen und Workflows** auf **Ja**.

   ![](assets/create_campaign_template_3.png)

1. Klicken Sie im Tab **Zielbestimmungen und Workflows** auf die Option **Workflow hinzufügen...**.

   ![](assets/create_campaign_template_4.png)

1. Füllen Sie das Feld **Titel** aus und klicken Sie auf **Ok**.
1. Erstellen Sie Ihren Workflow entsprechend Ihren Anforderungen.
1. Klicken Sie auf **Speicher** n. Ihre Vorlage kann jetzt in einer Kampagne verwendet werden.

Es besteht auch die Möglichkeit, die Standardvorlage zu **duplizieren** und ihre Konfiguration zu verwenden und anzupassen.

Die unterschiedlichen Registerkarten und Unterregisterkarten der Kampagnenvorlage ermöglichen den Zugriff auf die Einstellungen. Sie werden im Abschnitt [Allgemeine Konfiguration](#general-configuration) beschrieben.

![](assets/s_ncs_user_new_op_template_duplicate.png)

## Auswählen von Modulen {#select-modules}

Über den Link **[!UICONTROL Erweiterte Kampagnenparameter...]** können Sie Vorgänge für die auf dieser Vorlage basierenden Kampagnen aktivieren und deaktivieren. Wählen Sie die Funktionen aus, die Sie in den über diese Vorlage erstellten Kampagnen aktivieren möchten.

![](assets/s_ncs_user_op_template_tab1.3.png)

Wenn eine Funktion nicht ausgewählt ist, werden die den Prozess betreffenden Elemente (Menüs, Symbole, Optionen, Tabs, Unter-Tabs usw.) nicht auf der Benutzeroberfläche der Vorlage oder in den auf dieser Vorlage basierenden Kampagnen angezeigt. Die Tabs links von den Kampagnendetails entsprechen in der Regel den in der Vorlage ausgewählten Prozessen. Wenn beispielsweise **Ausgaben und Budget** nicht ausgewählt ist, wird der entsprechende Tab **[!UICONTROL Budget]** nicht in Kampagnen angezeigt, die auf dieser Vorlage basieren.

Im Dashboard der Kampagne werden zudem Verknüpfungen zu den Konfigurationsfenstern hinzugefügt: Wenn eine Funktionalität aktiviert ist, besteht über einen Link im Dashboard direkter Zugriff auf diese.

Beispielsweise werden mit dieser Konfiguration:

![](assets/s_ncs_user_op_template_tab1.4.png)

foglende Links im Dashboard der Kampagne angeboten (der Link **[!UICONTROL Aufgabe hinzufügen]** fehlt):

![](assets/s_ncs_user_op_template_tab1.3ex.png)

Und nur die folgenden Tabs werden angezeigt:

![](assets/s_ncs_user_op_template_tab1.4ex.png)

Mit folgender Konfiguration dagegen:

![](assets/s_ncs_user_op_template_tab2.2ex.png)

werden diese Links und Tabs angezeigt:

![](assets/s_ncs_user_op_template_tab2.3ex.png)

## Typologie von Modulen {#typology-of-enabled-modules}

* **Kontrollgruppe**

   Wenn dieses Modul ausgewählt wird, wird ein zusätzlicher Tab in den erweiterten Parametern der Vorlage und der auf dieser Vorlage basierenden Kampagnen hinzugefügt. Die Konfiguration kann in der Vorlage oder direkt in den einzelnen Kampagnen erfolgen. Weitere Informationen zu Kontrollgruppen finden Sie in [diesem Abschnitt](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

   ![](assets/s_ncs_user_op_template_activate_1.png)

* **Testadressen**

   Wenn dieses Modul ausgewählt wird, wird ein zusätzlicher Tab in den erweiterten Parametern der Vorlage und der auf dieser Vorlage basierenden Kampagnen hinzugefügt. Die Konfiguration kann in der Vorlage oder direkt in den einzelnen Kampagnen erfolgen. Weitere Informationen zu Testadressen finden Sie in [diesem Abschnitt](../../delivery/using/about-seed-addresses.md).

   ![](assets/s_ncs_user_op_template_activate_2.png)

* **Dokumente**

   Wenn dieses Modul ausgewählt wird, wird ein zusätzlicher Tab im Tab **[!UICONTROL Bearbeiten]** der Vorlage und der auf dieser Vorlage basierenden Kampagnen hinzugefügt. Angehängte Dokumente können über die Vorlage oder direkt in den einzelnen Kampagnen hinzugefügt werden. Weitere Informationen zu Dokumenten finden Sie in [diesem Abschnitt](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents).

   ![](assets/s_ncs_user_op_template_activate_3.png)

* **Versandentwurf**

   Wenn dieses Modul ausgewählt wird, wird dem Tab **[!UICONTROL Dokumente]** der Unter-Tab **[!UICONTROL Versandentwürfe]** hinzugefügt, um für die Kampagne unterschiedliche Versandentwürfe zu erstellen. Weitere Informationen zu Versandentwürfen finden Sie in [diesem Abschnitt](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

   ![](assets/s_ncs_user_op_template_activate_4.png)

* **Zielgruppenbestimmungen und Workflows**

   Wenn das Modul **[!UICONTROL Zielgruppenbestimmungen und Workflows]** ausgewählt wird, wird ein Tab zum Erstellen eines oder mehrerer Workflows für Kampagnen hinzugefügt, die auf dieser Vorlage basieren. Workflows können auch auf Basis dieser Vorlage einzeln für jede Kampagne konfiguriert werden. Weitere Informationen zu Kampagnen-Workflows finden Sie in [diesem Abschnitt](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow).

   ![](assets/s_ncs_user_op_template_activate_5.png)

   Darüber hinaus wird mit Aktivierung dieses Moduls in den erweiterten Parametern der Kampagne ein zusätzlicher Tab hinzugefügt, in dem die Ausführungsprioritäten der Prozesse bestimmt werden können.

   ![](assets/s_ncs_user_op_template_activate_5a.png)

* **Validierung**

   Wenn das Modul **[!UICONTROL Validierung]** ausgewählt wird, können Sie zu validierende Prozesse sowie validierungsverantwortliche Benutzer bestimmen. Weitere Informationen zu Validierungen finden Sie in [diesem Abschnitt](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers).

   ![](assets/s_ncs_user_op_template_activate_5b.png)

   Im Tab **[!UICONTROL Validierungen]** der erweiterten Parameter der Vorlage können Sie auswählen, ob Sie die Validierung von Prozessen aktivieren möchten oder nicht. Die Prozesse, die zur Validierung ausgewählt wurden, müssen zwingend validiert werden, damit ein Nachrichtenversand möglich ist.

   Jeder aktivierten Validierung muss ein validierender Benutzer oder eine validierende Benutzergruppe zugewiesen werden.

* **Ausgaben und Budget**

   Wenn dieses Modul ausgewählt wird, wird der Tab **[!UICONTROL Budget]** den Details der Vorlage und der auf dieser Vorlage basierenden Kampagnen hinzugefügt, damit das zugehörige Budget ausgewählt werden kann.

   ![](assets/s_ncs_user_op_template_activate_7.png)

## Eigenschaften und Ausführung {#general-configuration}

### Vorlageneigenschaften {#template-properties}

![](assets/s_ncs_user_op_new_template.png)

Bei der Erstellung einer Kampagnenvorlage ist die Angabe folgender Informationen notwendig:

* **Titel** der Vorlage: Dieser Titel wird allen auf dieser Vorlage basierenden Kampagnen automatisch zugewiesen.
* **Kampagnenart**: Die in der Dropdown-Liste angebotenen Werte entsprechen den in der Auflistung **[!UICONTROL natureOp]** gespeicherten Werten.

   >[!NOTE]
   >
   >Weitere Informationen zu Auflistungen finden Sie im Abschnitt [Erste Schritte](../../platform/using/managing-enumerations.md).

* Wählen Sie den **Kampagnentyp**: einmalig, wiederkehrend oder periodisch. Standardmäßig sind in Kampagnenvorlagen einmalige Kampagnen festgelegt. Wiederkehrende und periodische Kampagnen werden in [diesem Abschnitt](../../campaign/using/setting-up-marketing-campaigns.md#recurring-and-periodic-campaigns) beschrieben.
* Dauer der Kampagne an: Gemeint ist der Zeitraum, über den sich die Kampagne erstrecken wird. Bei Erstellung einer auf einer Vorlage basierenden Kampagne werden Beginn und Ende somit automatisch ausgefüllt.

   Handelt es sich um eine wiederkehrende Kampagne, müssen Beginn und Ende direkt in der Vorlage angegeben werden.

* **Zugehörigkeitsprogramm** der Vorlage: Die auf der Vorlage basierenden Kampagnen werden dem ausgewählten Programm zugeordnet.

### Ausführungsparameter der Vorlage {#template-execution-parameters}

Über den Link **[!UICONTROL Erweiterte Kampagnenparameter]** können weitere Optionen der Vorlage bezüglich Zielgruppen-Verarbeitung (Kontrollgruppe, Testadressen usw.) sowie Kampagnenmessung und Workflow-Ausführung konfiguriert werden.

![](assets/s_ncs_user_op_template_tab1.2.png)

## Tracken der Kampagnenausführung{#campaign-reverse-scheduling}

Sie können einen Zeitplan für eine Kampagne erstellen und Ergebnisse tracken, um beispielsweise ein gewisses Ereignis für ein bestimmtes Datum zu planen. Mit Kampagnenvorlagen können Sie jetzt das Anfangsdatum einer Aufgabe anhand des Enddatums einer Kampagne berechnen.

Aktivieren Sie hierzu im Konfigurationsfenster der Aufgabe im Abschnitt **[!UICONTROL Erfüllungsplanung]** die Option **[!UICONTROL Das Startdatum wird vom Enddatum der Kampagne aus berechnet]** (&quot;Startdatum&quot; meint hier den Zeitpunkt, an dem mit der Bearbeitung der Aufgabe begonnen werden soll). Geben Sie im Feld **[!UICONTROL Start]** ein Intervall ein: Die Aufgabe beginnt entsprechend lange vor dem Enddatum der Kampagne. Wenn Sie einen längeren Zeitraum als die Dauer der Kampagne angeben, liegt der Aufgabenanfang vor dem Kampagnenbeginn.

![](assets/mrm_task_in_template_start_date.png)

Wenn Sie eine Kampagne mit dieser Vorlage erstellen, wird der Beginn der Aufgabe automatisch berechnet. Sie haben jedoch die Möglichkeit, das Datum zu verändern.

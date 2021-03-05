---
solution: Campaign Classic
product: campaign
title: Marketing-Kampagnenvorlagen
description: Marketing-Kampagnenvorlagen
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '1168'
ht-degree: 72%

---


# Erstellen und Konfigurieren von Kampagnenvorlagen {#campaign-templates}

Alle Marketing-Kampagnen basieren auf einer Vorlage, in der die Hauptmerkmale und Funktionen gespeichert werden. Kampagnenvorlagen werden im Knoten **[!UICONTROL Ressourcen > Vorlagen > Kampagnenvorlagen]** zentralisiert. Eine leere Vorlage ist standardmäßig vorhanden. Sie ermöglicht die Erstellung einer neuen Kampagne, die alle verfügbaren Module enthält (Dokumente, Aufgaben, Testadressen usw.). Die vorgeschlagenen Module hängen von den Berechtigungen und Konfigurationen Ihrer Adobe-Campaign-Plattform ab.

![](assets/s_ncs_user_campaign_op_template_node.png)

>[!NOTE]
>
>Um den Navigationsbaum anzuzeigen, klicken Sie auf das Symbol **[!UICONTROL Explorer]** oberhalb der Startseite.

Es wird eine integrierte Vorlage bereitgestellt, um eine Kampagne zu erstellen, für die keine bestimmte Konfiguration definiert wurde. Sie können Ihre Kampagnenvorlagen erstellen und konfigurieren und dann Kampagnen aus diesen Vorlagen erstellen.

![](assets/do-not-localize/how-to-video.png) Weitere Informationen zur Erstellung von Kampagnen finden Sie in [diesem Video](../../campaign/using/marketing-campaign-deliveries.md#create-email-video).

## Eine Kampagnenvorlage {#creating-or-duplicating-a-campaign-template} erstellen

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

Sie können die Standardvorlage auch **Duplikat** verwenden, um sie erneut zu verwenden und ihre Konfiguration anzupassen.

Die unterschiedlichen Tabs und Unter-Tabs der Kampagnenvorlage ermöglichen den Zugriff auf die Einstellungen. Sie werden im Abschnitt [Allgemeine Konfiguration](#general-configuration) beschrieben.

![](assets/s_ncs_user_new_op_template_duplicate.png)

## Module {#select-modules} auswählen

Die Einstellungen für die erweiterte Kampagne...Über den ]**-Link können Sie Aufträge für die Kampagnen aktivieren und deaktivieren, die auf dieser Vorlage basieren.**[!UICONTROL  Wählen Sie die Funktionen aus, die Sie in den auf der Grundlage dieser Vorlage erstellten Kampagnen aktivieren möchten.

![](assets/s_ncs_user_op_template_tab1.3.png)

Wenn keine Funktion ausgewählt ist, beziehen sich die Elemente auf den Prozess (Menüs, Symbole, Optionen, Registerkarten, Unterregisterkarten usw.) wird nicht in der Benutzeroberfläche der Vorlage oder in Kampagnen angezeigt, die auf dieser Vorlage basieren. Die Registerkarten links neben den Details zur Kampagne entsprechen in der Regel den in der Vorlage ausgewählten Prozessen. Wenn beispielsweise **Ausgaben und Ziele** nicht ausgewählt ist, wird die entsprechende Registerkarte **[!UICONTROL Budget]** nicht in Kampagnen angezeigt, die auf dieser Vorlage basieren.

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

## Typologie der Module {#typology-of-enabled-modules}

* **Kontrollgruppe**

   Wenn dieses Modul ausgewählt wird, wird ein zusätzlicher Tab in den erweiterten Parametern der Vorlage und der auf dieser Vorlage basierenden Kampagnen hinzugefügt. Die Konfiguration kann in der Vorlage oder direkt in den einzelnen Kampagnen erfolgen. Weitere Informationen zu Kontrollgruppen finden Sie in [diesem Abschnitt](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

   ![](assets/s_ncs_user_op_template_activate_1.png)

* **Testadressen**

   Wenn dieses Modul ausgewählt wird, wird ein zusätzlicher Tab in den erweiterten Parametern der Vorlage und der auf dieser Vorlage basierenden Kampagnen hinzugefügt. Die Konfiguration kann in der Vorlage oder direkt in den einzelnen Kampagnen erfolgen. Weitere Informationen zu Testadressen finden Sie in [diesem Abschnitt](../../delivery/using/about-seed-addresses.md).

   ![](assets/s_ncs_user_op_template_activate_2.png)

* **Dokumente**

   Wenn dieses Modul ausgewählt wird, wird ein zusätzlicher Tab im Tab **[!UICONTROL Bearbeiten]** der Vorlage und der auf dieser Vorlage basierenden Kampagnen hinzugefügt. Dokumente können über die Vorlage oder direkt in den einzelnen Kampagnen hinzugefügt werden. Weitere Informationen zu Dokumenten finden Sie in [diesem Abschnitt](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents).

   ![](assets/s_ncs_user_op_template_activate_3.png)

* **Versandentwurf**

   Wenn dieses Modul ausgewählt wird, wird dem Tab **[!UICONTROL Dokumente]** ein Untertab **[!UICONTROL Versandentwürfe]** hinzugefügt, um für die Kampagne unterschiedliche Entwürfe zu erstellen. Weitere Informationen zu Versandentwürfen finden Sie in [diesem Abschnitt](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

   ![](assets/s_ncs_user_op_template_activate_4.png)

* **Zielbestimmungen und Workflows**

   Wenn Sie das Modul **[!UICONTROL Targeting und Workflows]** auswählen, wird eine Registerkarte hinzugefügt, mit der Sie eine oder mehrere Workflows für Kampagnen erstellen können, die auf dieser Vorlage basieren. Workflows können auch einzeln für jede Kampagne auf Grundlage dieser Vorlage konfiguriert werden.Weitere Informationen zu Kampagnen-Workflows finden Sie in [diesem Abschnitt](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow).

   ![](assets/s_ncs_user_op_template_activate_5.png)

   Darüber hinaus wird mit Aktivierung dieses Moduls in den erweiterten Parametern der Kampagne ein zusätzlicher Tab hinzugefügt, in dem die Ausführungsprioritäten der Prozesse bestimmt werden können.

   ![](assets/s_ncs_user_op_template_activate_5a.png)

* **Validierung**

   Wenn das Modul **[!UICONTROL Validierung]** ausgewählt wird, können Sie zu validierende Prozesse sowie validierungsverantwortliche Benutzer bestimmen. Weitere Informationen zu Genehmigungen finden Sie in [diesem Abschnitt](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers).

   ![](assets/s_ncs_user_op_template_activate_5b.png)

   Im Tab **[!UICONTROL Validierungen]** der erweiterten Parameter der Vorlage können Sie auswählen, ob Sie die Validierung von Prozessen aktivieren möchten oder nicht. Die Prozesse, die zur Validierung ausgewählt wurden, müssen zwingend validiert werden, damit ein Nachrichtenversand möglich ist.

   Jeder aktivierten Validierung muss ein validierender Benutzer oder eine validierende Benutzergruppe zugewiesen werden.

* **Ausgaben und Ziele**

   Wenn dieses Modul ausgewählt wird, wird der Tab **[!UICONTROL Budget]** den Details der Vorlage und der auf dieser Vorlage basierenden Kampagnen hinzugefügt, um das übergeordnete Budget auszuwählen.

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

* Wählen Sie den **Kampagnentyp**: einmalig, wiederkehrend oder periodisch. Standardmäßig gelten Kampagnenvorlagen für einmalige Kampagnen. Wiederkehrende und periodische Kampagnen werden in [diesem Abschnitt](../../campaign/using/setting-up-marketing-campaigns.md#recurring-and-periodic-campaigns) beschrieben.
* Dauer der Kampagne an: Gemeint ist der Zeitraum, über den sich die Kampagne erstrecken wird. Bei Erstellung einer auf einer Vorlage basierenden Kampagne werden Beginn und Ende somit automatisch ausgefüllt.

   Handelt es sich um eine wiederkehrende Kampagne, müssen Beginn und Ende direkt in der Vorlage angegeben werden.

* **Zugehörigkeitsprogramm** der Vorlage: Die auf der Vorlage basierenden Kampagnen werden dem ausgewählten Programm zugeordnet.

### Ausführungsparameter der Vorlage {#template-execution-parameters}

Über den Link **[!UICONTROL Erweiterte Kampagnenparameter]** können weitere Optionen der Vorlage bezüglich Zielgruppen-Verarbeitung (Kontrollgruppe, Testadressen usw.) sowie Kampagnenmessung und Workflow-Ausführung konfiguriert werden.

![](assets/s_ncs_user_op_template_tab1.2.png)

## Ausführung der Kampagne verfolgen{#campaign-reverse-scheduling}

Sie können einen Zeitplan für eine Kampagne erstellen und Errungenschaften verfolgen, um beispielsweise einen Zeitplan für ein bestimmtes Ereignis vorzubereiten. Mit Kampagnenvorlagen können Sie jetzt das Datum des Beginns einer Aufgabe basierend auf dem Enddatum einer Kampagne berechnen.

Aktivieren Sie hierzu im Konfigurationsfenster der Aufgabe im Abschnitt **[!UICONTROL Erfüllungsplanung]** die Option **[!UICONTROL Das Startdatum wird vom Enddatum der Kampagne aus berechnet]** (&quot;Startdatum&quot; meint hier den Zeitpunkt, an dem mit der Bearbeitung der Aufgabe begonnen werden soll). Geben Sie im Feld **[!UICONTROL Start]** ein Intervall ein: Die Aufgabe beginnt entsprechend lange vor dem Enddatum der Kampagne. Wenn Sie einen längeren Zeitraum als die Dauer der Kampagne angeben, liegt der Aufgabenanfang vor dem Kampagnenbeginn.

![](assets/mrm_task_in_template_start_date.png)

Wenn Sie eine Kampagne mit dieser Vorlage erstellen, wird der Beginn der Aufgabe automatisch berechnet. Sie haben jedoch die Möglichkeit, das Datum zu verändern.

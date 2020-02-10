---
title: Marketingkampagnenlieferungen
seo-title: Marketingkampagnenlieferungen
description: Marketingkampagnenlieferungen
seo-description: Weitere Informationen zu Marketingkampagnenlieferungen
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
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# Marketingkampagnenlieferungen {#marketing-campaign-deliveries}

Sendungen können über das Dashboard einer Kampagne, einen Kampagnenworkflow oder direkt über die Übersicht der Sendungen erstellt werden.

## Sendungen erstellen {#creating-deliveries}

To create a delivery linked to a campaign, click the **[!UICONTROL Add a delivery]** link in the campaign dashboard.

![](assets/campaign_op_add_delivery.png)

Die angebotenen Parameter werden den unterschiedlichen Versandtypen angepasst (Briefpost, E-Mail, Mobile-Kanäle, Fax oder Telefon).

>[!NOTE]
>
>Weitere Informationen zur Erstellung und Konfiguration von Sendungen finden Sie unter [Nachrichten senden](../../delivery/using/communication-channels.md).

## Zielgruppe bestimmen {#selecting-the-target-population}

Der Kampagnenverantwortliche bestimmt für jeden Versand

* Das Hauptziel. Weitere Informationen finden Sie unter [Erstellen des Hauptziels in einem Workflow](#building-the-main-target-in-a-workflow) und [Auswählen der Zielgruppe](#selecting-the-target-population).
* Die Kontrollgruppe. Weitere Informationen finden Sie unter [Definieren einer Kontrollgruppe](#defining-a-control-group).
* Die Seed-Adresse. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/about-seed-addresses.md).

Einige dieser Parameter werden bereits durch die Kampagnenvorlage festgelegt.

>[!NOTE]
>
>Kampagnenvorlagen werden in [Kampagnenvorlagen](../../campaign/using/marketing-campaign-templates.md#campaign-templates)dargestellt.

Zur Bestimmung einer Versand-Zielgruppe können Sie die in Ihrer Datenbank enthaltenen Empfänger mithilfe von Kriterien filtern. Dieser Auswahlmodus wird im Abschnitt [Nachrichten senden](../../delivery/using/steps-defining-the-target-population.md) beschrieben.

### Beispiel: Versand an eine Gruppe von Empfängern {#example--delivering-to-a-group-of-recipients}

Sie haben die Möglichkeit, eine Population in eine Liste zu importieren und diese Liste als Zielgruppe eines Versands zu verwenden.

1. To do this, edit the concerned delivery and click the **[!UICONTROL To]** link to change the targeted population.

1. Wählen Sie auf der **[!UICONTROL Main target]** Registerkarte die **[!UICONTROL Defined via the database]** Option aus und klicken Sie auf **[!UICONTROL Add]** , um die Empfänger auszuwählen.

![](assets/s_user_target_group_add.png)

1. Wählen Sie **[!UICONTROL A list of recipients]** die Option und klicken Sie auf **[!UICONTROL Next]** , um sie auszuwählen.

![](assets/s_user_target_group_next.png)

### Erstellen einer Hauptzielgruppe im Workflow {#building-the-main-target-in-a-workflow}

Die Hauptzielgruppe eines Versands kann auch über einen Zielgruppen-Workflow bestimmt werden: Die grafische Umgebung ermöglicht die Erstellung einer Zielgruppe mithilfe von Abfragen, Tests und Aktivitäten wie Vereinigungen, Deduplizierungen, Aufspaltungen usw.

Eine detaillierte Beschreibung der Funktionsweise des Workflow-Moduls erhalten Sie im Handbuch [Automatisierung mithilfe von Workflows](../../workflow/using/executing-a-workflow.md#architecture).

>[!CAUTION]
>
>Für dieselbe Kampagne können maximal 28 Workflows eingerichtet werden. Zusätzliche Workflows sind in der Benutzeroberfläche nicht sichtbar und können Fehler verursachen.

#### Erstellen eines Zielgruppen-Workflows {#creating-a-targeting-workflow}

Targeting kann über eine Kombination von Filterbedingungen in einer grafischen Sequenz in einem Workflow erstellt werden. Sie können Populationen und Subpopulationen erstellen, die entsprechend Ihren Anforderungen ausgerichtet werden. Um den Workflow-Editor anzuzeigen, klicken Sie auf die **[!UICONTROL Targeting and workflows]** Registerkarte im Kampagnen-Dashboard.

![](assets/s_ncs_user_edit_op_wf_link.png)

Die Zielpopulation wird über eine oder mehrere in einem Workflow platzierte Abfragen aus der Adobe-Campaign-Datenbank extrahiert. Weiterführende Informationen zum Erstellen einer Abfrage finden Sie in [diesem Abschnitt](../../workflow/using/query.md).

Sie können Abfragen starten und die resultierenden Populationen über Aktivitäten wie Vereinigung, Schnittmenge, Aufspaltung, Ausschluss weiter einschränken oder vergrößern.

Wählen Sie die gewünschten Aktivitäten aus den links vom Arbeitsbereich liegenden Menüs aus und reihen Sie diese aneinander, um die Zielgruppe zu erstellen.

![](assets/s_ncs_user_edit_op_wf_tab_a.png)

Verbinden Sie die zur Zielgruppenerstellung notwendigen Zielbestimmungs- und Steuerungsaktivitäten im Diagramm miteinander: Sie können die Zielgruppenbestimmung bereits während ihrer Erstellung ausführen, um die aus der Datenbank extrahierte Population zu überprüfen.

>[!NOTE]
>
>Examples and procedure for defining queries are presented in [this section](../../workflow/using/query.md).

Im linken Bereich des Editors befindet sich eine Bibliothek grafischer Objekte, die Aktivitäten repräsentieren. Der erste Tab enthält Aktivitäten zur Zielgruppenbestimmung, der zweite Aktivitäten zur Steuerung. Letztere werden gelegentlich zur Koordinierung der Zielgruppenbestimmungs-Aktivitäten verwendet.

Über die Symbolleiste des Workflow-Editors besteht Zugriff auf Funktionen zur Formatierung und Ausführung des Zielgruppen-Workflows.

![](assets/s_user_campaign_segmentation05.png)

>[!NOTE]
>
>Die zur Erstellung des Workflow-Diagramms verfügbaren Aktivitäten sowie alle Anzeige- und Layoutfunktionalitäten werden im Handbuch [Automatisierung mithilfe von Workflows](../../workflow/using/executing-a-workflow.md#architecture) dargestellt.

Es besteht die Möglichkeit, mehrere Zielgruppen-Workflows für eine einzelne Kampagne zu erstellen. Gehen Sie wie folgt vor, um einen Workflow hinzuzufügen:

1. Gehen Sie zum oberen linken Bereich der Workflow-Erstellungszone, klicken Sie mit der rechten Maustaste und wählen Sie **[!UICONTROL Add]**. Sie können auch die **[!UICONTROL New]** Schaltfläche oberhalb dieser Zone verwenden.

   ![](assets/s_ncs_user_add_a_wf.png)

1. Select the **[!UICONTROL New workflow]** template and name this workflow.
1. Klicken Sie auf **[!UICONTROL OK]**, um die Workflow-Erstellung zu bestätigen, und entwerfen Sie das Diagramm des Workflows.

#### Workflow ausführen {#executing-a-workflow}

Targeting workflows can be launched manually via the **[!UICONTROL Start]** button in the toolbar, provided that you have the appropriate rights.

Die Zielgruppenbestimmung kann so konfiguriert werden, dass sie entsprechend einer Planungsaktivität (Planungsassistent) oder abhängig von einem Ereignis (externes Signal, Dateiimport usw.) automatisch ausgeführt wird.

Bei Aktionen bezüglich der Ausführung des Zielgruppen-Workflows (Start, Stopp, Pause etc.) handelt es sich um **asynchrone** Prozesse: Der jeweilige Befehl wird gespeichert und wird ausgeführt, sobald der Server verfügbar ist.

Über die Symbolleiste hingegen kann die Ausführung des Zielgruppen-Workflows unmittelbar gesteuert werden.

* Starten oder neu starten

   * Über das **[!UICONTROL Start]** Symbol können Sie den Targeting-Arbeitsablauf starten. Wenn Sie auf dieses Symbol klicken, werden alle Aktivitäten ohne Eingabetaste aktiviert (mit Ausnahme von Endpunktspringern).

      ![](assets/s_user_segmentation_start.png)

      Die Anfrage wird vom Server erfasst, was sich im Ausführungsstatus widerspiegelt:

      ![](assets/s_user_segmentation_start_status.png)

      The process status changes to **[!UICONTROL Started]**.

   * Sie können den Targeting-Workflow über das entsprechende Symbolleistensymbol neu starten. Dieser Befehl kann nützlich sein, wenn das **[!UICONTROL Start]** Symbol nicht verfügbar ist, z. B. wenn das Beenden des Targeting-Workflows ausgeführt wird. Klicken Sie in diesem Fall auf das **[!UICONTROL Restart]** Symbol, um den Neustart vorherzusehen. Der Server berücksichtigt die Anforderung, wie ihr Status zeigt:

      ![](assets/s_user_segmentation_restart_status.png)

      The process then enters **[!UICONTROL Started]** status.

* Anhalten oder aussetzen

   * Über die Symbolleiste kann die Ausführung des Zielgruppen-Workflows angehalten oder ausgesetzt werden.

      When you click **[!UICONTROL Pause]**, operations in progress **[!UICONTROL are not]** paused, but no other activity is launched until the next restart.

      ![](assets/s_user_segmentation_pause.png)

      Die Anfrage wird vom Server erfasst und vom Ausführungsstatus angezeigt:

      ![](assets/s_user_segmentation_pause_status.png)

      You can also pause a targeting workflow automatically when its execution reaches a particular activity. To do this, right-click the activity from which targeting workflow is to be paused, and select **[!UICONTROL Enable but do not execute]**.

      ![](assets/s_user_segmentation_donotexecute.png)

      Die Konfiguration wird von einem spezifischen Symbol in der Grafik repräsentiert.

      ![](assets/s_user_segmentation_pause_activity.png)

      >[!NOTE]
      >
      >Diese Option erweist sich insbesondere in Entwurfs- und Testphasen einer Zielbestimmung als nützlich.

      Click **[!UICONTROL Start]** to resume execution.

   * Click the **[!UICONTROL Stop]** icon to stop the execution in progress.

      ![](assets/s_user_segmentation_stop.png)

      Die Anfrage wird vom Server erfasst und vom Ausführungsstatus angezeigt:

      ![](assets/s_user_segmentation_stop_status.png)
   You can also stop a targeting workflow automatically when the execution reaches an activity. To do this, right-click the activity from which targeting workflow will be stopped, and select **[!UICONTROL Do not activate]**.

   ![](assets/s_user_segmentation_donotactivate.png)

   ![](assets/s_user_segmentation_unactivation.png)

   Die Konfiguration wird von einem spezifischen Symbol in der Grafik repräsentiert.

   >[!NOTE]
   >
   >Diese Option erweist sich insbesondere in Entwurfs- und Testphasen einer Zielbestimmung als nützlich.

* Unbedingter Stopp

   Wählen Sie im Explorer **[!UICONTROL Administration > Production > Object created automatically > Campaign workflows]** die Option, um auf jeden Kampagnen-Workflow zuzugreifen und darauf zu reagieren.

   Sie können Ihren Workflow bedingungslos beenden, indem Sie auf das **[!UICONTROL Actions]** Symbol klicken und **[!UICONTROL Unconditional]** Stopp auswählen. Durch diese Aktion wird Ihr Kampagnen-Workflow beendet.

   ![](assets/s_user_segmentation_stop_unconditional.png)

### Bestimmen einer Kontrollgruppe {#defining-a-control-group}

Bei der Kontrollgruppe handelt es sich um eine Population, die den Versand nicht erhält. Sie erlaubt es, Verhaltensunterschiede im Vergleich zu den Empfängern der Zielgruppe, die den Versand erhält, und somit die Auswirkungen einer Kampagne zu messen.

Die Kontrollgruppe kann aus der Hauptzielgruppe extrahiert werden und/oder aus einer speziellen Abfrage hervorgehen.

#### Aktivieren der Kontrollgruppe für eine Kampagne {#activating-the-control-group-for-a-campaign}

Sie können eine Kontrollgruppe auf Kampagnenebene definieren. In diesem Fall wird die Kontrollgruppe auf jede Auslieferung der betreffenden Kampagne angewendet.

1. Bearbeiten Sie die betreffende Kampagne und klicken Sie auf die **[!UICONTROL Edit]** Registerkarte.
1. Klicks **[!UICONTROL Advanced campaign settings]**.

   ![](assets/s_ncs_user_edit_op_target.png)

1. Select the **[!UICONTROL Enable and edit control group configuration]** option.
1. Klicken Sie auf **[!UICONTROL Edit...]** , um die Kontrollgruppe zu konfigurieren.

   ![](assets/s_ncs_user_edit_op_general_tab_exe_target.png)

Das Konfigurationsverfahren wird unter [Extrahieren der Kontrollgruppe vom Hauptziel](#extracting-the-control-group-from-the-main-target) und [Hinzufügen einer Population](#adding-a-population)dargestellt.

#### Aktivieren der Kontrollgruppe für eine Bereitstellung {#activating-the-control-group-for-a-delivery}

Sie können eine Kontrollgruppe auf Bereitstellungsebene definieren. In diesem Fall wird die Kontrollgruppe auf jede Auslieferung der betreffenden Kampagne angewendet.

Die in einer Kampagne vorgenommene Konfiguration einer Kontrollgruppe gilt standardmäßig für jeden Versand dieser Kampagne. Sie kann jedoch für einzelne Sendungen angepasst werden.

>[!NOTE]
>
>Wenn Sie eine Kontrollgruppe für eine Kampagne bestimmt haben und eine andere für einen Versand dieser Kampagne konfigurieren, so wird nur die für den Versand bestimmte Kontrollgruppe angewandt.

1. Bearbeiten Sie die betreffende Lieferung und klicken Sie dann auf den **[!UICONTROL To]** Link im **[!UICONTROL Email parameters]** Abschnitt.

   ![](assets/s_ncs_user_edit_op_target_del.png)

1. Klicken Sie auf die **[!UICONTROL Control group]** Registerkarte und wählen Sie dann **[!UICONTROL Enable and edit control group configuration]**.
1. Klicken Sie **[!UICONTROL Edit...]** , um die Kontrollgruppe zu konfigurieren

Das Konfigurationsverfahren wird unter [Extrahieren der Kontrollgruppe vom Hauptziel](#extracting-the-control-group-from-the-main-target) und [Hinzufügen einer Population](#adding-a-population)dargestellt.

#### Extraktion der Kontrollgruppe aus der Hauptzielgruppe {#extracting-the-control-group-from-the-main-target}

Sie haben die Möglichkeit, Empfänger der Hauptzielgruppe eines Versands zu extrahieren: Die Empfänger werden in diesem Fall von der Zielgruppe der von dieser Konfiguration betroffenen Versandaktionen abgezogen. Diese Extraktion kann zufällig oder durch Sortierung der Empfänger erfolgen.

![](assets/s_ncs_user_extract_from_target_population.png)

Um eine Kontrollgruppe zu extrahieren, aktivieren Sie die Kontrollgruppe für die Kampagne oder Bereitstellung und wählen Sie eine der folgenden Optionen: **[!UICONTROL Activate random sampling]** oder **[!UICONTROL Keep only the first records after sorting]**.

* **[!UICONTROL Activate random sampling]** : Diese Option wendet Stichproben auf die Empfänger in der Zielgruppe an. Wenn Sie dann den Schwellenwert auf 100 festlegen, besteht die Kontrollgruppe aus 100 zufällig ausgewählten Empfängern aus der Zielgruppe. Die Stichprobenauswahl hängt von der Datenbank-Engine ab.
* **[!UICONTROL Keep only the first records after sorting]** : Mit dieser Option können Sie eine Beschränkung festlegen, die auf einer oder mehreren Sortierreihenfolgen basiert. Wenn Sie das **[!UICONTROL Age]** Feld als Sortierkriterium auswählen und dann 100 als Schwellenwert definieren, besteht die Kontrollgruppe aus den 100 jüngsten Empfängern. So könnte es interessant sein, eine Kontrollgruppe zu definieren, die Empfänger mit wenigen Käufen oder Empfänger mit häufigen Käufen umfasst, und ihr Verhalten mit dem der kontaktierten Empfänger zu vergleichen.

Click **[!UICONTROL Next]** to define the sorting order (if necessary) and select the recipient limitation mode.

![](assets/s_ncs_user_edit_op_target_param.png)

Diese Konfiguration entspricht der einer Aufspaltungsaktivität im Workflow, die die Unterteilung einer Zielgruppe in mehrere Teilmengen ermöglicht. Die Kontrollgruppe entspricht einer dieser Teilmengen. Weitere Informationen hierzu finden Sie in [diesem Abschnitt](../../workflow/using/executing-a-workflow.md#architecture).

### Hinzufügen einer zusätzlichen Population {#adding-a-population}

Sie können eine neue, als Kontrollgruppe zu verwendende Population bestimmen. Diese Population kann aus einer Gruppe von Empfängern oder aus einer spezifischen Abfrage hervorgehen.

![](assets/s_ncs_user_add_to_target_population.png)

>[!NOTE]
>
>Der Abfrageeditor von Adobe Campaign wird in [diesem Abschnitt](../../workflow/using/query.md) beschrieben.

## Starten eines Versands {#starting-a-delivery}

Sobald alle Genehmigungen erteilt wurden, kann die Bereitstellung gestartet werden. Der Liefervorgang hängt dann von der Art der Lieferung ab. Informationen zu E-Mail- oder Mobilkanalauslieferungen finden Sie unter [Starten einer Online-Auslieferung](#starting-an-online-delivery)und zu Direktversandauslieferungen finden Sie unter [Starten einer Offline-Auslieferung](#starting-an-offline-delivery).

### Starten eines Online-Versands {#starting-an-online-delivery}

Sobald alle Genehmigungsanforderungen erteilt wurden, ändert sich der Lieferstatus in **[!UICONTROL Pending confirmation]** und kann von einem Operator gestartet werden. Gegebenenfalls wird der Adobe Campaign-Betreiber (oder eine Gruppe von Betreibern), der bzw. die zum Starten der Bereitstellung ernannt wurde, darüber informiert, dass die Bereitstellung gestartet werden kann.

>[!NOTE]
>
>If a specific operator or group of operators is designated for starting a delivery in the delivery&#39;s properties, you can also allow the operator in charge of the delivery to confirm the send. To do this, activate the **NMS_ActivateOwnerConfirmation** option by entering **1** as the value. Die Optionen werden über den Knoten **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** im Adobe Campaign Explorer verwaltet.
>  
>Um die entsprechende Option zu deaktivieren, ist der Wert **0** anzugeben. In diesem Fall kann die Versandvalidierung nur durch die in den Versandeigenschaften angegebenen Benutzer oder Benutzergruppen bzw. einen Administrator erfolgen.

![](assets/s_ncs_user_edit_del_to_start_from_del.png)

Die Informationen werden auch im Kampagnen-Dashboard angezeigt. Über den **[!UICONTROL Confirm delivery]** Link können Sie die Bereitstellung starten.

![](assets/s_ncs_user_edit_del_to_start.png)

Zur Sicherheit werden Sie in einer Pop-up-Nachricht zur Bestätigung des Vorgangs aufgefordert.

### Starten eines Offline-Versands {#starting-an-offline-delivery}

Sobald alle Genehmigungen erteilt wurden, wird der Lieferstatus in **[!UICONTROL Pending extraction]** geändert. Die Extrahierungsdateien werden über einen speziellen Arbeitsablauf erstellt, der in einer Standardkonfiguration automatisch startet, wenn die Extrahierung einer Direktversand-Datei noch aussteht. Wenn ein Prozess ausgeführt wird, wird er im Dashboard angezeigt und kann über den Link bearbeitet werden.

>[!NOTE]
>
>Die technischen Arbeitsabläufe zu Kampagnenprozessen werden in der [Liste der Kampagnenprozesse](../../workflow/using/campaign.md)dargestellt.

**1. Schritt - Datei validieren**

Wenn der Extraktions-Workflow korrekt ausgeführt wurde, muss die Extrationsdatei validiert werden (sofern die Validierung der Extraktionsdatei in der Versandkonfiguration aktiviert wurde).

Weitere Informationen finden Sie unter [Genehmigen einer Extraktionsdatei](../../campaign/using/marketing-campaign-approval.md#approving-an-extraction-file).

**2. Schritt - Nachricht an den Dienstleister validieren**

* Nachdem die Validierung der Extraktionsdatei akzeptiert wurde, kann der Testversand der Benachrichtigungs-E-Mail an den Router erzeugt werden. Diese E-Mail wird über eine Versandvorlage erstellt und muss validiert werden.

   >[!NOTE]
   >
   >Diese Etappe ist nur dann verfügbar, wenn die Durchführung und Validierung von Testsendungen im Fenster der Validierungseinstellungen aktiviert wurden.

![](assets/s_ncs_user_file_valid_select_BAT.png)


* Klicken Sie auf die **[!UICONTROL Send a proof]** Schaltfläche, um die Proofs zu erstellen.

   Zunächst muss die Zielgruppe der Testsendungen bestimmt werden.

   Sie können so viele Proofs wie nötig erstellen. Diese werden über den **[!UICONTROL Direct mail...]** Link der Lieferdetails aufgerufen.

   ![](assets/s_ncs_user_file_notif_submit_proof.png)

* Der Bereitstellungsstatus ändert sich in **[!UICONTROL To submit]**. Klicken Sie auf die **[!UICONTROL Submit proofs]** Schaltfläche, um den Genehmigungsprozess zu starten.

   ![](assets/s_ncs_user_file_notif_submit_proof_validation.png)

* The delivery status changes to **[!UICONTROL Proof to validate]** and a button lets you accept or reject approval.

   ![](assets/s_ncs_user_file_notif_supplier_link.png)

   Im Validierungs-Pop-up können Sie die Validierung akzeptieren oder ablehnen oder zur Extraktionsetappe zurückkehren.

   ![](assets/s_ncs_user_file_notif_supplier_link_confirm.png)

* Die Extraktionsdatei wird dann dem Router gesendet und der Versand ist beendet.

### Kosten- und Lagerberechnung {#calculation-of-costs-and-stocks}

Die Dateiextraktion startet zwei Vorgänge: die Berechnung der Budgets und die Berechnung der Lagerbestände. Die Budgetzeilen werden aktualisiert.

* Auf der **[!UICONTROL Budget]** Registerkarte können Sie die Budgets für die Kampagne verwalten. Die Gesamtsumme der Kosteneinträge wird im **[!UICONTROL Calculates cost]** Feld der Hauptregisterkarte der Kampagne und des Programms angezeigt, zu dem sie gehört. Die Beträge werden auch im Kampagnenbudget angezeigt.

   Die tatsächlichen Kosten werden am Ende entsprechend der vom Router kommunizierten Informationen berechnet: Nur die tatsächlich versendeten Briefe werden fakturiert.

* Die Bestände werden im **[!UICONTROL Administration > Campaign management > Stocks]** Knoten des Baums definiert und die Kostenstrukturen im **[!UICONTROL Administration > Campaign management > Service providers]** Knoten.

   Lagerpositionen können auf Ebene der Lager angezeigt werden. Öffnen Sie eine Lagerposition, um den Anfangsbestand festzulegen. Der Bestand wird mit jedem Versand dekrementiert. Sie haben die Möglichkeit, einen Meldebestand mit Benachrichtigungen zu konfigurieren.

>[!NOTE]
>
>Weitere Informationen zu Kostenberechnungen und Bestandsverwaltung finden Sie unter [Anbieter, Bestände und Budgets](../../campaign/using/providers--stocks-and-budgets.md).

## Zugeordnete Dokumente verwalten {#managing-associated-documents}

Sie können verschiedene Dokumente mit einer Kampagne verknüpfen: Bericht, Foto, Webseite, Diagramm usw. Diese Dokumente können in jedem Format vorliegen (Microsoft Word, PowerPoint, PNG, JPG, Acrobat PDF usw.). Informationen zum Verknüpfen von Dokumenten mit einer Kampagne finden Sie unter [Hinzufügen von Dokumenten](#adding-documents).

>[!CAUTION]
>
>Diese Funktionalität eignet sich nur für kleine Dokumente.

In einer Kampagne können Sie auch auf andere Elemente verweisen, wie z.B. Promo-Gutscheine, Sonderangebote für eine bestimmte Branche oder einen bestimmten Store usw. Wenn diese Elemente in einer Umrisslinie enthalten sind, können sie mit einer Direktversand in Verbindung gebracht werden. See [Associating and structuring resources linked via a delivery outline](#associating-and-structuring-resources-linked-via-a-delivery-outline).

>[!NOTE]
>
>Wenn Sie MRM verwenden, können Sie auch eine Bibliothek mit Marketingressourcen verwalten, die mehreren Teilnehmern für die gemeinsame Arbeit zur Verfügung stehen. Siehe [Verwalten von Marketingressourcen](../../campaign/using/managing-marketing-resources.md).

### Hinzufügen von Dokumenten {#adding-documents}

Dokumente können einer Kampagne (kontextrelevante Dokumente) oder einem Programm (allgemeine Dokumente) zugeordnet werden.

Die **[!UICONTROL Documents]** Registerkarte enthält:

* die Liste aller für den Inhalt notwendigen Dokumente (Vorlagen, Bilder usw.), die von berechtigten Adobe-Campaign-Benutzern lokal heruntergeladen werden können;
* Informationen für den Router enthaltende Dokumente, wenn vorhanden.

The documents are linked to the program or the campaign via the **[!UICONTROL Edit > Documents]** tab.

![](assets/s_ncs_user_op_add_document.png)

Es besteht darüber hinaus die Möglichkeit, Dokumente über einen im Dashboard angebotenen Link einer Kampagne zuzuordnen.

![](assets/add_a_document_in_op.png)

Klicken Sie auf das Symbol **[!UICONTROL Details]**, um den Inhalt einer Datei anzusehen und ergänzende Informationen hinzuzufügen.

![](assets/s_ncs_user_op_add_document_details.png)

In the dashboard, documents associated with the campaign are grouped in the **[!UICONTROL Document(s)]** section, as in the following example:

![](assets/s_ncs_user_op_edit_document.png)

Über die Links können die Dokumente geöffnet und bearbeitet werden.

### Ressourcen in einem Versandentwurf verknüpfen {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>Lieferumrisse werden ausschließlich im Rahmen von Direktpostkampagnen verwendet.

Ein Versandentwurf stellt eine strukturierte Einheit von Elementen dar (Dokumente, Gutscheine etc.), die für eine bestimmte Kampagne erstellt wurden.

Der bestimmte Elemente umfassende Versandentwurf wird einem Versand angefügt: Im Versand wird der Entwurf in der dem **Dienstleister** übermittelten Extraktionsdatei referenziert, um schließlich als Anhang des Versands verschickt zu werden. Sie können beispielsweise einen Versandentwurf erstellen, der von einer Zweigstelle verwendete Marketingbroschüren enthält.

Versandentwürfe ermöglichen es, in Kampagnen externe Elemente zu strukturieren, die einem Versand nach bestimmten Kriterien hinzugefügt werden: bewilligtes Sonderangebot, Einladung zu einem lokalen Event etc.

#### Versandentwurf erstellen {#creating-an-outline}

To create an outline, click the **[!UICONTROL Delivery outlines]** sub-tab in the **[!UICONTROL Edit > Documents]** tab of the concerned campaign.

>[!NOTE]
>
>Sollte dieser Tab nicht vorhanden sein, ist die Funktionalität für diese Kampagne nicht verfügbar. Überprüfen Sie in diesem Fall die Konfiguration der Kampagnenvorlage.
>   
>For more on this, refer to [Campaign templates](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

![](assets/s_ncs_user_op_composition_link.png)

Klicken Sie anschließend auf **[!UICONTROL Add a delivery outline]** und erstellen Sie die Hierarchie der Umrisse für die Kampagne:

1. Klicken Sie mit der rechten Maustaste auf die Stamm-Node und wählen Sie **[!UICONTROL New > Delivery outlines]**.
1. Klicken Sie mit der rechten Maustaste auf die gerade erstellte Umrisslinie und wählen Sie **[!UICONTROL New > Item]** oder **[!UICONTROL New > Personalization fields]**.

![](assets/s_ncs_user_op_add_composition.png)

Ein Versandentwurf kann Artikel, Personalisierungsfelder, Ressourcen und Angebote enthalten:

* Artikel sind beispielsweise physische Dokumente, die an dieser Stelle referenziert und beschrieben und schließlich dem Versand angehängt werden.
* Mit Personalisierungsfeldern können Sie Personalisierungselemente erstellen, die sich auf Lieferungen und nicht auf Empfänger beziehen. Es ist somit möglich, Werte zu erstellen, die in Lieferungen für ein bestimmtes Ziel (Willkommensangebot, Rabatt usw.) verwendet werden. Sie werden in Adobe Campaign erstellt und über den **[!UICONTROL Import personalization fields...]** Link in die Gliederung importiert.

   ![](assets/s_ncs_user_op_add_composition_field.png)

   They can also be created directly in the outline by clicking the **[!UICONTROL Add]** icon to the right of the list zone.

   ![](assets/s_ncs_user_op_add_composition_field_button.png)

* The resources are marketing resources generated in the marketing resource dashboard accessed via the **[!UICONTROL Resources]** link of the **[!UICONTROL Campaigns]** universe.

   ![](assets/s_ncs_user_mkg_resource_ovv.png)

   >[!NOTE]
   >
   >Weitere Informationen zu Marketingressourcen finden Sie unter [Verwalten von Marketingressourcen](../../campaign/using/managing-marketing-resources.md).

#### Einen Versandentwurf auswählen {#selecting-an-outline}

Sie können für jeden Versand über den Bereich der Extraktionskonfiguration einen Entwurf auswählen, wie im folgenden Beispiel:

![](assets/s_ncs_user_op_select_composition.png)

Der ausgewählte Entwurf wird daraufhin im unteren Abschnitt des Fenster angezeigt. Er kann über das rechts vom Feld gelegene Lupensymbol geöffnet oder über die Dropdown-Liste durch einen anderen ersetzt werden:

![](assets/s_ncs_user_op_select_composition_b.png)

The **[!UICONTROL Summary]** tab of the delivery also displays this information:

![](assets/s_ncs_user_op_select_composition_c.png)

#### Extraktionsergebnis {#extraction-result}

In der dem Dienstleister übermittelten Extraktionsdatei werden der Name des Entwurfs sowie gegebenenfalls seine Eigenschaften (Kosten, Beschreibung usw.) dem Inhalt hinzugefügt, entsprechend der Informationen in der Exportvorlage, die dem Dienstleister zugeordnet wurde.

Im folgenden Beispiel werden der Titel, die Plankosten sowie die Beschreibung des dem Versand zugeordneten Entwurfs der Extraktionsdatei hinzugefügt.

![](assets/s_ncs_user_op_composition_in_export_template.png)

Das Exportmodell muss mit dem für die Lieferung ausgewählten Dienstleister verknüpft sein. See [Creating service providers and their cost structures](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).

>[!NOTE]
>
>Weitere Informationen zu Exporten finden Sie im Abschnitt [Erste Schritte](../../platform/using/generic-imports-and-exports.md).

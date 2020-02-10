---
title: A/B Testing
seo-title: A/B Testing
description: A/B Testing
seo-description: null
page-status-flag: never-activated
uuid: 8887574e-447b-48a5-afc6-95783ffa7fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 4113c3fe-a279-4fe1-be89-ea43c96edc34
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# A/B Testing{#a-b-testing}

Für einen E-Mail-Versand wurden verschiedene Inhalte erstellt und Sie möchten testen, welcher Inhalt bei der angesprochenen Zielgruppe die größten Erfolgschancen hat. Hierzu werden die verschiedenen Versionen jeweils an einen Teil der Zielgruppe gesendet. Die Version, die die besten Ergebnisse erzielt, wird dann an den Rest der Empfängerzielgruppe gesendet.

Im vorliegenden Anwendungsbeispiel wird ein Zielgruppen-Workflow verwendet, um zwei Inhaltsversionen zu vergleichen. Der Text ist jeweils derselbe, nur die Aufmachung unterscheidet sich.

Die Zielgruppe wird in drei Untergruppen geteilt: zwei Testpopulationen und die verbleibende Population. Jede Testpopulation erhält eine der beiden Versionen. Nach dem Versand werden die Öffnungsraten fünf Tage lang gesammelt. Die Version mit dem besten Ergebnis wird durch ein Script abgerufen und an die verbleibende Population gesendet.

Die Auswahl der Siegerversion kann je nach Bedarf nach verschiedenen Kriterien erfolgen. Hierbei kann es sich beispielsweise um die Öffnungsrate, Klickrate, Anmelderate oder die Reaktivität handeln.

Das vorliegende Beispiel beschränkt den Test auf zwei Versionen. Sie können jedoch bei Bedarf so viele Versionen wie nötig testen, indem Sie den Workflow entsprechend um weitere Aktivitäten ergänzen.

Gehen Sie zur Erstellung des A/B-Tests wie folgt vor:

* [1. Schritt: Erstellung eines Zielgruppen-Workflows](#step-1--creating-a-targeting-workflow)
* [2. Schritt: Konfiguration der Testpopulation](#step-2--configuring-population-samples)
* [3. Schritt: Erstellung von zwei Versandvorlagen](#step-3--creating-two-delivery-templates)
* [4. Schritt: Konfiguration der Sendungen im Workflow](#step-4--configuring-the-deliveries-in-the-workflow)
* [5. Schritt: Erstellung des Scripts](#step-5--creating-the-script)
* [7. Schritt: Start des Workflows](#step-7--starting-the-workflow)
* [8. Schritt: Ergebnisanalyse](#step-8--analyzing-the-result).

## 1. Schritt: Erstellung eines Zielgruppen-Workflows {#step-1--creating-a-targeting-workflow}

Sie müssen Ihren Workflow auf der **[!UICONTROL Targeting and Workflows]** Registerkarte einer Kampagne erstellen. Er besteht aus einer **[!UICONTROL Query]** Aktivität, einer **[!UICONTROL Split]** Aktivität, die mit zwei **[!UICONTROL Email delivery]** Aktivitäten verbunden ist, einer **[!UICONTROL Wait]** Aktivität, einer **[!UICONTROL JavaScript code]** Aktivität und einer **[!UICONTROL Delivery]** Aktivität.

1. Öffnen Sie eine existierende Kampagne oder erstellen Sie eine neue (siehe diesen [Abschnitt](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Go to the **[!UICONTROL Targeting and Workflows]** tab.

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Change the label of the existing workflow or click **[!UICONTROL Add]** to create a new one (for more on this, refer to this [section](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Verwenden Sie die Maus, um Aktivitäten in das Workflow-Diagramm zu ziehen, darunter eine **[!UICONTROL Query]** (**[!UICONTROL Target]** Registerkarte), eine **[!UICONTROL Split]** (**[!UICONTROL Target]** Registerkarte), zwei **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]** Registerkarte), eine **[!UICONTROL Wait]** Aktivität (**[!UICONTROL Flow Control]** Registerkarte), eine **[!UICONTROL JavaScript code]** Aktivität (Registerkarte) und eine-Aktivität (Registerkarte &quot;**[!UICONTROL Actions]** **[!UICONTROL Delivery]****[!UICONTROL Actions]** &quot;).

![](assets/use_case_abtesting_targetwkfl_004.png)

## 2. Schritt: Konfiguration der Testpopulation {#step-2--configuring-population-samples}

### Konfiguration der Abfrage {#configuring-the-query-activity}

* Double-click the **[!UICONTROL Query]** activity.

   ![](assets/use_case_abtesting_createrecipients_001.png)

* Click the **[!UICONTROL Edit query]** link and select the recipients you want to target.

   ![](assets/use_case_abtesting_createrecipients_002.png)

* Verknüpfen Sie die **[!UICONTROL Query]** Aktivität mit der **[!UICONTROL Split]** Aktivität.

   ![](assets/use_case_abtesting_createrecipients_003.png)

### Konfiguration der Aufspaltung {#configuring-the-split-activity}

Mithilfe dieser Aktivität werden die drei Populationen erstellt: A, B und Rest. Dank der Zufallsauswahl erhält jeweils nur ein Teil jeder Population den entsprechenden Versand.

1. Erstellung der Testpopulation A:

   * Double-click the **[!UICONTROL Split]** activity.

      ![](assets/use_case_abtesting_createrecipients_004.png)

   * Ändern Sie den Titel für die Testpopulation A entsprechend ab.

      ![](assets/use_case_abtesting_createrecipients_005.png)

   * Select the **[!UICONTROL Limit the selected records]** option.

      ![](assets/use_case_abtesting_createrecipients_006.png)

   * Klicken Sie auf den **[!UICONTROL Edit]** Link, wählen Sie **[!UICONTROL Activate random sampling]** und klicken Sie auf **[!UICONTROL Next]**.

      ![](assets/use_case_abtesting_createrecipients_007.png)

   * Set the threshold to 10%, then click **[!UICONTROL Finish]**.

      ![](assets/use_case_abtesting_createrecipients_008.png)

1. Erstellung der Testpopulation B:

   * Click **[!UICONTROL Add]** to create a new tab for population B.

      ![](assets/use_case_abtesting_createrecipients_009.png)

   * Begrenzen Sie wie zuvor die Testpopulation auf 10 %.

      ![](assets/use_case_abtesting_createrecipients_010.png)

1. Erstellung der verbleibenden Population:

   * Go to the **[!UICONTROL General]** tab.

      ![](assets/use_case_abtesting_createrecipients_011.png)

   * Auswählen **[!UICONTROL Generate complement]**.

      ![](assets/use_case_abtesting_createrecipients_012.png)

   * Benennen Sie die verbleibende Population und klicken Sie auf **[!UICONTROL OK]**, um die Aktivität zu schließen.

      ![](assets/use_case_abtesting_createrecipients_013.png)

## 3. Schritt: Erstellung von zwei Versandvorlagen {#step-3--creating-two-delivery-templates}

Wir möchten nun zwei Bereitstellungsvorlagen erstellen. Jede Vorlage wird in einer **[!UICONTROL Email delivery]** Aktivität referenziert, die mit der **[!UICONTROL Split]** Aktivität verknüpft ist. Weiterführende Informationen hierzu finden Sie in diesem [Abschnitt](../../delivery/using/about-templates.md).

1. Wechseln Sie zum **[!UICONTROL Resources > Delivery template]** Ordner.
1. Duplicate the **[!UICONTROL Email]** delivery template.

   ![](assets/use_case_abtesting_deliverymodel_001.png)

1. Erstellen Sie den Inhalt Ihres Versands A.

   ![](assets/use_case_abtesting_deliverymodel_002.png)

1. Wiederholen Sie den Vorgang zur Erstellung des Versands B.

   ![](assets/use_case_abtesting_deliverymodel_003.png)

## 4. Schritt: Konfiguration der Sendungen im Workflow {#step-4--configuring-the-deliveries-in-the-workflow}

Der nächste Schritt ist die Konfiguration der Auslieferungen. Sie sind für die drei Bevölkerungsgruppen bestimmt, die in der vorherigen Phase gebildet wurden: [Schritt 2: Konfigurieren von Populationsbeispielen](#step-2--configuring-population-samples). Die ersten beiden Auslieferungen ermöglichen es Ihnen, verschiedene Inhalte an die Gruppe A und B zu senden. Die dritte Lieferung ist für die Bevölkerung bestimmt, die weder A noch B erhalten hat. Der Inhalt wird durch ein Skript berechnet und ist entweder mit A oder B identisch, je nachdem, welche die höchste offene Rate erzielt hat. Wir müssen eine Wartezeit für die dritte Lieferung konfigurieren, um das Ergebnis der Lieferungen A und B herauszufinden. Deshalb beinhaltet die dritte Lieferung auch eine **[!UICONTROL Wait]** Aktivität.

1. Go to the **[!UICONTROL Split]** activity and link the transition destined for population A to one of the email deliveries already in the workflow.

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. Öffnen Sie den Versand per Doppelklick.
1. Wählen Sie aus der Dropdown-Liste die Versandvorlage A aus.

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. Click **[!UICONTROL Continue]** to view the delivery, then save it.

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. Link the transition of the **[!UICONTROL Split]** activity destined for population B to the second email delivery.

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. Öffnen Sie den Versand, wählen Sie die Vorlage B und speichern Sie den Versand.

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. Link the transition destined for the remaining population to the **[!UICONTROL Wait]** activity.

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. Open the **[!UICONTROL Wait]** activity and configure a 5-day waiting period.

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. Verknüpfen Sie die **[!UICONTROL Wait]** Aktivität mit der **[!UICONTROL JavaScript code]** Aktivität.

   ![](assets/use_case_abtesting_createdeliveries_008.png)

## 5. Schritt: Erstellung des Scripts {#step-5--creating-the-script}

Die Auswahl der Inhaltsversion, die an die verbleibende Population gesendet wird, erfolgt mithilfe eines Scripts. Das Script ruft die Information bezüglich der höchsten Öffnungsrate ab und kopiert den Inhalt der Siegerversion in den endgültigen Versand.

### Script-Beispiel {#example-of-a-script}

Das folgende Skript kann wie im Targeting-Arbeitsablauf verwendet werden. For more on this, refer to [Implementation](#implementation).

```
 // query the database to find the winner (best open rate)
   var winner = xtk.queryDef.create(
     <queryDef schema="nms:delivery" operation="get">
       <select>
         <node expr="@id"/>
         <node expr="@label"/>
         <node expr="[@operation-id]"/>
         <node expr="[@workflow-id]"/>
       </select>
       <where>
         <condition expr={"@FCP=0 and [@workflow-id]= " + instance.id}/>
       </where>
       <orderBy>
         <node expr="[indicators/@estimatedRecipientOpenRatio]" sortDesc="true"/>
       </orderBy>
     </queryDef>).ExecuteQuery()
   
   // create a new delivery object and initialize it by doing a copy of
   // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)

   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"

   // link the delivery to the operation to make sure it will be displayed in
   // the campaign dashboard. This attribute needs to be set manually here since 
   // the Duplicate() method has reset it to its default value => 0
   delivery.operation_id = winner.@["operation-id"]
   delivery.workflow_id = winner.@["workflow-id"]

   // adjust some delivery parameters to make it compatible with the 
   // "Prepare and start" option selected in the Delivery tab of this activity
   delivery.scheduling.validationMode = "manual"
   delivery.scheduling.delayed = 0
 
   // save the delivery in database
   delivery.save()
 
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
```

Eine ausführliche Erläuterung des Skripts finden Sie unter [Details des Skripts](#details-of-the-script).

### Umsetzung {#implementation}

1. Öffnen Sie Ihre **[!UICONTROL JavaScript code]** Aktivität.
1. Kopieren Sie das unter [Beispiel eines Skripts](#example-of-a-script) angebotene Skript in das **[!UICONTROL JavaScript code]** Fenster.

   ![](assets/use_case_abtesting_configscript_002.png)

1. In the **[!UICONTROL Label]** field, enter the name of the script, i.e.

   ```
   <%= vars.deliveryId %>
   ```

   ![](assets/use_case_abtesting_configscript_003.png)

1. Schließen Sie die **[!UICONTROL JavaScript code]** Aktivität.
1. Speichern Sie den Workflow.

### Script-Details {#details-of-the-script}

Im Folgenden werden die verschiedenen Script-Abschnitte und deren Funktionsweise erläutert.

* Der erste Teil des Skripts ist eine Abfrage. The **queryDef** command lets you recover from the **NmsDelivery** table the deliveries created by executing the targeting workflow and to sort them based on their estimated rate of opens, then the information from the delivery with the highest rate of opens is recovered.

   ```
   // query the database to find the winner (best open rate)
      var winner = xtk.queryDef.create(
        <queryDef schema="nms:delivery" operation="get">
          <select>
            <node expr="@id"/>
            <node expr="@label"/>
            <node expr="[@operation-id]"/>
          </select>
          <where>
            <condition expr={"@FCP=0 and [@workflow-id]= " + instance.id}/>
          </where>
          <orderBy>
            <node expr="[indicators/@estimatedRecipientOpenRatio]" sortDesc="true"/>
          </orderBy>
        </queryDef>).ExecuteQuery()
   ```

* Der Versand mit der besten Öffnungsrate wird dupliziert.

   ```
    // create a new delivery object and initialize it by doing a copy of
    // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)
   ```

* Der Titel des duplizierten Versands wird durch Hinzufügung von **final** angepasst.

   ```
   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"
   ```

* Der Versand wird in das Kampagnen-Dashboard kopiert.

   ```
   // link the delivery to the operation to make sure it will be displayed in
   // the campaign dashboard. This attribute needs to be set manually here since 
   // the Duplicate() method has reset it to its default value => 0
   delivery.operation_id = winner.@["operation-id"]
   delivery.workflow_id = winner.@["workflow-id"]
   ```

   ```
   // adjust some delivery parameters to make it compatible with the 
   // "Prepare and start" option selected in the Delivery tab of this activity
   delivery.scheduling.validationMode = "manual"
   delivery.scheduling.delayed = 0
   ```

* Der Versand wird in der Datenbank gespeichert.

   ```
   // save the delivery in database
   delivery.save()
   ```

* Die eindeutige Kennung des duplizierten Versands wird in der Workflow-Variable gespeichert.

   ```
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
   ```

### Andere Auswahlkriterien {#other-selection-criteria}

Im zuvor dargestellten Beispiel wird die endgültige Version anhand der Öffnungsraten der Testversionen bestimmt. Es besteht jedoch die Möglichkeit, andere Kriterien zu verwenden und das Script entsprechend anzupassen:

* Best click throughput: `[indicators/@recipientClickRatio]`,
* Höchste Reaktionsrate (Öffnung der E-Mail und Klicks in der Nachricht): `[indicators/@reactivity]`,
* Lowest complaint rate: `[indicators/@refusedRatio]` (use the false value for the sortDesc attribute),
* Highest conversion rate: `[indicators/@transactionRatio]`,
* Höchste Anzahl an besuchten Webseiten nach Erhalt der Nachricht: `[indicators/@totalWebPage]`,
* Lowest unsubscription rate: `[indicators/@optOutRatio]`,
* Transaction amount: `[indicators/@amount]`.

## 6. Schritt - Ausgabeformat bestimmen {#step-6--defining-the-final-delivery}

Nachdem das Script zur Ermittlung des Gewinners des A/B-Tests erstellt wurde, können Sie die Parameter des endgültigen Versands definieren.

1. Verbinden Sie die **[!UICONTROL JavaScript code]** Aktivität mit der verbleibenden **[!UICONTROL Delivery]** Aktivität.
1. Open the **[!UICONTROL Delivery]** activity.
1. Deaktivieren Sie die **[!UICONTROL Generate an outbound transition]** Option, um den Workflow mit dieser Aktivität abzuschließen.
1. Lassen Sie die Standardwerte der anderen Optionen unverändert.

   ![](assets/ab_test_final_delivery.png)

By preparing the delivery specified in the transition (defined via the **[!UICONTROL Javascript Code]** activity), you will be then able to approve it and to start the sending, as described in the next step.

## 7. Schritt: Start des Workflows {#step-7--starting-the-workflow}

1. Click **[!UICONTROL Start]** the workflow.

   ![](assets/use_case_abtesting_startwkfl_001.png)

1. Gehen Sie in das Kampagnen-Dashboard und validieren Sie die Zielgruppen und Inhalte der Sendungen A und B.
1. Bestätigen Sie die Absendung der Nachrichten.
1. Lassen Sie die Wartezeit von fünf Tagen verstreichen, um die erfolgreichste Versandversion zu ermitteln.

   ![](assets/use_case_abtesting_startwkfl_002.png)

   Im vorliegenden Beispiel handelt es sich um die Version A.

1. Validieren Sie Zielgruppe und Inhalt der endgültigen Version und bestätigen Sie die Absendung.

## 8. Schritt: Ergebnisanalyse {#step-8--analyzing-the-result}

Nach Verarbeitung der Testsendungen besteht die Möglichkeit im Kampagnen-Dashboard zu prüfen, welche Empfänger welche Version erhalten und ob sie die Sendungen geöffnet haben. Klicken Sie auf den Link einer der Sendungen:

* To find out which recipients have been targeted, open a delivery via the campaign dashboard and click the **[!UICONTROL Delivery]** tab.

   ![](assets/use_case_abtesting_analysis_001.png)

* Im **[!UICONTROL Tracking]**-Tab wird angezeigt, welche Empfänger den Versand geöffnet haben.

   ![](assets/use_case_abtesting_analysis_002.png)

* Vergleichen Sie die Ergebnisse beider Sendungen miteinander.

   ![](assets/use_case_abtesting_analysis_003.png)

Im vorliegenden Beispiel hat der Versand A die besseren Öffnungsraten erzielt. Daher wurde der Inhalt A für den endgültigen Versand ausgewählt.

![](assets/use_case_abtesting_analysis_004.png)


---
title: Hypothesenvorlagen
seo-title: Hypothesenvorlagen
description: Hypothesenvorlagen
seo-description: null
page-status-flag: never-activated
uuid: 080417c2-1c45-4404-961e-2e660d8f0436
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: addfc395-7a85-4be1-a757-a719ed34bb33
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# Hypothesenvorlagen{#hypothesis-templates}

## Hypothesenvorlage erstellen {#creating-a-hypothesis-model}

Die Konfiguration einer Hypothesenvorlage ermöglicht die Bestimmung des Kontexts, in dem die Reaktionen auf eine Sendung oder ein Angebot gemessen werden. An dieser Stelle werden zudem die unterschiedlichen für die Messung notwendigen Tabellen verzeichnet, darunter diejenigen, die die Beziehungen zwischen Individuen, Hypothesen und Transaktionstabelle definieren.

Folgen Sie den nachstehenden Etappen, um eine Hypothesenvorlage zu erstellen:

1. Klicken Sie im Adobe Campaign-Explorer auf **[!UICONTROL Resources>Templates>Hypothesis templates]**.

   ![](assets/response_hypothesis_model_creation_001.png)

1. Click **[!UICONTROL New]** or right-click in the list of templates and choose **[!UICONTROL New]** in the drop-down list.
1. Geben Sie den Titel der Hypothese ein.
1. Specify whether the template is destined for hypotheses on offers or deliveries via the **[!UICONTROL Hypothesis type]**.
1. For **[!UICONTROL Delivery]** type templates, specify whether measurements should be carried out with or without a control group (for more on this, refer to [Properties of a hypothesis template](#properties-of-a-hypothesis-template)).
1. For **[!UICONTROL Delivery]** type templates, you can choose a specific channel or decide to apply the template to all available channels in Adobe Campaign using the **[!UICONTROL Channel]** drop-down list (for more on this, refer to [Properties of a hypothesis template](#properties-of-a-hypothesis-template)).
1. Select the **[!UICONTROL Execution folder]** in which you wish to create and automatically execute the hypotheses that will be created from this template.
1. Wählen Sie die Ausführungseinstellungen aus (weitere Informationen finden Sie unter [Einstellungen](#hypothesis-template-execution-settings)für die Ausführung von Hypothese-Vorlagen).
1. Geben Sie den Zeitraum für die Berechnung der Hypothese an (weitere Informationen dazu finden Sie unter Einstellungen für die Ausführung der [Hypothese-Vorlage](#hypothesis-template-execution-settings)).

   >[!CAUTION]
   >
   >Der Zeitraum wird ausgehend vom Kontaktdatum bestimmt.

1. In the **[!UICONTROL Transactions]** tab, specify the tables and fields required for the hypothesis calculation (for more on this, refer to [Transactions](#transactions)).
1. If your template is configured for **[!UICONTROL Offer]** type hypotheses, you can enable the **[!UICONTROL Update offer proposition status]** option: in this case, select the status of the offer proposition you want to change.
1. Specify the scope of the hypothesis application (for more on this, refer to [Hypothesis perimeter](#hypothesis-perimeter)).
1. If necessary, use a script to complete filtering (for more on this, refer to [Hypothesis perimeter](#hypothesis-perimeter)).

### Eigenschaften einer Hypothesenvorlage {#properties-of-a-hypothesis-template}

Auf der **[!UICONTROL General]** Registerkarte der Vorlage können Sie die allgemeinen Vorlagenoptionen festlegen. Die verfügbaren Felder sind:

* **[!UICONTROL Hypothesis type]**: können Sie festlegen, ob die Vorlage für Hypothesen bei Lieferungen oder Angeboten bestimmt sein soll.

   Sie können auch eine Hypothese erstellen, die sich sowohl auf Sendungen als auch auf Angebote bezieht.

   >[!NOTE]
   >
   >Wenn die Vorlage für Angebote gilt, ist die **[!UICONTROL Update offer proposition status]** Option auf der **[!UICONTROL Transactions]** Registerkarte verfügbar.

* **[!UICONTROL Measurement with control group]**: können Sie angeben, ob eine Kontrollgruppe für die Bereitstellung oder die Kampagne definiert wurde, und diese in die Messungsindikatoren einbeziehen. Mit der Kontrollgruppe, die keine Auslieferungen erhält, können Sie die Auswirkungen der Kampagne nach der Auslieferung messen, indem Sie sie mit der Zielgruppe vergleichen, die die Auslieferung erhalten hat.

   >[!NOTE]
   >
   >Wenn die Konfiguration der Vorlage eine Kontrollgruppe vorsieht, jedoch keine in dem Versand bestimmt ist, auf den sich die Hypothesen beziehen, werden die Ergebnisse nur auf Grundlage der Zielgruppen-Empfänger berechnet.

   Weitere Informationen zum Definieren und Konfigurieren einer Kontrollgruppe finden Sie unter [Definieren einer Kontrollgruppe](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

* **[!UICONTROL Channel]**: Sie können einen bestimmten Kanal auswählen oder die Hypothese-Vorlage allen Kanälen in der Adobe Campaign-Konsole zur Verfügung stellen, indem Sie sie in **[!UICONTROL All channels]** der Dropdownliste auswählen. Wenn Sie die Vorlage für einen bestimmten Kanal konfigurieren, können Sie damit automatisch Auslieferungen pro Kanal filtern, wenn Sie die Hypothese erstellen (siehe [Erstellen von Hypothesen](../../campaign/using/creating-hypotheses.md)).

   ![](assets/response_properties_001.png)

* **[!UICONTROL Execution folder]**: können Sie den Ausführungsordner für die Hypothese angeben.
* **[!UICONTROL Taken into account in campaign ROI calculation]**: berücksichtigt das hypothetische Ergebnis bei der ROI-Berechnung für die entsprechende Kampagne.

### Ausführungsparameter einer Hypothesenvorlage {#hypothesis-template-execution-settings}

Auf der **[!UICONTROL General]** Registerkarte der Vorlage können Sie auch die Parameter für die Ausführung der Hypothese angeben. Die folgenden Optionen stehen zur Verfügung:

* **[!UICONTROL Schedule execution for a time of low activity]**: können Sie den Hypothese-Start planen, um die Leistung von Adobe Campaign zu optimieren. Wenn diese Option aktiviert ist, führt der Verarbeitungsablauf für Kampagnen während der Ausfallzeit eine Hypothese aus.

   ![](assets/response_exec_settings_002.png)

* **[!UICONTROL Priority]**: auf die Hypothese angewendet, um die hypothetischen Berechnungsaufträge auszugleichen, wenn es gleichzeitig ausgeführt wird.

   ![](assets/response_exec_settings_003.png)

* **[!UICONTROL Automatic execution]**: bei Bedarf können Sie eine Hypothese-Neuberechnung planen (z. B. wenn Sie Indikatoren regelmäßig bis zum Ende der Bereitstellung aktualisieren möchten).

   ![](assets/response_exec_settings_001.png)

   Um die Häufigkeit der Aktualisierung zu bestimmen, gehen Sie wie folgt vor:

   1. Klicken Sie auf den **[!UICONTROL Frequency of execution...]** Link und dann auf die **[!UICONTROL Change...]** Schaltfläche.

      ![](assets/response_frequency_execution_001.png)

   1. Konfigurieren Sie den Häufigkeitstyp, die jeweiligen Ereignisse und den Gültigkeitszeitraum der Ereignisse.

      ![](assets/response_frequency_execution_002.png)

   1. Click **[!UICONTROL Finish]** to save the schedule.

      ![](assets/response_frequency_execution_003.png)

* **[!UICONTROL Log SQL queries in journal]**: Diese Funktion ist für erfahrene Benutzer reserviert. Damit können Sie eine Registerkarte zur Prüfung der Messhypothese hinzufügen, um SQL-Abfragen anzuzeigen. Dies ermöglicht die Erkennung möglicher Fehlfunktionen, wenn eine Simulation mit Fehlern abgeschlossen ist.
* **[!UICONTROL Keep execution workflow]**: Sie können den Workflow behalten, der automatisch zu Beginn der Hypothese erstellt wurde. In den Hypothesen, die aus einer Vorlage erstellt wurden, für die diese Option aktiviert ist, steht der generierte Workflow zur Verfügung, um den Prozess zu verfolgen.

   >[!CAUTION]
   >
   >Diese Option sollte nur zu Debugging-Zwecken bei fehlerhaften Hypothesenausführungen aktiviert werden.\
   >Automatisch generierte Workflows sollten zudem nicht verändert werden. Jede dennoch vorgenommene Änderung wird nur für nachfolgende Berechnungen berücksichtigt.\
   >Denken Sie daran, den Workflow nach seiner Ausführung zu löschen, wenn Sie diese Option aktiviert haben.

### Transactions {#transactions}

Dieser Tab enthält die unterschiedlichen Felder und Tabellen, die den Verlauf der Empfängerreaktionen in Form von Transaktionen speichern. Weiterführende Informationen über die der Reaktionsverwaltung dedizierten Tabellen erhalten Sie im [Konfigurationshandbuch](../../configuration/using/about-schema-reference.md).

* **[!UICONTROL Schema (reaction log storage)]**: Wählen Sie die Reaktionstabelle des Empfängers aus. Die vordefinierte Tabelle in Adobe Campaign lautet **NmsRemaMatchRcp**.
* **[!UICONTROL Transaction schema]**: Wählen Sie die Tabelle aus, die die Hypothesen betreffen, d.h. die Transaktion oder die Kauftabelle.
* **[!UICONTROL Querying schema]**: die Kriterien zum Filtern der Hypothese auswählen.
* **[!UICONTROL Link to individuals]**: Wählen Sie die Verknüpfung zwischen Einzelpersonen und der als Transaktionsschema verwendeten Tabelle.
* **[!UICONTROL Link to the household]**: Wählen Sie den Link zum Haushalt im Transaktionsschema aus, wenn Sie alle Mitglieder eines Haushalts in eine Hypothese einbeziehen möchten. Dieses Feld ist optional.
* **[!UICONTROL Transaction date]**: Dieses Feld ist optional, wird jedoch empfohlen, da Sie damit einen Bereich für die Hypothese definieren können.
* **[!UICONTROL Measurement period]**: können Sie Start- und Enddaten konfigurieren, während denen Hypothesen ausgeführt und Kaufzeilen wiederhergestellt werden.

   Wenn eine Hypothese einem Versand zugeordnet wird, wird die Messung automatisch einige Tage nach dem Kontaktdatum (im Fall eines Briefpost-Versands) oder nach dem Versanddatum (im Fall eines E-Mail- oder SMS-Versands) ausgelöst.

   ![](assets/response_measurement_001.png)

   Wenn die Hypothese von vornherein gestartet wird, kann sie erzwungen werden, wenn sie sofort ausgelöst werden soll. Andernfalls wird sie automatisch auf Grundlage des konfigurierten Berechnungsdatums ausgelöst, das auf dem Erstellungsdatum der Hypothese basiert (siehe [Erstellen einer Hypothese im Handumdrehen bei Lieferung](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)).

* **[!UICONTROL Transaction/Margin amount]**: Diese Felder sind optional und ermöglichen die automatische Berechnung von Umsatzindikatoren (siehe [Indikatoren](../../campaign/using/hypothesis-tracking.md#indicators)).
* **[!UICONTROL Unit amount]**: können Sie einen Betrag zur Berechnung des Umsatzes festlegen (siehe [Indikatoren](../../campaign/using/hypothesis-tracking.md#indicators)).

   ![](assets/response_transactions_001.png)

* **[!UICONTROL Additional measures and data]**: können Sie zusätzliche Berichtsmaße oder Achsen aus Feldern in den verschiedenen Tabellen angeben.
* **[!UICONTROL Update offer proposition status]**: können Sie den Status des Angebotsprojektes ändern, wenn ein Angebotempfänger durch die Hypothese identifiziert wird.

   ![](assets/response_offer_status_001.png)

### Perimeter {#hypothesis-perimeter}

Nachdem die Transkationstabelle sowie die von der Hypothese betroffenen Felder definiert wurden, können Sie den Perimeter Ihrer Hypothese weiter einschränken, indem Sie die betreffenden Transaktionen und Sendungen mithilfe von Filtern angeben. Sie haben auch die Möglichkeit, ein JavaScript zu verwenden, um ein in der Transaktionstabelle referenziertes Produkt, für das Sie eine Hypothese erstellen möchten, explizit anzugeben.

* **Filtern nach Transaktionen**: auf der **[!UICONTROL Scope]** Registerkarte können Sie einen Filter auf die Hypothese konfigurieren. Gehen Sie dazu wie folgt vor:

   1. Klicken Sie auf den **[!UICONTROL Edit query]** Link.

      ![](assets/response_scope_filtering_001.png)

   1. Bestimmen Sie die gewünschten Filterkriterien.

      ![](assets/response_scope_filtering_002.png)

   1. Wählen Sie die Transaktion aus, auf die die Hypothese sich beziehen soll.

      ![](assets/response_scope_filtering_003.png)

* **Filtern nach Empfängern**: auf der **[!UICONTROL Scope]** Registerkarte können Sie Ihre Hypothese auf alle Informationen beschränken, die mit einer Nachricht verknüpft sind (Lieferung, Empfänger, E-Mail-Adresse, Dienst usw.):

   1. Klicken Sie auf den **[!UICONTROL Add a filter]** Link und dann **[!UICONTROL Edit query]**.

      ![](assets/response_scope_filtering_004.png)

   1. Bestimmen Sie die gewünschten Filterkriterien.

      ![](assets/response_scope_filtering_005.png)

   1. Click **[!UICONTROL Finish]** to save your query.

      ![](assets/response_scope_filtering_006.png)

* **Script**: Mithilfe eines JavaScripts besteht die Möglichkeit, die Parameter der Hypothese bei ihrer Ausführung dynamisch zu überschreiben.

   To do this, click the **[!UICONTROL Advanced settings]** link then enter the desired script.

   >[!NOTE]
   >
   >Diese Option sollte erfahrenen Benutzern vorbehalten bleiben.

   ![](assets/response_hypothesis_model_creation_011.png)

## Beispiel: Erstellen einer Hypothesenvorlage für einen Versand {#example--creating-a-hypothesis-template-on-a-delivery}

Im folgenden Beispiel wird eine Hypothesenvorlage für einen Briefpost-Versand erstellt. Die Transaktionstabelle (**Bestellungen** in unserem Beispiel), auf welcher die Hypothesen basieren, enthält Bestellzeilen, denen Produkte zugeordnet sind. Die Vorlage wird so konfiguriert, dass die Hypothesen sich auf eben diese Produkte bezieht.

1. Wechseln Sie im Adobe Campaign-Explorer zum **[!UICONTROL Resources > Templates > Hypothesis templates]** Knoten.
1. Click **[!UICONTROL New]** to create a template.

   ![](assets/response_hypothesis_model_example_001.png)

1. Ändern Sie den Titel der Vorlage.

   ![](assets/response_hypothesis_model_example_002.png)

1. Select **[!UICONTROL Deliveries]** as a hypothesis type.
1. Geben Sie an, dass der Versand eine Kontrollgruppe enthalten kann, indem Sie das entsprechende Feld ankreuzen.
1. Wählen Sie den **[!UICONTROL Direct mail]** Kanal aus.

   >[!NOTE]
   >
   >Da die Vorlage briefversandspezifisch ist, können die basierend auf dieser Vorlage erstellten Hypothesen keinen Sendungen zugeordnet werden, die andere Kanäle nutzen.

1. In the **[!UICONTROL Transactions]** tab, select the recipient reactions table.

   ![](assets/response_hypothesis_model_example_006.png)

1. In the **[!UICONTROL Transactions schema]** field, choose your purchase table.

   ![](assets/response_hypothesis_model_example_007.png)

1. Wählen Sie im **[!UICONTROL Querying schema]** Feld Kaufzeilen aus.

   ![](assets/response_hypothesis_model_example_008.png)

1. Wählen Sie die Empfänger aus, die mit der Tabelle der Bestellungen in Relation stehen.

   ![](assets/response_hypothesis_model_example_009.png)

1. Wählen Sie das dem Bestelldatum entsprechende Feld aus, um die Hypothesen zeitlich zu beschränken.

   Diese Etappe ist nicht zwingend erforderlich, sie wird jedoch empfohlen.

   ![](assets/response_hypothesis_model_example_010.png)

1. Konfigurieren Sie einen Berechnungszeitraum zwischen 5 und 25 Tagen.

   ![](assets/response_hypothesis_model_example_005.png)

1. In the **[!UICONTROL Scope]** tab, click **[!UICONTROL Edit query]** to create a filter on hypotheses.

   ![](assets/response_hypothesis_model_example_011.png)

   Die auf diese Weise erstellte Vorlage ermöglicht es Ihnen, Hypothesen für in Ihrer Bestellungen-Tabelle enthaltene Produkte zu erstellen.

1. Click **[!UICONTROL Save]** to record your template.


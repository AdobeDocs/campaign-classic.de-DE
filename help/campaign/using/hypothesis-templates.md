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
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '1566'
ht-degree: 100%

---


# Hypothesenvorlagen{#hypothesis-templates}

## Hypothesenvorlage erstellen {#creating-a-hypothesis-model}

Die Konfiguration einer Hypothesenvorlage ermöglicht die Bestimmung des Kontexts, in dem die Reaktionen auf eine Sendung oder ein Angebot gemessen werden. An dieser Stelle werden zudem die unterschiedlichen für die Messung notwendigen Tabellen verzeichnet, darunter diejenigen, die die Beziehungen zwischen Individuen, Hypothesen und Transaktionstabelle definieren.

Folgen Sie den nachstehenden Etappen, um eine Hypothesenvorlage zu erstellen:

1. Rufen Sie im Adobe-Campaign-Explorer den Verzeichnisknoten **[!UICONTROL Ressourcen > Vorlagen > Hypothesenvorlagen]** auf.

   ![](assets/response_hypothesis_model_creation_001.png)

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Neu]** oder machen Sie einen Rechtsklick in die Liste der Vorlagen und wählen Sie im Kontextmenü **[!UICONTROL Neu]** aus.
1. Geben Sie den Titel der Hypothese ein.
1. Wählen Sie im Feld **[!UICONTROL Hypothesentyp]** aus, ob die Vorlage für Hypothesen über Angebote oder Sendungen bestimmt ist.
1. Falls es sich um eine Vorlage vom Typ **[!UICONTROL Sendungen]** handelt, geben Sie an, ob die Messung mit oder ohne Kontrollgruppe stattfindet (siehe hierzu den Abschnitt [Eigenschaften einer Hypothesenvorlage](#properties-of-a-hypothesis-template)).
1. Für eine Vorlage vom Typ **[!UICONTROL Sendungen]** können Sie mithilfe der Dropdown-Liste **[!UICONTROL Kanal]** einen bestimmten oder alle in Adobe Campaign verfügbaren Kanäle auswählen (siehe hierzu den Abschnitt [Eigenschaften einer Hypothesenvorlage](#properties-of-a-hypothesis-template)).
1. Wählen Sie den **[!UICONTROL Ausführungsordner]**, in dem Sie die basierend auf der Vorlage aufgestellten Hypothesen erstellen und automatisch ausführen möchten.
1. Wählen Sie die Ausführungsparameter aus (weitere Informationen finden Sie unter [Ausführungsparameter einer Hypothesenvorlage](#hypothesis-template-execution-settings)).
1. Geben Sie den Berechnungszeitraum der Hypothese an (weitere Informationen finden Sie unter [Ausführungsparameter einer Hypothesenvorlage](#hypothesis-template-execution-settings)).

   >[!CAUTION]
   >
   >Der Zeitraum wird ausgehend vom Kontaktdatum bestimmt.

1. Geben Sie im Tab **[!UICONTROL Transaktionen]** die Tabellen und Felder an, die zur Berechnung der Hypothese benötigt werden (weitere Informationen finden Sie unter [Transaktionen](#transactions)).
1. Wenn Ihre Vorlage für Hypothesen vom Typ **[!UICONTROL Angebote]** konfiguriert ist, können Sie die Option **[!UICONTROL Vorschlagsstatus aktualisieren]** aktivieren: Wählen Sie in diesem Fall den Vorschlagsstatus aus, den Sie verändern möchten.
1. Geben Sie den Perimeter der Hypothesenanwendung an (weitere Informationen finden Sie unter [Perimeter](#hypothesis-perimeter)).
1. Vervollständigen Sie bei Bedarf die Filterung mithilfe eines Skripts (weitere Informationen finden Sie unter [Perimeter ](#hypothesis-perimeter)).

### Eigenschaften einer Hypothesenvorlage {#properties-of-a-hypothesis-template}

Im Tab **[!UICONTROL Allgemein]** der Vorlage werden die allgemeinen Optionen der Vorlage festgelegt. Es sind folgende Felder verfügbar:

* **[!UICONTROL Hypothesentyp]**: Wählen Sie hier aus, ob die Vorlage für Hypothesen über Sendungen oder über Angebote bestimmt ist.

   Sie können auch eine Hypothese erstellen, die sich sowohl auf Sendungen als auch auf Angebote bezieht.

   >[!NOTE]
   >
   >Wenn die Vorlage sich auf Angebote bezieht, wird die Option **[!UICONTROL Vorschlagsstatus aktualisieren]** im Tab **[!UICONTROL Transaktionen]** verfügbar.

* **[!UICONTROL Messung mit Kontrollgruppe]**: Aktivieren Sie diese Option, wenn eine Kontrollgruppe für den jeweiligen Versand oder die jeweilige Kampagne erstellt wurde und diese in den Messindikatoren berücksichtigt werden soll. Die Kontrollgruppe erhält keine Sendungen: Sie dient der Messung der Auswirkung dieser durch den Vergleich mit dem Verhalten der Zielgruppe, die die Sendungen erhält.

   >[!NOTE]
   >
   >Wenn die Konfiguration der Vorlage eine Kontrollgruppe vorsieht, jedoch keine in dem Versand bestimmt ist, auf den sich die Hypothesen beziehen, werden die Ergebnisse nur auf Grundlage der Zielgruppen-Empfänger berechnet.

   Weitere Informationen zum Definieren und Konfigurieren einer Kontrollgruppe finden Sie unter [Kontrollgruppen festlegen](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

* **[!UICONTROL Kanal]**: Sie können einen bestimmten Kanal auswählen oder die Hypothese-Vorlage für alle Kanäle in der Adobe Campaign-Konsole verfügbar machen, indem Sie in der Dropdown-Liste **[!UICONTROL Alle Kanäle]** auswählen. Wenn Sie die Vorlage für einen bestimmten Kanal konfigurieren, können Sie damit automatisch Sendungen pro Kanal filtern, wenn Sie die Hypothese erstellen (siehe [Hypothesenerstellung](../../campaign/using/creating-hypotheses.md)).

   ![](assets/response_properties_001.png)

* **[!UICONTROL Ausführungsordner]**: Legen Sie hier den Ordner fest, in dem die Hypothese erstellt und ausgeführt werden soll.
* **[!UICONTROL In der Berechnung des Kampagnen-ROIs berücksichtigen]**: Diese Option ermöglicht es, das Ergebnis der Hypothese in der Berechnung des ROIs der verbundenen Kampagne zu berücksichtigen (im Fall eines Kampagnenversands).

### Ausführungsparameter einer Hypothesenvorlage {#hypothesis-template-execution-settings}

Im Tab **[!UICONTROL Allgemein]** der Vorlage können zudem die Ausführungsparameter der Hypothese festgelegt werden. Folgende Optionen sind verfügbar:

* **[!UICONTROL Ausführung auf einen Zeitpunkt mit geringer Auslastung verschieben]**: Diese Option dient der Leistungsoptimierung von Adobe Campaign. Bei Aktivierung der Option verschiebt der Workflow der Kampagnenvorgänge den Start der Hypothesenberechnung auf einen Zeitraum mit schwacher Aktivität.

   ![](assets/response_exec_settings_002.png)

* **[!UICONTROL Priorität]**: Im Falle simultaner Ausführungen kann mithilfe der Prioritätseinteilung die Reihenfolge der Hypothesenberechnungen gestaffelt werden.

   ![](assets/response_exec_settings_003.png)

* **[!UICONTROL Automatische Ausführung]**: Mit dieser Option kann bei Bedarf eine erneute Berechnung der Hypothese geplant werden (z. B. wenn eine regelmäßige Aktualisierung der Indikatoren bis zum Ende eines Versands gewünscht ist).

   ![](assets/response_exec_settings_001.png)

   Um die Häufigkeit der Aktualisierung zu bestimmen, gehen Sie wie folgt vor:

   1. Klicken Sie auf den Link **[!UICONTROL Ausführungsfrequenz...]** und anschließend auf die Schaltfläche **[!UICONTROL Ändern]**.

      ![](assets/response_frequency_execution_001.png)

   1. Konfigurieren Sie den Häufigkeitstyp, die jeweiligen Ereignisse und den Gültigkeitszeitraum der Ereignisse.

      ![](assets/response_frequency_execution_002.png)

   1. Klicken Sie zur Bestätigung Ihrer Eingaben auf **[!UICONTROL Beenden]**.

      ![](assets/response_frequency_execution_003.png)

* **[!UICONTROL SQL-Abfragen im Protokoll speichern]**: Diese Funktion sollte erfahrenen Benutzern vorbehalten bleiben. Sie fügt der Verfolgung der Messhypothesen einen Tab hinzu, in dem SQL-Abfragen angezeigt werden. Dies ermöglicht es, mögliche Fehlfunktionen ausfindig zu machen, wenn eine Simulation mit Fehlern beendet wird.
* **[!UICONTROL Ausführungs-Workflow beibehalten]**: Diese Option ermöglicht es, den beim Start der Hypothesenberechnung automatisch erzeugten Workflow beizubehalten. In Hypothesen, die basierend auf einer Vorlage mit dieser Option erstellt werden, besteht zur Beobachtung des Ablaufs Zugriff auf den Workflow.

   >[!CAUTION]
   >
   >Diese Option sollte nur zu Debugging-Zwecken bei fehlerhaften Hypothesenausführungen aktiviert werden.\
   >Automatisch generierte Workflows sollten zudem nicht verändert werden. Jede dennoch vorgenommene Änderung wird nur für nachfolgende Berechnungen berücksichtigt.\
   >Denken Sie daran, den Workflow nach seiner Ausführung zu löschen, wenn Sie diese Option aktiviert haben.

### Transactions {#transactions}

Dieser Tab enthält die unterschiedlichen Felder und Tabellen, die den Verlauf der Empfängerreaktionen in Form von Transaktionen speichern. Weiterführende Informationen über die der Reaktionsverwaltung dedizierten Tabellen erhalten Sie im [Konfigurationshandbuch](../../configuration/using/about-schema-reference.md).

* **[!UICONTROL Schema (Speicherung des Reaktionslogs)]**: Geben Sie die Tabelle der Empfängerreaktionen an. Die standardmäßige Adobe-Campaign-Tabelle hierfür ist **NmsRemaMatchRcp**.
* **[!UICONTROL Transaktionsschema]**: Wählen Sie die Tabelle aus, auf die sich die Hypothesen beziehen sollen (also die die Bestellungen enthaltende Transaktionstabelle).
* **[!UICONTROL Abfrageschema]**: Wählen Sie Kriterien zur Filterung der Hypothese aus.
* **[!UICONTROL Relation zu den Individuen]**: Geben Sie die Relation zwischen den Individuen und der als Transaktionschema ausgewählten Tabelle an.
* **[!UICONTROL Relation zum Haushalt]**: Wählen Sie die Relation mit dem Haushalt im Transaktionsschema aus, wenn Sie alle Mitglieder eines Haushalts in Ihre Hypothese integrieren möchten. Dieses Feld ist optional.
* **[!UICONTROL Transaktionsdatum]**: Dieses Feld ist optional. Seine Nutzung wird jedoch empfohlen, da es die Begrenzung des Perimeters der Hypothesenberechnung ermöglicht.
* **[!UICONTROL Zeitraum der Hypothesenberechnung]**: Sie können Anfang und Ende des Zeitraums konfigurieren, während dem die Hypothesen ausgeführt und die Bestellzeilen abgerufen werden.

   Wenn eine Hypothese einem Versand zugeordnet wird, wird die Messung automatisch einige Tage nach dem Kontaktdatum (im Fall eines Briefpost-Versands) oder nach dem Versanddatum (im Fall eines E-Mail- oder SMS-Versands) ausgelöst.

   ![](assets/response_measurement_001.png)

   Wenn die Hypothese ohne Vorbereitung gestartet wird, kann sie erzwungen werden, wenn sie sofort ausgelöst werden soll. Andernfalls wird sie automatisch auf Grundlage des konfigurierten Berechnungsdatums ausgelöst, das auf dem Erstellungsdatum der Hypothese basiert (siehe [Erstellen einer Hypothese direkt in einem Versand](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)).

* **[!UICONTROL Transaktionsbetrag/Betrag der Spanne]**: Diese Felder sind optional. Sie ermöglichen die automatische Berechnung der Umsatzindikatoren (siehe [Indikatoren](../../campaign/using/hypothesis-tracking.md#indicators)).
* **[!UICONTROL Stückbetrag]**: Dieses Feld ermöglicht die Festsetzung eines Betrags für die Berechnung der Umsatzindikatoren (siehe Indikatoren[](../../campaign/using/hypothesis-tracking.md#indicators)).

   ![](assets/response_transactions_001.png)

* **[!UICONTROL Ergänzende Messungen und Daten]**: In diesem Feld werden zusätzliche Messungen und Berichtsachsen basierend auf den Feldern der unterschiedlichen Tabellen bestimmt.
* **[!UICONTROL Vorschlagsstatus aktualisieren]**: Diese Option ermöglicht die Änderung eines Vorschlagsstatus, wenn ein Angebotsempfänger von der Hypothese identifiziert wurde.

   ![](assets/response_offer_status_001.png)

### Perimeter {#hypothesis-perimeter}

Nachdem die Transkationstabelle sowie die von der Hypothese betroffenen Felder definiert wurden, können Sie den Perimeter Ihrer Hypothese weiter einschränken, indem Sie die betreffenden Transaktionen und Sendungen mithilfe von Filtern angeben. Sie haben auch die Möglichkeit, ein JavaScript zu verwenden, um ein in der Transaktionstabelle referenziertes Produkt, für das Sie eine Hypothese erstellen möchten, explizit anzugeben.

* **Filterung der Transaktionen**: Im Tab **[!UICONTROL Perimeter]** können Sie Filter für die Transaktionen erstellen. Gehen Sie hierzu wie folgt vor:

   1. Klicken Sie auf den Link **[!UICONTROL Abfrage bearbeiten...]**.

      ![](assets/response_scope_filtering_001.png)

   1. Bestimmen Sie die gewünschten Filterkriterien.

      ![](assets/response_scope_filtering_002.png)

   1. Wählen Sie die Transaktion aus, auf die die Hypothese sich beziehen soll.

      ![](assets/response_scope_filtering_003.png)

* **Empfängerfilter**: Im Tab **[!UICONTROL Perimeter]** können Sie Ihre Hypothese auf jegliche, in Zusammenhang mit einer Nachricht stehende Information beschränken (Versand, Empfänger, E-Mail-Adresse, Dienst etc.). Gehen Sie hierzu wie folgt vor:

   1. Klicken Sie auf den Link **[!UICONTROL Filter hinzufügen]** und anschließend auf **[!UICONTROL Abfrage bearbeiten]**.

      ![](assets/response_scope_filtering_004.png)

   1. Bestimmen Sie die gewünschten Filterkriterien.

      ![](assets/response_scope_filtering_005.png)

   1. Klicken Sie auf **[!UICONTROL Beenden]**, um Ihre Abfrage zu speichern.

      ![](assets/response_scope_filtering_006.png)

* **Script**: Mithilfe eines JavaScripts besteht die Möglichkeit, die Parameter der Hypothese bei ihrer Ausführung dynamisch zu überschreiben.

   Klicken Sie hierzu auf den Link **[!UICONTROL Erweiterte Parameter...]** und erfassen Sie das Script Ihrer Wahl.

   >[!NOTE]
   >
   >Diese Option sollte erfahrenen Benutzern vorbehalten bleiben.

   ![](assets/response_hypothesis_model_creation_011.png)

## Beispiel: Erstellen einer Hypothesenvorlage für einen Versand {#example--creating-a-hypothesis-template-on-a-delivery}

Im folgenden Beispiel wird eine Hypothesenvorlage für einen Briefpost-Versand erstellt. Die Transaktionstabelle (**Bestellungen** in unserem Beispiel), auf welcher die Hypothesen basieren, enthält Bestellzeilen, denen Produkte zugeordnet sind. Die Vorlage wird so konfiguriert, dass die Hypothesen sich auf eben diese Produkte bezieht.

1. Positionieren Sie sich im Knoten **[!UICONTROL Ressourcen > Vorlagen > Hypothesenvorlagen]** des Adobe-Campaign-Explorers.
1. Klicken Sie auf **[!UICONTROL Neu]**, um eine Vorlage zu erstellen.

   ![](assets/response_hypothesis_model_example_001.png)

1. Ändern Sie den Titel der Vorlage.

   ![](assets/response_hypothesis_model_example_002.png)

1. Wählen Sie den Hypothesentyp **[!UICONTROL Sendungen]**.
1. Geben Sie an, dass der Versand eine Kontrollgruppe enthalten kann, indem Sie das entsprechende Feld ankreuzen.
1. Wählen Sie den Kanal **[!UICONTROL Briefpost]**.

   >[!NOTE]
   >
   >Da die Vorlage briefversandspezifisch ist, können die basierend auf dieser Vorlage erstellten Hypothesen keinen Sendungen zugeordnet werden, die andere Kanäle nutzen.

1. Geben Sie im Tab **[!UICONTROL Transaktionen]** die Empfängerreaktionen-Tabelle an.

   ![](assets/response_hypothesis_model_example_006.png)

1. Wählen Sie im Feld **[!UICONTROL Transaktionsschema]** Ihre die Bestellung enthaltende Transaktionstabelle aus.

   ![](assets/response_hypothesis_model_example_007.png)

1. Wählen Sie im Feld **[!UICONTROL Abfrageschema]** Bestellzeilen aus.

   ![](assets/response_hypothesis_model_example_008.png)

1. Wählen Sie die Empfänger aus, die mit der Tabelle der Bestellungen in Relation stehen.

   ![](assets/response_hypothesis_model_example_009.png)

1. Wählen Sie das dem Bestelldatum entsprechende Feld aus, um die Hypothesen zeitlich zu beschränken.

   Diese Etappe ist nicht zwingend erforderlich, sie wird jedoch empfohlen.

   ![](assets/response_hypothesis_model_example_010.png)

1. Konfigurieren Sie einen Berechnungszeitraum zwischen 5 und 25 Tagen.

   ![](assets/response_hypothesis_model_example_005.png)

1. Klicken Sie im Tab **[!UICONTROL Perimeter]** auf **[!UICONTROL Abfrage bearbeiten]**, um einen Hypothesenfilter zu erstellen.

   ![](assets/response_hypothesis_model_example_011.png)

   Die auf diese Weise erstellte Vorlage ermöglicht es Ihnen, Hypothesen für in Ihrer Bestellungen-Tabelle enthaltene Produkte zu erstellen.

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Erstellung der Vorlage zu beenden.


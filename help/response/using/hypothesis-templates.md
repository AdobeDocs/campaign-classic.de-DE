---
product: campaign
title: Hypothesenvorlagen
description: Erfahren Sie, wie Sie Hypothesenvorlagen in Campaign Response Manager erstellen.
feature: Campaigns, Templates
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 428c7677-454b-4618-bae7-0be7df6dfcaa
TQID: https://experienceleague.adobe.com/FKf9pDlOZI1NEhwmdSpcpvEbNsT28wEvgy81TBEQQgo
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
subfeature_v2:
  - id: d72afaa0-c842-48c8-9a3c-51b7911edc1b
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 1539
ht-degree: 74%

---

# Hypothesenvorlagen{#hypothesis-templates}



## Hypothesenvorlage erstellen {#creating-a-hypothesis-model}

Durch die Konfiguration der Hypothesenvorlage können Sie den Kontext für die Messung von Reaktionen definieren, unabhängig davon, ob es sich um einen Versand oder ein Angebot handelt. Hier werden die verschiedenen Messtabellen referenziert, einschließlich derjenigen zur Definition der Beziehungen zwischen Personen, Hypothesen und der Transaktionstabelle.

Folgen Sie den nachstehenden Etappen, um eine Hypothesenvorlage zu erstellen:

1. Rufen Sie im Adobe Campaign-Explorer den Verzeichnisknoten **[!UICONTROL Ressourcen > Vorlagen > Hypothesenvorlagen]** auf.

   ![](assets/response_hypothesis_model_creation_001.png)

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Neu]** oder machen Sie einen Rechtsklick in die Liste der Vorlagen und wählen Sie im Kontextmenü **[!UICONTROL Neu]** aus.
1. Geben Sie den Titel der Hypothese ein.
1. Wählen Sie im Feld **[!UICONTROL Hypothesentyp]** aus, ob die Vorlage für Hypothesen über Angebote oder Sendungen bestimmt ist.
1. Geben Sie für Vorlagen vom Typ **[!UICONTROL Versand]** an, ob die Messungen mit oder ohne Kontrollgruppe durchgeführt werden sollen. [Weitere Informationen](#properties-of-a-hypothesis-template)
1. Für eine Vorlage vom Typ **[!UICONTROL Versand]** können Sie mithilfe der Dropdown-Liste **[!UICONTROL Kanal]** einen bestimmten Kanal wählen oder die Vorlage auf alle in Adobe Campaign verfügbaren Kanäle anwenden. [Weitere Informationen](#properties-of-a-hypothesis-template)
1. Wählen Sie den **[!UICONTROL Ausführungsordner]**, in dem Sie die basierend auf der Vorlage aufgestellten Hypothesen erstellen und automatisch ausführen möchten.
1. Wählen Sie die Ausführungseinstellungen aus. [Weitere Informationen](#hypothesis-template-execution-settings)
1. Geben Sie den Berechnungszeitraum der Hypothese an. [Weitere Informationen](#hypothesis-template-execution-settings)

   >[!CAUTION]
   >
   >Der Zeitraum wird ausgehend vom Kontaktdatum bestimmt.

1. Geben Sie im Tab **[!UICONTROL Transaktionen]** die Tabellen und Felder an, die für die Hypothesenberechnung erforderlich sind. [Weitere Informationen](#transactions)
1. Wenn Ihre Vorlage für Hypothesen vom Typ **[!UICONTROL Angebote]** konfiguriert ist, können Sie die Option **[!UICONTROL Vorschlagsstatus aktualisieren]** aktivieren: Wählen Sie in diesem Fall den Vorschlagsstatus aus, den Sie verändern möchten.
1. Geben Sie den Umfang der Hypothesenanwendung an. [Weitere Informationen](#hypothesis-perimeter)
1. Verwenden Sie bei Bedarf ein Skript, um die Filterung abzuschließen. [Weitere Informationen](#hypothesis-perimeter)

### Eigenschaften einer Hypothesenvorlage {#properties-of-a-hypothesis-template}

Auf der Registerkarte **[!UICONTROL Allgemein]** der Vorlage können Sie die allgemeinen Vorlagenoptionen angeben. Die verfügbaren Felder sind:

* **[!UICONTROL Hypothesentyp]**: Wählen Sie hier aus, ob die Vorlage für Hypothesen über Sendungen oder über Angebote bestimmt ist.

  Sie können auch eine Hypothese erstellen, die sich sowohl auf Sendungen als auch auf Angebote bezieht.

  >[!NOTE]
  >
  >Wenn die Vorlage sich auf Angebote bezieht, wird die Option **[!UICONTROL Vorschlagsstatus aktualisieren]** im Tab **[!UICONTROL Transaktionen]** verfügbar.

* **[!UICONTROL Messung mit Kontrollgruppe]**: Hiermit können Sie angeben, ob eine Kontrollgruppe für den Versand oder die Kampagne definiert wurde, und diese in Messindikatoren einbeziehen. Die Kontrollgruppe, die keine Sendungen erhält, ermöglicht es, die Wirkung der Kampagne nach dem Versand zu messen, indem sie sie mit der Zielpopulation vergleicht, die den Versand erhalten hat.

  >[!NOTE]
  >
  >Wenn die Konfiguration der Vorlage eine Kontrollgruppe vorsieht, jedoch keine in dem Versand bestimmt ist, auf den sich die Hypothesen beziehen, werden die Ergebnisse nur auf Grundlage der Zielgruppen-Empfänger berechnet.

  Weitere Informationen zum Definieren und Konfigurieren einer Kontrollgruppe finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html?lang=de#add-a-control-group){target=_blank}.

* **[!UICONTROL Kanal]**: Sie können einen bestimmten Kanal auswählen oder die Hypothese-Vorlage für alle Kanäle in der Adobe Campaign-Konsole verfügbar machen, indem Sie in der Dropdown-Liste **[!UICONTROL Alle Kanäle]** auswählen. Wenn Sie die Vorlage für einen bestimmten Kanal konfigurieren, können die Sendungen bei der Hypothesenerstellung automatisch nach Kanal gefiltert werden. [Weitere Informationen](creating-hypotheses.md)

  ![](assets/response_properties_001.png)

* **[!UICONTROL Ausführungsordner]**: Legen Sie hier den Ordner fest, in dem die Hypothese erstellt und ausgeführt werden soll.
* **[!UICONTROL In der Berechnung des Kampagnen-ROIs berücksichtigen]**: Diese Option ermöglicht es, das Ergebnis der Hypothese in der Berechnung des ROIs der verbundenen Kampagne zu berücksichtigen (im Fall eines Kampagnenversands).

### Ausführungsparameter einer Hypothesenvorlage {#hypothesis-template-execution-settings}

Auf der Registerkarte **[!UICONTROL Allgemein]** der Vorlage können Sie auch die Ausführungsparameter der Hypothese angeben. Folgende Optionen sind verfügbar:

* **[!UICONTROL Ausführung auf einen Zeitpunkt mit geringer Aktivität planen]** ermöglicht es Ihnen, den Hypothesenstart zu planen, um die Leistung von Adobe Campaign zu optimieren. Wenn diese Option aktiviert ist, führt der Verarbeitungs-Workflow für Kampagnen die Hypothesenberechnung während der Ausfallzeit durch.

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

* **[!UICONTROL SQL-Abfragen im Protokoll speichern]**: Diese Funktion ist erfahrenen Benutzern vorbehalten. Damit können Sie dem Audit der Messhypothese eine Registerkarte hinzufügen, um SQL-Abfragen anzuzeigen. Dies ermöglicht die Erkennung möglicher Fehlfunktionen, falls eine Simulation mit Fehlern beendet wird.
* **[!UICONTROL Ausführungs-Workflow beibehalten]** ermöglicht es Ihnen, den Workflow beizubehalten, der automatisch zu Beginn der Hypothesenberechnung generiert wurde. In den Hypothesen, die aus einer Vorlage erstellt wurden, in der diese Option aktiviert ist, steht der generierte Workflow zur Verfügung, um den Prozess zu verfolgen.

  >[!CAUTION]
  >
  >Diese Option sollte nur zu Debugging-Zwecken bei fehlerhaften Hypothesenausführungen aktiviert werden.\
  >Darüber hinaus dürfen automatisch generierte Workflows nicht geändert werden. Eventuelle Änderungen würden bei späteren Berechnungen an anderer Stelle nicht berücksichtigt.\
  >Denken Sie daran, den Workflow nach seiner Ausführung zu löschen, wenn Sie diese Option aktiviert haben.

### Transactions {#transactions}

Dieser Tab enthält Felder und Tabellen, mithilfe derer Sie den Verlauf der Empfängerreaktionen bei Transaktionen speichern können. Weiterführende Informationen zu den für die Reaktionsverwaltung verwendeten Tabellen finden Sie in diesem [Abschnitt](../../configuration/using/about-schema-reference.md).

* **[!UICONTROL Schema (Speicherung des Reaktionslogs)]**: Wählen Sie die Empfängerreaktionstabelle aus. Die standardmäßige Adobe Campaign-Tabelle hierfür ist **NmsRemaMatchRcp**.
* **[!UICONTROL Transaktionsschema]**: Wählen Sie die Tabelle aus, auf die sich die Hypothesen beziehen sollen (also die die Käufe enthaltende Transaktionstabelle).
* **[!UICONTROL Abfrageschema]**: Wählen Sie Kriterien zur Filterung der Hypothese aus.
* **[!UICONTROL Relation zu den Individuen]**: Geben Sie die Relation zwischen den Individuen und der als Transaktionschema ausgewählten Tabelle an.
* **[!UICONTROL Mit dem Haushalt verknüpfen]**: Wählen Sie die Verknüpfung mit dem Haushalt im Transaktionsschema aus, wenn Sie alle Mitglieder eines Haushalts in eine Hypothese einbeziehen möchten. Dieses Feld ist optional.
* **[!UICONTROL Transaktionsdatum]**: Dieses Feld ist optional. Seine Nutzung wird jedoch empfohlen, da es die Begrenzung des Perimeters der Hypothesenberechnung ermöglicht.
* **[!UICONTROL Zeitraum der Hypothesenberechnung]**: Sie können Start- und Enddatum des Zeitraums konfigurieren, während dem die Hypothesen ausgeführt und die Bestellzeilen abgerufen werden.

  Wenn eine Hypothese einem Versand zugeordnet wird, wird die Messung automatisch einige Tage nach dem Kontaktdatum (im Fall eines Briefpost-Versands) oder nach dem Versanddatum (im Fall eines E-Mail- oder SMS-Versands) ausgelöst.

  ![](assets/response_measurement_001.png)

  Wenn die Hypothese im laufenden Betrieb gestartet wird, kann sie erzwungen werden, wenn sie sofort Trigger werden soll. Andernfalls wird sie automatisch auf der Grundlage des konfigurierten Enddatums der Berechnung ausgelöst, das auf dem Erstellungsdatum der Hypothese basiert. [Weitere Informationen](creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery).

* **[!UICONTROL Transaktionsbetrag/Betrag der Spanne]**: Diese Felder sind optional. Sie ermöglichen die automatische Berechnung der Umsatzindikatoren. [Weitere Informationen](hypothesis-tracking.md#indicators)
* **[!UICONTROL Stückbetrag]**: Dieses Feld ermöglicht die Festsetzung eines Betrags für die Berechnung des Umsatzes. [Weitere Informationen](hypothesis-tracking.md#indicators)

  ![](assets/response_transactions_001.png)

* **[!UICONTROL Ergänzende Messungen und Daten]**: In diesem Feld werden zusätzliche Messungen und Berichtsachsen basierend auf den Feldern der unterschiedlichen Tabellen bestimmt.
* **[!UICONTROL Vorschlagsstatus aktualisieren]**: Diese Option ermöglicht die Änderung eines Vorschlagsstatus, wenn ein Angebotsempfänger von der Hypothese identifiziert wurde.

  ![](assets/response_offer_status_001.png)

### Perimeter {#hypothesis-perimeter}

Nachdem Sie die Transaktionstabelle und die von der Hypothese betroffenen Felder definiert haben, können Sie den Umfang Ihrer Hypothesen einschränken, indem Sie die zielgerichteten Transaktionen und Sendungen mithilfe von Filtern angeben. Sie können auch ein JavaScript-Skript verwenden, um explizit auf ein Produkt zu verweisen, auf das in der Transaktionstabelle verwiesen wird.

* **Filterung der Transaktionen**: Im Tab **[!UICONTROL Umfang]** können Sie Filter für die Hypothese konfigurieren. Gehen Sie dazu wie folgt vor:

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

Im folgenden Beispiel wird eine Hypothesenvorlage für einen Briefpost-Versand erstellt. Die Transaktionstabelle (**Käufe** in unserem Beispiel), auf welcher die Hypothesen basieren, enthält Bestellzeilen, denen Produkte zugeordnet sind. Die Vorlage wird so konfiguriert, dass die Hypothesen sich auf eben diese Produkte bezieht.

1. Positionieren Sie sich im Knoten **[!UICONTROL Ressourcen > Vorlagen > Hypothesenvorlagen]** des Adobe Campaign-Explorers.
1. Klicken Sie auf **[!UICONTROL Neu]**, um eine Vorlage zu erstellen.

   ![](assets/response_hypothesis_model_example_001.png)

1. Ändern Sie den Titel der Vorlage.

   ![](assets/response_hypothesis_model_example_002.png)

1. Wählen Sie den Hypothesentyp **[!UICONTROL Sendungen]**.
1. Geben Sie an, dass der Versand eine Kontrollgruppe enthalten kann, indem Sie das entsprechende Feld ankreuzen.
1. Wählen Sie den Kanal **[!UICONTROL Briefpost]**.

   >[!NOTE]
   >
   >Da die Vorlage briefpostspezifisch ist, können die basierend auf dieser Vorlage erstellten Hypothesen keinen Sendungen zugeordnet werden, die andere Kanäle nutzen.

1. Geben Sie im Tab **[!UICONTROL Transaktionen]** die Empfängerreaktionen-Tabelle an.

   ![](assets/response_hypothesis_model_example_006.png)

1. Wählen Sie im Feld **[!UICONTROL Transaktionsschema]** Ihre den Kauf enthaltende Transaktionstabelle aus.

   ![](assets/response_hypothesis_model_example_007.png)

1. Wählen Sie im Feld **[!UICONTROL Abfrageschema]** Bestellzeilen aus.

   ![](assets/response_hypothesis_model_example_008.png)

1. Wählen Sie die Empfänger aus, die mit der Tabelle der Käufe in Relation stehen.

   ![](assets/response_hypothesis_model_example_009.png)

1. Wählen Sie das dem Kaufdatum entsprechende Feld aus, um die Hypothesen zeitlich zu beschränken.

   Auf diese Weise können Sie einen Zeitrahmen für Hypothesen definieren. Dieser Schritt ist nicht obligatorisch, wird aber empfohlen.

   ![](assets/response_hypothesis_model_example_010.png)

1. Konfigurieren Sie einen Berechnungszeitraum zwischen 5 und 25 Tagen.

   ![](assets/response_hypothesis_model_example_005.png)

1. Klicken Sie im Tab **[!UICONTROL Perimeter]** auf **[!UICONTROL Abfrage bearbeiten]**, um einen Hypothesenfilter zu erstellen.

   ![](assets/response_hypothesis_model_example_011.png)

   Die auf diese Weise erstellte Vorlage ermöglicht es Ihnen, Hypothesen für in Ihrer Käufe-Tabelle enthaltene Produkte zu erstellen.

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Erstellung der Vorlage zu beenden.

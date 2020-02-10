---
title: Dienstleister, Lager und Budgets
seo-title: Dienstleister, Lager und Budgets
description: Dienstleister, Lager und Budgets
seo-description: null
page-status-flag: never-activated
uuid: 6caffaaf-a6a6-40e1-8b17-07c81748382c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
discoiquuid: d4627141-cef1-4ddb-ad6a-5dc217b9fa96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# Dienstleister, Lager und Budgets{#providers-stocks-and-budgets}

In Adobe Campaign haben Sie die Möglichkeit, Dienstleister zu bestimmen, die an der Ausführung bestimmter Prozesse der Kampagnen beteiligt sind. Informationen bezüglich dieser Dienstleister und der ihnen zugeordneten Kostenstrukturen werden vom Adobe-Campaign-Administrator über die allgemeine Übersicht festgelegt. Der Dienstleister wird auf Versandebene referenziert: Seine Kostenstrukturen ermöglichen die Berechnung der mit dem jeweiligen Versand verbundenen Kosten sowie die Verwaltung der betroffenen Lager.

## Erstellung von Dienstleistern und deren Kostenstrukturen {#creating-service-providers-and-their-cost-structures}

Jeder Dienstleister wird in einer Datei gespeichert, die seine Kontaktdaten, Dienstleistungsvorlagen und verbundene Vorgänge enthält.

Service providers are configured in the **[!UICONTROL Administration > Campaign management]** node of the tree.

Diverse, in Sendungen zu realisierende Vorgänge werden von Dienstleistern ausgeführt, insbesondere solche, die Briefpost und mobile Kanäle betreffen. Diese Dienstleister kommen beispielsweise in Druckvorgängen oder bei der Zustellung von Nachrichten zum Einsatz. Diese Vorgänge erfordern dienstleisterspezifische Einstellungen und verursachen Kosten. Die Konfiguration von Dienstleistern erfolgt in vier Schritten:

1. Erstellung des Dienstleisters in Adobe Campaign.

   See [Adding a service provider](#adding-a-service-provider).

1. Definition der Kostenstellen und -strukturen der dem Dienstleister zugeordneten Dienstleistungsvorlagen.

   Siehe [Definieren von Kostenkategorien](#defining-cost-categories) und [Definieren der Kostenstruktur](#defining-the-cost-structure).

1. Konfiguration der Vorgänge.

   See [Configuring processes associated with a service](#configuring-processes-associated-with-a-service).

1. Referenzierung des Dienstleisters in Kampagnen.

   See [Associating a service with a campaign](#associating-a-service-with-a-campaign).

### Erstellen eines Dienstleisters und seiner Kostenstellen {#creating-a-service-provider-and-its-cost-categories}

#### Hinzufügen eines Dienstleisters {#adding-a-service-provider}

Sie können so viele Dienstleister erstellen, wie für Ihre Sendungen notwendig sind. Gehen Sie wie folgt vor, um einen Dienstleister hinzuzufügen:

1. Right-click the list of service providers and select **[!UICONTROL New]**, or click the **[!UICONTROL New]** button above the list of service providers.
1. Geben Sie im unteren Abschnitt des Fensters Namen und Kontaktdaten des Dienstleisters an.

   ![](assets/s_ncs_user_supplier_node_01.png)

1. Click the **[!UICONTROL Save]** button to add the service provider to the list.

#### Bestimmung der Kostenstellen {#defining-cost-categories}

Jedem Dienstleister müssen Dienstleistungsvorlagen zugeordnet werden. In diesen Vorlagen werden zunächst die unterschiedlichen Kostenstellen und bei Bedarf die betroffenen Lager angegeben. Daraufhin müssen über die Kostenstrukturen Regeln zur Kostenberechnung für jeden Kostentyp erstellt werden.

>[!NOTE]
>
>For more on this, refer to [Defining the cost structure](#defining-the-cost-structure).

Eine Kostenstelle ist eine Einheit, die die für einen bestimmten Versandtyp (E-Mail, Briefpost usw.) oder für eine Aufgabe anfallenden Kosten enthält. Kostenstellen werden in Dienstleistungsvorlagen zusammengefasst, die wiederum Dienstleistern zugeordnet werden. Jeder Dienstleister kann eine oder mehrere Dienstleistungsvorlagen referenzieren.

Um eine Dienstleistungsvorlage zu erstellen und ihren Inhalt zu bestimmen, gehen Sie wie folgt vor:

1. In the **[!UICONTROL Services]** tab of the service provider, click the **[!UICONTROL Add]** button and name the service template.

   ![](assets/s_ncs_user_supplier_node_create_template.png)

1. Erstellen Sie die Kostenkategorien für jeden Prozesstyp (Lieferung per Direktversand/E-Mail/etc.). oder Aufgabe). Klicken Sie dazu auf die **[!UICONTROL Cost categories]** Registerkarte und dann auf die **[!UICONTROL Add]** Schaltfläche und geben Sie die Parameter der einzelnen Kostenkategorien ein.

   ![](assets/s_ncs_user_supplier_node_03.png)

   * Geben Sie eine Beschriftung für diese Kostenkategorie ein und wählen Sie den betreffenden Prozesstyp aus: Lieferung durch **[!UICONTROL Direct mail]**, **[!UICONTROL E-mail]**, **[!UICONTROL Mobile]**, **[!UICONTROL Telephone]** oder **[!UICONTROL Fax]****[!UICONTROL Task]**.
   * Click the **[!UICONTROL Add]** button to define the types of cost associated with this category.
   * Bei Bedarf können Sie jedem Kostentyp eine Lagerposition hinzufügen, um den bestehenden Lagern automatisch die verwendeten Mengen anzurechnen.

      >[!NOTE]
      >
      >The stock lines are defined in the **[!UICONTROL Stock management]** node.\
      >Weitere Informationen finden Sie unter [Lagerbestandsverwaltung](#stock-and-order-management).

1. Sie können einen Wert für diese Kostenkategorie vorab auswählen, der standardmäßig in den Kostenkategorien des Dienstanbieters angeboten wird (anstelle eines Leerzeichens). Wählen Sie dazu die Option in der **[!UICONTROL Selected]** Spalte für die betreffende Kategorie aus:

   ![](assets/s_ncs_user_supplier_cost_structure_defaut.png)

   Auf Ebene des Versand wird der Wert standardmäßig vorgeschlagen:

   ![](assets/s_ncs_user_supplier_default_cost.png)

### Bestimmung der Kostenstruktur {#defining-the-cost-structure}

Eine Kostenstruktur gibt für jede Kostenstelle die anzuwendenden Berechnungsregeln an.

Klicken Sie auf die **[!UICONTROL Cost structure]** Registerkarte, um die Kostenberechnung für jede Kostenkategorie und jeden Kostentyp zu konfigurieren. Klicken Sie auf **[!UICONTROL Add]** und geben Sie die Kostenstruktur ein.

![](assets/s_ncs_user_supplier_node_04.png)

* Um die Kostenstruktur zu erstellen, wählen Sie den Typ der Nachricht und die betreffende Kostenkategorie aus den Dropdownlisten sowie den Kostentyp, für den die Berechnungsregel gilt. Der Inhalt dieser Dropdownlisten stammt aus den Informationen, die über die **[!UICONTROL Cost categories]** Registerkarte eingegeben wurden.

   Die Kostenstruktur muss benannt werden. Standardmäßig setzt sich ihr Titel wie folgt zusammen: **Kostenstelle - Kostentyp**.

   You can, however, rename it: enter the desired value directly in the **[!UICONTROL Label]** field.

* Die Formel zur Berechnung der Kosten wird im unteren Abschnitt des Fensters definiert.

   Diese Formel kann unabhängig von der Nachrichtenanzahl festgelegt oder entsprechend der Nachrichtenanzahl berechnet werden.

   Wenn es von der Anzahl der Nachrichten abhängt, kann die Kostenberechnungsstruktur **[!UICONTROL Linear]**, **[!UICONTROL Linear by threshold]** oder **[!UICONTROL Constant by threshold]**.

#### Lineare Struktur {#linear-structure}

Wenn es sich unabhängig von der Gesamtzahl von Nachrichten immer um den gleichen Betrag für eine Nachricht (oder eine Gruppe von Nachrichten) handelt, wählen Sie den Strukturtyp **[!UICONTROL Linear]** aus und geben Sie die Kosten pro Nachricht an.

![](assets/s_ncs_user_supplier_cost_structure_calc_01.png)

If this amount applies to a batch of messages, specify the number of messages concerned in the **[!UICONTROL for]** field.

![](assets/s_ncs_user_supplier_cost_structure_calc_02.png)

#### Lineare Struktur mit Schwellen {#linear-structure-by-threshold}

Wenn der Betrag für jede Nachricht als Schwellenwert gilt, müssen Sie eine **[!UICONTROL Linear by threshold]** Berechnungsstruktur definieren. In dieser Kostenstruktur kostet jede Nachricht beispielsweise 0,13, wenn die Gesamtanzahl der Nachrichten zwischen 1 und 100 liegt, und 0,12 von 100 bis 1000 gesendeten Nachrichten oder 0,11 über 1000 Nachrichten hinaus.

Die Konfiguration stellt sich wie folgt dar:

![](assets/s_ncs_user_supplier_cost_structure_calc_03.png)

To add a threshold, click the **[!UICONTROL Add]** button to the right of the list.

#### Konstante Struktur mit Schwellen {#constant-structure-by-threshold}

Schließlich können Sie eine Kostenberechnung entsprechend der Gesamtanzahl der Nachrichten konfigurieren. Wählen Sie dazu eine **[!UICONTROL Constant by threshold]** Berechnungsstruktur aus. Beispielsweise werden die Kosten für 1 bis 100 Nachrichten auf einen festen Betrag von 12,00 und für 1 bis 1000 Nachrichten auf 100,00 und für 1000 Nachrichten auf 500,00 für alle Sendungen über 1000 Nachrichten, unabhängig von der Gesamtzahl, festgesetzt.

![](assets/s_ncs_user_supplier_cost_structure_calc_04.png)

### Konfiguration der mit Dienstleistungen verbundenen Vorgänge {#configuring-processes-associated-with-a-service}

You can associate information on the processes associated with the service via the **[!UICONTROL Processes]** tab.

To do this, click the **[!UICONTROL Processes]** tab to configure the sending of information to the router.

![](assets/s_ncs_user_supplier_node_02.png)

* Der **[!UICONTROL File extraction]** Abschnitt zeigt die Exportvorlage an, die bei Auswahl dieses Dienstes für die Bereitstellung verwendet wird. Sie können den Namen der Ausgabedatei im **[!UICONTROL Extraction file]** Feld angeben. Mithilfe der Schaltfläche rechts neben dem Feld können Sie Variablen einfügen.

   ![](assets/s_ncs_user_supplier_node_02a.png)

* Im **[!UICONTROL Notification e-mail]** Abschnitt können Sie die Vorlage angeben, um Dienstanbieter nach dem Senden von Dateien zu benachrichtigen. Wählen Sie die Vorlage aus, mit der die Warnmeldung erstellt wird, und die Gruppe der Empfänger.

   By default, delivery templates for notification messages are saved in the **[!UICONTROL Administration > Campaign management > Technical delivery templates]** node, which is accessible from the general view.

* Im **[!UICONTROL Post-processing]** Abschnitt können Sie den Workflow auswählen, der nach Genehmigung der Bereitstellung gestartet werden soll. Wenn eine Workflow-Vorlage eingegeben wird, wird automatisch eine Workflow-Instanz erstellt und gestartet, sobald die Genehmigung wirksam wird. Dieser Workflow kann die Extraktionsdatei beispielsweise zur Verarbeitung an einen externen Dienstleister senden.

### Zuordnung von Dienstleistungen zu Kampagnen {#associating-a-service-with-a-campaign}

Dienstleistungen werden Kampagnen über Sendungen oder Aufgaben zugeordnet. Damit in einer Sendung bestimmte Dienstleistungen zur Anwendung kommen können, sind die entsprechenden Dienstleister in der genutzten Versandvorlage anzugeben.

Wenn eine Dienstleistung ausgewählt wird, werden die dem Versandtyp (Briefpost, E-Mail usw.) entsprechenden Kostenstellen automatisch in der zentralen Tabelle angegeben, ebenso wie die bereits definierten Vorgangsoptionen.

>[!NOTE]
>
>Wenn bei Auswahl eines Dienstes keine Kostenkategorie angezeigt wird, bedeutet dies, dass für diesen Prozesstyp keine Kostenkategorie definiert wurde. Wenn beispielsweise für eine E-Mail-Zustellung keine **[!UICONTROL E-mail]** Kostenkategorie definiert wurde, wird keine Kategorie angezeigt und die Auswahl des Dienstes hat keine Auswirkungen.

* In Briefpost-Sendungen können Sie eine Dienstleistung über das Konfigurationsfenster auswählen.

   ![](assets/s_ncs_user_supplier_mail_delivery_select.png)

* In Mobile-, Fax- oder Telefonsendungen werden Dienstleistungen auf die gleiche Weise wie bei Briefpost-Sendungen ausgewählt.
* For an email delivery, the service is selected from the **[!UICONTROL Advanced]** tab in the delivery properties, as in the following example:

   ![](assets/s_ncs_user_supplier_email_delivery_select.png)

The **[!UICONTROL Amount to surcharge]** column lets you add a cost for this category in the context of the delivery or task concerned.

You can impose mandatory selection of a cost type during the definition of cost categories for a delivery. To do this, select **[!UICONTROL A cost type must be selected]**.

![](assets/s_ncs_user_supplier_cost_structure_select.png)

## Verwaltung von Lagern und Lagerergänzungen {#stock-and-order-management}

Kostentypen können Lagerpositionen zugeordnet werden, um Bestandsmeldungen zu verwalten, Lagerergänzungen zu verfolgen und Bestellungen zu tätigen.

Um die Verwaltung von Lagern und Lagerergänzungen in Adobe Campaign einzusetzen und Benutzern für die Durchführung eines Versands unzureichende Bestände zu melden, ist die Einhaltung folgender Schritte erforderlich:

1. Erstellung von Lagern und Referenzierung von zugeordneten Dienstleistern.

   See [Creating a stock](#creating-a-stock).

1. Hinzufügen von Lagerpositionen

   Siehe [Hinzufügen von](#adding-stock-lines)Stammzeilen.

1. Benachrichtigung der Benutzer bei Unterschreiten des Meldebestands.

   Siehe [Warnungs-Operatoren](#alerting-operators).

1. Bestellungen und Lieferungen;

   Siehe [Bestellungen](#orders).

### Lagerverwaltung {#stock-management}

Adobe Campaign kann eine Gruppe von Operatoren warnen, wenn der Bestand abgelaufen ist oder einen Mindestschwellenwert erreicht hat. Über den **[!UICONTROL Stocks]** Link des **[!UICONTROL Campaigns]** Universums über die **[!UICONTROL Other choices]** Verknüpfung des Navigationsbereichs sind die Ebenen auf Lager zugänglich.

![](assets/s_ncs_user_stocks_view.png)

#### Erstellung eines Lagers {#creating-a-stock}

Folgen Sie den nachstehenden Etappen, um ein neues Lager zu erstellen:

1. Click the **[!UICONTROL Create]** button above the list of stocks.
1. Geben Sie den Titel des Lagers an und wählen Sie in der Dropdown-Liste den zugehörigen Dienstleister aus.

   ![](assets/s_ncs_user_stocks_add.png)

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter [Erstellen von Dienstanbietern und deren Kostenstrukturen](#creating-service-providers-and-their-cost-structures).

#### Hinzufügen von Lagerpositionen {#adding-stock-lines}

Ein Lager setzt sich aus unterschiedlichen Lagerpositionen zusammen. Eine Lagerposition enthält eine Anfangsmenge der Ressourcen, die von den Sendungen verbraucht werden. Jede Position enthält außerdem die verbrauchte Menge, den Restbestand sowie die bestellte Menge.

When you create a stock, click the **[!UICONTROL Stock lines]** tab to add new lines.

![](assets/s_ncs_user_stocks_display_line.png)

Nach der Erstellung des Lagers können Sie dieses per Klick öffnen und über sein Dashboard die Lagerpositionen anzeigen lassen.

Click the **[!UICONTROL Create]** button to define the stock parameters.

![](assets/s_ncs_user_stocks_new_line.png)

* Anzugeben ist die anfänglich auf Lager befindliche Menge im **[!UICONTROL Initial stock]** Feld. Die **[!UICONTROL Consumed]** und **[!UICONTROL In stock]** Felder werden automatisch berechnet und aktualisiert, sobald Kampagnen voranschreiten.

   ![](assets/s_ncs_user_stocks_create_line.png)

* Geben Sie den Schwellenwert an, ab dem die Betreiber auf die Bestellung von Vorräten im **[!UICONTROL Alert level]** Feld hingewiesen werden sollten. Wenn die Alarmstufe erreicht ist, wird im Genehmigungsfenster bei Auslieferungen, die diesen Bestand verwenden, eine Warnmeldung angezeigt.

#### Lagerpositionen zu Kostenstellen zuordnen {#associating-a-stock-with-cost-categories}

Folgendes Beispiel zeigt, wie Lagerpositionen in Dienstleistungen über die Kostenstellen zugeordnet werden können:

![](assets/s_ncs_user_stocks_select_from_supplier.png)

### Lagerverfolgung {#stock-tracking}

#### Benachrichtigung bei unzureichendem Bestand {#alerting-operators}

Bei einem Versand, der auf eine Lagerposition mit unzureichendem Bestand zugreift, wird ein Warnhinweis angezeigt. Unten stehendes Beispiel zeigt die Meldung, die bei Validierung einer Extraktionsdatei erscheint:

![](assets/s_ncs_user_stocks_valid_alert.png)

#### Lagerergänzungen {#orders}

The **[!UICONTROL Orders]** sub-tab lets you view current orders and save new orders.

![](assets/s_ncs_user_stocks_edit_from_board.png)

To save an order, edit the targeted stock line, click the **[!UICONTROL Add]** button and specify the delivery date and the quantity ordered.

![](assets/s_ncs_user_stocks_node_06.png)

>[!NOTE]
>
>Sobald der Liefertermin erreicht ist, verschwindet die bestellte Linie automatisch und die in das **[!UICONTROL Volume on order]** Feld eingegebene Menge wird der **[!UICONTROL Tracking]** Registerkarte hinzugefügt. Diese Menge wird automatisch zum Lagervolumen hinzugefügt.

![](assets/s_ncs_user_stocks_node_08.png)

Die **[!UICONTROL Consumptions]** Registerkarte enthält das pro Kampagne verbrauchte Volumen. Die Informationen aus diesem Register werden automatisch entsprechend den durchgeführten Lieferungen eingegeben. Klicken Sie auf die **[!UICONTROL Edit]** Schaltfläche, um die betreffende Kampagne zu öffnen.

![](assets/s_ncs_user_stocks_edit_from_board_consumed.png)

## Berechnung von Budgets {#calculating-budgets}

### Funktionsprinzip {#principle}

Sie haben die Möglichkeit, Kosten für Sendungen oder Kampagnen zu verwalten und diese auf zuvor definierte Budgets anzurechnen.

Die Versandkosten einer Kampagne werden in der jeweiligen Kampagne, die Kosten aller Kampagnen eines Programms im jeweiligen Programm konsolidiert. Dedizierte Berichte ermöglichen die Verfolgung der Budgets für die gesamte Plattform oder für jeden Plan und jedes Programm.

### Umsetzung {#implementation}

Wenn Sie in einer Kampagne das Budget auswählen, müssen Sie den Anfangsbetrag eingeben. Die berechneten Kosten werden automatisch entsprechend der Höhe der Mittelbindungen aktualisiert (Ausgaben, die getätigt, erwartet, reserviert, gebunden). Siehe [Berechnen von Beträgen](../../campaign/using/controlling-costs.md#calculating-amounts).

>[!NOTE]
>
>Das Verfahren zum Erstellen von Budgets finden Sie unter [Erstellen eines Budgets](../../campaign/using/controlling-costs.md#creating-a-budget).


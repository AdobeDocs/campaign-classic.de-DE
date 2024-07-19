---
product: campaign
title: Kosten kontrollieren
description: Erfahren Sie, wie Sie Kosten kontrollieren können
feature: Resource Management
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
exl-id: 6765e307-915a-44d2-a486-85c64e8ec52e
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '2559'
ht-degree: 100%

---

# Kosten kontrollieren{#controlling-costs}



Adobe Campaign ermöglicht mit dem MRM-Modul die Kontrolle der geplanten, eingesetzten und berechneten Marketing-Kosten sowie ihre Verteilung nach Kategorie.

Die für die unterschiedlichen Kampagnenvorgänge anfallenden Kosten werden einem zuvor festgesetzten Budget zugeteilt. Die Beträge können in verschiedene Kategorien verteilt werden, um eine bessere Lesbarkeit und detailliertere Berichte der Marketing-Kosten zu ermöglichen.

Die Budgetverwaltung und -verfolgung sind in einem dedizierten Knoten des Adobe-Campaign-Navigationsbaums zentralisiert. Von hier aus können Sie alle Budgets sowie die zugeteilten, reservierten, eingesetzten und verbrauchten Beträge kontrollieren.

![](assets/s_ncs_user_budget_node_02.png)

Zur Nutzung der Budget-Verwaltung mit MRM sind folgende Etappen umzusetzen:

1. Festlegung des Budgets;

   Weitere Informationen hierzu finden Sie unter [Erstellen von Budgets](#creating-a-budget).

1. Bestimmung des Kostenberechnungsmodus;

   Kostenstrukturen werden für Dienstleister bestimmt. Siehe [Erstellen eines Dienstleisters und seiner Kostenkategorien](../../campaign/using/providers-stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories).

1. Bestimmung der Kampagnenkosten (Sendungen/Aufgaben);

   die durch Sendungen und Aufgaben anfallenden Kosten werden einzeln oder pauschal in der Kampagnenvorlage angegeben. Siehe [Kosten- und Lagerberechnung](../../campaign/using/marketing-campaign-deliveries.md#calculation-of-costs-and-stocks).

1. Konsolidierung;

   gemäß dem Erfüllungsstatus der Aufgaben, Sendungen und Kampagnen werden die Kosten berechnet und dem entsprechenden Budget übermittelt.

   Wenn die Erstellung der Kampagne ausreichend fortgeschritten ist, kann der Erfüllungsstatus des Kampagnenbudgets in **[!UICONTROL Angegeben]** geändert werden. Die berechneten Kosten des Programms werden daraufhin automatisch mit den berechneten Kosten der Kampagnen konsolidiert. Siehe [Entstehung, Berechnung und Anrechnung von Kosten](#cost-commitment--calculation-and-charging).

## Erstellen eines Budgets {#creating-a-budget}

Budgets werden in der Karte im Knoten **[!UICONTROL Kampagnenverwaltung > Budgets]** erstellt. Die Schaltfläche **[!UICONTROL Neu]** in der Symbolleiste ermöglicht es Ihnen, ein Budget zu erstellen.

* Neues Budget hinzufügen

  Klicken Sie auf das Symbol **[!UICONTROL Neu]**, benennen und speichern Sie das Budget.

* Zugeteilten Betrag eingeben

  Geben Sie den zugeteilten Betrag im entsprechenden Feld ein. Die übrigen Beträge werden automatisch ausgefüllt. Siehe [Beträge berechnen](#calculating-amounts).

* Gültigkeitszeitraum bestimmen

  Geben Sie Beginn und Ende der Budgetplanung ein. Es handelt sich hierbei lediglich um Richtwerte.

* Ausgaben

  Erstellen Sie die Ausgabenkategorien, denen die für Kampagnen, Sendungen, Aufgaben usw. anfallenden Kosten in diesem Budget zugeordnet werden können. Siehe [Ausgabenkategorien](#expense-categories).

  ![](assets/s_ncs_user_budget_create_and_save.png)

>[!NOTE]
>
>Sie können ein übergeordnetes Budget auswählen.
>
>Weitere Informationen hierzu finden Sie unter [Zuordnung von Budgets untereinander](#linking-a-budget-to-another).

### Beträge berechnen {#calculating-amounts}

Der Anfangsbestand eines Budgets verringert sich im Zuge der ihm zugeordneten Kampagnen, Sendungen oder Aufgaben um die anfallenden Kosten, sobald diese geplant oder realisiert wurden. Der Status der Beträge (Geplant, Reserviert, Eingesetzt, Verbraucht, Fakturiert) hängt vom Kostentyp und dem Verbindlichkeitsniveau ab, die in der Kamapgne, der Sendung oder der Aufgabe festgelegt wurden.

>[!NOTE]
>
>Die in den Kategorien eingetragenen Beträge müssen dem im Feld **[!UICONTROL Zugeteilt]** angegebenen Gesamtbudget entsprechen.

In Kampagnen können je nach Verbindlichkeitsniveau Kosten für eine zukünftige Aktion geplant, eingesetzt oder reserviert werden.

![](assets/s_user_cost_op_engaged.png)

>[!CAUTION]
>
>Bei der Erstellung einer Kampagne muss der Fortschrittsstatus im **[!UICONTROL Budget]** auf **[!UICONTROL Angegeben]** eingestellt sein, damit die Kosten bei der Ausführung berücksichtigt werden. Wenn der Status **[!UICONTROL In Bearbeitung]** ist, werden die Kosten nicht konsolidiert.
>   
>Die Option **[!UICONTROL Verbindlichkeitsniveau]** stellt eine Schätzung der zukünftigen Kosten dar, bevor diese dem Budget angerechnet werden. Entsprechend dem Fortschritt einer Kampagne, einer Aufgabe oder eines Versands kann mithilfe der Dropdown-Liste ein höheres oder niedrigeres Niveau zugewiesen werden (1. Geplant, 2. Reserviert, 3. Eingesetzt).

Beispiel: Die Kosten einer Web-Kampagne werden auf 45 000 Euro geschätzt.

![](assets/s_user_edit_budget_node_impact_0.png)

Wenn der Erfüllungsstatus des Budgets in der Kampagne **[!UICONTROL Angegeben]** ist, werden die tatsächlichen Kosten der Kampagne (oder, wenn nicht angegeben, die berechneten Kosten) in die Budgetbeträge übertragen.

![](assets/s_user_budget_in_op_a.png)

Je nach Verbindlichkeitsniveau der Kampagne wird der Betrag in das Feld **[!UICONTROL Geplant]**, **[!UICONTROL Reserviert]** oder **[!UICONTROL Eingesetzt]** übertragen.

Das Verbindlichkeitsniveau kann geändert werden:

* in einer **Kampagne** im Fenster **[!UICONTROL Budget]** des **[!UICONTROL Bearbeiten]**-Tabs. Hier werden insbesondere Budgets, Kosten und Ausgaben konfiguriert.
* in einer **Aufgabe** im Fenster **[!UICONTROL Ausgaben und Einnahmen]**.

![](assets/s_user_op_engagement_level_costs.png)

Sobald ein Budget **[!UICONTROL Reserviert]** ist, wird automatisch das zugeteilte Budget aktualisiert.

![](assets/s_user_edit_budget_node_impact_2.png)

Der Ablauf entspricht dem der Aufgaben:

![](assets/s_user_edit_budget_node_impact_task.png)

Wenn eine Ausgabe in Rechnung gestellt und diese Rechnung beglichen wird, wird der jeweilige Betrag im Feld **[!UICONTROL Fakturiert]** eintragen.

### Ausgabenkategorien {#expense-categories}

Die Beträge können in verschiedene Ausgabenkategorien verteilt werden, um eine bessere Lesbarkeit der Daten und eine detailliertere Berichterstattung über Marketing-Investitionen zu erreichen. Die Ausgabenkategorien werden bei der Budgeterstellung über den Knoten **[!UICONTROL Budgets]** des Baums definiert.

Klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]** im unteren Abschnitt des Fensters, um eine Kategorie hinzuzufügen.

![](assets/s_user_budget_category.png)

Sie können eine der existierenden Kategorien auswählen oder eine neue definieren, indem Sie sie direkt in das Feld eingeben. Bei der Bestätigung Ihrer Eingabe wird Ihnen ermöglicht, die Kategorie der Liste der existierenden Kategorien hinzuzufügen und sie bei Bedarf einer Art zuzuordnen. Diese Informationen werden in den Budgetberichten ausgewertet.

### Zuordnung von Budgets untereinander {#linking-a-budget-to-another}

Sie können ein Budget mit einem Hauptbudget verknüpfen. Wählen Sie dazu das Hauptbudget im Feld **[!UICONTROL Übergeordnetes Budget]** der sekundären Budgets aus.

![](assets/budget_link.png)

Dem Hauptbudget wird daraufhin ein Tab zur Auflistung der untergeordneten Budgets hinzugefügt.

![](assets/budget_link_new_tab.png)

Diese Informationen werden in den Budgetberichten ausgewertet.

## Ausgabenzeilen hinzufügen {#adding-expense-lines}

Ausgabezeilen werden dem Budget automatisch hinzugefügt. Sie werden bei der Versandanalyse und beim Abschluss einer Aufgabe erstellt.

![](assets/s_ncs_user_budget_line_edit.png)

Die für Kampagnen, Sendungen oder Aufgaben anfallenden Kosten werden in den Ausgabenzeilen des Budgets, dem sie zugeteilt sind, zusammengefasst. Diese Ausgabenzeilen werden abhängig von den Kostenkategorien des beteiligten Dienstleisters erstellt und ausgehend von den verbundenen Kostenstrukturen berechnet.

Damit enthält jede Ausgabenzeile folgende Informationen:

* die Kampagne und Sendung oder Aufgabe, der sie zugeordnet ist;
* den ausgehend von den Kostenstrukturen oder den Plankosten berechneten Betrag;
* die tatsächlichen Kosten der Sendung oder der betreffenden Aufgabe;
* die entsprechende Rechnungszeile (ausschließlich in MRM);
* die Liste der berechneten Kosten je Kostenkategorie (wenn eine Kostenstruktur existiert).

Im obigen Beispiel enthält die bearbeitete Ausgabenzeile die berechneten Kosten für den Versand **Neue Karten** für die Kampagne **Loyalty Spring Pack**. Bei der Bearbeitung des Versands zeigt die Registerkarte **[!UICONTROL Briefpost]** an, wie die Ausgabenzeile berechnet wird.

Als Grundlage der Kostenberechnung für diesen Versand dienen die für den betroffenen Dienstleister ausgewählten Kostenkategorien.

![](assets/s_user_edit_del_supplier_costs.png)

Abhängig von diesen Kostenkategorien werden die entsprechenden Kostenstrukturen zur Berechnung der Ausgabenzeilen angewandt. Im vorliegenden Beispiel handelt es sich um folgenden Kostenstrukturen für den betroffenen Dienstleister:

![](assets/s_user_edit_node_supplier_costs.png)

>[!NOTE]
>
>Kostenkategorien und -strukturen werden unter [Erstellen eines Dienstleisters und seiner Kostenkategorien](../../campaign/using/providers-stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories) beschrieben.

## Entstehung, Berechnung und Anrechnung von Kosten {#cost-commitment--calculation-and-charging}

Kosten können in Sendungen und Aufgaben entstehen. Abhängig vom Bearbeitungsfortschritt des jeweiligen Vorgangs wird der Kostenstatus aktualisiert.

### Kostenarten {#cost-calculation-process}

Kosten werden in drei Kategorien eingeteilt:

1. Plankosten

   Die Plankosten entsprechen einer Schätzung der Kosten für die Kampagnenprozesse. Solange sie bearbeitet werden, werden die eingegebenen Beträge nicht konsolidiert. Der Status **[!UICONTROL Angegeben]** ist hier nötig, damit die eingegebenen Beträge in den Berechnungen berücksichtigt werden.

   Dieser Betrag wird manuell eingegeben und kann in mehrere Ausgabenkategorien unterteilt werden. Klicken Sie zum Aufschlüssen von Kosten auf den Link **[!UICONTROL Aufschlüsselung…]** und dann auf die Schaltfläche **[!UICONTROL Hinzufügen]**, um einen neuen Betrag zu definieren.

   ![](assets/s_user_edit_budget_tab_ventil.png)

   Jeder Kostenbetrag kann einer Kategorie zugeordnet werden. Dies ermöglicht eine Übersicht der Kostenverteilung nach Ausgabenkategorien im übergeordneten Budget sowie in den Budgetberichten.

1. Berechnete Kosten

   Die berechneten Kosten hängen vom betroffenen Element (Kampagne, Versand, Aufgabe etc.) und seinem Status ab (In Bearbeitung, In Gang, Abgeschlossen). Sobald die tatsächlichen Kosten angegeben sind, wird dieser Betrag grundsätzlich von den berechneten Kosten übernommen.

   Wenn die tatsächlichen Kosten nicht angegeben sind, gelten folgende Regeln:

   * In einer sich in Bearbeitung befindenden Kampagne entsprechen die berechneten Kosten dem Betrag der Plankosten der Kampagne. Wenn diese nicht global für die Kampagne angegeben wurden, setzen sich die berechneten Kosten aus der Summe der Plankosten der einzelnen Sendungen und Aufgaben der Kampagne zusammen. Nach Abschluss der Kampagne entsprechen die berechneten Kampagnenkosten der Summe aller berechneten Kosten.
   * In einem noch nicht analysierten Versand entsprechen die berechneten Kosten dem Betrag der Plankosten. Wenn die Analyse bereits stattgefunden hat, setzen sich die berechneten Kosten aus den basierend auf den Kostenstrukturen des Dienstleisters und der Anzahl der ausgewählten Empfänger berechneten Beträgen zusammen.
   * In einer gestarteten Aufgabe werden die Plankosten als berechnete Kosten verwendet. Nach Abschluss der Aufgabe entsprechen die berechneten Kosten der Summe aller basierend auf den Kostenstrukturen des Dienstleisters und - falls zutreffend - der Anzahl an insgesamt benötigten Tagen berechneten Kosten.
   * Sowohl für Marketing-Pläne als auch für Programme entsprechen die berechneten Kosten der Summe der für die verknüpften Kampagnen berechneten Kosten. Wenn diese nicht angegeben sind, werden die Plankosten anstelle der berechneten Kosten verwendet.

   >[!NOTE]
   >
   >Über den **[!UICONTROL Verteilung]**-Link der berechneten Kosten können Details der Berechnung sowie das Datum der letzten Kostenberechnung eingesehen werden.

1. Tatsächliche Kosten

   Tats. Kosten werden manuell erfasst und bei Bedarf zwischen unterschiedlichen Ausgabenkategorien verteilt.

### Anrechnung auf Budgets {#calculation-and-charging}

Kosten werden mithilfe der Kostenstrukturen berechnet und auf die in den betroffenen Kampagnen, Sendungen oder Aufgaben ausgewählten Budgets angerechnet.

Über die Budget-Validierung können die in Kampagnen anfallenden Beträge geprüft werden. Zusätzlich ist die Erstellung von Kontrollaufgaben ein weiteres Mittel, um einzelne Bereiche einer Kampagne zur Validierung zu unterbreiten. Siehe [Aufgabenarten](../../mrm/using/creating-and-managing-tasks.md#types-of-task).

### Beispiel {#example}

Im Folgenden wird eine Kampagne mit folgenden Elementen erstellt:

* Briefpost-Versand mit Kostenstrukturen eines Dienstleisters
* Aufgabe mit Fixkosten
* Aufgabe mit Tageskosten

#### Schritt 1: Budget erstellen {#step-1---creating-the-budget}

1. Erstellen Sie ein neues Budget über den Knoten **[!UICONTROL Kampagnenverwaltung > Budgets]**.

1. Bestimmen Sie ein Gesamtbudget von 10.000 Euro im Feld **[!UICONTROL Zugeteilt]** des Abschnitts **[!UICONTROL Beträge]**. Fügen Sie drei Ausgabenkategorien im unteren Abschnitt des Fensters hinzu:

![](assets/s_user_cost_mgmt_sample_1.png)

#### Schritt 2: Dienstleister konfigurieren und Kostenstrukturen festlegen {#step-2---configuring-the-service-provider-and-defining-the-cost-structures}

1. Erstellen Sie einen Dienstleister sowie eine Dienstleistungsvorlage mit Kostenstruktur über den Knoten **[!UICONTROL Administration > Kampagnen > Dienstleister]**. Weitere Informationen hierzu finden Sie unter [Erstellen eines Dienstleisters und seiner Kostenkategorien](../../campaign/using/providers-stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories).

   Erstellen Sie für die Briefpost-Sendungen **[!UICONTROL Briefumschläge]**-Kostenkategorien (Typen 114x229 und 162x229), **[!UICONTROL Porto und Versand]** und **[!UICONTROL Farbdruck]** (Typen A3 und A4). Erstellen Sie dann die folgenden Kostenstrukturen:

   ![](assets/s_user_cost_mgmt_sample_2.png)

1. Fügen Sie in den Kostenkategorien Fixkosten vom Typ &quot;Festpreis&quot; hinzu, deren Betrag in der entsprechenden Kostenstruktur leer ist. (Dieser wird einzeln für jeden Versand angegeben.)

   ![](assets/s_user_cost_mgmt_sample_5.png)

   Erstellen Sie für die Aufgaben die folgenden zwei Kostenkategorien:

   * **[!UICONTROL Raumreservierung]** (Typen Kleiner Saal und Großer Saal) mit einer **Pauschale** von 300 und 500 Euro.

   ![](assets/s_user_cost_mgmt_sample_6.png)

   * **[!UICONTROL Erstellung]** (Typ **Inhaltsvorlage**) mit von der **Dauer in Tagen** abhängigen Kosten in Höhe von 300 Euro:

   ![](assets/s_user_cost_mgmt_sample_7.png)

#### Schritt 3: Anfallende Kosten auf das Kampagnenbudget anrechnen {#step-3---charging-the-budget-in-the-campaign}

1. Erstellen Sie eine Kampagne und wählen Sie das im 1. Schritt erstellte Budget aus.

   >[!NOTE]
   >
   >Das im Programm ausgewählte Budget wird standardmäßig für alle Kampagnen des Programms angewandt.

   ![](assets/s_user_cost_mgmt_sample_4.png)

1. Geben Sie die Plankosten mit Verteilung an:

   ![](assets/s_user_cost_mgmt_sample_9.png)

1. Klicken Sie zur Speicherung dieser Daten auf **[!UICONTROL OK]** und dann auf **[!UICONTROL Speichern]**. Die berechneten Kosten der Kampagne werden daraufhin mit den Plankosten aktualisiert.

#### Schritt 4: Briefpost-Versand erstellen {#step-4---creating-the-direct-mail-delivery}

1. Erstellen einen Kampagnen-Workflow mit einer Abfrage zur Zielgruppenbestimmung. Stellen Sie sicher, dass die Postadresse der ausgewählten Empfänger angegeben ist.

1. Erstellen Sie nun einen Briefpost-Versand und wählen Sie den im zweiten Schritt erstellten Dienstleister aus: Die Kostenkategorien werden automatisch angezeigt.

1. Überschreiben Sie die Kosten der Briefumschläge und fügen Sie Fixkosten hinzu. Wählen Sie zudem die von diesen Kosten betroffenen Kategorien aus.

   ![](assets/s_user_cost_mgmt_sample_3.png)

   >[!NOTE]
   >
   >Wenn eine der Kostenkategorien nicht verwendet wird, fallen durch diese keinerlei Ausgaben an.

1. Starten Sie den gerade erstellten Workflow, um die Analyse zu beginnen und die Kosten zu berechnen.

   ![](assets/s_user_cost_mgmt_sample_10.png)

1. Wenn die Budgetvalidierung für diese Kampagne aktiviert wurde, validieren Sie das Budget über das Dashboard. Sie können an dieser Stelle auch die Validierung der Kostenkategorien überprüfen.

   ![](assets/s_user_cost_mgmt_sample_10b.png)

Die den Versand betreffende Ausgabenzeile wird im Tab **[!UICONTROL Bearbeiten > Budget]** der Kampagne hinzugefügt. Klicken Sie auf Details..., um genauere Informationen zu erhalten.

![](assets/s_user_cost_mgmt_sample_11.png)

Auf Versandniveau werden die berechneten Kosten mit folgenden Daten aktualisiert:

![](assets/s_user_cost_mgmt_sample_12.png)

Beim Bearbeiten der berechneten Kosten können Sie die Kostenverteilung sowie Status und Datum der Kostenberechnung überprüfen.

#### Schritt 5: Aufgaben erstellen {#step-5---creating-tasks}

Zu dieser Kampagne fügen wir die beiden Aufgaben hinzu, für die die Kostenstrukturen zuvor erstellt wurden (siehe [Schritt 2: Dienstleister konfigurieren und Kostenstrukturen festlegen](#step-2---configuring-the-service-provider-and-defining-the-cost-structures)). Klicken Sie dazu im Kampagnen-Dashboard auf die Schaltfläche **[!UICONTROL Aufgabe hinzufügen]**. Benennen Sie die Aufgabe und klicken Sie auf **[!UICONTROL Speichern]**.

1. Konfigurieren Sie sie wie folgt:

1. Klicken Sie auf **[!UICONTROL Eigenschaften]**, um die Dienstleistung sowie die entsprechende Kostenkategorie auszuwählen:

   ![](assets/s_user_cost_mgmt_sample_14.png)

1. Öffnen Sie anschließend die **[!UICONTROL Ausgaben und Einnahmen]** der Aufgabe und geben Sie ihre Plankosten an.

   ![](assets/s_user_cost_mgmt_sample_15.png)

   Mit Speicherung der Aufgabe übernehmen die berechneten Kosten den für die Plankosten angegebenen Wert.

   Nach Beendung der Aufgabe (Status **[!UICONTROL Abgeschlossen]**) werden die berechneten Kosten automatisch mit den Kosten des Großen Saals aktualisiert (entsprechend der Angabe in seiner Kostenstruktur). Diese Kosten werden ebenfalls der Kategorie zugeordnet.

1. Erstellen Sie auf die gleiche Weise eine zweite Aufgabe mit einer Planung über fünf Tage und verbinden Sie sie mit der zuvor erstellen Kostenstruktur.

   ![](assets/s_user_cost_mgmt_sample_16.png)

   Nach Abschluss der Aufgabe übernehmen die berechneten Kosten den aus der Kostenstruktur stammenden Wert, in unserem Beispiel also 1500 Euro (5 Tage x 300 Euro).

   ![](assets/s_user_cost_mgmt_sample_17.png)

#### Schritt 6: Status des Kampagnenbudgets aktualisieren {#step-6---update-the-campaign-budget-status}

Der Status eines konfigurierten Budgets kann aktualisiert werden: Setzen Sie hierzu den Status auf **[!UICONTROL Angegeben]**. Im Feld der berechneten Kosten der Kampagne wird daraufhin die Summe der für den Versand und die Aufgaben der Kampagne berechneten Kosten angezeigt.

![](assets/s_user_cost_mgmt_sample_18.png)

#### Validierung von Budgets {#budget-approval}

Bei aktivierter Validierung kann das Budget über einen speziellen Link im Kampagnen-Dashboard validiert werden. Der Link wird angezeigt, sobald der Zielgruppenbestimmungs-Workflow gestartet wurde und ein Direkt-Mail-Versand validiert werden muss.

![](assets/s_user_cost_mgmt_sample_19.png)

Sie können dann die Validierung über diesen Link akzeptieren oder ablehnen. Wenn Benachrichtigungen für die Kampagne aktiviert wurden, können Sie den Link auch in der Benachrichtigungs-E-Mail verwenden.

Nach Budgetvalidierung und Abschluss des Versands werden die Kosten automatisch über einen speziellen technischen Workflow weiter verarbeitet.

## Lagerergänzungen und Rechnungen {#orders-and-invoices}

Im Kontext von MRM können Sie bei Dienstleistern aufgebebene Bestellungen und zugehörige Rechnungen erfassen. Der gesamte Kreislauf von Bestellungen, Wareneingängen und Rechnungen kann über Adobe Campaign verwaltet werden.

### Lagerergänzungen {#order-creation}

Um eine Lagerergänzung zu erfassen, gehen Sie zum Knoten **[!UICONTROL MRM > Lagerergänzungen]** des Navigationsbaums und klicken Sie auf die Schaltfläche **[!UICONTROL Neu]**.

Geben Sie die Nummer der Lagerergänzung, den entsprechenden Dienstleister sowie die Gesamtkosten für die Lagerergänzung an.

![](assets/s_user_cost_create_order.png)

### Rechnungen erstellen und verfolgen {#issuing-and-tracking-invoices}

Sie können für jeden Dienstleister Rechnungen speichern und ihren Status sowie das betroffene Budget angeben.

Rechnungen werden im Knoten **[!UICONTROL MRM > Rechnungen]** des Adobe-Campaign-Navigationsbaums erstellt.

![](assets/s_user_cost_create_invoice.png)

Eine Rechnung besteht aus Rechnungszeilen, deren Summe die automatische Berechnung des Betrags ermöglicht. Diese Zeilen werden manuell über die Registerkarte **[!UICONTROL Rechnungszeilen]** erstellt. Sie können einer Bestellung zugeordnet werden, um die Informationen in die Bestellungen hochzuladen.

![](assets/s_user_cost_invoice_add_line.png)

Die Rechnungen jeden Dienstleisters werden im **[!UICONTROL Rechnungen]**-Tab seines Profils angezeigt:

![](assets/s_ncs_user_invoice_from_supplier.png)

Im **[!UICONTROL Details]**-Tab kann der Inhalt der jeweiligen Rechnung eingesehen werden.

Klicken Sie auf **[!UICONTROL Hinzufügen]**, um eine neue Rechnung zu erstellen.

---
title: Kampagnensimulation
seo-title: Kampagnensimulation
description: Kampagnensimulation
seo-description: null
page-status-flag: never-activated
uuid: d5a090ef-57e5-46b2-b9ad-6d4d964c8e20
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: e8e7a720-c93d-491d-8768-270e47e9c898
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Kampagnensimulation{#campaign-simulations}

## Über Simulationen {#about-simulations}

Campaign Optimization ermöglicht es, die Effizienz eines Kampagnenplans mithilfe von Simulationen zu testen. Sie haben so die Möglichkeit, den potenziellen Erfolg einer Kampagne im Detail einzuschätzen, beispielsweise die zu erwartenden Einnahmen, die Zielgruppengröße nach Anwendung der entsprechenden Typologieregeln etc.

Mithilfe der Simulation können die voraussichtlichen Auswirkungen von Sendungen miteinander verglichen werden.

>[!NOTE]
>
>Die im Testmodus vorbereiteten Sendungen wirken sich nicht gegenseitig aufeinander aus, beispielsweise in der Auswertung einer dezentralen Marketingkampagne oder solange der Eintrag der Sendungen in den Planungskalender noch nicht validiert wurde.\
>Das bedeutet, dass Druck- und Kapazitätsregeln nur für Lieferungen im **[!UICONTROL Target estimation and message personalization]** Modus gelten. Lieferungen im **[!UICONTROL Estimation and approval of the provisional target]** und im **[!UICONTROL Target evaluation]** Modus werden nicht berücksichtigt.\
>The delivery mode is chosen in the **[!UICONTROL Typology]** sub-tab of the delivery properties.

![](assets/simu_campaign_select_delivery_mode.png)

## Simulation einrichten {#setting-up-a-simulation}

### Simulation erstellen {#creating-a-simulation}

Folgen Sie den nachstehenden Etappen, um eine Simulation zu erstellen:

1. Go to the **[!UICONTROL Campaigns]** universe, click the **[!UICONTROL More]** link within the **[!UICONTROL Create]** section and select the **[!UICONTROL Simulation]** option.

   ![](assets/simu_campaign_opti_01.png)

1. Geben Sie die Vorlage und den Namen der Simulation ein. Klicken Sie auf **[!UICONTROL Save]** , um die Simulation zu erstellen.

   ![](assets/simu_campaign_opti_02.png)

1. Click the **[!UICONTROL Edit]** tab to configure it.

   ![](assets/simu_campaign_opti_edit.png)

1. Geben Sie auf der **[!UICONTROL Scope]** Registerkarte die Auslieferungen an, die Sie für diese Simulation berücksichtigen möchten. Klicken Sie dazu auf die **[!UICONTROL Add]** Schaltfläche und geben Sie den zu berücksichtigenden Auslieferungsauswahlmodus an.

   ![](assets/simu_campaign_opti_edit_scope.png)

   Sie können entweder jeden Versand einzeln oder alle zu einer bestimmten Kampagne, einem Programm oder einem Plan gehörenden Sendungen auswählen.

   >[!NOTE]
   >
   >Wenn Sie Auslieferungen über einen Plan, ein Programm oder eine Kampagne auswählen, kann Adobe Campaign die Liste der Auslieferungen automatisch aktualisieren, um sie zu berücksichtigen, sobald eine Simulation gestartet wird. Markieren Sie dazu die **[!UICONTROL Refresh the selection of deliveries each time the simulation is started]** Option.
   >  
   >Andernfalls werden nur die zum Zeitpunkt der Simulationserstellung im Plan, Programm oder in der Kampagne vorhandenen Sendungen berücksichtigt: Später hinzugefügte Sendungen werden nicht beachtet.

   ![](assets/simu_campaign_opti_edit_scope_update.png)

1. Wählen Sie die dem Simulationsperimeter hinzuzufügenden Elemente aus. Mithilfe der Umschalt- und der Steuerung-Tasten können Sie mehrere Elemente auf einmal auswählen.

   ![](assets/simu_campaign_opti_edit_scope_select.png)

   Klicken Sie auf **[!UICONTROL Finish]**, um die Auswahl zu bestätigen.

   Es besteht die Möglichkeit, manuell ausgewählte Sendungen mit solchen aus verschiedenen Plänen, Programmen oder Kampagnen zu kombinieren.

   ![](assets/simu_campaign_opti_edit_scope_save.png)

   Bei Bedarf können Sie eine dynamische Bedingung über den **[!UICONTROL Edit the dynamic condition...]** Link verwenden

   Click **[!UICONTROL Save]** to approve this configuration.

   >[!CAUTION]
   >
   >In den Simulationsberechnungen werden nur die Sendungen berücksichtigt, deren Zielgruppe bereits berechnet wurde (Status **Zielbestimmung abgeschlossen** oder **Versandbereit**).

1. In the **[!UICONTROL Calculations]** tab, select an analysis dimension such as the recipient schema for example.

   ![](assets/simu_campaign_opti_dimension.png)

1. Im Anschluss können Sie Ausdrücke hinzufügen.

   ![](assets/simu_campaign_opti_dimension_02.png)

### Ausführungsparameter {#execution-settings}

The **[!UICONTROL General]** tab of the simulation lets you enter execution settings:

* Die **[!UICONTROL Schedule execution for down-time]** Option verschiebt den Simulationsstart je nach Prioritätsstufe auf einen weniger ausgelasteten Zeitraum. Simulationen verwenden wichtige Datenbankressourcen, deshalb sollten nicht dringende Simulationen z. B. für die Nacht geplant werden.
* The **[!UICONTROL Priority]** is the level applied to the simulation to delay its triggering.
* **[!UICONTROL Save SQL queries in the log]**. Mit SQL-Protokollen können Sie eine Simulation diagnostizieren, wenn sie mit Fehlern endet. Sie können Ihnen auch helfen herauszufinden, warum eine Simulation zu langsam ist. Diese Meldungen werden nach der Simulation auf der **[!UICONTROL SQL logs]** Unterregisterkarte der **[!UICONTROL Audit]** Registerkarte angezeigt.

## Simulation starten {#executing-a-simulation}

### Simulation starten {#starting-a-simulation}

Sobald der Perimeter der Simulation definiert wurde, kann sie ausgeführt werden.

To do this, open the simulation dashboard and click **[!UICONTROL Start simulation]**.

![](assets/simu_campaign_opti_start.png)

Once execution is complete, open the simulation and click the **[!UICONTROL Results]** tab to view the targets calculated for each delivery.

![](assets/simu_campaign_opti_results.png)

1. Die **[!UICONTROL Deliveries]** Unterregisterkarte listet alle Lieferungen auf, die bei der Simulation berücksichtigt wurden. Er zeigt zwei Zahlen an:

   * The **[!UICONTROL Initial count]** is the target as it was calculated during its estimation in the delivery.
   * The **[!UICONTROL Final count]** is the number of recipients counted after simulation.

      Der Unterschied zwischen ursprünglicher und endgültiger Zählung spiegelt die vor der Simulation konfigurierten unterschiedlichen Regeln oder Filter wider.

      To learn more about this calculation, edit the **[!UICONTROL Exclusions]** sub-tab.

1. The **[!UICONTROL Exclusions]** sub-tab lets you view the exclusion break-down.

   ![](assets/simu_campaign_opti_14.png)

1. Auf der **[!UICONTROL Alerts]** Unterregisterkarte werden alle während der Simulation generierten Warnmeldungen gruppiert. Warnmeldungen können im Falle einer Kapazitätsüberlastung gesendet werden (wenn beispielsweise die Anzahl der Empfänger die festgelegte Kapazität überschreitet).
1. Auf der **[!UICONTROL Exploration of the exclusions]** Unterregisterkarte können Sie eine Ergebnistabelle erstellen. Der Benutzer muss Variablen in den Achsen abscissa/ordinates angeben.

   For an example of analysis table creation, refer to the end of [Exploring results](#exploring-results).

### Ergebnisse einsehen {#viewing-results}

#### Verfolgung {#audit}

Auf der **[!UICONTROL Audit]** Registerkarte können Sie die Simulationsausführung überwachen. Die **[!UICONTROL SQL Logs]** Unterregisterkarte ist für Benutzer von Experten nützlich. Es listet ausführbare Protokolle im SQL-Format auf. Diese Protokolle werden nur angezeigt, wenn die **[!UICONTROL Save SQL queries in the log]** Option auf der Registerkarte vor der **[!UICONTROL General]** Simulationsausführung ausgewählt wurde.

![](assets/simu_campaign_opti_11.png)

#### Ergebnisse analysieren {#exploring-results}

Auf der **[!UICONTROL Exploration of the exclusions]** Unterregisterkarte können Sie die aus einer Simulation resultierenden Daten analysieren.

Weitere Informationen zur deskriptiven Analyse finden Sie in [diesem Abschnitt](../../reporting/using/about-adobe-campaign-reporting-tools.md).

## Ergebnisse einer Simulation {#results-of-a-simulation}

Die Indikatoren in den Registerkarten **[!UICONTROL Log]** und **[!UICONTROL Results]** bieten einen ersten Überblick über die Simulationsergebnisse. Um eine detailliertere Ansicht der Ergebnisse zu erhalten, öffnen Sie die **[!UICONTROL Reports]** Registerkarte.

### Berichte {#reports}

Um das Ergebnis einer Simulation zu analysieren, nutzen Sie die mit ihr verbundenen Berichte: Sie stellen die Simulationsausschlüsse und ihre Gründe dar.

Standardmäßig werden folgende Berichte angeboten:

* **[!UICONTROL Detail of simulation exclusions]** : Dieser Bericht enthält eine detaillierte Aufstellung der Ausschlussgründe für alle betroffenen Lieferungen.
* **[!UICONTROL Simulation summary]** : Dieser Bericht zeigt die Bevölkerungsgruppen, die während der verschiedenen Lieferungen von der Simulation ausgeschlossen sind.
* **[!UICONTROL Summary of exclusions linked to the simulation]** : Dieser Bericht zeigt ein Diagramm der durch die Simulation verursachten Ausnahmen zusammen mit der angewandten Typologieregel und ein Diagramm mit dem Ausschlussverhältnis pro Regel.

>[!NOTE]
>
>Sie können neue Berichte erstellen und diese den angebotenen Berichten hinzufügen. Weitere Informationen hierzu finden Sie in [diesem Abschnitt](../../reporting/using/about-adobe-campaign-reporting-tools.md).

To access reports, click the **[!UICONTROL Reports]** link of the targeted simulation via its dashboard.

![](assets/campaign_opt_reporting_edit_from_board.png)

You can also edit reports using the **[!UICONTROL Reports]** link accessible from the simulation dashboard.

### Simulationen vergleichen {#comparing-simulations-}

Bei wiederholter Ausführung einer Simulation wird das vorherige Ergebnis durch das neu berechnete Ergebnis ersetzt; die Ergebnisse unterschiedlicher Ausführungen können daher nicht angezeigt und miteinander verglichen werden.

Es besteht jedoch die Möglichkeit, sie mithilfe von Berichten zu vergleichen: Adobe Campaign kann einen Berichtsverlauf speichern, der im Nachhinein angezeigt werden kann. Dieser Verlauf wird über den gesamten Simulations-Lebenszyklus gespeichert.

**Beispiel:**

1. Erstellen Sie eine Simulation für einen Versand, der die Typologie **A** anwendet.
1. Bearbeiten Sie auf der **[!UICONTROL Reports]** Registerkarte einen der verfügbaren Berichte, z. B. **[!UICONTROL Detail of simulation exclusions]** einen.
1. Klicken Sie oben rechts auf das Symbol zur Erstellung eines neuen Verlaufs.

   ![](assets/campaign_opt_reporting_create_hist.png)

1. Schließen Sie diese Simulation und ändern Sie die Konfiguration der Typologie **A**.
1. Führen Sie die Simulation erneut aus und vergleichen Sie das Ergebnis mit dem in dem Bericht angezeigten Ergebnis, in dem zuvor ein Verlauf erstellt wurde.

   ![](assets/campaign_opt_reporting_edit_hist.png)

   Es können beliebig viele Berichtsverläufe gespeichert werden.

### Berichtsachsen {#reporting-axes}

Auf der **[!UICONTROL Calculations]** Registerkarte können Sie Berichtsachsen für das Ziel definieren. Diese Achsen werden bei der Ergebnisanalyse verwendet (siehe [Ergebnisse](#exploring-results)überprüfen).

>[!NOTE]
>
>Es ist empfehlenswert, die Berichtsachsen in einer Simulationsvorlage zu bestimmen und nicht in jeder einzelnen Simulation.\
>Simulationsvorlagen werden im **[!UICONTROL Resources > Templates > Simulation templates]** Knoten der Adobe Campaign-Struktur gespeichert.

**Beispiel:**

Es soll eine zusätzliche Berichtsachse über den Empfängerstatus (&quot;Kunde&quot;, &quot;Interessent&quot; oder kein Status) erstellt werden.

1. Um eine Berichtsachse zu definieren, wählen Sie die Tabelle mit den im **[!UICONTROL Analysis dimension]** Feld zu verarbeitenden Informationen aus. Diese Informationen sind obligatorisch.
1. An dieser Stelle wird das entsprechende Feld der Empfängertabelle ausgewählt.

   ![](assets/simu_campaign_opti_09.png)

1. Folgende Optionen stehen zur Verfügung:

   * **[!UICONTROL Generate target overlap statistics]** Sie können alle Überschneidungsstatistiken im Simulationsbericht wiederherstellen. Überschneidungen sind Empfänger, die in mindestens zwei Auslieferungen innerhalb einer Simulation als Ziel dienen.

      >[!CAUTION]
      >
      >Die Auswahl dieser Option verlängert die Ausführungsdauer der Simulation beträchtlich.

   * **[!UICONTROL Keep the simulation work table]** können Sie Simulationsspuren beibehalten.

      >[!CAUTION]
      >
      >Die systematische Speicherung dieser Tabellen erfordert eine erhöhte Speicherkapazität: Stellen Sie sicher, dass Ihre Datenbank über entsprechenden Speicherplatz verfügt.

When the simulation results are displayed, the information on the selected expression will be displayed in the **[!UICONTROL Overlaps]** sub-tab.

Die Überschneidungen geben die Empfänger an, die in mindestens zwei verschiedenen Sendungen einer Simulation den Zielgruppen angehören.

![](assets/simu_campaign_opti_13.png)

>[!NOTE]
>
>Diese Unterregisterkarte wird nur angezeigt, wenn die **[!UICONTROL Generate target recovery statistics]** Option aktiviert wurde.

Die Informationen zu Berichtsachsen können in Ausschlussanalyseberichten verarbeitet werden, die auf der **[!UICONTROL Exploring exclusions]** Unterregisterkarte erstellt wurden. For more on this, refer to [Exploring results](#exploring-results).

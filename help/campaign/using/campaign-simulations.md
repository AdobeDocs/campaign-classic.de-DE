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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1376'
ht-degree: 100%

---


# Kampagnensimulation{#campaign-simulations}

## Über Simulationen {#about-simulations}

Campaign Optimization ermöglicht es, die Effizienz eines Kampagnenplans mithilfe von Simulationen zu testen. Sie haben so die Möglichkeit, den potenziellen Erfolg einer Kampagne im Detail einzuschätzen, beispielsweise die zu erwartenden Einnahmen, die Zielgruppengröße nach Anwendung der entsprechenden Typologieregeln etc.

Mithilfe der Simulation können die voraussichtlichen Auswirkungen von Sendungen miteinander verglichen werden.

>[!NOTE]
>
>Die im Testmodus vorbereiteten Sendungen wirken sich nicht gegenseitig aufeinander aus, beispielsweise in der Auswertung einer dezentralen Marketingkampagne oder solange der Eintrag der Sendungen in den Planungskalender noch nicht validiert wurde.\
>So werden die Druck- und Kapazitätsregeln nur auf Sendungen im Modus **[!UICONTROL Zielgruppenschätzung und Nachrichtenpersonalisierung]** angewandt. Die Sendungen im Modus **[!UICONTROL Schätzung und Validierung der geplanten Zielgruppe]** und **[!UICONTROL Zielgruppenevaluierung]** werden nicht berücksichtigt.\
>Der Versandmodus wird in den Eigenschaften des jeweiligen Versands im Tab **[!UICONTROL Typologie]** ausgewählt.

![](assets/simu_campaign_select_delivery_mode.png)

## Simulation einrichten {#setting-up-a-simulation}

### Simulation erstellen {#creating-a-simulation}

Folgen Sie den nachstehenden Etappen, um eine Simulation zu erstellen:

1. Klicken Sie in der Rubrik **[!UICONTROL Kampagnen]** im Abschnitt **[!UICONTROL Erstellen]** auf den Link **[!UICONTROL Andere Optionen]** und wählen Sie **[!UICONTROL Simulation]** aus.

   ![](assets/simu_campaign_opti_01.png)

1. Wählen Sie eine Simulationsvorlage aus und geben Sie einen Titel an. Klicken Sie auf die Schaltfläche **[!UICONTROL Speichern]**, um die Simulation zu erstellen.

   ![](assets/simu_campaign_opti_02.png)

1. Klicken Sie auf den Tab **[!UICONTROL Bearbeiten]**, um sie zu konfigurieren.

   ![](assets/simu_campaign_opti_edit.png)

1. Geben Sie im Tab **[!UICONTROL Perimeter]** die für diese Simulation zu berücksichtigenden Sendungen an. Klicken Sie hierfür auf die Schaltfläche **[!UICONTROL Hinzufügen]** und wählen Sie den gewünschten Modus aus.

   ![](assets/simu_campaign_opti_edit_scope.png)

   Sie können entweder jeden Versand einzeln oder alle zu einer bestimmten Kampagne, einem Programm oder einem Plan gehörenden Sendungen auswählen.

   >[!NOTE]
   >
   >Wenn Sie die Sendungen eines Plans, eines Programms oder einer Kampagne auswählen, kann Adobe Campaign automatisch die Liste der zu berücksichtigenden Sendungen bei jedem Simulationsstart aktualisieren. Kreuzen Sie dafür die Option **[!UICONTROL Versandauswahl bei jedem Simulationsstart aktualisieren]** an.
   >  
   >Andernfalls werden nur die zum Zeitpunkt der Simulationserstellung im Plan, Programm oder in der Kampagne vorhandenen Sendungen berücksichtigt: Später hinzugefügte Sendungen werden nicht beachtet.

   ![](assets/simu_campaign_opti_edit_scope_update.png)

1. Wählen Sie die dem Simulationsperimeter hinzuzufügenden Elemente aus. Mithilfe der Umschalt- und der Steuerung-Tasten können Sie mehrere Elemente auf einmal auswählen.

   ![](assets/simu_campaign_opti_edit_scope_select.png)

   Klicken Sie auf die Schaltfläche **[!UICONTROL Beenden]**, um die Auswahl zu bestätigen.

   Es besteht die Möglichkeit, manuell ausgewählte Sendungen mit solchen aus verschiedenen Plänen, Programmen oder Kampagnen zu kombinieren.

   ![](assets/simu_campaign_opti_edit_scope_save.png)

   Über den Link **[!UICONTROL Dynamische Bedingung bearbeiten]** können Sie eine dynamische Bedingung hinzufügen..

   Klicken Sie zur Bestätigung der Konfiguration auf die Schaltfläche **[!UICONTROL Speichern]**.

   >[!NOTE]
   >
   >In den Simulationsberechnungen werden nur die Sendungen berücksichtigt, deren Zielgruppe bereits berechnet wurde (Status **Zielbestimmung abgeschlossen** oder **Versandbereit**).

1. Wählen Sie im **[!UICONTROL Berechnungen]**-Tab eine Analysedimension, beispielsweise das Empfängerschema aus.

   ![](assets/simu_campaign_opti_dimension.png)

1. Im Anschluss können Sie Ausdrücke hinzufügen.

   ![](assets/simu_campaign_opti_dimension_02.png)

### Ausführungsparameter {#execution-settings}

Im Tab **[!UICONTROL Allgemein]** der Simulation können Sie ihre Ausführungsparameter eingeben:

* Die Option **[!UICONTROL Ausführung auf einen Zeitpunkt mit geringer Auslastung verschieben]** verschiebt die Simulation auf einen weniger ausgelasteten Zeitpunkt, entsprechend der gewählten Priorität. Da Simulationen umfangreiche Datenbankressourcen in Anspruch nehmen, sollten weniger dringende Simulationen zum Beispiel nachts ausgeführt werden.
* Die **[!UICONTROL Priorität]** entspricht der Dringlichkeit, die der Simulation zugeteilt wird, um sie schnellstmöglich durchzuführen oder ihren Start zu verzögern.
* Option **[!UICONTROL SQL-Abfragen im Protokoll speichern]**: SQL-Logs dienen dazu, fehlerhafte oder zu langsame Simulationen zu diagnostizieren. Die entsprechenden Logs sind nach der Simulation im Untertab **[!UICONTROL SQL-Logs]** des Tabs **[!UICONTROL Verfolgung]** verfügbar.

## Simulation starten {#executing-a-simulation}

### Simulation starten {#starting-a-simulation}

Sobald der Perimeter der Simulation definiert wurde, kann sie ausgeführt werden.

Öffnen Sie das Simulations-Dashboard und klicken Sie auf die Schaltfläche **[!UICONTROL Simulation starten]**.

![](assets/simu_campaign_opti_start.png)

Öffnen Sie nach der Ausführung die Simulation und klicken Sie auf den Tab **[!UICONTROL Ergebnisse]**, um die für die Sendungen berechneten Zielgruppen anzuzeigen.

![](assets/simu_campaign_opti_results.png)

1. Im Untertab **[!UICONTROL Sendungen]** werden die von der Simulation berücksichtigten Sendungen in zwei Zählungen aufgelistet:

   * Die **[!UICONTROL Ursprüngliche Zählung]** entspricht der Schätzung der Zielgruppe auf Ebene des Versands;
   * Die **[!UICONTROL Endgültige Zählung]** zeigt die Anzahl der nach Ausführung der Simulation verbleibenden Empfänger an.

      Der Unterschied zwischen ursprünglicher und endgültiger Zählung spiegelt die vor der Simulation konfigurierten unterschiedlichen Regeln oder Filter wider.

      Gehen Sie in den Untertab **[!UICONTROL Ausschlüsse]**, um die Details der Berechnung anzusehen.

1. Die **[!UICONTROL Ausschlüsse]** werden nach Sendungen aufgestaffelt dargestellt.

   ![](assets/simu_campaign_opti_14.png)

1. Der Untertab **[!UICONTROL Warnungen]** fasst alle bei der Simulation erzeugten Warnnachrichten zusammen. Diese können den Benutzer bei Überschreitung der Kapazität benachrichtigen (wenn beispielsweise die Zielgruppe mehr Empfänger enthält, als die festgelegte Kapazität zulässt).
1. Im Untertab **[!UICONTROL Ausschlussanalyse]** kann eine Tabelle zur übersichtlichen Darstellung der Ergebnisse erstellt werden. Der Benutzer gibt die jeweiligen Variablen für die Abszissen- und Ordinatenachsen an.

   Ein Beispiel zur Erstellung einer Analysetabelle findet sich im Anschluss an den Abschnitt [Ergebnisse analysieren](#exploring-results).

### Ergebnisse einsehen {#viewing-results}

#### Verfolgung {#audit}

Über den Tab **[!UICONTROL Verfolgung]** können Sie die Ausführung der Simulation überwachen. Insbesondere für erfahrene Benutzer ist hier der Untertab **[!UICONTROL SQL-Logs]** hilfreich, auf dem die Ausführungslogs im SQL-Format aufgeführt werden. Damit die SQL-Logs angezeigt werden, muss vor Ausführung der Simulation im Tab **[!UICONTROL Allgemein]** die Option **[!UICONTROL SQL-Abfragen im Protokoll speichern]** aktiviert werden.

![](assets/simu_campaign_opti_11.png)

#### Ergebnisse analysieren {#exploring-results}

Der Untertab **[!UICONTROL Ausschlussanalyse]** ermöglicht die Analyse der aus der Simulation resultierenden Daten.

Weitere Informationen zur deskriptiven Analyse finden Sie in [diesem Abschnitt](../../reporting/using/about-adobe-campaign-reporting-tools.md).

## Ergebnisse einer Simulation {#results-of-a-simulation}

Die im Tab **[!UICONTROL Ergebnisse]** dargestellten Indikatoren geben einen ersten Einblick in das Ergebnis der Simulation. Anhand der vom Simulations-Dashboard aus verfügbaren **[!UICONTROL Berichte]** können Sie eine präzise Analyse der Informationen vornehmen.****

### Berichte {#reports}

Um das Ergebnis einer Simulation zu analysieren, nutzen Sie die mit ihr verbundenen Berichte: Sie stellen die Simulationsausschlüsse und ihre Gründe dar.

Standardmäßig werden folgende Berichte angeboten:

* **[!UICONTROL Detail der Simulationsausschlüsse]**: Dieser Bericht bietet eine detaillierte Tabelle aller Ausschlussgründe für alle von dieser Simulation betroffenen Sendungen.
* **[!UICONTROL Simulationszusammenfassung]**: Dieser Bericht zeigt den Umfang der von der Simulation ausgeschlossenen Zielgruppen gestaffelt nach Sendungen an.
* **[!UICONTROL Zusammenfassung der simulationsbedingten Ausschlüsse]**: Dieser Bericht zeigt eine Tabelle der Ausschlüsse durch die Simlation an. Des weiteren werden die Typologieregeln aufgeführt, die zum Ausschluss geführt haben sowie ihr jeweiliger Anteil an den regelbedingten Ausschlüssen.

>[!NOTE]
>
>Sie können neue Berichte erstellen und diese den angebotenen Berichten hinzufügen. Weitere Informationen hierzu finden Sie in [diesem Abschnitt](../../reporting/using/about-adobe-campaign-reporting-tools.md).

Um Berichte zu öffnen, klicken Sie auf den für die jeweilige Simulation im Dashboard verfügbaren **[!UICONTROL Berichte]**-Link.

![](assets/campaign_opt_reporting_edit_from_board.png)

Klicken Sie auf den Link **[!UICONTROL Berichte]** auf dem Dashboard der entsprechenden Simulation, um auf die Berichte zuzugreifen.

### Simulationen vergleichen {#comparing-simulations-}

Bei wiederholter Ausführung einer Simulation wird das vorherige Ergebnis durch das neu berechnete Ergebnis ersetzt; die Ergebnisse unterschiedlicher Ausführungen können daher nicht angezeigt und miteinander verglichen werden.

Es besteht jedoch die Möglichkeit, sie mithilfe von Berichten zu vergleichen: Adobe Campaign kann einen Berichtsverlauf speichern, der im Nachhinein angezeigt werden kann. Dieser Verlauf wird über den gesamten Simulations-Lebenszyklus gespeichert.

**Beispiel:**

1. Erstellen Sie eine Simulation für einen Versand, der die Typologie **A** anwendet.
1. Öffnen Sie im Tab **[!UICONTROL Berichte]** einen der verfügbaren Berichte, zum Beispiel **[!UICONTROL Detail der simulationsbedingten Ausschlüsse]**.
1. Klicken Sie oben rechts auf das Symbol zur Erstellung eines neuen Verlaufs.

   ![](assets/campaign_opt_reporting_create_hist.png)

1. Schließen Sie diese Simulation und ändern Sie die Konfiguration der Typologie **A**.
1. Führen Sie die Simulation erneut aus und vergleichen Sie das Ergebnis mit dem in dem Bericht angezeigten Ergebnis, in dem zuvor ein Verlauf erstellt wurde.

   ![](assets/campaign_opt_reporting_edit_hist.png)

   Es können beliebig viele Berichtsverläufe gespeichert werden.

### Berichtsachsen {#reporting-axes}

Auf dem Tab **[!UICONTROL Berechnungen]** können Sie Berichtsachsen bezüglich der Zielgruppe definieren. Diese Achsen werden bei der Ergebnisanalyse verwendet (siehe [Ergebnisse analysieren](#exploring-results)).

>[!NOTE]
>
>Es ist empfehlenswert, die Berichtsachsen in einer Simulationsvorlage zu bestimmen und nicht in jeder einzelnen Simulation.\
>Die Simulationsvorlagen werden im Knoten **[!UICONTROL Ressourcen > Vorlagen > Simulationsvorlagen]** des Adobe-Campaign-Navigationsbaums gespeichert.

**Beispiel:**

Es soll eine zusätzliche Berichtsachse über den Empfängerstatus (&quot;Kunde&quot;, &quot;Interessent&quot; oder kein Status) erstellt werden.

1. Um eine Berichtsachse zu bestimmen, wählen Sie die Tabelle der zu nutzenden Informationen im Feld **[!UICONTROL Analysedimension]** aus.
1. An dieser Stelle wird das entsprechende Feld der Empfängertabelle ausgewählt.

   ![](assets/simu_campaign_opti_09.png)

1. Folgende Optionen stehen zur Verfügung:

   * **[!UICONTROL Statistiken der Zielgruppenüberschneidung erzeugen]**, um alle Überschneidungsstatistiken im Simulationsbericht zu erhalten. Die Überschneidung entspricht den Empfängern, die in mindestens zwei Sendungen einer Simulation der Zielgruppe angehören.

      >[!IMPORTANT]
      >
      >Die Auswahl dieser Option verlängert die Ausführungsdauer der Simulation beträchtlich.

   * **[!UICONTROL Simulationsarbeitstabelle beibehalten]**, um Spuren der Simulation zu speichern.

      >[!IMPORTANT]
      >
      >Die systematische Speicherung dieser Tabellen erfordert eine erhöhte Speicherkapazität: Stellen Sie sicher, dass Ihre Datenbank über entsprechenden Speicherplatz verfügt.

Bei der Anzeige der Simulationsergebnisse werden Informationen bezüglich des ausgewählten Ausdrucks im Untertab **[!UICONTROL Überschneidungen]** angezeigt.

Die Überschneidungen geben die Empfänger an, die in mindestens zwei verschiedenen Sendungen einer Simulation den Zielgruppen angehören.

![](assets/simu_campaign_opti_13.png)

>[!NOTE]
>
>Dieser Untertab wird nur angezeigt, wenn die Option **[!UICONTROL Statistiken der Zielgruppenüberschneidung erzeugen]** aktiviert wurde.

Informationen bezüglich der Berichtsachsen können in den Berichten der Ausschlussanalyse genutzt werden, die im Unter-Tab **[!UICONTROL Ausschlussanalyse]** erstellt werden. Weitere Informationen hierzu finden Sie im Abschnitt [Ergebnisse analysieren](#exploring-results).

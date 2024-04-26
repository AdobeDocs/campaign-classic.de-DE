---
product: campaign
title: Zugriff auf Marketing-Kampagnen
description: Zugriff auf Marketing-Kampagnen
role: User
feature: Campaigns, Cross Channel Orchestration
exl-id: 1278bda1-f83c-4d38-8042-e6611755cf36
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: ht
source-wordcount: '1217'
ht-degree: 100%

---

# Auf Marketing-Kampagnen zugreifen{#accessing-marketing-campaigns}

Adobe Campaign ermöglicht die Erstellung, Konfiguration, Ausführung und Analyse von Marketing-Kampagnen. Die Anwendung stellt somit ein einheitliches Kontrollzentrum dar, über das alle Marketing-Kampagnen verwaltet werden können.

## Grundlagen zum Arbeitsbereich {#workspace-basics}

### Startseite         {#home-page}

Sobald die Verbindung mit Adobe Campaign hergestellt wurde, können Sie die verschiedenen Funktionen mithilfe von Links in der Navigationsleiste durchsuchen.


![](assets/campaign_global_view.png)


Die Kampagnenelemente befinden sich auf der Registerkarte **[!UICONTROL Kampagnen]**: Hier erhalten Sie einen Überblick über die Marketing-Programme und -Kampagnen sowie deren Untergruppen. Ein Marketing-Programm besteht aus Kampagnen, die ihrerseits aus Sendungen, Aufgaben, verknüpften Ressourcen usw. bestehen. Im Zusammenhang mit der Marketing Campaign Management-Funktion von Campaign sind die Informationen über Sendungen, Budgets, Validierungsverantwortliche und verlinkte Dokumente in den Kampagnen zu finden.

Der **[!UICONTROL Navigationsblock]** im Tab **[!UICONTROL Kampagnen]** enthält je nach installierten Instanzmodulen verschiedene Einträge. Sie können beispielsweise auf Folgendes zugreifen:

* **Kampagnenkalender**: Kalender der Pläne, Marketing-Programme, Sendungen und Kampagnen. Siehe [Kampagnenkalender](#campaign-calendar).
* **Kampagnen**: Zugriff auf alle in Marketing-Programmen enthaltenen Kampagnen;
* **Sendungen**: Zugriff auf in Kampagnen enthaltene Sendungen;
* **Web-Anwendungen**: Zugriff auf Web-Anwendungen (Formulare, Landingpages usw.).

>[!NOTE]
>
>Der strukturelle Aufbau der Adobe-Campaign-Konsole, Berechtigungen sowie die Profilverwaltung werden in [diesem Abschnitt](../../platform/using/adobe-campaign-workspace.md) beschrieben.
>
>Im Zusammenhang mit Kanälen und Sendungen stehende Funktionalitäten werden in [diesem Abschnitt](../../delivery/using/steps-about-delivery-creation-steps.md) erläutert.

### Kampagnenkalender {#campaign-calendar}

Jede Kampagne gehört zu einem Programm, das wiederum zu einem Plan gehört. Der Zugriff auf Pläne, Programme und Kampagnen erfolgt über das Menü **[!UICONTROL Kampagnenkalender]** auf der Registerkarte **Kampagnen**.

Um einen Plan, ein Programm, eine Kampagne oder einen Versand zu bearbeiten, klicken Sie auf den jeweiligen Titel im Kalender und anschließend auf den Link **[!UICONTROL Öffnen…]**. Das gewünschte Element öffnet sich in einem neuen Tab:

![](assets/d_ncs_user_interface_hierar.png)

Sie haben die Möglichkeit, die im Kampagnenkalender angezeigten Informationen zu filtern. Klicken Sie hierzu auf den Link **[!UICONTROL Filtern]** und wählen Sie die gewünschten Kriterien aus.

![](assets/campaign_planning_filter.png)

>[!NOTE]
>
>Wenn Sie nach einem Datum filtern, werden alle Kampagnen angezeigt, deren Startdatum nach dem angegebenen Datum liegt und/oder deren Enddatum vor dem angegebenen Datum liegt. Datumsangaben können in den Kalendern rechts von jedem Feld ausgewählt werden.

Sie können zur Filterung der angezeigten Elemente auch das Feld **[!UICONTROL Suchen]** verwenden.

Die den Elementen zugeordneten Symbole geben Auskunft über ihren jeweiligen Status: Abgeschlossen, In Gang, In Bearbeitung usw.

### Navigation in einem Marketing-Programm {#browsing-in-a-marketing-program}

Campaign ermöglicht die Verwaltung von Programmen, die aus unterschiedlichen Marketing-Kampagnen bestehen. Jede dieser Kampagnen setzt sich wiederum aus Sendungen und mit diesen verbundenen Vorgängen und Ressourcen zusammen.

#### In einem Programm navigieren {#browsing-a-program}

Zur Konfiguration und Bearbeitung eines Programms stehen die folgenden Registerkarten zur Verfügung:

* Auf der Registerkarte **Planung** können Sie sich den Programmkalender nach Monat, Woche oder Tag anzeigen lassen, indem Sie in der Kalenderkopfzeile auf die jeweilige Registerkarte klicken.

  Bei Bedarf können an dieser Stelle auch Programme, Kampagnen oder Aufgaben erstellt werden.

  ![](assets/s_ncs_user_interface_campaign02.png)

* Über den Tab **Bearbeiten** kann das Programm konfiguriert und verändert werden (Name, Beginn und Ende, Budget, benötigte Dokumente usw.).

  ![](assets/s_ncs_user_interface_campaign05.png)

#### Kampagnen durchsuchen {#browsing-campaigns}

Kampagnen sind über den Kampagnenkalender, über den Tab **[!UICONTROL Planung]** des entsprechenden Programms und über die Liste der Kampagnen verfügbar:

1. Über den Kampagnenkalender können Sie die gewünschte Kampagne auswählen und auf den Link **[!UICONTROL Öffnen]** klicken.

   ![](assets/campaign_planning_edit_op.png)

   Die Kampagne öffnet sich daraufhin in einem neuen Tab:

   ![](assets/campaign_op_edit.png)

1. Über den Tab **[!UICONTROL Planung]** des Programms kann die Kampagne auf die gleiche Weise wie im Kalender geöffnet werden.
1. Über den Link **[!UICONTROL Kampagnen]** im Tab **[!UICONTROL Kampagnen]** wird eine Liste aller Kampagnen aufgerufen. Klicken Sie auf den Namen der Kampagne, die Sie bearbeiten möchten.

   ![](assets/campaign_edit_from_list.png)

### Steuerung einer Kampagne {#controlling-a-campaign}

#### Dashboard {#dashboard}

Alle Kampagnen, Vorgänge und Ressourcen werden in einem zentralen Bildschirm, dem Dashboard, zusammengefasst, um eine kollaborative Verwaltung der Marketing-Aktionen zu ermöglichen.

Das Dashboard einer Kampagne wird wie eine Kontrollschnittstelle verwendet. Es ermöglicht den direkten Zugriff auf die wichtigsten Etappen der Kampagnenerstellung und -verwaltung: Sendungen, Extraktonsdateien, Benachrichtigungen, Budgets usw.

![](assets/s_ncs_user_op_board_start_del.png)

Adobe Campaign ermöglicht den Einsatz kollaborativer Prozesse zur Ausführung und Validierung der unterschiedlichen Etappen von Marketing- und Kommunikationskampagnen, darunter die Budget-, Zielgruppen- und Inhaltsvalidierung.

![](assets/s_ncs_user_op_board_validate.png)

>[!NOTE]
>
>Die Konfiguration von Kampagnenvorlagen wird im Abschnitt [Kampagnenvorlagen](../../campaign/using/marketing-campaign-templates.md#campaign-templates) beschrieben.

#### Planung {#schedule}

Eine Kampagne zentralisiert eine Gruppe von Sendungen. Für jede Kampagne bietet die Planung eine globale Ansicht aller Komponenten: Sie können die Aufgaben und Sendungen anzeigen und leicht darauf zugreifen.

![](assets/campaign_planning_tab.png)

#### Forum {#forum}

Jede Kampagne verfügt über ein dediziertes Forum, in dem beteiligte Benutzerinnen und Benutzer Nachrichten austauschen können.

Weitere Informationen finden Sie in den [Diskussionsforen](../../mrm/using/discussion-forums.md).

#### Berichte {#reports}

Über den Link **[!UICONTROL Berichte]** können die Kampagnenberichte eingesehen werden.

![](assets/campaign_reporting_tab.png)

>[!NOTE]
>
>Weitere Informationen zu Berichten finden Sie in [diesem Abschnitt](../../reporting/using/about-adobe-campaign-reporting-tools.md).

#### Konfiguration {#configuration}

Kampagnen werden basierend auf Kampagnenvorlagen erstellt. Diese wiederverwendbaren Vorlagen können so konfiguriert werden, dass bestimmte Optionen und Einstellungen bereits ausgewählt und gespeichert sind. Für jede Kampagne stehen folgende Funktionalitäten zur Verfügung:

* Referenzierung von [Dokumenten und Ressourcen](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents): Sie können mit der Kampagne Dokumente (Briefing, Bericht, Bilder usw.) verknüpfen. Alle Dokumentformate werden unterstützt.
* Kostenbestimmung: Mit Adobe Campaign ist es möglich, für jede Kampagne [Kostenkategorien und Berechnungsstrukturen für Kosten](../../campaign/using/providers-stocks-and-budgets.md#defining-cost-categories) zu definieren, die beim Erstellen einer Marketing-Kampagne verwendet werden können, z. B. Druckkosten, Inanspruchnahme eines externen Dienstleisters, Raummiete usw.
* Definition von Zielvorgaben: Sie können für eine Kampagne quantifizierbare Zielvorgaben definieren, z. B. die Anzahl der Abonnentinnen und Abonnenten, das Geschäftsvolumen usw. Diese Informationen werden später in den Kampagnenberichten verwendet.
* Verwaltung von [Testadressen](../../delivery/using/about-seed-addresses.md) und [Kontrollgruppen](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).
* Validierungsverwaltung: Sie können die zu validierenden Abwandlungen sowie bei Bedarf validierungsverantwortliche Benutzerinnen bzw. Benutzer oder Benutzergruppen auswählen. [Weitere Informationen](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)

>[!NOTE]
>
>Wenn Sie die Kampagneneinstellungen öffnen und ändern möchten, klicken Sie auf den Link **[!UICONTROL Erweiterte Kampagnenparameter...]** im Tab **[!UICONTROL Bearbeiten]**.

## Web-Zugriff {#using-the-web-interface-}

Sie haben die Möglichkeit, über einen Webbrowser auf die Adobe-Campaign-Konsole zuzugreifen, um alle Kampagnen und ihre Sendungen sowie Berichte und Informationen bezüglich der Profile Ihrer Datenbank einzusehen. Über den Webzugriff können keine Datensätze erstellt werden. Sie können jedoch eingesehen und entsprechend der jeweiligen Benutzerberechtigungen weiterverarbeitet werden. So können beispielsweise Inhalte und Zielgruppen der Kampagnen validiert oder Sendungen unterbrochen werden.

1. Melden Sie sich wie gewohnt über https://`<your instance>:<port>/view/home` an.
1. Über die unterschiedlichen Rubriken besteht Zugriff auf Listen und weitere Navigationselemente.

   ![](assets/s_ncs_user_interface_web_campaign_01.png)

Neben dem Navigieren durch und Ansehen von Kampagnen können Sie auch die folgenden Aufgaben ausführen:

* Überwachen von Aktivitäten in einer Instanz
* Teilnahme an Validierungsprozessen, beispielsweise an der Validierung von Versandinhalten
* Durchführen anderer Schnellaktionen, z. B. Pausieren eines Workflows
* Zugriff auf alle Reporting-Funktionen
* Teilnahme an Forumsdiskussionen

Diese Tabelle fasst die Aktionen zusammen, die Sie über einen Browser für Kampagnen durchführen können:

| Seite  | Aktion |
| --- | --- |
| Liste der Kampagnen, Sendungen, Angebote usw. | Löschen von Listenelementen |
| Kampagne | Abbrechen einer Kampagne |
| Versand | Inhalt und Zielgruppe des Versands validieren<br/>Versandinhalt übermitteln<br/>Versand bestätigen<br/>Versand anhalten und stoppen |
| Web-Programm | Web-Programm erstellen<br/>Bearbeiten des Programminhalts und der Eigenschaften<br/>Programminhalt als Vorlage speichern<br/>Programm veröffentlichen |
| Angebot | Inhalt und Eignung des Angebots validieren<br/>Online-Angebot deaktivieren |
| Aufgabe | Aufgabe abschließen<br/>Aufgabe abbrechen |
| Marketing-Ressourcen | Ressource validieren<br/>Ressource sperren und entsperren |
| Kampagnenkit | Kit zur Genehmigung einreichen<br/>Kit genehmigen oder ablehnen<br/>Kit abbrechen |
| Kampagnenbestellung | Bestellung erstellen<br/>Bestellung annehmen oder ablehnen <!-- Je n'ai pas pu créer de campaign order pour vérifier cela. Peut-on accéder à ces fonctionnalités depuis l'accès web ? --> |
| Lager | Lagerposition löschen |
| Angebotssimulation | Simulation starten und stoppen |
| Zielgruppenbestimmungs-Workflow | Workflow starten, pausieren und stoppen |
| Bericht | Aktuelle Daten im Berichtsverlauf speichern |
| Forum | Diskussion hinzufügen<br/>Eine Nachricht in einer Diskussion beantworten<br/>Einer Diskussion folgen und das Abonnement beenden |

### Validierungen

Validierungen (beispielsweise einer Zielgruppe oder des Inhalts eines Versands) können über die Web-Schnittstelle erfolgen.

![](assets/campaign_web_interface_validation.png)

Sie können auch den in den Benachrichtigungsinhalten enthaltenen Link verwenden. Weitere Informationen hierzu finden Sie unter [Kontrolle und Validierung von Sendungen](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).

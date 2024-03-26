---
product: campaign
title: Synchronisieren von Audiences
description: Erfahren Sie, wie Sie Audiences mit dem ACS-Connector synchronisieren
feature: ACS Connector
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
hide: true
hidefromtoc: true
exl-id: 88e581cf-43cd-4c43-9347-d016c62fdf42
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1192'
ht-degree: 83%

---

# Synchronisieren von Audiences{#synchronizing-audiences}



Sie können mit den erweiterten Funktionen von Campaign v7 eine umfangreiche Liste erstellen und als Audience direkt und in Echtzeit in Campaign Standard freigeben (einschließlich zusätzlicher Daten). Ihr Campaign-Standard-Benutzer kann dann die Audience in Adobe Campaign Standard verwenden.

Eine komplexe Zielgruppenbestimmung einschließlich zusätzlicher Daten, die nicht in Campaign Standard repliziert werden, kann nur mithilfe von Campaign v7 durchgeführt werden.

Sie können auch über einen Connector wie beispielsweise Microsoft Dynamics bereitgestellte Empfänger- oder Datenlisten einfach in Campaign Standard freigeben.

Dieser Anwendungsfall zeigt, wie Sie in Campaign v7 einen Zieldatensatz für den Versand vorbereiten und gemeinsam mit zusätzlichen Daten in einem in Adobe Campaign Standard erstellten und durchgeführten Versand verwenden können.

>[!NOTE]
>
>Zusätzlich können Sie Daten mit Aggregaten und Sammlungen in Adobe Campaign Standard anreichern, wenn alle erforderlichen Daten bereits repliziert wurden.

## Voraussetzungen {#prerequisites}

Dazu ist Folgendes erforderlich:

* Empfänger, die in der Campaign v7-Datenbank gespeichert und mit Campaign Standard synchronisiert werden. Siehe Abschnitt [Profile synchronisieren](../../integrations/using/synchronizing-profiles.md).
* Zusätzliche in Tabellen gespeicherte Daten, wie Abmeldungen oder Transaktionen, die mit nms:recipients in der Campaign v7-Datenbank verknüpft sind. Diese Daten können aus nativen Schemata oder benutzerdefinierten Tabellen in Campaign v7 stammen. Sie sind standardmäßig nicht in Campaign Standard verfügbar, da sie nicht synchronisiert werden.
* Die Berechtigung zur Durchführung von Workflows in sowohl Campaign v7 als auch Campaign Standard.
* Die Berechtigung zur Erstellung und Durchführung eines Versands in Campaign Standard.

## Zielgruppenbestimmungs-Workflow mit zusätzlichen Daten in Campaign v7 erstellen {#create-a-targeting-workflow-with-additional-data-in-campaign-v7}

Eine komplexe Zielgruppenbestimmung einschließlich zusätzlicher Daten, die nicht in Campaign Standard repliziert werden, kann nur mithilfe von Campaign v7 durchgeführt werden.

Nachdem die Zielgruppe und ihre zusätzlichen Daten definiert wurden, können sie als Liste gespeichert und in Campaign Standard freigegeben werden.

>[!NOTE]
>
>Dies ist ein Beispiel. Je nach Anforderungen können Sie eine Empfängerliste einfach abfragen und in ACS ohne jegliche Weiterverarbeitung freigeben. Sie können zur Erstellung Ihrer endgültigen Zielgruppe auch andere Datenverwaltungsaktivitäten nutzen.

Gehen Sie folgendermaßen vor, um die endgültige Audience und ihre zusätzlichen Daten zu erhalten:

1. Erstellen Sie einen neuen Workflow in **[!UICONTROL Profile und Zielgruppen]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Zielgruppen-Workflow]**.
1. Fügen Sie die Aktivität **[!UICONTROL Abfrage]** hinzu und wählen Sie die Empfänger aus, denen Sie die E-Mail senden möchten, wie z. B. alle Empfänger zwischen 18 und 30 Jahren, die in Frankreich leben.

   ![](assets/acs_connect_query1.png)

1. Fügen Sie zusätzliche Daten aus der Abfrage hinzu. Weitere Informationen finden Sie im Abschnitt [Daten hinzufügen](../../workflow/using/query.md#adding-data) Abschnitt.

   In diesem Beispiel wird gezeigt, wie ein Aggregat hinzugefügt wird, das zählt, wie viele Sendungen ein Empfänger pro Jahr erhält.

   Wählen Sie in **[!UICONTROL Abfrage]** die Option **[!UICONTROL Daten hinzufügen...]**.

   ![](assets/acs_connect_query2.png)

1. Wählen Sie zuerst **[!UICONTROL Daten in Relation mit der Filterdimension]** und danach **[!UICONTROL Weiter]** aus.

   ![](assets/acs_connect_query3.png)

1. Wählen Sie **[!UICONTROL Daten in Relation mit der Filterdimension]** und danach den Knoten **[!UICONTROL Versandlogs des Empfängers]** und abschließend **[!UICONTROL Weiter]** aus.

   ![](assets/acs_connect_query4.png)

1. Wählen Sie **[!UICONTROL Aggregate]** im Feld **[!UICONTROL Abgerufene Daten]** und danach **[!UICONTROL Weiter]** aus.

   ![](assets/acs_connect_query5.png)

1. Fügen Sie eine Filterbedingung hinzu, sodass nur Logs berücksichtigt werden, die in den letzten 365 Tagen erstellt wurden, und klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/acs_connect_query6.png)

1. Definieren Sie die Ausgabespalten. In unserem Beispiel ist nur eine einzige Spalte nötig, in der die Anzahl der Sendungen gezählt wird. Gehen Sie dazu folgendermaßen vor:

   * Wählen Sie rechts im Fenster **[!UICONTROL Hinzufügen]**.
   * Wählen Sie im Fenster **[!UICONTROL Feldauswahl]** die Schaltfläche **[!UICONTROL Erweiterte Auswahl]** aus.
   * Auswählen **[!UICONTROL Aggregat]**, dann **[!UICONTROL Count]**. Überprüfen Sie die **[!UICONTROL Unterschiedlich]** und klicken Sie auf **[!UICONTROL Nächste]**.
   * Wählen Sie in der Liste der Felder das für die **Count** -Funktion. Wählen Sie ein Feld aus, das immer ausgefüllt wird, z. B. die **[!UICONTROL Primärer Schlüssel]** und klicken Sie auf **[!UICONTROL Beenden]**.
   * Ändern Sie den Ausdruck im **[!UICONTROL Alias]** Spalte. Mit diesem Alias können Sie die hinzugefügte Spalte im endgültigen Versand einfach abrufen. Beispiel **NBdeliveries**.
   * Wählen Sie **[!UICONTROL Beenden]** aus und speichern Sie die Konfiguration der Aktivität **[!UICONTROL Abfrage]**.

   ![](assets/acs_connect_query7.png)

1. Speichern Sie den Workflow. Im nächsten Abschnitt sehen Sie, wie Sie die Population in ACS freigeben können.

## Zielgruppe in Campaign Standard freigeben {#share-the-target-with-campaign-standard}

Sobald die Zielpopulation definiert ist, können Sie sie in ACS mit der Aktivität **[!UICONTROL Listen-Update]** freigeben.

1. Fügen Sie im zuvor erstellten Workflow die Aktivität **[!UICONTROL Listen-Update]** hinzu und spezifizieren Sie die Liste, die Sie aktualisieren oder erstellen möchten.

   Geben Sie den Ordner an, in dem Sie die Liste in Campaign v7 speichern möchten. Listen unterliegen dem während der Implementierung definierten Ordner-Mapping, das sich auf ihre Sichtbarkeit auswirken kann, sobald sie in Campaign Standard freigegeben wurden. Siehe Abschnitt [Konvertierung der Berechtigungen](../../integrations/using/acs-connector-principles-and-data-cycle.md#rights-conversion).

1. Vergewissern Sie sich, dass die Option **[!UICONTROL In ACS freigeben]** mit einem Häkchen versehen ist. Standardmäßig ist diese Option aktiviert.

   ![](assets/acs_connect_listupdate1.png)

1. Speichern und starten Sie den Workflow.

   Die Zielgruppe und ihre zusätzlichen Daten werden in einer Liste in Campaign v7 gespeichert und sofort als eine Audience vom Typ Liste in Campaign Standard freigegeben. Nur die replizierten Profile werden in ACS freigegeben.

Wenn ein Fehler auf der **[!UICONTROL Listen-Update]** -Aktivität, bedeutet dies, dass die Synchronisierung mit Campaign Standard möglicherweise fehlgeschlagen ist. Um weitere Informationen zu den Fehlern zu erhalten, gehen Sie zu **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Prozess]** > **[!UICONTROL Diagnose]**. Dieser Ordner enthält Synchronisations-Workflows, die von der **[!UICONTROL Listen-Update]** Aktivitätsausführung. Weitere Informationen finden Sie im Abschnitt [Fehlerbehebung bei ACS Connector](../../integrations/using/troubleshooting-the-acs-connector.md).

## Daten in Campaign Standard abrufen und in einem Versand verwenden {#retrieve-the-data-in-campaign-standard-and-use-it-in-a-delivery}

Sobald der Zielgruppen-Workflow in Campaign v7 ausgeführt wird, finden Sie die Audience vom Typ Liste im schreibgeschützten Format im **[!UICONTROL Audiences]**-Menü in Campaign Standard.

![](assets/acs_connect_deliveryworkflow_audience.png)

Durch die Erstellung eines Versand-Workflows in Campaign Standard können Sie dann diese Audience sowie die darin enthaltenen zusätzlichen Daten in einem Versand verwenden.

1. Erstellen Sie einen neuen Workflow im Menü **[!UICONTROL Marketing-Aktivitäten]**.
1. Fügen Sie die Aktivität **[!UICONTROL Zielgruppe lesen]** hinzu und wählen Sie die zuvor von Campaign v7 übertragene Audience aus.

   Mit dieser Aktivität werden die Daten der ausgewählten Audience abgerufen. Sie können auch eine **[!UICONTROL Quellfilterung]** bei Bedarf mithilfe des entsprechenden Tabs dieser Aktivität.

1. Fügen Sie die Aktivität **[!UICONTROL E-Mail-Versand]** hinzu und konfigurieren Sie sie wie eine übliche [E-Mail-Versand-Aktivität](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html?lang=de).
1. Öffnen Sie den Versandinhalt.
1. Personalisierungsfeld hinzufügen; Suchen Sie im Popup die **[!UICONTROL Zusätzliche Daten (targetData)]** Knoten. Dieser Knoten enthält die Zusatzdaten der Audience, die im anfänglichen Zielgruppen-Workflow berechnet wurden. Sie können sie wie jedes andere Personalisierungsfeld verwenden.

   In unserem Beispiel beinhalten die zusätzlichen, vom ursprünglichen Zielgruppen-Workflow stammenden Daten die Anzahl der Sendungen an jeden Empfänger in den letzten 365 Tagen. Das im Zielgruppen-Workflow spezifizierte NBdeliveries-Alias ist hier sichtbar.

   ![](assets/acs_connect_deliveryworkflow_targetdata.png)

1. Speichern Sie den Versand und den Workflow.

   Der Workflow kann jetzt ausgeführt werden. Der Versand wird analysiert und kann durchgeführt werden.

   ![](assets/acs_connect_deliveryworkflow_ready.png)

## Versand durchführen und überwachen {#send-and-monitor-your-delivery}

Sobald der Versand und sein Inhalt vorbereitet sind, führen Sie den Versand aus:

1. Führen Sie den Versand-Workflow aus. In diesem Schritt werden die E-Mails für den Versand vorbereitet.
1. Bestätigen Sie manuell im Versand-Dashboard, dass der Versand durchgeführt werden kann.
1. Überwachen Sie die Berichte und Logs des Versandes:

   * **In Campaign Standard**: die üblichen [Berichte](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/about-reporting/about-dynamic-reports.html?lang=de) und [Logs](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html?lang=de) in Verbindung mit dem Versand
   * **in Campaign v7 und Campaign Standard**: Versandkennungen, E-Mail-Broadlogs und E-Mail-Trackinglogs werden mit Campaign v7 synchronisiert. Dies ermöglicht einen umfassenden Überblick Ihrer Marketing-Kampagnen in Campaign v7.

     Quarantänen werden automatisch nach Campaign v7 zurücksynchronisiert. Dadurch können Unzustellbarkeitsinformationen bei der nächsten Zielgruppenbestimmung in Campaign v7 berücksichtigt werden.

     Mehr Informationen zur Quarantäneverwaltung in Campaign Standard finden Sie in [diesem Abschnitt](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html?lang=de).

---
product: campaign
title: Synchronisieren von Zielgruppen
description: Erfahren Sie, wie Sie Zielgruppen mit dem ACS-Connector synchronisieren
feature: ACS Connector
hide: true
exl-id: 88e581cf-43cd-4c43-9347-d016c62fdf42
TQID: https://experienceleague.adobe.com/9gc7VAt25SZk-QEFwAKpmRJCtRQu1HpMXQYzaRZAJ2I
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: a658c786-869b-4194-a780-2594d663adda
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: bea9e610-36b4-4df2-94bb-0fb6fe46cb50
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
  - id: d1110311-2ca4-442b-be37-088a6db845ee
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 1236
ht-degree: 70%

---

# Synchronisieren von Zielgruppen{#synchronizing-audiences}



Mithilfe der erweiterten Funktionen von Campaign v7 können Sie eine umfangreiche Liste erstellen und als Audience direkt und in Echtzeit (einschließlich zusätzlicher Daten) nahtlos mit Campaign Standard teilen. Ihre Campaign Standard-Benutzenden können dann die Zielgruppe in Adobe Campaign Standard verwenden.

Eine komplexe Zielgruppenbestimmung einschließlich zusätzlicher Daten, die nicht in Campaign Standard repliziert werden, kann nur mithilfe von Campaign v7 durchgeführt werden.

Sie können auch über einen Connector wie beispielsweise Microsoft Dynamics bereitgestellte Empfänger- oder Datenlisten einfach in Campaign Standard freigeben.

Dieser Anwendungsfall zeigt, wie Sie in Campaign v7 einen Zieldatensatz für den Versand vorbereiten und gemeinsam mit zusätzlichen Daten in einem in Adobe Campaign Standard erstellten und durchgeführten Versand verwenden können.

>[!NOTE]
>
>Zusätzlich können Sie Daten mit Aggregaten und Sammlungen in Adobe Campaign Standard anreichern, wenn alle erforderlichen Daten bereits repliziert wurden.

## Voraussetzungen {#prerequisites}

Dazu ist Folgendes erforderlich:

* Empfänger, die in der Campaign v7-Datenbank gespeichert und mit Campaign Standard synchronisiert werden. Siehe Abschnitt [Profile synchronisieren](../../integrations/using/synchronizing-profiles.md).
* Zusätzliche Daten wie Abonnements oder Transaktionen, die in nms-bezogenen Tabellen in :recipients Campaign v7-Datenbank gespeichert sind. Diese Daten können aus nativen Schemata oder benutzerdefinierten Tabellen in Campaign v7 stammen. Sie sind standardmäßig nicht in Campaign Standard verfügbar, da sie nicht synchronisiert werden.
* Die Berechtigung zur Durchführung von Workflows in sowohl Campaign v7 als auch Campaign Standard.
* Die Berechtigung zur Erstellung und Durchführung eines Versands in Campaign Standard.

## Zielgruppenbestimmungs-Workflow mit zusätzlichen Daten in Campaign v7 erstellen {#create-a-targeting-workflow-with-additional-data-in-campaign-v7}

Eine komplexe Zielgruppenbestimmung einschließlich zusätzlicher Daten, die nicht in Campaign Standard repliziert werden, kann nur mithilfe von Campaign v7 durchgeführt werden.

Nachdem die Zielgruppe und ihre zusätzlichen Daten definiert wurden, können sie als Liste gespeichert und in Campaign Standard freigegeben werden.

>[!NOTE]
>
>Dies ist ein Beispiel. Je nach Ihren Anforderungen können Sie einfach eine Empfängerliste abfragen und sie ohne weitere Verarbeitung für ACS freigeben. Sie können Ihre endgültige Zielgruppe auch mit anderen Daten-Management-Aktivitäten vorbereiten.

Gehen Sie folgendermaßen vor, um die endgültige Zielgruppe und ihre zusätzlichen Daten zu erhalten:

1. Erstellen Sie einen neuen Workflow in **[!UICONTROL Profile und Zielgruppen]** > **[!UICONTROL Aufträge]** > **[!UICONTROL Zielgruppen-Workflow]**.
1. Fügen Sie eine Aktivität **[!UICONTROL Abfrage]** hinzu und wählen Sie die Empfänger aus, an die Sie die endgültige E-Mail senden möchten. Zum Beispiel alle Empfänger zwischen 18 und 30 Jahren, die in Frankreich leben.

   ![](assets/acs_connect_query1.png)

1. Fügen Sie in der Abfrageoption zusätzliche Daten hinzu. Weiterführende Informationen hierzu finden Sie im Abschnitt [Daten hinzufügen](../../workflow/using/query.md#adding-data).

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

1. Definieren Sie die Ausgabespalten. Hier ist die einzige erforderliche Spalte die Spalte, die die Anzahl der Sendungen zählt. Gehen Sie dazu folgendermaßen vor:

   * Wählen Sie rechts im Fenster **[!UICONTROL Hinzufügen]**.
   * Wählen Sie im Fenster **[!UICONTROL Feldauswahl]** die Schaltfläche **[!UICONTROL Erweiterte Auswahl]** aus.
   * Wählen Sie **[!UICONTROL Aggregat]** und danach **[!UICONTROL Zählung]** aus. Markieren Sie die Option **[!UICONTROL Unterschiedlich]** und wählen Sie **[!UICONTROL Weiter]** aus.
   * Wählen Sie in der Felderliste das für die Funktion **Zählung** verwendete Feld aus. Wählen Sie ein Feld aus, das immer ausgefüllt wird, z. B. **[!UICONTROL Primärschlüssel]**, und klicken Sie auf **[!UICONTROL Beenden]**.
   * Ändern Sie den Ausdruck in der Spalte **[!UICONTROL Alias]**. Dieser Alias ermöglicht Ihnen, die hinzugefügte Spalte im endgültigen Versand einfach abzurufen. **NBdeliveries**, um die hinzugefügte Spalte im endgültigen Versand einfach abrufen zu können.
   * Wählen Sie **[!UICONTROL Beenden]** aus und speichern Sie die Konfiguration der Aktivität **[!UICONTROL Abfrage]**.

   ![](assets/acs_connect_query7.png)

1. Speichern Sie den Workflow. Im nächsten Abschnitt erfahren Sie, wie Sie die Population für ACS freigeben.

## Zielgruppe in Campaign Standard freigeben {#share-the-target-with-campaign-standard}

Sobald die Zielpopulation definiert ist, können Sie sie in ACS mit der Aktivität **[!UICONTROL Listen-Update]** freigeben.

1. Fügen Sie im zuvor erstellten Workflow die Aktivität **[!UICONTROL Listen-Update]** hinzu und spezifizieren Sie die Liste, die Sie aktualisieren oder erstellen möchten.

   Geben Sie den Ordner an, in dem Sie die Liste in Campaign v7 speichern möchten. Listen unterliegen dem während der Implementierung definierten Ordner-Mapping, das sich auf ihre Sichtbarkeit auswirken kann, sobald sie in Campaign Standard freigegeben wurden. Siehe Abschnitt [Konvertierung der Berechtigungen](../../integrations/using/acs-connector-principles-and-data-cycle.md#rights-conversion).

1. Stellen Sie sicher **[!UICONTROL dass die Option „Mit ACS]**&quot; aktiviert ist. Sie ist standardmäßig aktiviert.

   ![](assets/acs_connect_listupdate1.png)

1. Speichern und starten Sie den Workflow.

   Die Zielgruppe und die zugehörigen zusätzlichen Daten werden in einer Liste in Campaign v7 gespeichert und sofort als Audience-Liste in Campaign Standard freigegeben. Nur die Profile, die repliziert wurden, werden für ACS freigegeben.

Wenn bei der Aktivität **[!UICONTROL Listen-Update]** ein Fehler auftritt, ist möglicherweise die Synchronisation mit Campaign Standard fehlgeschlagen. Um zu sehen, wo der Fehler liegt, gehen Sie zu **[!UICONTROL Administration]** > **[!UICONTROL ACS-Connector]** > **[!UICONTROL Prozesse]** > **[!UICONTROL Prüfung]**. Dieser Ordner enthält Synchronisations-Workflows, die von der Aktivität **[!UICONTROL Listen-Update]** ausgelöst wurden. Weitere Informationen finden Sie im Abschnitt [Fehlerbehebung beim ACS-Connector](../../integrations/using/troubleshooting-the-acs-connector.md).

## Daten in Campaign Standard abrufen und in einem Versand verwenden {#retrieve-the-data-in-campaign-standard-and-use-it-in-a-delivery}

Sobald der Zielgruppen-Workflow in Campaign v7 ausgeführt wird, finden Sie die Audience vom Typ Liste im schreibgeschützten Format im **[!UICONTROL Audiences]**-Menü in Campaign Standard.

![](assets/acs_connect_deliveryworkflow_audience.png)

Durch die Erstellung eines Versand-Workflows in Campaign Standard können Sie dann diese Zielgruppe sowie die darin enthaltenen zusätzlichen Daten in einem Versand verwenden.

1. Erstellen Sie einen neuen Workflow im Menü **[!UICONTROL Marketing-Aktivitäten]**.
1. Fügen Sie die Aktivität **[!UICONTROL Zielgruppe lesen]** hinzu und wählen Sie die zuvor von Campaign v7 übertragene Audience aus.

   Mit dieser Aktivität können Daten aus der ausgewählten Audience abgerufen werden. Sie können bei Bedarf auch eine zusätzliche **[!UICONTROL Filterung der Quelle]** anwenden, indem Sie den entsprechenden Tab dieser Aktivität auswählen.

1. Fügen Sie die Aktivität **[!UICONTROL E-Mail-Versand]** hinzu und konfigurieren Sie sie wie eine übliche [E-Mail-Versand-Aktivität](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html?lang=de).
1. Öffnen Sie den Versandinhalt.
1. Personalisierungsfeld hinzufügen; Suchen Sie im Popup den Knoten **[!UICONTROL Zusätzliche Daten (targetData)]**. Dieser Knoten enthält die zusätzlichen Audience-Daten, die im anfänglichen Zielgruppen-Workflow erstellt wurden. Sie können sie wie jedes andere Personalisierungsfeld verwenden.

   In diesem Beispiel entsprechen die zusätzlichen Daten aus dem ursprünglichen Zielgruppen-Workflow der Anzahl der Sendungen, die in den letzten 365 Tagen an jeden einzelnen Empfänger gesendet wurden. Der im Zielgruppenbestimmungs-Workflow angegebene NB-Versandalias ist hier sichtbar.

   ![](assets/acs_connect_deliveryworkflow_targetdata.png)

1. Speichern Sie den Versand und den Workflow.

   Der Workflow kann jetzt ausgeführt werden. Der Versand wird analysiert und kann versendet werden.

   ![](assets/acs_connect_deliveryworkflow_ready.png)

## Versand durchführen und überwachen {#send-and-monitor-your-delivery}

Sobald der Versand und sein Inhalt vorbereitet sind, führen Sie den Versand aus:

1. Führt den Versand-Workflow aus Dieser Schritt bereitet die E-Mail für den Versand vor.
1. Bestätigen Sie manuell im Versand-Dashboard, dass der Versand durchgeführt werden kann.
1. Überwachen Sie die Berichte und Logs des Versandes:

   * **In Campaign Standard**: die üblichen [Berichte](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/about-reporting/about-dynamic-reports.html?lang=de) und [Logs](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html?lang=de) in Verbindung mit dem Versand
   * **in Campaign v7 und Campaign Standard**: Versand-IDs, E-Mail-Broadlogs und E-Mail-Trackinglogs werden mit Campaign v7 synchronisiert. Von Campaign v7 aus erhalten Sie dann eine 360-Grad-Ansicht Ihrer Marketing-Kampagnen.

     Quarantänen werden automatisch wieder mit Campaign v7 synchronisiert. Auf diese Weise können nicht zustellbare Informationen für die nächste Zielgruppenbestimmung in Campaign v7 berücksichtigt werden.

     Mehr Informationen zur Quarantäneverwaltung in Campaign Standard finden Sie in [diesem Abschnitt](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html?lang=de).

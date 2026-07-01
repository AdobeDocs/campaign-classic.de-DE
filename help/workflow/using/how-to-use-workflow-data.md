---
product: campaign
title: Workflow-Daten verwenden
description: Erfahren Sie, wie Sie die Workflow-Daten verwenden.
feature: Workflows, Data Management
hide: true
exl-id: 5354d608-2fea-45f9-a0aa-11c7e965ab04
TQID: https://experienceleague.adobe.com/xasYSu6WyHC0T6CpKn51bZ5K7WlspJAbB0R45AeXb8M
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 417
ht-degree: 100%

---

# Workflow-Daten verwenden{#how-to-use-workflow-data}



## Datenbank aktualisieren {#updating-the-database}

Alle erfassten Daten können zur Aktualisierung der Datenbank oder in Sendungen verwendet werden. Sie können beispielsweise die Möglichkeiten der Personalisierung von Nachrichteninhalten anreichern (einschließlich der Anzahl der Verträge in der Nachricht, Angabe des durchschnittlichen Warenkorbs im letzten Jahr usw.) oder die Zielgruppenbestimmung detaillierter darstellen (eine Nachricht an die Mitversicherten senden, die 1.000 besten Abonnentinnen und Abonnenten von Online-Diensten ansprechen usw.). Diese Daten können auch exportiert oder in einer Liste archiviert werden.

### Listen und direkte Aktualisierungen {#lists-and-direct-updates}

Zur Aktualisierung der Adobe Campaign-Datenbank und von Listen stehen zwei dedizierte Aktivitäten zur Verfügung:

* Über die Aktivität **[!UICONTROL Listen-Update]** können Arbeitstabellen in einer Datenliste gespeichert werden.

  Sie können eine vorhandene Liste auswählen oder eine Liste erstellen. In diesem Fall werden ihr Name und gegebenenfalls ihr Eintragsordner berechnet.

  ![](assets/s_user_create_list.png)

  Siehe [Listen-Update](list-update.md).

* Die **[!UICONTROL Daten-Update]**-Aktivität ermöglicht eine gebündelte Aktualisierung von Datenbankfeldern.

  Weitere Informationen hierzu finden Sie im Abschnitt [Daten-Update](update-data.md).

### An- und Abmeldungen verwalten {#subscription-unsubscription-management}

Die An- und Abmeldung von Empfängern für einen Informationsdienst im Rahmen eines Workflows wird im Abschnitt [An-/Abmeldedienst](subscription-services.md) beschrieben.

## Über einen Workflow versenden {#sending-via-a-workflow}

### Versandaktivität {#delivery-activity}

Die Versandaktivität wird im Abschnitt [Versand](delivery.md) beschrieben.

### Sendungen anreichern und personalisieren {#enriching-and-targeting-deliveries}

Im Rahmen von Sendungen bieten Workflow-Aktivitäten die Möglichkeit, Daten zur Personalisierung des Inhalts oder zur Konfiguration der Versandzielpopulationen bereitzustellen.

Beispielsweise können Sie bei Briefpost-Sendungen Zusatzdaten in die Extraktionsdatei aufnehmen, die mithilfe einer Workflow-Aktivität abgerufen werden:

![](assets/s_advuser_add_data_postal_mail.png)

Ergänzend zu den üblichen Personalisierungsfeldern können Sie den Versandinhalt mit aus einem Workflow stammenden Daten personalisieren. Tatsächlich können die aus Workflow-Aktivitäten gewonnenen Zusatzdaten gespeichert und im Versandassistenten verfügbar gemacht werden. Unten stehendes Beispiel verdeutlicht dies anhand des Namens der Ausgabedatei eines Briefpost-Versands:

![](assets/s_advuser_using_additional_data.png)

Aus Workflow-Arbeitstabellen stammende Daten sind über ihren Namen leicht identifizierbar. Er beginnt jeweils mit **targetData**. Weitere Informationen hierzu finden Sie im Abschnitt [Zielgruppendaten](data-life-cycle.md#target-data).

Auch im Rahmen eines E-Mail-Versands können Personalisierungsfelder auf Daten zugreifen, die im Zuge einer Erweiterung des Zieldatensatzes in einem Zielgruppen-Workflow erhoben wurden, wie die folgende Abbildung verdeutlicht:

![](assets/s_advuser_add_data_email.png)

Wenn ein Segment-Code in einer Zielgruppenbestimmungsaktivität angegeben wird, wird er einer bestimmten Spalte der Workflow-Tabelle hinzugefügt und zusammen mit den Personalisierungsfeldern angeboten. Klicken Sie zur Anzeige aller Personalisierungsfelder auf die entsprechende Schaltfläche im Versand und wählen Sie die Option **[!UICONTROL Erweiterung des Zieldatensatzes > Sonstige...]** aus.

![](assets/s_advuser_segment_code_select.png)

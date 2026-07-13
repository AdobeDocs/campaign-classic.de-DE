---
product: campaign
title: Verwenden von Aggregaten
description: Machen Sie sich mit der Verwendung von Aggregaten vertraut
feature: Workflows
hide: true
exl-id: 12b173e9-5068-4d45-9e1e-2aecc9866e9c
TQID: https://experienceleague.adobe.com/gGjUc-62oHW0OBV-iPKYGoDWiTebnQ3g7v4cInh3TLw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: c35995a47788db080636c66827a4bd6dc98806cf
workflow-type: ht
source-wordcount: 673
ht-degree: 100%

---

# Verwenden von Aggregaten{#using-aggregates}



Ziel des folgenden Anwendungsbeispiels ist es, die zuletzt zur Datenbank hinzugefügten Empfänger zu identifizieren.

Unter Verwendung des folgenden Prozesses wird das Erstellungsdatum von Empfangenden in der Datenbank mithilfe eines Aggregats mit dem letzten bekannten Datum verglichen, an dem eine Empfängerin bzw. ein Empfänger erstellt wurde. Alle am selben Tag erstellten Empfangenden werden ebenfalls ausgewählt.

Die Konfiguration eines Empfängerfilters vom Typ **Erstellungsdatum = max (Erstellungsdatum)** ist mithilfe des folgenden Workflows möglich:

1. Abrufen von Datenbankempfängern mithilfe einer einfachen Abfrage. Weitere Informationen zu diesem Schritt finden Sie unter [Abfragen erstellen](query.md#creating-a-query).
1. Berechnung des letzten bekannten Empfängererstellungs-Datums mit der Aggregatfunktion **max (Erstellungsdatum)**.
1. Zuordnung der Empfänger zum Ergebnis des Aggregats im selben Schema.
1. Filterung der Empfänger mithilfe des Aggregats im bearbeiteten Schema.

![](assets/datamanagement_usecase_1.png)

## &#x200B;1. Schritt: Berechnung des Aggregats {#step-1--calculating-the-aggregate-result}

1. Erstellen Sie eine Abfrage. Hier ist das Ziel die Berechnung des letzten bekannten Erstellungsdatums aller Empfangenden in der Datenbank. Die Abfrage enthält daher keinen Filter.
1. Klicken Sie auf den Link **[!UICONTROL Daten hinzufügen...]**.
1. Wählen Sie in den aufeinanderfolgenden Fenstern die Optionen **[!UICONTROL Daten in Relation mit der Filterdimension]** und **[!UICONTROL Daten der Filterdimension]**.
1. Definieren Sie im Fenster **[!UICONTROL Hinzuzufügende Daten]** eine neue Spalte zur Berechnung des maximalen Werts im Feld **Erstellungsdatum** der Empfängertabelle. Verwenden Sie hierzu den Ausdruckseditor oder geben Sie direkt **max(@created)** in der **[!UICONTROL Ausdruck]**-Spalte ein. Klicken Sie dann auf **[!UICONTROL Beenden]**.

   ![](assets/datamanagement_usecase_2.png)

1. Klicken Sie auf **[!UICONTROL Zusätzliche Daten bearbeiten]** und dann auf **[!UICONTROL Erweiterte Parameter…]**. Aktivieren Sie die Option **[!UICONTROL Automatisches Hinzufügen der Primärschlüssel der Zielgruppendimension deaktivieren]**.

   Diese Option stellt sicher, dass nicht alle Empfangenden als Ergebnis angezeigt werden und dass explizit hinzugefügte Daten nicht beibehalten werden. Dies bezieht sich hier auf das letzte Datum, an dem eine Empfängerin bzw. ein Empfänger erstellt wurde.

   Lassen Sie die Option **[!UICONTROL Duplikate löschen (DISTINCT)]** angekreuzt.

## &#x200B;2. Schritt: Verknüpfung von Empfängern und Aggregat {#step-2--linking-the-recipients-and-the-aggregation-function-result}

Verwenden Sie die Schema-Bearbeitung, um die auf Empfänger bezogene Abfrage mit der zur Berechnung eines Aggregats dienenden Abfrage zu verknüpfen.

1. Wählen Sie als Hauptmenge die Abfrage bezüglich der Empfänger aus.
1. Fügen Sie im **[!UICONTROL Relationen]**-Tab eine neue Relation hinzu und konfigurieren Sie sie wie folgt:

   * Wählen Sie das temporäre Schema des Aggregats aus. Die Daten dieses Schemas werden zu den Mitgliedern der Hauptmenge hinzugefügt.
   * Aktivieren Sie die Option **[!UICONTROL Einfachen Join verwenden]**, um das Ergebnis des Aggregats zu jedem Empfänger der Hauptmenge zuzuordnen.
   * Geben Sie schließlich an, dass es sich bei der Relation um eine **[!UICONTROL 1:1-Relation]** handelt.

   ![](assets/datamanagement_usecase_3.png)

Auf diese Weise wird das Ergebnis des Aggregats mit jedem einzelnen der Empfänger verknüpft.

## &#x200B;3. Schritt: Filterung der Empfänger mithilfe des Aggregats {#step-3--filtering-recipients-using-the-aggregate-}

Sobald die Relation hergestellt wurde, bilden das Aggregatergebnis und die Empfangenden einen Teil desselben temporären Schemas. Dadurch ist es möglich, einen Filter zum Vergleichen des Erstellungsdatums der Empfangenden und des letzten bekannten Erstellungsdatums (dargestellt durch die Aggregatsfunktion) auf das Schema anzuwenden. Dieser Filter wird mithilfe einer Aufspaltungsaktivität angewendet.

1. Wählen Sie im **[!UICONTROL Allgemein]**-Tab **Empfänger** als Zielgruppendimension und **Schema-Bearbeitung** als Filterdimension aus (um das Schema der eingehenden Transition zu filtern).
1. Gehen Sie in den **[!UICONTROL Teilmengen]**-Tab, kreuzen Sie die Option **[!UICONTROL Filterbedingung für die Eingangspopulation hinzufügen]** an und klicken Sie auf **[!UICONTROL Bearbeiten...]**.
1. Setzen Sie im Ausdruckseditor das Erstellungsdatum der Empfänger mit dem vom Aggregat berechneten Datum gleich.

   Die Datumsfelder in der Datenbank werden in der Regel auf die Millisekunde genau gespeichert. Die Datumsangaben müssen daher auf den ganzen Tag ausgedehnt werden, um nicht nur die Empfangenden abzurufen, die in derselben Millisekunde erstellt wurden.

   Im Ausdruckseditor steht hierzu die Funktion **ToDate** zur Verfügung, die Datumsangaben mit Uhrzeit in einfache Daten konvertiert.

   Folgende Ausdrücke sind also für die Bedingung erforderlich:

   * **[!UICONTROL Ausdruck]**: `toDate([target/@created])`.
   * **[!UICONTROL Wert`toDate([datemax/expr####])`]**, wobei expr#### dem in der Aggregatabfrage definierten Aggregat entspricht.

   ![](assets/datamanagement_usecase_4.png)

Das Ergebnis der Aufspaltung entspricht somit den am selben Tag wie die letzte bekannte Erstellung erstellten Empfängern.

Sie haben die Möglichkeit, im Anschluss weitere Aktivitäten wie beispielsweise ein Listen-Update oder einen Versand im Workflow-Diagramm zu platzieren.


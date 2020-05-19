---
title: 'Daten anreichern '
seo-title: 'Daten anreichern '
description: 'Daten anreichern '
seo-description: null
page-status-flag: never-activated
uuid: 3f65a8a2-b3e1-4c4c-9653-b8a7c4d7557a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: f87da08f-68b9-4e2b-821f-b3ff20e390f1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1aca6758bc787f91ae28d7d5add875edf04541e8
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 97%

---


# Daten anreichern{#enriching-data}

## Über die Anreicherung von Daten {#about-enriching-data}

In diesem Anwendungsbeispiel werden mögliche Verwendungen der Aktivität **[!UICONTROL Anreicherung]** in einem Zielgruppen-Workflow beschrieben. Weitere Informationen zur Verwendung der Aktivität **[!UICONTROL Anreicherung]** finden Sie unter [Anreicherung](../../workflow/using/enrichment.md).

In [diesem Abschnitt](../../workflow/using/email-enrichment-with-custom-date-fields.md)finden Sie außerdem ein Anwendungsbeispiel zur Aufwertung eines E-Mail-Versands mit benutzerdefinierten Datumsangaben.

Den in der Marketing-Datenbank enthaltenen Kontakten soll über eine Webapp ein Preisausschreiben angeboten werden. Die Ergebnisse des Wettbewerbs werden in der Tabelle **[!UICONTROL Wettbewerbsergebnisse]** gespeichert. Diese Tabelle steht in Relation mit der Tabelle der Kontakte (**[!UICONTROL Empfänger]**). Die Tabelle **[!UICONTROL Wettbewerbsergebnisse]** enthält folgende Spalten:

* Wettbewerbsname (@game),
* Versuchnummer (@trial),
* Score (@score).

![](assets/uc1_enrich_1.png)

Ein in der **[!UICONTROL Empfängertabelle]** enthaltener Kontakt kann mehrere Einträge in der Tabelle der **[!UICONTROL Wettbewerbsergebnisse]** aufweisen. Die Relation zwischen beiden Tabellen ist somit vom Typ 1:n. Nachfolgend werden für einen Empfänger beispielhaft die Ergebnislogs dargestellt:

![](assets/uc1_enrich_2.png)

Ziel des vorliegenden Beispiels ist es, den Teilnehmern des letzten Wettbewerbs eine je nach erreichtem Score personalisierte Mitteilung zukommen zu lassen. Der Teilnehmer mit dem höchsten Score erhält den ersten Preis, der Teilnehmer mit dem zweithöchsten Score einen Trostpreis und alle anderen Teilnehmer werden aufgefordert, ihr Glück beim nächsten Wettbewerb erneut zu versuchen.

Der Workflow für dieses Anwendungsbeispiel stellt sich wie folgt dar:

![](assets/uc1_enrich_3.png)

Die Workflow-Erstellung gliedert sich in folgende Schritte:

1. Platzierung von zwei **[!UICONTROL Abfragen]** und einer **[!UICONTROL Schnittmenge]** zum Abruf aller neuen Abonnenten, die am letzten Wettbewerb teilgenommen haben.
1. Im Anschluss daran folgt eine **[!UICONTROL Anreicherung]**, die es ermöglicht, die Daten aus der Tabelle **[!UICONTROL Wettbewerbsergebnisse]** zu verwenden. Das für die Personalisierung benötigte Feld **[!UICONTROL Score]** wird daher zur Workflow-Arbeitstabelle hinzugefügt.
1. Mithilfe der **[!UICONTROL Aufspaltung]** werden nun je nach erreichtem Score Teilmengen erstellt.
1. An jede Teilmenge wird ein **[!UICONTROL Versand]** angeschlossen.

## 1. Schritt: Zielgruppenbestimmung {#step-1--targeting}

In der ersten Abfrage werden die Kontakte abgerufen, die innerhalb der letzten sechs Monate in die Datenbank aufgenommen wurden.

![](assets/uc1_enrich_4.png)

In der zweiten Abfrage werden die Kontakte abgerufen, die am letzten Wettbewerb teilgenommen haben.

![](assets/uc1_enrich_5.png)

Die **[!UICONTROL Schnittmenge]** ermittelt dann die Population, die beiden Bedingungen entspricht.

## 2. Schritt: Anreicherung {#step-2--enrichment}

Im vorliegenden Beispiel sollen die Sendungen basierend auf dem in der Tabelle **[!UICONTROL Wettbewerbsergebnisse]** enthaltenen Feld **[!UICONTROL Score]** personalisiert werden. Diese Tabelle weist eine 1:n-Relation mit der Empfängertabelle auf. Die **[!UICONTROL Anreicherungsaktivität]** ermöglicht es, Daten aus einer mit der Filterdimension in Relation stehenden Tabelle zur Arbeitstabelle des Workflows hinzuzufügen.

1. Klicken Sie auf den Link **[!UICONTROL Daten hinzufügen...]** im Bearbeitungsbildschirm der Anreicherung und aktivieren Sie die Option **[!UICONTROL Daten in Relation mit der Filterdimension]**. Klicken Sie dann auf **[!UICONTROL Weiter]**.

   ![](assets/uc1_enrich_6.png)

1. Aktivieren Sie im nächsten Bildschirm wiederum die Option **[!UICONTROL Daten in Relation mit der Filterdimension]**, markieren Sie die Tabelle **[!UICONTROL Wettbewerbsergebnisse]** und klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/uc1_enrich_7.png)

1. Geben Sie eine Kennung und einen Titel an und wählen Sie im Feld **[!UICONTROL Abgerufene Daten]** die Option **[!UICONTROL Zeilenanzahl begrenzen]** aus. Geben Sie dann im Feld **[!UICONTROL Abzurufende Zeilen]** den Wert &#39;1&#39; an. Für jeden Empfänger fügt die Anreicherungsaktivität somit genau eine Zeile aus der Tabelle **[!UICONTROL Wettbewerbsergebnisse]** in die Workflow-Arbeitstabelle ein. Klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/uc1_enrich_8.png)

1. Im vorliegenden Beispiel soll das beste Ergebnis der Empfänger aus dem letzten Wettbewerb abgerufen werden. Filtern Sie hierzu die Tabelle nach dem Feld **[!UICONTROL Wettbewerb]** und rufen Sie nur die Datensätze ab, die dem letzten Wettbewerb entsprechen. Klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/uc1_enrich_9.png)

1. Klicken Sie im Bildschirm **[!UICONTROL Sortierung]** auf die **[!UICONTROL Hinzufügen]**-Schaltfläche, wählen Sie das Feld **[!UICONTROL Score]** aus und kreuzen Sie das Feld **[!UICONTROL Absteigend]** an. Für jeden Empfänger fügt die Anreicherungsaktivität somit die Zeile aus der Ergebnistabelle ein, die dem höchsten Score entspricht. Klicken Sie auf **[!UICONTROL Weiter]****[!UICONTROL .]**

   ![](assets/uc1_enrich_10.png)

1. Doppelklicken Sie im Bildschirm **[!UICONTROL Hinzuzufügende Daten]** auf das Feld **[!UICONTROL Score]**. Auf diese Weise fügt die Anreicherungsaktivität nur das Feld **[!UICONTROL Score]** hinzu. Klicken Sie auf **[!UICONTROL Beenden]**.

   ![](assets/uc1_enrich_11.png)

Klicken Sie mit der rechten Maustaste auf die in die Anreicherungsaktivität eingehende Transition und wählen Sie die Option **[!UICONTROL Ergebnis anzeigen...]**. Die Arbeitstabelle enthält folgende Daten:

![](assets/uc1_enrich_13.png)

Das Schema der Arbeitstabelle stellt sich wie folgt dar:

![](assets/uc1_enrich_15.png)

Wiederholen Sie den Vorgang für die ausgehende Transition der Anreicherungsaktivität. Sie können sehen, dass die Score-Daten der Empfänger hinzugefügt wurden. Für jeden Empfänger wurde der höchste Score abgerufen.

![](assets/uc1_enrich_12.png)

Auch das Schema wurde entsprechend angereichert.

![](assets/uc1_enrich_14.png)

## 3. Schritt: Aufspaltung und Versand {#step-3--split-and-delivery}

Im Anschluss an die Anreicherung sorgt die **[!UICONTROL Aufspaltung]** für die Verteilung der Empfänger nach den erreichten Scores.

![](assets/uc1_enrich_18.png)

1. Die erste Teilmenge (**Gewinner**) enthält den Empfänger mit dem höchsten Score. Definieren Sie hierzu eine Begrenzung der Datensatzanzahl, sortieren Sie die Scores in absteigender Reihenfolge und begrenzen Sie die Datensatzanzahl auf 1.

   ![](assets/uc1_enrich_16.png)

1. Die zweite Teilmenge (**Trostpreis**) enthält den Empfänger mit dem zweithöchsten Score. Konfigurieren Sie die zweite Teilmenge analog zur ersten.

   ![](assets/uc1_enrich_17.png)

1. Die dritte Teilmenge (**Verlierer**) enthält die verbleibenden Empfänger. Kreuzen Sie im **[!UICONTROL Allgemein]**-Tab die Option **[!UICONTROL Komplement erzeugen]** an, um alle die Empfänger abzurufen, die weder den höchsten noch den zweithöchsten Score erzielt haben.

   ![](assets/uc1_enrich_19.png)

1. Schließen Sie an jede Teilmenge einen **[!UICONTROL Versand]** an. Verwenden Sie für jeden Versand eine andere Versandvorlage.

   ![](assets/uc1_enrich_20.png)


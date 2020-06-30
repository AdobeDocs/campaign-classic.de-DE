---
title: Listen-Update
seo-title: Listen-Update
description: Listen-Update
seo-description: null
page-status-flag: never-activated
uuid: 1446f115-3f64-4b95-8e04-6426ab1b8dab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: ca2cd5bf-78a2-4e43-955d-206f4474d1e0
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: b1a961822224ab0a9551f51942a5f94cf201c8ee
workflow-type: ht
source-wordcount: '522'
ht-degree: 100%

---


# Listen-Update{#list-update}

Das **Listen-Update** speichert die Ergebnisse der eingehenden Aktivitäten in einer Liste.

![](assets/s_user_segmentation_update_group.png)

Die Liste kann bereits existieren.

Sie kann jedoch auch mithilfe der Optionen **[!UICONTROL Wenn nötig Liste erstellen (Titel berechnet)]** oder **[!UICONTROL Wenn nötig Liste erstellen (Ordner und Titel berechnet)]** neu erstellt werden. Auf diese Weise können Sie den Titel der Liste und eventuell den Speicherordner angeben. Der Titel kann jedoch auch über dynamische Felder oder ein Script berechnet werden. Der Zugriff auf die dynamischen Felder erfolgt über das Kontextmenü der Schaltfläche rechts vom Titel.

![](assets/s_user_segmentation_update_list_calc.png)

Wenn die Liste bereits existiert, werden die neuen Datensätze hinzugefügt, es sei denn, Sie aktivieren die Option **[!UICONTROL Wenn sie existiert, Liste leeren und erneut verwenden (nicht vervollständigen)]**.

Kreuzen Sie die Option **[!UICONTROL Liste mit eigener Tabelle erstellen oder verwenden]** an, wenn die erstellte oder aktualisierte Liste nicht die Empfängertabelle verwenden soll.

In diesem Fall müssen die entsprechenden Tabellen zuvor in der Adobe-Campaign-Instanz konfiguriert werden.

Im Allgemeinen stellt die Speicherung einer Zielgruppe in einer Liste das Ende eines Workflows dar. Standardmäßig bietet die **[!UICONTROL Listen-Update]**-Aktivität daher keine ausgehende Transition. Dies kann durch Ankreuzen der Option **[!UICONTROL Ausgehende Transition erzeugen]** umgangen werden.

## Anwendungsbeispiel Listen-Update {#example--list-update}

Im vorliegenden Beispiel soll eine Liste mit allen Männern über 30 Jahre, die in Deutschland leben, erstellt werden. Bei der ersten Durchführung des Workflows wird die Liste erstellt, bei allen späteren Durchführungen wird sie aktualisiert. Die Liste kann beispielsweise im Rahmen von speziell abgestimmten Werbekampagnen Verwendung finden.

1. Schließen Sie an eine Abfrage ein **[!UICONTROL Listen-Update]** an und öffnen Sie die Aktivität.

   Weitere Informationen zum Erstellen von Abfragen in Workflows finden unter [Abfrage](../../workflow/using/query.md).

1. Benennen Sie die Aktivität.
1. Kreuzen Sie die Option **[!UICONTROL Wenn nötig Liste erstellen (Titel berechnet)]** an, damit die Liste bei der ersten Durchführung erstellt und später jeweils aktualisiert wird.
1. Wählen Sie den Ordner aus, in dem die Liste gespeichert werden soll.
1. Geben Sie den Titel der Liste an. Fügen Sie gegebenenfalls dynamische Felder ein, um den Listentitel automatisch zu berechnen. Im vorliegenden Beispiel hat die Liste den gleichen Namen wie die Abfrage, um den Inhalt leichter identifizieren zu können.
1. Lassen Sie die Option **[!UICONTROL Wenn sie existiert, Liste leeren und erneut verwenden (nicht vervollständigen)]** aktiv, damit die Empfänger, die nicht mehr den Filterkriterien entsprechen, gelöscht und die neuen Empfänger eingfügt werden.
1. Lassen Sie die Option **[!UICONTROL Liste mit eigener Tabelle erstellen oder verwenden]** ebenfalls aktiv.
1. Lassen Sie die Option **[!UICONTROL Ausgehende Transition erzeugen]** deaktiviert.
1. Klicken Sie auf **[!UICONTROL OK]** und starten Sie den Workflow.

   ![](assets/s_user_segmentation_update_list_calc_example.png)

   Die Empfängerliste wird erstellt und bei erneuter Ausführung des Workflows aktualisiert.

Mehr dazu erfahren Sie im Video [Creating a list of recipients](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html).

## Eingabeparameter {#input-parameters}

* tableName
* schema

Identifiziert die in der Gruppe zu speichernde Population.

## Ausgabeparameter {#output-parameters}

* groupId: Kennung der Gruppe.

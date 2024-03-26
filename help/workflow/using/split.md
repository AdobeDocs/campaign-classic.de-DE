---
product: campaign
title: Aufspaltung
description: Erfahren Sie mehr über die Workflow-Aktivität "Aufspaltung".
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
feature: Workflows, Targeting Activity
exl-id: 4204350a-c2d2-4033-9bdf-87b49d8211b9
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '2151'
ht-degree: 80%

---

# Aufspaltung{#split}



Über die **Aufspaltung** lässt sich eine Population in verschiedene Teilmengen splitten. Die Zielgruppe wird aus allen eingehenden Ergebnissen erstellt, dies bedeutet, dass die vorgeschalteten Aktivitäten beendet sein müssen, bevor die Aufspaltung ausgeführt werden kann.

Diese Aktivität Trigger keine Vereinigung der eingehenden Populationen. Wenn mehrere Transitionen in einer Aufspaltungsaktivität landen, wird empfohlen, eine **[!UICONTROL Vereinigung]** -Aktivität vor.

Ein Beispiel der verwendeten Aufspaltungs-Aktivität finden Sie unter [Teilmengen mithilfe der Aufspaltungs-Aktivität erstellen](targeting-data.md#creating-subsets-using-the-split-activity).

Ein Beispiel für die Verwendung der Aufspaltungs-Aktivität zur Segmentierung der Zielgruppe in unterschiedliche Populationen mithilfe von Filterbedingungen finden Sie in [diesem Abschnitt](cross-channel-delivery-workflow.md).

Ein Beispiel für die Verwendung einer Instanzvariablen in einer Aufspaltungs-Aktivität finden Sie in [diesem Abschnitt](javascript-scripts-and-templates.md).

Konfigurieren Sie die Aktivität, indem Sie im Tab **[!UICONTROL Teilmengen]** jeweils einen Titel und die Auswahlkriterien der Teilmengen angeben. Geben Sie im Tab **[!UICONTROL Allgemein]** die Zielgruppendimension an.

## Teilmengen erstellen {#creating-subsets}

Gehen Sie wie folgt vor:

1. Bennennen Sie die Teilmenge und geben Sie den Auswahlmodus an.
1. Wenn die eingehende Population gefiltert werden soll, ist die Option **[!UICONTROL Filterbedingung für die Eingangspopulation hinzufügen]** zu verwenden. Klicken Sie dann auf den Link **[!UICONTROL Bearbeiten...]**.

   Wählen Sie nun den Filtertyp aus.

   Die Vorgehensweise ist mit der der Abfrageaktivität identisch.****

   >[!NOTE]
   >
   >Es können maximal Daten aus zwei externen Datenbanken gefiltert werden.

1. Sie können die Anzahl an Datensätzen festlegen, die maximal aus der Zielgruppe extrahiert werden sollen, um die Teilmenge zu erstellen. Überprüfen Sie dazu die **[!UICONTROL Ausgewählte Datensätze begrenzen]** und klicken Sie auf **[!UICONTROL Bearbeiten...]** -Link.

   Mit einem Assistenten können Sie den Auswahlmodus für Datensätze dieser Teilmenge auswählen. Die Schritte finden Sie unter [Anzahl an Datensätzen in Teilmengen begrenzen](#limiting-the-number-of-subset-records).

   ![](assets/s_user_segmentation_partage4.png)

1. **** Durch Klick auf die Schaltfläche **[!UICONTROL Hinzufügen]** können Sie weitere Teilmengen definieren.

   ![](assets/s_user_segmentation_partage_add.png)

   >[!NOTE]
   >
   >Wenn Sie im Allgemein-Tab nicht die Option **[!UICONTROL Überlappung der Ausgabepopulationen zulassen]** angekreuzt haben, werden die Teilmengen in Reihenfolge der Tabs erstellt. Mithilfe der Pfeile oben rechts kann diese angepasst werden. Wenn also die erste Teilmenge beispielsweise 70 % der Ursprungspopulation abruft, werden die Auswahlkriterien der zweiten Teilmenge nur auf die restlichen 30 Prozent angewendet.

   Für jede Teilmenge weist die Aufspaltung standardmäßig eine ausgehende Transition auf.

   ![](assets/s_user_segmentation_partage_add2.png)

   Sie können jedoch auch alle Teilmengen in einer ausgehenden Transition zusammenzufassen. Kreuzen Sie hierzu im **[!UICONTROL Allgemein]**-Tab die Option **[!UICONTROL Alle Teilmengen in derselben Tabelle erzeugen]** an. In diesem Fall kann der Segment-Code verwendet werden, um die Zugehörigkeit zu einer bestimmten Teilmenge anzuzeigen.

   Falls angegeben, wird der Segment-Code aller Teilmengen automatisch in einer Zusatzspalte gespeichert. Auf diese Spalte kann im Rahmen eines Versands über die Personalisierungsfelder zugegriffen werden.

## Anzahl an Datensätzen in Teilmengen begrenzen {#limiting-the-number-of-subset-records}

Es besteht die Möglichkeit, die Anzahl an Datensätzen in Teilmengen zu begrenzen, wenn Sie nicht alle potentiellen Empfänger ansprechen wollen.

1. Kreuzen Sie in diesem Fall die Option **[!UICONTROL Anzahl von Datensätzen begrenzen]** an und klicken Sie auf den Link **[!UICONTROL Bearbeiten...]**.
1. Wählen Sie den Begrenzungstyp aus:

   * **[!UICONTROL Zufallsauswahl aktivieren]**: Die Datenbank-Engine wählt die Datensätze nach dem Zufallsprinzip aus.
   * **[!UICONTROL Nur die ersten Datensätze nach der Sortierung beibehalten]**: Mit dieser Option können Sie eine Begrenzung festlegen, die auf einer oder mehreren Sortierreihenfolgen basiert. Wenn Sie die **[!UICONTROL Alter]** als Sortierungskriterium und 100 als Begrenzung angeben, werden nur die jüngsten 100 Empfänger beibehalten.
   * **[!UICONTROL Die ersten, aus einer Sortierung hervorgehenden Elemente beibehalten (Auswahl nach Kriterien oder zufällig)]**: Kombination der beiden vorangehenden Optionen. Diese Option ermöglicht die Angabe von Sortierungskriterien und im Anschluss eine zufällige Auswahl aus den ersten Datensätzen, falls mehrere Datensätze für die gewählten Kriterien den gleichen Wert aufweisen.

     Angenommen, das Feld **[!UICONTROL Alter]** wurde als Sortierungskriterium gewählt und die Anzahl der auszugebenden Datensätze auf 100 begrenzt. Wenn nun die 2000 jüngsten Empfänger in der Datenbank alle 18 Jahre alt sind, werden aus diesen 2000 Empfängern 100 zufällig ausgewählt.

   ![](assets/s_user_segmentation_partage_wz1.png)

1. Wenn Sie sich für die Definition von Sortierungskriterien entscheiden, können Sie im darauffolgenden Schritt die Spalten und die Reihenfolge der Sortierung bestimmen.

   ![](assets/s_user_segmentation_partage_wz1.1.png)

1. Wählen Sie dann die Begrenzungsmethode aus.

   ![](assets/s_user_segmentation_partage_wz2.png)

   Verschiedene Möglichkeiten bieten sich Ihnen:

   * **[!UICONTROL Größe (in %)]**: Begrenzt die Datensätze auf einen prozentualen Anteil in Bezug auf die gesamte Population (in der vorangehenden Abbildung 10 %).

     Der prozentuale Anteil bezieht sich auf die Eingangspopulation und nicht auf das Ergebnis der Aktivität.

   * **[!UICONTROL Größe (in % von der Teilmenge)]**: Begrenzt die Datensätze auf einen prozentualen Anteil in Bezug auf die Teilmenge (und nicht auf die Eingangspopulation).
   * **[!UICONTROL Maximale Größe]**: Begrenzt die Datensätze auf eine anzugebende Anzahl.
   * **[!UICONTROL Durch Datengruppierung]**: Begrenzt die Datensätze auf die Profile der Eingangspopulation, die in einem anzugebenden Feld einen bestimmten Wert aufweisen. Weitere Informationen zu diesem Thema finden Sie unter [Anzahl an Datensätzen in Teilmengen durch Datengruppierung begrenzen](#limiting-the-number-of-subset-records-by-data-grouping).
   * **[!UICONTROL Durch Datengruppierung (in %)]**: Begrenzt die Datensätze auf die Profile der Eingangspopulation, die in einem anzugebenden Feld einen bestimmten Wert aufweisen, durch einen Prozentsatz. Weitere Informationen zu diesem Thema finden Sie unter [Anzahl an Datensätzen in Teilmengen durch Datengruppierung begrenzen](#limiting-the-number-of-subset-records-by-data-grouping).
   * **[!UICONTROL Durch Datenverteilung]**: Begrenzt die Datensätze, wenn die Gruppierungsfelder zu viele Werte aufweisen oder wenn Sie die Werte nicht bei jeder Aufspaltung neu erfassen möchten (erfordert das Modul **[!UICONTROL Dezentrales Marketing]**). Weitere Informationen hierzu finden Sie unter [Anzahl an Datensätzen in Teilmengen durch Datenverteilung begrenzen](#limiting-the-number-of-subset-records-per-data-distribution).

1. Klicken Sie auf **[!UICONTROL Beenden]**, um die Begrenzungskriterien zu bestätigen. Die Konfiguration wird im zentralen Bereich des Editors zusammenfassend angezeigt.

## Anzahl an Datensätzen in Teilmengen durch Datengruppierung begrenzen {#limiting-the-number-of-subset-records-by-data-grouping}

Die Anzahl an Datensätzen kann mithilfe einer Datengruppierung begrenzt werden. Dies kann entweder über einen prozentualen Anteil oder eine feste Größe geschehen.

Wenn Sie beispielsweise das Feld **[!UICONTROL Sprache]** als Gruppierungsfeld auswählen, können Sie für jede Sprache separat eine Begrenzung definieren.

1. Kreuzen Sie die Option **[!UICONTROL Durch Datengruppierung]** oder **[!UICONTROL Durch Datengruppierung (in %)]** an und klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/s_user_segmentation_partage_wz3.png)

1. Geben Sie dann das oder die Gruppierungsfelder (z. B. **[!UICONTROL Sprache]**) an und klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/s_user_segmentation_partage_wz4.png)

1. Definieren Sie abschließend die Schwellenwerte für die Datengruppierung (unter Verwendung der festen Werte oder Prozentsätze je nach zuvor ausgewählter Gruppierungsmethode). Um für jeden Wert denselben Schwellenwert festzulegen, wählen Sie beispielsweise für jede Sprache die Option **[!UICONTROL Alle Datengruppierungen haben dieselbe Größe]** -Option. Um für jeden Wert eine andere Begrenzung festzulegen, wählen Sie die **[!UICONTROL Einschränkungen nach Gruppierungswert]** -Option. Auf diese Weise können Sie eine andere Einschränkung für Englisch, Französisch usw. auswählen.

   ![](assets/s_user_segmentation_partage_wz5.png)

1. Klicken Sie auf **[!UICONTROL Beenden]**, um die Begrenzungen zu bestätigen und zur Konfiguration der Aufspaltungsaktivität zurückzukehren.

## Anzahl an Datensätzen in Teilmengen durch Datenverteilung begrenzen {#limiting-the-number-of-subset-records-per-data-distribution}

Wenn Ihre Gruppierungsfelder zu viele Werte enthalten oder Sie vermeiden möchten, dass Werte für jede neue Aufspaltungsaktivität zurückgesetzt werden, können Sie mit Adobe Campaign eine Beschränkung für die Datenverteilung erstellen. Wählen Sie bei der Auswahl von Datenbegrenzungswerten (weitere Informationen zu diesem Thema finden Sie im Abschnitt [Teilmengen erstellen](#creating-subsets)) die Option **[!UICONTROL Durch Datenverteilung]** und anschließend eine Vorlage aus dem Dropdown-Menü aus. Die Erstellung einer Datenverteilungsvorlage wird nachfolgend erläutert.

Ein Beispiel für die Aktivität **[!UICONTROL Lokale Validierung]** mit einer Verteilungsvorlage finden Sie unter [Lokale Validierung verwenden](using-the-local-approval-activity.md).

![](assets/s_user_segmentation_partage_wz6.png)

>[!IMPORTANT]
>
>Zur Verwendung dieser Funktion benötigen Sie das Modul Distributed Marketing (Campaign-Option). Bitte prüfen Sie Ihren Lizenzvertrag.

Eine Verteilungsvorlage ermöglicht die Begrenzung der Datensatzanzahl mithilfe einer Gruppierungswertliste. Gehen Sie wie folgt vor, um eine entsprechende Vorlage zu erstellen:

1. Gehen Sie in den Knoten **[!UICONTROL Ressourcen > Kampagnenverwaltung > Datenverteilung]** und klicken Sie auf die Schaltfläche **[!UICONTROL Neu]**.

   ![](assets/local_validation_data_distribution_1.png)

1. Der **[!UICONTROL Allgemein]**-Tab dient der Angabe eines Titels sowie des Ausführungskontexts (Zielgruppendimension und Verteilungsfeld).

   ![](assets/local_validation_data_distribution_2.png)

   Folgende Angaben sind erforderlich:

   * **[!UICONTROL Titel]**: Titel der Verteilungsvorlage.
   * **[!UICONTROL Zielgruppendimension]**: Geben Sie das Schema an, auf das sich die Verteilung beziehen soll, z. B. **[!UICONTROL Empfänger]**. Das Schema muss mit den im Zielgruppen-Workflow verwendeten Daten kompatibel sein.
   * **[!UICONTROL Verteilungsfeld]**: Wählen Sie ein Feld über die Zielgruppendimension aus. Wenn Sie beispielsweise die **[!UICONTROL E-Mail-Domain]** -Feld, wird die Empfängerliste nach Domain aufgeschlüsselt.
   * **[!UICONTROL Verteilungstyp]**: Wählen Sie hier aus, ob der Begrenzungswert im Tab **[!UICONTROL Verteilung]** als **[!UICONTROL Feste Größe]** oder als **[!UICONTROL Größe in Prozent]** ausgedrückt werden soll.
   * **[!UICONTROL Zuweisungstyp]**: Wählen Sie den Zuordnungstyp für die Datenverteilung aus. Sie können zwischen der Zuweisung nach Gruppe oder Benutzer oder der Zuweisung durch die Lokalstelle wählen. Die Zuweisung durch die Lokalstelle wird in **Distributed Marketing**. Weiterführende Informationen hierzu finden Sie in diesem [Abschnitt](../../distributed/using/about-distributed-marketing.md).
   * **[!UICONTROL Validierungsspeicherung]**: Wenn Sie eine Aktivität **[!UICONTROL Lokale Validierung]** in Ihrem Zielgruppen-Workflow verwenden (siehe [Lokale Validierung](local-approval.md)), geben Sie das Schema ein, in dem die Validierungsergebnisse gespeichert werden. Sie müssen ein Speicherschema pro Zielgruppenbestimmungsschema angeben. Wenn Sie das Zielgruppenbestimmungsschema für **[!UICONTROL Empfänger]** verwenden, geben Sie das standardmäßige Speicherschema **[!UICONTROL Lokale Validierung der Empfänger]** ein.

     Bei einer einfachen Begrenzung durch Datenverteilung ohne lokale Validierung, ist im Feld **[!UICONTROL Validierungsspeicherung]** keine Angabe erforderlich.

1. Wenn Sie eine **[!UICONTROL Lokale Validierung]** verwenden (siehe [Lokale Validierung](local-approval.md)), sind auch die **[!UICONTROL Erweiterten Parameter]** der Datenverteilungsvorlage anzugeben:

   ![](assets/local_validation_data_distribution_3.png)

   Folgende Angaben sind erforderlich:

   * **[!UICONTROL Nachrichten validieren]**: Kreuzen Sie diese Option an, wenn alle Empfänger in der Liste der zu validierenden Empfänger vor-ausgewählt sein sollen. Wenn die Option deaktiviert ist, wird kein Empfänger vor-ausgewählt.

     >[!NOTE]
     >
     >Diese Option ist standardmäßig aktiviert.

     ![](assets/local_validation_notification.png)

   * **[!UICONTROL Versandtitel]**: Erlaubt die Definition eines Ausdrucks zur Berechnung des Versandtitels in der Versandreaktionen-Benachrichtigung. Der Standardausdruck gibt den Versandtitel aus (Compute String). Der Ausdruck kann angepasst werden.

     ![](assets/local_validation_notification_3.png)

   * **[!UICONTROL Gruppierungsfeld]**: Erlaubt die Definition der für die Empfängeranzeige in den Validierungs- und Versandreaktionen-Benachrichtigungen verwendeten Gruppierung.

     ![](assets/local_validation_notification_4.png)

   * **[!UICONTROL Webschnittstelle]**: erstellt eine Relation zwischen einer Webanwendung und der Empfängerliste. In der Validierungs- und Versandreaktionen-Benachrichtigung kann jeder Empfänger angeklickt werden und verweist auf die ausgewählte Webanwendung. Die **[!UICONTROL Parameter]** -Feld (z. B. **[!UICONTROL recipientId]**) können Sie den zusätzlichen Parameter konfigurieren, der in der URL und der Webanwendung verwendet werden soll.

     ![](assets/local_validation_notification_5.png)

1. Im Tab **[!UICONTROL Verteilung]** wird die Liste der Verteilungswerte definiert.

   ![](assets/local_validation_data_distribution_4.png)

   * **[!UICONTROL Wert des Verteilungsfeldes]**: Geben Sie die Werte der Verteilung an.
   * **[!UICONTROL Prozent/Feste Größe]**: Geben Sie die jedem Wert zugeordnete Speicherbegrenzung in Prozent oder als feste Größe an.

     Diese Spalte wird durch das Feld **[!UICONTROL Verteilungstyp]** im **[!UICONTROL Allgemein]**-Tab bestimmt.

   * **[!UICONTROL Titel]**: Vergeben Sie für jeden Verteilungswert einen Titel.
   * **[!UICONTROL Gruppe oder Benutzer]**: Wählen Sie im Falle der Verwendung einer Aktivität vom Typ **[!UICONTROL Lokale Validierung]** (siehe [Lokale Validierung](local-approval.md)) für jeden Verteilungswert den zugewiesenen Benutzer oder die Benutzergruppe aus.

     Bei einer einfachen Begrenzung durch Datenverteilung ohne lokale Validierung ist ein Zuweisung in der Spalte **[!UICONTROL Benutzer oder Benutzergruppe]** nicht erforderlich.

     >[!IMPORTANT]
     >
     >Stellen Sie sicher, dass die Benutzer über die nötigen Berechtigungen verfügen.

   * **[!UICONTROL Lokalstelle]**: Wählen Sie für jeden Verteilungswert die Lokalstelle aus. Lokalstellen werden in **Distributed Marketing**. Weiterführende Informationen hierzu finden Sie in diesem [Abschnitt](../../distributed/using/about-distributed-marketing.md).

## Filterparameter {#filtering-parameters}

Gehen Sie in den **[!UICONTROL Allgemein]**-Tab und benennen Sie die Aktivität. Wählen Sie die Zielgruppen- und Filterdimensionen der Aufspaltung aus. Bei Bedarf können diese für jede Teilmenge angepasst werden.

![](assets/s_user_segmentation_partage_general.png)

Kreuzen Sie die Option **[!UICONTROL Komplement erzeugen]** an, wenn Sie auch die restliche Population im weiteren Verlauf des Workflows verwenden möchten. Das Komplement enthält in diesem Fall die eingehende Population abzüglich der Vereinigung der Teilmengen. Die Aufspaltungsaktivität weist somit, wie unten abgebildet, eine zusätzliche Transition auf:

![](assets/s_user_segmentation_partage_compl.png)

Damit diese Option korrekt arbeiten kann, müssen die eingehenden Daten einen Primärschlüssel aufweisen.

Wenn die Daten beispielsweise direkt aus einer externen Datenbank wie Netezza (die keine Unterstützung von Indizes bietet) über eine **[!UICONTROL Laden-(SGBD)]**-Aktivität gelesen werden, ist das von der **[!UICONTROL Aufspaltung]** erzeugte Komplement falsch.

Um dies zu vermeiden, können Sie eine **[!UICONTROL Anreicherung]** -Aktivität direkt vor dem **[!UICONTROL Aufspaltung]** -Aktivität. Im **[!UICONTROL Anreicherung]** Aktivität, überprüfen Sie die **[!UICONTROL Alle zusätzlichen Daten aus der Hauptmenge beibehalten]** und geben Sie in den Zusatzdaten die Spalten an, die Sie zum Konfigurieren der Filter der **[!UICONTROL Aufspaltung]** -Aktivität. Die Daten aus der eingehenden Transition der **[!UICONTROL Aufspaltung]** -Aktivitäten werden dann lokal in einer temporären Tabelle auf dem Adobe Campaign-Server gespeichert und das Komplement kann korrekt generiert werden.

Die Option **[!UICONTROL Überlappung der Ausgabepopulationen zulassen]** ermöglicht den Umgang mit Profilen, die in mehreren Teilmengen enthalten sind:

* Wenn diese Option deaktiviert ist, stellt die Aufspaltung sicher, dass ein Profil nur in einer Ergebnismenge enthalten ist, auch wenn es den Kriterien anderer Teilmengen entspricht. Das Profil ist in der ersten Teilmenge enthalten, dessen Kriterien es entspricht.
* Wenn die Option aktiviert ist, sind die Profile in allen Teilmengen enthalten, deren Kriterien sie erfüllen. Es wird jedoch empfohlen, keine Überlappungen zuzulassen.

## Eingabeparameter {#input-parameters}

* tableName
* schema

Jedes eingehende Ereignis muss eine durch diese Parameter definierte Zielgruppe angeben.

## Ausgabeparameter {#output-parameters}

* tableName
* schema
* recCount

Anhand der drei Werte lässt sich die durch den Ausschluss ermittelte Zielgruppe identifizieren. **[!UICONTROL tableName]** ist der Name der Tabelle, welche die Kennungen der Zielgruppe enthält, **[!UICONTROL schema]** ist das Schema der Population, (in der Regel nms:recipient) und **[!UICONTROL recCount]** ist die Anzahl der Elemente in der Tabelle.

Die Transition des Komplements weist die gleichen Parameter auf.

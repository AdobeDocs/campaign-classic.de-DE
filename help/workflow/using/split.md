---
solution: Campaign Classic
product: campaign
title: Aufspaltung
description: Weitere Informationen zur Aktivität des Arbeitsablaufs "Teilen"
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2133'
ht-degree: 99%

---


# Aufspaltung{#split}

Über die **Aufspaltung** lässt sich eine Population in verschiedene Teilmengen splitten. Die Zielgruppe wird aus allen eingehenden Ergebnissen erstellt, dies bedeutet, dass die vorgeschalteten Aktivitäten beendet sein müssen, bevor die Aufspaltung ausgeführt werden kann.

Da die Aktivität die eingehenden Populationen nicht vereinigt, wird im Fall von mehreren eingehenden Transitionen empfohlen, eine **[!UICONTROL Vereinigung]** vorzuschalten, um eine korrekte Ergebnisfindung zu gewährleisten.

Ein Beispiel der verwendeten Aufspaltungs-Aktivität finden Sie unter [Teilmengen mithilfe der Aufspaltungs-Aktivität erstellen](../../workflow/using/targeting-data.md#creating-subsets-using-the-split-activity).

Ein Beispiel für die Verwendung der Aufspaltungs-Aktivität zur Segmentierung der Zielgruppe in unterschiedliche Populationen mithilfe von Filterbedingungen finden Sie in [diesem Abschnitt](../../workflow/using/cross-channel-delivery-workflow.md).

Ein Beispiel für die Verwendung einer Instanzvariablen in einer Aufspaltungs-Aktivität finden Sie in [diesem Abschnitt](../../workflow/using/javascript-scripts-and-templates.md).

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

1. Es besteht die Möglichkeit, die Anzahl an zu berücksichtigenden Datensätzen zu begrenzen. Kreuzen Sie hierfür die entsprechende Option an und klicken Sie auf den Link **[!UICONTROL Bearbeiten.........]**.****

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
   * **[!UICONTROL Die ersten, aus einer Sortierung hervorgehenden Elemente beibehalten]**: Die Begrenzung erfolgt mithilfe von Sortierungskriterien. Wenn Sie beispielsweise das Feld **[!UICONTROL Alter]** als Kriterium wählen und eine Begrenzung von 100 angeben, werden nur die 100 jüngsten Empfänger beibehalten.
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

1. Definieren Sie nun die Begrenzungswerte der Datengruppierung (je nach gewählter Option in Prozent oder mit einer festen Größe). Kreuzen Sie die Option **[!UICONTROL Alle Datengruppierungen haben die gleiche Größe]** an, wenn jeder Wert mit der gleichen Häufigkeit im Endergebnis vertreten sein soll (beispielsweise je 10 Profile pro Sprache). Die Option **[!UICONTROL Bregrenzungen nach Gruppierungswert]** erlaubt die Angabe einer unterschiedlichen Begrenzung für jeden Wert (beispielsweise 20 für Englisch, 50 für Deutsch etc.).

   ![](assets/s_user_segmentation_partage_wz5.png)

1. Klicken Sie auf **[!UICONTROL Beenden]**, um die Begrenzungen zu bestätigen und zur Konfiguration der Aufspaltungsaktivität zurückzukehren.

## Anzahl an Datensätzen in Teilmengen durch Datenverteilung begrenzen {#limiting-the-number-of-subset-records-per-data-distribution}

Wenn Ihre Gruppierungsfelder zu viele Werte enthalten oder Sie vermeiden möchten, dass Werte für jede neue Split-Aktivität zurückgesetzt werden, können Sie mit Adobe Campaign eine Beschränkung für die Datenverteilung erstellen. Wählen Sie bei der Auswahl von Datenbegrenzungswerten (weitere Informationen zu diesem Thema finden Sie im Abschnitt [Teilmengen erstellen](#creating-subsets)) die Option **[!UICONTROL Durch Datenverteilung]** und anschließend eine Vorlage aus dem Dropdown-Menü aus. Die Erstellung einer Datenverteilungsvorlage wird nachfolgend erläutert.

Ein Beispiel für die Aktivität **[!UICONTROL Lokale Validierung]** mit einer Verteilungsvorlage finden Sie unter [Lokale Validierung verwenden](../../workflow/using/using-the-local-approval-activity.md).

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
   * **[!UICONTROL Verteilungsfeld]**: Wählen Sie ausgehend von der Zielgruppendimension ein Feld aus. Wenn Sie beispielsweise das Feld **[!UICONTROL E-Mail-Domain]** auswählen, werden die Empfänger nach ihren Domains verteilt.
   * **[!UICONTROL Verteilungstyp]**: Wählen Sie hier aus, ob der Begrenzungswert im Tab **[!UICONTROL Verteilung]** als **[!UICONTROL Feste Größe]** oder als **[!UICONTROL Größe in Prozent]** ausgedrückt werden soll.
   * **[!UICONTROL Zuweisungstyp]**: Die Datenverteilung kann entweder einer Gruppe oder einem Benutzer bzw. einer Lokalstelle zugewiesen werden. Eine Zuweisung zu einer Lokalstelle erfolgt im Rahmen des **dezentralen Marketings**. Weiterführende Informationen finden Sie in diesem [Abschnitt](../../campaign/using/about-distributed-marketing.md).
   * **[!UICONTROL Validierungsspeicherung]**: Wenn Sie eine Aktivität **[!UICONTROL Lokale Validierung]** in Ihrem Zielgruppen-Workflow verwenden (siehe [Lokale Validierung](../../workflow/using/local-approval.md)), geben Sie das Schema ein, in dem die Validierungsergebnisse gespeichert werden. Sie müssen ein Speicherschema pro Zielgruppenbestimmungsschema angeben. Wenn Sie das Zielgruppenbestimmungsschema für **[!UICONTROL Empfänger]** verwenden, geben Sie das standardmäßige Speicherschema **[!UICONTROL Lokale Validierung der Empfänger]** ein.

      Bei einer einfachen Begrenzung durch Datenverteilung ohne lokale Validierung, ist im Feld **[!UICONTROL Validierungsspeicherung]** keine Angabe erforderlich.

1. Wenn Sie eine **[!UICONTROL Lokale Validierung]** verwenden (siehe [Lokale Validierung](../../workflow/using/local-approval.md)), sind auch die **[!UICONTROL Erweiterten Parameter]** der Datenverteilungsvorlage anzugeben:

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

   * **[!UICONTROL Webschnittstelle]**: Erlaubt die Zuordnung einer Webschnittstelle zur Empfängerliste. In den Validierungs- und Versandreaktionen-Benachrichtigungen ist dann jeder Empfänger anklickbar und leitet auf die ausgewählte Webschnittstelle weiter. Im Feld **[!UICONTROL Parameter]** (z. B. **[!UICONTROL recipientId]**) kann der zusätzliche Parameter angegeben werden, der in der URL der Webanwendung verwendet werden soll.

      ![](assets/local_validation_notification_5.png)

1. Im Tab **[!UICONTROL Verteilung]** wird die Liste der Verteilungswerte definiert.

   ![](assets/local_validation_data_distribution_4.png)

   * **[!UICONTROL Wert des Verteilungsfeldes]**: Geben Sie die Werte der Verteilung an.
   * **[!UICONTROL Prozent/Feste Größe]**: Geben Sie die jedem Wert zugeordnete Speicherbegrenzung in Prozent oder als feste Größe an.

      Diese Spalte wird durch das Feld **[!UICONTROL Verteilungstyp]** im **[!UICONTROL Allgemein]**-Tab bestimmt.

   * **[!UICONTROL Titel]**: Vergeben Sie für jeden Verteilungswert einen Titel.
   * **[!UICONTROL Gruppe oder Benutzer]**: Wählen Sie im Falle der Verwendung einer Aktivität vom Typ **[!UICONTROL Lokale Validierung]** (siehe [Lokale Validierung](../../workflow/using/local-approval.md)) für jeden Verteilungswert den zugewiesenen Benutzer oder die Benutzergruppe aus.

      Bei einer einfachen Begrenzung durch Datenverteilung ohne lokale Validierung ist ein Zuweisung in der Spalte **[!UICONTROL Benutzer oder Benutzergruppe]** nicht erforderlich.

      >[!IMPORTANT]
      >
      >Stellen Sie sicher, dass die Benutzer über die nötigen Berechtigungen verfügen.

   * **[!UICONTROL Lokalstelle]**: Wählen Sie für jeden Verteilungswert die zugeordnete Lokalstelle aus. Lokalstellen werden im Zusammenhang mit dem **Dezentralen Marketing** verwendet. Weiterführende Informationen finden Sie in diesem [Abschnitt](../../campaign/using/about-distributed-marketing.md).

## Filterparameter {#filtering-parameters}

Gehen Sie in den **[!UICONTROL Allgemein]**-Tab und benennen Sie die Aktivität. Wählen Sie die Zielgruppen- und Filterdimensionen der Aufspaltung aus. Bei Bedarf können diese für jede Teilmenge angepasst werden.

![](assets/s_user_segmentation_partage_general.png)

Kreuzen Sie die Option **[!UICONTROL Komplement erzeugen]** an, wenn Sie auch die restliche Population im weiteren Verlauf des Workflows verwenden möchten. Das Komplement enthält in diesem Fall die eingehende Population abzüglich der Vereinigung der Teilmengen. Die Aufspaltungsaktivität weist somit, wie unten abgebildet, eine zusätzliche Transition auf:

![](assets/s_user_segmentation_partage_compl.png)

Damit diese Option korrekt arbeiten kann, müssen die eingehenden Daten einen Primärschlüssel aufweisen.

Wenn die Daten beispielsweise direkt aus einer externen Datenbank wie Netezza (die keine Unterstützung von Indizes bietet) über eine **[!UICONTROL Laden-(SGBD)]**-Aktivität gelesen werden, ist das von der **[!UICONTROL Aufspaltung]** erzeugte Komplement falsch.

Dies lässt sich vermeiden, indem Sie der **[!UICONTROL Aufspaltung]** eine **[!UICONTROL Anreicherung]** vorschalten. Aktivieren Sie in der **[!UICONTROL Anreicherung]** die Option **[!UICONTROL Alle Zusatzdaten der Hauptmenge beibehalten]** und geben Sie als Zusatzdaten die Spalten an, die Sie für die Konfiguration der Filter der **[!UICONTROL Aufspaltung]** verwenden möchten. Die Daten der in die **[!UICONTROL Aufspaltung]** eingehenden Transition werden in diesem Fall lokal in einer temporären Tabelle auf dem Adobe-Campaign-Server gespeichert und das Komplement kann korrekt erzeugt werden.

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

Anhand der drei Werte lässt sich die durch den Ausschluss ermittelte Zielgruppe identifizieren. **[!UICONTROL tableName]** ist der Name der Tabelle, welche die Kennungen der Zielgruppenempfänger enthält, **[!UICONTROL schema]** ist das Schema der Population, (i. d. R. nms:recipient) und **[!UICONTROL recCount]** ist die Anzahl an Elementen in der Tabelle.

Die Transition des Komplements weist die gleichen Parameter auf.

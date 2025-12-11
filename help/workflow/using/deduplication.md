---
product: campaign
title: Deduplizierung
description: Erfahren Sie mehr über die Workflow-Aktivität "Deduplizierung".
feature: Workflows, Targeting Activity
hide: true
hidefromtoc: true
exl-id: 38add4fe-6238-45de-863e-895ebca189b7
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: ht
source-wordcount: '1171'
ht-degree: 100%

---

# Deduplizierung{#deduplication}



Die Deduplizierung dient der Identifizierung von Duplikaten in der oder den eingehenden Aktivitäten. Zur Identifizierung können beispielsweise die E-Mail-Adresse, eine Telefonnummer oder andere Felder herangezogen werden.

Die Aktivität **[!UICONTROL Deduplizierung]** wird zum Entfernen von Duplikat-Zeilen aus einem Datensatz verwendet. Die folgenden Datensätze können beispielsweise als Duplikate betrachtet werden, da sie dieselbe E-Mail-Adresse und dieselbe Mobil- und/oder Festnetztelefonnummer haben.

| Datum der letzten Änderung | Vorname | Nachname | E-Mail | Mobiltelefon | Telefon |
|-----|------------|-----------|-------|--------------|------|
| 3.2.2020 | Bob | Tisner | bob@mycompany.com | 444-444-4444 | 888-888-8888 |
| 19.5.2020 | Robert | Tisner | bob@mycompany.com | 444-444-4444 | 777-777-7777 |
| 22.7.2020 | Bobby | Tisner | bob@mycompany.com | 444-444-4444 | 777-777-7777 |

Die Aktivität **[!UICONTROL Deduplizierung]** kann eine ganze Zeile als den einzigen Datensatz speichern, nachdem Duplikate identifiziert wurden. Wenn die Aktivität beispielsweise im oben genannten Anwendungsfall so konfiguriert ist, dass nur der Datensatz mit dem ältesten **[!UICONTROL Datum]** beibehalten wird, lautet das Ergebnis:

| Datum | Vorname | Nachname | E-Mail | Mobiltelefon | Telefon |
|-----|----------|------------|-------|--------------|------|
| 3.2.2020 | Bob | Tisner | bob@mycompany.com | 444-444-4444 | 888-888-8888 |

Der ausgewählte Hauptdatensatz leitet die Daten weiter, ohne dass Felddaten mit anderen relevanten Daten in den Duplikat-Zeilen zusammengeführt werden.

Komplement:

| Datum | Vorname | Nachname | E-Mail | Mobiltelefon | Telefon |
|-----|------------|-----------|-------|--------------|------|
| 19.5.2020 | Robert | Tisner | bob@mycompany.com | 444-444-4444 | 777-777-7777 |
| 22.7.2020 | Bobby | Tisner | bob@mycompany.com | 444-444-4444 | 777-777-7777 |

## Best Practices {#best-practices}

Bei der Deduplizierung werden die eingehenden Datenströme getrennt verarbeitet. Wenn also ein Empfänger &#39;A&#39; sowohl im Ergebnis der Abfrage 1 als auch im Ergebnis der Abfrage 2 enthalten ist, wird er nicht dedupliziert.

In diesem Fall ist wie folgt vorzugehen:

* Schließen Sie an die Abfragen zunächst eine **Vereinigung** an, um alle eingehenden Datenströme zusammenzufassen.
* Erstellen Sie dann eine **Deduplizierung** im Anschluss an die **Vereinigung**.

![](assets/dedup_bonnepratique.png)

## Konfiguration {#configuration}

Die Aktivität ist zu benennen, Deduplizierungsmethode und -bedingungen sind anzugeben und gegebenenfalls Optionen in Bezug auf das Ergebnis zu wählen.

1. Klicken Sie auf den Link **[!UICONTROL Konfiguration bearbeiten...]**, um die Deduplizierungsmethode zu definieren.

   ![](assets/s_user_segmentation_dedup_param.png)

1. Wählen Sie den Typ der Zielgruppe für diese Aktivität (Deduplizierung ist standardmäßig mit Empfängern verknüpft) und das zu verwendende Kriterium aus, d. h. das Feld, in dem Sie durch identische Werte Duplikate identifizieren können.

   >[!NOTE]
   >
   >Wenn Sie externe Daten als Eingabe verwenden möchten (z. B. Daten aus einer externen Datei), müssen Sie die Option **[!UICONTROL Temporäres Schema]** markieren.
   >
   >Die Option **[!UICONTROL Andere]** ermöglicht im nächsten Schritt die Auswahl der zu verwendenden Kriterien:

   ![](assets/s_user_segmentation_dedup_param2.png)

1. Die Option **[!UICONTROL Andere]** ermöglicht im nächsten Schritt die Auswahl der zu verwendenden Kriterien im Fall von identischen Werten.

   ![](assets/s_user_segmentation_dedup_param3.png)

1. Wählen Sie aus der Dropdown-Liste die gewünschte Methode aus und geben Sie die Anzahl an beizubehaltenden Duplikate an.

   ![](assets/s_user_segmentation_dedup_param4.png)

   Folgende Methoden stehen zur Verfügung:

   * **[!UICONTROL Automatische Auswahl]**: wählt nach dem Zufallsprinzip unter den Duplikaten den beizubehaltenden Datensatz aus.
   * **[!UICONTROL Gemäß einer Werteliste]**: ermöglicht die Bestimmung einer Reihenfolge nach Priorität von Werten für ein oder mehrere Felder. Wählen Sie zur Bestimmung dieser Werte ein Feld aus oder erstellen Sie einen Ausdruck, fügen Sie dann den oder die Werte der entsprechenden Tabelle hinzu. Verwenden Sie die Schaltfläche **[!UICONTROL Hinzufügen]** oberhalb der Werteliste, um ein neues Feld zu definieren.

     ![](assets/s_user_segmentation_dedup_param5.png)

   * **[!UICONTROL Wert nicht leer]**: hiermit lassen sich vornehmlich jene Datensätze beibehalten, für die der Wert des ausgewählten Ausdrucks nicht leer ist.

     ![](assets/s_user_segmentation_dedup_param6.png)

   * **[!UICONTROL Von einem Ausdruck ausgehend]**: Beibehalten werden die Datensätze, für die der ausgewählte Ausdruck den kleinsten oder größen Wert aufweist.

     ![](assets/s_user_segmentation_dedup_param7.png)

   >[!NOTE]
   >
   >Mit der Funktion **[!UICONTROL Zusammenführen]**, die über den Link **[!UICONTROL Erweiterte Parameter]** aufgerufen werden kann, können Sie einen Regelsatz konfigurieren, um ein Feld oder eine Gruppe von Feldern zu einem einzigen Ergebnisdatensatz zusammenzuführen. Weitere Informationen hierzu finden Sie unter [Zusammenführen von Feldern zu einem einzigen Datensatz](#merging-fields-into-single-record).

1. Klicken Sie auf **[!UICONTROL Beenden]**, um die Auswahl der Deduplizierungsmethode zu bestätigen.

   Die konfigurierten Deduplizierungsparameter werden zusammenfassend angezeigt.

   Im unteren Bereich des Fensters können Sie den Titel der ausgehenden Transition anpassen und einen Segment-Code angeben, der dem Ergebnis zugeordnet wird. Dieser Code kann im weiteren Verlauf als Kriterium bei der Zielgruppenbestimmung herangezogen werden.

   ![](assets/s_user_segmentation_dedup_param8.png)

1. Kreuzen Sie die Option **[!UICONTROL Komplement erzeugen]** an, wenn Sie auch die restliche Population im weiteren Verlauf des Workflows verwenden möchten. Das Komplement enthält in diesem Fall alle Duplikate und die Aktivität weist somit, wie unten abgebildet, eine zusätzliche Transition auf:

   ![](assets/s_user_segmentation_dedup_param9.png)

## Anwendungsbeispiel: Duplikate identifizieren, bevor ein Versand gestartet wird {#example--identify-the-duplicates-before-a-delivery}

Im folgenden Beispiel soll die Vereinigung der Ergebnisse dreier Abfragen dedupliziert werden.

Ziel des Workflows ist die Bestimmung einer Versandzielgruppe ohne Duplikate, damit dieselben Empfänger den Versand nicht mehrmals erhalten.

Die identifizierten Duplikate werden für eine eventuelle spätere Verwendung in einer spezifischen Liste gespeichert.

![](assets/deduplication_example.png)

1. Positionnieren Sie die erforderlichen Aktivitäten wie oben abgebildet im Workflow-Diagramm.

   Die Vereinigungsaktivität dient hier der Zusammenführung der verschiedenen Abfrageergebnisse in einer ausgehenden Transition. Auf diese Weise erfolgt die Deduplizierung nicht separat für jede Abfrage, sondern gebündelt für alle Ergebnisse. Weitere Informationen zu diesem Thema finden Sie unter [Best Practices](#best-practices).

1. Öffnen Sie die Deduplizierungsaktivität und klicken Sie auf den Link **[!UICONTROL Konfiguration bearbeiten...]**, um die Deduplizierungsmethode zu bestimmen.
1. Wählen Sie im sich öffnenden Fenster die Option **[!UICONTROL Datenbankschema]** aus.
1. Wählen Sie für die Zielgruppenbestimmungs- und die Filterdimension jeweils **Empfänger** aus.
1. Kreuzen Sie **[!UICONTROL E-Mail]** als Identifizierungskriterium der Duplikate an, damit jeder Empfänger den Versand nur einmal erhält. Klicken Sie auf **[!UICONTROL Weiter]**.

   Wenn die Identifizierung der Duplikate auf einem anderen als den angebotenen Feldern basieren soll, kreuzen Sie **[!UICONTROL Sonstige]** an. Im nächsten Schritt können Sie dann das Feld aus den in der zugrundeliegenden Tabelle enthaltenen auswählen.

1. Geben Sie an, dass nur ein Datensatz beibehalten werden soll, wenn dieselbe E-Mail-Adresse für mehrere Empfänger identifiziert wurde.
1. Wählen Sie als Deduplizierungsmethode **[!UICONTROL Automatische Auswahl]**, damit der beizubehaltende Datensatz zufällig bestimmt wird. Klicken Sie abschließend auf **[!UICONTROL Beenden]**.

Bei Ausführung des Workflows werden die als Duplikate identifizierten Empfänger von der Ergebnismenge (und somit vom Versand) ausgeschlossen und in der Liste der Duplikate gespeichert. Diese Liste kann erneut verwendet werden, um die Identifizierung der Duplikate nicht wiederholt vornehmen zu müssen.

## Zusammenführen von Feldern zu einem einzigen Datensatz {#merging-fields-into-single-record}

Mit der Funktion **[!UICONTROL Zusammenführen]** können Sie einen Regelsatz für die Deduplizierung konfigurieren, um ein Feld oder eine Feldgruppe zu definieren, das bzw. die zu einem einzigen Ergebnisdatensatz zusammengeführt werden soll.

Bei einer Reihe von Duplikat-Datensätzen können Sie beispielsweise entscheiden, jeweils die älteste Telefonnummer oder den neuesten Namen beizubehalten.

Ein Anwendungsfall, der diese Funktion nutzt, ist in [diesem Abschnitt](deduplication-merge.md) verfügbar.

Gehen Sie dazu wie folgt vor:

1. Klicken Sie im Auswahlschritt **[!UICONTROL Deduplizierungsmethode]** auf den Link **[!UICONTROL Erweiterte Parameter]**.

   ![](assets/dedup1.png)

1. Wählen Sie die Option **[!UICONTROL Datensätze zusammenführen]** aus, um die Funktion zu aktivieren.

   Wenn Sie mehrere Datenfelder in jeder Zusammenführungsbedingung gruppieren möchten, aktivieren Sie die Option **[!UICONTROL Mehrere Kriterien für die Zusammenführung von Datensätzen verwenden]**.

   ![](assets/dedup2.png)

1. Nach Aktivierung der Funktion wird der Aktivität **[!UICONTROL Deduplizierung]** die Registerkarte **[!UICONTROL Zusammenführen]** hinzugefügt. Damit können Sie Gruppen von Feldern definieren, die zusammengeführt werden sollen, sowie die zugehörigen Regeln.

   Weitere Informationen hierzu finden Sie im Anwendungsfall in [diesem Abschnitt](deduplication-merge.md).

   ![](assets/dedup3.png)

## Eingabeparameter {#input-parameters}

* tableName
* schema

Jedes eingehende Ereignis muss eine durch diese Parameter definierte Zielgruppe angeben.

## Ausgabeparameter {#output-parameters}

* tableName
* schema
* recCount

Anhand der drei Werte lässt sich die durch die Deduplizierung ermittelte Zielgruppe identifizieren. **[!UICONTROL tableName]** ist der Name der Tabelle, die die Kennungen der Zielgruppenempfangenden speichert, **[!UICONTROL schema]** ist das Schema der Population, (i. d. R. „nms:recipient“) und **[!UICONTROL recCount]** ist die Anzahl der Elemente in der Tabelle.

Die Transition des Komplements weist die gleichen Parameter auf.

---
product: campaign
title: Deduplizierung
description: Erfahren Sie mehr über die Workflow-Aktivität "Deduplizierung".
feature: Workflows, Targeting Activity
hide: true
exl-id: 38add4fe-6238-45de-863e-895ebca189b7
TQID: https://experienceleague.adobe.com/wQ6v5bFKx8hd7zLjR6t7GjE1D2iTW9is0lbrj8-UbRg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 1192
ht-degree: 100%

---

# Deduplizierung{#deduplication}



Die Deduplizierung dient der Identifizierung von Dubletten in der oder den eingehenden Aktivitäten. Zur Deduplizierung können beispielsweise die E-Mail-Adresse, eine Telefonnummer oder andere Felder herangezogen werden.

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

Bei einer Deduplizierung werden die eingehenden Flüsse getrennt voneinander verarbeitet. Wenn also eine Person „A“ sowohl im Ergebnis der Abfrage 1 als auch im Ergebnis der Abfrage 2 enthalten ist, wird sie nicht dedupliziert.

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

   Im unteren Bereich des Fensters können Sie den Titel der ausgehenden Transition des Grafikobjekts anpassen und einen Segment-Code angeben, der dem Ergebnis zugeordnet wird. Dieser Code kann später als Kriterium für die Zielgruppenbestimmung verwendet werden.

   ![](assets/s_user_segmentation_dedup_param8.png)

1. Aktivieren Sie die Option **[!UICONTROL Komplement erzeugen]**, wenn Sie auch die verbleibende Population verwenden möchten. Das Komplement besteht aus allen Duplikaten. Die Aktivität weist somit eine zusätzliche ausgehende Transition auf, wie im Folgenden gezeigt:

   ![](assets/s_user_segmentation_dedup_param9.png)

## Anwendungsbeispiel: Duplikate identifizieren, bevor ein Versand gestartet wird {#example--identify-the-duplicates-before-a-delivery}

Im folgenden Beispiel soll die Vereinigung der Ergebnisse dreier Abfragen dedupliziert werden.

Ziel des Workflows ist die Bestimmung einer Versandzielgruppe ohne Duplikate, damit dieselben Empfänger den Versand nicht mehrmals erhalten.

Die identifizierten Duplikate werden für eine eventuelle spätere Verwendung in einer spezifischen Liste gespeichert.

![](assets/deduplication_example.png)

1. Positionnieren Sie die erforderlichen Aktivitäten wie oben abgebildet im Workflow-Diagramm.

   Die Vereinigungsaktivität wird hier verwendet, um die drei Abfragen in einer einzigen Transition zu „vereinen“. Auf diese Weise erfolgt die Deduplizierung nicht separat für jede Abfrage, sondern gebündelt für alle Ergebnisse. Weitere Informationen zu diesem Thema finden Sie unter [Best Practices](#best-practices).

1. Öffnen Sie die Deduplizierungsaktivität und klicken Sie auf den Link **[!UICONTROL Konfiguration bearbeiten...]**, um die Deduplizierungsmethode zu bestimmen.
1. Wählen Sie im sich öffnenden Fenster die Option **[!UICONTROL Datenbankschema]** aus.
1. Wählen Sie für die Zielgruppenbestimmungs- und die Filterdimension jeweils **Empfänger** aus.
1. Kreuzen Sie **[!UICONTROL E-Mail]** als Identifizierungskriterium der Duplikate an, damit jeder Empfänger den Versand nur einmal erhält. Klicken Sie auf **[!UICONTROL Weiter]**.

   Wenn die Identifizierung der Duplikate auf einem anderen als den angebotenen Feldern basieren soll, kreuzen Sie **[!UICONTROL Sonstige]** an. Im nächsten Schritt können Sie dann das Feld aus den in der zugrundeliegenden Tabelle enthaltenen auswählen.

1. Geben Sie an, dass nur ein Datensatz beibehalten werden soll, wenn dieselbe E-Mail-Adresse für mehrere Empfänger identifiziert wurde.
1. Wählen Sie als Deduplizierungsmethode **[!UICONTROL Automatische Auswahl]**, damit der beizubehaltende Datensatz zufällig bestimmt wird. Klicken Sie abschließend auf **[!UICONTROL Beenden]**.

Bei Ausführung des Workflows werden die als Duplikate identifizierten Empfangenden aus der Ergebnismenge (und somit vom Versand) ausgeschlossen und in der Liste der Duplikate gespeichert. Diese Liste kann erneut verwendet werden, sodass die Duplikate nicht erneut identifiziert werden müssen.

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

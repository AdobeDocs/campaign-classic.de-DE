---
title: Deduplizierung
seo-title: Deduplizierung
description: Deduplizierung
seo-description: null
page-status-flag: never-activated
uuid: 90dee589-ac45-442e-89ef-1c14bb22200d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 83b915bd-7e23-41b5-9f9a-f7eb72026376
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Deduplizierung{#deduplication}

Die Deduplizierung dient der Identifizierung von Dubletten in der oder den eingehenden Aktivitäten. Zur Identifizierung können beispielsweise die E-Mail-Adresse, eine Telefonnummer oder andere Felder herangezogen werden.

## Best Practices {#best-practices}

Bei der Deduplizierung werden die eingehenden Datenströme getrennt verarbeitet. Wenn also ein Empfänger &#39;A&#39; sowohl im Ergebnis der Abfrage 1 als auch im Ergebnis der Abfrage 2 enthalten ist, wird er nicht dedupliziert.

In diesem Fall ist wie folgt vorzugehen:

* Schließen Sie an die Abfragen zunächst eine **Vereinigung** an, um alle eingehenden Datenströme zusammenzufassen.
* Erstellen Sie dann eine **Deduplizierung** im Anschluss an die **Vereinigung**.

![](assets/dedup_bonnepratique.png)

## Konfiguration {#configuration}

Die Aktivität ist zu benennen, Deduplizierungsmethode und -bedingungen sind anzugeben und gegebenenfalls Optionen in Bezug auf das Ergebnis zu wählen.

Click the **[!UICONTROL Edit configuration...]** link to define the deduplication mode.

![](assets/s_user_segmentation_dedup_param.png)

1. Auswahl der Zielgruppe

   Wählen Sie die Zielgruppendimension aus (standardmäßig bezieht sich die Deduplizierung auf die Empfänger) und kreuzen Sie das für die Identifizierung von Dubletten zu verwendende Feld an: E-Mail-Adresse, Telefon (Mobil oder Festnetz), Fax oder Postanschrift.

   ![](assets/s_user_segmentation_dedup_param2.png)

   In the next step, the **[!UICONTROL Other]** option lets you select the criterion or criteria to be used:

   ![](assets/s_user_segmentation_dedup_param3.png)

1. Deduplizierungsmethode

   Wählen Sie aus der Dropdown-Liste die gewünschte Methode aus und geben Sie die Anzahl an beizubehaltenden Dubletten an.

   ![](assets/s_user_segmentation_dedup_param4.png)

   Folgende Methoden stehen zur Verfügung:

   * **[!UICONTROL Choose for me]**: wählt zufällig den Datensatz aus den Duplikaten aus.
   * **[!UICONTROL Following a list of values]**: können Sie eine Wertpriorität für ein oder mehrere Felder definieren. Wählen Sie zur Bestimmung dieser Werte ein Feld aus oder erstellen Sie einen Ausdruck, fügen Sie dann den oder die Werte der entsprechenden Tabelle hinzu. To define a new field, click the **[!UICONTROL Add]** button located above the list of values.

      ![](assets/s_user_segmentation_dedup_param5.png)

   * **[!UICONTROL Non-empty value]**: Auf diese Weise können Sie Datensätze speichern, für die der Wert des ausgewählten Ausdrucks als Priorität nicht leer ist.

      ![](assets/s_user_segmentation_dedup_param6.png)

   * **[!UICONTROL Using an expression]**: können Sie Datensätze mit dem niedrigsten (oder höchsten) Wert des angegebenen Ausdrucks führen.

      ![](assets/s_user_segmentation_dedup_param7.png)
   Click **[!UICONTROL Finish]** to approve the selected deduplication method.

   Die konfigurierten Deduplizierungsparameter werden zusammenfassend angezeigt.

   Im unteren Bereich des Fensters können Sie den Titel der ausgehenden Transition anpassen und einen Segment-Code angeben, der dem Ergebnis zugeordnet wird. Dieser Code kann im weiteren Verlauf als Kriterium bei der Zielgruppenbestimmung herangezogen werden.

   ![](assets/s_user_segmentation_dedup_param8.png)

   Aktivieren Sie die **[!UICONTROL Generate complement]** Option, wenn Sie die verbleibende Population ausnutzen möchten. Die Ergänzung besteht aus allen Duplikaten. Anschließend wird der Aktivität ein zusätzlicher Übergang wie folgt hinzugefügt:

   ![](assets/s_user_segmentation_dedup_param9.png)

## Anwendungsbeispiel: Dubletten identifizieren, bevor ein Versand gestartet wird {#example--identify-the-duplicates-before-a-delivery}

Im folgenden Beispiel soll die Vereinigung der Ergebnisse dreier Abfragen dedupliziert werden.

Ziel des Workflows ist die Bestimmung einer Versandzielgruppe ohne Dubletten, damit dieselben Empfänger den Versand nicht mehrmals erhalten.

Die identifizierten Dubletten werden für eine eventuelle spätere Verwendung in einer spezifischen Liste gespeichert.

![](assets/deduplication_example.png)

1. Positionnieren Sie die erforderlichen Aktivitäten wie oben abgebildet im Workflow-Diagramm.

   Die Gewerkschaftsaktivität wird hier verwendet, um die drei Abfragen in einem einzigen Übergang zu &quot;vereinen&quot;. Deduplizierung funktioniert daher nicht für jede Abfrage einzeln, sondern für die gesamte Abfrage. Weitere Informationen zu diesem Thema finden Sie unter [Bewährte Verfahren](#best-practices).

1. Open the deduplication activity then click the **[!UICONTROL Edit configuration...]** link to define the deduplication mode.
1. Wählen Sie im neuen Fenster **[!UICONTROL Database schema]**.
1. Wählen Sie für die Zielgruppen- und die Filterdimension jeweils **Empfänger** aus.
1. Select the ID field for the **[!UICONTROL Email]** duplicates, to send the delivery only once to every email address, then click **[!UICONTROL Next]**.

   If you wish to base the duplicate IDs on a specific field, select **[!UICONTROL Other]** to access the list of available fields.

1. Geben Sie an, dass nur ein Datensatz beibehalten werden soll, wenn dieselbe E-Mail-Adresse für mehrere Empfänger identifiziert wurde.
1. Select the **[!UICONTROL Choose for me]** deduplication mode so that the records saved in case of identified duplicates are randomly chosen, then click **[!UICONTROL Finish]**.

Bei Ausführung des Workflows werden die als Dubletten identifizierten Empfänger von der Ergebnismenge (und somit vom Versand) ausgeschlossen und in der Liste der Dubletten gespeichert. Diese Liste kann erneut verwendet werden, um die Identifizierung der Dubletten nicht wiederholt vornehmen zu müssen.

## Eingabeparameter {#input-parameters}

* tableName
* schema

Jedes eingehende Ereignis muss eine durch diese Parameter definierte Zielgruppe angeben.

## Ausgabeparameter {#output-parameters}

* tableName
* schema
* recCount

Dieser Satz von drei Werten identifiziert das Ziel, das sich aus der Deduplizierung ergibt. **[!UICONTROL tableName]** ist der Name der Tabelle, in der Zielkennungen gespeichert werden, das Schema der Population (normalerweise nms:empfänger) und die Anzahl der Elemente in der Tabelle **[!UICONTROL schema]** ist **[!UICONTROL recCount]** dies.

Die Transition des Komplements weist die gleichen Parameter auf.

---
solution: Campaign Classic
product: campaign
title: Erstellung einer zusammenfassenden Liste.
description: Erstellung einer zusammenfassenden Liste.
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1060'
ht-degree: 100%

---


# Erstellung einer zusammenfassenden Liste.{#creating-a-summary-list}

Das folgende Anwendungsbeispiel erläutert die Erstellung eines Workflows zum Abruf und zur Anreicherung von Dateien mit dem Ziel, eine zusammenfassende Liste zu erstellen. Die zu erstellende Liste enthält Kontakte, die Einkäufe in Geschäften getätigt haben.

![](assets/uc2_enrich_overview.png)

Die Datenstruktur stellt sich wie folgt dar:

![](assets/uc2_enrich_data.png)

Sie ermöglicht Ihnen Folgendes:

* Verwendung der verschiedenen Optionen der Anreicherung;
* Aktualisierung der in der Datenbank gespeicherten Informationen im Anschluss an eine Abstimmung;
* Erstellung einer Gesamtübersicht der angereicherten Daten.

Gehen Sie wie folgt vor, um eine zusammenfassende Liste zu erstellen:

1. Abruf und Ladung einer Verkaufsdatei in die Workflow-Arbeitstabelle.
1. Anreicherung der importierten Daten durch Erstellung einer Relation zu einer Referenztabellle.
1. Aktualisierung der Verkaufsdatei mit den Anreicherungsdaten.
1. Anreicherung der Kontaktdaten mit einem aus der Verkaufstabelle stammenden Aggregat.
1. Erstellung einer zusammenfassenden Liste.

## 1. Schritt: Laden der Datei und Abstimmung der importierten Daten {#step-1--loading-the-file-and-reconciling-the-imported-data}

Die zu ladenden Verkaufsdaten weisen folgende Struktur auf:

```
Product Name;Product price;Store
Computer;2000;London 3
Tablet;600;Cambridge
Computer;2000;London 5
Comptuer;2000;London 8
Tablet;600;Cambridge
Phone;500;London 5
```

Die Daten stammen aus der Datei &quot;Verkauf.txt&quot;

1. Ziehen Sie die Aktivitäten **Datei-Wächter** und **Laden (Datei)** in das Workflow-Diagramm.

   Der **Datei-Wächter** sammelt Dateien und sendet sie auf den Adobe-Campaign-Server.

   Die Aktivität **Laden (Datei)** lädt die gesammelten Daten in die Arbeitstabelle des Workflows.

   Weitere Informationen zu dieser Aktivität finden Sie unter [Daten aus einer Datei laden](../../workflow/using/importing-data.md#loading-data-from-a-file).

1. Konfigurieren Sie den **Datei-Wächter** dahingehend, dass er Textdateien (.txt) im angegebenen Verzeichnis abruft.

   ![](assets/uc2_enrich_collecteur.png)

   Die Aktivität ist auch in der Lage, dass Nicht-Vorhandensein von Dateien im bezeichneten Verzeichnis zu verarbeiten. Kreuzen Sie hierfür die Option **Fehlen von Dateien verarbeiten** an. Die in diesem Workflow enthaltene **[!UICONTROL Warten]**-Aktivität löst einen erneuten Abrufversuch aus, wenn zuvor keine Datei im angegebenen Verzeichnis enthalten war.****

1. Konfigurieren Sie die Aktivität **Laden (Datei)**, indem Sie eine Beispieldatei angeben, die die gleiche Datenstruktur wie die zu importierenden Daten aufweist.

   ![](assets/uc2_enrich_chargement1.png)

   Klicken Sie auf den Link **[!UICONTROL Zur Formatänderung hier klicken...]**, um die Spaltenbezeichnungen denen der Verkauf-Tabelle anzupassen.

   ![](assets/uc2_enrich_chargement2.png)

Nach dem Import der Daten, werden diese durch Erstellung einer Relation zur Referenztabelle (hier Geschäft) angereichert.

Ziehen Sie die Anreicherung in das Diagramm und konfigurieren Sie sie wie folgt:

1. Definieren Sie als Hauptmenge die aus der Aktivität **Laden (Datei)** stammenden Daten.

   ![](assets/uc2_enrich_enrich1.png)

1. Klicken Sie auf **[!UICONTROL Daten hinzufügen]** und wählen Sie die Option **[!UICONTROL Relation]** aus.

   ![](assets/uc2_enrich_enrich2.png)

1. Aktivieren Sie die Option **[!UICONTROL Kollektion definieren]**.
1. Wählen Sie das Schema &quot;Geschäfte&quot; als Zielschema aus.

   ![](assets/uc2_enrich_enrich3.png)

Weitere Informationen zu den verschiedenen Link-Typen finden Sie unter [Daten anreichern und ändern](../../workflow/using/targeting-data.md#enriching-and-modifying-data).

Im nächsten Bildschirm ist der Join zu erstellen, der die Abstimmung zwischen den Daten erlaubt. Wählen Sie aus der Hauptmenge die Quelle und aus dem Schema &quot;Geschäfte&quot; den Zieldatensatz aus.

![](assets/uc2_enrich_enrich4.png)

Dank des Joins ist es nun möglich, die Workflow-Arbeitstabelle um eine aus dem Schema &quot;Geschäfte&quot; stammende Spalte zu erweitern: hier &quot;Referenz-Postleitzahl&quot;.

1. Öffnen Sie die Anreicherung.
1. Klicken Sie auf **[!UICONTROL Zusätzliche Daten bearbeiten...]**
1. Fügen Sie &quot;Referenz-Postleitzahl&quot; zu den **[!UICONTROL Ausgabespalten]** hinzu.

![](assets/uc2_enrich_enrich5.png)

Nach der Anreicherung stellen sich die Daten der Workflow-Arbeitstabelle wie folgt dar:

![](assets/uc2_enrich_population1.png)

## 2. Schritt: Schreiben der angereicherten Daten in die &#39;Verkauf&#39;-Tabelle {#step-2--writing-enriched-data-to-the--purchases--table}

In diesem Schritt werden die importierten und angereicherten Daten in die &quot;Verkauf&quot;-Tabelle geschrieben. Dies geschieht mithilfe der Aktivität **Datenaktualisierung**.

Vor der Aktualisierung sind die Daten der Workflow-Arbeitstabelle mit denen aus der Zielgruppendimension **Verkauf** abzustimmen.****

1. Gehen Sie in den Tab **[!UICONTROL Abstimmung]** der Anreicherung.
1. Wählen Sie die Zieldimension, im vorliegenden Beispiel also das Schema &#39;Verkauf&#39;, aus.
1. Geben Sie einen Quellausdruck für die Daten der Workflow-Arbeitstabelle an (hier &quot;NameGeschäft&quot;).
1. Geben Sie dann einen Zielausdruck für die Daten der Verkauf-Tabelle an (hier &quot;NameGeschäft&quot;).
1. Aktivieren Sie die Option **[!UICONTROL Nicht zugeordnete Daten aus der Arbeitstabelle beibehalten]**.

![](assets/uc2_enrich_reconciliation.png)

Konfigurieren Sie die **Datenaktualisierung**-Aktivität wie folgt:

1. Aktivieren Sie im Feld **[!UICONTROL Aktionstyp]** die Option **[!UICONTROL Hinzufügen oder aktualisieren]**, um zu vermeiden, dass bei jedem Datenabruf neue Datensätze erstellt werden.
1. Geben Sie bei der Option **[!UICONTROL Datensatz-Identifizierung]** den Wert **[!UICONTROL Über die Zielgruppendimension]** an.
1. Wählen Sie als **[!UICONTROL Dokumenttyp]** das Schema &quot;Verkauf&quot; aus.
1. Definieren Sie die zu aktualisierenden Felder. Geben Sie hierzu in der Spalte **[!UICONTROL Ziel]** die Felder des Schemas &quot;Verkauf&quot; und in der Spalte **[!UICONTROL Ausdruck]** die entsprechenden Felder der Workflow-Arbeitstabelle an, um die Felder zu mappen.
1. Aktivieren Sie die Option **[!UICONTROL Ausgehende Transition erzeugen]**.

![](assets/uc2_enrich_miseajour.png)

## 3. Schritt: Anreicherung der &#39;Kontakt&#39;-Daten {#step-3--enriching--contact--data-}

Das Schema &quot;Kontakte&quot; steht in Relation zum Schema &#39;Verkauf&#39;. Dies ermöglicht die Verwendung einer weiteren Option der Anreicherungsaktivität, nämlich die Hinzufügung von Daten in Relation mit der Filterdimension.

Ziel dieser zweiten Anreicherung ist es, ein Aggregat von Verkaufsdaten zu erstellen, um den Gesamtumsatz pro identifiziertem Kontakt zu berechnen.

1. Ziehen Sie eine **Abfrage** in das Workflow-Diagramm, um alle in der Datenbank gespeicherten **Kontakte** abzurufen.
1. Schließen Sie eine **Anreicherung** an und definieren Sie als Hauptmenge die Population aus der vorangehenden Abfrage.
1. Klicken Sie auf **[!UICONTROL Daten hinzufügen]**.
1. Aktivieren Sie die Option **[!UICONTROL Daten in Relation mit der Filterdimension]**.
1. Wählen Sie im Fenster **[!UICONTROL Auswahl der hinzuzufügenden Daten]** erneut die Option **[!UICONTROL Daten in Relation mit der Filterdimension]** aus.
1. Markieren Sie den Knoten **[!UICONTROL Verkauf]** und klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/uc2_enrich_enrich9.png)

1. Wählen Sie aus der Dropdown-Liste des Felds **[!UICONTROL Abgerufene Daten]** die Option **[!UICONTROL Aggregate]** aus.

   ![](assets/uc2_enrich_enrich10.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie folgenden Ausdruck an, um für jeden Kontakt die Summe der Verkäufe zu berechnen: &quot;Sum(@artikelpreis)&quot;.

   ![](assets/uc2_enrich_enrich6.png)

Für die zusammenfassende Liste werden Felder aus dem Verkaufsschema und aus der ersten Anreicherung benötigt.

1. Klicken Sie daher in der Anreicherung auf den Link **[!UICONTROL Zusätzliche Daten bearbeiten...]**.
1. Fügen Sie die Felder &quot;Verkauf/NameGeschäft&quot; und &quot;Verkauf/Referenz-Postleitzahl&quot; hinzu.

   ![](assets/uc2_enrich_enrich7.png)

1. Gehen Sie in den Tab **[!UICONTROL Eigenschaften]**.
1. Ändern Sie die zweite Relation, um nur eine Zeile zu erstellen.

   ![](assets/uc2_enrich_enrich8.png)

## 4. Schritt: Erstellung einer zusammenfassenden Liste {#step-4--creating-and-adding-to-a-summary-list}

Im letzten Schritt werden die angereicherten Daten in eine Liste geschrieben.

1. Platzieren Sie im Anschluss an die zweite Anreicherung ein **Listen-Update** im Workflow-Diagramm.
1. Aktivieren Sie die Option **[!UICONTROL Wenn nötig Liste erstellen (Titel berechnet)]**.
1. Wählen Sie einen Wert für den berechneten Titel aus. Im vorliegenden Beispiel wird das aktuelle Datum als Titel für die Liste verwendet: &lt;%= formatDate(new Date(), &quot;%2D.%2M.%2Y&quot;) %>.

Nach Ausführung des Workflows enthält die Liste folgende Informationen:

* eine Liste an Kontakten,
* eine Spalte mit Gesamtumsätzen,
* eine Spalte mit Geschäftsbezeichnungen,
* eine Spalte mit der Referenz-Postleitzahl für die Geschäfte, die im Referenzschema der Geschäfte enthalten sind.

![](assets/uc2_enrich_listfinal.png)


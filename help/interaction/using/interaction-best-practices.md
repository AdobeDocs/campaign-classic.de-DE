---
product: campaign
title: Best Practices für Adobe Campaign Classic Interaction
description: In diesem Abschnitt werden Best Practices für die Verwaltung des Interaction-Moduls in Adobe Campaign Classic vorgestellt
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: interaction-overview
exl-id: 98413cde-50c9-416c-8316-85837f724c27
TQID: https://experienceleague.adobe.com/3EnUxwwGdhqG7vmysgbDBwiCbbBIl2bG1byaRe3j6O8
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 1210
ht-degree: 75%

---

# Best Practices für Interaction{#interaction-best-practices}



## Allgemeine Empfehlungen {#general-recommendations}

In diesem Abschnitt werden Best Practices für die Verwaltung des Interaction-Moduls in Adobe Campaign Classic vorgestellt, einschließlich Eignungsregeln, vordefinierter Filter, Workflow-Aktivitäten und Datenbankoptionen.

Interaktion in Adobe Campaign erfordert sorgfältige Verwaltung, um effizient zu funktionieren. Sie müssen ein Gleichgewicht zwischen der Anzahl der Kontakte und der Anzahl der Angebotskategorien und Angebote finden. Wenn diese Faktoren nicht sorgfältig gehandhabt werden, kann es zu Problemen in Ihrer Adobe Campaign-Instanz kommen.

### Implementierung {#implementation}

Im Folgenden sind wichtige Elemente aufgelistet, die bei der Implementierung und Konfiguration von Interaktionen beachtet werden sollten.

* Bei Batch-Modulen (die in der Regel in ausgehenden Kommunikationen wie E-Mails verwendet werden) ist der Durchsatz das Hauptproblem, da mehrere Kontakte gleichzeitig verarbeitet werden können. Der typische Engpass ist die Datenbankleistung.
* Die wichtigste Einschränkung für eine einheitliche Engine (wird normalerweise in eingehenden Kommunikationen wie einem Banner auf einer Website verwendet) ist Latenz, da jemand eine Antwort erwartet. Der typische Engpass ist die Leistung von CPU.
* Der Aufbau des Angebotskatalogs hat einen großen Einfluss auf die Performance von Adobe Campaign Classic.
* Wenn es viele Angebote gibt, teilen Sie diese in mehrere Angebotskataloge auf.

### Eignungsregeln {#eligibility-rules}

Nachfolgend sind einige Best Practices zu den Eignungsregeln aufgeführt.

* Vereinfachung der Regeln. Die Komplexität von Regeln wirkt sich auf die Leistung aus, da sie die Suche erweitert. Eine komplexe Regel ist jede Regel mit mehr als fünf Bedingungen.
* Um die Performance zu verbessern, können Regeln in verschiedenen vordefinierten Filtern aufgelöst werden, die von mehreren Angebote gemeinsam verwendet werden.
* Platzieren Sie die restriktivsten Regeln für Angebotskategorien an der höchstmöglichen Position im Baum. Dadurch filtern sie zuerst die meisten Kontakte heraus, reduzieren die Anzahl der Zielkontakte und verhindern, dass sie von weiteren Regeln verarbeitet werden.
* Setzen Sie die teuersten Regeln in Bezug auf Zeit oder Verarbeitung am unteren Ende des Baums. Dadurch werden diese Regeln nur für die verbleibende Zielgruppe ausgeführt.
* Beginnen Sie bei einer bestimmten Kategorie, um zu vermeiden, dass der gesamte Baum durchsucht wird.
* Um Verarbeitungszeit zu sparen, berechnen Sie Aggregate vorab, anstatt komplexe Regeln mit Joins zu erstellen. Versuchen Sie dazu, Kundendaten in einer Referenztabelle zu speichern, die innerhalb der Eignungsregeln nachgeschlagen werden kann.
* Verwenden Sie eine minimale Anzahl von Gewichtungen, um die Anzahl der Abfragen zu begrenzen.
* Es wird empfohlen, eine begrenzte Anzahl von Angeboten pro Platzierung zu haben. Dadurch wird ein schnellerer Abruf von Angeboten in beliebiger Platzierung gewährleistet.
* Verwenden Sie Indizes, insbesondere für häufig verwendete Suchspalten.

### Vorschlagstabelle {#proposition-table}

Nachfolgend sind einige Best Practices bezüglich der Vorschlagstabelle aufgeführt.

* Verwenden Sie möglichst wenige Regeln, um die Verarbeitung so schnell wie möglich zu gestalten.
* Beschränken Sie die Anzahl der Datensätze in der Vorschlagstabelle: Bewahren Sie nur die Datensätze auf, die zum Tracken der Statusaktualisierung und für die Regeln erforderlich sind, und archivieren Sie sie dann in einem anderen System.
* Führen Sie eine intensive Datenbankwartung für die Vorschlagstabelle durch, wie z. B. eine Neuerstellung des Index oder der Tabelle.
* Anzahl der pro Zielgruppe abgefragten Vorschläge begrenzen Legen Sie nicht mehr fest, als Sie tatsächlich verwenden werden.
* Vermeiden Sie möglichst Joins in den Regelbedingungen.

## Tipps und Tricks zur Verwaltung von Angeboten {#tips-managing-offers}

Dieser Abschnitt enthält ausführlichere Ratschläge zur Verwaltung von Angeboten und zum Einsatz des Interaction-Moduls in Adobe Campaign Classic.

### Verwenden komplexer Platzierungen in einem E-Mail-Versand {#multiple-offer-spaces}

Wenn Angebote in Sendungen einbezogen werden, werden die Angebote in der Regel zuvor im Kampagnen-Workflow über eine Aktivität „Anreicherung“ (oder eine andere ähnliche Aktivität) ausgewählt.

Bei der Auswahl von Angeboten in einer Aktivität „Anreicherung“ können Sie festlegen, welche Platzierung verwendet werden soll. Das Menü zur Anpassung des Versands hängt jedoch unabhängig von der ausgewählten Platzierung von jener Platzierung ab, die im Versand eingerichtet wurde.

Im folgenden Beispiel lautet die im Versand ausgewählte Platzierung **[!UICONTROL E-Mail (Umgebung - Empfänger)]**:

![](assets/Interaction-best-practices-offer-space-selected.png)

Wenn für die Platzierung, die Sie im Versand auswählen, keine HTML-Rendering-Funktion eingerichtet ist, wird sie nicht im Versandmenü angezeigt und kann nicht ausgewählt werden. Auch das ist unabhängig von der Platzierung, die in der Aktivität „Anreicherung“ ausgewählt wurde.

Im folgenden Beispiel ist die HTML-Rendering-Funktion in der Dropdown-Liste verfügbar, da die im Versand ausgewählte Platzierung eine Rendering-Funktion hat:

![](assets/Interaction-best-practices-HTML-rendering.png)

Diese Funktion fügt Code wie folgt ein: `<%@ include proposition="targetData.proposition" view="rendering/html" %>`.

Wenn Sie den Vorschlag auswählen, lautet der Wert des Attributs **[!UICONTROL view]** wie folgt:
* &quot;rendering/html&quot;: html rendering. Die HTML-Rendering-Funktion wird verwendet.
* &quot;offer/view/html&quot;: html content. Die HTML-Rendering-Funktion wird nicht verwendet. Lediglich das HTML-Feld ist enthalten.

Wenn Sie komplexe Platzierungen in einem einzelnen E-Mail-Versand einschließen und einige von ihnen Rendering-Funktionen aufweisen und andere nicht, müssen Sie sich merken, welche Angebote welche Platzierungen verwenden und welche Platzierungen über Rendering-Funktionen verfügen.

Um Probleme zu vermeiden, wird daher empfohlen, für alle Platzierungen eine HTML-Rendering-Funktion zu definieren, auch wenn für Ihre Platzierung nur HTML-Inhalte erforderlich sind.

### Festlegen des Rangs in der Vorschlagstabelle {#rank-proposition-log-table}

Platzierungen können Daten in der Vorschlagstabelle speichern, wenn Vorschläge generiert oder akzeptiert werden:

![](assets/Interaction-best-practices-offer-space-storage.png)

Dies gilt jedoch nur für eingehende Interaktionen.

Zudem ist es möglich, zusätzliche Daten in der Vorschlagstabelle zu speichern, wenn ausgehende Interaktionen bzw. wenn ausgehende Angebote ohne das Interaction-Modul verwendet werden.

Jedes Feld aus der temporären Workflow-Tabelle, dessen Name mit einem Feldnamen in der Vorschlagstabelle übereinstimmt, wird in dasselbe Feld der Vorschlagstabelle kopiert.

Bei der manuellen Auswahl eines Angebots (ohne Interaction) in einer Anreicherung sind die Standardfelder beispielsweise wie folgt definiert:

![](assets/Interaction-best-practices-manual-offer-std-fields.png)

Zusätzliche Felder können hinzugefügt werden, z. B. ein „@rank“-Feld:

![](assets/Interaction-best-practices-manual-offer-add-fields.png)

Da sich in der Vorschlagstabelle ein Feld namens „@rank“ befindet, wird der Wert in der temporären Workflow-Tabelle kopiert.

Weitere Informationen zum Speichern zusätzlicher Felder in der Vorschlagstabelle finden Sie im Abschnitt [Integration über Workflows](../../interaction/using/integrating-an-offer-via-a-workflow.md#storing-offer-rankings-and-weights).

Bei ausgehenden Angeboten mit Interaction ist dies nützlich, wenn mehrere Angebote ausgewählt sind und Sie ermitteln möchten, in welcher Reihenfolge sie in einer E-Mail angezeigt werden sollen.

Sie können auch zusätzliche Metadaten direkt in der Vorschlagstabelle speichern, z. B. die aktuelle Ausgabenebene, um historische Aufzeichnungen über die Ausgaben zu speichern, die zum Zeitpunkt der Erstellung der Angebote vorgenommen wurden.

Bei Verwendung der ausgehenden Interaktion kann das Feld „@rank“ hinzugefügt werden (wie im Beispiel oben); dessen Wert wird jedoch auf Basis der von Interaction zurückgegebenen Reihenfolge automatisch festgelegt. Wenn Sie beispielsweise mit Interaction drei Angebote auswählen, werden im Feld „@rank“ die Werte 1, 2 und 3 zurückgegeben.

Bei Verwendung von Interaction und manueller Auswahl von Angeboten können beide Ansätze kombiniert werden. Beispielsweise kann der Benutzer das Feld „@rank“ für das manuell ausgewählte Angebot manuell auf „1“ setzen und einen Ausdruck wie „1 + @rank“ für die von Interaction zurückgegebenen Angebote verwenden. Wenn Interaction drei Angebote auswählt, werden die von beiden Ansätzen zurückgegebenen Angebote nach 1-4 bewertet:

![](assets/Interaction-best-practices-manual-offer-combined.png)

### Erweitern des nms:offer-Schemas {#extending-nms-offer-schema}

Achten Sie bei der Erweiterung :offer nms-Schemas darauf, dass Sie die bereits eingerichtete vordefinierte Struktur befolgen:
* Definieren Sie ein neues Feld für die Inhaltsspeicherung unter `<element name="view">`.
* Jedes neue Feld muss zweimal definiert werden: einmal als normales XML-Feld und einmal als CDATA-XML-Feld mit „_jst“ an den Namen angehängt. Beispiel:

  ```
  <element label="Price" name="price" type="long" xml="true"/>
  <element advanced="true" label="Script price" name="price_jst" type="CDATA" xml="true"/>
  ```

* Alle Felder, die zu verfolgende URLs enthalten, müssen unter `<element name="trackedUrls">` platziert werden (zu finden unter `<element name="view" >`).

---
product: campaign
title: Best Practices für Datenmodelle
description: Erfahren Sie, wie Sie mit dem Campaign Classic-Datenmodell arbeiten.
feature: Data Model
exl-id: 9c59b89c-3542-4a17-a46f-3a1e58de0748
source-git-commit: 65e80f16a6beaee89b51636017c42766589e179e
workflow-type: tm+mt
source-wordcount: '4005'
ht-degree: 55%

---

# Best Practices für Datenmodelle{#data-model-best-practices}

![](../../assets/v7-only.svg)

In diesem Dokument werden die wichtigsten Empfehlungen beim Entwerfen Ihres Adobe Campaign-Datenmodells erläutert.

Die in Campaign integrierten Tabellen und deren Interaktion werden im Abschnitt [diesem Abschnitt](../../configuration/using/about-data-model.md) Abschnitt.

Lesen [diese Dokumentation](../../configuration/using/about-schema-reference.md) , um mit Campaign-Schemata zu beginnen. Erfahren Sie, wie Sie Erweiterungsschemata konfigurieren, um das konzeptionelle Datenmodell der Adobe Campaign-Datenbank in [dieses Dokuments](../../configuration/using/about-schema-edition.md).

## Überblick {#overview}

Das Adobe Campaign-System ist äußerst flexibel und kann über die ursprüngliche Implementierung hinaus erweitert werden. Obwohl die Möglichkeiten unbegrenzt sind, ist es wichtig, die richtigen Entscheidungen zu treffen und eine solide Grundlage zu schaffen, um mit der Entwicklung Ihres Datenmodells zu beginnen.

Dieses Dokument enthält gängige Anwendungsfälle und Best Practices, mit denen Sie erfahren, wie Sie Ihr Adobe Campaign-Tool ordnungsgemäß erstellen.

## Architektur von Datenmodellen {#data-model-architecture}

Adobe Campaign ist ein leistungsstarkes kanalübergreifendes System zur Kampagnenverwaltung, das es Ihnen ermöglicht, Online- und Offline-Strategien zu kombinieren, um personalisierte Kundenerlebnisse bereitzustellen.

### Kundenorientierter Ansatz {#customer-centric-approach}

Während die meisten E-Mail-Dienstleister für die Kundenkommunikation einen listenorientierten Ansatz verfolgen, setzt Adobe Campaign eine relationale Datenbank ein, um eine breitere Sicht auf die Kunden und ihre Eigenschaften zu nutzen.

Dieser kundenorientierte Ansatz wird in der Grafik unten dargestellt. Die **Empfänger** Die graue Tabelle stellt die Hauptkundentabelle dar, um die herum alles erstellt wird:

![](assets/customer-centric-data-model.png)

Um Beschreibungen der einzelnen Tabellen aufzurufen, navigieren Sie zu **[!UICONTROL &quot;Admin&quot; > &quot;Konfiguration&quot; > &quot;Datenschemata&quot;]**, wählen Sie eine Ressource aus der Liste und klicken Sie auf die Registerkarte **[!UICONTROL Dokumentation]**.

Das Adobe Campaign-Standarddatenmodell wird im Abschnitt [dieses Dokuments](../../configuration/using/data-model-description.md).

>[!NOTE]
>
>Mit Adobe Campaign Classic können Sie eine benutzerdefinierte Kundentabelle erstellen. In den meisten Fällen wird jedoch empfohlen, den Standard [Empfängertabelle](../../configuration/using/about-data-model.md#default-recipient-table) die bereits über vordefinierte zusätzliche Tabellen und Funktionen verfügt.

### Daten für Adobe Campaign {#data-for-campaign}

Welche Daten sollten an Adobe Campaign gesendet werden? Es ist äußerst wichtig festzustellen, welche Daten Sie für Ihre Marketingaktivitäten benötigen.

>[!NOTE]
>
>Adobe Campaign ist weder ein Data Warehouse noch ein Reporting-Tool. Versuchen Sie also nicht, alle möglichen Kunden und zugehörige Daten in Adobe Campaign zu importieren bzw. Daten zu importieren, die nur dem Erstellen von Berichten dienen werden.

Um zu entscheiden, ob ein Attribut in Adobe Campaign erforderlich ist, fragen Sie sich, ob es in eine der folgenden Kategorien passt:

* Für die **Segmentierung** verwendetes Attribut
* Für **Datenverwaltungsprozesse** verwendetes Attribut (z. B. Aggregatberechnung)
* Für die **Personalisierung** verwendetes Attribut

Wenn ein Attribut nicht in eine dieser Kategorien fällt, benötigen Sie es wahrscheinlich nicht in Adobe Campaign.

### Auswahl von Datentypen {#data-types}

Um eine gute Architektur und Systemleistung sicherzustellen, befolgen Sie die folgenden Best Practices, wenn Sie Daten in Adobe Campaign einrichten.

* Eine große Tabelle sollte überwiegend numerische Felder aufweisen und Relationen zu Referenztabellen enthalten (bei Einsatz von Wertelisten).
* Mit dem Attribut **expr** können Sie ein Schema-Attribut in einer Tabelle als berechnetes Feld definieren (anstelle eines physischen definierten Werts). Dies ermöglicht den Zugriff auf Informationen in einem anderen Format (z. B. Alter und Geburtsdatum), ohne beide Werte speichern zu müssen. So lässt sich verhindern, dass Felder dupliziert werden. Die Empfängertabelle nutzt beispielsweise einen Ausdruck für die Domain, der bereits im E-Mail-Feld vorhanden ist.
* Wenn die Berechnung des Ausdrucks jedoch komplex ist, wird eine Verwendung des Attributs **expr** nicht empfohlen, da eine Ad-hoc-Berechnung Auswirkungen auf die Leistung Ihrer Abfragen haben kann.
* Der Typ **XML** hilft dabei, eine Erstellung von zu vielen Feldern zu verhindern. Er benötigt jedoch Speicherplatz, da er eine CLOB-Spalte in der Datenbank verwendet. Außerdem können komplexe SQL-Abfragen entstehen, die die Leistung beeinträchtigen.
* Die Länge eines **Zeichenfolgenfelds** sollte immer mit der Spalte definiert werden. Standardmäßig beträgt die maximale Länge in Adobe Campaign 255 Zeichen. Adobe empfiehlt jedoch, das Feld zu kürzen, wenn Sie bereits wissen, dass auch weniger ausreicht.
* Es ist akzeptabel, dass ein Feld in Adobe Campaign kürzer ist als im Quellsystem, wenn Sie sicher sind, dass die Länge im Quellsystem zu groß ist und nicht benötigt wird. Dies könnte eine kürzere Zeichenfolge oder kleinere Ganzzahl in Adobe Campaign bedeuten.

### Auswahl von Feldern {#choice-of-fields}

Felder müssen in einer Tabelle gespeichert werden, wenn sie Zielgruppenbestimmungs- oder Personalisierungszwecken dienen. Wenn also ein Feld nicht zum Senden einer personalisierten E-Mail verwendet oder als Kriterium in einer Abfrage verwendet wird, belegt es Speicherplatz, während es nutzlos ist.

Bei hybriden und On-Premise-Instanzen deckt FDA (Federated Data Access, eine optionale Funktion, die den Zugriff auf externe Daten ermöglicht) die Notwendigkeit ab, während eines Kampagnenprozesses ein Feld &quot;spontan&quot;hinzuzufügen. Sie müssen nicht alles importieren, wenn Sie über FDA verfügen. Weitere Informationen hierzu finden Sie unter [Über Federated Data Access](../../installation/using/about-fda.md).

### Auswahl von Schlüsseln {#choice-of-keys}

Zusätzlich zu den **autopk** Standardmäßig in den meisten Tabellen definiert, sollten Sie erwägen, einige logische oder geschäftliche Schlüssel hinzuzufügen (Kontonummer, Kundennummer usw.). Diese können später für Importe, Abstimmungen oder Daten-Packages verwendet werden. Weitere Informationen hierzu finden Sie unter [Kennungen](#identifiers).

Effiziente Schlüssel sind unverzichtbar für hohe Leistung. Numerische Datentypen sollten als Schlüssel für Tabellen stets bevorzugt werden.

Für SQLServer-Datenbanken können Sie die Verwendung von &quot;geclustertem Index&quot;in Erwägung ziehen, wenn eine Leistung erforderlich ist. Da Adobe dies nicht handhabt, müssen Sie es in SQL erstellen.

### Dedizierte Tablespaces {#dedicated-tablespaces}

Mit dem Tablespace-Attribut im Schema können Sie einen dedizierten Tablespace für eine Tabelle angeben.

Mit dem Installationsassistenten können Sie Objekte nach Typ (Daten, temporär und Index) speichern.

Dedizierte Tablespaces eignen sich besser für Partitionierung, Sicherheitsregeln und ermöglichen eine reibungslose und flexible Verwaltung, bessere Optimierung und Leistung.

## Kennungen {#identifiers}

Adobe Campaign-Ressourcen verfügen über drei Kennungen (IDs). Sie können auch eine zusätzliche Kennung hinzuzufügen.

Die folgende Tabelle beschreibt diese Kennungen und ihren Zweck.

| Kennung | Beschreibung | Best Practices |
|--- |--- |--- |
| ID | <ul><li>Die ID ist der physische Primärschlüssel einer Adobe Campaign-Tabelle. Bei nativen Tabellen handelt es sich um eine generierte 32-Bit-Zahl aus einer Sequenz</li><li>Diese Kennung ist in der Regel für eine bestimmte Adobe Campaign-Instanz eindeutig. </li><li>Eine automatisch generierte ID kann in einer Schemadefinition sichtbar sein. Suchen Sie die *autopk=&quot;true&quot;* -Attribut.</li></ul> | <ul><li>Automatisch erstellte Kennungen sollten nicht als Referenz in einem Workflow oder in einer Package-Definition verwendet werden.</li><li>Es sollte nicht angenommen werden, dass die ID immer eine steigende Zahl sein wird.</li><li>Die ID in einer nativen Tabelle ist eine 32-Bit-Zahl und dieser Typ sollte nicht geändert werden. Diese Zahl stammt aus einer &quot;Sequenz&quot;, die im Abschnitt mit demselben Namen behandelt wird.</li></ul> |
| Name (oder interner Name) | <ul><li>Diese Information ist eine eindeutige Kennung eines Datensatzes in einer Tabelle. Der Wert kann manuell aktualisiert werden, üblicherweise mit einem erstellten Namen.</li><li>Die Kennung behält ihren Wert bei, wenn sie in einer anderen Instanz von Adobe Campaign bereitgestellt wird, und darf nicht leer sein.</li></ul> | <ul><li>Benennen Sie den von Adobe Campaign generierten Datensatznamen um, wenn das Objekt von einer Umgebung in eine andere bereitgestellt werden soll.</li><li>Wenn ein Objekt beispielsweise über ein Namespace-Attribut verfügt (zum Beispiel *schema*), wird dieser gemeinsame Namespace für alle erstellten benutzerdefinierten Objekte genutzt. Einige reservierte Namespaces sollten nicht verwendet werden: *nms*, *xtk*, *nl*, *ncl*, *crm*, *xxl*.</li><li>Wenn ein Objekt keinen Namespace aufweist (zum Beispiel *workflow* oder *delivery*), wird dieser Namespace-Begriff als Präfix eines internen Namensobjekts hinzugefügt: *namespaceMyObjectName*.</li><li>Verwenden Sie keine Sonderzeichen wie Leerzeichen &quot;&quot;, Semikolon &quot;:&quot; oder Bindestrich &quot;-&quot;. Alle diese Zeichen würden durch einen Unterstrich (_) ersetzt werden. Beispielsweise würden &quot;abc-def&quot; und &quot;abc:def&quot; als &quot;abc_def&quot; gespeichert werden und sich gegenseitig überschreiben.</li></ul> |
| Titel | <ul><li>Der Titel ist die Unternehmenskennung eines Objekts oder Datensatzes in Adobe Campaign.</li><li>Dieses Objekt erlaubt Leerzeichen und Sonderzeichen.</li><li>Der Titel garantiert nicht die Einzigartigkeit eines Datensatzes.</li></ul> | <ul><li>Es wird empfohlen, eine Struktur für die Objekttitel festzulegen.</li><li>Dies ist die benutzerfreundlichste Lösung, um einen Datensatz oder ein Objekt für einen Adobe Campaign-Benutzer zu identifizieren.</li></ul> |

## Benutzerdefinierte interne Schlüssel {#custom-internal-keys}

Für jede in Adobe Campaign erstellte Tabelle sind Primärschlüssel erforderlich.

Die meisten Unternehmen importieren Datensätze aus externen Systemen. Während der physische Schlüssel der Empfängertabelle das &quot;id&quot;-Attribut ist, kann zusätzlich ein benutzerdefinierter Schlüssel festgelegt werden.

Dieser benutzerdefinierte Schlüssel ist der eigentliche Hauptschlüssel des Datensatzes im externen System, das Daten für Adobe Campaign bereitstellt.

Wenn eine vordefinierte Tabelle sowohl über ein autopk als auch über einen internen Schlüssel verfügt, wird der interne Schlüssel als eindeutiger Index in der physischen Datenbanktabelle festgelegt.

Beim Erstellen einer benutzerdefinierten Tabelle stehen Ihnen zwei Optionen zur Verfügung:
* Kombination aus einem automatisch erstellten Schlüssel (ID) und einem internen Schlüssel (benutzerdefiniert). Diese Option ist interessant, wenn Ihr Systemschlüssel ein zusammengesetzter Schlüssel oder keine Ganzzahl ist. Ganzzahlen bieten höhere Leistungen in umfangreichen Tabellen und in Verbindung mit anderen Tabellen.
* Verwendung des Primärschlüssels als Primärschlüssel des externen Systems. Diese Lösung wird in der Regel bevorzugt, da sie das Importieren und Exportieren von Daten durch einen einheitlichen Schlüssel zwischen verschiedenen Systemen vereinfacht. Autopk sollte deaktiviert werden, wenn der Schlüssel &quot;id&quot;heißt und mit externen Werten gefüllt werden soll (nicht automatisch generiert).

>[!IMPORTANT]
>
>Ein Autopk sollte nicht als Referenz in Workflows verwendet werden.

## Sequenzen {#sequences}

Der Primärschlüssel von Adobe Campaign ist eine automatisch generierte ID für alle nativen Tabellen und kann für benutzerdefinierte Tabellen identisch sein. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](#identifiers).

Dieser Wert stammt aus dem so genannten **Sequenz**: ein Datenbankobjekt, mit dem eine Zahlensequenz generiert wird.

Es gibt zwei Arten von Sequenzen:
* **Freigegeben**: mehr als eine Tabelle würde ihre ID aus derselben Sequenz auswählen. Das bedeutet, dass keine andere Tabelle, die dieselbe Sequenz hat, einen Datensatz mit der ID &#39;X&#39; hätte, wenn eine ID &#39;X&#39; von einer Tabelle verwendet wird. **XtkNewId** ist die standardmäßige freigegebene Sequenz, die in Adobe Campaign verfügbar ist.
* **Dediziert**: nur eine Tabelle wählt ihre IDs aus der Sequenz aus. Der Sequenzname würde normalerweise den Tabellennamen enthalten.

>[!IMPORTANT]
>
>Die Sequenz ist ein ganzzahliger 32-Bit-Wert mit einer endlichen maximalen Anzahl verfügbarer Werte: 2,14 Mrd. Nach Erreichen des maximalen Werts wird die Sequenz wieder auf 0 zurückgesetzt, um IDs wiederzuverwenden.
>
>Wenn die alten Daten nicht bereinigt wurden, stellt das Ergebnis eine Verletzung des eindeutigen Schlüssels dar, die zu einem Blocker für den Zustand und die Nutzung der Plattform wird. Adobe Campaign wäre nicht in der Lage, Nachrichten zu versenden (wenn es sich auf die Versandlog-Tabelle auswirkt) und die Leistung wäre stark beeinträchtigt.

Deshalb würde einem Kunden, der jährlich 6 Milliarden E-Mails mit einer Aufbewahrungsfrist von 180 Tagen für seine Protokolle sendet, innerhalb von 4 Monaten die IDs ausgehen. Um eine solche Herausforderung zu vermeiden, stellen Sie sicher, dass Sie Bereinigungsparameter entsprechend Ihren Volumina haben. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](#data-retention).

Wenn in Adobe Campaign eine benutzerdefinierte Tabelle mit einem Primärschlüssel als autoPK erstellt wird, sollte dieser Tabelle systematisch eine benutzerdefinierte dedizierte Sequenz zugeordnet werden.

Standardmäßig hat eine benutzerdefinierte Sequenz Werte zwischen +1.000 und +2,1 BB. Technisch gesehen ist es möglich, einen vollständigen Bereich von 4BB zu erhalten, indem negative IDs aktiviert werden. Dies sollte mit Vorsicht verwendet werden und eine ID geht beim Übergang von negativen zu positiven Werten verloren: Der Datensatz 0 wird normalerweise von Adobe Campaign in generierten SQL-Abfragen ignoriert.

Weitere Informationen zur Erschöpfung von Sequenzen finden Sie unter [dieses Video](https://helpx.adobe.com/customer-care-office-hours/campaign/sequences-exhaustion-campaign-classic.html).

## Indizes {#indexes}

Indizes sind für die Leistung unverzichtbar. Wenn Sie einen Schlüssel im Schema deklarieren, erstellt Adobe automatisch einen Index für die Schlüsselfelder. Sie können auch weitere Indizes für Abfragen deklarieren, die den Schlüssel nicht verwenden.

Adobe empfiehlt, zusätzliche Indizes zu definieren, da dies die Leistung verbessern kann.

Beachten Sie jedoch Folgendes:

* Die Indexnutzung ist an Ihr Zugriffsmuster gebunden. Die Optimierung der Indizierung ist häufig ein wichtiger Bestandteil des Datenbankdesigns und muss von Experten durchgeführt werden. Das Hinzufügen von Indizes ist häufig ein iterativer Workflow, der mit der Datenbankwartung verbunden ist. Es wird Schritt für Schritt durchgeführt, um Leistungsprobleme zu beheben, wenn dies geschieht.
* Indizes erhöhen die Gesamtgröße der Tabelle (um den Index selbst zu speichern).
* Das Hinzufügen von Index zu Spalten kann die Leistung des Datenlesehilfen (SELECT) verbessern, kann aber die Leistung des Datenschreibzugriffs (UPDATE) verringern.
* Da sich dies auf die Leistung beim Einfügen von Daten auswirkt, sollten Indizes in Größe und Anzahl begrenzt sein.
* Fügen Sie bei Bedarf keine Indizes hinzu. Stellen Sie sicher, dass sie erforderlich ist und die Gesamtleistung Ihrer Abfragen erhöht (Test und Lernen).
* Im Allgemeinen ist ein Index effizient, wenn Sie wissen, dass Ihre Abfragen nicht mehr als 10 % der Datensätze zurückbringen.
* Wählen Sie die zu definierenden Indizes sorgfältig aus.
* Entfernen Sie keine nativen Indizes aus nativen Tabellen.

<!--When you are performing an initial import with very high volumes of data insert in Adobe Campaign database, it is recommended to run that import without custom indexes at first. It will allow to accelerate the insertion process. Once you’ve completed this important import, it is possible to enable the index(es).-->

### Beispiel

Die Verwaltung von Indizes kann sehr komplex werden. Daher ist es wichtig zu verstehen, wie sie funktionieren. Um diese Komplexität zu veranschaulichen, nehmen wir ein grundlegendes Beispiel, wie die Suche nach Empfängern durch Filterung des Vor- und Nachnamens. Gehen Sie dazu wie folgt vor:
1. Gehen Sie in den Ordner, in dem alle Empfänger der Datenbank aufgeführt sind. Weitere Informationen hierzu finden Sie unter [Profile verwalten](../../platform/using/managing-profiles.md).
1. Klicken Sie mit der rechten Maustaste auf die **[!UICONTROL Vorname]** -Feld.
1. Auswählen **[!UICONTROL Nach diesem Feld filtern]**.

   ![](assets/data-model-index-example.png)

1. Wiederholen Sie diesen Vorgang für die **[!UICONTROL Nachname]** -Feld.

Die beiden entsprechenden Filter werden am oberen Bildschirmrand hinzugefügt.

![](assets/data-model-index-search.png)

Sie können jetzt Suchfilter für die **[!UICONTROL Vorname]** und **[!UICONTROL Nachname]** -Felder entsprechend den unterschiedlichen Filterbedingungen.

Um die Suche nach diesen Filtern zu beschleunigen, können Sie jetzt Indizes hinzufügen. Welche Indizes sollten jedoch verwendet werden?

>[!NOTE]
>
>Dieses Beispiel gilt für gehostete Kunden, die eine PostgreSQL-Datenbank verwenden.

Die folgende Tabelle zeigt, in welchen Fällen die drei unten beschriebenen Indizes verwendet werden oder nicht dem in der ersten Spalte angezeigten Zugriffsmuster entsprechen.

| Suchkriterien | Index 1 (Vorname + Nachname) | Index 2 (nur Vorname) | Index 3 (nur Nachname) | Erklärung |
|--- |--- |--- |--- |--- |
| Vorname gleich &quot;Johnny&quot; | In Gebrauch | In Gebrauch | Nicht verwendet | Da der Vorname an erster Stelle auf Index 1 steht, wird er trotzdem verwendet: Es ist nicht erforderlich, eine Bedingung für den Nachnamen hinzuzufügen. |
| Vorname gleich &quot;Johnny&quot;UND Nachname gleich &quot;Smith&quot; | In Gebrauch | Nicht verwendet | Nicht verwendet | Da beide Attribute in derselben Abfrage gesucht werden, wird nur der Index verwendet, der beide Attribute kombiniert. |
| Nachname gleich &quot;Smith&quot; | Nicht verwendet | Nicht verwendet | In Gebrauch | Die Reihenfolge der Attribute im Index wird berücksichtigt. Wenn Sie diese Reihenfolge nicht einhalten, kann der Index nicht verwendet werden. |
| Vorname beginnt mit &quot;Joh&quot; | In Gebrauch | In Gebrauch | Nicht verwendet | &quot;Linke Suche&quot;aktiviert Indizes. |
| Vorname endet mit &quot;nny&quot; | Nicht verwendet | Nicht verwendet | Nicht verwendet | &quot;Richtige Suche&quot;deaktiviert Indizes und eine vollständige Überprüfung wird durchgeführt. Einige bestimmte Indextypen können diesen Anwendungsfall handhaben, sind jedoch standardmäßig nicht in Adobe Campaign verfügbar. |
| Vorname enthält &quot;John&quot; | Nicht verwendet | Nicht verwendet | Nicht verwendet | Dies ist eine Kombination aus &quot;links&quot;und &quot;rechten&quot;Suchen. Aufgrund letzterer werden Indizes deaktiviert und eine vollständige Überprüfung durchgeführt. |
| Vorname gleich &quot;john&quot; | Nicht verwendet | Nicht verwendet | Nicht verwendet | Bei Indizes wird zwischen Groß- und Kleinschreibung unterschieden. Damit nicht zwischen Groß- und Kleinschreibung unterschieden wird, sollten Sie einen bestimmten Index erstellen, der eine SQL-Funktion wie &quot;upper(firstname)&quot;enthält. Dasselbe gilt für andere Datenumwandlungen wie &quot;unaccent(firstname)&quot;. |

## Relationen und Kardinalität {#links-and-cardinality}

### Relationen {#links}

Achten Sie bei großen Tabellen auf die &quot;eigene&quot; Integrität. Das Löschen von Datensätzen mit großen Tabellen in der Integrität &quot;own&quot;kann die Instanz stoppen. Die Tabelle wird gesperrt; die Löschungen werden einzeln vorgenommen. Daher ist es am besten, bei untergeordneten Tabellen mit großen Volumen &quot;neutrale&quot; Integrität anzuwenden.

Das Deklarieren einer Relation als externer Join ist nicht gut für die Leistung. Der Null-ID-Datensatz emuliert die externe Join-Funktion. Es ist nicht erforderlich, externe Joins zu deklarieren, wenn der Link die automatische Verknüpfung verwendet.

Obwohl es möglich ist, eine beliebige Tabelle in einem Workflow einzubinden, empfiehlt Adobe, allgemeine Relationen zwischen Ressourcen direkt in der Definition der Datenstruktur festzulegen.

Die Relation sollte entsprechend den tatsächlichen Daten in den Tabellen definiert werden. Eine falsche Definition könnte sich auf Daten auswirken, die über Relationen abgerufen wurden, z. B. durch unerwartetes Duplizieren von Datensätzen.

Benennen Sie die Relation konsequent nach der Tabelle: Der Name der Relation sollte Aufschluss über die ferne Tabelle geben.

Benennen Sie eine Relation nicht mit &quot;id&quot; als Suffix. Benennen Sie sie beispielsweise &quot;transaction&quot; anstelle von &quot;transactionId&quot;.

Standardmäßig erstellt Adobe Campaign eine Relation mit dem Primärschlüssel der externen Tabelle. Aus Gründen der Klarheit ist es besser, den Join in der Relationsdefinition explizit zu definieren.

Den Attributen, die in einem Link verwendet werden, wird ein Index hinzugefügt.

Die Links created-by und last-modified-by sind in vielen Tabellen enthalten. Es ist möglich, den Index mithilfe des Attributs noDbIndex im Link zu deaktivieren, wenn diese Informationen nicht vom Unternehmen verwendet werden.

### Kardinalität {#cardinality}

Stellen Sie beim Entwerfen einer Relation sicher, dass der Zieldatensatz eindeutig ist, falls eine 1-1-Beziehung deklariert wurde. Andernfalls gibt der Join möglicherweise mehrere Datensätze zurück, wenn nur einer erwartet wird. Dies führt bei der Versandvorbereitung zu Fehlern, wenn &quot;die Abfrage mehr Zeilen zurückgibt als erwartet&quot;. Verwenden Sie als Namen für die Relation denselben Namen wie beim Zielschema.

Definieren Sie eine Relation mit einer Kardinalität (1-N) im Schema auf der Seite (1). So sollte beispielsweise die Relation &quot;Empfänger (1) - (N) Transaktion&quot; im Transaktionsschema definiert werden.

Beachten Sie, dass eine Umkehrkardinalität einer Relation standardmäßig (N) lautet. Sie können eine Relation (1-1) definieren, indem Sie das Attribut revCardinality=&#39;single&#39; zur Relationsdefinition hinzufügen.

Wenn die Umkehrrelation für den Anwender nicht sichtbar sein soll, können Sie sie mit der Relationsdefinition revLink=&#39;_NONE_&#39; ausblenden. Ein typischer Anwendungsfall hierfür wäre die Definition einer Relation vom Empfänger zur letzten ausgeführten Transaktion. Sie müssen lediglich die Relation vom Empfänger zur letzten Transaktion sehen. In der Transaktionstabelle muss keine Umkehrrelation sichtbar sein.

Relationen, die einen externen Join vornehmen (1-0..1), sollten mit Vorsicht verwendet werden, da sie die Systemleistung beeinträchtigen.

## Datenbeibehaltung - Bereinigung und Bereinigung {#data-retention}

Adobe Campaign ist weder ein Data Warehouse noch ein Reporting-Tool. Zur Sicherstellung hoher Leistung von Adobe Campaign sollte daher das Datenbankwachstum kontrolliert werden. Dazu kann hilfreich sein, einige der unten aufgeführten Best Practices zu befolgen.

Standardmäßig haben Versand- und Trackinglogs von Adobe Campaign eine Aufbewahrungsdauer von 180 Tagen. Ein Bereinigungsprozess wird ausgeführt, um alle Protokolle zu entfernen, die älter sind.

* Wenn Sie die Logs länger aufbewahren möchten, sollte diese Entscheidung in Abhängigkeit von der Größe der Datenbank und der Menge der gesendeten Nachrichten sorgfältig getroffen werden. Zur Erinnerung: Die Adobe Campaign-Sequenz ist eine 32-Bit-Ganzzahl.
* Es wird empfohlen, nicht mehr als eine Milliarde Datensätze gleichzeitig in diesen Tabellen zu haben (etwa 50 % der verfügbaren 2,14 Milliarden IDs), um das Risiko des Verbrauchs aller verfügbaren IDs zu begrenzen. Dies erfordert, dass einige Kunden die Aufbewahrungsdauer unter 180 Tage senken.

Erfahren Sie mehr über die Datenaufbewahrung in [Richtlinien zum Datenschutz und zur Sicherheit von Campaign](../../platform/using/privacy-and-recommendations.md).

Erfahren Sie mehr über den Workflow für die Datenbasisbereinigung in Campaign [in diesem Abschnitt](../../production/using/database-cleanup-workflow.md).

>[!IMPORTANT]
>
>Benutzerdefinierte Tabellen werden im standardmäßigen Bereinigungsprozess nicht bereinigt. Er mag zwar am ersten Tag noch nicht erforderlich sein, vergessen Sie aber nicht, einen Bereinigungsprozess für Ihre benutzerdefinierten Tabellen einzurichten, da sonst später Leistungsprobleme auftreten können.

Es gibt verschiedene Lösungen, um den Bedarf an Datensätzen in Adobe Campaign zu minimieren:
* Exportieren Sie die Daten in ein Data Warehouse außerhalb von Adobe Campaign.
* Generieren Sie aggregierte Werte, die weniger Platz einnehmen und dennoch für Ihre Marketing-Zwecke ausreichen. Sie benötigen beispielsweise nicht den vollständigen Verlauf von Kundentransaktionen in Adobe Campaign, um die letzten Käufe verfolgen zu können.

Sie können in einem Schema das Attribut &quot;deleteStatus&quot; deklarieren. Effizienter ist es, den Datensatz als gelöscht zu markieren und das Löschen in die Bereinigungsaufgabe zu verschieben.

## Leistung {#performance}

Befolgen Sie die nachstehenden Best Practices, um eine bessere Leistung sicherzustellen.

### Allgemeine Empfehlungen {#general-recommendations}

* Vermeiden Sie die Verwendung von Operationen wie &quot;CONTAINS&quot; in Abfragen. Wenn Sie wissen, wonach gefiltert werden soll, wenden Sie dieselbe Bedingung mit &quot;EQUAL TO&quot; oder anderen spezifischen Filteroperatoren an.
* Vermeiden Sie die Verknüpfung mit nicht indizierten Feldern beim Aufbau von Daten in Workflows.
* Vergewissern Sie sich, dass Prozesse wie Import und Export außerhalb der Geschäftszeiten ausgeführt werden.
* Stellen Sie sicher, dass ein Zeitplan für alle täglichen Aktivitäten vorhanden ist und halten Sie sich an ihn.
* Wenn einer oder mehrere der täglichen Prozesse fehlschlagen und sie am selben Tag noch ausgeführt werden müssen, stellen Sie sicher, dass beim Starten des manuellen Prozesses keine Konflikte auftreten, da dies die Systemleistung beeinträchtigen könnte.
* Stellen Sie sicher, dass keine der täglichen Kampagnen während des Importvorgangs oder bei der Ausführung eines manuellen Prozesses ausgeführt wird.
* Verwenden Sie eine oder mehrere Referenztabellen, anstatt ein Feld in jeder Zeile zu duplizieren. Bei Verwendung von Schlüssel/Wert-Paaren ist es empfehlenswert, einen numerischen Schlüssel zu wählen.
* Eine kurze Zeichenfolge ist weiterhin zulässig. Falls Referenztabellen bereits in einem externen System vorhanden sind, erleichtert die Wiederverwendung derselben die Datenintegration mit Adobe Campaign.

### 1-zu-n-Beziehungen {#one-to-many-relationships}

* Das Datendesign beeinflusst Benutzerfreundlichkeit und Funktionalität. Wenn Sie Ihr Datenmodell mit zahlreichen 1-zu-n-Beziehungen entwickeln, wird es für Benutzer schwieriger, in der Anwendung eine sinnvolle Logik zu erstellen. Für technisch nicht versierte Marketing-Experten kann es schwierig sein, eine 1-zu-n-Filterlogik zu entwerfen und zu verstehen.
* Es wird empfohlen, alle wichtigen Felder in einer Tabelle zu vereinen, da Benutzer so leichter Abfragen erstellen können. Unter Umständen kann die Leistung auch verbessert werden, wenn einige Felder in mehreren Tabellen dupliziert werden, wenn dadurch ein Join vermieden werden kann.
* Bestimmte integrierte Funktionen können nicht auf 1-zu-n Beziehungen verweisen, z. B. die Angebotsgewichtungsformel und Sendungen.

## Große Tabellen {#large-tables}

Adobe Campaign setzt auf Datenbank-Engines von Drittanbietern. Je nach Anbieter ist für die Leistungsoptimierung bei größeren Tabellen möglicherweise ein bestimmtes Design erforderlich.

Im Folgenden finden Sie einige verbreitete Best Practices, die beim Entwerfen Ihres Datenmodells mit großen Tabellen und komplexen Joins befolgt werden sollten.

* Wenn Sie zusätzliche benutzerdefinierte Empfängertabellen verwenden, stellen Sie sicher, dass Sie für jedes Versand-Mapping über eine dedizierte Protokolltabelle verfügen.
* Reduzieren Sie die Anzahl der Spalten, indem Sie beispielsweise die nicht verwendeten Spalten ermitteln.
* Optimieren Sie die Datenmodellrelationen, indem Sie komplexe Joins vermeiden, wie z. B. Joins mit mehreren Bedingungen und/oder mit mehreren Spalten.
* Verwenden Sie für Join-Schlüssel immer numerische Daten anstelle von Zeichenfolgen.
* Reduzieren Sie die Tiefe der Protokollaufbewahrung so weit wie möglich. Wenn Sie einen tieferen Verlauf benötigen, können Sie Berechnungen aggregieren und/oder benutzerdefinierte Protokolltabellen bearbeiten, um einen größeren Verlauf zu speichern.

### Größe von Tabellen {#size-of-tables}

Die Tabellengröße ist eine Kombination aus der Anzahl der Datensätze und der Anzahl der Spalten pro Datensatz. Beide können sich auf die Leistung von Abfragen auswirken.

* Eine **kleine** Tabelle entspricht der Größe der Versandtabelle.
* Eine **mittelgroße** Tabelle entspricht der Größe der Empfängertabelle. Sie weist einen Datensatz pro Kunde auf.
* Eine **große** Tabelle entspricht der Größe der Tabelle &quot;Umfassendes Protokoll&quot;. Sie enthält mehrere Datensätze pro Kunde.
Wenn Ihre Datenbank z. B. 10 Millionen Empfänger umfasst, enthält die Tabelle &quot;Umfassendes Protokoll&quot; etwa 100 bis 200 Millionen Nachrichten und die Tabelle &quot;Versand&quot; einige Tausend Datensätze.

Auf PostgreSQL sollte eine Zeile nicht größer als 8 KB sein, um dies zu vermeiden [TOAST](https://wiki.postgresql.org/wiki/TOAST) Mechanismus. Versuchen Sie daher, die Anzahl der Spalten und die Größe jeder Zeile so weit wie möglich zu reduzieren, um eine optimale Systemleistung (Speicher und CPU) zu gewährleisten.

Die Anzahl der Zeilen wirkt sich ebenfalls auf die Leistung aus. Die Adobe Campaign-Datenbank dient nicht zum Speichern von Verlaufsdaten, die nicht aktiv für Zielgruppenbestimmungs- oder Personalisierungszwecke verwendet werden. Es handelt sich dabei um eine operative Datenbank.

Um Leistungsprobleme im Zusammenhang mit der hohen Zeilenanzahl zu verhindern, sollten Sie nur die erforderlichen Datensätze in der Datenbank speichern. Alle anderen Datensätze sollten Sie in das Data Warehouse eines Drittanbieters exportieren und aus der Adobe Campaign-Betriebsdatenbank entfernen.

Im Folgenden finden Sie Best Practices zur Größe von Tabellen:

* Planen Sie große Tabellen mit weniger Feldern und mehr numerischen Daten.
* Verwenden Sie nicht den umfangreichen Spaltentyp (z. B.: Int64), um kleine Zahlen wie boolesche Werte zu speichern.
* Entfernen Sie nicht verwendete Spalten aus der Tabellendefinition.
* Behalten Sie keine alten oder inaktiven Daten in Ihrer Adobe Campaign-Datenbank bei (Export und Bereinigung).

Hier ein Beispiel:

![](assets/transaction-table-example.png)

In diesem Beispiel:
* Die *Transaktion* und *Transaktionselement* -Tabellen sind groß: mehr als 10 Millionen.
* Die *Produkt* und *Store* -Tabellen sind kleiner: weniger als 10.000.
* Das Produktetikett und die Referenz wurden im *Produkt* Tabelle.
* Die *Transaktionselement* -Tabelle enthält nur einen Link zum *Produkt* -Tabelle, die numerisch ist.

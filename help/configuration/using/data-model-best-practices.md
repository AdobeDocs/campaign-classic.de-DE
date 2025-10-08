---
product: campaign
title: Best Practices für Datenmodelle
description: Erfahren Sie, wie Sie mit dem Campaign Classic-Datenmodell arbeiten
feature: Data Model
exl-id: 9c59b89c-3542-4a17-a46f-3a1e58de0748
source-git-commit: 4d8c4ba846148d3df00a76ecc29375b9047c2b20
workflow-type: tm+mt
source-wordcount: '4022'
ht-degree: 55%

---

# Best Practices für Datenmodelle{#data-model-best-practices}

In diesem Dokument werden die wichtigsten Empfehlungen beim Entwerfen Ihres Adobe Campaign-Datenmodells erläutert.

Genauere Informationen zu den integrierten Campaign-Tabellen und ihrer Interaktion finden Sie in [diesem Abschnitt](../../configuration/using/about-data-model.md).

Lesen Sie [diese Dokumentation](../../configuration/using/about-schema-reference.md) um mit Campaign-Schemata zu beginnen. Erfahren Sie in diesem Dokument, wie Sie Erweiterungsschemata konfigurieren können, um das konzeptionelle Datenmodell der Adobe Campaign[Datenbank zu &#x200B;](../../configuration/using/about-schema-edition.md).

## Überblick {#overview}

Das Adobe Campaign-System ist äußerst flexibel und kann über die ursprüngliche Implementierung hinaus erweitert werden. Obwohl die Möglichkeiten unbegrenzt sind, ist es wichtig, die richtigen Entscheidungen zu treffen und eine solide Grundlage zu schaffen, um mit der Entwicklung Ihres Datenmodells zu beginnen.

Dieses Dokument enthält gängige Anwendungsfälle und Best Practices, mit denen Sie Ihr Adobe Campaign-Tool ordnungsgemäß entwickeln können.

## Architektur von Datenmodellen {#data-model-architecture}

Adobe Campaign ist ein leistungsstarkes kanalübergreifendes System zur Kampagnenverwaltung, das es Ihnen ermöglicht, Online- und Offline-Strategien zu kombinieren, um personalisierte Kundenerlebnisse bereitzustellen.

### Kundenorientierter Ansatz {#customer-centric-approach}

Während die meisten E-Mail-Dienstleister für die Kundenkommunikation einen listenorientierten Ansatz verfolgen, setzt Adobe Campaign eine relationale Datenbank ein, um eine breitere Sicht auf die Kunden und ihre Eigenschaften zu nutzen.

Dieser kundenorientierte Ansatz wird in der Grafik unten dargestellt. Die **Empfänger**-Tabelle in Grau stellt die wichtigste Kundentabelle dar, um die herum alles erstellt wird:

![](assets/customer-centric-data-model.png)

Um Beschreibungen der einzelnen Tabellen aufzurufen, navigieren Sie zu **[!UICONTROL &quot;Admin&quot; > &quot;Konfiguration&quot; > &quot;Datenschemata&quot;]**, wählen Sie eine Ressource aus der Liste und klicken Sie auf die Registerkarte **[!UICONTROL Dokumentation]**.

Das standardmäßige Adobe Campaign-Datenmodell wird in [diesem Dokument) &#x200B;](../../configuration/using/data-model-description.md).

>[!NOTE]
>
>Mit Adobe Campaign Classic können Sie eine benutzerdefinierte Kundentabelle erstellen. In den meisten Fällen wird jedoch empfohlen, die standardmäßige [Empfängertabelle) zu nutzen](../../configuration/using/about-data-model.md#default-recipient-table) die bereits über zusätzliche vordefinierte Tabellen und Funktionen verfügt.

### Daten für Adobe Campaign {#data-for-campaign}

Welche Daten sollten an Adobe Campaign gesendet werden? Es ist äußerst wichtig festzustellen, welche Daten Sie für Ihre Marketing-Aktivitäten benötigen.

>[!NOTE]
>
>Adobe Campaign ist weder ein Data Warehouse noch ein Reporting-Tool. Versuchen Sie also nicht, alle möglichen Kunden und zugehörige Daten in Adobe Campaign zu importieren bzw. Daten zu importieren, die nur dem Erstellen von Berichten dienen werden.

Um zu entscheiden, ob ein Attribut in Adobe Campaign erforderlich ist, fragen Sie sich, ob es in eine der folgenden Kategorien passt:

* Für die **Segmentierung** verwendetes Attribut
* Für **Datenverwaltungsprozesse** verwendetes Attribut (z. B. Aggregatberechnung)
* Für die **Personalisierung** verwendetes Attribut

Wenn ein Attribut nicht in eine dieser Kategorien fällt, benötigen Sie es wahrscheinlich nicht in Adobe Campaign.

### Auswahl von Datentypen {#data-types}

Um eine gute Architektur und System-Performance sicherzustellen, befolgen Sie die folgenden Best Practices, wenn Sie Daten in Adobe Campaign einrichten.

* Eine große Tabelle sollte überwiegend numerische Felder aufweisen und Relationen zu Referenztabellen enthalten (bei Einsatz von Wertelisten).
* Mit dem Attribut **expr** können Sie ein Schema-Attribut in einer Tabelle als berechnetes Feld definieren (anstelle eines physischen definierten Werts). Auf diese Weise können Sie auf Informationen in einem anderen Format zugreifen (z. B. für Alter und Geburtsdatum), ohne beide Werte speichern zu müssen. So lässt sich verhindern, dass Felder dupliziert werden. Die Empfängertabelle nutzt beispielsweise einen Ausdruck für die Domain, der bereits im E-Mail-Feld vorhanden ist.
* Wenn die Berechnung des Ausdrucks jedoch komplex ist, wird eine Verwendung des Attributs **expr** nicht empfohlen, da eine Ad-hoc-Berechnung Auswirkungen auf die Performance Ihrer Abfragen haben kann.
* Der Typ **XML** hilft dabei, eine Erstellung von zu vielen Feldern zu verhindern. Er benötigt jedoch Speicherplatz, da er eine CLOB-Spalte in der Datenbank verwendet. Außerdem können komplexe SQL-Abfragen entstehen, die die Performance beeinträchtigen.
* Die Länge eines **Zeichenfolgenfelds** sollte immer mit der Spalte definiert werden. Standardmäßig beträgt die maximale Länge in Adobe Campaign 255 Zeichen. Adobe empfiehlt jedoch, das Feld zu kürzen, wenn Sie bereits wissen, dass auch weniger ausreicht.
* Es ist akzeptabel, dass ein Feld in Adobe Campaign kürzer ist als im Quellsystem, wenn Sie sicher sind, dass die Länge im Quellsystem zu groß ist und nicht benötigt wird. Dies könnte eine kürzere Zeichenfolge oder kleinere Ganzzahl in Adobe Campaign bedeuten.

### Auswahl von Feldern {#choice-of-fields}

Felder müssen in einer Tabelle gespeichert werden, wenn sie Zielgruppenbestimmungs- oder Personalisierungszwecken dienen. Anders ausgedrückt: Wenn ein Feld nicht zum Senden einer personalisierten E-Mail oder als Kriterium in einer Abfrage verwendet wird, nimmt es Speicherplatz ein, ist aber nutzlos.

Bei Hybrid- und On-Premise-Instanzen deckt FDA (Federated Data Access, eine optionale Funktion, die den Zugriff auf externe Daten ermöglicht) die Notwendigkeit ab, während eines Kampagnenprozesses ein Feld „on-the-fly“ hinzuzufügen. Sie müssen nicht alles importieren, wenn Sie FDA haben. Weitere Informationen hierzu finden Sie unter [Über Federated Data Access](../../installation/using/about-fda.md).

### Auswahl von Schlüsseln {#choice-of-keys}

Zusätzlich zu dem **autopk** der in den meisten Tabellen standardmäßig definiert ist, sollten Sie ggf. einige logische oder geschäftliche Schlüssel (Kontonummer, Kundennummer usw.) hinzufügen. Diese können später für Importe, Abstimmungen oder Daten-Packages verwendet werden. Weitere Informationen hierzu finden Sie unter [Kennungen](#identifiers).

Effiziente Schlüssel sind unverzichtbar für hohe Performance. Numerische Datentypen sollten als Schlüssel für Tabellen stets bevorzugt werden.

Bei einer SQL Server-Datenbank können Sie ggf. einen „Cluster-Index“ verwenden, wenn Leistung erforderlich ist. Da Adobe dies nicht handhabt, müssen Sie es in SQL erstellen.

### Eigene Tablespaces {#dedicated-tablespaces}

Mit dem Attribut tablespace im Schema können Sie einen dedizierten Tablespace für eine Tabelle angeben.

Mit dem Installationsassistenten können Sie Objekte nach Typ speichern (Daten, temporär und Index).

Dedizierte Tablespaces eignen sich besser für Partitionierung und Sicherheitsregeln und ermöglichen eine flüssige und flexible Verwaltung sowie eine bessere Optimierung und Leistung.

## Kennungen {#identifiers}

Adobe Campaign-Ressourcen verfügen über drei Kennungen (IDs). Sie können auch eine zusätzliche Kennung hinzuzufügen.

Die folgende Tabelle beschreibt diese Kennungen und ihren Zweck.

| Kennung | Beschreibung | Best Practices |
|--- |--- |--- |
| ID | <ul><li>Die ID ist der physische Primärschlüssel einer Adobe Campaign-Tabelle. Bei vordefinierten Tabellen handelt es sich um eine generierte 32-Bit-Zahl aus einer Sequenz</li><li>Diese Kennung ist in der Regel für eine bestimmte Adobe Campaign-Instanz eindeutig. </li><li>Eine automatisch generierte ID kann in einer Schemadefinition sichtbar sein. Suchen Sie das Attribut *autopk=„true*.</li></ul> | <ul><li>Automatisch erstellte Kennungen sollten nicht als Referenz in einem Workflow oder in einer Package-Definition verwendet werden.</li><li>Es sollte nicht davon ausgegangen werden, dass die ID immer eine steigende Zahl ist.</li><li>Die ID in einer vordefinierten Tabelle ist eine 32-Bit-Zahl. Dieser Typ sollte nicht geändert werden. Diese Nummer stammt aus einer „Sequenz“, die im Abschnitt mit demselben Namen behandelt wird.</li></ul> |
| Name (oder interner Name) | <ul><li>Diese Information ist eine eindeutige Kennung eines Datensatzes in einer Tabelle. Der Wert kann manuell aktualisiert werden, üblicherweise mit einem erstellten Namen.</li><li>Die Kennung behält ihren Wert bei, wenn sie in einer anderen Instanz von Adobe Campaign bereitgestellt wird, und darf nicht leer sein.</li></ul> | <ul><li>Benennen Sie den von Adobe Campaign generierten Datensatznamen um, wenn das Objekt von einer Umgebung in einer anderen bereitgestellt werden soll.</li><li>Wenn ein Objekt beispielsweise über ein Namespace-Attribut verfügt (zum Beispiel *schema*), wird dieser gemeinsame Namespace für alle erstellten benutzerdefinierten Objekte genutzt. Bestimmte reservierte Namespaces sollten nicht verwendet werden: *nms*, *xtk*, *nl*, *ncl*, *crm*, *xxl*.</li><li>Wenn ein Objekt keinen Namespace aufweist (zum Beispiel *workflow* oder *delivery*), wird dieser Namespace-Begriff als Präfix eines internen Namensobjekts hinzugefügt: *namespaceMyObjectName*.</li><li>Verwenden Sie keine Sonderzeichen wie Leerzeichen &quot;&quot;, Semikolon &quot;:“ oder Bindestrich &quot;-&quot;. Alle diese Zeichen würden durch einen Unterstrich „_“ (zulässiges Zeichen) ersetzt werden. Beispielsweise würden „abc-def“ und „abc:def&quot; als „abc_def“ gespeichert und einander überschreiben.</li></ul> |
| Titel | <ul><li>Der Titel ist die Unternehmenskennung eines Objekts oder Datensatzes in Adobe Campaign.</li><li>Dieses Objekt erlaubt Leerzeichen und Sonderzeichen.</li><li>Der Titel garantiert nicht die Einzigartigkeit eines Datensatzes.</li></ul> | <ul><li>Es wird empfohlen, eine Struktur für die Objekttitel festzulegen.</li><li>Dies ist die benutzerfreundlichste Lösung, um einen Datensatz oder ein Objekt für einen Adobe Campaign-Benutzer zu identifizieren.</li></ul> |

## Benutzerdefinierte interne Schlüssel {#custom-internal-keys}

Für jede in Adobe Campaign erstellte Tabelle sind Primärschlüssel erforderlich.

Die meisten Unternehmen importieren Datensätze aus externen Systemen. Während der physische Schlüssel der Empfängertabelle das &quot;id&quot;-Attribut ist, kann zusätzlich ein benutzerdefinierter Schlüssel festgelegt werden.

Dieser benutzerdefinierte Schlüssel ist der eigentliche Hauptschlüssel des Datensatzes im externen System, das Daten für Adobe Campaign bereitstellt.

Wenn eine vordefinierte Tabelle sowohl über einen autopk als auch über einen internen Schlüssel verfügt, wird der interne Schlüssel als eindeutiger Index in der physischen Datenbanktabelle festgelegt.

Beim Erstellen einer benutzerdefinierten Tabelle stehen Ihnen zwei Optionen zur Verfügung:
* Kombination aus einem automatisch erstellten Schlüssel (ID) und einem internen Schlüssel (benutzerdefiniert). Diese Option ist interessant, wenn Ihr Systemschlüssel ein zusammengesetzter Schlüssel oder keine Ganzzahl ist. Ganzzahlen bieten höhere Performance in umfangreichen Tabellen und in Verbindung mit anderen Tabellen.
* Verwendung des Primärschlüssels als Primärschlüssel des externen Systems. Diese Lösung wird in der Regel bevorzugt, da sie das Importieren und Exportieren von Daten durch einen einheitlichen Schlüssel zwischen verschiedenen Systemen vereinfacht. Autopk sollte deaktiviert werden, wenn der Schlüssel „id“ heißt und mit externen Werten ausgefüllt wird (also nicht automatisch erstellt werden soll).

>[!IMPORTANT]
>
>Ein autopk sollte in Workflows nicht als Referenz verwendet werden.

## Sequenzen {#sequences}

Der Adobe Campaign-Primärschlüssel ist eine automatisch generierte ID für alle vordefinierten Tabellen und kann für benutzerdefinierte Tabellen identisch sein. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](#identifiers).

Dieser Wert wird aus dem so genannten **Sequenz“ entnommen** bei dem es sich um ein Datenbankobjekt handelt, das zum Generieren einer Zahlensequenz verwendet wird.

Es gibt zwei Arten von Sequenzen:
* **Freigegeben**: Mehr als eine Tabelle wählt ihre ID aus derselben Sequenz aus. Das bedeutet, dass keine andere Tabelle mit derselben Sequenz einen Datensatz mit dieser ID „X“ hätte, wenn eine ID „X“ von einer Tabelle verwendet wird. **XtkNewId** ist die standardmäßige freigegebene Sequenz, die in Adobe Campaign verfügbar ist.
* **Dediziert**: nur eine Tabelle wählt ihre IDs aus der Sequenz aus. Der Sequenzname würde normalerweise den Tabellennamen enthalten.

>[!IMPORTANT]
>
>Die Sequenz ist ein ganzzahliger 32-Bit-Wert mit einer endlichen maximalen Anzahl verfügbarer Werte: 2,14 Milliarden. Nach Erreichen des Höchstwerts wird die Sequenz wieder auf 0 zurückgesetzt, um IDs zu recyceln.
>
>Wenn die alten Daten nicht gelöscht wurden, ist das Ergebnis eine Verletzung des eindeutigen Schlüssels, die zu einem Blocker für die Plattformintegrität und -nutzung wird. Adobe Campaign wäre nicht in der Lage, Nachrichten zu senden (wenn sich dies auf die Versandlog-Tabelle auswirkt), und die Leistung wäre stark beeinträchtigt.

Daher würden Kunden, die jährlich 6 Milliarden E-Mails mit einer Aufbewahrungsfrist von 180 Tagen für ihre Protokolle versenden, in 4 Monaten keine IDs mehr haben. Um eine solche Herausforderung zu vermeiden, stellen Sie sicher, dass die Bereinigungseinstellungen Ihren Volumes entsprechen. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](#data-retention).

Wenn in Adobe Campaign eine benutzerdefinierte Tabelle mit einem Primärschlüssel als AutoPK erstellt wird, sollte dieser Tabelle systematisch eine benutzerdefinierte dedizierte Sequenz zugeordnet werden.

Standardmäßig hat eine benutzerdefinierte Sequenz Werte zwischen +1.000 und +2,1BB. Technisch ist es möglich, eine vollständige Bandbreite von 4BB zu erhalten, indem negative IDs aktiviert werden. Dies sollte mit Vorsicht verwendet werden und eine ID geht verloren, wenn von negativen zu positiven Zahlen gewechselt wird: Der Datensatz 0 wird von Adobe Campaign in generierten SQL-Abfragen normalerweise ignoriert.

Weitere Informationen zur Erschöpfung von Sequenzen finden Sie [diesem Video](https://helpx.adobe.com/customer-care-office-hours/campaign/sequences-exhaustion-campaign-classic.html).

## Indizes {#indexes}

Indizes sind für die Leistung von entscheidender Bedeutung. Wenn Sie einen Schlüssel im Schema deklarieren, erstellt Adobe automatisch einen Index für die Schlüsselfelder. Sie können auch weitere Indizes für Abfragen deklarieren, die nicht den Schlüssel verwenden.

Adobe empfiehlt, zusätzliche Indizes zu definieren, da dies die Performance verbessern kann.

Beachten Sie jedoch Folgendes:

* Die Indexnutzung ist an Ihr Zugriffsmuster gebunden. Die Optimierung der Indizierung ist häufig ein wichtiger Bestandteil des Datenbankdesigns und muss von Experten durchgeführt werden. Das Hinzufügen von Indizes ist oft ein iterativer Workflow, der an die Datenbankwartung angehängt ist. Sie wird im Laufe der Zeit Schritt für Schritt durchgeführt, um Leistungsprobleme zu beheben, wenn sie auftreten.
* Indizes erhöhen die Gesamtgröße der Tabelle (um den Index selbst zu speichern).
* Das Hinzufügen eines Index zu Spalten kann die Leistung des Datenlesezugriffs (SELECT) verbessern, aber es kann auch die Leistung des Datenschreibzugriffs (UPDATE) verringern.
* Da sich dies auf die Leistung beim Einfügen von Daten auswirkt, sollten -Indizes in Größe und Anzahl begrenzt sein.
* Fügen Sie keine Indizes hinzu, wenn dies nicht erforderlich ist. Stellen Sie sicher, dass sie erforderlich ist und die Gesamtleistung Ihrer Abfragen (Testen und Lernen) erhöht wird.
* Im Allgemeinen ist ein Index effizient, wenn Sie wissen, dass Ihre Abfragen nicht mehr als 10 % der Datensätze zurückbringen.
* Wählen Sie die zu definierenden Indizes sorgfältig aus.
* Entfernen Sie keine nativen Indizes aus vordefinierten Tabellen.

<!--When you are performing an initial import with very high volumes of data insert in Adobe Campaign database, it is recommended to run that import without custom indexes at first. It will allow to accelerate the insertion process. Once you've completed this important import, it is possible to enable the index(es).-->

### Beispiel

Die Verwaltung von Indizes kann sehr komplex werden. Daher ist es wichtig zu verstehen, wie sie funktionieren. Um diese Komplexität zu veranschaulichen, nehmen wir ein einfaches Beispiel, indem wir beispielsweise nach Empfängern suchen, indem wir nach dem Vor- und Nachnamen filtern. Gehen Sie dazu wie folgt vor:

1. Navigieren Sie zu dem Ordner, der alle Empfänger in der Datenbank auflistet.
1. Klicken Sie mit der rechten Maustaste auf **[!UICONTROL Feld]** Vorname“.
1. Wählen Sie **[!UICONTROL Nach diesem Feld filtern]** aus.

   ![](assets/data-model-index-example.png)

1. Wiederholen Sie diesen Vorgang für das Feld **[!UICONTROL Nachname]**.

Die beiden entsprechenden Filter werden oben im Bildschirm hinzugefügt.

![](assets/data-model-index-search.png)

Sie können jetzt Suchfilter für die Felder **[!UICONTROL Vorname]** und **[!UICONTROL Nachname]** entsprechend den verschiedenen Filterbedingungen durchführen.

Um die Suche nach diesen Filtern zu beschleunigen, können Sie jetzt Indizes hinzufügen. Aber welche Indizes sollten verwendet werden?

>[!NOTE]
>
>Dieses Beispiel gilt für gehostete Kunden, die eine PostgreSQL-Datenbank verwenden.

Die folgende Tabelle zeigt, in welchen Fällen die drei unten beschriebenen Indizes gemäß dem in der ersten Spalte angezeigten Zugriffsmuster verwendet werden oder nicht.

| Suchkriterien | Index 1 (Vorname + Nachname) | Index 2 (nur Vorname) | Index 3 (nur Nachname) | Kommentare |
|--- |--- |--- |--- |--- |
| Vorname ist gleich „Johnny“ | In Gebrauch | In Gebrauch | Nicht verwendet | Da der Vorname auf Index 1 an erster Stelle steht, wird er trotzdem verwendet: Es ist nicht erforderlich, ein Kriterium für den Nachnamen hinzuzufügen. |
| Vorname entspricht „Johnny“ UND Nachname entspricht „Smith“ | In Gebrauch | Nicht verwendet | Nicht verwendet | Da beide Attribute in derselben Abfrage gesucht werden, wird nur der Index verwendet, der beide Attribute kombiniert. |
| Nachname ist gleich „Smith“ | Nicht verwendet | Nicht verwendet | In Gebrauch | Die Reihenfolge der Attribute im Index wird berücksichtigt. Wenn Sie nicht mit dieser Reihenfolge übereinstimmen, wird der Index möglicherweise nicht verwendet. |
| Vorname beginnt mit „John“ | In Gebrauch | In Gebrauch | Nicht verwendet | „Linke Suche“ aktiviert Indizes. |
| Vorname endet mit „nny“ | Nicht verwendet | Nicht verwendet | Nicht verwendet | Mit „Rechter Suche“ werden Indizes deaktiviert und ein vollständiger Scan wird durchgeführt. Einige bestimmte Indextypen könnten diesen Anwendungsfall bewältigen, sie sind jedoch in Adobe Campaign nicht standardmäßig verfügbar. |
| Vorname enthält „John“ | Nicht verwendet | Nicht verwendet | Nicht verwendet | Dies ist eine Kombination aus „links“ und „rechts“ Suchen. Aus diesem Grund werden Indizes deaktiviert und ein vollständiger Scan wird durchgeführt. |
| Vorname ist gleich „john“ | Nicht verwendet | Nicht verwendet | Nicht verwendet | Bei Indizes wird zwischen Groß- und Kleinschreibung unterschieden. Um die Groß-/Kleinschreibung nicht zu berücksichtigen, sollten Sie einen spezifischen Index erstellen, der eine SQL-Funktion wie „upper(firstName)“ enthält. Sie sollten dasselbe mit anderen Datenumwandlungen wie „unaccent(firstName)“ tun. |

## Relationen und Kardinalität {#links-and-cardinality}

### Relationen {#links}

Achten Sie bei großen Tabellen auf die &quot;eigene&quot; Integrität. Durch das Löschen von Datensätzen mit großen Tabellen mit „eigener“ Integrität kann die Instanz angehalten werden. Die Tabelle wird gesperrt; die Löschungen werden einzeln vorgenommen. Daher ist es am besten, bei untergeordneten Tabellen mit großen Volumen &quot;neutrale&quot; Integrität anzuwenden.

Das Deklarieren einer Relation als externer Join ist nicht gut für die Performance. Der Null-ID-Datensatz emuliert die externe Join-Funktion. Es müssen keine externen Joins deklariert werden, wenn der Link den autopk verwendet.

Obwohl es möglich ist, eine beliebige Tabelle in einem Workflow einzubinden, empfiehlt Adobe, allgemeine Relationen zwischen Ressourcen direkt in der Definition der Datenstruktur festzulegen.

Die Relation sollte entsprechend den tatsächlichen Daten in den Tabellen definiert werden. Eine falsche Definition könnte sich auf Daten auswirken, die über Relationen abgerufen wurden, z. B. durch unerwartetes Duplizieren von Datensätzen.

Benennen Sie die Relation konsequent nach der Tabelle: Der Name der Relation sollte Aufschluss über die ferne Tabelle geben.

Benennen Sie eine Relation nicht mit „id“ als Suffix. Benennen Sie sie beispielsweise „transaction“ anstelle von „transactionId“.

Standardmäßig erstellt Adobe Campaign eine Relation mit dem Primärschlüssel der externen Tabelle. Aus Gründen der Klarheit ist es besser, den Join in der Relationsdefinition explizit zu definieren.

Den in einem Link verwendeten Attributen wird ein Index hinzugefügt.

Die   Links des Typs „Erstellt nach“ und „Zuletzt geändert von“ sind in vielen Tabellen vorhanden. Es ist möglich, den Index mithilfe des Attributs noDbIndex auf der Relation zu deaktivieren, wenn diese Informationen nicht vom Unternehmen verwendet werden.

### Kardinalität {#cardinality}

Stellen Sie beim Entwerfen einer Relation sicher, dass der Zieldatensatz eindeutig ist, falls eine 1-1-Beziehung deklariert wurde. Andernfalls gibt der Join möglicherweise mehrere Datensätze zurück, wenn nur einer erwartet wird. Dies führt bei der Versandvorbereitung zu Fehlern, wenn &quot;die Abfrage mehr Zeilen zurückgibt als erwartet&quot;. Verwenden Sie als Namen für die Relation denselben Namen wie beim Zielschema.

Definieren Sie eine Relation mit einer Kardinalität (1-N) im Schema auf der Seite (1). So sollte beispielsweise die Relation &quot;Empfänger (1) - (N) Transaktion&quot; im Transaktionsschema definiert werden.

Beachten Sie, dass eine Umkehrkardinalität einer Relation standardmäßig (N) lautet. Sie können eine Relation (1-1) definieren, indem Sie das Attribut revCardinality=&#39;single&#39; zur Relationsdefinition hinzufügen.

Wenn die Umkehrrelation für den Anwender nicht sichtbar sein soll, können Sie sie mit der Relationsdefinition revLink=&#39;_NONE_&#39; ausblenden. Ein typischer Anwendungsfall hierfür wäre die Definition einer Relation vom Empfänger zur letzten ausgeführten Transaktion. Sie müssen lediglich die Relation vom Empfänger zur letzten Transaktion sehen. In der Transaktionstabelle muss keine Umkehrrelation sichtbar sein.

Relationen, die einen externen Join vornehmen (1-0..1), sollten mit Vorsicht verwendet werden, da sie die System-Performance beeinträchtigen.

## Datenaufbewahrung - Bereinigung und Bereinigung {#data-retention}

Adobe Campaign ist weder ein Data Warehouse noch ein Reporting-Tool. Zur Sicherstellung hoher Performance von Adobe Campaign sollte daher das Datenbankwachstum kontrolliert werden. Dazu kann hilfreich sein, einige der unten aufgeführten Best Practices zu befolgen.

Standardmäßig haben Adobe Campaign-Versand- und -Trackinglogs eine Aufbewahrungsdauer von 180 Tagen. Ein Bereinigungsprozess wird ausgeführt, um alle Protokolle zu entfernen, die älter als dieses Protokoll sind.

* Wenn Sie Protokolle länger aufbewahren möchten, sollte diese Entscheidung abhängig von der Datenbankgröße und der Anzahl der gesendeten Nachrichten sorgfältig getroffen werden. Zur Erinnerung: Die Adobe Campaign-Sequenz ist eine 32-Bit-Ganzzahl.
* Es wird empfohlen, nicht mehr als 1 Milliarde Datensätze gleichzeitig in diesen Tabellen zu haben (etwa 50 % der verfügbaren 2,14 Milliarden IDs), um die Risiken der Nutzung aller verfügbaren IDs zu begrenzen. Dies erfordert für einige Kunden, die Aufbewahrungsdauer unter 180 Tage zu senken.

Weitere Informationen zur Datenaufbewahrung finden Sie unter [Richtlinien für Datenschutz und Sicherheit in Campaign](../../platform/using/privacy-and-recommendations.md).

Weitere Informationen zum Workflow zur Bereinigung der Campaign-Datenbank [in diesem Abschnitt](../../production/using/database-cleanup-workflow.md).

>[!IMPORTANT]
>
>Benutzerdefinierte Tabellen werden im standardmäßigen Bereinigungsprozess nicht bereinigt. Er mag zwar am ersten Tag noch nicht erforderlich sein, vergessen Sie aber nicht, einen Bereinigungsprozess für Ihre benutzerdefinierten Tabellen einzurichten, da sonst später Performance-Probleme auftreten können.

Es gibt verschiedene Lösungen, um den Bedarf an Datensätzen in Adobe Campaign zu minimieren:
* Exportieren Sie die Daten in ein Data Warehouse außerhalb von Adobe Campaign.
* Generieren Sie aggregierte Werte, die weniger Platz einnehmen und dennoch für Ihre Marketing-Zwecke ausreichen. Sie benötigen beispielsweise nicht den vollständigen Verlauf von Kundentransaktionen in Adobe Campaign, um die letzten Käufe verfolgen zu können.

Sie können in einem Schema das Attribut &quot;deleteStatus&quot; deklarieren. Effizienter ist es, den Datensatz als gelöscht zu markieren und das Löschen in die Bereinigungsaufgabe zu verschieben.

## Performance {#performance}

Befolgen Sie die nachstehenden Best Practices, um eine bessere Performance sicherzustellen.

### Allgemeine Empfehlungen {#general-recommendations}

* Vermeiden Sie die Verwendung von Operationen wie „CONTAINS“ in Abfragen. Wenn Sie wissen, wonach gefiltert werden soll, wenden Sie dieselbe Bedingung mit „EQUAL TO“ oder anderen spezifischen Filteroperatoren an.
* Vermeiden Sie die Verknüpfung mit nicht indizierten Feldern beim Aufbau von Daten in Workflows.
* Vergewissern Sie sich, dass Prozesse wie Import und Export außerhalb der Geschäftszeiten ausgeführt werden.
* Stellen Sie sicher, dass ein Zeitplan für alle täglichen Aktivitäten vorhanden ist und halten Sie sich an ihn.
* Wenn einer oder mehrere der täglichen Prozesse fehlschlagen und sie am selben Tag noch ausgeführt werden müssen, stellen Sie sicher, dass beim Starten des manuellen Prozesses keine Konflikte auftreten, da dies die System-Performance beeinträchtigen könnte.
* Stellen Sie sicher, dass keine der täglichen Kampagnen während des Importvorgangs oder bei der Ausführung eines manuellen Prozesses ausgeführt wird.
* Verwenden Sie eine oder mehrere Referenztabellen, anstatt ein Feld in jeder Zeile zu duplizieren. Bei Verwendung von Schlüssel/Wert-Paaren ist es empfehlenswert, einen numerischen Schlüssel zu wählen.
* Eine kurze Zeichenfolge ist weiterhin zulässig. Falls Verweistabellen bereits in einem externen System vorhanden sind, erleichtert die Wiederverwendung derselben die Datenintegration mit Adobe Campaign.

### 1-zu-n-Beziehungen {#one-to-many-relationships}

* Das Datendesign beeinflusst Benutzerfreundlichkeit und Funktionalität. Wenn Sie Ihr Datenmodell mit zahlreichen 1-zu-n-Beziehungen entwickeln, wird es für Benutzer schwieriger, in der Anwendung eine sinnvolle Logik zu erstellen. Für technisch nicht versierte Marketing-Experten kann es schwierig sein, eine 1-zu-n-Filterlogik zu entwerfen und zu verstehen.
* Es wird empfohlen, alle wichtigen Felder in einer Tabelle zu vereinen, da Benutzer so leichter Abfragen erstellen können. Unter Umständen kann die Performance auch verbessert werden, wenn einige Felder in mehreren Tabellen dupliziert werden, wenn dadurch ein Join vermieden werden kann.
* Bestimmte integrierte Funktionen können nicht auf 1-zu-n Beziehungen verweisen, z. B. die Angebotsgewichtungsformel und Sendungen.

## Große Tabellen {#large-tables}

Adobe Campaign setzt auf Datenbank-Engines von Drittanbietern. Je nach Anbieter ist für die Performance-Optimierung bei größeren Tabellen möglicherweise ein bestimmtes Design erforderlich.

Im Folgenden finden Sie einige verbreitete Best Practices, die beim Entwerfen Ihres Datenmodells mit großen Tabellen und komplexen Joins befolgt werden sollten.

* Wenn Sie zusätzliche benutzerdefinierte Empfängertabellen verwenden, stellen Sie sicher, dass Sie für jedes Versand-Mapping über eine dedizierte Protokolltabelle verfügen.
* Reduzieren Sie die Anzahl der Spalten, indem Sie beispielsweise die nicht verwendeten Spalten ermitteln.
* Optimieren Sie die Datenmodellrelationen, indem Sie komplexe Joins vermeiden, wie z. B. Joins mit mehreren Bedingungen und/oder mit mehreren Spalten.
* Verwenden Sie für Join-Schlüssel immer numerische Daten anstelle von Zeichenfolgen.
* Reduzieren Sie die Tiefe der Protokollaufbewahrung so weit wie möglich. Wenn Sie einen tieferen Verlauf benötigen, können Sie Berechnungen aggregieren und/oder benutzerdefinierte Protokolltabellen bearbeiten, um einen größeren Verlauf zu speichern.

### Größe von Tabellen {#size-of-tables}

Die Tabellengröße ist eine Kombination aus der Anzahl der Datensätze und der Anzahl der Spalten pro Datensatz. Beide können sich auf die Performance von Abfragen auswirken.

* Eine **kleine** Tabelle entspricht der Größe der Versandtabelle.
* Eine **mittelgroße** Tabelle entspricht der Größe der Empfängertabelle. Sie weist einen Datensatz pro Kunde auf.
* Eine **große** Tabelle entspricht der Größe der Tabelle &quot;Umfassendes Protokoll&quot;. Sie enthält mehrere Datensätze pro Kunde.
Wenn Ihre Datenbank z. B. 10 Millionen Empfänger umfasst, enthält die Tabelle &quot;Umfassendes Protokoll&quot; etwa 100 bis 200 Millionen Nachrichten und die Tabelle &quot;Versand&quot; einige Tausend Datensätze.

Unter PostgreSQL sollte eine Zeile nicht größer als 8 KB sein, um den [TOAST](https://wiki.postgresql.org/wiki/TOAST)-Mechanismus zu vermeiden. Versuchen Sie daher, die Anzahl der Spalten und die Größe jeder Zeile so weit wie möglich zu reduzieren, um die optimale Leistung des Systems (Speicher und CPU) beizubehalten.

Die Anzahl der Zeilen wirkt sich ebenfalls auf die Performance aus. Die Adobe Campaign-Datenbank dient nicht zum Speichern von Verlaufsdaten, die nicht aktiv für Zielgruppenbestimmungs- oder Personalisierungszwecke verwendet werden. Es handelt sich dabei um eine operative Datenbank.

Um Performance-Probleme im Zusammenhang mit der hohen Zeilenanzahl zu verhindern, sollten Sie nur die erforderlichen Datensätze in der Datenbank speichern. Alle anderen Datensätze sollten Sie in das Data Warehouse eines Drittanbieters exportieren und aus der Adobe Campaign-Betriebsdatenbank entfernen.

Im Folgenden finden Sie Best Practices zur Größe von Tabellen:

* Planen Sie große Tabellen mit weniger Feldern und mehr numerischen Daten.
* Verwenden Sie nicht Spalten vom Typ große Zahlen (z. B. Int64), um kleine Zahlen wie boolesche Werte zu speichern.
* Entfernen Sie nicht verwendete Spalten aus der Tabellendefinition.
* Behalten Sie keine alten oder inaktiven Daten in Ihrer Adobe Campaign-Datenbank bei (Export und Bereinigung).

Hier ein Beispiel:

![](assets/transaction-table-example.png)

In diesem Beispiel:
* Die *Transaktions* und *Transaktionselement* sind groß: mehr als 10 Millionen.
* Die *Produkt*- und *Store*-Tabellen sind kleiner: weniger als 10.000.
* Das Produktlabel und die Referenz wurden in die Tabelle *Produkt* eingefügt.
* Die *Transaktionselement*-Tabelle enthält nur eine Relation zur *Produkt*-Tabelle, die numerisch ist.

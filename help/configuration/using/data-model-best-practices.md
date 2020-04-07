---
title: Verwenden der Tabelle "Adobe Campaign Classic Empfänger"
description: Erfahren Sie, wie Sie beim Entwerfen Ihres Datenmodells die vordefinierte Empfänger-Tabelle in Adobe Campaign Classic verwenden.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8c71f54b68558178171fa30601aebf5e638db37f

---


# Best Practices für Datenmodelle{#data-model-best-practices}

In diesem Dokument werden die wichtigsten Empfehlungen beim Entwerfen Ihres Adobe Campaign-Datenmodells erläutert.

Weitere Informationen zu integrierten Tabellen und deren Interaktion mit Kampagnen finden Sie im Abschnitt zum [Campaign Classic-Datenmodell](../../configuration/using/about-data-model.md) .

Lesen Sie diese [Dokumentation](../../configuration/using/about-schema-reference.md) , um mit Kampagne-Schemas zu beginnen. Erfahren Sie, wie Sie Erweiterungsschema konfigurieren, um das konzeptionelle Datenmodell der Adobe Campaign-Datenbank in diesem [Dokument](../../configuration/using/about-schema-edition.md)zu erweitern.

## Übersicht {#overview}

Das Adobe Campaign-System ist äußerst flexibel und kann über die ursprüngliche Implementierung hinaus erweitert werden. Obwohl die Möglichkeiten unbegrenzt sind, ist es wichtig, die richtigen Entscheidungen zu treffen und eine solide Grundlage zu schaffen, um mit der Entwicklung Ihres Datenmodells zu beginnen.

Dieses Dokument enthält gängige Anwendungsfälle und Best Practices, um zu erfahren, wie Sie Ihr Adobe Campaign-Tool richtig erstellen.

## Architektur von Datenmodellen {#data-model-architecture}

Adobe Campaign Standard ist ein leistungsstarkes kanalübergreifendes System zur Kampagnenverwaltung, das es Ihnen ermöglicht, Online- und Offline-Strategien zu kombinieren, um personalisierte Kundenerlebnisse bereitzustellen.

### Kundenorientierter Ansatz {#customer-centric-approach}

Während die meisten E-Mail-Dienstleister für die Kundenkommunikation einen listenorientierten Ansatz verfolgen, setzt Adobe Campaign eine relationale Datenbank ein, um eine breitere Sicht auf die Kunden und ihre Eigenschaften zu nutzen.

Dieser kundenorientierte Ansatz wird in der Grafik unten dargestellt. The **Recipient** table in grey represents the main customer table around which everything is being built:

![](assets/customer-centric-data-model.png)

Um die Tabellenbeschreibung aufzurufen, wählen Sie in der Liste eine Ressource aus **[!UICONTROL Admin > Configuration > Data schemas]** und klicken Sie auf die **[!UICONTROL Documentation]** Registerkarte.

The Adobe Campaign default data model is presented in this [document](../../configuration/using/data-model-description.md).

>[!NOTE]
>
>Mit Adobe Campaign Classic können Sie eine benutzerdefinierte Kundentabelle erstellen. In den meisten Fällen wird jedoch empfohlen, die Standardtabelle für den [Empfänger](../../configuration/using/about-data-model.md#default-recipient-table) zu verwenden, die bereits über vordefinierte zusätzliche Tabellen und Funktionen verfügt.

### Daten für Adobe Campaign {#data-for-campaign}

Welche Daten sollten an Adobe Campaign gesendet werden? Es ist äußerst wichtig festzustellen, welche Daten Sie für Ihre Marketingaktivitäten benötigen.

>[!NOTE]
>
>Adobe Campaign ist weder ein Data Warehouse noch ein Berichte-Tool. Versuchen Sie daher nicht, alle möglichen Kunden und die zugehörigen Informationen in Adobe Campaign zu importieren oder Daten zu importieren, die nur zum Erstellen von Berichten verwendet werden.

Wenn Sie entscheiden möchten, ob ein Attribut im Adobe Campaign benötigt wird oder nicht, fragen Sie sich, ob es unter eine dieser Kategorien fällt:

* Für die **Segmentierung** verwendetes Attribut
* Für **Datenverwaltungsprozesse** verwendetes Attribut (z. B. Aggregatberechnung)
* Für die **Personalisierung** verwendetes Attribut

Wenn ein Attribut nicht in eine dieser Kategorien fällt, benötigen Sie es wahrscheinlich nicht in Adobe Campaign.

### Auswahl der Datentypen {#data-types}

Um eine gute Architektur und Systemleistung sicherzustellen, befolgen Sie die folgenden Best Practices, wenn Sie Daten in Adobe Campaign einrichten.

* Eine große Tabelle sollte meist numerische Felder enthalten und Links zu Referenztabellen enthalten (bei der Liste von Werten).
* Mit dem **Attribut &quot;expr** &quot;können Sie ein Schema-Attribut als berechnetes Feld und nicht als physikalischen Tabellensatzwert definieren. Dadurch können Informationen in einem anderen Format (z. B. Alter und Geburtsdatum) aufgerufen werden, ohne dass beide Werte gespeichert werden müssen. Dies ist eine gute Möglichkeit, Felder nicht zu duplizieren. Die Tabelle &quot;Empfänger&quot;verwendet beispielsweise einen Ausdruck für die Domäne, der bereits im E-Mail-Feld vorhanden ist.
* Wenn die Berechnung des Ausdrucks jedoch komplex ist, wird nicht empfohlen, das **Attribut &quot;expr** &quot;zu verwenden, da die Berechnung im Handumdrehen die Leistung Ihrer Abfragen beeinträchtigen kann.
* Der **XML** -Typ ist eine gute Möglichkeit, zu viele Felder zu vermeiden. Es nimmt aber auch Speicherplatz auf der Festplatte auf, da es eine CLOB-Spalte in der Datenbank verwendet. Es kann auch zu komplexen SQL-Abfragen führen und die Leistung beeinträchtigen.
* The length for a **string** field should always be defined with the column. Standardmäßig beträgt die maximale Feldlänge 255. Adobe empfiehlt jedoch, das Adobe Campaign kürzer zu halten, wenn Sie bereits wissen, dass die Feldlänge kürzer ist.
* Es ist akzeptabel, dass ein Feld in Adobe Campaign kürzer ist als im Quellsystem, wenn Sie sicher sind, dass die Länge im Quellsystem zu groß ist und nicht benötigt wird. Dies könnte eine kürzere Zeichenfolge oder kleinere Ganzzahl in Adobe Campaign bedeuten.

### Feldauswahl {#choice-of-fields}

Ein Feld muss in einer Tabelle gespeichert werden, wenn es einen Targeting- oder Personalisierungszweck hat. Mit anderen Worten, wenn ein Feld nicht zum Senden einer personalisierten E-Mail verwendet wird oder als Kriterium in einer Abfrage verwendet wird, nimmt es Speicherplatz auf der Festplatte in Anspruch, ist jedoch nutzlos.

Bei Hybrid- und lokalen Instanzen deckt die FDA (Federated Data Access, eine optionale Funktion, die den Zugriff auf externe Daten ermöglicht) die Notwendigkeit ab, während einer Kampagne ein Feld &quot;on-the-fly&quot;hinzuzufügen. Sie müssen nicht alles importieren, wenn Sie FDA haben. For more on this, see [About Federated Data Access](../../platform/using/about-fda.md).

### Schlüsselauswahl {#choice-of-keys}

Zusätzlich zu dem in den meisten Tabellen standardmäßig definierten **Autotyp** sollten Sie einige logische oder geschäftliche Schlüssel hinzufügen (Kontonummer, Kundennummer usw.). Sie kann später für Einfuhren/Überleitungszwecke oder Datenpackagen verwendet werden. Weitere Informationen finden Sie unter [Bezeichner](#identifiers).

Effiziente Schlüssel sind unverzichtbar für die Leistung. Numerische Datentypen sollten immer als Schlüssel für Tabellen bevorzugt werden.

Für die SQLServer-Datenbank können Sie die Verwendung eines &quot;Clusterindex&quot; in Erwägung ziehen, wenn eine Leistung erforderlich ist. Da Adobe dies nicht handhabt, müssen Sie es in SQL erstellen.

### Dedizierte Tablespaces {#dedicated-tablespaces}

Mit dem Attribut tablespace im Schema können Sie einen eigenen Tablespace für eine Tabelle angeben.

Mit dem Installationsassistenten können Sie Objekte nach Typ (Daten, temporär und Index) speichern.

Dedizierte Tablespaces eignen sich besser für Partitionierung, Sicherheitsregeln und ermöglichen eine reibungslose und flexible Verwaltung, bessere Optimierung und Leistung.

## Kennungen {#identifiers}

Adobe Campaign-Ressourcen verfügen über drei Kennungen (IDs). Sie können auch eine zusätzliche Kennung hinzuzufügen.

Die folgende Tabelle beschreibt diese Kennungen und ihren Zweck.

| Kennung | Beschreibung | Best Practices |
|--- |--- |--- |
| Kennung | <ul><li>Die ID ist der physische Primärschlüssel einer Adobe Campaign-Tabelle. Bei vordefinierten Tabellen handelt es sich um eine generierte 32-Bit-Zahl aus einer Sequenz</li><li>Diese Kennung ist in der Regel für eine bestimmte Adobe Campaign-Instanz eindeutig. </li><li>Eine automatisch generierte ID kann in einer Schema-Definition sichtbar sein. Suchen Sie das *Attribut autopk=&quot;true&quot;* .</li></ul> | <ul><li>Automatisch generierte IDs sollten nicht als Referenz in einem Workflow oder in einer Paketdefinition verwendet werden.</li><li>Es sollte nicht angenommen werden, dass die ID immer eine steigende Zahl ist.</li><li>Die ID in einer vordefinierten Tabelle ist eine 32-Bit-Zahl und dieser Typ sollte nicht geändert werden. Diese Zahl stammt aus einer Sequenz, die im Abschnitt mit demselben Namen behandelt wird.</li></ul> |
| Name (oder interner Name) | <ul><li>Diese Information ist eine eindeutige Kennung eines Datensatzes in einer Tabelle. Dieser Wert kann manuell aktualisiert werden, üblicherweise mit einem generierten Namen.</li><li>Dieser Bezeichner behält seinen Wert bei, wenn er in einer anderen Instanz von Adobe Campaign bereitgestellt wird, und sollte nicht leer sein.</li></ul> | <ul><li>Benennen Sie den von Adobe Campaign generierten Datensatznamen um, wenn das Objekt von einer Umgebung in eine andere bereitgestellt werden soll.</li><li>Wenn ein Objekt über ein Namensraum-Attribut verfügt (z. B.*Schema* ), wird dieser allgemeine Namensraum für alle erstellten benutzerdefinierten Objekte verwendet. Einige reservierte Namensraum sollten nicht verwendet werden: *nms*, *xtk*.</li><li>Wenn ein Objekt keinen Namensraum hat (z. B.*Workflow* oder *Versand* ), wird dieser Namensraum als Präfix eines internen Namensobjekts hinzugefügt: *namespaceMyObjectName*.</li><li>Verwenden Sie keine Sonderzeichen wie Leerzeichen &quot; &quot;, Doppelpunkt &quot;:&quot; oder Bindestrich &quot;-&quot;. Alle diese Zeichen würden durch einen Unterstrich (_) ersetzt werden. Beispielsweise würden &quot;abc-def&quot; und &quot;abc:def&quot; als &quot;abc_def&quot; gespeichert werden und sich gegenseitig überschreiben.</li></ul> |
| Titel | <ul><li>Der Titel ist die Unternehmenskennung eines Objekts oder Datensatzes in Adobe Campaign.</li><li>Dieses Objekt erlaubt Leerzeichen und Sonderzeichen.</li><li>Der Titel garantiert nicht die Einzigartigkeit eines Datensatzes.</li></ul> | <ul><li>Es wird empfohlen, eine Struktur für die Objekttitel festzulegen.</li><li>Dies ist die benutzerfreundlichste Lösung, um einen Datensatz oder ein Objekt für einen Adobe Campaign-Benutzer zu identifizieren.</li></ul> |

## Benutzerdefinierte interne Schlüssel {#custom-internal-keys}

Für jede in Adobe Campaign erstellte Tabelle sind Primärschlüssel erforderlich.

Die meisten Organisationen importieren Datensätze aus externen Systemen. Während der physische Schlüssel der Empfänger-Tabelle das Attribut &quot;id&quot;ist, kann zusätzlich ein benutzerdefinierter Schlüssel festgelegt werden.

Dieser benutzerdefinierte Schlüssel ist der eigentliche Hauptschlüssel für den Datensatz im externen Adobe Campaign zur Systemzufuhr.

Wenn eine vordefinierte Tabelle sowohl einen automatischen als auch einen internen Schlüssel enthält, wird der interne Schlüssel als eindeutiger Index in der physischen Datenbanktabelle festgelegt.

Beim Erstellen einer benutzerdefinierten Tabelle stehen Ihnen zwei Optionen zur Verfügung:
* Eine Kombination aus automatisch generiertem Schlüssel (ID) und internem Schlüssel (benutzerdefiniert). Diese Option ist interessant, wenn Ihr Systemschlüssel ein zusammengesetzter Schlüssel oder keine Ganzzahl ist. Ganzzahlen bieten höhere Leistungen in umfangreichen Tabellen und in Verbindung mit anderen Tabellen.
* Verwendung des Primärschlüssels als Primärschlüssel des externen Systems. Diese Lösung wird in der Regel bevorzugt, da sie das Importieren und Exportieren von Daten durch einen einheitlichen Schlüssel zwischen verschiedenen Systemen vereinfacht. Autopk sollte deaktiviert werden, wenn der Schlüssel &quot;id&quot;heißt und mit externen Werten gefüllt werden soll (nicht automatisch generiert).

>[!IMPORTANT]
>
>Ein Autopk sollte nicht als Referenz in Workflows verwendet werden.

## Sequenzen {#sequences}

Der primäre Adobe Campaign ist eine automatisch generierte ID für alle vordefinierten Tabellen und kann für benutzerdefinierte Tabellen identisch sein. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](#identifiers).

Dieser Wert stammt aus einer so genannten **Sequenz**, einem Datenbankobjekt, das zum Generieren einer Zahlensequenz verwendet wird.

Es gibt zwei Arten von Sequenzen:
* **Freigegeben**: mehr als eine Tabelle würde ihre ID aus derselben Sequenz auswählen. Das bedeutet, dass keine andere Tabelle, die dieselbe Sequenz verwendet, einen Datensatz mit der ID &quot;X&quot;hat, wenn eine ID &quot;X&quot;von einer Tabelle verwendet wird. **XtkNewId** ist die standardmäßige freigegebene Sequenz, die in Adobe Campaign verfügbar ist.
* **Zweckgebunden**: Nur eine Tabelle wählt ihre IDs aus der Sequenz. Der Sequenzname enthält normalerweise den Tabellennamen.

>[!IMPORTANT]
>
>Die Sequenz ist ein 32-Bit-Ganzzahlwert mit einer endlichen Höchstzahl verfügbarer Werte: 2,14 Mrd. Nach Erreichen des Maximalwerts wird die Sequenz auf 0 zurückgesetzt, um IDs zu recyceln.
>
>Wenn die alten Daten nicht bereinigt wurden, stellt dies eine Verletzung des eindeutigen Schlüssels dar, die zu einem Blocker für den Zustand und die Nutzung der Plattform wird. Adobe Campaign wäre nicht in der Lage, Mitteilungen zu senden (wenn es sich auf die Versand-Protokolltabelle auswirkt), und die Leistungen wären stark beeinträchtigt.

Daher würde einem Kunden, der jährlich 6 Milliarden E-Mails mit einer Retentionszeit von 180 Tagen für seine Protokolle sendet, innerhalb von 4 Monaten die ID ausgehen. Um eine solche Herausforderung zu vermeiden, stellen Sie sicher, dass die Bereinigungseinstellungen Ihren Volumes entsprechen. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](#data-retention).

Wenn eine benutzerdefinierte Tabelle in Adobe Campaign mit einem Primärschlüssel als autoPK erstellt wird, sollte dieser Tabelle systematisch eine benutzerdefinierte, dedizierte Sequenz zugeordnet werden.

Standardmäßig hat eine benutzerdefinierte Sequenz Werte zwischen +1.000 und +2.1BB. Technisch ist es möglich, eine komplette Reichweite von 4BB zu erhalten, indem negative IDs aktiviert werden. Dies sollte mit Vorsicht verwendet werden und eine ID geht verloren, wenn von negativen zu positiven Zahlen übergegangen wird: Der Datensatz 0 wird normalerweise von Adobe Campaign Classic in generierten SQL-Abfragen ignoriert.

**Verwandte Themen:**
* Weitere Informationen zur Funktion zur automatischen **Sequenzgenerierung** finden Sie in diesem [Dokument](https://helpx.adobe.com/de/campaign/kb/sequence_auto_generation.html).
* Weitere Informationen zur Sequenzerschöpfung finden Sie in diesem [Video](https://helpx.adobe.com/customer-care-office-hours/campaign/sequences-exhaustion-campaign-classic.html).

## Indizes {#indexes}

Indizes sind unverzichtbar für die Leistung. Wenn Sie einen Schlüssel im Schema deklarieren, erstellt Adobe automatisch einen Index für die Schlüsselfelder. Sie können auch weitere Indizes für Abfragen deklarieren, die den Schlüssel nicht verwenden.

Adobe empfiehlt, zusätzliche Indizes zu definieren, da dies die Leistung verbessern kann.

Beachten Sie jedoch Folgendes:

* Die Indexverwendung ist an Ihr Zugriffsmuster gebunden. Die Optimierung der Indizierung ist oft ein wichtiger Bestandteil des Datenbankentwurfs und muss von Experten bearbeitet werden. Das Hinzufügen von Indizes ist oft ein iterativer Arbeitsablauf, der an die Datenbankwartung angehängt wird. Es wird im Laufe der Zeit Schritt für Schritt durchgeführt, um Leistungsprobleme anzugehen, wenn es passiert.
* Indizes erhöhen die Gesamtgröße der Tabelle (um den Index selbst zu speichern).
* Das Hinzufügen von Indizes zu Spalten kann die Leistung des Datenlesezugriffs (SELECT) verbessern, kann jedoch die Leistung des Datenschreibzugriffs (UPDATE) verringern.
* Da sich dies auf die Leistung beim Einfügen von Daten auswirkt, sollten Indizes in Größe und Anzahl begrenzt sein.
* Fügen Sie bei Bedarf keine Indizes hinzu. Vergewissern Sie sich, dass dies erforderlich ist und die Gesamtleistung Ihrer Abfragen erhöht (Test- und Lernleistung).
* Im Allgemeinen ist ein Index effizient, wenn Sie wissen, dass Ihre Abfragen nicht mehr als 10 % der Datensätze zurückbringen.
* Wählen Sie die zu definierenden Indizes sorgfältig aus.
* Entfernen Sie keine nativen Indizes aus den vordefinierten Tabellen.

<!--When you are performing an initial import with very high volumes of data insert in Adobe Campaign database, it is recommended to run that import without custom indexes at first. It will allow to accelerate the insertion process. Once you’ve completed this important import, it is possible to enable the index(es).-->

### Beispiel 

Indizes zu verwalten kann sehr komplex werden, daher ist es wichtig zu verstehen, wie sie funktionieren. Um diese Komplexität zu verdeutlichen, lassen Sie uns ein einfaches Beispiel nehmen, wie z. B. die Suche nach Empfängern durch Filterung des Vor- und Nachnamens. Gehen Sie dazu wie folgt vor:
1. Wechseln Sie zu dem Ordner, in dem alle Empfänger in der Datenbank Liste werden. For more on this, see [Managing profiles](../../platform/using/managing-profiles.md).
1. Klicken Sie mit der rechten Maustaste auf das **[!UICONTROL First name]** Feld.
1. Auswählen **[!UICONTROL Filter on this field]**.

   ![](assets/data-model-index-example.png)

1. Wiederholen Sie diesen Vorgang für das **[!UICONTROL Last name]** Feld.

Die beiden entsprechenden Filter werden oben auf dem Bildschirm hinzugefügt.

![](assets/data-model-index-search.png)

Sie können jetzt Suchfilter für die **[!UICONTROL First name]** und die **[!UICONTROL Last name]** Felder entsprechend den verschiedenen Filterbedingungen durchführen.

Um die Suche auf diesen Filtern zu beschleunigen, können Sie nun Indizes hinzufügen. Aber welche Indizes sollten verwendet werden?

>[!NOTE]
>
>Dieses Beispiel gilt für gehostete Kunden, die eine PostgreSQL-Datenbank verwenden.

Die folgende Tabelle zeigt, in welchen Fällen die drei unten beschriebenen Indizes gemäß dem in der ersten Spalte angezeigten Zugriffsmuster verwendet werden oder nicht.

| Suchkriterien | Index 1 (Vorname + Nachname) | Index 2 (nur Vorname) | Index 3 (nur Nachname) | Erklärung |
|--- |--- |--- |--- |--- |
| Vorname gleich &quot;Johnny&quot; | Verwendet | Verwendet | Nicht verwendet | Da sich der Vorname an erster Stelle auf Index 1 befindet, wird er trotzdem verwendet: Es ist nicht erforderlich, ein Kriterium für den Nachnamen hinzuzufügen. |
| Vorname gleich &quot;Johnny&quot;UND Nachname gleich &quot;Smith&quot; | Verwendet | Nicht verwendet | Nicht verwendet | Da beide Attribute in derselben Abfrage gesucht werden, wird nur der Index verwendet, der beide Attribute kombiniert. |
| Nachname gleich &quot;Schmidt&quot; | Nicht verwendet | Nicht verwendet | Verwendet | Die Reihenfolge der Attribute im Index wird berücksichtigt. Wenn Sie diese Reihenfolge nicht einhalten, wird der Index möglicherweise nicht verwendet. |
| Beginn mit Vorname und &quot;Joh&quot; | Verwendet | Verwendet | Nicht verwendet | &quot;Nach links suchen&quot;aktiviert Indizes. |
| Vorname endet mit &quot;nny&quot; | Nicht verwendet | Nicht verwendet | Nicht verwendet | &quot;Rechtliche Suche&quot; deaktiviert Indizes und eine vollständige Überprüfung wird durchgeführt. Einige bestimmte Indextypen können diesen Anwendungsfall bearbeiten, sind jedoch in Adobe Campaign nicht standardmäßig verfügbar. |
| Vorname enthält &quot;John&quot; | Nicht verwendet | Nicht verwendet | Nicht verwendet | Dies ist eine Kombination aus &quot;links&quot;und &quot;rechts&quot;-Suchen. Aufgrund der letzteren werden Indizes deaktiviert und eine vollständige Überprüfung durchgeführt. |
| Vorname gleich &quot;john&quot; | Nicht verwendet | Nicht verwendet | Nicht verwendet | Bei Indizes wird zwischen Groß- und Kleinschreibung unterschieden. Damit die Groß-/Kleinschreibung nicht berücksichtigt wird, sollten Sie einen bestimmten Index erstellen, der eine SQL-Funktion wie &quot;upper(firstname)&quot;enthält. Sie sollten dies auch bei anderen Datentransformationen tun, z. B. &quot;unaccent(firstname)&quot;. |

## Links und Kardinalität {#links-and-cardinality}

### Relationen {#links}

Achten Sie auf die &quot;eigene&quot; Integrität auf großen Tischen. Das Löschen von Datensätzen mit einer breiten Tabelle in &quot;eigener&quot;Integrität kann die Instanz stoppen. Die Tabelle ist gesperrt und die Löschungen werden einzeln vorgenommen. Daher ist es am besten, &quot;neutrale&quot; Integrität auf untergeordneten Tabellen mit großen Mengen zu verwenden.

Das Deklarieren eines Links als externer Verbindungspunkt ist nicht gut für die Leistung. Der Null-ID-Datensatz emuliert die externe Verbindungsfunktion. Es ist nicht erforderlich, externe Verbindungen zu deklarieren, wenn der Link das Autopk verwendet.

Obwohl es möglich ist, eine beliebige Tabelle in einem Workflow einzubinden, empfiehlt Adobe, allgemeine Relationen zwischen Ressourcen direkt in der Definition der Datenstruktur festzulegen.

Die Relation sollte entsprechend den tatsächlichen Daten in den Tabellen definiert werden. Eine falsche Definition könnte sich auf Daten auswirken, die über Relationen abgerufen wurden, z. B. durch unerwartetes Duplizieren von Datensätzen.

Benennen Sie den Link konsistent mit dem Tabellennamen: der Linkname sollte dabei helfen, zu verstehen, was die entfernte Tabelle ist.

Benennen Sie eine Relation nicht mit &quot;id&quot; als Suffix. Benennen Sie sie beispielsweise &quot;transaction&quot; anstelle von &quot;transactionId&quot;.

Standardmäßig erstellt Adobe Campaign eine Verknüpfung mit dem Primärschlüssel der externen Tabelle. Aus Gründen der Klarheit ist es besser, die Verknüpfung in der Linkdefinition explizit zu definieren.

Den Attributen, die in einem Link verwendet werden, wird ein Index hinzugefügt.

Die Links &quot;Erstellt von&quot;und &quot;Zuletzt geändert von&quot;sind in vielen Tabellen vorhanden. Es ist möglich, den Index mithilfe des Attributs noDbIndex für den Link zu deaktivieren, wenn diese Informationen nicht vom Unternehmen verwendet werden.

### Kardinalität {#cardinality}

Stellen Sie beim Entwerfen eines Links sicher, dass der Datensatz der Zielgruppe eindeutig ist, wenn eine 1-1-Beziehung deklariert wurde. Andernfalls gibt der Beitritt möglicherweise mehrere Datensätze zurück, wenn nur einer erwartet wird. Dies führt bei der Vorbereitung des Versands zu Fehlern, wenn &quot;die Abfrage mehr Zeilen zurückgibt als erwartet&quot;. Stellen Sie den Linknamen auf denselben Namen wie das Zielgruppe-Schema ein.

Definieren Sie einen Link mit einer Kardinalität (1-N) im Schema auf der (1) Seite. So sollte beispielsweise der Empfänger (1) - (N) Transaktion im Transaktions-Schema definiert werden.

Beachten Sie, dass die umgekehrte Kardinalität eines Links standardmäßig (N) lautet. Es ist möglich, einen Link (1-1) zu definieren, indem das Attribut revCardinality=&#39;single&#39; zur Linkdefinition hinzugefügt wird.

Wenn der umgekehrte Link für den Benutzer nicht sichtbar sein sollte, können Sie ihn mit der Linkdefinition revLink=&#39;_NONE_&#39; ausblenden. Ein guter Anwendungsfall hierfür ist die Definition eines Links vom Empfänger zur letzten abgeschlossenen Transaktion. Sie müssen nur den Link vom Empfänger zur letzten Transaktion sehen, und es ist kein Rückwärtslink erforderlich, um in der Transaktionstabelle sichtbar zu sein.

Links, die einen externen Anschluss (1-0.1) ausführen, sollten mit Vorsicht verwendet werden, da dies die Systemleistung beeinträchtigt.

## Datenaufbewahrung - Bereinigung und Bereinigung {#data-retention}

Adobe Campaign ist weder ein Data Warehouse noch ein Berichte-Tool. Um eine gute Performance der Adobe Campaign-Lösung zu gewährleisten, sollte daher das Datenbankwachstum unter Kontrolle bleiben. Um dies zu erreichen, kann die Befolgung einiger der unten aufgeführten Best Practices hilfreich sein.

Standardmäßig haben Adobe Campaign-Versand und Trackinglogs eine Retentionsdauer von 180 Tagen. Ein Bereinigungsprozess wird ausgeführt, um alle älteren Protokolle zu entfernen.

* Wenn Sie die Protokolle länger aufbewahren möchten, sollten Sie diese Entscheidung in Abhängigkeit von der Datenbankgröße und der Menge der gesendeten Nachrichten sorgfältig treffen. Zur Erinnerung: Die Adobe Campaign-Sequenz ist eine 32-Bit-Ganzzahl.
* Es wird empfohlen, nicht mehr als 1 Milliarde Datensätze gleichzeitig in diesen Tabellen zu haben (etwa 50 % der 2,14 Milliarden verfügbaren IDs), um die Risiken des Verbrauchs aller verfügbaren IDs zu begrenzen. Dies erfordert, dass einige Kunden die Retentionsdauer unter 180 Tage senken.

>[!IMPORTANT]
>
>Benutzerdefinierte Tabellen werden nicht mit dem standardmäßigen Bereinigungsprozess bereinigt. Dies ist zwar am ersten Tag nicht erforderlich, vergessen Sie jedoch nicht, einen Bereinigungsprozess für Ihre benutzerdefinierten Tabellen zu erstellen, da dies zu Leistungsproblemen führen könnte.

Es gibt einige Lösungen, um den Bedarf an Datensätzen in Adobe Campaign zu minimieren:
* Exportieren Sie die Daten in ein Data Warehouse außerhalb von Adobe Campaign.
* Generieren Sie aggregierte Werte, die weniger Platz einnehmen und gleichzeitig für Ihre Marketingpraktiken ausreichen. So benötigen Sie beispielsweise nicht den vollständigen Verlauf der Kundentransaktionen in Adobe Campaign, um die letzten Käufe zu verfolgen.

Sie können das Attribut &quot;deleteStatus&quot;in einem Schema deklarieren. Es ist effizienter, den Datensatz als gelöscht zu kennzeichnen und dann die Löschung in der Bereinigungs-Aufgabe zu verschieben.

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

Adobe Campaign setzt auf Datenbankmaschinen von Drittanbietern. Je nach Anbieter ist für die Leistungsoptimierung bei größeren Tabellen möglicherweise ein bestimmtes Design erforderlich.

Im Folgenden finden Sie einige gängige Best Practices, die beim Entwerfen Ihres Datenmodells mit großen Tabellen und komplexen Verbindungen befolgt werden sollten.

* Wenn Sie zusätzliche benutzerdefinierte Empfänger-Tabellen verwenden, stellen Sie sicher, dass Sie für jede Zuordnung von Versänden über eine dedizierte Protokolltabelle verfügen.
* Reduzieren Sie die Anzahl der Spalten, indem Sie beispielsweise die nicht verwendeten Spalten ermitteln.
* Optimieren Sie die Datenmodellrelationen, indem Sie komplexe Joins vermeiden, wie z. B. Joins mit mehreren Bedingungen und/oder mit mehreren Spalten.
* Verwenden Sie für Join-Schlüssel immer numerische Daten anstelle von Zeichenfolgen.
* Reduzieren Sie die Tiefe der Protokollaufbewahrung so weit wie möglich. Wenn Sie einen tieferen Verlauf benötigen, können Sie Berechnungen aggregieren und/oder benutzerdefinierte Protokolltabellen bearbeiten, um einen größeren Verlauf zu speichern.

### Tabellengröße {#size-of-tables}

Die Tabellengröße ist eine Kombination aus der Anzahl der Datensätze und der Anzahl der Spalten pro Datensatz. Beide können sich auf die Performance von Abfragen auswirken.

* Eine **kleine** Tabelle ähnelt der Versand-Tabelle.
* Eine **mittlere** Tabelle entspricht der Größe der Empfänger-Tabelle. Es hat einen Datensatz pro Kunde.
* Eine **große** Tabelle ähnelt der weit gefassten Tabelle. Es enthält viele Datensätze pro Kunde.
Wenn Ihre Datenbank z. B. 10 Millionen Empfänger enthält, enthält die Tabelle &quot;Umfassendes Protokoll&quot;etwa 100 bis 200 Millionen Meldungen und die Tabelle &quot;Versand&quot;einige Tausend Datensätze.

Unter PostgreSQL sollte eine Zeile nicht größer als 8 KB sein, um den [TOAST](https://wiki.postgresql.org/wiki/TOAST) -Mechanismus zu vermeiden. Daher sollten Sie versuchen, die Anzahl der Spalten und die Größe jeder Zeile so weit wie möglich zu reduzieren, um eine optimale Leistung des Systems (Speicher und CPU) zu erhalten.

Die Anzahl der Zeilen wirkt sich auch auf die Leistung aus. Die Adobe Campaign-Datenbank dient nicht zum Speichern von Verlaufsdaten, die nicht aktiv für Targeting- oder Personalisierungszwecke verwendet werden - dies ist eine operative Datenbank.

Um Leistungsprobleme im Zusammenhang mit der hohen Zeilenanzahl zu vermeiden, sollten Sie nur die erforderlichen Datensätze in der Datenbank speichern. Alle anderen Datensätze sollten in ein Drittanbieter-Data Warehouse exportiert und aus der Adobe Campaign-Betriebsdatenbank entfernt werden.

Im Folgenden finden Sie einige Best Practices zur Größe von Tabellen:

* Entwerfen Sie große Tabellen mit weniger Feldern und mehr numerischen Daten.
* Keine große Anzahl von Spalten verwenden (z. B.: Int64), um kleine Zahlen wie boolesche Werte zu speichern.
* Entfernen Sie nicht verwendete Spalten aus der Tabellendefinition.
* Behalten Sie keine historischen oder inaktiven Daten in Ihrer Adobe Campaign-Datenbank bei (Export und Bereinigung).

Hier ein Beispiel:

![](assets/transaction-table-example.png)

In diesem Beispiel:
* Die Tabellen *für Transaktions* - und *Transaktionselemente* sind groß: mehr als 10 Millionen.
* Die *Tabellen &quot;Produkt* &quot;und &quot; *Store* &quot;sind kleiner: weniger als 10.000.
* Die Produktbeschriftung und die Referenz wurden in die *Produkttabelle* aufgenommen.
* Die Tabelle &quot; *Transaktionselement* &quot;enthält nur einen Link zur Tabelle &quot; *Produkt* &quot;, die numerisch ist.

<!--For more detailed best practices on how to optimize the database design for larger volumes, see [Campaign Classic Data model Best practices](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html).-->
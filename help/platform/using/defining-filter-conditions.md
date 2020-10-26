---
title: Filterbedingungen definieren
seo-title: Filterbedingungen definieren
description: Filterbedingungen definieren
seo-description: null
page-status-flag: never-activated
uuid: 2ed5d0bd-88fd-4eff-baf0-ed1b097269da
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: creating-queries
discoiquuid: 8e575da0-c51a-4106-a826-3e1771e63649
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '3397'
ht-degree: 100%

---


# Filterbedingungen definieren{#defining-filter-conditions}

## Operator auswählen {#choosing-the-operator}

In einer Filterbedingung werden zwei Werte durch einen Operator zueinander in Beziehung gesetzt.

![](assets/query_editor_nveau_96.png)

Die folgende Liste beschreibt alle verfügbaren Operatoren:

<table> 
 <thead> 
  <tr> 
   <th> Operator<br /> </th> 
   <th> Zweck<br /> </th> 
   <th> Beispiel<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Gleich</span> <br /> </td> 
   <td> Die ausgegebenen Daten stimmen vollständig mit dem angegebenen Wert überein.<br /> </td> 
   <td> <strong>Nachname (@lastName) gleich 'Müller'</strong>. Nur Empfänger mit dem Nachnamen "Müller" unter Beachtung der genauen Schreibung werden ausgegeben.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Größer als</span> <br /> </td> 
   <td> Die ausgegebenen Daten übersteigen den angegebenen Wert.<br /> </td> 
   <td> <strong>Alter (@age) größer als '50'</strong>. Nur Kontakte/Empfänger mit einem Alter von mehr als '50' Jahren werden ausgegeben (also z. B. '51', '52' usw.).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Niedriger als</span> <br /> </td> 
   <td> Die ausgegebenen Daten unterschreiten den angegebenen Wert.<br /> </td> 
   <td> <strong>Erstellungsdatum (@created) früher als 'DaysAgo(100)'</strong>. Es werden nur die Kontakte ausgegeben, die vor weniger als 100 Tagen angelegt wurden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Größer oder gleich</span> <br /> </td> 
   <td> Die ausgegebenen Daten sind identisch mit oder übersteigen den angegebenen Wert.<br /> </td> 
   <td> <strong>Alter (@age) größer oder gleich '30'</strong>. Nur Kontakte/Empfänger mit einem Alter ab '30' Jahren werden ausgegeben (also z. B. '30', '31', '32' Jahre usw.).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Kleiner oder gleich</span> <br /> </td> 
   <td> Die ausgegebenen Daten sind identisch mit oder unterschreiten den angegebenen Wert.<br /> </td> 
   <td> <strong>Alter (@age) kleiner oder gleich '60'</strong>. Nur Kontakte/Empfänger mit einem Alter bis einschließlich '60' Jahren werden ausgegeben.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Ungleich</span> <br /> </td> 
   <td> Die ausgegebenen Daten unterscheiden sich vom angegebenen Wert.<br /> </td> 
   <td> <strong>Sprache (@language) ungleich 'Englisch'</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Beginnt mit</span> <br /> </td> 
   <td> Die ausgegebenen Daten beginnen mit dem angegebenen Wert.<br /> </td> 
   <td> <strong>Kundennummer (@account) beginnt mit '32010'.</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Beginnt nicht mit</span> <br /> </td> 
   <td> Die ausgegebenen Daten beginnen nicht mit dem angegebenen Wert.<br /> </td> 
   <td> <strong>Kundennummer (@account) beginnt nicht mit '20'</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Enthält</span> <br /> </td> 
   <td> Die ausgegebenen Daten enthalten den angegebenen Wert.<br /> </td> 
   <td> <strong>E-Mail-Domain (@domain) enthält 'mail'</strong>. Nur E-Mail-Domains, die den Wert 'mail' enthalten, werden ausgegeben (z. B. 'gmail.com').<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Enthält nicht</span> <br /> </td> 
   <td> Die ausgegebenen Daten enthalten den angegebenen Wert nicht.<br /> </td> 
   <td> <strong>E-Mail-Domain (@domain) enthält nicht 'oo'</strong>. E-Mail-Domains, die den Wert 'oo' enthalten, werden nicht ausgegeben (z. B. 'google.com' oder 'yahoo.de' zählen nicht zu den Ergebnissen).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Ist wie</span> <br /> </td> 
   <td> <span class="uicontrol">Ist wie</span> erzielt ähnliche Ergebnisse wie der Operator <span class="uicontrol">enthält. </span> Sie können ein Platzhalterzeichen (<span class="uicontrol">%</span>) in den Wert einfügen.<br /> </td> 
   <td> <strong>Nachname (@lastName) ist wie 'Me%er'</strong>. In diesem Fall werden alle Empfänger ausgegeben, deren Nachname z. B. 'Meyer', 'Meier' oder 'Meiser' lautet.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Ist nicht wie</span> <br /> </td> 
   <td> Negative Form des Operators <span class="uicontrol">ist wie</span>. Hier dürfen die ausgegebenen Daten nicht dem angegebenen Wert ähneln. Auch in diesem Fall ist der Platzhalter <span class="uicontrol">%</span> zu verwenden.<br /> </td> 
   <td> <strong>Nachname (@lastName) ist nicht wie 'Schmi%t'</strong>. Alle Empfänger mit Nachnamen 'Schmiedt', 'Schmidt', 'Schmitt' usw. werden ausgeschlossen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Ist leer</span> <br /> </td> 
   <td> Die ausgegebenen Daten enthalten keinen Wert in der entsprechenden Spalte.<br /> </td> 
   <td> <strong>Mobiltelefon (@mobilePhone) ist leer</strong>. Nur Empfänger, für die keine Mobiltelefonnummer angegeben wurde, werden ausgegeben.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Ist nicht leer</span> <br /> </td> 
   <td> Negative Form des Operators <span class="uicontrol">ist leer</span>. Auch hier wird in der Wert-Spalte nichts angegeben.<br /> </td> 
   <td> <strong>E-Mail (@email) ist nicht leer</strong>. Nur Empfänger, die eine E-Mail-Adresse angegeben haben, werden ausgegeben.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Ist enthalten in</span> <br /> </td> 
   <td> Die ausgegebenen Daten sind in den angegebenen Werten enthalten. Die Werte werden durch Kommata getrennt.<br /> </td> 
   <td> <strong>Postleitzahl (location/@zipCode) ist enthalten in '21149,22041,22043'</strong>. Nur Empfänger, deren Postleitzahl '21149', '22041' oder '22043' lautet, werden ausgegeben. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Ist nicht enthalten in</span> <br /> </td> 
   <td> Negative Form des Operators <span class="uicontrol">ist enthalten in</span>. Die den angegebenen Werten entsprechenden Daten werden aus dem Ergebnis ausgeschlossen.<br /> </td> 
   <td> <strong>Postleitzahl (location/@zipCode) ist nicht enthalten in '21149,22041,22043'</strong>. Alle Empfänger, deren Postleitzahl '21149', '22041' oder '22043' lautet, werden vom Ergebnis ausgeschlossen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## UND, ODER, AUSSER verwenden {#using-and--or--except}

In Abfragen, die mehr als eine Bedingung enthalten, müssen die Bedingungen miteinander verknüpft werden. Mögliche Verknüpfungen sind:

* **[!UICONTROL Und]** - beide Filterbedingungen müssen erfüllt werden;
* **[!UICONTROL Oder]** - mindestens eine der Filterbedingungen muss erfüllt werden;
* **[!UICONTROL Außer]** - bezeichnet eine Ausnahme.

Standardmäßig wird die Verknüpfung **[!UICONTROL Und]** vorgeschlagen. Anhand der Dropdown-Liste besteht jedoch die Möglichkeit, eine andere Verknüpfung auszuwählen.

![](assets/query_condition_modif_01.png)

* **[!UICONTROL Und]** fügt eine weitere Filterbedingung hinzu und schränkt die Ergebnisse weiter ein.
* **[!UICONTROL Oder]** berücksichtigt mindestens eine der angegebenen Bedingungen.

   Im unten stehenden Beispiel werden die Empfänger ausgegeben, deren E-Mail-Domain &quot;web.de&quot; enthält ODER deren Postleitzahl mit &quot;20&quot; beginnt.

   ![](assets/query_condition_modif_02.png)

* **[!UICONTROL Außer]** ermöglicht die Konfiguration einer Ausnahme, wenn die erste Filterbedingung keine Ergebnisse zulässt.

   Im unten stehenden Beispiel werden die Empfänger ausgegeben, deren E-Mail-Domain &quot;web.de&quot; enthält, AUSSER wenn der Familienname &quot;Schmidt&quot; lautet.

   ![](assets/query_condition_modif_03.png)

Folgendes Beispiel zeigt einen Filter zur Anzeige aller Empfänger spanischer Sprache ODER aller Frauen, deren Mobiltelefonnummer angegeben ist, ODER aller Empfänger, deren Kundennummer nicht angegeben ist und deren Firma mit &quot;N&quot; anfängt.

![](assets/query_editor_nveau_31.png)

## Bedingungen hierarchisieren {#prioritizing-conditions}

In diesem Kapitel wird erläutert, wie anhand der blauen Pfeile in der Symbolleiste Filterbedingungen hierarchisiert werden können.

* Der Rechtspfeil fügt eine Klammerebene hinzu.
* Der Linkspfeil entfernt eine Klammerebene.

   ![](assets/query_condition_modif_04.png)

* Die nach oben und unten gerichteten Pfeile ermöglichen das Verschieben einer Bedingung und somit die Reihenfolge der Filterung.

Das folgende Beispiel verdeutlicht die Funktionsweise des Linkspfeils. Die ursprüngliche Filterbedingung lautet: **[!UICONTROL Ort gleich Hamburg ODER Geschlecht gleich Männlich und Mobiltelefon nicht angegeben ODER Kundennummer beginnt mit &quot;95&quot; und Firma beginnt mit &quot;A&quot;]**.

Platzieren Sie den Cursor auf der Filterbedingung **[!UICONTROL Geschlecht (@gender) gleich Männlich]** und klicken Sie auf den Pfeil **[!UICONTROL Eine Klammerebene entfernen]**.

![](assets/query_editor_nveau_32.png)

Die Bedingung **[!UICONTROL Geschlecht (@gender) gleich Männlich]** wurde aus der Klammer entfernt. Sie befindet sich nun auf der gleichen Ebene wie die Bedingung &quot;Ort gleich Hamburg&quot;. Die entsprechenden Bedingungen sind jetzt durch **[!UICONTROL Und]** verknüpft.

## Zu extrahierende Daten auswählen {#selecting-data-to-extract}

Je nach Tabelle stehen verschiedene Felder zur Verfügung. Alle Felder sind in einem **[!UICONTROL Hauptelement]** genannten Knoten gespeichert. Die Felder in unten stehendem Beispiel stammen aus der Empfängertabelle (nms:recipient). Die Anzeige erfolgt jeweils in alphabetischer Reihenfolge.

Unten im Fenster werden weitere Details zum ausgewählten Feld angezeigt. So handelt es sich beispielsweise beim Feld **[!UICONTROL E-Mail-Domain]** um ein **[!UICONTROL Berechnetes SQL-Feld]** mit der ergänzenden Bezeichnung **[!UICONTROL (@domain)]**.

![](assets/query_editor_nveau_59.png)

>[!NOTE]
>
>Verwenden Sie das Eingabefeld **[!UICONTROL Suchen]**, um die Liste der möglichen Felder einzuschränken.

Doppelklicken Sie auf ein Feld, um es zu den Ausgabespalten hinzuzufügen. Jedes ausgewählte Feld entspricht einer Spalte in der **[!UICONTROL Datenvorschau]** am Ende der Abfrage.

![](assets/query_editor_nveau_01.png)

Standardmäßig werden erweiterte Felder nicht angezeigt. Dies können Sie ändern, indem Sie auf **[!UICONTROL Erweiterte Felder anzeigen]** im rechten unteren Winkel der verfügbaren Felder klicken. Dann wird auch der vollständige Name der Felder angezeigt.

In der Empfängertabelle beispielsweise gelten folgende Felder als erweitert: **Boolesch 1**, **[!UICONTROL Boolesch 2]**, **[!UICONTROL Boolesch 3]**, **[!UICONTROL Fremdschlüssel der &#39;Ordner&#39;-Verknüpfung]** usw.

In unten stehendem Beispiel wurden alle erweiterten Felder der Empfängertabelle markiert.

![](assets/query_editor_nveau_53.png)

Feld-Kategorien:

<table> 
 <thead> 
  <tr> 
   <th> Symbol<br /> </th> 
   <th> Beschreibung<br /> </th> 
   <th> Beispiele<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_47.png" /> </td> 
   <td> Einfaches Feld<br /> </td> 
   <td> Anrede, E-Mail, Geschlecht usw.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_48.png" /> </td> 
   <td> Primärschlüssel. Dieses SQL-Feld dient der eindeutigen Identifikation eines Datensatzes.<br /> </td> 
   <td> Eine Benutzerkennung - von Natur aus "eindeutig" - ist ein Primärschlüssel.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_02.png" /> </td> 
   <td> Fremdschlüssel. Ermöglicht die Herstellung einer Relation zu einer anderen Tabelle.<br /> </td> 
   <td> Fremdschlüssel des Empfängers, Fremdschlüssel des Dienstes usw.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_46.png" /> </td> 
   <td> Berechnetes Feld. Diese Art von Feld wird bei Bedarf basierend auf den in der Datenbank hinterlegten Werten berechnet.<br /> </td> 
   <td> Alter, E-Mail-Domain usw.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_49.png" /> </td> 
   <td> Textfeld für längere Texte<br /> </td> 
   <td> Kommentare, vollständige Adressen usw.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_50.png" /> </td> 
   <td> Indexiertes SQL-Feld. <br /> </td> 
   <td> Vollständiger Name, ISO-Code usw. <br /> </td> 
  </tr> 
 </tbody> 
</table>

Relationen zu einer Tabelle oder zu Kollektionselementen:

<table> 
 <thead> 
  <tr> 
   <th> Symbol<br /> </th> 
   <th> Beschreibung<br /> </th> 
   <th> Beispiel<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_51.png" /> </td> 
   <td> 1:1-Relationen zu einer bestimmten Tabelle. Einem Datensatz in der Quelltabelle entspricht höchstens ein Datensatz in der Zieltabelle. Ein Empfänger kann beispielsweise höchstens einem Land zugeordnet werden.<br /> </td> 
   <td> Ordner, Zustand, Land usw. <br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_52.png" /> </td> 
   <td> Kollektionselemente bezogen auf eine bestimmte Tabelle. Es handelt sich um 1:n-Relationen. Einem Datensatz in der Quelltabelle können mehrere Datensätze in der Zieltabelle entsprechen, aber ein Datensatz der Zieltabelle entspricht genau einem Datensatz in der Quelltabelle. Ein Empfänger kann z. B. für 'n' Newsletter angemeldet sein.<br /> </td> 
   <td> Abonnements, Listen, Ausschlusslogs usw.<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* Verwenden Sie die Schaltfläche **[!UICONTROL Hinzufügen]** (über der Seitensymbolleiste), um eine Ausgabespalte hinzuzufügen, in der Sie den Ausdruck bearbeiten möchten. Weitere Informationen zum Bearbeiten eines Ausdrucks finden Sie unter [Erstellung von Ausdrücken](#building-expressions).
>* Klicken Sie auf das rote Kreuz **Löschen**, um eine Ausgabespalte zu entfernen.
>* Ändern Sie die Reihenfolge der Ausgabespalten anhand der Pfeile.
>* Verwenden Sie die Schaltfläche **[!UICONTROL Werteverteilung]**, um die im ausgewählten Feld enthaltenen Werte anzuzeigen (z. B. das anteilige Vorkommen von Städten oder Sprachen).


## Erstellung berechneter Felder {#creating-calculated-fields}

Sie haben die Möglichkeit, im Schritt der Datenformatierung ein berechnetes Feld hinzuzufügen. Dieses wird bei der Datenvorschau in Form einer zusätzlichen Spalte angezeigt. Klicken Sie hierfür auf die Schaltfläche **[!UICONTROL Berechnetes Feld hinzufügen]**.

![](assets/query_editor_nveau_43.png)

Vier verschiedene Feldtypen stehen zur Verfügung:

* **[!UICONTROL Unveränderliche Zeichenkette]**: Fügt eine Zeichenkette hinzu.

   ![](assets/query_editor_nveau_60.png)

* **[!UICONTROL Zeichenkette mit JavaScript-Fusion]**: Das berechnete Feld kombiniert eine Zeichenkette mit JavaScript-Direktiven.

   ![](assets/query_editor_nveau_61.png)

* **[!UICONTROL JavaScript-Ausdruck]**: Der Wert des berechneten Felds ist das Ergebnis einer JavaScript-Funktion. Der ausgegebene Wert kann einen bestimmten Typ aufweisen (Ziffer, Datum usw.).

   ![](assets/query_editor_nveau_62.png)

* **[!UICONTROL Auflistungen]**: Dieser Feldtyp erlaubt die Verwendung/Umwandlung des Inhalts einer anderen Spalte.

   Dem Quellwert einer Spalte kann ein Zielwert zugeordnet werden. Es ist der Zielwert, der in der neuen Ausgabespalte angezeigt wird.

   Ein Beispiel zu berechneten **[!UICONTROL Auflistungsfeldern]** können Sie [diesem Abschnitt](../../workflow/using/adding-enumeration-type-calculated-field.md) entnehmen.

   ![](assets/query_editor_nveau_63.png)

   Ein berechnetes Feld vom Typ **[!UICONTROL Auflistungen]** kann vier Bedingungen enthalten:

   * **[!UICONTROL Quellwert beibehalten]** gibt den Quellwert unverändert als Zielwert aus.
   * **[!UICONTROL Folgenden Wert benutzen]** ermöglicht die Eingabe eines Standard-Zielwerts für fehlende Quellwerte.
   * **[!UICONTROL Warnhinweis erzeugen und fortfahren]** weist den Benutzer darauf hin, dass der Quellwert nicht verändert werden kann.
   * **[!UICONTROL Fehler erzeugen und Zeile zurückweisen]** verhindert die Berechnung und den Export der Zeile.

Eine detaillierte Ansicht des hinzugefügten Felds erhalten Sie durch Klick auf die Lupe (**[!UICONTROL Details des berechneten Felds]**).

Klicken Sie zum Entfernen des Felds auf das rote Kreuz (**[!UICONTROL Berechnetes Feld entfernen]**).

![](assets/query_editor_nveau_58.png)

## Erstellung von Ausdrücken {#building-expressions}

Der Ausdruckseditor dient der Berechnung von Aggregaten, der Erstellung von Funktionen oder der Bearbeitung von Formeln von einem Ausdruck ausgehend.

Folgendes Beispiel zeigt die Erstellung eines Ausdrucks zum Zählen eines Primärschlüssels.

Gehen Sie wie folgt vor:

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]** im Fenster **[!UICONTROL Zu extrahierende Daten]** und wählen Sie im Fenster **[!UICONTROL Formeltyp]** die Ihrem Ausdruck entsprechende Formel aus.

   **[!UICONTROL Einfaches Feld]**, **[!UICONTROL Aggregat]** und **[!UICONTROL Ausdruck]** stehen zur Verfügung.

   Wählen Sie die Option **[!UICONTROL Aggregatfunktionen]** und **[!UICONTROL Zählung]** und klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/query_editor_nveau_54.png)

1. Die Zählung der Primärschlüssel wurde konfiguriert.

   ![](assets/query_editor_nveau_88.png)

Nachfolgend werden die **[!UICONTROL Formeltypen]** detailliert dargestellt:

![](assets/query_editor_nveau_05.png)

1. **[!UICONTROL Einfaches Feld]**: führt zurück zum Fenster **[!UICONTROL Feldauswahl]**.
1. **[!UICONTROL Aggregat (Aggregatfunktionen)]**. Nachfolgend einige Beispiele zur Verwendung von Aggregaten:

   * **[!UICONTROL Zählung]**: ermöglicht die Zählung eines Primärschlüssels.
   * **[!UICONTROL Summe]**: berechnet beispielsweise die Gesamtheit aller Bestellungen eines Kunden.
   * **[!UICONTROL Maximaler Wert]**: gibt beispielsweise die Kunden aus, die maximal &quot;n&quot; Artikel gekauft haben.
   * **[!UICONTROL Minimaler Wert]**: gibt beispielsweise die Kunden aus, die zuletzt ein Angebot angenommen haben.
   * **[!UICONTROL Durchschnitt]**: berechnet beispielsweise das durchschnittliche Alter der Empfänger.

      Das Feld **[!UICONTROL Unterschiedlich]** gibt die unterschiedlichen Werte aus, die ungleich Null sind. Auf diese Weise lassen sich z. B. alle Trackinglogs für einen Empfänger abfragen und auf 1 setzen, da es sich um nur einen Empfänger handelt.

1. **[!UICONTROL Ausdruck]**: öffnet das Fenster **[!UICONTROL Ausdruck bearbeiten]**. Ein Ausdruck kann beispielsweise Postleitzahlen mit mehr als 4 bzw. 5 Ziffern filtern, um eventuelle Eingabefehler zu korrigieren.

   ![](assets/query_editor_nveau_71.png)

   Im Abschnitt ](#list-of-functions)Funktionsliste[ finden Sie eine vollständige Liste aller Funktionen.

## Funktionsliste {#list-of-functions}

Mit der Option **[!UICONTROL Ausdruck]** gelangen Sie zum Fenster &quot;Ausdruck bearbeiten&quot;. Verschiedene Funktionskategorien können mit den verfügbaren Feldern zum Einsatz kommen: **[!UICONTROL Aggregate]**, **[!UICONTROL String]**, **[!UICONTROL Datum]**, **[!UICONTROL Numerisch]**, **[!UICONTROL Währung]**, **[!UICONTROL Geomarketing]**, **[!UICONTROL Sonstige]** und **[!UICONTROL Window-Funktionen]**.

Der Ausdruckseditor gestaltet sich wie folgt:

![](assets/s_ncs_user_filter_define_expression.png)

Er ermöglicht die Verknüpfung von Feldern aus den Datenbanktabellen mit folgenden fortgeschrittenen Funktionen:

**Aggregate**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Name</strong><br /> </td> 
   <td> <strong>Beschreibung</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Avg</strong><br /> </td> 
   <td> Gibt den Durchschnittswert einer Spalte vom Typ Zahl aus<br /> </td> 
   <td> Avg(&lt;Wert&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Count</strong><br /> </td> 
   <td> Zählt die Werte ungleich null einer Spalte<br /> </td> 
   <td> Count(&lt;Wert&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>CountAll</strong><br /> </td> 
   <td> Zählt die ausgegebenen Werte (alle Felder)<br /> </td> 
   <td> CountAll()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Countdistinct</strong><br /> </td> 
   <td> Zählt die unterschiedlichen Werte ungleich null einer Spalte<br /> </td> 
   <td> Countdistinct(&lt;Wert&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Max</strong><br /> </td> 
   <td> Gibt den Höchstwert einer Spalte vom Typ Zahl, String oder Datum aus<br /> </td> 
   <td> Max(&lt;Wert&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>Min</strong><br /> </td> 
   <td> Gibt den Mindestwert einer Spalte vom Typ Zahl, String oder Datum aus<br /> </td> 
   <td> Min(&lt;Wert&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>StdDev</strong><br /> </td> 
   <td> Gibt die Standardabweichung der Werte einer Spalte vom Typ Zahl aus<br /> </td> 
   <td> StdDev(&lt;Wert&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Sum</strong><br /> </td> 
   <td> Gibt die Summe der Werte einer Spalte vom Typ Zahl, String oder Datum aus<br /> </td> 
   <td> Sum(&lt;Wert&gt;)<br /></td> 
  </tr> 
 </tbody> 
</table>

**String**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Name</strong><br /> </td> 
   <td> <strong>Beschreibung</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AllNonNull2</strong><br /> </td> 
   <td> Gibt an, ob alle Parameter ungleich null und nicht leer sind<br /> </td> 
   <td> AllNonNull2(&lt;String&gt;, &lt;String&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>AllNonNull3</strong><br /> </td> 
   <td> Gibt an, ob alle Parameter ungleich null und nicht leer sind<br /> </td> 
   <td> AllNonNull3(&lt;String&gt;, &lt;String&gt;, &lt;String&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Ascii</strong><br /> </td> 
   <td> Gibt den ASCII-Wert des ersten Zeichens des Strings aus.<br /> </td> 
   <td> Ascii(&lt;String&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Char</strong><br /> </td> 
   <td> Gibt das ASCII-Code-Zeichen 'n' aus<br /> </td> 
   <td> Char(&lt;Zahl&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>Charindex</strong><br /> </td> 
   <td> Gibt die Position des Strings 2 im String 1 aus..<br /> </td> 
   <td> Charindex(&lt;String&gt;, &lt;String&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>GetLine</strong><br /> </td> 
   <td> Gibt die n-te Zeile (beginnend bei 1) des Strings aus<br /> </td> 
   <td> GetLine(&lt;String&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IfEquals</strong><br /> </td> 
   <td> Gibt den dritten Parameter aus, wenn die ersten beiden Parameter den gleichen Wert aufweisen, sonst wird der letzte Parameter ausgegeben<br /> </td> 
   <td> IfEquals(&lt;String&gt;, &lt;String&gt;, &lt;String&gt;, &lt;String&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IsMemoNull</strong><br /> </td> 
   <td> Gibt an, ob das als Parameter ausgegebene Memo gleich null ist<br /> </td> 
   <td> IsMemoNull(&lt;Memo&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>JuxtWords</strong><br /> </td> 
   <td> Konkatenation von drei als Parameter übergebenen Strings. Fügt, wenn nötig, Leerstellen hinzu.<br /> </td> 
   <td> JuxtWords(&lt;String&gt;, &lt;String&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>JuxtWords3</strong><br /> </td> 
   <td> Konkatenation von drei als Parameter übergebenen Strings. Fügt, wenn nötig, Leerstellen hinzu<br /> </td> 
   <td> JuxtWords3(&lt;String&gt;, &lt;String&gt;, &lt;String&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>LPad</strong><br /> </td> 
   <td> Gibt den String linksseitig aufgefüllt aus<br /> </td> 
   <td> LPad(&lt;String&gt;, &lt;Zahl&gt;, &lt;Zeichen&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Left</strong><br /> </td> 
   <td> Gibt die n ersten Zeichen des Strings aus<br /> </td> 
   <td> Left(&lt;String&gt;, &lt;Zahl&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Length</strong><br /> </td> 
   <td> Gibt die Länge des Strings aus<br /> </td> 
   <td> Length(&lt;String&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Lower</strong><br /> </td> 
   <td> Gibt den String in Kleinbuchstaben aus<br /> </td> 
   <td> Lower(&lt;String&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Ltrim</strong><br /> </td> 
   <td> Löscht die Leerstellen links vom String<br /> </td> 
   <td> Ltrim(&lt;String&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Md5Digest</strong><br /> </td> 
   <td> Gibt eine hexadezimale Darstellung des MD5-Schlüssels eines Strings aus<br /> </td> 
   <td> Md5Digest(&lt;String&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>MemoContains</strong><br /> </td> 
   <td> Gibt an, ob das Memo den als Parameter übergebenen String enthält<br /> </td> 
   <td> MemoContains(&lt;Memo&gt;, &lt;String&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>RPad</strong><br /> </td> 
   <td> Gibt den String rechtsseitig aufgefüllt aus<br /> </td> 
   <td> RPad(&lt;String&gt;, &lt;Zahl&gt;, &lt;Zeichen&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Right</strong><br /> </td> 
   <td> Gibt die n letzten Zeichen des Strings aus<br /> </td> 
   <td> Right(&lt;String&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Rtrim</strong><br /> </td> 
   <td> Löscht die Leerstellen rechts vom String<br /> </td> 
   <td> Rtrim(&lt;String&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Smart</strong><br /> </td> 
   <td> Gibt jedes Wort des Strings beginnend mit einem Großbuchstaben aus<br /> </td> 
   <td> Smart(&lt;String&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Substring</strong><br /> </td> 
   <td> Extrahiert aus dem String den Teilstring, der mit dem Zeichen n1 beginnt und die Länge n2 aufweist<br /> </td> 
   <td> Substring(&lt;String&gt;, &lt;Start&gt;, &lt;Länge&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToString</strong><br /> </td> 
   <td> Konvertiert eine Zahl in einen String<br /> </td> 
   <td> ToString(&lt;Zahl&gt;, &lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Upper</strong><br /> </td> 
   <td> Gibt den String in Großbuchstaben aus<br /> </td> 
   <td> Upper(&lt;String&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>VirtualLink</strong><br /> </td> 
   <td> Gibt den Fremdschlüssel einer als erster Parameter übergebenen Relation aus, wenn die beiden anderen Parameter identisch sind<br /> </td> 
   <td> VirtualLink(&lt;Zahl&gt;, &lt;Zahl&gt;, &lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>VirtualLinkStr</strong><br /> </td> 
   <td> Gibt den Fremdschlüssel (Text) einer als erster Parameter übergebenen Relation aus, wenn die beiden anderen Parameter identisch sind<br /> </td> 
   <td> VirtualLinkStr(&lt;String&gt;, &lt;Zahl&gt;, &lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>dataLength</strong><br /> </td> 
   <td> Gibt die Größe des Strings in Byte aus<br /> </td> 
   <td> dataLength(&lt;String&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Datum**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Name</strong><br /> </td> 
   <td> <strong>Beschreibung</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AddDays</strong><br /> </td> 
   <td> Fügt dem Datum eine Anzahl an Tagen hinzu<br /> </td> 
   <td> AddDays(&lt;Datum&gt;, &lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddHours</strong><br /> </td> 
   <td> Fügt dem Datum eine Anzahl an Stunden hinzu<br /> </td> 
   <td> AddHours(&lt;Datum&gt;, &lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddMinutes</strong><br /> </td> 
   <td> Fügt dem Datum eine Anzahl an Minuten hinzu<br /> </td> 
   <td> AddMinutes(&lt;Datum&gt;, &lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddMonths</strong><br /> </td> 
   <td> Fügt dem Datum eine Anzahl an Monaten hinzu<br /> </td> 
   <td> AddMonths(&lt;Datum&gt;, &lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddSeconds</strong><br /> </td> 
   <td> Fügt dem Datum eine Anzahl an Sekunden hinzu<br /> </td> 
   <td> AddSeconds(&lt;Datum&gt;, &lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddYears</strong><br /> </td> 
   <td> Fügt dem Datum eine Anzahl an Jahren hinzu<br /> </td> 
   <td> AddYears(&lt;Datum&gt;, &lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DateOnly</strong><br /> </td> 
   <td> Gibt nur das Datum aus (mit Uhrzeit = 00:00 Uhr)*<br /> </td> 
   <td> DateOnly(&lt;Datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Day</strong><br /> </td> 
   <td> Gibt die Zahl aus, die dem Tag des Datums entspricht<br /> </td> 
   <td> Day(&lt;Datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DayOfYear</strong><br /> </td> 
   <td> Gibt die Zahl des Tages im Jahr des angegebenen Datums aus<br /> </td> 
   <td> DayOfYear(&lt;Datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgo</strong><br /> </td> 
   <td> Gibt das Datum aus, das dem aktuellen Datum abzüglich n Tage entspricht<br /> </td> 
   <td> DaysAgo(&lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgoInt</strong><br /> </td> 
   <td> Gibt das Datum (Integer JJJJMMTT) aus, das dem aktuellen Datum abzüglich n Tage entspricht<br /> </td> 
   <td> DaysAgoInt(&lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysDiff</strong><br /> </td> 
   <td> Anzahl von Tagen zwischen zwei Daten<br /> </td> 
   <td> DaysDiff(&lt;Enddatum&gt;, &lt;Startdatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysOld</strong><br /> </td> 
   <td> Gibt das Alter in Tagen in Bezug auf ein Datum aus<br /> </td> 
   <td> DaysOld(&lt;Datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetDate</strong><br /> </td> 
   <td> Gibt das aktuelle Systemdatum des Servers aus<br /> </td> 
   <td> GetDate()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Hour</strong><br /> </td> 
   <td> Gibt die Stunde der im Datum angegebenen Uhrzeit aus<br /> </td> 
   <td> Hour(&lt;Datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>HoursDiff</strong><br /> </td> 
   <td> Gibt die Anzahl von Stunden zwischen zwei Daten aus<br /> </td> 
   <td> HoursDiff(&lt;Enddatum&gt;, &lt;Startdatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Minute</strong><br /> </td> 
   <td> Gibt die Minuten der im Datum angegebenen Uhrzeit aus<br /> </td> 
   <td> Minute(&lt;Datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MinutesDiff</strong><br /> </td> 
   <td> Gibt die Anzahl von Minuten zwischen zwei Daten aus<br /> </td> 
   <td> MinutesDiff(&lt;Enddatum&gt;, &lt;Startdatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Month</strong><br /> </td> 
   <td> Gibt die Zahl aus, die dem Monat des Datums entspricht<br /> </td> 
   <td> Month(&lt;Datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsAgo</strong><br /> </td> 
   <td> Gibt das Datum aus, das dem aktuellen Datum abzüglich n Monate entspricht<br /> </td> 
   <td> MonthsAgo(&lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsDiff</strong><br /> </td> 
   <td> Gibt die Anzahl von Monaten zwischen zwei Daten aus<br /> </td> 
   <td> MonthsDiff(&lt;Enddatum&gt;, &lt;Startdatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsOld</strong><br /> </td> 
   <td> Gibt das Alter in Monaten in Bezug auf ein Datum aus<br /> </td> 
   <td> MonthsOld(&lt;Datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Second</strong><br /> </td> 
   <td> Gibt die Sekunden der im Datum angegebenen Uhrzeit aus<br /> </td> 
   <td> Second(&lt;Datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SecondsDiff</strong><br /> </td> 
   <td> Gibt die Anzahl von Sekunden zwischen zwei Daten aus<br /> </td> 
   <td> SecondsDiff(&lt;Enddatum&gt;, &lt;Startdatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubDays</strong><br /> </td> 
   <td> Zieht die angegebene Anzahl von Tagen vom Datum ab<br /> </td> 
   <td> SubDays(&lt;Datum&gt;, &lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubHours</strong><br /> </td> 
   <td> Zieht die angegebene Anzahl von Stunden vom Datum ab<br /> </td> 
   <td> SubHours(&lt;Datum&gt;, &lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubMinutes</strong><br /> </td> 
   <td> Zieht die angegebene Anzahl von Minuten vom Datum ab<br /> </td> 
   <td> SubMinutes(&lt;Datum&gt;, &lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubMonths</strong><br /> </td> 
   <td> Zieht die angegebene Anzahl von Monaten vom Datum ab<br /> </td> 
   <td> SubMonths(&lt;Datum&gt;, &lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubSeconds</strong><br /> </td> 
   <td> Zieht die angegebene Anzahl von Sekunden vom Datum ab<br /> </td> 
   <td> SubSeconds(&lt;Datum&gt;, &lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubYears</strong><br /> </td> 
   <td> Zieht die angegebene Anzahl von Jahren vom Datum ab<br /> </td> 
   <td> SubYears(&lt;Datum&gt;, &lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDate</strong><br /> </td> 
   <td> Konvertiert eine Angabe Datum+Uhrzeit in Datum alleine<br /> </td> 
   <td> ToDate(&lt;Datum + Uhrzeit&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDateTime</strong><br /> </td> 
   <td> Konvertiert einen String in Datum+Uhrzeit<br /> </td> 
   <td> ToDateTime(&lt;String&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncDate</strong><br /> </td> 
   <td> Kürzt die Angabe Datum+Uhrzeit auf Sekunden<br /> </td> 
   <td> TruncDate(@lastModified, &lt;Anzahl Sekunden&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TruncDateTZ</strong><br /> </td> 
   <td> Kürzt die Angabe Datum+Uhrzeit auf Sekunden<br /> </td> 
   <td> TruncDateTZ(&lt;Datum&gt;, &lt;Anzahl Sekunden&gt;, &lt;Zeitzone&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TruncQuarter</strong><br /> </td> 
   <td> Kürzt die Angabe des Datums auf den ersten Tag des Quartals<br /> </td> 
   <td> TruncQuarter(&lt;Datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncTime</strong><br /> </td> 
   <td> Kürzt die Uhrzeitangabe auf Sekunden<br /> </td> 
   <td> TruncTime(&lt;Datum&gt;, &lt;Anzahl Sekunden&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> Kürzt ein Datum auf die Woche<br /> </td> 
   <td> TruncWeek(&lt;Datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncYear</strong><br /> </td> 
   <td> Kürzt die Angabe Datum+Uhrzeit auf den ersten Januar des Jahres<br /> </td> 
   <td> TruncYear(&lt;Datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> Gibt die Zahl des Wochentags in Bezug auf das Datum aus (0=Montag, 6=Sonntag)<br /> </td> 
   <td> WeekDay(&lt;Datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Year</strong><br /> </td> 
   <td> Gibt die Zahl aus, die dem Jahr des Datums entspricht<br /> </td> 
   <td> Year(&lt;Datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearAndMonth</strong><br /> </td> 
   <td> Gibt Jahr und Monat eines Datums aus<br /> </td> 
   <td> YearAndMonth(&lt;Datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearsDiff</strong><br /> </td> 
   <td> Gibt die Anzahl von Jahren zwischen zwei Daten aus<br /> </td> 
   <td> YearsDiff(&lt;Enddatum&gt;, &lt;Startdatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearsOld</strong><br /> </td> 
   <td> Gibt das Alter in Jahren in Bezug auf ein Datum aus<br /> </td> 
   <td> YearsOld(&lt;Datum&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Beachten Sie, dass die Funktion **Dateonly** nicht die Zeitzone des Benutzers, sondern des Servers verwendet.

**Numerisch**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Name</strong><br /> </td> 
   <td> <strong>Beschreibung</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Abs</strong><br /> </td> 
   <td> Gibt den absoluten Wert einer Zahl aus<br /> </td> 
   <td> Abs(&lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Ceil</strong><br /> </td> 
   <td> Gibt die kleinste ganze Zahl aus, die größer oder gleich der angegebenen Zahl ist<br /> </td> 
   <td> Ceil(&lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Floor</strong><br /> </td> 
   <td> Gibt die größte ganze Zahl aus, die kleiner oder gleich der angegebenen Zahl ist<br /> </td> 
   <td> Floor(&lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Greatest</strong><br /> </td> 
   <td> Gibt die größere von zwei Zahlen aus<br /> </td> 
   <td> Greatest(&lt;Zahl 1&gt;, &lt;Zahl 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Least</strong><br /> </td> 
   <td> Gibt die kleinere von zwei Zahlen aus<br /> </td> 
   <td> Least(&lt;Zahl 1&gt;, &lt;Zahl 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Mod</strong><br /> </td> 
   <td> Gibt den Rest der ganzzahligen Division von n1 durch n2 aus<br /> </td> 
   <td> Mod(&lt;Zahl 1&gt;, &lt;Zahl 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Percent</strong><br /> </td> 
   <td> Gibt das Verhältnis zwischen zwei Werten in Prozent aus<br /> </td> 
   <td> Percent(&lt;Zahl 1&gt;, &lt;Zahl 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Random</strong><br /> </td> 
   <td> Gibt einen Zufallswert aus<br /> </td> 
   <td> Random()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Round</strong><br /> </td> 
   <td> Rundet eine Zahl auf n Dezimalstellen<br /> </td> 
   <td> Round(&lt;Zahl&gt;, &lt;Anzahl Dezimalstellen&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Sign</strong><br /> </td> 
   <td> Gibt das Vorzeichen einer Zahl aus<br /> </td> 
   <td> Sign(&lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDouble</strong><br /> </td> 
   <td> Konvertiert einen Integer in einen Real<br /> </td> 
   <td> ToDouble(&lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToInt64</strong><br /> </td> 
   <td> Konvertiert einen Real in einen 64-Bit-Integer<br /> </td> 
   <td> ToInt64(&lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToInteger</strong><br /> </td> 
   <td> Konvertiert einen Real in einen Integer<br /> </td> 
   <td> ToInteger(&lt;Zahl&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Trunc</strong><br /> </td> 
   <td> Kürzt n1 auf n2 Dezimalstellen<br /> </td> 
   <td> Trunc(&lt;n1&gt;, &lt;n2&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

1. Währung

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Name</strong><br /> </td> 
   <td> <strong>Beschreibung</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>ConvertCurrency</strong><br /> </td> 
   <td> Konvertiert einen Betrag der Ursprungswährung in einen Betrag der Zielwährung<br /> </td> 
   <td> ConvertCurrency(&lt;Betrag&gt;, &lt;Ursprungswährung&gt;, &lt;Zielwährung&gt;, &lt;Umrechnungsdatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>FormatCurrency</strong><br /> </td> 
   <td> Formatiert einen Betrag, um ihn den Parametern der gewählten Währung entsprechend anzuzeigen<br /> </td> 
   <td> FormatCurrency(&lt;Betrag&gt;, &lt;Währung&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Geomarketing**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Name</strong><br /> </td> 
   <td> <strong>Beschreibung</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Distance</strong><br /> </td> 
   <td> Gibt die Entfernung zwischen zwei durch Längen- und Breitengrad bezeichneten Punkten aus (in Grad)..<br /> </td> 
   <td> Distance(&lt;Längengrad A&gt;, &lt;Breitengrad A&gt;, &lt;Längengrad B&gt;, &lt;Breitengrad B&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Sonstige**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Name</strong><br /> </td> 
   <td> <strong>Beschreibung</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Case</strong><br /> </td> 
   <td> Gibt den Wert 1 aus, wenn die Bedingung wahr ist, sonst den Wert 2<br /> </td> 
   <td> Case(When(&lt;Bedingung&gt;, &lt;Wert 1&gt;), Else(&lt;Wert 2&gt;))<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>ClearBit</strong><br /> </td> 
   <td> Löscht das Flag aus dem Wert<br /> </td> 
   <td> ClearBit(&lt;Kennung&gt;, &lt;Flag&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Coalesce</strong><br /> </td> 
   <td> Gibt den Wert 2 aus, wenn der Wert 1 gleich null oder leer ist, sonst den Wert 1<br /> </td> 
   <td> Coalesce(&lt;Wert 1&gt;, &lt;Wert 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Decode</strong><br /> </td> 
   <td> Gibt Wert 3 aus, wenn Wert 1 = Wert 2, sonst den Wert 4<br /> </td> 
   <td> Decode(&lt;Wert 1&gt;, &lt;Wert 2&gt;, &lt;Wert 3&gt;, &lt;Wert 4&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Else</strong><br /> </td> 
   <td> Gibt den Wert 1 aus (kann nur als Parameter der 'Case'-Funktion verwendet werden)<br /> </td> 
   <td> Else(&lt;Wert 1&gt;, &lt;Wert 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetEmailDomain</strong><br /> </td> 
   <td> Extrahiert die Domain einer E-Mail-Adresse<br /> </td> 
   <td> GetEmailDomain(&lt;Wert&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetMirrorURL</strong><br /> </td> 
   <td> Ruft die URL des Mirrorseiten-Servers ab<br /> </td> 
   <td> GetMirrorURL(&lt;Wert&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Iif</strong><br /> </td> 
   <td> Gibt den Wert 1 aus, wenn der Ausdruck wahr ist, sonst den Wert 2<br /> </td> 
   <td> Iif(&lt;Bedingung&gt;, &lt;Wert 1&gt;, &lt;Wert 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>IsBitSet</strong><br /> </td> 
   <td> Gibt an, ob das Flag im Wert vorkommt<br /> </td> 
   <td> IsBitSet(&lt;Kennung&gt;, &lt;Flag&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>IsEmptyString</strong><br /> </td> 
   <td> Gibt den Wert 2 aus, wenn der String 1 leer ist, sonst den Wert 3<br /> </td> 
   <td> IsEmptyString(&lt;Wert 1&gt;, &lt;Wert 2&gt;, &lt;Wert 3&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>NoNull</strong><br /> </td> 
   <td> Gibt einen Leerstring aus, wenn das Argument gleich null ist<br /> </td> 
   <td> NoNull(&lt;Wert&gt;)<br /> </td>   
  </tr> 
  <tr> 
   <td> <strong>RowId</strong><br /> </td> 
   <td> Gibt die Zeilennummer aus<br /> </td> 
   <td> RowId<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>SetBit</strong><br /> </td> 
   <td> Setzt das Flag im Wert<br /> </td> 
   <td> SetBit(&lt;Kennung&gt;, &lt;Flag&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToBoolean</strong><br /> </td> 
   <td> Konvertiert eine Zahl in einen booleschen Wert<br /> </td> 
   <td> ToBoolean(&lt;Zahl&gt;)<br /> </td>   
  </tr> 
  <tr> 
   <td> <strong>When</strong><br /> </td> 
   <td> Gibt den Wert 1 aus, wenn der Ausdruck wahr ist, sonst den Wert 2 (kann nur als Parameter der 'Case'-Funktion verwendet werden)<br /> </td> 
   <td> When(&lt;Bedingung&gt;, &lt;Wert 1&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Window-Funktionen**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Name</strong><br /> </td> 
   <td> <strong>Beschreibung</strong><br /> </td> 
   <td> <strong>Syntax</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Desc</strong><br /> </td> 
   <td> Absteigende Sortierung<br /> </td> 
   <td> Desc(&lt;Wert 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>OrderBy</strong><br /> </td> 
   <td> Sortiert das Ergebnis innerhalb der Partition<br /> </td> 
   <td> OrderBy(&lt;Wert 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>PartitionBy</strong><br /> </td> 
   <td> Partitioniert das Ergebnis einer Abfrage<br /> </td> 
   <td> PartitionBy(&lt;Wert 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>RowNum</strong><br /> </td> 
   <td> Erzeugt eine Zeilennummer in Abhängigkeit von der Tabellenpartition und der Sortierreihenfolge<br /> </td> 
   <td> RowNum(PartitionBy(&lt;Wert 1&gt;), OrderBy(&lt;Wert 1&gt;))<br /> </td> 
  </tr> 
 </tbody> 
</table>
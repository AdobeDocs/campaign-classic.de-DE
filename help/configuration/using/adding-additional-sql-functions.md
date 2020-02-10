---
title: Hinzufügen zusätzlicher SQL-Funktionen
seo-title: Hinzufügen zusätzlicher SQL-Funktionen
description: Hinzufügen zusätzlicher SQL-Funktionen
seo-description: null
page-status-flag: never-activated
uuid: d66b5ca2-ac7d-4654-9f0e-9bfe56490c19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 728a95f8-46fe-49a8-a645-a0dd6eeb6615
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7ff12260d875b85256c8678fa8d100fd355398e

---


# Hinzufügen zusätzlicher SQL-Funktionen{#adding-additional-sql-functions}

## Einleitung {#introduction}

Adobe Campaign ermöglicht es dem Benutzer, **eigene Funktionen** zu definieren, die auf SQL-Funktionen zugreifen können, sowohl auf die Funktionen der Datenbank als auch auf die Funktionen, die nicht bereits in der Konsole verfügbar sind. Dies ist beispielsweise bei Aggregationsfunktionen (Durchschnitt, Maximum, Summe) nützlich, die nur auf dem Server berechnet werden können, oder wenn die Datenbank eine einfachere Möglichkeit bietet, bestimmte Funktionen zu implementieren, anstatt den Ausdruck manuell in die Konsole zu schreiben (z.B. Datumsverwaltung).

Dieser Mechanismus kann auch verwendet werden, wenn Sie eine kürzlich verwendete oder ungewöhnliche Datenbank-Engine-SQL-Funktion verwenden möchten, die noch nicht von der Adobe Campaign-Konsole angeboten wird.

Nachdem diese Funktionen hinzugefügt wurden, werden sie wie andere vordefinierte Funktionen im Ausdruckseditor angezeigt.

>[!CAUTION]
>
>SQL-Funktionsaufrufe in der Konsole werden nicht mehr automatisch an den Server gesendet. Der hier beschriebene Mechanismus wird daher **die einzige Möglichkeit, den ungeplanten SQL-Funktionsserver aufzurufen** .

## Installation {#installation}

Die hinzuzufügenden Funktionen befinden sich in einer **&quot;Paket&quot;-Datei im XML-Format**, deren Struktur im folgenden Absatz beschrieben wird.

Um das Paket über die Konsole zu installieren, wählen Sie im Menü die Optionen **Extras/Erweitert/Paket** importieren aus, dann die **[!UICONTROL Install from file]** und befolgen Sie die Anweisungen im Importassistenten.

>[!CAUTION]
>
>Warnung: Auch wenn die Liste der importierten Funktionen sofort im Funktionseditor angezeigt wird, sind sie erst nach einem Neustart von Adobe Campaign einsetzbar.

## Allgemeine Struktur des zu importierenden Pakets {#general-structure-of-package-to-import}

Die hinzuzufügende(n) Funktion(en) befindet/befinden sich in der Datei **&quot;** package&quot;im XML-Format. Hier ein Beispiel:

```
<?xml version="1.0" encoding='ISO-8859-1' ?>
<!-- ===========================================================================
  Additional SQL functions for Adobe Campaign
  ========================================================================== -->
<package
  namespace   = "nms"
  name        = "package-additional-funclist"
  label       = "Additional functions"
  buildVersion= "6.1"
  buildNumber = "10000">

  <entities schema="xtk:funcList">
    <funcList name="myList" namespace="cus">
      <group name="date" label="Personalized date">
        <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
                  minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
          <providerPart provider="MSSQL,Sybase,PostgreSQL" body="extract(year from age($1))-18"/>
        </function>
      </group>
    </funcList>
  </entities>
</package>
```

* Der **Name**, der **Namespace** und die **Beschriftung** dienen nur Informationszwecken. Sie können eine Zusammenfassung des Pakets in der Liste der installierten Pakete anzeigen (Explorer/Administration/Paketverwaltung/Installierte Pakete).
* Die Felder **buildVersion** und **buildNumber** sind obligatorisch. Sie müssen der Servernummer entsprechen, mit der die Konsole verbunden ist. Diese Informationen finden Sie im Feld &quot;Hilfe/Info&quot;.
* Die folgenden Blöcke, **Entitäten** und **Funktionslisten** sind obligatorisch. In funcList sind die Felder &quot;name&quot;und &quot;namespace&quot;obligatorisch, ihr Name bleibt jedoch dem Benutzer überlassen, der entscheidet, und sie geben die Funktionsliste eindeutig an.

   Das bedeutet, dass beim Importieren einer weiteren Liste von Funktionen mit demselben Namespace-/Namenspaar (hier &quot;cus::myList&quot;) die zuvor importierten Funktionen gelöscht werden. Wenn Sie dagegen dieses Namespace/Namenspaar ändern, wird die neue Reihe importierter Funktionen der vorherigen hinzugefügt.

* Mit dem **group** -Element können Sie die Funktionsgruppe angeben, in der die importierten Funktionen im Funktionseditor angezeigt werden. Das Attribut &quot;@name&quot;kann entweder ein bereits vorhandener Name sein (in diesem Fall werden die Funktionen der betreffenden Gruppe hinzugefügt) oder ein neuer Name (in diesem Fall wird er in einer neuen Gruppe angezeigt).
* Erinnerung: Mögliche Werte für das Attribut &quot;@name&quot;im `<group>` Element sind:

   ```
     name="aggregate"      ( label="Aggregates"         )
     name="string"             ( label="String"           )
     name="date"               ( label="Date"             )
     name="numeric"          ( label="Numeric"        )
     name="geomarketing" ( label="Geomarketing"     )
     name="other"              ( label="Others"           )
     name="window"          ( label="Windowing functions" )
   ```

>[!CAUTION]
>
>Vergewissern Sie sich, dass Sie das Attribut &quot;@label&quot;abgeschlossen haben: dies ist der Name, der in der Liste der verfügbaren Funktionen angezeigt wird. Wenn Sie nichts eingeben, hat die Gruppe keinen Namen. Wenn Sie jedoch einen anderen Namen als den vorhandenen eingeben, ändert sich der Name der gesamten Gruppe.

Wenn Sie Funktionen zu verschiedenen Gruppen hinzufügen möchten, können Sie mehrere `<group>` Elemente in derselben Liste verfolgen.

Schließlich kann ein `<group>` Element die Definition einer oder mehrerer Funktionen enthalten, d. h. den Zweck der Paketdatei. Das `<function>` Element ist im folgenden Absatz beschrieben.

## Funktionsbeschreibung &lt;function>&lt;/function> {#function-descriptor--function-}

Der hier vorgestellte Fall ist ein allgemeiner Fall, bei dem wir die **Funktionsdurchführung** gewährleisten wollen.

Nachstehend finden Sie ein Beispiel für eine Funktion der &quot;relativen Reife&quot;, die anhand eines Alters anzeigt, wie viele Jahre die Person als reif gilt.

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

Das Feld **@name** verweist auf den Namen der Funktion, und &quot;args&quot;ist die Liste der Parameter, die in der Beschreibung angezeigt werden. In diesem Fall wird die Funktion im Funktionsauswahlfenster als &quot;relativeMaturity ( `<age>` )&quot;angezeigt.

* **help** ist das Feld, das unten im Fenster des Ausdrucks-Editors angezeigt wird.
* **@display** ist eine informative Nachricht.

   >[!NOTE]
   >
   >In den Attributen &quot;@help&quot;und &quot;@display&quot;steht die Zeichenfolge &quot;$1&quot;für den Namen, der im ersten Funktionsparameter angegeben wurde (hier &quot;Alter&quot;). $2, $3... würde die folgenden Parameter darstellen. Im unten stehenden @body-Attribut gibt $1 den Argumentwert an, der während des Aufrufs an die Funktion übergeben wird.

   >[!NOTE]
   >
   >Die Beschreibung muss eine Zeichenfolge mit gültigen XML-Zeichen sein: Beachten Sie bitte die Verwendung von &#39;&lt;&#39; und &#39;>&#39; anstelle von &lt; und >.

* **@type** ist der Rückgabetyp der Funktion und ist ein Standardwert (lang, string, byte, datetime...). Wird dieser ausgelassen, bestimmt der Server den besten Typ unter den verfügbaren Typen innerhalb des Ausdrucks, der die Funktion implementiert.
* **@minArgs** und **maxArgs** geben die Anzahl der Parameter (Minimum und Maximum) für einen Parameter an. Beispiel: Für eine Funktion mit 2 Parametern sind minArgs und maxArgs 2 und 2. Bei 3 Parametern plus 1 optional sind es 3 bzw. 4.
* Schließlich stellt das **providerPart** -Element die Funktionsimplementierung bereit.

   * Das **provider** -Attribut ist obligatorisch und gibt die Datenbanksysteme an, für die die Implementierung bereitgestellt wird. Wie im Beispiel gezeigt, können bei unterschiedlichen Ausdruckssyntaxen oder zugrunde liegenden Funktionen alternative Implementierungen entsprechend der Datenbank bereitgestellt werden.
   * Das **@body** -Attribut enthält die Funktionsimplementierung. Bitte beachten Sie: Diese Implementierung muss ein Ausdruck in Datenbanksprache sein (kein Codeblock). Abhängig von den Datenbanken können Ausdrücke Unterabfragen sein (&quot;(Spalte aus Tabelle auswählen, bei der ...)&quot;), die nur einen Wert zurückgeben. Dies ist beispielsweise bei Oracle der Fall (die Abfrage muss in Klammern geschrieben werden).
   >[!NOTE]
   >
   >Wenn nur eine oder zwei Datenbanken von der definierten Funktion abgefragt werden können, können wir immer nur die Definitionen angeben, die diesen Datenbanken entsprechen.

## Funktionsbeschreibung für &quot;Pass-through&quot; {#pass-through--function-descriptor}

Ein spezieller Funktionsdeskriptor ist der **&quot;Pass-Through&quot;** -Block mit einem nicht spezifizierten &quot;Provider&quot;-Datenbanksystem. In diesem Fall kann &quot;body&quot;-Implementierungen nur einen einzelnen Funktionsaufruf mit einer Syntax enthalten, die nicht von der verwendeten Datenbank abhängt. Der Block &quot;ProviderPart&quot;ist dagegen eindeutig.

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

In diesem Fall dient das Hinzufügen einer Funktion nur dazu, eine Datenbankfunktion zu erstellen, die standardmäßig nicht verfügbar wäre und nun für den Client sichtbar ist.

## Beispiele {#examples}

Weitere Funktionsbeispiele finden Sie im vordefinierten Paket &quot;xtkdatakitfuncList.xml&quot;.

---
product: campaign
title: Hinzufügen zusätzlicher SQL-Funktionen
description: Erfahren Sie, wie Sie zusätzliche SQL-Funktionen definieren
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: 04b0a0e5-d6df-447c-ac67-66adb1bdf717
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1037'
ht-degree: 0%

---

# Zusätzliche SQL-Funktionen definieren{#adding-additional-sql-functions}

Adobe Campaign ermöglicht es dem Benutzer, **seine eigenen Funktionen** zu definieren, die auf SQL-Funktionen zugreifen können, sowohl auf die Funktionen der Datenbank als auch auf die Funktionen, die noch nicht in der Konsole verfügbar sind. Dies ist beispielsweise bei Aggregatfunktionen (Durchschnitt, Maximum, Summe) nützlich, die nur auf dem Server berechnet werden können oder wenn die Datenbank eine einfachere Möglichkeit bietet, bestimmte Funktionen zu implementieren, anstatt den Ausdruck manuell in die Konsole zu schreiben (z. B. Datumsverwaltung).

Dieser Mechanismus kann auch verwendet werden, wenn Sie eine aktuelle oder ungewöhnliche SQL-Funktion der Datenbank-Engine verwenden möchten, die noch nicht von der Adobe Campaign-Konsole angeboten wird.

Nachdem diese Funktionen hinzugefügt wurden, werden sie im Ausdruckseditor wie andere vordefinierte Funktionen angezeigt.

>[!IMPORTANT]
>
>SQL-Funktionsaufrufe in der Konsole werden nicht mehr automatisch an den Server gesendet. Der hier beschriebene Mechanismus wird daher **zur einzigen Methode,** auf dem ungeplanten SQL-Funktionsserver aufzurufen.

## Installation {#installation}

Die hinzuzufügenden Funktionen befinden sich in der Datei **&quot;package&quot; im XML-Format**, deren Struktur im folgenden Absatz beschrieben wird.

Um es über die Konsole zu installieren, wählen Sie im Menü die Optionen **Tools/Erweitert/Package importieren** , dann die Option **[!UICONTROL Aus Datei installieren]** und befolgen Sie die Anweisungen im Import-Assistenten.

>[!IMPORTANT]
>
>Warnung: Selbst wenn die Liste der importierten Funktionen sofort im Funktionseditor angezeigt wird, können sie erst nach dem Neustart von Adobe Campaign verwendet werden.

## Allgemeine Struktur des zu importierenden Packages {#general-structure-of-package-to-import}

Die hinzuzufügenden Funktionen finden Sie in der Datei **&quot;package&quot;** im XML-Format. Hier ein Beispiel:

```
<?xml version="1.0" encoding='ISO-8859-1' ?>
<!-- ===========================================================================
  Additional SQL functions for Adobe Campaign
  ========================================================================== -->
<package
  namespace   = "nms"
  name        = "package-additional-funclist"
  label       = "Additional functions"
  buildVersion= "7.1"
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

* Die **name**, **namespace** und **label** dienen nur zu Informationszwecken. Sie können eine Zusammenfassung des Pakets in der Liste der installierten Packages anzeigen (Explorer/Administration/Package Management/Installierte Packages).
* Die Felder **buildVersion** und **buildNumber** sind obligatorisch. Sie müssen der Server-Nummer entsprechen, mit der die Konsole verbunden ist. Diese Informationen finden Sie im Feld &quot;Hilfe/Info&quot;.
* Die folgenden Blöcke, **entitäten** und **funktionlist** sind obligatorisch. In funcList sind die Felder &quot;name&quot;und &quot;namespace&quot;obligatorisch, ihr Name bleibt jedoch dem Benutzer überlassen, zu entscheiden, und sie geben die Funktionsliste eindeutig an.

  Wenn also eine andere Liste von Funktionen mit demselben Namespace-/Namenspaar (hier &quot;cus::myList&quot;) importiert wird, werden die zuvor importierten Funktionen gelöscht. Umgekehrt wird die neue Serie importierter Funktionen zur vorherigen hinzugefügt, wenn Sie dieses Namespace-/Namenspaar ändern.

* Mit dem Element **group** können Sie die Funktionsgruppe angeben, in der die importierten Funktionen im Funktionseditor angezeigt werden. Das Attribut @name kann entweder ein bereits vorhandener Name sein (in diesem Fall werden die Funktionen der betreffenden Gruppe hinzugefügt) oder ein neuer Name (in diesem Fall wird er in einer neuen Gruppe angezeigt).
* Erinnerung: Mögliche Werte für das Attribut @name im Element `<group>` sind:

  ```
    name="aggregate"      ( label="Aggregates"         )
    name="string"             ( label="String"           )
    name="date"               ( label="Date"             )
    name="numeric"          ( label="Numeric"        )
    name="geomarketing" ( label="Geomarketing"     )
    name="other"              ( label="Others"           )
    name="window"          ( label="Windowing functions" )
  ```

>[!IMPORTANT]
>
>Vergewissern Sie sich, dass Sie das Attribut @label ausgefüllt haben: Dies ist der Name, der in der Liste der verfügbaren Funktionen angezeigt wird. Wenn Sie nichts eingeben, hat die Gruppe keinen Namen. Wenn Sie jedoch einen anderen Namen als den vorhandenen eingeben, ändert sich der Name der gesamten Gruppe.

Wenn Sie Funktionen zu mehreren Gruppen hinzufügen möchten, können Sie mehrere `<group>` -Elemente in derselben Liste nachverfolgen lassen.

Schließlich kann ein Element `<group>` die Definition einer oder mehrerer Funktionen enthalten, also den Zweck der Paketdatei. Der `<function>`   -Element wird im folgenden Absatz beschrieben.

## Funktionsdeskriptor &lt;function>&lt;/function> {#function-descriptor--function-}

Der hier dargestellte Fall ist ein allgemeiner Fall, in dem wir die Implementierung der **Funktion** bereitstellen möchten.

Unten finden Sie ein Beispiel für eine Funktion der &quot;relativen Reife&quot;, die anhand eines Alters angibt, für wie viele Jahre die Person als reif angesehen wurde.

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

Das Feld **@name** bezieht sich auf den Namen der Funktion und &quot;args&quot; ist die Liste der Parameter, die in der Beschreibung angezeigt werden. In diesem Fall wird die Funktion im Funktionsauswahlfenster als &quot;relativeMaturity ( `<age>` )&quot;angezeigt.

* **help** ist das Feld, das unten im Ausdruckseditor-Fenster angezeigt wird.
* **@display** ist eine informative Nachricht.

  >[!NOTE]
  >
  >In den Attributen @help und @display stellt die Zeichenfolge &quot;$1&quot;den Namen dar, der im ersten Funktionsparameter angegeben wurde (hier &quot;Alter&quot;). $2, $3.. würde die folgenden Parameter darstellen. Im unten beschriebenen @body-Attribut gibt $1 den Argumentwert an, der während des Aufrufs an die Funktion übergeben wird.

  >[!NOTE]
  >
  >Die Beschreibung muss eine Zeichenfolge aus gültigen XML-Zeichen sein: Beachten Sie die Verwendung von &#39;&lt;&#39; und &#39;>&#39; anstelle von &lt; und >.

* **@type** ist der Rückgabetyp der Funktion und ist ein Standardwert (long, string, byte, datetime..). Wenn es weggelassen wird, bestimmt der Server den besten Typ unter den verfügbaren Typen innerhalb des Ausdrucks, der die Funktion implementiert.
* **@minArgs** und **maxArgs** geben die Anzahl der Parameter (Minimum und Maximum) für einen Parameter an. Für eine Funktion mit 2 Parametern sind beispielsweise minArgs und maxArgs 2 und 2. Für 3 Parameter, plus 1 optional, sind sie 3 bzw. 4.
* Schließlich stellt das Element **providerPart** die Funktionsimplementierung bereit.

   * Das Attribut **provider** ist obligatorisch und gibt die Datenbanksysteme an, für die die Implementierung bereitgestellt wird. Wie im Beispiel gezeigt, können bei unterschiedlichen Ausdruckssyntax oder zugrunde liegenden Funktionen je nach Datenbank alternative Implementierungen bereitgestellt werden.
   * Das Attribut **@body** enthält die Implementierung der Funktion. Bitte beachten Sie: Bei dieser Implementierung muss es sich um einen Ausdruck in Datenbanksprache (nicht um einen Codeblock) handeln. Abhängig von den Datenbanken können Ausdrücke aus Unterabfragen (&quot;(Spalte aus Tabelle auswählen, wo..)&quot;) bestehen, die nur einen einzigen Wert zurückgeben. Dies ist beispielsweise bei Oracle der Fall (die Abfrage muss in Klammern geschrieben sein).

  >[!NOTE]
  >
  >Wenn nur eine oder zwei Datenbanken von der definierten Funktion abgefragt werden können, können wir immer nur die den Datenbanken entsprechenden Definitionen angeben.

## Funktionsdeskriptor &quot;Pass-Through&quot; {#pass-through--function-descriptor}

Ein spezieller Funktionsdeskriptor ist der Block **&quot;Pass-Through&quot;** mit einem nicht spezifizierten Datenbanksystem &quot;Provider&quot;. In diesem Fall kann die Implementierung von &quot;body&quot;nur einen einzelnen Funktionsaufruf mit einer Syntax enthalten, die nicht von der verwendeten Datenbank abhängig ist. In der Zwischenzeit ist der Block &quot;ProviderPart&quot;eindeutig.

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

In diesem Fall dient das Hinzufügen einer Funktion nur dazu, eine Datenbankfunktion zu erstellen, die standardmäßig nicht verfügbar gewesen wäre und nun für den Client sichtbar ist.

## Beispiele {#examples}

Weitere Funktionsbeispiele finden Sie im vordefinierten Paket &quot;xtkdatakitfuncList.xml&quot;.

---
product: campaign
title: Hinzufügen zusätzlicher SQL-Funktionen
description: Erfahren Sie, wie Sie zusätzliche SQL-Funktionen definieren
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 04b0a0e5-d6df-447c-ac67-66adb1bdf717
source-git-commit: acfe0c4139671fc3df69ff434ba307aaaaf70676
workflow-type: tm+mt
source-wordcount: '1026'
ht-degree: 0%

---

# Zusätzliche SQL-Funktionen definieren{#adding-additional-sql-functions}

Mit Adobe Campaign kann der Benutzer **eigene Funktionen** , die auf SQL-Funktionen zugreifen können, sowohl auf die von der Datenbank angebotenen Funktionen als auch auf die Funktionen, die noch nicht in der Konsole verfügbar sind. Dies ist beispielsweise bei Aggregatfunktionen (Durchschnitt, Maximum, Summe) nützlich, die nur auf dem Server berechnet werden können oder wenn die Datenbank eine einfachere Möglichkeit bietet, bestimmte Funktionen zu implementieren, anstatt den Ausdruck manuell in die Konsole zu schreiben (z. B. Datumsverwaltung).

Dieser Mechanismus kann auch verwendet werden, wenn Sie eine aktuelle oder ungewöhnliche SQL-Funktion der Datenbank-Engine verwenden möchten, die noch nicht von der Adobe Campaign-Konsole angeboten wird.

Nachdem diese Funktionen hinzugefügt wurden, werden sie im Ausdruckseditor wie andere vordefinierte Funktionen angezeigt.

>[!IMPORTANT]
>
>SQL-Funktionsaufrufe in der Konsole werden nicht mehr automatisch an den Server gesendet. Der hier beschriebene Mechanismus wird somit **die einzige Möglichkeit,** auf dem ungeplanten SQL-Funktionsserver.

## Installation {#installation}

Die hinzuzufügenden Funktionen befinden sich in einer **&quot;package&quot;-Datei im XML-Format**, deren Struktur im folgenden Absatz beschrieben wird.

Um es über die Konsole zu installieren, wählen Sie die **Tools/Erweitert/Import-Paket** Optionen aus dem Menü, dann die **[!UICONTROL Aus Datei installieren]** und befolgen Sie die Anweisungen im Importassistenten.

>[!IMPORTANT]
>
>Warnung: selbst wenn die Liste der importierten Funktionen sofort im Funktionseditor angezeigt wird, können sie erst nach dem Neustart von Adobe Campaign verwendet werden.

## Allgemeine Struktur des zu importierenden Packages {#general-structure-of-package-to-import}

Die hinzuzufügenden Funktionen finden Sie im Abschnitt **Datei &quot;package&quot;** im XML-Format. Hier ein Beispiel:

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

* Die **name**, **namespace** und **label** dienen nur Informationszwecken. Sie können eine Zusammenfassung des Pakets in der Liste der installierten Packages anzeigen (Explorer/Administration/Package Management/Installierte Packages).
* Die **buildVersion** und **buildNumber** -Felder sind Pflichtfelder. Sie müssen der Server-Nummer entsprechen, mit der die Konsole verbunden ist. Diese Informationen finden Sie im Feld &quot;Hilfe/Info&quot;.
* Die folgenden Blöcke **entity** und **functionList** sind zwingend erforderlich. In funcList sind die Felder &quot;name&quot;und &quot;namespace&quot;obligatorisch, ihr Name bleibt jedoch dem Benutzer überlassen, zu entscheiden, und sie geben die Funktionsliste eindeutig an.

  Wenn also eine andere Liste von Funktionen mit demselben Namespace-/Namenspaar (hier &quot;cus::myList&quot;) importiert wird, werden die zuvor importierten Funktionen gelöscht. Umgekehrt wird die neue Serie importierter Funktionen zur vorherigen hinzugefügt, wenn Sie dieses Namespace-/Namenspaar ändern.

* Die **Gruppe** -Element können Sie die Funktionsgruppe angeben, in der die importierten Funktionen im Funktionseditor angezeigt werden. Das Attribut @name kann entweder ein bereits vorhandener Name sein (in diesem Fall werden die Funktionen der betreffenden Gruppe hinzugefügt) oder ein neuer Name (in diesem Fall wird er in einer neuen Gruppe angezeigt).
* Erinnerung: mögliche Werte für das Attribut @name im `<group>` -Element:

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
>Vergewissern Sie sich, dass das Attribut @label ausgefüllt ist: Dies ist der Name, der in der Liste der verfügbaren Funktionen angezeigt wird. Wenn Sie nichts eingeben, hat die Gruppe keinen Namen. Wenn Sie jedoch einen anderen Namen als den vorhandenen eingeben, ändert sich der Name der gesamten Gruppe.

Wenn Sie Funktionen zu mehreren Gruppen hinzufügen möchten, können Sie mehrere `<group>`  -Elemente in derselben Liste nachverfolgt werden.

Schließlich wird eine `<group>` -Element kann die Definition einer oder mehrerer Funktionen enthalten, also den Zweck der Paketdatei. Die  `<function>`   -Element wird im folgenden Absatz beschrieben.

## Funktionsdeskriptor &lt;function>&lt;/function> {#function-descriptor--function-}

Der hier vorgestellte Fall ist ein allgemeiner Fall, in dem wir die **Funktionsimplementierung**.

Unten finden Sie ein Beispiel für eine Funktion der &quot;relativen Reife&quot;, die anhand eines Alters angibt, für wie viele Jahre die Person als reif angesehen wurde.

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

Die **@name** -Feld bezieht sich auf den Namen der Funktion und &quot;args&quot;ist die Liste der Parameter, die in der Beschreibung angezeigt werden. In diesem Fall wird die Funktion als &quot;relativeMaturity ( `<age>` )&quot; im Funktionsauswahlfenster.

* **help** ist das Feld, das unten im Ausdruckseditor-Fenster angezeigt wird.
* **@display** ist eine informative Nachricht.

  >[!NOTE]
  >
  >In den Attributen @help und @display stellt die Zeichenfolge &quot;$1&quot;den Namen dar, der im ersten Funktionsparameter angegeben wurde (hier &quot;Alter&quot;). $2, $3.. würde die folgenden Parameter darstellen. Im unten beschriebenen @body-Attribut gibt $1 den Argumentwert an, der während des Aufrufs an die Funktion übergeben wird.

  >[!NOTE]
  >
  >Die Beschreibung muss eine Zeichenfolge aus gültigen XML-Zeichen sein: Beachten Sie bitte die Verwendung von &#39;&lt;&#39; und &#39;>&#39; anstelle von &lt; und >.

* **@type** ist der Rückgabetyp der Funktion und ist ein Standardwert (long, string, byte, datetime..). Wenn es weggelassen wird, bestimmt der Server den besten Typ unter den verfügbaren Typen innerhalb des Ausdrucks, der die Funktion implementiert.
* **@minArgs** und **maxArgs** gibt die Anzahl der Parameter (Minimum und Maximum) für einen Parameter an. Für eine Funktion mit 2 Parametern sind beispielsweise minArgs und maxArgs 2 und 2. Für 3 Parameter, plus 1 optional, sind sie 3 bzw. 4.
* Schließlich wird die **providerPart** -Element stellt die Funktionsimplementierung bereit.

   * Die **Anbieter** -Attribut erforderlich ist, gibt es die Datenbanksysteme an, für die die Implementierung bereitgestellt wird. Wie im Beispiel gezeigt, können bei unterschiedlichen Ausdruckssyntax oder zugrunde liegenden Funktionen je nach Datenbank alternative Implementierungen bereitgestellt werden.
   * Die **@body** -Attribut enthält die Funktionsimplementierung. Bitte beachten Sie: Diese Implementierung muss ein Ausdruck in Datenbanksprache (kein Codeblock) sein. Abhängig von den Datenbanken können Ausdrücke aus Unterabfragen (&quot;(Spalte aus Tabelle auswählen, wo..)&quot;) bestehen, die nur einen einzigen Wert zurückgeben. Dies ist beispielsweise bei Oracle der Fall (die Abfrage muss in Klammern geschrieben sein).

  >[!NOTE]
  >
  >Wenn nur eine oder zwei Datenbanken von der definierten Funktion abgefragt werden können, können wir immer nur die den Datenbanken entsprechenden Definitionen angeben.

## Funktionsdeskriptor &quot;Pass-Through&quot; {#pass-through--function-descriptor}

Ein spezieller Funktionsdeskriptor ist die **&quot;Pass-Through&quot;** -Block mit einem nicht spezifizierten &quot;Anbieter&quot;-Datenbanksystem. In diesem Fall kann die Implementierung von &quot;body&quot;nur einen einzelnen Funktionsaufruf mit einer Syntax enthalten, die nicht von der verwendeten Datenbank abhängig ist. In der Zwischenzeit ist der Block &quot;ProviderPart&quot;eindeutig.

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

In diesem Fall dient das Hinzufügen einer Funktion nur dazu, eine Datenbankfunktion zu erstellen, die standardmäßig nicht verfügbar gewesen wäre und nun für den Client sichtbar ist.

## Beispiele {#examples}

Weitere Funktionsbeispiele finden Sie im vordefinierten Paket &quot;xtkdatakitfuncList.xml&quot;.

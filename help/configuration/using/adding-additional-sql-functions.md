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

# Definieren zusätzlicher SQL-Funktionen{#adding-additional-sql-functions}

Adobe Campaign ermöglicht es dem Benutzer, **seine eigenen Funktionen** zu definieren, die auf SQL-Funktionen zugreifen können, sowohl auf die Datenbankfunktionen als auch auf die Funktionen, die noch nicht in der Konsole verfügbar sind. Dies ist beispielsweise für Aggregatfunktionen (Durchschnitt, Maximum, Summe) nützlich, die nur auf dem Server berechnet werden können oder wenn die Datenbank eine einfachere Möglichkeit bietet, bestimmte Funktionen zu implementieren, anstatt den Ausdruck in der Konsole „manuell“ zu schreiben (z. B. Datumsverwaltung).

Dieser Mechanismus kann auch verwendet werden, wenn Sie eine aktuelle oder ungewöhnliche SQL-Datenbankmodul-Funktion verwenden möchten, die von der Adobe Campaign-Konsole noch nicht angeboten wird.

Nachdem diese Funktionen hinzugefügt wurden, werden sie im Ausdruckseditor wie andere vordefinierte Funktionen angezeigt.

>[!IMPORTANT]
>
>SQL-Funktionsaufrufe in der Konsole werden nicht mehr automatisch an den Server gesendet. Der hier beschriebene Mechanismus wird daher **die einzige Möglichkeit zum Aufrufen** auf dem ungeplanten SQL-Funktions-Server.

## Installation {#installation}

Die hinzuzufügenden Funktionen befinden sich in einer **„Package“-Datei im XML-Format** deren Struktur im folgenden Absatz beschrieben wird.

Um es über die Konsole zu installieren, wählen Sie die **Tools/Erweitert/**-Optionen aus dem Menü, dann **[!UICONTROL Installieren aus Datei]** und befolgen Sie die Anweisungen im Importassistenten.

>[!IMPORTANT]
>
>Warnung: Selbst wenn die Liste der importierten Funktionen sofort im Funktionseditor angezeigt wird, können sie erst nach einem Neustart von Adobe Campaign verwendet werden.

## Allgemeine Struktur des zu importierenden Pakets {#general-structure-of-package-to-import}

Die hinzuzufügenden Funktionen finden Sie in der **„package“** XML-Format. Hier ein Beispiel:

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

* Die **name**, **namespace** und **label** dienen nur zu Informationszwecken. Sie ermöglichen es, eine Zusammenfassung des Pakets in der Liste Installierte Pakete anzuzeigen (Explorer/Administration/Paketverwaltung/Installierte Pakete).
* Die Felder **buildVersion** und **buildNumber** sind obligatorisch. Sie müssen der Server-Nummer entsprechen, mit der die Konsole verbunden ist. Diese Informationen finden Sie im Feld „Hilfe/Info“.
* Die folgenden Blöcke, **Entitäten** und **funcList** sind obligatorisch. In funcList sind die Felder „name“ und „namespace“ obligatorisch, ihr Name bleibt jedoch dem Benutzer überlassen und sie bestimmen die Funktionsliste eindeutig.

  Wenn also eine weitere Liste von Funktionen mit demselben Namespace/Namenspaar (hier „cus::myList„) importiert wird, werden die zuvor importierten Funktionen gelöscht. Wenn Sie umgekehrt dieses Namespace/Name-Paar ändern, wird die neue Reihe importierter Funktionen zur vorherigen hinzugefügt.

* Mit **group**-Element können Sie die Funktionsgruppe angeben, in der die importierten Funktionen im Funktionseditor angezeigt werden. Das Attribut @name kann entweder ein bereits vorhandener Name sein (in diesem Fall werden die Funktionen der betreffenden Gruppe hinzugefügt) oder ein neuer Name (in diesem Fall wird er in einer neuen Gruppe angezeigt).
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
>Vervollständigen Sie das @label: Dies ist der Name, der in der Liste der verfügbaren Funktionen angezeigt wird. Wenn Sie nichts eingeben, hat die Gruppe keinen Namen. Wenn Sie jedoch einen anderen Namen als den vorhandenen eingeben, ändert sich der Name der gesamten Gruppe.

Wenn Sie Funktionen zu mehreren verschiedenen Gruppen hinzufügen möchten, können Sie mehrere `<group>` Elemente in derselben Liste nachverfolgen lassen.

Schließlich kann ein `<group>`-Element die Definition einer oder mehrerer Funktionen enthalten, d. h. den Zweck der Paketdatei. Die `<function>`   -Element wird im folgenden Absatz beschrieben.

## Funktionsdeskriptor &lt;function>&lt;/function> {#function-descriptor--function-}

Der hier vorgestellte Fall ist ein allgemeiner Fall, bei dem wir die **Funktionsimplementierung“ bereitstellen**.

Nachfolgend finden Sie ein Beispiel für eine Funktion „Relative Reife“, die anhand eines Alters angibt, für wie viele Jahre die Person als reif angesehen wurde.

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

Das Feld **@name** bezieht sich auf den Namen der Funktion, und „args“ ist die Liste der Parameter, die in der Beschreibung angezeigt werden. In diesem Fall wird die Funktion als „relativeMaturity ( `<age>` )“ im Funktionsauswahlfenster angezeigt.

* **Hilfe** ist das Feld, das unten im Fenster des Ausdruckseditors angezeigt wird.
* **@display** ist eine informative Nachricht.

  >[!NOTE]
  >
  >In den Attributen @help und @display steht die Zeichenfolge &quot;$1“ für den Namen, der im ersten Funktionsparameter angegeben wurde (hier „Alter„). $2, $3… würden die folgenden Parameter darstellen. Im folgenden @body bezeichnet $1 den Argumentwert, der während des Aufrufs an die Funktion übergeben wird.

  >[!NOTE]
  >
  >Die Beschreibung muss eine Zeichenfolge mit gültigen XML-Zeichen sein: Es ist zu beachten, dass &quot;&lt;&quot; und &quot;>&quot; anstelle von &lt; und > verwendet werden.

* **@type** ist der Rückgabetyp der Funktion und ein Standardwert (long, string, byte, datetime…). Wenn er ausgelassen wird, bestimmt der Server den besten Typ unter den verfügbaren Typen innerhalb des Ausdrucks, der die Funktion implementiert.
* **@minArgs** und **maxArgs** gibt die Anzahl der Parameter (Minimum und Maximum) für einen Parameter an. Für eine Funktion mit zwei Parametern sind z. B. minArgs und maxArgs 2 und 2. Bei 3 Parametern plus 1 optional sind sie 3 bzw. 4.
* Schließlich stellt das **providerPart**-Element die Funktionsimplementierung bereit.

   * Das **provider**-Attribut ist obligatorisch. Es gibt die Datenbanksysteme an, für die die Implementierung bereitgestellt wird. Wie im Beispiel gezeigt, können bei unterschiedlichen Ausdruckssyntaxen oder zugrunde liegenden Funktionen alternative Implementierungen je nach Datenbank bereitgestellt werden.
   * Das Attribut **@body** enthält die Funktionsimplementierung. Hinweis: Diese Implementierung muss ein Ausdruck in der Datenbanksprache sein (kein Code-Block). Je nach Datenbanken können Ausdrücke Unterabfragen sein („(Spalte aus Tabelle auswählen, wobei…)„), die nur einen einzigen Wert zurückgeben. Dies ist z. B. beim Oracle der Fall (die Abfrage muss in Klammern geschrieben werden).

  >[!NOTE]
  >
  >Wenn wahrscheinlich nur eine oder zwei Datenbanken von der definierten Funktion abgefragt werden, können wir immer nur die Definitionen bereitstellen, die diesen Datenbanken entsprechen.

## „Pass-Through“-Funktionsdeskriptor {#pass-through--function-descriptor}

Ein spezieller Funktionsdeskriptor ist der **„Pass-Through“**-Block mit einem nicht spezifizierten „Provider“-Datenbanksystem. In diesem Fall kann die Implementierung des „Hauptteils“ nur einen einzigen Funktionsaufruf mit einer Syntax enthalten, die nicht von der verwendeten Datenbank abhängig ist. In der Zwischenzeit ist der Block „ProviderPart“ eindeutig.

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

In diesem Fall dient das Hinzufügen einer Funktion nur dazu, eine Datenbankfunktion zu erstellen, die standardmäßig nicht verfügbar wäre und jetzt für den Client sichtbar ist.

## Beispiele {#examples}

Weitere Funktionsbeispiele finden Sie im vordefinierten Paket „xtkdatakitfuncList.xml“.

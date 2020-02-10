---
title: Implementieren von SOAP-Methoden
seo-title: Implementieren von SOAP-Methoden
description: Implementieren von SOAP-Methoden
seo-description: null
page-status-flag: never-activated
uuid: c9366f4e-460d-4087-88f7-9cc6d0de597a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 76984d9d-7759-4e0f-a275-09cca27589fa
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7ff12260d875b85256c8678fa8d100fd355398e

---


# Implementieren von SOAP-Methoden{#implementing-soap-methods}

## Einleitung {#introduction}

Es ist möglich, SOAP-Methoden in JavaScript zu erstellen. Diese Funktion ermöglicht einfach anwendbare Prozesse, sie kann die Entwicklung von JSPs und deren Aufruf in den Formularen vermeiden.

Diese SOAP-Methoden verhalten sich genauso wie die nativ in der Anwendung definierten Methoden. Die gleichen Attribute werden unterstützt: static, key only und const.

## Definieren einer Methodenbibliothek {#defining-a-method-library}

Das Erstellen einer Methodenbibliothek umfasst zwei Schritte:

* die SOAP-Methodendeklaration,
* Definition (oder Implementierung) in JavaScript.

### Erklärung {#declaration}

Erklären Sie zunächst die Methoden in den Schemata (weitere Informationen zum Erstellen und Bearbeiten von Schemata finden Sie in [diesem Abschnitt](../../configuration/using/about-schema-edition.md)).

Ihre Deklaration ähnelt der der nativen Methoden, allerdings müssen Sie das Attribut &quot;library&quot;hinzufügen, um den Namen der Methodenbibliothek anzugeben, in der sich die Definition befindet.

Dieser Name fällt mit dem Namen (mit dem Namespace) der Entität des Typs &quot;JavaScript-Code&quot;zusammen.

Beispiel:

Die Methode testLog(msg) wird in der Erweiterung nms:empfänger deklariert

```
<method name="testLog" static="true" library="cus:test">
     <parameters>
       <param name="message" type="string" inout="in"/>
     </parameters>
   </method>
```

>[!NOTE]
>
>Der Namespace und der für die Bibliothek verwendete Name sind unabhängig vom Namespace- und Schemanamen, in dem die Deklaration gefunden wird.

### Definition {#definition}

SOAP-Methoden werden in Form einer JavaScript-Funktion implementiert, die in einem Skript gruppiert ist, das eine Bibliothek darstellt.

>[!NOTE]
>
>Eine Methodenbibliothek kann Funktionen für verschiedene Schemata gruppieren oder umgekehrt, die Funktionen eines Schemas können in separaten Bibliotheken definiert werden.

Das Skript kann Code enthalten, der beim ersten Laden der Bibliothek ausgeführt wird.

**1. Name**

Der Name der Funktion muss dem folgenden Format entsprechen:

```
 <schema-namespace>_<schema-name>_<method-name>
```

Beispiel:

Die folgende JavaScript-Funktion ist die Implementierung der oben beschriebenen Methode. Sie wird in der Typentität &quot;JavaScript-Code&quot;unter Verwendung des Namens &quot;cus:test&quot;definiert.

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2. Unterschrift**

Die Signatur der Funktion muss ein Argument für jeden &#39;in&#39;- oder &#39;inout&#39;-Parameter der Deklaration enthalten.

Sonderfälle:

* **nichtstatische Methoden**: Die Funktion muss zuerst ein zusätzliches Argument enthalten, das mit der XML-Entität zusammenfällt, die in Form eines E4X-Objekts (XML) übergeben wird.
* **Typmethoden**&quot;nur Schlüssel&quot;: Die Funktion muss zuerst ein zusätzliches Argument enthalten, das mit dem in Form von Zeichenfolgen übergebenen Schlüssel übereinstimmt.

**3. Rückgegebene Werte**

Die Funktion muss einen Wert für jeden Parameter vom Typ &#39;out&#39; oder &#39;inout&#39; zurückgeben. Sonderfall: Wenn die Methode ohne die Attribute &quot;static&quot;, &quot;key only&quot;oder &quot;const&quot;deklariert wird, muss der erste zurückgegebene Wert mit der geänderten Entität übereinstimmen. Es ist möglich, ein neues Objekt zurückzugeben oder den ersten geänderten Parameter zurückzugeben.

Beispiel:

```
function nms_recipient_setLastName(self, name)
 {
   self.@lastName = name
   return self
 }
```

Wenn mehrere Werte zurückgegeben werden sollen, müssen sie in einer Tabelle angezeigt werden.

Beispiel:

```
function nms_recipient_getKey(self)
 {
   return [self.@firstName, self.@lastName]
 }
```


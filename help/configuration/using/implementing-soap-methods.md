---
product: campaign
title: Implementieren von SOAP-Methoden
description: Implementieren von SOAP-Methoden
feature: Configuration
role: Developer
exl-id: 441a0e5c-fa7f-46c8-a65a-5cca4c846d43
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 4%

---

# Implementieren von SOAP-Methoden{#implementing-soap-methods}



## Einleitung {#introduction}

Es ist möglich, SOAP-Methoden in JavaScript zu erstellen. Diese Funktion ermöglicht lediglich anwendungsbezogene Prozesse und kann die Entwicklung von JSPs und deren Aufrufen in den Formularen vermeiden.

Diese SOAP-Methoden verhalten sich auf die gleiche Weise wie die nativ im Programm definierten. Es werden die gleichen Attribute unterstützt: static, key only und const.

## Definieren einer Methodenbibliothek {#defining-a-method-library}

Das Erstellen einer Methodenbibliothek umfasst zwei Schritte:

* Die SOAP-Methodendeklaration,
* Definition (oder Implementierung) in JavaScript.

### Deklaration {#declaration}

Deklarieren Sie zunächst die Methoden in den Schemata (weitere Informationen zum Erstellen und Bearbeiten von Schemata finden Sie [&#x200B; diesem Abschnitt](../../configuration/using/about-schema-edition.md)).

Ihre Deklaration ähnelt der von nativen Methoden, mit dem Unterschied, dass Sie das Attribut „library“ hinzufügen müssen, das den Namen der Methodenbibliothek angibt, in der sich die Definition befindet.

Dieser Name entspricht dem Namen (mit dem Namespace) der Entität vom Typ &quot;JavaScript-Code“.

Beispiel:

Die Methode testLog(msg) wird in einer nms:recipient-Erweiterung deklariert

```
<method name="testLog" static="true" library="cus:test">
     <parameters>
       <param name="message" type="string" inout="in"/>
     </parameters>
   </method>
```

>[!NOTE]
>
>Der Namespace und der für die Bibliothek verwendete Name sind unabhängig von dem Namespace- und Schemanamen, in dem sich die Deklaration befindet.

### Definition {#definition}

SOAP-Methoden werden in Form von JavaScript-Funktionen implementiert, die in einem Skript gruppiert sind, das eine Bibliothek darstellt.

>[!NOTE]
>
>Eine Methodenbibliothek kann Funktionen für verschiedene Schemata gruppieren oder umgekehrt. Die Funktionen eines Schemas können in separaten Bibliotheken definiert werden.

Das Skript kann Code enthalten, der beim ersten Laden der Bibliothek ausgeführt wird.

**1. Name**

Der Name der Funktion muss dem folgenden Format entsprechen:

```
 <schema-namespace>_<schema-name>_<method-name>
```

Beispiel:

Die folgende JavaScript-Funktion ist die Implementierung der oben beschriebenen -Methode. Sie wird in der Entität vom Typ &quot;JavaScript-Code“ unter Verwendung des Namens „cus:test&quot; definiert.

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2. Signatur**

Die Signatur der Funktion muss für jeden „in“- oder „input“-Parameter der Deklaration ein Argument enthalten.

Sonderfälle:

* **Nicht statische Methoden**: Die Funktion muss zuerst ein zusätzliches Argument enthalten, das mit der XML-Entität übereinstimmt, die in Form eines Objekts vom Typ „xml“ (E4X) übergeben wird.
* **Methoden vom Typ „Nur Schlüssel**: Die Funktion muss zuerst ein zusätzliches Argument enthalten, das mit dem in Form von Zeichenfolgen übergebenen Schlüssel übereinstimmt.

**3. Zurückgegebene Werte**

Die Funktion muss für jeden Parameter vom Typ „out“ oder „inout“ einen Wert zurückgeben. Sonderfall: Wenn die Methode ohne eines der Attribute „static“, „key only“ oder „const“ deklariert wird, muss der erste zurückgegebene Wert mit der geänderten Entität übereinstimmen. Es ist möglich, ein neues -Objekt oder den ersten geänderten Parameter zurückzugeben.

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

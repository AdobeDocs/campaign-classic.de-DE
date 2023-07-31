---
product: campaign
title: Implementieren von SOAP-Methoden
description: Implementieren von SOAP-Methoden
feature: Configuration
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
exl-id: 441a0e5c-fa7f-46c8-a65a-5cca4c846d43
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 4%

---

# SOAP-Methoden implementieren{#implementing-soap-methods}



## Einleitung {#introduction}

Es ist möglich, SOAP-Methoden in JavaScript zu erstellen. Diese Funktion ermöglicht einfach anwendungsbezogene Prozesse. Sie kann die Entwicklung von JSPs und deren Aufruf in den Formularen vermeiden.

Diese SOAP-Methoden verhalten sich genauso wie die nativ in der Anwendung definierten Methoden. Es werden dieselben Attribute unterstützt: &quot;Statisch&quot;, &quot;Nur Schlüssel&quot;und &quot;const&quot;.

## Definieren einer Methodenbibliothek {#defining-a-method-library}

Das Erstellen einer Methodenbibliothek umfasst zwei Phasen:

* die SOAP-Methodendeklaration,
* Definition (oder Implementierung) in JavaScript.

### Erklärung {#declaration}

Deklarieren Sie zunächst die Methoden in den Schemas (weitere Informationen zum Erstellen und Bearbeiten von Schemas finden Sie unter [diesem Abschnitt](../../configuration/using/about-schema-edition.md)).

Ihre Deklaration ähnelt der nativen Methoden, allerdings müssen Sie das Attribut &quot;library&quot;hinzufügen, das den Namen der Methodenbibliothek angibt, in der sich die Definition befindet.

Dieser Name entspricht dem Namen (mit dem Namespace) der Entität vom Typ &quot;JavaScript-Code&quot;.

Beispiel:

Die Methode testLog(msg) wird in der Erweiterung nms:recipient deklariert

```
<method name="testLog" static="true" library="cus:test">
     <parameters>
       <param name="message" type="string" inout="in"/>
     </parameters>
   </method>
```

>[!NOTE]
>
>Der Namespace und der für die Bibliothek verwendete Name sind unabhängig vom Namespace und vom Schemanamen, in dem die Deklaration gefunden wird.

### Definition {#definition}

SOAP-Methoden werden in Form von JavaScript-Funktionen implementiert, die in einem Skript gruppiert sind, das eine Bibliothek darstellt.

>[!NOTE]
>
>Eine Methodenbibliothek kann Funktionen für verschiedene Schemas gruppieren oder umgekehrt. Die Funktionen eines Schemas können in separaten Bibliotheken definiert werden.

Das Skript kann Code enthalten, der beim ersten Laden der Bibliothek ausgeführt werden soll.

**1. Name**

Der Name der Funktion muss dem folgenden Format entsprechen:

```
 <schema-namespace>_<schema-name>_<method-name>
```

Beispiel:

Die folgende JavaScript-Funktion ist die Implementierung der oben beschriebenen Methode. Sie wird in der Entität vom Typ &quot;JavaScript-Code&quot;unter Verwendung des Namens &quot;cus:test&quot;definiert.

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2. Unterschrift**

Die Signatur der Funktion muss ein -Argument für jeden &quot;in&quot;- oder &quot;inout&quot;-Parameter der Deklaration enthalten.

Sonderfälle:

* **nicht statische Methoden**: Die Funktion muss zunächst ein zusätzliches -Argument enthalten, das mit der XML-Entität übereinstimmt, die in Form eines Objekts vom Typ &quot;xml&quot;(E4X) übergeben wurde.
* **Methoden vom Typ &quot;Nur Schlüssel&quot;**: Die Funktion muss zuerst ein zusätzliches -Argument enthalten, das mit dem in Form von Zeichenfolgen übergebenen Schlüssel übereinstimmt.

**3. Zurückgegebene Werte**

Die Funktion muss für jeden Parameter vom Typ &#39;out&#39; oder &#39;inout&#39; einen Wert zurückgeben. Sonderfall: Wenn die Methode ohne die Attribute &quot;static&quot;, &quot;key only&quot;oder &quot;const&quot;deklariert wird, muss der erste zurückgegebene Wert mit der geänderten Entität übereinstimmen. Es ist möglich, ein neues Objekt zurückzugeben oder den ersten geänderten Parameter zurückzugeben.

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

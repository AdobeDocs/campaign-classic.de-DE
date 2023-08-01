---
product: campaign
title: Schemaelemente und Attribute - Methodelement
description: Methodenelement
feature: Schema Extension
exl-id: 0fb74318-fe09-473c-8e33-1f3afd66b4cc
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 1%

---

# Methodenelement {#method--element}

![](../../../assets/v7-only.svg)

## Inhaltsmodell {#content-model-10}

Methode:==( help | Parameter)

## Attribute {#attributes-10}

* @_operation (string)
* @access (string)
* @const (boolean)
* @hidden (boolean)
* @label (string)
* @library (string)
* @name (MNTOKEN)
* @pkonly (boolean)
* @static (boolean)

## Eltern {#parents-10}

`<methods>`  ,  `<interface />`

## Untergeordnetes Element {#children-10}

* `<help>`
* `<parameters>`

## Beschreibung {#description-10}

Mit diesem Element können Sie eine SOAP-Methode definieren.

## Verwendung und Verwendungskontext {#use-and-context-of-use-7}

SOAP-Methoden ermöglichen Anwendungsprozesse.

Die &quot;@library&quot;ist für die Deklarierung einer neuen (nicht nativen) Methode erforderlich: Der Namespace und der Name, der für die Bibliothek verwendet wird, sind unabhängig vom Namespace und Namen des Schemas, in dem die Deklaration enthalten ist.

## Attributbeschreibung {#attribute-description-10}

* **access (Zeichenfolge)**: Dieses Attribut definiert die Zugriffskontrolle für die Verwendung der -Methode. Wenn dieses Attribut fehlt, ist eine Identifizierung erforderlich. Verfügbare Werte sind: &#39;anonymous&#39;, &#39;admin&#39; und &#39;sql&#39;.
* **const (boolesch)**: Wenn es aktiviert ist, bedeutet dieses Attribut, dass die deklarierte Methode die Entität ändert
* **label (string)**: Titel der Methode.
* **library (string)**: Diese Methode ist nicht nativ für die Anwendung. Dieses Attribut nimmt den Wert der Methodenbibliothek an, in der die Methodendefinition gefunden wird (nms:mylibrary.js).
* **name (MNTOKEN)**: eindeutiger Methodenname.
* **static (boolean)**: Wenn dieses Attribut aktiviert ist, wird die Methode als autonom betrachtet, alle Parameter müssen der Methode zum Zeitpunkt des Aufrufs zugewiesen werden.

## Beispiele {#examples-7}

Definition der vordefinierten Anmeldemethode:

```
 
<method name="Subscribe" static="true">
      <help>Creation of update of a recipient's subscription to an information service</help>
      <parameters>
        <param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string"/>
        <param desc="Recipient to subscribe and possibly create" name="recipient"
               type="DOMElement"/>
        <param desc="Create the recipient if they don't exist" name="create" type="boolean"/>
      </parameters>     
    </method>
```

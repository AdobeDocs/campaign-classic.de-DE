---
product: campaign
title: Elemente und Attribute
description: Elemente und Attribute
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 0fb74318-fe09-473c-8e33-1f3afd66b4cc
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 4%

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

## Übergeordnete Elemente {#parents-10}

`<methods>`  ,  `<interface />`

## Untergeordnetes Element {#children-10}

* `<help>`
* `<parameters>`

## Beschreibung {#description-10}

Mit diesem Element können Sie eine SOAP-Methode definieren.

## Verwendung und Verwendungskontext {#use-and-context-of-use-7}

SOAP-Methoden ermöglichen Anwendungsprozesse.

Die &quot;@library&quot;ist zum Deklarieren einer neuen Methode (nicht nativ) erforderlich: der Namespace und der für die Bibliothek verwendete Name sind unabhängig vom Namespace und Namen des Schemas, in dem sich die Deklaration befindet.

## Attributbeschreibung {#attribute-description-10}

* **access (string)**: Dieses Attribut definiert die Zugriffskontrolle für die Verwendung der -Methode. Wenn dieses Attribut fehlt, ist eine Identifizierung erforderlich. Verfügbare Werte sind: &#39;anonymous&#39;, &#39;admin&#39; und &#39;sql&#39;.
* **const (boolean)**: Wenn es aktiviert ist, bedeutet dieses Attribut, dass die deklarierte Methode die Entität ändert
* **label (string)**: Titel der Methode.
* **library (string)**: Diese Methode ist nicht nativ für die Anwendung. Dieses Attribut nimmt den Wert der Methodenbibliothek an, in der die Methodendefinition gefunden wird (nms:mylibrary.js).
* **name (MNTOKEN)**: eindeutiger Methodenname.
* **static (boolean)**: Wenn dieses Attribut aktiviert ist, gilt die Methode als autonom, alle Parameter müssen der Methode zum Zeitpunkt des Aufrufs zugewiesen werden.

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

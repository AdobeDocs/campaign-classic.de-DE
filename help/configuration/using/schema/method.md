---
product: campaign
title: Schemaelemente und -attribute - Methodenelement
description: Methodenelement
feature: Schema Extension
exl-id: 0fb74318-fe09-473c-8e33-1f3afd66b4cc
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 1%

---

# Methodenelement {#method--element}


## Inhaltsmodell {#content-model-10}

Method:==( Hilfe | Parameter)

## Attribute {#attributes-10}

* @_operation (Zeichenfolge)
* @access (Zeichenfolge)
* @const (Boolesch)
* @hidden (Boolesch)
* @label (Zeichenfolge)
* @library (Zeichenfolge)
* @name (MNTOKEN)
* @pkonly (Boolesch)
* @static (Boolesch)

## Übergeordnete Elemente {#parents-10}

`<methods>` , `<interface />`

## Untergeordnetes Element {#children-10}

* `<help>`
* `<parameters>`

## Beschreibung {#description-10}

Mit diesem Element können Sie eine SOAP-Methode definieren.

## Verwendung und Nutzungskontext {#use-and-context-of-use-7}

SOAP-Methoden ermöglichen Anwendungsprozesse.

Das &quot;@library“ ist für die Deklaration einer neuen Methode (nicht nativ) erforderlich: Der Namespace und der für die Bibliothek verwendete Name sind unabhängig vom Namespace und vom Namen des Schemas, in dem sich die Deklaration befindet.

## Attributbeschreibung {#attribute-description-10}

* **access (Zeichenfolge)** Dieses Attribut definiert die Zugriffssteuerung für die Verwendung der Methode. Wenn dieses Attribut fehlt, ist eine Identifizierung obligatorisch. Verfügbare Werte sind: „anonym“, „admin“ und „sql“.
* **const (Boolesch)**: Wenn es aktiviert ist, bedeutet dieses Attribut, dass die deklarierte Methode die Entität ändert
* **label (Zeichenfolge)**: Bezeichnung der Methode.
* **Library (String)**: Diese Methode ist nicht programmspezifisch. Dieses Attribut übernimmt den Wert der Methodenbibliothek, in der sich die Methodendefinition befindet (nms:mylibrary.js).
* **name (MNTOKEN)**: Eindeutiger Methodenname.
* **static (boolean)**: Wenn dieses Attribut aktiviert ist, wird die Methode als autonom betrachtet, alle Parameter müssen für die Methode beim Aufruf angegeben werden.

## Beispiele {#examples-7}

Definition der vorkonfigurierten Methode „Subscribe“:

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

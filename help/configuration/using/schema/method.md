---
product: campaign
title: Schemaelemente und -attribute - Methodenelement
description: Methodenelement
feature: Schema Extension
exl-id: 0fb74318-fe09-473c-8e33-1f3afd66b4cc
TQID: 'https://experienceleague.adobe.com/GaT6bmWzojcbk8-XjCoqrMv2-02aoxv1cIXM0E0Y0UU'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 2%
---
# Methodenelement {#method--element}


## Inhaltsmodell {#content-model-10}

Methode:==( Hilfe | Parameter)

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

`<methods>`  ,  `<interface />`

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

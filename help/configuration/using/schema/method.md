---
solution: Campaign Classic
product: campaign
title: Elemente und Attribute
description: Elemente und Attribute
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 4%

---


# method element {#method--element}

## Inhaltsmodell {#content-model-10}

Methode:==( help | Parameter)

## Attribute {#attributes-10}

* @_operation (Zeichenfolge)
* @access (Zeichenfolge)
* @const (boolean)
* @hidden (boolean)
* @label (Zeichenfolge)
* @library (string)
* @name (MNTOKEN)
* @pkonly (boolean)
* @static (boolean)

## Eltern {#parents-10}

`<methods>`  ,  `<interface />`

## Kinder {#children-10}

* `<help>`
* `<parameters>`

## Beschreibung {#description-10}

Mit diesem Element können Sie eine SOAP-Methode definieren.

## Verwendung und Kontext der Verwendung von {#use-and-context-of-use-7}

SOAP-Methoden ermöglichen Anwendungsprozesse.

Die &quot;@library&quot;ist erforderlich, um eine neue Methode zu deklarieren (nicht native): der Namensraum und der Bibliotheksname sind unabhängig vom Namensraum und vom Namen des Schemas, in dem die Deklaration enthalten ist.

## Attributbeschreibung {#attribute-description-10}

* **access (Zeichenfolge)**: Dieses Attribut definiert die Zugriffskontrolle für die Verwendung der Methode. Wenn dieses Attribut fehlt, ist die Identifizierung obligatorisch. Verfügbare Werte sind: &#39;anonymous&#39;, &#39;admin&#39; und &#39;sql&#39;.
* **const (boolean)**: Wenn es aktiviert ist, bedeutet dieses Attribut, dass die deklarierte Methode die Entität ändert
* **label (Zeichenfolge)**: Bezeichnung der Methode.
* **library (string)**: Diese Methode ist nicht nativ für die Anwendung. Dieses Attribut nimmt den Wert der Methodenbibliothek ein, in der die Methodendefinition gefunden wird (nms:mylibrary.js).
* **name (MNTOKEN)**: eindeutiger Methodenname.
* **statisch (boolean)**: Wenn dieses Attribut aktiviert ist, wird die Methode als autonom betrachtet, müssen alle Parameter bei Aufruf der Methode angegeben werden.

## Beispiele {#examples-7}

Definition der Out-of-the-Box-Methode &quot;Abonnieren&quot;:

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

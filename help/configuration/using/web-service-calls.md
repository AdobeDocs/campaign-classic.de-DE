---
product: campaign
title: Web-Dienstaufrufe
description: Web-Dienstaufrufe
feature: API
role: Data Engineer, Developer
exl-id: ce94e7e7-b8f8-4c82-937f-e87d15e50c34
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 1%

---

# Web-Dienstaufrufe{#web-service-calls}

## Allgemeine Informationen {#general-information}

Alle API-Methoden werden in Form von Webdiensten dargestellt. Auf diese Weise können Sie alle Adobe Campaign-Funktionen über SOAP -Aufrufe verwalten, die den nativen Einstiegspunkt des Adobe Campaign-Anwendungsservers bilden. Die Adobe Campaign-Konsole selbst verwendet nur SOAP Aufrufe.

Mit Webdiensten können Sie viele Anwendungen aus einem Drittanbietersystem erstellen:

* synchrone Warnhinweise, Benachrichtigungen und Ausführung von Versandvorlagen in Echtzeit von einem Back-Office- oder Transaktionssystem aus;
* Entwicklung spezieller Schnittstellen mit vereinfachter Funktionalität (Webschnittstellen usw.),
* Fütterung und Suche von Daten in der Datenbank unter Beachtung von Handelsregeln und isoliert von dem zugrunde liegenden physischen Modell.

## Definition von Webdiensten {#definition-of-web-services}

Die Definition der auf dem Adobe Campaign-Anwendungsserver implementierten Webdienste ist in den Datenschemata verfügbar.

Ein Webdienst wird in der Grammatik der Datenschemata beschrieben und ist im Element **`<methods>`** verfügbar.

```
<methods>
  <method name="GenerateForm" static="true">
    <help>Generates the form in Mail or Web mode</help>
    <parameters>
      <param name="formName" type="string" desc="Name of form"/>
      <param name="mailMode" type="boolean" desc="Generate a form of type Mail"/>
      <param name="result" type="string" inout="out" desc="Result "/>
    </parameters>
  </method>
</methods>
```

Hier finden Sie ein Beispiel für die Definition der Methode **GenerateForm**.

Die Beschreibung des Dienstes beginnt mit dem Element `<method>` . Die Liste der Parameter der Methode wird aus dem Element `<parameters>` ausgefüllt. Jeder Parameter wird durch einen Namen, einen Typ (Boolesch, Zeichenfolge, DOMElement usw.) und eine Beschreibung. Mit dem Attribut &quot;inout&quot;mit dem Wert &quot;out&quot;können Sie angeben, dass sich der Parameter &quot;result&quot;in der SOAP-Aufrufausgabe befindet.

Das Attribut &quot;static&quot;(mit dem Wert &quot;true&quot;) beschreibt diese Methode als statisch, d. h., alle Parameter der Methode müssen deklariert werden.

Eine &quot;const&quot;-Methode hat implizit ein XML-Dokument im Format seines zugehörigen Schemas als Eingabe.

Eine vollständige Beschreibung des Elements `<method>` eines Adobe Campaign-Schemas finden Sie im Kapitel &quot;Schema references&quot;unter [Method](../../configuration/using/schema/method.md)

Beispiel der Methode &quot;const&quot;-type &quot;ExecuteQuery&quot; aus dem Schema &quot;xtk:queryDef&quot;:

```
<method name="ExecuteQuery" const="true">
  <help>Retrieve data from a query</help>
  <parameters>
    <param desc="Output xml document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

Der Eingabeparameter dieser Methode ist ein XML-Dokument im Format des Schemas &quot;xtk:queryDef&quot;.

## Webdienstbeschreibung: WSDL {#web-service-description--wsdl}

Für jeden Dienst ist eine WSDL-Datei (Web Service Description Library) verfügbar. Diese XML-Datei verwendet eine Metalsprache, um den Dienst zu beschreiben und die verfügbaren Methoden, Parameter und den Server anzugeben, die für die Ausführung des Dienstes kontaktiert werden sollen.

### WSDL-Dateigenerierung {#wsdl-file-generation}

Um eine WSDL-Datei zu generieren, müssen Sie die folgende URL in einem Webbrowser eingeben:

https://`<server>`/nl/jsp/schemawsdl.jsp?schema=`<schema>`

Mit:

* **`<server>`**: der Adobe Campaign-Anwendungsserver (nlserver web)
* **`<schema>`**: Schemaidentifizierungsschlüssel (namespace:schema_name)

### Beispiel für die Methode &#39;ExecuteQuery&#39; des Schemas &#39;xtk:queryDef&#39; {#example-on-the--executequery--method-of-schema--xtk-querydef-}

Die WSDL-Datei wird über die URL generiert:

`https://localhost/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef`

Eine WSDL-Beschreibung beginnt mit der Definition der Typen, die zum Erstellen von Nachrichten verwendet werden, die mit &quot;Ports&quot;verknüpft sind, die mit einem Protokoll verbunden sind, indem &quot;Bindungen&quot;Webdienste bilden.

#### Typen {#types}

Typdefinitionen basieren auf XML-Schemata. In unserem Beispiel nimmt die Methode &quot;ExecuteQuery&quot;eine Zeichenfolge &quot;s:string&quot;und ein XML-Dokument (`<s:complextype>`) als Parameter an. Der Rückgabewert der Methode (&quot;ExecuteQueryResponse&quot;) ist ein XML-Dokument ( `<s:complextype>`).

```
<types>
<s:schema elementFormDefault="qualified" targetNamespace="urn:xtk:queryDef">
  <s:element name="ExecuteQuery">
    <s:complexType>
      <s:sequence>
        <s:element maxOccurs="1" minOccurs="1" name="sessiontoken" type="s:string"/>
        <s:element maxOccurs="1" minOccurs="1" name="entity">
          <s:complexType>
            <s:sequence>
              <s:any/>
            </s:sequence>
          </s:complexType>
        </s:element>
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:element name="ExecuteQueryResponse">
    <s:complexType>
      <s:sequence>
        <s:element maxOccurs="1" minOccurs="1" name="pdomOutput">
          <s:complexType mixed="true">
            <s:sequence>
              <s:any/>
            </s:sequence>
          </s:complexType>
        </s:element>
      </s:sequence>
    </s:complexType>
  </s:element>
```

#### Nachrichten {#messages}

Der `<message>` beschreibt die Namen und Typen eines Satzes von zu sendenden Feldern. Die Methode verwendet zwei Nachrichten, die als Parameter (&quot;ExecuteQueryIn&quot;) und als Rückgabewert (&quot;ExecuteQueryOut&quot;) übergeben werden.

```
<message name="ExecuteQueryIn">
  <part element="tns:ExecuteQuery" name="parameters"/>
</message>

<message name="ExecuteQueryOut">
  <part element="tns:ExecuteQueryResponse" name="parameters"/>
</message> 
```

#### PortType {#porttype}

Der `<porttype>` verknüpft die Nachrichten mit dem Vorgang &quot;ExecuteQuery&quot;, der durch die Abfrage (&quot;input&quot;) ausgelöst wird, die eine Antwort generiert (&quot;output&quot;).

```
<portType name="queryDefMethodsSoap">
  <operation name="ExecuteQuery">
    <input message="tns:ExecuteQueryIn"/>
    <output message="tns:ExecuteQueryOut"/>
  </operation>
</portType>
```

#### Bindung {#binding}

Der Teil `<binding>` gibt das SOAP Kommunikationsprotokoll ( `<soap:binding>` ), den Datentransport in HTTP (Wert des Attributs &quot;transport&quot;) und das Datenformat für den Vorgang &quot;ExecuteQuery&quot; an. Der Hauptteil des SOAP Umschlags enthält die Nachrichtensegmente direkt ohne Umwandlung.

```
<binding name="queryDefMethodsSoap" type="tns:queryDefMethodsSoap">
  <soap:binding style="document" transport="http://schemas.xmlsoap.org/soap/http"/>
  <operation name="ExecuteQuery">
    <soap:operation soapAction="xtk:queryDef#ExecuteQuery" style="document"/>
    <input>
      <soap:body encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:xtk:queryDef" use="literal"/>
    </input>
    <output>
      <soap:body encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:xtk:queryDef" use="literal"/>
    </output>
  </operation>
</binding>
```

#### Service {#service}

Der Abschnitt &quot;`<service>`&quot;beschreibt den Dienst &quot;XtkQueryDef&quot;mit seinem URI auf der URL des Adobe Campaign-Anwendungsservers.

```
<service name="XtkQueryDef">
  <port binding="tns:queryDefMethodsSoap" name="queryDefMethodsSoap">
    <soap:address location="https://localhost/nl/jsp/soaprouter.jsp"/>
  </port>
</service>
```

## Konnektivität {#connectivity}

Adobe Campaign hat die Sicherheit für Authentifizierungsmechanismen erhöht, indem [Sicherheitszonen](../../installation/using/security-zones.md) und Sitzungsverwaltungseinstellungen eingeführt wurden.

Es stehen zwei Authentifizierungsmodi zur Verfügung:

* **über einen Aufruf an logon method()**. Dieser Modus generiert ein Sitzungstoken und ein Sicherheits-Token. Dies ist der sicherste Modus und daher der am besten empfohlene.

oder

* **über die Adobe Campaign-Anmeldung + Passwort**, die ein Sitzungstoken erstellt. Das Sitzungstoken läuft nach einem festgelegten Zeitraum automatisch ab. Dieser Modus wird nicht empfohlen und erfordert eine Reduzierung der Sicherheitseinstellungen der Anwendung für einige Zoneneinstellungen (allowUserPassword=&quot;true&quot; und sessionTokenOnly=&quot;true&quot;).

### Eigenschaften des Sitzungstokens {#session-token-characteristics}

Das Sitzungstoken weist die folgenden Merkmale auf:

* X-Stunden-Lebenszyklus (der Lebenszyklus ist in der Datei &quot;serverConf.xml&quot;konfigurierbar, der Standardzeitraum beträgt 24 Stunden)
* eine zufällige Konstruktion (sie enthält nicht mehr die Benutzeranmeldung und das Kennwort)
* beim Zugriff über das Internet:

   * wird das Sitzungs-Token zu einem permanenten Token, es wird nicht mehr zerstört, sobald der Browser geschlossen wird.
   * es wird in einem HTTP-NUR-Cookie platziert (Cookies müssen für Benutzer aktiviert werden)

### Eigenschaften des Sicherheits-Tokens {#security-token-characteristics}

Das Security-Token weist die folgenden Merkmale auf:

* wird aus dem Sitzungstoken generiert
* Er hat einen Lebenszyklus von 24 Stunden (konfigurierbar in der Datei &quot;serverConf.xml&quot;, der Standardzeitraum beträgt 24 Stunden).
* wird in der Adobe Campaign-Konsole gespeichert
* beim Zugriff über das Internet:

   * in einem Dokument gespeichert.__securityToken-Eigenschaft
   * die Seiten-URLs aktualisiert werden, um das Security-Token zu aktualisieren
   * Die Formulare werden auch über ein ausgeblendetes Feld mit dem Token aktualisiert.

#### Bewegung des Sicherheits-Tokens {#security-token-movement}

Der Zugriff über die Konsole erfolgt wie folgt:

* wird in der Anmeldeantwort übertragen (im HTTP-Header)
* wird in jeder Abfrage verwendet (im HTTP-Header)

Von einer POST und GET HTTP:

* der Server schließt die Links mit dem Token ab
* Der Server fügt ein ausgeblendetes Feld zu Formularen hinzu

Bei einem SOAP-Aufruf:

* wird hinzugefügt, um Kopfzeilen aufzurufen

### Aufrufbeispiele {#call-examples}

* Verwenden von **HttpSoapConnection/SoapService**:

```
  
    var cnx = new HttpSoapConnection("https://serverURL/nl/jsp/soaprouter.jsp");
  var session = new SoapService(cnx, 'urn:xtk:session');
  session.addMethod("Logon", "xtk:session#Logon",
                      ["sessiontoken", "string", "Login", "string", "Password", "string", "Parameters", "NLElement"],
                      ["sessionToken", "string", "sessionInfo", "NLElement", "securityToken", "string"]);
  
  var res = session.Logon("", "admin", "pwd", <param/>);
  var sessionToken = res[0];
  var securityToken = res[2];
  
  cnx.addTokens(sessionToken, securityToken);
  var query = new SoapService(cnx, 'urn:xtk:queryDef');
  query.addMethod("ExecuteQuery", "xtk:queryDef#ExecuteQuery",
                      ["sessiontoken", "string", "entity", "NLElement"],
                      ["res", "NLElement"]);
  
  var queryRes = query.ExecuteQuery("", <queryDef operation="select" schema="nms:recipient">
            <select>
              <node expr="@email"/>
              <node expr="@lastName"/>
              <node expr="@firstName"/>
            </select>
            <where>
              <condition expr="@email = 'joe.doe@aol.com'"/>
            </where>
          </queryDef>);
  logInfo(queryRes[0].toXMLString())
```

* Verwenden von **HttpServletRequest**:

>[!NOTE]
>
>Die URLs, die in den folgenden **HttpServletRequest** -Aufrufen verwendet werden, müssen im Abschnitt &quot;URL-Berechtigungen&quot;der Datei **serverConf.xml** auf Zulassungsliste sein. Dies gilt auch für die URL des Servers selbst.

Logon execution():

```
var req = new HttpClientRequest("https://serverURL/nl/jsp/soaprouter.jsp");
req.header["Content-Type"] = "text/xml; charset=utf-8";
req.header["SOAPAction"] =   "xtk:session#Logon";
req.method = "POST";
req.body = '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:xtk:session">' +
    '<soapenv:Header/>' +
    '<soapenv:Body>' +
        '<urn:Logon>' +
            '<urn:sessiontoken></urn:sessiontoken>' +
            '<urn:strLogin>LOGIN_HERE</urn:strLogin>' +
            '<urn:strPassword>PASSWORD_HERE</urn:strPassword>' +
            '<urn:elemParameters></urn:elemParameters>' +
        '</urn:Logon>' +
    '</soapenv:Body>' +
'</soapenv:Envelope>';
req.execute();
           
var resp = req.response;
var xmlRes = new XML(String(resp.body).replace("<?xml version='1.0'?>",""));
var sessionToken = String(xmlRes..*::pstrSessionToken);;
var securityToken = String(xmlRes..*::pstrSecurityToken);
```

Ausführung der Abfrage:

```
var req2 = new HttpClientRequest("https://serverURL/nl/jsp/soaprouter.jsp");
req2.header["Content-Type"] = "text/xml; charset=utf-8";
req2.header["SOAPAction"] =   "xtk:queryDef#ExecuteQuery";req2.header["X-Security-Token"] = securityToken;
req2.header["cookie"]           = "__sessiontoken="+sessionToken;
req2.method = "POST";
req2.body = '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:xtk:queryDef">' +
             '<soapenv:Header/><soapenv:Body><urn:ExecuteQuery><urn:sessiontoken/><urn:entity>' +
                '<queryDef operation="select" schema="nms:recipient">' +
                  '<select><node expr="@email"/><node expr="@lastName"/><node expr="@firstName"/></select>' +
                  '<where><condition expr="@email = \'john.doe@aol.com\'"/></where>' +
                '</queryDef>' +
           '</urn:entity></urn:ExecuteQuery></soapenv:Body></soapenv:Envelope>';
req2.execute();
var resp2 = req2.response;
logInfo(resp2.body)
```

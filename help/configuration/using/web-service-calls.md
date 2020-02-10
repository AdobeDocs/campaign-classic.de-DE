---
title: Webdienstaufrufe
seo-title: Webdienstaufrufe
description: Webdienstaufrufe
seo-description: null
page-status-flag: never-activated
uuid: 7defe0e4-bb4a-4f6a-b6e8-e2ffac73b4c1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 6934c165-6d27-4ce5-8607-170f299b4702
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a527f246c4b0bf84c2a83e8df74b7a92542fda7a

---


# Webdienstaufrufe{#web-service-calls}

## Allgemeine Informationen {#general-information}

Alle API-Methoden werden in Form von Webdiensten dargestellt. Auf diese Weise können Sie alle Adobe Campaign-Funktionen über SOAP-Aufrufe verwalten, die den nativen Einstiegspunkt des Adobe Campaign-Anwendungsservers darstellen. Die Adobe Campaign-Konsole selbst verwendet nur SOAP-Aufrufe.

Mit Webdiensten können Sie viele Anwendungen aus einem Drittanbietersystem erstellen:

* synchrone Warnhinweise, Benachrichtigungen und die Ausführung von Vorlagen für die Bereitstellung in Echtzeit über eine Backoffice- oder Transaktionszentrale,
* Entwicklung spezieller Schnittstellen mit vereinfachten Funktionen (Webschnittstellen usw.),
* Fütterung und Suche von Daten in der Datenbank unter Einhaltung von Handelsregeln und isoliert von dem zugrunde liegenden physischen Modell.

## Definition von Webdiensten {#definition-of-web-services}

Die Definition der auf dem Adobe Campaign-Anwendungsserver implementierten Webdienste ist in den Datenschemata verfügbar.

Ein Webdienst wird in der Grammatik der Datenschemata beschrieben und ist über das **`<methods>`** Element verfügbar.

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

Hier haben wir ein Beispiel für die Definition der Methode namens **GenerateForm**.

Die Beschreibung des Dienstes beginnt mit dem `<method>` Element. Die Liste der Parameter der Methode wird vom `<parameters>` Element abgeschlossen. Jeder Parameter wird durch einen Namen, einen Typ (Boolescher Wert, Zeichenfolge, DOMElement usw.) angegeben. und eine Beschreibung. Mit dem Attribut &quot;inout&quot;mit dem Wert &quot;out&quot;können Sie angeben, dass sich der Parameter &quot;result&quot;in der SOAP-Aufrufausgabe befindet.

Das Vorhandensein des Attributs &quot;static&quot;(mit dem Wert &quot;true&quot;) beschreibt diese Methode als statisch, d. h. alle Parameter der Methode müssen deklariert werden.

Eine &quot;const&quot;-Methode verfügt implizit über ein XML-Dokument im Format des zugehörigen Schemas als Eingabe.

Eine vollständige Beschreibung des `<method>` Elements eines Adobe Campaign-Schemas finden Sie im Kapitel &quot;Schemaverweise&quot;unter <a href="../../configuration/using/elements-and-attributes.md#method--element" target="_blank">  `<method>`    Element.

Beispiel der Methode &quot;const&quot;-Typ &quot;ExecuteQuery&quot; aus dem Schema &quot;xtk:queryDef&quot;:

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

Für jeden Dienst steht eine WSDL-Datei (Web Service Description Library) zur Verfügung. Diese XML-Datei verwendet eine Metalsprache, um den Dienst zu beschreiben und die verfügbaren Methoden, Parameter und den Server anzugeben, der zum Ausführen des Dienstes kontaktiert werden soll.

### WSDL-Dateigenerierung {#wsdl-file-generation}

Um eine WSDL-Datei zu erstellen, müssen Sie die folgende URL aus einem Webbrowser eingeben:

[https://`<server>`/nl/jsp/schemawsdl.jsp?schema=`<schema>`

Mit:

* **`<server>`**: Adobe Campaign-Anwendungsserver (nlserver web)
* **`<schema>`**: Schemaidentifizierungsschlüssel (namespace:schema_name)

### Beispiel für die Methode &#39;ExecuteQuery&#39; des Schemas &#39;xtk:queryDef&#39; {#example-on-the--executequery--method-of-schema--xtk-querydef-}

Die WSDL-Datei wird aus der URL generiert:

[https://localhost/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef](https://my_serveur/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef)

Eine WSDL-Beschreibung beginnt mit der Definition der Typen, die verwendet werden, um Nachrichten zu bilden, die in &quot;Ports&quot; verknüpft sind, verbunden mit einem Protokoll durch &quot;Bindungen&quot;, die Webdienste bilden.

#### Typen {#types}

Typdefinitionen basieren auf XML-Schemata. In unserem Beispiel nimmt die Methode &quot;ExecuteQuery&quot;die Zeichenfolge &quot;s:string&quot;und ein XML-Dokument (`<s:complextype>`) als Parameter an. Der Rückgabewert der Methode (&quot;ExecuteQueryResponse&quot;) ist ein XML-Dokument ( `<s:complextype>`).

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

Die `<message>` beschreibt die Namen und Typen eines Satzes von Feldern, die gesendet werden sollen. Die Methode verwendet zwei Meldungen, die als Parameter (&quot;ExecuteQueryIn&quot;) und als Rückgabewert (&quot;ExecuteQueryOut&quot;) übergeben werden.

```
<message name="ExecuteQueryIn">
  <part element="tns:ExecuteQuery" name="parameters"/>
</message>

<message name="ExecuteQueryOut">
  <part element="tns:ExecuteQueryResponse" name="parameters"/>
</message> 
```

#### PortType {#porttype}

Die `<porttype>` verknüpfte die Meldungen des Vorgangs &quot;ExecuteQuery&quot;, der durch die Abfrage (&quot;Eingabe&quot;) ausgelöst wird, die eine Antwort (&quot;Ausgabe&quot;) generiert.

```
<portType name="queryDefMethodsSoap">
  <operation name="ExecuteQuery">
    <input message="tns:ExecuteQueryIn"/>
    <output message="tns:ExecuteQueryOut"/>
  </operation>
</portType>
```

#### Bindung {#binding}

Der `<binding>` Teil gibt das SOAP-Kommunikationsprotokoll ( `<soap:binding>` ), den Datentransport in HTTP (Wert des Attributs &quot;transport&quot;) und das Datenformat für den Vorgang &quot;ExecuteQuery&quot; an. Der Text des SOAP-Umschlags enthält die Meldungssegmente direkt ohne Transformation.

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

Der `<service>` Teil beschreibt den Dienst &quot;XtkQueryDef&quot;mit seinem URI auf der URL des Adobe Campaign-Anwendungsservers.

```
<service name="XtkQueryDef">
  <port binding="tns:queryDefMethodsSoap" name="queryDefMethodsSoap">
    <soap:address location="https://localhost/nl/jsp/soaprouter.jsp"/>
  </port>
</service>
```

## Konnektivität {#connectivity}

Adobe Campaign hat die Sicherheit für Authentifizierungsmechanismen erhöht, indem Sicherheitszonen (siehe Kapitel **Definieren von Sicherheitszonen** in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#defining-security-zones)) sowie Sitzungsverwaltungseinstellungen eingeführt wurden.

Es stehen zwei Authentifizierungsmodi zur Verfügung:

* **über einen Aufruf der Anmeldemethode()**. Dieser Modus generiert ein Sitzungstoken und ein Sicherheitstoken. Es ist der sicherste Modus und daher der am meisten empfohlen.

oder

* **über die Adobe Campaign-Anmeldung + das Kennwort** , mit dem ein Sitzungstoken erstellt wird. Das Sitzungstoken läuft nach einem bestimmten Zeitraum automatisch ab. Dieser Modus wird nicht empfohlen und erfordert eine Reduzierung der Anwendungssicherheitseinstellungen für einige Zoneneinstellungen (allowUserPassword=&quot;true&quot; und sessionTokenOnly=&quot;true&quot;).

### Merkmale des Sitzungstokens {#session-token-characteristics}

Das Sitzungstoken weist die folgenden Merkmale auf:

* eine X-Stunden-Lebensdauer (der Lebenszyklus ist in der Datei &quot;serverConf.xml&quot;konfigurierbar, der Standardzeitraum ist 24 Stunden)
* eine zufällige Konstruktion (sie enthält nicht mehr die Benutzeranmeldung und das Kennwort)
* beim Zugriff über das Web:

   * Wenn das Sitzungs-Token ein permanentes Token wird, wird es nicht zerstört, sobald der Browser geschlossen wird
   * es wird in einem HTTP-ONLY-Cookie platziert (Cookies müssen für Operatoren aktiviert werden)

### Eigenschaften von Sicherheitstoken {#security-token-characteristics}

Das Sicherheits-Token weist folgende Merkmale auf:

* es wird aus dem Sitzungstoken generiert
* es hat einen 24-Stunden-Lebenszyklus (konfigurierbar in der Datei &quot;serverConf.xml&quot;, der Standardzeitraum ist 24 Stunden)
* es wird in der Adobe Campaign-Konsole gespeichert
* beim Zugriff über das Web:

   * es wird in einem Dokument gespeichert.__securityToken-Eigenschaft
   * die Seiten-URLs aktualisiert werden, um das Sicherheitstoken zu aktualisieren
   * die Formulare auch über ein unsichtbares Feld mit dem Token aktualisiert werden

#### Bewegung des Sicherheits-Tokens {#security-token-movement}

Beim Zugriff über die Konsole ist dies:

* gesendet in der Anmeldeantwort (im HTTP-Header)
* verwendet in jeder Abfrage (im HTTP-Header)

Von einem POST und GET HTTP:

* der Server schließt die Verknüpfungen mit dem Token ab
* der Server ein unsichtbares Feld zu Formularen hinzufügt

Aus einem SOAP-Aufruf:

* hinzugefügt, um Header aufzurufen

### Beispiele {#call-examples}

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
>Die in den folgenden **HttpServletRequest** -Aufrufen verwendeten URLs müssen im Abschnitt &quot;URL-Berechtigungen&quot;der Datei &quot; **serverConf.xml** &quot;in die Positivliste aufgenommen werden. Dies gilt auch für die URL des Servers selbst.

Anmeldeausführung():

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

Abfrageausführung:

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


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

Alle API-Methoden werden in Form von Web-Services präsentiert. Dadurch können Sie alle Adobe Campaign-Funktionen über SOAP-Aufrufe verwalten, die den nativen Einstiegspunkt des Adobe Campaign-Anwendungsservers bilden. Die Adobe Campaign-Konsole selbst verwendet nur SOAP-Aufrufe.

Mit Webservices können Sie viele Anwendungen aus einem Drittanbietersystem erstellen:

* synchrone Warnhinweise, Benachrichtigungen und die Ausführung von Versandvorlagen in Echtzeit über ein Back-Office- oder Transaktionssystem,
* Entwicklung spezieller Schnittstellen mit vereinfachter Funktionalität (Web-Schnittstellen usw.),
* Einspeisung und Suche von Daten in der Datenbank unter Einhaltung der Handelsregeln und isolierter Nutzung des zugrunde liegenden physischen Modells.

## Definition von Web-Services {#definition-of-web-services}

Die Definition der auf dem Adobe Campaign-Anwendungsserver implementierten Webservices ist in den Datenschemata verfügbar.

Ein Webdienst wird in der Grammatik der Datenschemata beschrieben und ist über das **`<methods>`** verfügbar.

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

Hier sehen Sie ein Beispiel für die Definition der Methode namens **GenerateForm**.

Die Beschreibung des Dienstes beginnt mit dem `<method>`. Die Liste der Parameter der -Methode wird aus dem `<parameters>`-Element vervollständigt. Jeder Parameter wird durch einen Namen, einen Typ (Boolesch, Zeichenfolge, DOMElement usw.) und eine Beschreibung angegeben. Mit dem Attribut „inout“ mit dem Wert „out“ können Sie angeben, dass sich der Parameter „result“ an der SOAP-Aufrufausgabe befindet.

Das Vorhandensein des Attributs „static“ (mit dem Wert „true„) beschreibt diese Methode als statisch, was bedeutet, dass alle Parameter der Methode deklariert werden müssen.

Eine „const“-Methode verfügt implizit über ein XML-Dokument im Format des zugehörigen Schemas als Eingabe.

Eine vollständige Beschreibung des `<method>` eines Adobe Campaign-Schemas finden Sie im Kapitel „Schemaverweise“ unter [Methode](../../configuration/using/schema/method.md)

Beispiel der Methode „ExecuteQuery“ vom Typ „const“ aus dem Schema „xtk:queryDef“:

```
<method name="ExecuteQuery" const="true">
  <help>Retrieve data from a query</help>
  <parameters>
    <param desc="Output xml document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

Der Eingabeparameter dieser Methode ist ein XML-Dokument im Format des Schemas „xtk:queryDef“.

## Webdienst-Beschreibung: WSDL {#web-service-description--wsdl}

Für jeden Service ist eine WSDL-Datei (Web Service Description Library) verfügbar. Diese XML-Datei verwendet eine Metasprache, um den Service zu beschreiben und die verfügbaren Methoden, Parameter und den Server anzugeben, an den der Service ausgeführt werden soll.

### Generieren einer WSDL-Datei {#wsdl-file-generation}

Um eine WSDL-Datei zu generieren, müssen Sie die folgende URL aus einem Webbrowser eingeben:

https://`<server>`/nl/jsp/schemawsdl.jsp?schema=`<schema>`

Mit:

* **`<server>`**: Der Adobe Campaign-Anwendungsserver (nlserver web)
* **`<schema>`**: Schema-Identifizierungsschlüssel (namespace:schema_name)

### Beispiel für die Methode „ExecuteQuery“ des Schemas „xtk:queryDef“ {#example-on-the--executequery--method-of-schema--xtk-querydef-}

Die WSDL-Datei wird aus der URL generiert:

`https://localhost/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef`

Eine WSDL-Beschreibung beginnt mit der Definition der Typen, die zum Erstellen von Nachrichten verwendet werden, die in „Ports“ zugeordnet sind und durch „Bindungen“, die Webdienste bilden, mit einem Protokoll verbunden sind.

#### Typen {#types}

Typdefinitionen basieren auf XML-Schemata. In unserem Beispiel akzeptiert die Methode „ExecuteQuery“ eine Zeichenfolge „s:string“ und ein XML-Dokument (`<s:complextype>`) als Parameter. Der Rückgabewert der Methode („ExecuteQueryResponse„) ist ein XML-Dokument ( `<s:complextype>`).

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

Die `<message>` beschreibt die Namen und Typen eines Satzes von zu sendenden Feldern. Die Methode verwendet zwei Meldungen, die als Parameter („ExecuteQueryIn„) und als Rückgabewert („ExecuteQueryOut„) übergeben werden.

```
<message name="ExecuteQueryIn">
  <part element="tns:ExecuteQuery" name="parameters"/>
</message>

<message name="ExecuteQueryOut">
  <part element="tns:ExecuteQueryResponse" name="parameters"/>
</message> 
```

#### PortType {#porttype}

Die `<porttype>` verknüpft die Nachrichten mit dem Vorgang „ExecuteQuery“, der durch die Abfrage („Eingabe„) ausgelöst wird, die eine Antwort („Ausgabe„) generiert.

```
<portType name="queryDefMethodsSoap">
  <operation name="ExecuteQuery">
    <input message="tns:ExecuteQueryIn"/>
    <output message="tns:ExecuteQueryOut"/>
  </operation>
</portType>
```

#### Bindung {#binding}

Der `<binding>` Teil spezifiziert das SOAP-Kommunikationsprotokoll ( `<soap:binding>` ), den Datentransport in HTTP (Wert des Attributs „transport„) und das Datenformat für den Vorgang „ExecuteQuery“. Der Hauptteil der SOAP-Hülle enthält die Nachrichtensegmente direkt ohne Umwandlung.

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

Der `<service>` Teil beschreibt den Service „XtkQueryDef“ mit dem URI auf der URL des Adobe Campaign-Anwendungsservers.

```
<service name="XtkQueryDef">
  <port binding="tns:queryDefMethodsSoap" name="queryDefMethodsSoap">
    <soap:address location="https://localhost/nl/jsp/soaprouter.jsp"/>
  </port>
</service>
```

## Konnektivität {#connectivity}

Adobe Campaign hat die Sicherheit für Authentifizierungsmechanismen durch die Einführung von [Sicherheitszonen](../../installation/using/security-zones.md) und Sitzungsverwaltungseinstellungen erhöht.

Es stehen zwei Authentifizierungsmodi zur Verfügung:

* **über einen Aufruf der Methode zur Anmeldung()**. Dieser Modus generiert ein Sitzungs-Token und ein Sicherheits-Token. Dies ist der sicherste Modus und wird daher am meisten empfohlen.

oder

* **Über das Adobe Campaign-Login + -**, das ein Sitzungs-Token erstellt. Das Sitzungs-Token läuft nach einem festgelegten Zeitraum automatisch ab. Dieser Modus wird nicht empfohlen und erfordert eine Reduzierung der Sicherheitseinstellungen der Anwendung für einige Zoneneinstellungen (allowUserPassword=„true“ und sessionTokenOnly=„true„).

### Sitzungs-Token-Merkmale {#session-token-characteristics}

Das Sitzungs-Token weist die folgenden Merkmale auf:

* ein Lebenszyklus von X Stunden (der Lebenszyklus kann in der Datei „serverConf.xml“ konfiguriert werden, der Standardzeitraum beträgt 24 Stunden)
* eine zufällige Konstruktion (sie enthält nicht mehr den Benutzernamen und das Passwort)
* Bei Zugriff über das Web:

   * Das Sitzungs-Token wird zu einem permanenten Token. Es wird nicht zerstört, sobald der Browser geschlossen wird
   * es wird in einem HTTP-NUR-Cookie abgelegt (Cookies müssen für Benutzer aktiviert sein)

### Merkmale des Sicherheits-Tokens {#security-token-characteristics}

Das Sicherheits-Token weist die folgenden Merkmale auf:

* Er wird aus dem Sitzungs-Token generiert
* Er hat einen 24-Stunden-Lebenszyklus (kann in der Datei „serverConf.xml“ konfiguriert werden, der Standardzeitraum beträgt 24 Stunden)
* Sie wird in der Adobe Campaign-Konsole gespeichert
* Bei Zugriff über das Web:

   * Sie wird in einem Dokument gespeichert.__securityToken-Eigenschaft
   * Die Seiten-URLs werden aktualisiert, um das Sicherheits-Token zu aktualisieren
   * Die Formulare werden auch über ein ausgeblendetes Feld aktualisiert, das das Token enthält

#### Verlagerung von Sicherheits-Token {#security-token-movement}

Beim Zugriff über die Konsole ist dieser:

* Wird in der Anmeldeantwort (im HTTP-Header) gesendet
* wird in jeder Abfrage verwendet (im HTTP-Header)

Aus einem POST- und GET-HTTP:

* Der Server vervollständigt die Links mit dem Token
* Der Server fügt Formularen ein ausgeblendetes Feld hinzu

Aus einem SOAP-Aufruf:

* Er wird Aufrufkopfzeilen hinzugefügt

### Beispiele für Aufrufe {#call-examples}

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
>Die URLs, die in den folgenden **HttpServletRequest**-Aufrufen verwendet werden, müssen in der Zulassungsliste im Abschnitt „URL-Berechtigungen“ der Datei **serverConf.xml** vorhanden sein. Dies gilt auch für die URL des Servers selbst.

Ausführung der Anmeldung():

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

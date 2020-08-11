---
title: Über Web-Dienste
seo-title: Über Web-Dienste
description: Über Web-Dienste
seo-description: null
page-status-flag: never-activated
uuid: f0b21cb3-aa75-4f54-a9f5-64e880f93e53
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 65919173-3ce0-4d98-936b-f4581df536ae
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: bc54cef4c44be4c694e062f56685dbb09d2fcf8e
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 5%

---


# Über Web-Dienste{#about-web-services}

## Definition von Adobe Campaign-APIs {#definition-of-adobe-campaign-apis}

Der Adobe Campaign Application Server wurde für Offenheit und einfache Integration mit immer vielfältigeren und komplexeren Firmen-Informationssystemen entwickelt.

Adobe Campaign-APIs werden in JavaScript innerhalb der Anwendung und in SOAP außerhalb der Anwendung verwendet. Sie bilden eine Bibliothek generischer Funktionen, die bereichert werden können. Weitere Informationen finden Sie unter SOAP- [Methoden](../../configuration/using/implementing-soap-methods.md)implementieren.

>[!IMPORTANT]
>
>Die Anzahl der autorisierten Engine-Aufrufe pro Tag hängt von Ihrem Lizenzvertrag ab. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-classic---product-description.html).\
>Eine Liste aller APIs mit ihrer vollständigen Beschreibung finden Sie in [dieser Dokumentation](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).

## Voraussetzungen {#prerequisites}

Bevor Sie die Adobe Campaign-APIs verwenden, müssen Sie sich mit den folgenden Themen vertraut machen:

* Javascript
* SOAP protocol
* Adobe Campaign datamodel

## Using Adobe Campaign APIs {#using-adobe-campaign-apis}

Adobe Campaign verwendet zwei API-Typen:

* Generic data acces APIs for querying the datamodel data. Refer to [Data oriented APIs](../../configuration/using/data-oriented-apis.md).
* Business specific APIs that let you act on each object: deliveries, workflows, subscriptions, etc. Refer to [Business oriented APIs](../../configuration/using/business-oriented-apis.md).

In order to develop APIs and interact with Adobe Campaign, you need to be familiar with your datamodel. Adobe Campaign lets you generate a complete description of the base. Refer to [Description of the model](../../configuration/using/data-oriented-apis.md#description-of-the-model).

## SOAP calls {#soap-calls}

Mit dem SOAP-Protokoll können Sie API-Methoden über den Rich-Client, Drittanbieteranwendungen, die Webdienste verwenden, oder JSP mit diesen Methoden nativ aufrufen.

![](assets/s_ncs_configuration_architecture.png)

Die Struktur einer SOAP-Nachricht lautet wie folgt:

* an envelope which defines the structure of the message,
* an optional header,
* a body containing the information about the call and the response,
* error management that defines the error condition.

## Ressourcen und Austausch {#resources-and-exchanges}

The following schema shows the various resources involved in the use of Adobe Campaign APIs:

![](assets/s_ncs_integration_webservices_schema_pres.png)

## Beispiel einer SOAP-Meldung bei der Methode &#39;ExecuteQuery&#39; {#example-of-a-soap-message-on-the--executequery--method--}

In diesem Beispiel ruft eine SOAP-Abfrage die Methode &quot;ExecuteQuery&quot;auf, die eine Zeichenfolge als Authentifizierungsparameter (Sitzungstoken) und einen XML-Inhalt für die Beschreibung der auszuführenden Abfrage akzeptiert.

Weitere Informationen finden Sie unter [ExecuteQuery (xtk:queryDef)](../../configuration/using/data-oriented-apis.md#executequery--xtk-querydef-).

>[!NOTE]
>
>Die WSDL-Beschreibung dieses Dienstes ist im folgenden Beispiel abgeschlossen: [Webdienstbeschreibung: WSDL](../../configuration/using/web-service-calls.md#web-service-description--wsdl).

### SOAP-Abfrage {#soap-query}

```
<?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <ExecuteQuery xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <__sessiontoken xsi:type='xsd:string'/>
        <entity xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <queryDef firstRows="true" lineCount="200" operation="select" schema="nms:rcpGrpRel" startLine="0" startPath="/" xtkschema="xtk:queryDef">
          ...
          </queryDef>
        </entity>
      </ExecuteQuery>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Das `<soap-env:envelope>` Element ist das erste Element der Meldung, das den SOAP-Umschlag darstellt.

Das `<soap-env:body>` Element ist das erste untergeordnete Element der Hülle. Es enthält die Beschreibung der Nachricht, d.h. den Inhalt der Abfrage oder die Antwort.

Die aufzurufende Methode wird aus dem Hauptteil der SOAP-Nachricht in das `<executequery>` Element eingegeben.

In SOAP werden die Parameter in der Reihenfolge ihres Erscheinungsbilds erkannt. Der erste Parameter nimmt `<__sessiontoken>`die Authentifizierungskette und der zweite Parameter die XML-Beschreibung der Abfrage aus dem `<querydef>` Element.

### SOAP-Antwort {#soap-response}

```
<?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <ExecuteQueryResponse xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <pdomOutput xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <rcpGrpRel-collection><rcpGrpRel group-id="1872" recipient-id="1362"></rcpGrpRel></rcpGrpRel-collection>
        </pdomOutput>
      </ExecuteQueryResponse>
    </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Das Ergebnis der Abfrage wird aus dem `<pdomoutput>` Element eingegeben.

## Umgang mit Fehlern      {#error-management}

Beispiel für SOAP-Fehlerantwort:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <SOAP-ENV:Fault>
      <faultcode>SOAP-ENV:Server</faultcode>
      <faultstring>Error while executing 'Write' of the 'xtk:persist'.</faultstring> service
      <detail>ODBC error: [Microsoft][ODBC SQL Server Driver][SQL Server]Cannot insert duplicate key row in object 'XtkOption' with unique index 'XtkOption_name'. SQLSTate: 23000
ODBC error: [Microsoft][ODBC SQL Server Driver][SQL Server]The statement has been terminated. SQLSTate: 01000 Cannot save the 'Options (xtk:option)' document </detail>
    </SOAP-ENV:Fault>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Das `<soap-env:fault>` Element im Textkörper der SOAP-Meldung wird verwendet, um die Fehlersignale zu vermitteln, die bei der Verarbeitung des Webdiensts auftreten. Dies setzt sich aus den folgenden Unterelementen zusammen:

* `<faultcode>` : indicates the type of error. Die Fehlertypen sind:

   * &quot;VersionMismatch&quot;im Ereignis der Inkompatibilität mit der verwendeten SOAP-Version,
   * &quot;MustUnderstand&quot;im Ereignis eines Problems in der Kopfzeile der Nachricht,
   * &quot;Client&quot;in dem Ereignis, dass dem Kunden einige Informationen fehlen,
   * &quot;Server&quot;im Ereignis, dass der Server ein Problem bei der Ausführung der Verarbeitung hat.

* `<faultstring>` : Meldung, die den Fehler beschreibt
* `<detail>` : Lange Fehlermeldung

Der Erfolg oder Misserfolg des Dienstaufrufs wird bei der Überprüfung des `<faultcode>` Elements identifiziert.

>[!IMPORTANT]
>
>Alle Adobe Campaign-Webdienste behandeln Fehler. Es wird daher dringend empfohlen, jeden Aufruf zu testen, um zurückgegebene Fehler zu behandeln.

Beispiel für die Fehlerbehandlung in C#:

```
try 
{
  // Invocation of method
  ...
}
catch (SoapException e)
{
  System.Console.WriteLine("Soap exception: " + e.Message);        
  if (e.Detail != null)
    System.Console.WriteLine(e.Detail.InnerText);
}
```

## URL des Webdienstservers (oder EndPoint) {#url-of-web-service-server--or-endpoint-}

Um den Webdienst zu senden, muss der Adobe Campaign-Server, der die entsprechende Dienstmethode implementiert, kontaktiert werden.

Die Server-URL lautet wie folgt:

https://serverName/nl/jsp/soaprouter.jsp

Mit **`<server>`** dem Adobe Campaign-Anwendungsserver (**nlserver web**).

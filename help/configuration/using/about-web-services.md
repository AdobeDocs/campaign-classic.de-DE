---
product: campaign
title: Über Web-Dienste
description: Über Web-Dienste
audience: configuration
content-type: reference
topic-tags: api
exl-id: 7aa2aef1-2eb6-48a6-82fa-4451bed66216
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 8%

---

# Über Web-Dienste{#about-web-services}

![](../../assets/v7-only.svg)

## Definition von Adobe Campaign-APIs {#definition-of-adobe-campaign-apis}

Der Adobe Campaign-Anwendungsserver wurde für Offenheit und einfache Integration in immer vielfältigere und komplexere Unternehmensinformationssysteme entwickelt.

Adobe Campaign-APIs werden in JavaScript innerhalb der Anwendung und in SOAP außerhalb der Anwendung verwendet. Sie bilden eine Bibliothek allgemeiner Funktionen, die angereichert werden können. Weitere Informationen finden Sie unter [Implementieren von SOAP-Methoden](../../configuration/using/implementing-soap-methods.md).

>[!IMPORTANT]
>
>Die Anzahl der pro Tag zulässigen Engine-Aufrufe hängt von Ihrem Lizenzvertrag ab. Weitere Informationen hierzu finden Sie auf [dieser Seite](https://helpx.adobe.com/de/legal/product-descriptions/adobe-campaign-classic---product-description.html).\
>Eine Liste aller APIs einschließlich ihrer vollständigen Beschreibung finden Sie unter [diese spezielle Dokumentation](https://docs.adobe.com/content/help/de-DE/campaign-classic/technicalresources/api/index.html).

## Voraussetzungen {#prerequisites}

Bevor Sie die Adobe Campaign-APIs verwenden, müssen Sie sich mit den folgenden Themen vertraut machen:

* JavaScript
* SOAP-Protokoll
* Adobe Campaign-Datenmodell

## Verwenden von Adobe Campaign-APIs {#using-adobe-campaign-apis}

Adobe Campaign verwendet zwei API-Typen:

* Generische Data Access APIs zum Abfragen der Daten des Datenmodells. Näheres hierzu finden Sie unter [Datenorientierte APIs](../../configuration/using/data-oriented-apis.md).
* Business-orientierte APIs, mit denen Sie auf diese einzelnen Objekte, also Versand, Workflows, Abonnements usw., Aktionen ausführen können. Siehe [Geschäftsorientierte APIs](../../configuration/using/business-oriented-apis.md).

Um APIs zu entwickeln und mit Adobe Campaign zu interagieren, müssen Sie mit Ihrem Datenmodell vertraut sein. Mit Adobe Campaign können Sie eine vollständige Beschreibung der Basis erstellen. Siehe [Beschreibung des Modells](../../configuration/using/data-oriented-apis.md#description-of-the-model).

## SOAP-Aufrufe {#soap-calls}

Mit dem SOAP-Protokoll können Sie API-Methoden über den Rich-Client, Drittanbieteranwendungen mithilfe von Webservices oder JSP aufrufen, indem Sie diese Methoden nativ verwenden.

![](assets/s_ncs_configuration_architecture.png)

Eine SOAP-Nachricht weist folgende Struktur auf:

* einen Umschlag, der die Nachrichtenstruktur festlegt,
* eine optionale Kopfzeile,
* einen Text mit Informationen zum Aufruf und zur Antwort,
* Fehlerverwaltung, die die Fehlerbedingung definiert.

## Ressourcen und Austausch {#resources-and-exchanges}

Das folgende Schema zeigt die verschiedenen Ressourcen, die an der Verwendung von Adobe Campaign-APIs beteiligt sind:

![](assets/s_ncs_integration_webservices_schema_pres.png)

## Beispiel einer SOAP-Nachricht in der &#39;ExecuteQuery&#39;-Methode {#example-of-a-soap-message-on-the--executequery--method--}

In diesem Beispiel ruft eine SOAP-Abfrage die Methode &quot;ExecuteQuery&quot;auf, die eine Zeichenkette als Parameter für die Authentifizierung (Sitzungstoken) und einen XML-Inhalt für die Beschreibung der auszuführenden Abfrage akzeptiert.

Weitere Informationen finden Sie unter [ExecuteQuery (xtk:queryDef)](../../configuration/using/data-oriented-apis.md#executequery--xtk-querydef-).

>[!NOTE]
>
>Die WSDL-Beschreibung dieses Dienstes ist im folgenden Beispiel ausgefüllt: [Webdienstbeschreibung: WSDL](../../configuration/using/web-service-calls.md#web-service-description--wsdl).

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

Die `<soap-env:envelope>` element ist das erste Element der Nachricht, das den SOAP-Umschlag darstellt.

Die `<soap-env:body>` -Element ist das erste untergeordnete Element des Umschlags. Sie enthält die Beschreibung der Nachricht, d. h. den Inhalt der Abfrage oder der Antwort.

Die aufzurufende Methode wird im `<executequery>` -Element aus dem Text der SOAP-Nachricht.

In SOAP werden die Parameter in der Reihenfolge ihres Erscheinungsbilds erkannt. Der erste Parameter, `<__sessiontoken>`, nimmt die Authentifizierungskette und der zweite Parameter ist die XML-Beschreibung der Abfrage aus der `<querydef>` -Element.

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

Das Ergebnis der Abfrage wird aus dem `<pdomoutput>` -Element.

## Umgang mit Fehlern       {#error-management}

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

Die `<soap-env:fault>` -Element im Textkörper der SOAP-Nachricht verwendet wird, um die bei der Verarbeitung des Webdienstes auftretenden Fehlersignale zu übermitteln. Dies setzt sich aus den folgenden Unterelementen zusammen:

* `<faultcode>` : gibt den Fehlertyp an. Die Fehlertypen sind:

   * &quot;VersionMismatch&quot; im Fall der Inkompatibilität mit der verwendeten SOAP-Version,
   * &quot;MustUnderstand&quot;im Fall eines Problems in der Kopfzeile der Nachricht,
   * &quot;Client&quot;, falls dem Client einige Informationen fehlen,
   * &quot;Server&quot;, wenn der Server ein Problem bei der Ausführung der Verarbeitung hat.

* `<faultstring>` : Fehlermeldung
* `<detail>` : Lange Fehlermeldung

Der Erfolg oder Misserfolg des Dienstaufrufs wird identifiziert, wenn die Variable `<faultcode>` -Element überprüft wird.

>[!IMPORTANT]
>
>Alle Adobe Campaign-Webdienste behandeln Fehler. Es wird daher dringend empfohlen, jeden Aufruf zu testen, um zurückgegebene Fehler zu verarbeiten.

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

Um den Webdienst zu übermitteln, muss der Adobe Campaign-Server kontaktiert werden, der die entsprechende Dienstmethode implementiert.

Die Server-URL lautet wie folgt:

https://serverName/nl/jsp/soaprouter.jsp

Mit **`<server>`** der Adobe Campaign-Anwendungsserver (**nlserver web**).

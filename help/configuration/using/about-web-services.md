---
product: campaign
title: Über Web-Dienste
description: Über Web-Dienste
feature: API
role: Data Engineer, Developer
exl-id: 7aa2aef1-2eb6-48a6-82fa-4451bed66216
source-git-commit: 517b85f5d7691acc2522bf4541f07c34c60c7fbf
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 8%

---

# Über Web-Dienste{#about-web-services}

## Definition von Adobe Campaign-APIs {#definition-of-adobe-campaign-apis}

Der Adobe Campaign-Anwendungsserver wurde für Offenheit und einfache Integration in immer vielfältigere und komplexere Unternehmensinformationssysteme entwickelt.

Adobe Campaign-APIs werden in JavaScript innerhalb und SOAP außerhalb der Anwendung verwendet. Sie bilden eine Bibliothek allgemeiner Funktionen, die angereichert werden können. Weitere Informationen finden Sie unter [Implementieren SOAP Methoden](../../configuration/using/implementing-soap-methods.md).

>[!IMPORTANT]
>
>Die Anzahl der pro Tag zulässigen Engine-Aufrufe hängt von Ihrem Lizenzvertrag ab. Weitere Informationen hierzu finden Sie auf [dieser Seite](https://helpx.adobe.com/de/legal/product-descriptions/adobe-campaign-classic---product-description.html).\
>Eine Liste aller APIs einschließlich ihrer vollständigen Beschreibung finden Sie in [dieser speziellen Dokumentation](https://experienceleague.adobe.com/developer/campaign-api/api/index.html).

## Voraussetzungen {#prerequisites}

Bevor Sie die Adobe Campaign-APIs verwenden, müssen Sie sich mit den folgenden Themen vertraut machen:

* JavaScript
* SOAP-Protokoll
* Adobe Campaign-Datenmodell

## Verwenden von Adobe Campaign-APIs {#using-adobe-campaign-apis}

Adobe Campaign verwendet zwei API-Typen:

* Generische Datenzugriffs-APIs zur Abfrage von Datenmodelldaten. Näheres hierzu finden Sie unter [Datenorientierte APIs](../../configuration/using/data-oriented-apis.md).
* Business-orientierte APIs, mit denen Sie auf diese einzelnen Objekte, also Versand, Workflows, Abonnements usw., Aktionen ausführen können. Siehe [Geschäftsorientierte APIs](../../configuration/using/business-oriented-apis.md).

Um APIs zu entwickeln und mit Adobe Campaign zu interagieren, müssen Sie mit Ihrem Datenmodell vertraut sein. Mit Adobe Campaign können Sie eine vollständige Beschreibung der Basis erstellen. Siehe [Beschreibung des Modells](../../configuration/using/data-oriented-apis.md#description-of-the-model).

## SOAP-Aufrufe {#soap-calls}

Mit dem SOAP-Protokoll können Sie API-Methoden über den Rich-Client, Drittanbieteranwendungen mithilfe von Webservices oder JSP über diese Methoden nativ aufrufen.

![](assets/s_ncs_configuration_architecture.png)

Eine SOAP Nachricht weist die folgende Struktur auf:

* einen Umschlag, der die Nachrichtenstruktur festlegt,
* eine optionale Kopfzeile,
* einen Text mit Informationen zum Aufruf und zur Antwort,
* Fehlerverwaltung, die die Fehlerbedingung definiert.

## Ressourcen und Austausch {#resources-and-exchanges}

Das folgende Schema zeigt die verschiedenen Ressourcen, die an der Verwendung von Adobe Campaign-APIs beteiligt sind:

![](assets/s_ncs_integration_webservices_schema_pres.png)

## Beispiel für eine SOAP Nachricht in der Methode &quot;ExecuteQuery&quot; {#example-of-a-soap-message-on-the--executequery--method--}

In diesem Beispiel ruft eine SOAP Abfrage die Methode &quot;ExecuteQuery&quot;auf, die eine Zeichenkette als Parameter für die Authentifizierung (Sitzungstoken) und einen XML-Inhalt für die Beschreibung der auszuführenden Abfrage akzeptiert.

Weitere Informationen finden Sie unter [ExecuteQuery (xtk:queryDef)](../../configuration/using/data-oriented-apis.md#executequery--xtk-querydef-).

>[!NOTE]
>
>Die WSDL-Beschreibung dieses Dienstes wird im folgenden Beispiel ausgefüllt: [Beschreibung des Webdienstes: WSDL](../../configuration/using/web-service-calls.md#web-service-description--wsdl).

### SOAP Abfrage {#soap-query}

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

Das Element `<soap-env:envelope>` ist das erste Element der Nachricht, das den SOAP Umschlag darstellt.

Das Element `<soap-env:body>` ist das erste untergeordnete Element des Umschlags. Sie enthält die Beschreibung der Nachricht, d. h. den Inhalt der Abfrage oder der Antwort.

Die aufzurufende Methode wird im Element `<executequery>` aus dem Hauptteil der SOAP Nachricht eingegeben.

In SOAP werden die Parameter in der Reihenfolge ihres Erscheinungsbilds erkannt. Der erste Parameter, `<__sessiontoken>`, verwendet die Authentifizierungskette, der zweite Parameter ist die XML-Beschreibung der Abfrage aus dem Element `<querydef>` .

### SOAP Antwort {#soap-response}

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

Das Ergebnis der Abfrage wird aus dem Element `<pdomoutput>` eingegeben.

## Umgang mit Fehlern {#error-management}

Beispiel SOAP Fehlerantwort:

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

Das Element `<soap-env:fault>` im Textkörper der SOAP wird verwendet, um die bei der Verarbeitung des Webdienstes auftretenden Fehlersignale zu übermitteln. Dies setzt sich aus den folgenden Unterelementen zusammen:

* `<faultcode>` : Gibt den Fehlertyp an. Die Fehlertypen sind:

   * &quot;VersionMismatch&quot; im Fall der Inkompatibilität mit der verwendeten SOAP,
   * &quot;MustUnderstand&quot;im Fall eines Problems in der Kopfzeile der Nachricht,
   * &quot;Client&quot;, falls dem Client einige Informationen fehlen,
   * &quot;Server&quot;, wenn der Server ein Problem bei der Ausführung der Verarbeitung hat.

* `<faultstring>` : Fehlerbeschreibung
* `<detail>` : Lange Fehlermeldung

Der Erfolg oder Misserfolg des Dienstaufrufs wird bei der Überprüfung des Elements `<faultcode>` identifiziert.

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

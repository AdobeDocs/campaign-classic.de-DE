---
product: campaign
title: Über Web-Dienste
description: Über Web-Dienste
feature: API
role: Developer
exl-id: 7aa2aef1-2eb6-48a6-82fa-4451bed66216
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 8%

---

# Über Web-Dienste{#about-web-services}

## Definition der Adobe Campaign-APIs {#definition-of-adobe-campaign-apis}

Der Adobe Campaign-Anwendungsserver wurde für Offenheit und einfache Integration mit immer vielfältigeren und komplexeren Unternehmensinformationssystemen konzipiert.

Adobe Campaign-APIs werden in JavaScript innerhalb des Programms und in SOAP außerhalb desselben verwendet. Sie bilden eine Bibliothek allgemeiner Funktionen, die angereichert werden können. Weitere Informationen finden Sie unter [&#x200B; von SOAP-](../../configuration/using/implementing-soap-methods.md).

>[!IMPORTANT]
>
>Die Anzahl der autorisierten Engine-Aufrufe pro Tag hängt von Ihrem Lizenzvertrag ab. Weitere Informationen hierzu finden Sie auf [dieser Seite](https://helpx.adobe.com/de/legal/product-descriptions/adobe-campaign-classic---product-description.html).\
>Eine Liste aller APIs einschließlich ihrer vollständigen Beschreibung finden Sie in [dieser speziellen Dokumentation]&#x200B;(https://experienceleague.adobe.com/developer/campaign-api/api/index.html.

## Voraussetzungen {#prerequisites}

Bevor Sie die Adobe Campaign-APIs verwenden, müssen Sie mit den folgenden Themen vertraut sein:

* JavaScript
* SOAP-Protokoll
* Adobe Campaign-Datenmodell

## Verwenden von Adobe Campaign-APIs {#using-adobe-campaign-apis}

Adobe Campaign verwendet zwei Arten von APIs:

* Generische Datenzugriffs-APIs zur Abfrage von Datenmodelldaten. Näheres hierzu finden Sie unter [Datenorientierte APIs](../../configuration/using/data-oriented-apis.md).
* Business-orientierte APIs, mit denen Sie auf diese einzelnen Objekte, also Versand, Workflows, Abonnements usw., Aktionen ausführen können. Siehe [Business-orientierte APIs](../../configuration/using/business-oriented-apis.md).

Um APIs entwickeln und mit Adobe Campaign interagieren zu können, müssen Sie mit Ihrem Datenmodell vertraut sein. Mit Adobe Campaign können Sie eine vollständige Beschreibung der Basis generieren. Siehe [Beschreibung des Modells](../../configuration/using/data-oriented-apis.md#description-of-the-model).

## SOAP-Aufrufe {#soap-calls}

Mit dem SOAP-Protokoll können Sie API-Methoden über den Rich-Client oder Anwendungen von Drittanbietern mithilfe von Web-Services oder JSP aufrufen, indem Sie diese Methoden nativ verwenden.

![](assets/s_ncs_configuration_architecture.png)

Eine SOAP-Nachricht weist die folgende Struktur auf:

* einen Umschlag, der die Struktur der Nachricht definiert,
* eine optionale Kopfzeile,
* einen Text, der die Informationen über den Aufruf und die Antwort enthält,
* Fehlerverwaltung, die die Fehlerbedingung definiert.

## Ressourcen und Austausch {#resources-and-exchanges}

Das folgende Schema zeigt die verschiedenen Ressourcen, die bei der Verwendung von Adobe Campaign-APIs zum Einsatz kommen:

![](assets/s_ncs_integration_webservices_schema_pres.png)

## Beispiel einer SOAP-Nachricht mit der Methode „ExecuteQuery“ {#example-of-a-soap-message-on-the--executequery--method--}

In diesem Beispiel ruft eine SOAP-Abfrage die Methode „ExecuteQuery“ auf, die eine Zeichenfolge als Authentifizierungsparameter (Sitzungs-Token) und einen XML-Inhalt für die Beschreibung der auszuführenden Abfrage benötigt.

Weitere Informationen finden Sie unter [&#x200B; (xtk:queryDef)](../../configuration/using/data-oriented-apis.md#executequery--xtk-querydef-).

>[!NOTE]
>
>Die WSDL-Beschreibung dieses Dienstes wird im folgenden Beispiel ausgefüllt: [Webdienstbeschreibung: WSDL](../../configuration/using/web-service-calls.md#web-service-description--wsdl).

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

Das `<soap-env:envelope>` ist das erste Element der Nachricht, das die SOAP-Hülle darstellt.

Das `<soap-env:body>` ist das erste untergeordnete Element der Envelope. Sie enthält die Beschreibung der Nachricht, d. h. den Inhalt der Abfrage oder der Antwort.

Die aufzurufende Methode wird im `<executequery>` aus dem Hauptteil der SOAP-Nachricht eingegeben.

In SOAP werden die Parameter anhand der Reihenfolge des Erscheinungsbilds erkannt. Der erste Parameter übernimmt `<__sessiontoken>` die Authentifizierungskette, der zweite Parameter ist die XML-Beschreibung der Abfrage aus dem `<querydef>`.

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

Das Ergebnis der Abfrage wird über das `<pdomoutput>` eingegeben.

## Umgang mit Fehlern {#error-management}

Beispiel einer SOAP-Fehlerantwort:

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

Das `<soap-env:fault>` Element im Textkörper der SOAP-Nachricht wird verwendet, um die bei der Verarbeitung des Webservices auftretenden Fehlersignale zu übermitteln. Dieses besteht aus den folgenden Unterelementen:

* `<faultcode>` : Gibt den Fehlertyp an. Die Fehlertypen sind:

   * „VersionMismatch“ im Fall von Inkompatibilität mit der verwendeten SOAP-Version,
   * „MustUnderstand“ im Falle eines Problems im Nachrichtenkopf,
   * „Client“ für den Fall, dass dem Client einige Informationen fehlen,
   * „Server“, falls beim Ausführen der Verarbeitung auf dem Server Probleme auftreten.

* `<faultstring>` : Meldung, die den Fehler beschreibt
* `<detail>` : lange Fehlermeldung

Der Erfolg oder Misserfolg des Service-Aufrufs wird identifiziert, wenn das `<faultcode>` überprüft wird.

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

## URL des Webservice-Servers (oder Endpunkts) {#url-of-web-service-server--or-endpoint-}

Um den Webdienst zu übermitteln, muss der Adobe Campaign-Server kontaktiert werden, der die entsprechende Dienstmethode implementiert.

Die Server-URL lautet wie folgt:

https://serverName/nl/jsp/soaprouter.jsp

**`<server>`** mit dem Adobe Campaign-Anwendungsserver (**nlserver web**).

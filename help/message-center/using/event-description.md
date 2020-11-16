---
title: Beschreibung des Message Center-Ereignisses
description: Weitere Informationen zum transaktionalen Messaging-Ereignis
page-status-flag: never-activated
uuid: 7b174ffd-28b2-4147-b992-e17b0b2cf733
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: introduction
discoiquuid: 3c8388d8-1a91-4d16-a8ac-016f643c6009
translation-type: tm+mt
source-git-commit: cb2fb5a338220c54aba96b510a7371e520c2189e
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 98%

---


# Ereignisbeschreibung{#event-description}

## Über das Datenmodell für Transaktionsnachrichten {#about-transactional-messaging-datamodel}

Transaktionsnachrichten basieren auf dem Adobe Campaign-Datenmodell und verwenden zwei zusätzliche separate Tabellen. Die [Tabellen](../../configuration/using/data-model-description.md#message-center-module), **NmsRtEvent** und **NmsBatchEvent** enthalten dieselben Felder und ermöglichen Ihnen die Verwaltung von Echtzeit-Ereignissen einerseits und Batch-Ereignissen andererseits.

## SOAP-Methoden {#soap-methods}

In diesem Abschnitt werden die in Zusammenhang mit den Schemata des Transaktionsnachrichten-Moduls verwendeten SOAP-Methoden beschrieben.

Die zwei SOAP-Methoden **PushEvent** und **PushEvents** werden jeweils den Datenschemata **nms:rtEvent** und **nms:BatchEvent** zugeordnet. Das Informationssystem bestimmt hierbei, ob es sich um ein &quot;Batch&quot;- oder &quot;Echtzeit&quot;-Ereignis handelt.

* **PushEvent** ermöglicht das Einfügen eines einzelnen Ereignisses in eine Nachricht,
* **PushEvents** ermöglicht das Einfügen einer Kollektion von Ereignissen in eine Nachricht.

Die WSDL-Zugriffspfade der zwei Methoden lauten:

* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:rtEvent**, um auf das Echtzeit-Schema zuzugreifen;
* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:batchEvent**, um auf das Batch-Schema zuzugreifen.

Beide Methoden enthalten ein **`<urn:sessiontoken>`**-Element zum Anmelden beim Modul für den Transaktionsnachrichtenversand. Wir empfehlen die Verwendung einer Authentifizierungsmethode über vertrauenswürdige IP-Adressen. Um das Sitzungstoken abzurufen, führen Sie einen SOAP-Aufruf zur Anmeldung und dann ein GET-Token gefolgt von einer Abmeldung durch. Verwenden Sie dasselbe Token für mehrere RT-Aufrufe. Die in diesem Abschnitt enthaltenen Beispiele verwenden die Sitzungstoken-Methode, wobei es sich um das empfohlene Verfahren handelt.

Wenn Sie einen Lastverteilungsserver verwenden, können Sie die Benutzer-/Passwort-Authentifizierung (auf der Ebene der Echtzeitnachricht) verwenden. Beispiel:

```
<PushEvent xmlns="urn:nms:rtEvent">
<sessiontoken>mc/PASSWORD</sessiontoken>
<domEvent>
<rtEvent wishedChannel="41" type="rt_MobileJourney_iOS_Push" registrationToken="c3ddc8aaecc24822df25d0f49865cca61ea3f86c61bfa53ae4d37294e37f4a1c" hashlpId="27EE7571EC14DBA23B9B5CC0EF79BB782DAECF4C03C88E5D92CC9B9DAC4E5DDA" correlationId="415b7593-4f6f-e911-811f-00505691247c" xmlns="">
<mobileApp uuid="236B24DC-C073-412F-8BCB-AC7207096258" _operation="none"/>
<ctx>...</ctx>
</rtEvent>
</domEvent>
</PushEvent>
```

Die Methode **PushEvent** besteht aus einem **`<urn:domevent>`**-Parameter, der das Ereignis enthält.

Die Methode **PushEvents** besteht aus einem **`<urn:domeventcollection>`**-Parameter, der die Ereigniskollektion enthält.

Beispiel der Methode PushEvent:

```
<urn:PushEvent>

 <sessiontoken>___921f9b38-72ac-49ad-b481-ab32973efc50</sessiontoken>
 
 <urn:domEvent>
 
   <rtEvent>
   
   ...
   
   </rtEvent>
 
 </urn:domEvent>

</urn:PushEvent>
```

>[!NOTE]
>
>Bei Aufruf der **PushEvents**-Methode müssen wir ein übergeordnetes XML-Element hinzufügen, um die standardmäßige XML zu erfüllen. Dieses XML-Element bildet den Rahmen für die verschiedenen im Ereignis enthaltenen **`<rtevent>`**-Elemente.

Beispiel der Methode PushEvents:

```
<urn:PushEvents>

 <sessiontoken>___921f9b38-72ac-49ad-b481-ab32973efc50</sessiontoken>
 
 <urn:domEventCollection>
 
   <Events>
   
     <rtEvent>... </rtEvent>
     
     <rtEvent>... </rtEvent>
     
     ...
   
   </Events>
 
 </urn:domEventCollection>

</urn:PushEvents>
```

Die **`<rtevent>`**- und **`<batchevent>`**-Elemente besitzen einen Satz an Attributen sowie ein unbedingt erforderliches Kindelement **`<ctx>`**, welches die Integration der Nachrichtendaten ermöglicht.

>[!NOTE]
>
>Mit dem **`<batchevent>`**-Element können Sie das Ereignis der „Batch“-Warteschlange hinzufügen. Das Ereignis **`<rtevent>`** wird der Warteschlange „Echtzeit“ hinzugefügt.

Die obligatorischen Attribute der Elemente **`<rtevent>`** und **`<batchevent>`** lauten „@type“ und „@email“. Der Wert von „@type“ muss mit dem bei der Konfiguration der Ausführungsinstanz definierten Auflistungswert übereinstimmen. Mit diesem Wert können Sie die Vorlage definieren, die beim Versand mit dem Inhalt des Ereignisses verknüpft werden soll.

`<rtevent> configuration example:`

```
<rtEvent type="order_confirmation" email="john.doe@domain.com" origin="eCommerce" wishedChannel="0" externalId="1242" mobilePhone="+33620202020"> 
```

In diesem Beispiel sind mit der E-Mail-Adresse und der Mobiltelefonnummer zwei Kanäle angegeben. Das Feld **wishedChannel** ermöglicht die Bestimmung des Kanals, der bei der Reaktion auf ein Ereignis verwendet werden soll. Der Wert &quot;0&quot; entspricht dem E-Mail-Kanal, der Wert &quot;1&quot; dem Mobile-Kanal usw.

Wenn Sie die Verarbeitung eines Ereignisses terminieren möchten, fügen Sie das Feld **[!UICONTROL scheduled]** hinzu, gefolgt vom gewünschten Datum. Erst zum angegebenen Zeitpunkt wird auf das Ereignis reagiert.

Es wird empfohlen, die Attribute @wishedChannel und @emailFormat in Form von numerischen Werten anzugeben. Die Mapping-Tabelle der numerischen Werte und der ihnen zugeordnete Titel finden sich in der Beschreibung der Datenschemata.

>[!NOTE]
>
>Zulässige Attribute und ihre Werte werden in den Schemabeschreibungen von **nms:rtEvent** und **nms:BatchEvent** aufgeführt.

Das **`<ctx>`**-Element enthält die Nachrichtendaten. Der XML-Inhalt ist offen, d. h. er kann je nach zu sendendem Inhalt konfiguriert werden.

>[!NOTE]
>
>Die Anzahl und Größe der in der Nachricht enthaltenen XML-Knoten sollte dahingehend optimiert werden, eine Serverüberlastung beim Versand zu vermeiden.

Datenbeispiel:

```
   <ctx>
               <client>
                        <firstname>John</firstname>
                        <lastname>Doe</lastname>
               </client>
               <action>
                         <type>Order confirmation</type>
                          <number>CN23453</number>
               </action>
               <orderdetails>
                          <article num="1">
                                   <name>Generic USB key</name>
                                   <price>20</price>
                           </article>
               </orderdetails>
    </ctx>
   
```

## Vom SOAP-Aufruf zurückgegebene Informationen {#information-returned-by-the-soap-call}

Beim Empfang eines Ereignisses erzeugt Adobe Campaign eine eindeutige Rückgabe-Kennung. Diese entspricht der Kennung der im Verlauf gespeicherten Ereignisversion.

>[!IMPORTANT]
>
>Beim Empfang von SOAP-Anfragen verifiziert Adobe Campaign das Format der E-Mail-Adresse. Wenn die E-Mail-Adresse falsch formatiert ist, wird ein Fehler zurückgegeben.

* Beispiel einer von der Methode zurückgegebenen Kennung bei der erfolgreichen Verarbeitung eines Ereignisses:

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
            <plId xsi:type="xsd:long">72057594037935966</plId>
         </urn:PushEventResponse>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

Wenn der Wert der Rückgabe-Kennung streng größer als null ist, wurde das Ereignis im Verlauf in Adobe Campaign gespeichert.

Wenn die Verarbeitung des Ereignisses fehlgeschlagen ist, gibt die Methode eine Fehlernachricht oder einen Wert gleich null zurück.

* Beispiel einer fehlgeschlagenen Ereignisverarbeitung, bei der in der Abfrage die Kennung fehlt oder der angegebene Benutzer nicht über die erforderlichen Berechtigungen verfügt:

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <SOAP-ENV:Fault>
            <faultcode>SOAP-ENV:Client</faultcode>
            <faultstring xsi:type="xsd:string">Error while reading parameters of method 'PushEvent' of service 'nms:rtEvent'.</faultstring>
            <detail xsi:type="xsd:string">Invalid login or password. Connection denied.</detail>
         </SOAP-ENV:Fault>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* Beispiel einer fehlgeschlagenen Ereignisverarbeitung, bei der die Abfrage einen Fehler ergeben hat (nicht eingehaltene XML-Nomenklatur):

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <SOAP-ENV:Fault>
            <faultcode>SOAP-ENV:Client</faultcode>
            <faultstring xsi:type="xsd:string">The XML SOAP message is invalid (service 'PushEvent', method 'nms:rtEvent').</faultstring>
            <detail xsi:type="xsd:string"><![CDATA[(16:8) : Expected end of tag 'rtevent'
   Error while parsing XML string '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
      <soapenv:Header/>
      <soapenv:Body>
         <urn:PushEvent>
            <urn:sessiontoken>mc/</urn:sessiontoken>
            <urn:domEvent>
   <rtevent type="create_account" email="esther.hall@adobe.com" origin="eCommerce" wishedChannel="email" 
         externalId="1596" language="english" country="EN" emailFormat="2"
         mobilePhone="+447700123123">
     <ctx>
      <website name="eCommerce" url="http://www.eCo']]></detail>
         </SOAP-ENV:Fault>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* Beispiel einer fehlgeschlagenen Ereignisverarbeitung, bei der eine Null-Kennung zurückgegeben wird (fehlerhafter Methodenname):

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
            <plId xsi:type="xsd:long">0</plId>
         </urn:PushEventResponse>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```


---
title: Geschäftsorientierte APIs
seo-title: Geschäftsorientierte APIs
description: Geschäftsorientierte APIs
seo-description: null
page-status-flag: never-activated
uuid: ddb6e5cf-dfe0-4dc9-ac5b-fab21827b874
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: e7b3ffca-c85f-498d-89b4-23fcff59de49
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c51a51f175e9f3fe5a55f2b5f57872057f70909d
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 4%

---


# Geschäftsorientierte APIs{#business-oriented-apis}

Die Business-API ist für jeden Objekttyp spezifisch. Sie wirken sich auf Folgendes aus:

* Deliveries:

   * Erstellen einer Versand-Aktion, siehe [SubmitDelivery (nms:Versand)](#submitdelivery--nms-delivery-),
   * Senden einer Kampagne (Beginn, Pause, Stopp, Testversand senden),
   * Wiederherstellen von Versandlogs.

* Workflows:

   * Workflow starten,
   * Verfahren usw. überprüfen.

      Siehe [SOAP-Methoden in JavaScript](../../configuration/using/soap-methods-in-javascript.md).

* Content Management
* Abonnement-Management, siehe [Abonnieren (nms:Abonnement)](#subscribe--nms-subscription-) und [Abmelden (nms:Abonnement)](#unsubscribe--nms-subscription-).
* Datenprozesse: Einfuhren, Ausfuhren.

In diesem Abschnitt wird die Verwendung der Dienste &quot;Abonnieren&quot;, &quot;Abbestellen&quot;und &quot;SendenAuslieferung&quot;beschrieben.

>[!IMPORTANT]
>
>[Die JSAPI-Dokumentation](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html) der Kampagne enthält zusätzliche Informationen zu SOAP-Aufrufen und zum Einsatz von JavaScript in Adobe Campaign sowie einen vollständigen Verweis auf alle in der Anwendung verwendeten Methoden und Funktionen.

## Abonnieren (nms:Abonnement) {#subscribe--nms-subscription-}

Mit diesem Dienst können Sie einen Empfänger für einen Informationsdienst abonnieren und das Empfänger-Profil aktualisieren.

Folgende Parameter sind erforderlich, um den Dienst aufzurufen:

* eine Authentifizierung,
* interner Name des Anmeldediensts,
* ein XML-Dokument, das die Informationen zum Empfänger enthält (aus dem Schema &quot;nms:Empfänger&quot;),
* Ein boolescher Wert für die Erstellung von Empfängern, wenn noch kein solcher vorhanden ist.

Beschreibung der Methode &quot;subscribe&quot;im Schema &quot;nms:Abonnement&quot;:

```
<method name="Subscribe" static="true">
  <parameters>
     <param name="serviceName" type="string"  desc="List of information service names (comma separated)"/>
     <param name="recipient" type="DOMElement" desc="Recipient"/>
     <param name="create" type="Boolean" desc="Create recipient if it does not exist"/>
   </parameters>
</method>
```

Die Definition des Abstimmschlüssels muss über das Attribut &quot;_**key** &quot;im `<recipient>` Element des XML-Dokuments eingegeben werden. Der Inhalt dieses Attributs ist eine kommagetrennte XPath-Liste.

Dieser Aufruf gibt keine Daten außer Fehler zurück.

### Beispiele {#examples}

Abonnement mit Empfänger Abstimmschlüssel auf der E-Mail-Adresse: Das XML-Dokument für die Eingabe muss auf die E-Mail-Adresse und die Definition des Schlüssels in diesem Feld verweisen.

```
<recipient _key="email" email= "john.doe@adobe.com"/>
```

Aktualisieren des Empfängers und des Abonnements.

```
<recipient _key="email, [folder-id]" email= "john.doe@adobe.com" folder-id="1305" firstName="John" lastName="Doe"/>
```

### Beispiel für SOAP-Meldungen {#example-of-soap-messages}

* Abfrage:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <m:Subscribe xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
         <sessiontoken xsi:type='xsd:string'/>
         <service xsi:type='xsd:string'>SVC1</service>
         <content xsi:type='' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
           <recipient _key="@email" email= "john.doe@adobe.com/>
         </content>
         <create xsi:type='xsd:boolean'>true</create>
       </m:Subscribe>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* Antwort:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <m:SubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
       </m:SubscribeResponse>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

## Abmelden (nms:Abonnement) {#unsubscribe--nms-subscription-}

Mit diesem Dienst können Sie einen Empfänger von einem Informationsdienst abmelden und das Empfänger-Profil aktualisieren.

Folgende Parameter sind erforderlich, um den Dienst aufzurufen:

* eine Authentifizierung,
* Interner Name des Dienstes, von dem das Abonnement abgemeldet werden soll,
* ein XML-Dokument, das die Informationen zum Empfänger enthält (aus dem Schema &quot;nms:Empfänger&quot;),

Beschreibung der Methode &quot;Unsubscribe&quot;im Schema &quot;nms:Abonnement&quot;:

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>
```

Die Definition des Abstimmschlüssels muss über das Attribut &quot;_key&quot;im `<recipient>` Element des XML-Dokuments eingegeben werden. Der Inhalt dieses Attributs ist eine kommagetrennte XPath-Liste.

Wenn der Empfänger nicht in der Datenbank vorhanden ist oder nicht für den betreffenden Informationsdienst abonniert wird, führt der Dienst keine Aktion durch und verursacht keinen Fehler.

>[!NOTE]
>
>Wenn der Dienstname nicht als Parameter angegeben ist, wird der Empfänger automatisch auf blockierungsliste (@blockierungsliste=&quot;1&quot;) gesetzt.

Dieser Aufruf gibt keine Daten außer Fehler zurück.

### Beispiel für SOAP-Meldungen {#example-of-soap-messages-1}

Abfrage:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:Unsubscribe xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    <sessiontoken xsi:type='xsd:string'/>
    <service xsi:type='xsd:string'>SVC1</service>
    <content xsi:type='' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
      <recipient _key="@email" email= "john.doe@adobe.com/>
    </content>
  </m:Unsubscribe>
</SOAP-ENV:Body>
```

Antwort:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:UnsubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    </m:UnsubscribeResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## SubmitDelivery (nms:Versand) {#submitdelivery--nms-delivery-}

Mit diesem Dienst können Sie eine Versand-Aktion erstellen und senden.

Folgende Parameter sind erforderlich, um den Dienst aufzurufen:

* eine Authentifizierung,
* interner Name der Versandvorlage,
* ein optionales XML-Dokument, das zusätzliche Versand-Daten enthält.

Diese API sollte nicht im Volume aufgerufen werden, da möglicherweise Leistungsprobleme auftreten.

Beschreibung der Methode in ihrem Schema:

```
<method name="SubmitDelivery" static="true">
  <parameters>
    <param name="scenarioName" type="string" inout="in" desc="Internal name of the delivery template"/>
    <param name="content" type="DOMElement"  inout="in" desc="XML content of the delivery template" />
  </parameters>
</method>
```

Eine Versandvorlage muss über die Adobe Campaign-Client-Konsole erstellt werden. Es enthält die für alle Versand gemeinsamen Parameter (Absenderadresse oder Gültigkeitsdauer der Nachricht).

Das Eingabe-XML-Dokument ist ein Versandvorlage-Fragment, das der Struktur des Schemas &quot;nms:Versand&quot;folgt. Es enthält alle zusätzlichen Daten, die in der Versandvorlage nicht statisch definiert werden konnten (z. B. Liste der Empfänger zur Zielgruppe).

Dieser Aufruf gibt keine Daten außer Fehler zurück.

### XML-Dokument-Beispiel {#xml-document-example}

Dieses Beispiel basiert auf einer benutzerdefinierten Versandvorlage aus einer externen Datenquelle (in diesem Fall einer Datei). Die Konfiguration wird in der Versandvorlage vollständig beschrieben, sodass beim Aufruf nur der Dateiinhalt des `<externalsource>` Elements gesendet werden muss.

```
<delivery>
  <targets fromExternalSource="true">
    <externalSource>
      MsgId|ClientId|Title|Name|FirstName| Mobile|Email| Market_segment|Product_affinity1 |Product_affinity2|Product_affinity3| Product_affinity4| Support_Number|Amount|Threshold1|000001234|M.| Doe|John|0650201020| john.doe@adobe.com
|1| A1|A2|A3|A4|E12|120000|100000
    </externalSource>
  </target>
</delivery>
```

Wenn Sie keine Versandvorlage haben, können Sie das folgende Beispiel verwenden:

```
<delivery>
<targets fromExternalSource="true" targetMode="1" noReconciliation="true" addressField="Email" >  
    <fileFormat active="true">  
      <source format="text" type="text">  
        <dataSourceConfig >  
          <dataSourceColumn label="Email" name="Email" type="string"/>  
        </dataSourceConfig>  
      </source>  
      <destination type="xtkDataStore"/>  
    </fileFormat>  
    <externalSource><![CDATA[not-a-repicipient@domain.com]]></externalSource>  
  </targets> 
</delivery> 
```


---
product: campaign
title: Geschäftsorientierte APIs
description: Geschäftsorientierte APIs
feature: API
role: Data Engineer, Developer
exl-id: e6638870-3141-4f12-b904-db436127c0d1
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 2%

---

# Geschäftsorientierte APIs{#business-oriented-apis}

Die Business-API ist für jeden Objekttyp spezifisch. Sie wirken sich auf Folgendes aus:

* Sendungen:

   * Versandaktionen, siehe [SubmitDelivery (nms:delivery)](#submitdelivery--nms-delivery-),
   * Versand einer Kampagne (Start, Pause, Stopp, Testversand),
   * Abruf der Versandlogs.

* Workflows:

   * Workflow starten,
   * Überprüfen von Prozessen usw.

     Siehe Abschnitt [SOAP-Methoden in JavaScript](../../configuration/using/soap-methods-in-javascript.md).

* Content Management
* Abonnementverwaltung, siehe [Abonnieren (nms:subscription)](#subscribe--nms-subscription-) und [Abmeldung (nms:subscription)](#unsubscribe--nms-subscription-).
* Datenprozesse: Importe, Exporte.

In diesem Abschnitt wird die Verwendung der Dienste &quot;Abonnieren&quot;, &quot;Abmelden&quot;und &quot;SendenVersand&quot;beschrieben.

>[!IMPORTANT]
>
>[Dokumentation zu Campaign JSAPI](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=de) enthält zusätzliche Informationen zu SOAP-Aufrufen und zur Verwendung von JavaScript in Adobe Campaign sowie einen vollständigen Verweis auf alle in der Anwendung verwendeten Methoden und Funktionen.

## Abonnieren (nms:subscription) {#subscribe--nms-subscription-}

Mit diesem Dienst können Sie einen Empfänger für einen Informationsdienst anmelden und das Empfängerprofil aktualisieren.

Die folgenden Parameter sind erforderlich, um den Dienst aufzurufen:

* eine Authentifizierung,
* interner Name des Anmeldedienstes,
* ein XML-Dokument mit den Empfängerinformationen (aus dem Schema &quot;nms:recipient&quot;),
* einen booleschen Wert für die Empfängererstellung, falls noch keiner vorhanden ist.

Beschreibung der Methode &quot;subscribe&quot;im Schema &quot;nms:subscription&quot;:

```
<method name="Subscribe" static="true">
  <parameters>
     <param name="serviceName" type="string"  desc="List of information service names (comma separated)"/>
     <param name="recipient" type="DOMElement" desc="Recipient"/>
     <param name="create" type="Boolean" desc="Create recipient if it does not exist"/>
   </parameters>
</method>
```

Die Definition des Abstimmschlüssels muss über _ eingegeben werden **key** -Attribut in der `<recipient>` -Element des XML-Dokuments. Der Inhalt dieses Attributs ist eine kommagetrennte XPath-Liste.

Mit Ausnahme von Fehlern gibt dieser Aufruf keine Daten zurück.

### Beispiele {#examples}

Anmeldung mit Empfänger-Abstimmschlüssel in der E-Mail-Adresse: Das XML-Eingabedokument muss auf die E-Mail-Adresse und die Definition des Schlüssels in diesem Feld verweisen.

```
<recipient _key="email" email= "john.doe@adobe.com"/>
```

Aktualisieren des Empfängers sowie des Abonnements

```
<recipient _key="email, [folder-id]" email= "john.doe@adobe.com" folder-id="1305" firstName="John" lastName="Doe"/>
```

### Beispiel für SOAP-Nachrichten {#example-of-soap-messages}

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

## Abmeldung (nms:subscription) {#unsubscribe--nms-subscription-}

Mit diesem Dienst können Sie einen Empfänger von einem Informationsdienst abmelden und das Empfängerprofil aktualisieren.

Die folgenden Parameter sind erforderlich, um den Dienst aufzurufen:

* eine Authentifizierung,
* Interner Name des Dienstes, von dem sich abmelden soll,
* ein XML-Dokument mit den Empfängerinformationen (aus dem Schema &quot;nms:recipient&quot;),

Beschreibung der Methode &quot;Unsubscribe&quot;im Schema &quot;nms:subscription&quot;:

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>
```

Die Definition des Abstimmschlüssels muss über das Attribut _key im `<recipient>` -Element des XML-Dokuments. Der Inhalt dieses Attributs ist eine kommagetrennte XPath-Liste.

Wenn der Empfänger nicht in der Datenbank vorhanden ist oder nicht den entsprechenden Informationsdienst abonniert hat, führt der Dienst keine Aktion durch und erzeugt keinen Fehler.

>[!NOTE]
>
>Wenn der Dienstname nicht als Parameter angegeben ist, wird der Empfänger automatisch auf der Blockierungsliste &quot;&quot;(@blackList=&quot;1&quot;) gespeichert.

Mit Ausnahme von Fehlern gibt dieser Aufruf keine Daten zurück.

### Beispiel für SOAP-Nachrichten {#example-of-soap-messages-1}

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

## SubmitDelivery (nms:delivery) {#submitdelivery--nms-delivery-}

Mit diesem Dienst können Sie eine Versandaktion erstellen und senden.

Die folgenden Parameter sind erforderlich, um den Dienst aufzurufen:

* eine Authentifizierung,
* interner Name der Versandvorlage,
* ein optionales XML-Dokument, das zusätzliche Versanddaten enthält.

Diese API sollte nicht vollständig aufgerufen werden, da Leistungsprobleme auftreten können.

Beschreibung der Methode in ihrem Schema:

```
<method name="SubmitDelivery" static="true">
  <parameters>
    <param name="scenarioName" type="string" inout="in" desc="Internal name of the delivery template"/>
    <param name="content" type="DOMElement"  inout="in" desc="XML content of the delivery template" />
  </parameters>
</method>
```

In der Adobe Campaign-Clientkonsole muss eine Versandvorlage erstellt werden. Sie enthält die für alle Sendungen gemeinsamen Parameter (Absenderadresse oder Gültigkeitsdauer der Nachricht).

Das XML-Eingabedokument ist ein Versandvorlagenfragment, das der Struktur des Schemas &quot;nms:delivery&quot;entspricht. Sie enthält alle zusätzlichen Daten, die nicht statisch in der Versandvorlage definiert werden konnten (z. B. die Liste der Zielgruppenempfänger).

Mit Ausnahme von Fehlern gibt dieser Aufruf keine Daten zurück.

### Beispiel für XML-Dokument {#xml-document-example}

Dieses Beispiel basiert auf einer benutzerdefinierten Versandvorlage aus einer externen Datenquelle (in diesem Fall eine Datei). Die Konfiguration wird in der Versandvorlage ausführlich beschrieben, sodass nur der Inhalt der Datei aus dem `<externalsource>` -Element.

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

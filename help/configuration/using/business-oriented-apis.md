---
product: campaign
title: Geschäftsorientierte APIs
description: Geschäftsorientierte APIs
feature: API
role: Developer
exl-id: e6638870-3141-4f12-b904-db436127c0d1
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 2%

---

# Geschäftsorientierte APIs{#business-oriented-apis}

Business-APIs sind für jeden Objekttyp spezifisch. Sie haben Auswirkungen auf:

* Sendungen:

   * Informationen zum Erstellen einer Versandaktion finden Sie unter [SubmitDelivery (nms:delivery)](#submitdelivery--nms-delivery-),
   * Senden einer Kampagne (Starten, Pausieren, Stoppen, Testversand),
   * Abruf der Versandlogs

* Workflows:

   * Starten eines Workflows,
   * Überprüfen von Prozessen usw.

     Siehe [SOAP-Methoden in JavaScript](../../configuration/using/soap-methods-in-javascript.md).

* Content-Management
* Abonnementverwaltung, siehe [Abonnieren (nms:subscription)](#subscribe--nms-subscription-) und [Abmelden (nms:subscription)](#unsubscribe--nms-subscription-).
* Datenprozesse: Importe, Exporte.

In diesem Abschnitt wird die Verwendung der Services „Abonnieren“, „Abmelden“ und „SubmitDelivery“ beschrieben.

>[!IMPORTANT]
>
>[Campaign JSAPI](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=de)Dokumentation) enthält zusätzliche Informationen zu SOAP-Aufrufen und zur Verwendung von JavaScript in Adobe Campaign sowie einen vollständigen Verweis auf alle Methoden und Funktionen, die in der Anwendung verwendet werden.

## Abonnieren (nms:subscription) {#subscribe--nms-subscription-}

Mit diesem Service können Sie einen Empfänger für einen Informations-Service anmelden und das Empfängerprofil aktualisieren.

Die folgenden Parameter sind erforderlich, um den Service aufzurufen:

* einer Authentifizierung,
* Interner Name des Anmeldedienstes,
* ein XML-Dokument, das die Empfängerinformationen enthält (aus dem Schema &quot;:recipient„),
* Ein boolescher Wert für die Empfängererstellung, falls noch kein solcher vorhanden ist.

Beschreibung der Methode „subscribe“ im Schema „nms:subscription:

```
<method name="Subscribe" static="true">
  <parameters>
     <param name="serviceName" type="string"  desc="List of information service names (comma separated)"/>
     <param name="recipient" type="DOMElement" desc="Recipient"/>
     <param name="create" type="Boolean" desc="Create recipient if it does not exist"/>
   </parameters>
</method>
```

Die Definition des Abstimmschlüssels muss über das Attribut _**key** im `<recipient>` des XML-Dokuments eingegeben werden. Der Inhalt dieses Attributs ist eine kommagetrennte XPath-Liste.

Dieser Aufruf gibt keine Daten zurück, mit Ausnahme von Fehlern.

### Beispiele {#examples}

Abonnement mit Empfänger-Abstimmschlüssel in der E-Mail-Adresse: Das XML-Eingabedokument muss auf die E-Mail-Adresse und die Definition des Schlüssels in diesem Feld verweisen.

```
<recipient _key="email" email= "john.doe@adobe.com"/>
```

Aktualisieren der Empfängerin bzw. des Empfängers sowie des Abonnements

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

## Abmelden (nms:subscription) {#unsubscribe--nms-subscription-}

Mit diesem Service können Sie ein Abonnement für einen Empfänger von einem Informations-Service kündigen und das Empfängerprofil aktualisieren.

Die folgenden Parameter sind erforderlich, um den Service aufzurufen:

* einer Authentifizierung,
* Interner Name des Services, für den das Abonnement beendet werden soll,
* ein XML-Dokument, das die Empfängerinformationen enthält (aus dem Schema &quot;:recipient„),

Beschreibung der Methode „Unsubscribe“ im Schema „nms:subscription:

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>
```

Die Definition des Abstimmschlüssels muss über das Attribut _key im `<recipient>` des XML-Dokuments eingegeben werden. Der Inhalt dieses Attributs ist eine kommagetrennte XPath-Liste.

Wenn der Empfänger nicht in der Datenbank vorhanden oder den betreffenden Informationsdienst nicht abonniert hat, führt der Dienst keine Aktion durch und erzeugt keinen Fehler.

>[!NOTE]
>
>Wenn der Service-Name nicht als Parameter angegeben wird, wird der Empfänger automatisch auf Blockierungsliste (@blackList=„1„) angezeigt.

Dieser Aufruf gibt keine Daten zurück, mit Ausnahme von Fehlern.

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

Mit diesem Service können Sie eine Versandaktion erstellen und senden.

Die folgenden Parameter sind erforderlich, um den Service aufzurufen:

* einer Authentifizierung,
* interner Name der Versandvorlage,
* ein optionales XML-Dokument mit zusätzlichen Versanddaten.

Diese API sollte nicht in großen Mengen aufgerufen werden, da dies zu Leistungsproblemen führen kann.

Beschreibung der Methode in ihrem Schema:

```
<method name="SubmitDelivery" static="true">
  <parameters>
    <param name="scenarioName" type="string" inout="in" desc="Internal name of the delivery template"/>
    <param name="content" type="DOMElement"  inout="in" desc="XML content of the delivery template" />
  </parameters>
</method>
```

Über die Adobe Campaign-Client-Konsole muss eine Versandvorlage erstellt werden. Sie enthält die für alle Sendungen gemeinsamen Parameter (Absenderadresse oder Gültigkeitsdauer der Nachricht).

Das XML-Eingabedokument ist ein Fragment einer Versandvorlage, das der Struktur des Schemas „nms:delivery&quot; entspricht. Sie enthält alle zusätzlichen Daten, die nicht statisch in der Versandvorlage definiert werden konnten (z. B. Liste der an die Zielgruppe adressierten Empfänger).

Dieser Aufruf gibt keine Daten zurück, mit Ausnahme von Fehlern.

### Beispiel eines XML-Dokuments {#xml-document-example}

Dieses Beispiel basiert auf einer benutzerdefinierten Versandvorlage aus einer externen Datenquelle (in diesem Fall einer Datei). Die Konfiguration ist in der Versandvorlage vollständig beschrieben. Daher muss beim Aufruf nur noch der Inhalt der Datei aus dem `<externalsource>`-Element gesendet werden.

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

Wenn Sie keine Versandvorlage haben, können Sie folgendes Beispiel verwenden:

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

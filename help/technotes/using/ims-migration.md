---
title: Migration von technischen Benutzerinnen und Benutzern zur Adobe Developer Console
description: Erfahren Sie, wie Sie technische Campaign-Benutzerinnen bzw. -Benutzer zu einem technischen Konto in der Adobe Developer-Konsole migrieren.
feature: Technote
role: Admin
exl-id: 1a409daf-57be-43c9-a3d9-b8ab54c88068
source-git-commit: c63fea4d400440005ecf3733413c346bd4a2fd18
workflow-type: tm+mt
source-wordcount: '1748'
ht-degree: 91%

---

# Migration von technischen Campaign-Benutzerinnen und -Benutzern zur Adobe Developer Console {#migrate-tech-users-to-ims}

Um die Sicherheits- und Authentifizierungsprozesse zu verbessern, wird ab Campaign Classic v7.3.5 der Authentifizierungsprozess für Campaign Classic verbessert. Technische Benutzerinnen und Benutzer sollten jetzt das [Adobe Identity Management System (IMS)](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"} to connect to Campaign. Learn more about the new server to server authentication process in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/){target="_blank"} benutzen. **Adobe empfiehlt, diese Migration in Campaign v7.3.5 durchzuführen, um eine reibungslose Migration zu Campaign v8 zu ermöglichen.**

Eine technische Benutzerin bzw. ein technischer Benutzer ist ein Campaign-Benutzerprofil, das explizit für die API-Integration erstellt wurde. In diesem Artikel werden die Schritte beschrieben, die zum Migrieren einer technischen Benutzerin bzw. eines technischen Benutzers zu einem technischen Konto über die Adobe Developer Console erforderlich sind.

## Sind Sie betroffen?{#ims-impacts}

Wenn Sie API-Aufrufe von einem Campaign-externen System in die Campaign-Marketing-Instanz oder die Message-Center-Echtzeitinstanz durchführen, müssen Sie die technischen Benutzerinnen und Benutzer über die Adobe Developer Console in technische Konten migrieren, wie unten beschrieben.

Diese Änderung gilt ab Campaign Classic v7.3.5 (und für die neuesten [mit der IMS-Migration kompatiblen Versionen](#ims-versions-tech)) und ist **zwingend** für den Wechsel zu Adobe Campaign v8.

## Migrationsprozess {#ims-migration-procedure}

Führen Sie die folgenden Schritte aus, um technische Konten in der Adobe Developer Console zu erstellen und diese neu erstellten Konten zu verwenden, um die Authentifizierungsmethoden für alle externen Systeme zu ändern, die API-Aufrufe in Adobe Campaign tätigen.

Es folgt eine Übersicht über die Schritte:

* Erstellen Sie ein Projekt in der Adobe Developer Console
* Weisen Sie die entsprechenden APIs dem neu erstellten Projekt zu
* Weisen Sie die erforderlichen Campaign-Produktprofile dem Projekt zu
* Aktualisieren Sie die APIs für die Verwendung der neu erstellten technischen Kontoanmeldeinformationen
* Entfernen Sie die veralteten technischen Benutzerinnen und Benutzer aus Ihrer Campaign-Instanz


### Mit der IMS-Migration kompatible Versionen {#ims-versions-tech}

Voraussetzung für diese Migration ist die Aktualisierung Ihrer Umgebung auf eine der folgenden Produktversionen:

* Campaign v7.3.5 (empfohlen)
* Campaign v7.3.3.IMS
* Campaign v7.3.2.IMS

Diese Campaign-Versionen werden im Abschnitt [Versionshinweise](../../rn/using/latest-release.md) behandelt.

### Voraussetzungen für die Migration{#ims-migration-prerequisites}

<!--To be able to create the technical accounts which replace the technical operators, the prerequisite that the proper Campaign Product Profiles exist within the Admin Console for all Campaign instances need to be validated. You can learn more about Product Profiles within the Adobe Console in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}.-->

* Campaign-gehostete und Managed Services-Kundinnen und -Kunden

  Für API-Aufrufe in die Message-Center-Instanz(en) muss das Produktprofil (siehe unten) während der Aktualisierung auf Campaign v7.3.5 (oder andere) erstellt werden. [Kompatible Version der IMS-Migration](#ims-versions-tech)) oder während der Bereitstellung der Instanz. Wenn das Produktprofil nicht angezeigt wird, wenden Sie sich an Ihren Transition Manager oder an den Support, um das Produktprofil zu erhalten, bevor Sie mit der IMS-Migration beginnen. Dieses Produktprofil hat den Namen:

  `campaign - <your campaign marketing instance> - messagecenter`

  Wenn Sie bereits die IMS-basierte Authentifizierung für den Benutzerzugriff auf Campaign verwendet haben, sollten die für die API-Aufrufe erforderlichen Produktprofile bereits in der Admin Console vorhanden sein. Wenn Sie eine benutzerdefinierte Benutzergruppe in Campaign für die API-Aufrufe an die Marketing-Instanz verwenden, müssen Sie dieses Produktprofil in der Admin Console erstellen.

  Wenden Sie sich mit anderen Fällen an Ihre Adobe-Kontaktperson für Migrationen (Managed Services-Benutzende) oder an den Adobe-Kundendienst (anderweitig gehostete Benutzende), damit die technischen Teams von Adobe Ihre vorhandenen Benutzergruppen und spezifischen Berechtigungen in die Produktprofile in der Admin Console migrieren können.

* Lokale und hybride Campaign-Kundinnen und -Kunden

  Für API-Aufrufe in die Message-Center-Instanzen müssen Sie ein Produktprofil mit folgendem Namen erstellen:

  `campaign - <your campaign instance> - messagecenter`

  Wenn Sie bereits die IMS-basierte Authentifizierung für den Benutzerzugriff auf Campaign verwendet haben, sollten die für die API-Aufrufe erforderlichen Produktprofile bereits in der Admin Console vorhanden sein. Wenn Sie eine benutzerdefinierte Benutzergruppe in Campaign für die API-Aufrufe an die Marketing-Instanz verwenden, müssen Sie dieses Produktprofil in der Admin Console erstellen.

  Weitere Informationen zu Produktprofilen in der Adobe Console finden Sie in der [Dokumentation zur Adobe Developer Console](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}.


### Schritt 1: Erstellen Ihres Campaign-Projekts in der Adobe Developer Console {#ims-migration-step-1}

Integrationen werden im Rahmen eines **Projekts** in der Adobe Developer Console erstellt. Weitere Informationen zu Projekten sind in der [Dokumentation zur Adobe Developer Console](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"} zu finden.

Sie können jedes zuvor von Ihnen erstellte Projekt verwenden oder ein neues Projekt erstellen. Die Schritte zum Erstellen eines Projekts werden im Detail in der [Dokumentation zur Adobe Developer Console](https://developer.adobe.com/developer-console/docs/guides/getting-started/) beschrieben{target="_blank"}. Nachfolgend finden Sie die wichtigsten Schritte.

<!--
For this migration, you must add below APIs in your project: **I/O Management API** and **Adobe Campaign**.

![](assets/do-not-localize/ims-products-and-services.png)-->

Um ein neues Projekt zu erstellen, klicken Sie auf **Neues Projekt erstellen** auf dem Hauptbildschirm in der Adobe Developer Console.

![](assets/New-Project.png)

Sie können die Schaltfläche **Projekt bearbeiten** verwenden, um dieses Projekt umzubenennen.


### Schritt 2: Hinzufügen von APIs zu Ihrem Projekt {#ims-migration-step-2}

Fügen Sie im neu erstellten Projektbildschirm die erforderlichen APIs hinzu, um dieses Projekt als technisches Konto für Ihre API-Aufrufe an Adobe Campaign verwenden zu können.

Gehen Sie wie folgt vor, um Ihrem Projekt APIs hinzuzufügen:

1. Klicken Sie auf **API hinzufügen**, um die APIs auszuwählen, die zum Projekt hinzugefügt werden sollen.
   ![](assets/do-not-translate/ims-updates-01.png)
1. Wählen Sie die Adobe Campaign-API aus und fügen Sie sie zu Ihrem Projekt hinzu, indem Sie das Kontrollkästchen oben rechts auf der Adobe Campaign-Karte aktivieren, das angezeigt wird, wenn Sie den Mauszeiger über die Karte bewegen.
   ![](assets/do-not-translate/ims-updates-02.png)
1. Klicken Sie auf **Weiter** unten auf dem Bildschirm.

### Schritt 3: Authentifizierungstyp auswählen  {#ims-migration-step-3}

Wählen Sie auf dem Bildschirm **API konfigurieren** den benötigten Authentifizierungstyp aus. Die **OAuth-Server-zu-Server**-Authentifizierung ist für dieses Projekt erforderlich. Stellen Sie sicher, dass sie ausgewählt ist, und klicken Sie auf **Weiter** unten auf dem Bildschirm.

![](assets/do-not-translate/ims-updates-03.png)

<!--
Once your project is created in the Adobe Developer Console, add an API that uses Server-to-Server authentication. Learn how to set up the OAuth Server-to-Server credential in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/){target="_blank"}.

When the API has been successfully connected, you can access the newly generated credentials including Client ID and Client Secret, as well as generate an access token.-->

### Schritt 4: Produktprofile auswählen {#ims-migration-step-4}

Wie im Abschnitt „Voraussetzungen“ beschrieben, müssen Sie die entsprechenden Produktprofile zuweisen, die das Projekt verwenden soll. In diesem Schritt wählen Sie die Produktprofile, die das zu erstellende technische Konto verwenden soll.

Wenn dieses technische Konto zum Ausführen von API-Aufrufen an die Message-Center-Instanz verwendet wird, wählen Sie für die mit Message Center verknüpfte Marketinginstanz das Adobe-Produktprofil aus, das mit messageCenter endet.

Wählen Sie für API-Aufrufe an die Marketing-Instanz(en) das Produktprofil aus, das der Instanz entspricht, und z. B. Benutzergruppe `campaign - <your campaign marketing instance> - Admin`.

Klicken Sie nach Auswahl der gewünschten Produktprofile auf **Konfigurierte API speichern** unten auf dem Bildschirm.

<!--
You can now add your Campaign product profile to the project, as detailed below:

1. Open the Adobe Campaign API.
1. Click the **Edit product profiles** button

    ![](assets/do-not-localize/ims-edit-api.png)

1. Assign all the relevant Product Profiles to the API, for example 'messagecenter', and save your changes.
1. Browse to the **Credential details** tab of your project, and copy the **Technical Account Email** value.-->

### Schritt 5: Hinzufügen der I/O-Management-API zu Ihrem Projekt {#ims-migration-step-5}


Klicken Sie im Projektbildschirm auf **[!UICONTROL + Zum Projekt hinzufügen]** und wählen Sie **[!UICONTROL API]** oben links im Bildschirm, um die I/O-Management-API zu diesem Projekt hinzufügen zu können.

![](assets/do-not-translate/ims-updates-04.png)

Scrollen Sie auf dem Bildschirm **API hinzufügen** nach unten, um die Karte **I/O-Management-API** zu suchen. Wählen Sie sie aus, indem Sie auf das Kontrollkästchen klicken, das angezeigt wird, wenn Sie den Mauszeiger über die Karte bewegen. Klicken Sie anschließend auf **Weiter** unten auf dem Bildschirm.

![](assets/do-not-translate/ims-updates-05.png)


Im Bildschirm **API konfigurieren** ist die OAuth-Server-zu-Server-Authentifizierung bereits vorhanden. Klicken Sie auf **Konfigurierte API speichern** unten auf dem Bildschirm.


![](assets/do-not-translate/ims-updates-06.png)

Dadurch gelangen Sie zurück zum Projektbildschirm in der I/O-Management-API des neu erstellten Projekts. Klicken Sie oben im Bildschirm in den Breadcrumbs auf den Projektnamen, um zur Hauptseite mit den Projektdetails zurückzukehren.


### Schritt 6: Überprüfen der Projekteinrichtung {#ims-migration-step-6}

Überprüfen Sie Ihr Projekt, um sicherzustellen, dass es ähnlich wie das unten gezeigte aussieht, mit der **I/O-Management-API** und **Adobe Campaign-API** im Abschnitt „Produkte und Dienste“ sowie **OAuth-Server-zu-Server** im Abschnitt „Anmeldedaten“.

![](assets/do-not-translate/ims-updates-07.png)


### Schritt 7: Validieren der Konfiguration {#ims-migration-step-7}

Um die Verbindung zu testen, führen Sie die Schritte aus, die im [Handbuch zu den Anmeldedaten für die Adobe Developer Console](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/#generate-access-tokens){target="_blank"} zum Generieren eines Zugriffstokens beschrieben sind, und kopieren Sie den bereitgestellten Beispiel-cURL-Befehl. Sie können mithilfe dieser Anmeldedaten einen SOAP-Aufruf erstellen, um zu testen, ob Sie sich authentifizieren und eine korrekte Verbindung zu den Adobe Campaign-Instanzen herstellen können. Es wird empfohlen, diese Validierung durchzuführen, bevor alle Änderungen an den API-Integrationen von Drittanbieterfirmen vorgenommen werden.

### Schritt 8: Aktualisieren der API-Integrationen von Drittanbieterfirmen {#ims-migration-step-8}

Sie müssen jetzt die API-Integrationen aktualisieren, die Aufrufe an Adobe Campaign tätigen, um das neu erstellte technische Konto zu verwenden.

Weitere Informationen zu den Schritten zur API-Integration finden Sie in den folgenden Codebeispielen.

>[!BEGINTABS]

>[!TAB SOAP-Aufruf]

```
curl --location --request POST 'https://<instance_name>.campaign.adobe.com/nl/jsp/soaprouter.jsp' \
--header 'Content-Type: text/xml; charset=utf-8' \
--header 'SOAPAction: xtk:queryDef#ExecuteQuery' \
--header 'Authorization: Bearer eyJhw' \
--data-raw '<?xml version="1.0" encoding="utf-8"?>
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <ExecuteQuery xmlns="urn:xtk:queryDef">
            <sessiontoken></sessiontoken>
            <entity>
                <queryDef schema="nms:recipient" operation="select">
                    <!-- fields to retrieve -->
                    <select>
                        <node expr="@lastName"/>
                        <node expr="@email"/>
                        <node expr="@firstName"/>
                    </select>
                    <!-- condition on email -->
                    <!-- <where><condition expr="@email= '\''joh@com.com'\''"/>
                </where> -->
                </queryDef>
            </entity>
        </ExecuteQuery>
  </soap:Body>
</soap:Envelope>
'
```

>[!TAB  SampleCode Java]

```javascript
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import com.google.gson.Gson;
import com.google.gson.JsonObject;
 
import com.google.gson.JsonSyntaxException;
import org.apache.hc.client5.http.classic.methods.HttpPost;
import org.apache.hc.client5.http.impl.classic.CloseableHttpClient;
import org.apache.hc.client5.http.impl.classic.CloseableHttpResponse;
import org.apache.hc.client5.http.impl.classic.HttpClients;
import org.apache.hc.core5.http.HttpEntity;
import org.apache.hc.core5.http.io.entity.StringEntity;
 
 
public class TAAccessToken {
    public static void main(String[] args) throws IOException {
        String accessToken = null;
        CloseableHttpClient httpClient = HttpClients.createDefault();
        try {
            HttpPost httpPost = new HttpPost("https://ims-na1.adobelogin.com/ims/token/v3");
 
            // Request headers
            httpPost.addHeader("Content-Type", "application/x-www-form-urlencoded");
 
            String clientId = "<client_id>";
            String clientSecret = "<client_secret>";
            String scopes = "<scopes>";
 
            // Define the request body
            String requestBody = "client_id="+clientId+"&client_secret="+clientSecret+"&grant_type=client_credentials&scope="+scopes+"";
            StringEntity requestEntity = new StringEntity(requestBody);
            httpPost.setEntity(requestEntity);
 
            // Execute the request
            CloseableHttpResponse response = httpClient.execute(httpPost);
            try {
                // Get the response entity
                HttpEntity entity = response.getEntity();
                int responseCode = response.getCode();
 
                // Print the response
                if (entity != null) {
                    BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(entity.getContent()));
                    String lineImsToken;
                    StringBuilder responseImsToken = new StringBuilder();
                    while ((lineImsToken = bufferedReader.readLine()) != null) {
                        responseImsToken.append(lineImsToken);
                    }
 
                    String jsonString = responseImsToken.toString();
 
                    try {
                        Gson gson = new Gson();
                        JsonObject jsonObject = gson.fromJson(jsonString, JsonObject.class);
 
                        // Get the value of a specific key
                        accessToken = jsonObject.get("access_token").getAsString();
                    }
                    catch (JsonSyntaxException | NullPointerException e) {
                        System.err.println("Error parsing JSON: " + e.getMessage());
                        e.printStackTrace();
                    }
                    System.out.println("Response Code: " + responseCode);
                    System.out.println("Response Body: " + accessToken);
                }
            } catch (IOException e) {
                e.printStackTrace();
            } finally {
                response.close();
            }
        } finally {
            httpClient.close();
        }
 
        CloseableHttpClient httpClientSoap = HttpClients.createDefault();
        try {
            HttpPost httpPostSoap = new HttpPost("https://<instance_name>.campaign.adobe.com/nl/jsp/soaprouter.jsp");
 
            // Request headers
            httpPostSoap.addHeader("Content-Type", "text/xml; charset=utf-8");
            httpPostSoap.addHeader("SOAPAction", "xtk:queryDef#ExecuteQuery");
            httpPostSoap.addHeader("Authorization", "Bearer "+accessToken);
 
            // Request body
            String xmlData = "<?xml version=\"1.0\" encoding=\"utf-8\"?>\n" +
                    "<soap:Envelope xmlns:soap=\"http://schemas.xmlsoap.org/soap/envelope/\">\n" +
                    "  <soap:Body>\n" +
                    "    <ExecuteQuery xmlns=\"urn:xtk:queryDef\">\n" +
                    "            <sessiontoken></sessiontoken>\n" +
                    "            <entity>\n" +
                    "                <queryDef schema=\"nms:recipient\" operation=\"select\">\n" +
                    "                    <!-- fields to retrieve -->\n" +
                    "                    <select>\n" +
                    "                        <node expr=\"@lastName\"/>\n" +
                    "                        <node expr=\"@email\"/>\n" +
                    "                        <node expr=\"@firstName\"/>\n" +
                    "                    </select>\n" +
                    "                    <!-- condition on email -->\n" +
                    "                    <!-- <where><condition expr=\"@email= '\''joh@com.com'\''\"/>\n" +
                    "                </where> -->\n" +
                    "                </queryDef>\n" +
                    "            </entity>\n" +
                    "        </ExecuteQuery>\n" +
                    "  </soap:Body>\n" +
                    "</soap:Envelope>";
            StringEntity requestEntity = new StringEntity(xmlData);
            httpPostSoap.setEntity(requestEntity);
 
            // Execute the request
            CloseableHttpResponse response = httpClientSoap.execute(httpPostSoap);
            try {
                // Get the response entity
                HttpEntity entity = response.getEntity();
 
                // Print the response
                if (entity != null) {
                    BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(entity.getContent()));
                    String line;
                    while ((line = bufferedReader.readLine()) != null) {
                        System.out.println(line);
                    }
                }
            } catch (IOException e) {
                e.printStackTrace();
            } finally {
                response.close();
            }
        } finally {
            httpClientSoap.close();
        }
 
    }
}
```

>[!TAB SampleCodePython]

```python
import requests
 
oauth_url = 'https://ims-na1.adobelogin.com/ims/token/v3'
data = {
    'grant_type': 'client_credentials',
    'scope': '<scopes>',
    'client_id': '<client_id>',
    'client_secret': '<client_secret>'
}
 
headers = {
    'Content-Type': 'application/x-www-form-urlencoded',
    'Accept': 'application/json'
}
response = requests.post(oauth_url, data=data, headers=headers)
response = response.json()
access_token = response['access_token']
 
 
url = 'https://<instance_name>.campaign.adobe.com/nl/jsp/soaprouter.jsp'
headers = {
    'Content-Type': 'text/xml; charset=utf-8',
    'SOAPAction': 'xtk:queryDef#ExecuteQuery',
    'Authorization': 'Bearer '+access_token
}
xml_data = '''<?xml version="1.0" encoding="utf-8"?>
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <ExecuteQuery xmlns="urn:xtk:queryDef">
            <sessiontoken></sessiontoken>
            <entity>
                <queryDef schema="nms:recipient" operation="select">
                    <!-- fields to retrieve -->
                    <select>
                        <node expr="@lastName"/>
                        <node expr="@email"/>
                        <node expr="@firstName"/>
                    </select>
                    <!-- condition on email -->
                    <!-- <where><condition expr="@email= '\''joh@com.com'\''"/>
                </where> -->
                </queryDef>
            </entity>
        </ExecuteQuery>
  </soap:Body>
</soap:Envelope>
'''
response = requests.post(url, headers=headers, data=xml_data)
```

>[!ENDTABS]

Weitere Informationen finden Sie unter [Dokumentation zur Authentifizierung der Adobe Developer Console](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/){target="_blank"}.

Im Folgenden finden Sie Beispiele für SOAP-Aufrufe, die die Aufrufe vor und nach der Migration für die Systeme von Drittanbietern zeigen.

Sobald der Migrationsprozess erreicht und validiert wurde, werden die SOAP-Aufrufe wie folgt aktualisiert:

* Vor der Migration: Zugriffstoken für technische Konten wurden nicht unterstützt.

  ```sql
  POST /nl/jsp/soaprouter.jsp HTTP/1.1
  Host: localhost:8080
  Content-Type: application/soap+xml;
  SOAPAction: "nms:rtEvent#PushEvent"
  charset=utf-8
  
  <?xml version="1.0" encoding="utf-8"?>  <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
  <soapenv:Header/>
  <soapenv:Body>
      <urn:PushEvent>
          <urn:sessiontoken>SESSION_TOKEN</urn:sessiontoken>
          <urn:domEvent>
              <!--You may enter ANY elements at this point-->
              <rtEvent type="type" email="name@domain.com"/>
          </urn:domEvent>
      </urn:PushEvent>
  </soapenv:Body>
  </soapenv:Envelope>
  ```

* Nach der Migration: Zugriffstoken für technische Konten werden unterstützt. Es wird erwartet, dass das Zugriffstoken in der `Authorization` Kopfzeile als Bearer-Token angegeben wird. Die Verwendung eines Sitzungs-Tokens sollte hier ignoriert werden, wie im folgenden Beispiel für einen SOAP-Aufruf dargestellt.

  ```sql
  POST /nl/jsp/soaprouter.jsp HTTP/1.1
  Host: localhost:8080
  Content-Type: application/soap+xml;
  SOAPAction: "nms:rtEvent#PushEvent"
  charset=utf-8
  Authorization: Bearer <IMS_Technical_Token_Token>
  
  <?xml version="1.0" encoding="utf-8"?>  <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
  <soapenv:Header/>
  <soapenv:Body>
      <urn:PushEvent>
          <urn:sessiontoken></urn:sessiontoken>
          <urn:domEvent>
              <!--You may enter ANY elements at this point-->
              <rtEvent type="type" email="name@domain.com"/>
          </urn:domEvent>
      </urn:PushEvent>
  </soapenv:Body>
  </soapenv:Envelope>
  ```



### Schritt 9: (optional) Aktualisieren der technischen Kontenbenutzenden in der Campaign Client Console {#ims-migration-step-9}

Dieser Schritt ist optional und nur innerhalb der Marketing-Instanz(en) verfügbar, nicht aber in einer Message Center-Instanz. Wenn spezifische Ordnerberechtigungen oder spezifische Berechtigungen für die technischen Benutzenden nicht über die zugewiesene(n) Benutzergruppe(n) definiert wurden. Sie müssten jetzt die neu erstellten Benutzenden des technischen Kontos in der Admin Console aktualisieren, um die erforderlichen Ordnerberechtigungen oder spezifischen Berechtigungen zu erteilen.

Beachten Sie, dass die Benutzenden des technischen Kontos so lange NICHT in Adobe Campaign vorhanden sind, bis mindestens ein API-Aufruf an die Campaign-Instanz erfolgt. Zu diesem Zeitpunkt erstellt IMS die Benutzenden in Campaign. Wenn Sie die technischen Benutzenden in Campaign nicht finden können, stellen Sie sicher, dass Sie erfolgreich einen API-Aufruf senden konnten, wie [in Schritt 7](#ims-migration-step-7) beschrieben.

1. Um die für die neuen Benutzenden des technischen Kontos erforderlichen Änderungen anzuwenden, suchen Sie diese in der Campaign Client Console nach E-Mail-Adresse. Diese E-Mail-Adresse wurde während der obigen Schritte zur Projekterstellung und -authentifizierung erstellt.

   Klicken Sie auf die Überschrift **OAuth-Server-zu-Server** im Abschnitt **Anmeldeinformationen** des Projekts, um diese E-Mail-Adresse zu finden.

   ![](assets/do-not-translate/ims-updates-07.png)

   Scrollen Sie im Bildschirm **Anmeldedaten** nach unten, um die **E-Mail-Adresse des technischen Kontos** zu suchen, und klicken Sie auf die Schaltfläche **Kopieren**.

   ![](assets/do-not-translate/ims-updates-08.png)

1. Sie müssen jetzt den neu erstellten technischen Benutzer bzw. die Benutzerin in der Adobe Campaign-Client-Konsole aktualisieren. Sie müssen die bestehenden Berechtigungen für den Ordner des technischen Benutzers bzw. der Benutzerin auf die neue Person übertragen.

   Gehen Sie wie folgt vor, um diesen Benutzer bzw. diese Benutzerin zu aktualisieren:

   1. Navigieren Sie im Explorer der Campaign-Client-Konsole zu **Administration > Zugriffsverwaltung > Benutzer**.
   1. Greifen Sie auf den bestehenden technischen Benutzer bzw. die technische Benutzerin zu, der bzw. die für APIs verwendet wird.
   1. Navigieren Sie zu den Ordnerberechtigungen und überprüfen Sie die Berechtigungen.
   1. Wenden Sie dieselben Berechtigungen auf den neu erstellten technischen Benutzer bzw. die neu erstellte technische Benutzerin an. Die E-Mail-Adresse dieser Benutzerin bzw. dieses Benutzers ist der Wert der **E-Mail für technische Konten**, der zuvor kopiert wurde.
   1. Speichern Sie Ihre Änderungen.


>[!CAUTION]
>
>Der neue technische Benutzer bzw. die Benutzerin muss mindestens einen API-Aufruf durchgeführt haben, damit er der Campaign-Client-Konsole hinzugefügt werden kann.
>

### Schritt 10: Entfernen der alten technischer Benutzenden aus Adobe Campaign {#ims-migration-step-10}

Sobald Sie alle Drittanbietersysteme migriert haben, um das neue technische Konto mit IMS-Authentifizierung zu verwenden, können Sie die alten technischen Benutzenden aus der Campaign-Client-Konsole löschen.

Melden Sie sich dazu bei der Campaign-Client-Konsole an und navigieren Sie zu **Administration > Zugriffsverwaltung > Benutzer**, wo Sie die alten technischen Benutzenden finden und löschen können.

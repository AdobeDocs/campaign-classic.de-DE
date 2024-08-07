---
product: campaign
title: Richtlinien für Script-Erstellung und Codierung
description: Erfahren Sie mehr über die Richtlinien für die Entwicklung in Adobe Campaign (Workflows, JavaScript, JSSP usw.).
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 1f96c3df-0ef2-4f5f-9c36-988cbcc0769f
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 29%

---

# Richtlinien für Script-Erstellung und Codierung {#scripting-coding-guidelines}



## Scripts

Weiterführende Informationen finden Sie in der [JSAPI-Dokumentation für Campaign](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=de).

Wenn Sie Scripts mit Workflows, Webanwendungen und JSSP verwenden, folgen Sie diesen Best Practices:

* Vermeiden Sie möglichst SQL-Anweisungen.

* Verwenden Sie bei Bedarf parametrierte Funktionen (prepare-Anweisung) anstelle von String-Konkatenation.

  Schlechte Praxis:

  ```
  sqlGetInt( "select iRecipientId from NmsRecipient where sEmail ='" + request.getParameter('email') +  "'  limit 1" )
  ```

  Gute Praxis:

  ```
  sqlGetInt( "select iRecipientId from NmsRecipient where sEmail = $(sz) limit 1", request.getParameter('email'));
  ```

  >[!IMPORTANT]
  >
  >sqlSelect unterstützt diese Funktion nicht, daher müssen Sie die Abfragefunktion der DBEngine-Klasse verwenden:

  ```
  var cnx = application.getConnection()
  var stmt = cnx.query("SELECT sFirstName, sLastName FROM NmsRecipient where sEmail = $(sz)", request.getParameter('email'))
  for each(var row in stmt) logInfo(row[0] + " : " + row[1])
  cnx.dispose()
  ```

Um SQL-Injections zu vermeiden, müssen der Zulassungsliste SQL-Funktionen hinzugefügt werden, die in Adobe Campaign verwendet werden sollen. Nachdem sie der Zulassungsliste hinzugefügt wurden, werden sie für Ihre Operatoren im Ausdruckseditor sichtbar. Mehr dazu erfahren Sie auf [dieser Seite](../../configuration/using/adding-additional-sql-functions.md).

>[!IMPORTANT]
>
>Wenn Sie einen Build verwenden, der älter als 8140 ist, kann die Option **XtkPassUnknownSQLFunctionsToRDBMS** auf &quot;1&quot;gesetzt sein. Wenn Sie Ihre Datenbank sichern möchten, löschen Sie diese Option (oder legen Sie sie auf &quot;0&quot;fest).

Wenn Sie Benutzereingaben zum Erstellen von Filtern in Abfragen oder SQL-Anweisungen verwenden, müssen Sie diese immer maskieren (siehe die [Dokumentation zu Campaign JSAPI](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=de) - Datenschutz: Escaping-Funktionen). Diese Funktionen sind:

* NL.XML.escape(data)
* NL.SQL.escape(data)
* NL.JS.escape(data)
* NL.XML.escapeAttribute(data)

## Schutz Ihres neuen Datenmodells

### Ordnerbasis

Weitere Informationen finden Sie auf diesen Seiten:

* [Ordnerzugriffseigenschaften](../../platform/using/access-management.md)
* [Verknüpfte Ordner](../../configuration/using/configuration.md#linked-folder)

### Spezifische Berechtigungen

Zusätzlich zum ordnerbasierten Sicherheitsmodell können Sie Benutzeraktionen auch mit spezifischen Berechtigungen einschränken:

* Sie können einige Systemfilter (sysFilter) hinzufügen, um das Lesen/Schreiben Ihrer Daten zu verhindern (siehe [diese Seite](../../configuration/using/filtering-schemas.md)).

  ```
  <sysFilter name="writeAccess">    
      <condition enabledIf="hasNamedRight('myNewRole')=false" expr="FALSE"/>  
  </sysFilter>
  ```

* Sie können auch einige Aktionen (SOAP Methode) schützen, die in Schemas definiert sind. Legen Sie einfach das Zugriffsattribut mit der entsprechenden benannten Berechtigung als Wert fest.

  ```
  <method name="grantVIPAccess" access="myNewRole">
      <parameters>
  ...
      </parameters>
  </method>
  ```

  Weitere Informationen hierzu finden Sie auf [dieser Seite](../../configuration/using/implementing-soap-methods.md).

>[!IMPORTANT]
>
>Sie können spezifische Berechtigungen im Befehlsknoten in einem Navigationsbaum verwenden. Es bietet ein besseres Benutzererlebnis, bietet jedoch keinen Schutz (nur clientseitig verwenden, um sie auszublenden/zu deaktivieren). Sie müssen das Zugriffsattribut verwenden.

### Überlauftabelle

Wenn Sie vertrauliche Daten (Teil eines Schemas) je nach Zugriffsebene des Benutzers schützen müssen, sollten Sie sie nicht in der Formulardefinition ausblenden (Bedingungen enabledIf/visibleIf ).

Die gesamte Entität wird vom Bildschirm geladen. Sie können sie auch in der Spaltendefinition anzeigen. Erstellen Sie hierzu eine Überlauftabelle. Sehen Sie [diese Seite](../../configuration/using/examples-of-schemas-edition.md#overflow-table).

## Hinzufügen von Captchas in Webanwendungen

Es ist empfehlenswert, öffentlichen Landingpages und Anmeldeseiten ein Captcha hinzuzufügen. Leider ist dies in DCE-Seiten (Digital Content Editor) nicht einfach. Wir zeigen Ihnen, wie Sie ein v5 Captcha oder ein Google reCAPTCHA hinzufügen.

Im DCE wird ein Captcha im Allgemeinen hinzugefügt, indem ein Gestaltungsbaustein erstellt wird, der ihn einfach in den Seiteninhalt einbezieht. Sie müssen eine **Script** -Aktivität und einen **Test** hinzufügen.

### Gestaltungsbaustein

1. Gehen Sie zu **[!UICONTROL Ressourcen]** > **[!UICONTROL Kampagnenverwaltung]** > **[!UICONTROL Gestaltungsbausteine]** und erstellen Sie einen neuen Gestaltungsbaustein.

1. Verwenden Sie den Inhaltstyp **[!UICONTROL Webanwendung]** und aktivieren Sie die Option **[!UICONTROL In den Personalisierungsmenüs sichtbar]**.

   Weitere Informationen dazu finden Sie auf [dieser Seite](../../delivery/using/personalization-blocks.md).

   Dies ist ein Beispiel für ein **Kampagnen-Captcha**:

   ```javascript
   <%
   var captchaID = CaptchaIDGen();
   %>
   <img src="/nms/jsp/captcha.jsp?captchaID=<%=captchaID%>&width=200&height=50&minWordSize=8&maxWordSize=8"/>
   <input id="captchaValue" name="captchaValue" <%= String(ctx.vars.captchaValid) === "false" ? class="ui-state-error" : "" %>>
   <input type="hidden" name="captchaID" value="<%=captchaID%>"/>
   <%
   if( serverForm.isInputErroneous("captchaValue") ) {
   %>
   <script type="text/javascript"> 
   $("#captchaValue").addClass("ui-state-error")
   </script>
   <%
   }
   %>
   ```

   * Mit den Zeilen 1 bis 6 werden alle erforderlichen Eingaben erzeugt.
   * Mit den Zeilen 7 bis zum Ende werden Fehler gehandhabt.
   * Mit Zeile 4 können Sie die Größe des grauen Captcha-Felds (Breite/Höhe) und die Länge des generierten Wortes (minWordSize/maxWordSize) ändern.
   * Bevor Sie Google reCAPTCHA verwenden, müssen Sie sich bei Google registrieren und eine neue reCAPTCHA-Site erstellen.

     `<div class="g-recaptcha" data-sitekey="YOUR_SITE_KEY"></div>`

   Sie sollten die Validierungsschaltfläche deaktivieren können, aber da wir keine Standardschaltfläche/keinen Standardlink haben, ist es besser, dies auf der HTML selbst zu tun. Weiterführende Informationen dazu finden Sie auf [dieser Seite](https://developers.google.com/recaptcha/).

### Webanwendung aktualisieren

1. Greifen Sie auf die Eigenschaften Ihrer Webanwendung zu, um eine boolesche Variable namens **captchaValid** hinzuzufügen.

   ![](assets/scripting-captcha.png)

1. Fügen Sie zwischen der letzten Seite und der Aktivität **[!UICONTROL Speicherung]** ein **[!UICONTROL Skript]** und einen **[!UICONTROL Test]** hinzu.

   Verbinden Sie den Zweig **[!UICONTROL True]** mit dem **[!UICONTROL Speicher]** und den anderen mit der Seite, die das Captcha aufweisen soll.

   ![](assets/scripting-captcha2.png)

1. Bearbeiten Sie die Bedingung der Verzweigung True mit `"[vars/captchaValid]"` gleich True .

   ![](assets/scripting-captcha3.png)

1. Bearbeiten Sie die Aktivität **[!UICONTROL Script]** . Der Inhalt hängt von der ausgewählten Captcha-Engine ab.

1. Schließlich können Sie Ihren personalisierten Baustein zur Seite hinzufügen: siehe [diese Seite](../../web/using/editing-content.md).

   ![](assets/scripting-captcha4.png)

   ![](assets/scripting-captcha5.png)

>[!IMPORTANT]
>
>Für die reCAPTCHA-Integration müssen Sie clientseitige JavaScript in der HTML hinzufügen (in `<head>...</head>`):
>
>`<script src="https://www.google.com/recaptcha/api.js" async defer></script>`

### Campaign Captcha

```javascript
var captchaID = request.getParameter("captchaID");
var captchaValue = request.getParameter("captchaValue");
  
if( !CaptchaValidate(captchaID, captchaValue) ) {
  serverForm.logInputError("captchaValue",
                           "The characters you typed for the captcha must match the image ones.",
                           "captchaValue")
  ctx.vars.captchaValid = false
}
else
  ctx.vars.captchaValid = true
```

Zeile 6: Sie können eine beliebige Fehlermeldung eingeben.

### Google recaptcha

Weitere Informationen finden Sie in der [offiziellen Dokumentation](https://developers.google.com/recaptcha/docs/verify).

```javascript
ctx.vars.captchaValid = false
var gReCaptchaResponse = request.getParameter("g-recaptcha-response");
  
// Call reCaptcha API to validate it
var req = new HttpClientRequest("https://www.google.com/recaptcha/api/siteverify")
req.method = "POST"
req.header["Content-Type"] = "application/x-www-form-urlencoded"
req.body = "secret=YOUR_SECRET_HERE&response=" + encodeURIComponent(gReCaptchaResponse)
req.execute()
var response = req.response
if( response.code == 200 ) {
  captchaRes = JSON.parse(response.body.toString(response.codePage));
  ctx.vars.captchaValid = captchaRes.success
}
  
if( ctx.vars.captchaValid == false ) {
  serverForm.logInputError("reCaptcha",
                           "Please validate the captcha",
                           "reCaptcha")
  logInfo("reCaptcha not validated")
}
```

Um JSON.parse zu verwenden, müssen Sie &quot;shared/json2.js&quot; in Ihre Webapp integrieren:

![](assets/scripting-captcha6.png)

Seit Build 8797 müssen Sie zur Verwendung der Verifizierungs-API-URL sie der Zulassungsliste in der Datei serverConf hinzufügen, indem Sie sie im Knoten urlPermission hinzufügen:

`<url dnsSuffix="www.google.com" urlRegEx="https://www.google.com/recaptcha/api/siteverify"/>`

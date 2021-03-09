---
solution: Campaign Classic
product: campaign
title: Richtlinien für Skripterstellung und Kodierung
description: Erfahren Sie mehr über die Richtlinien, die bei der Entwicklung in Adobe Campaign befolgt werden müssen (Workflows, Javascript, JSSP usw.).
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 48%

---


# Richtlinien für Skripterstellung und Kodierung {#scripting-coding-guidelines}

## Scripts

Weiterführende Informationen finden Sie in der [JSAPI-Dokumentation für Campaign](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).

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
   >sqlSelect unterstützt diese Funktion nicht. Daher müssen Sie die Abfrage-Funktion der DBEngine-Klasse verwenden:

   ```
   var cnx = application.getConnection()
   var stmt = cnx.query("SELECT sFirstName, sLastName FROM NmsRecipient where sEmail = $(sz)", request.getParameter('email'))
   for each(var row in stmt) logInfo(row[0] + " : " + row[1])
   cnx.dispose()
   ```

Um SQL-Injections zu vermeiden, müssen SQL-Funktionen auf die Zulassungsliste gesetzt werden, damit sie in Adobe Campaign verwendet werden können. Sobald sie auf der Zulassungsliste stehen, werden sie für Ihre Benutzer im Ausdruckseditor sichtbar. Mehr dazu erfahren Sie auf [dieser Seite](../../configuration/using/adding-additional-sql-functions.md).

>[!IMPORTANT]
>
>Wenn Sie einen Build verwenden, der älter als 8140 ist, kann die Option **XtkPassUnknownSQLFunctionsToRDBMS** auf &#39;1&#39; eingestellt werden. Wenn Sie Ihre Datenbank sichern möchten, löschen Sie diese Option (oder setzen Sie sie auf &#39;0&#39;).

Wenn Sie Benutzereingaben zur Erstellung von Filtern in Abfragen oder SQL-Anweisungen verwenden, müssen Sie sie immer escapen (siehe die [JSAPI-Dokumentation für Campaign](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html) - Schutz von Daten: Escape-Funktionen). Diese Funktionen sind:

* NL.XML.escape(data)
* NL.SQL.escape(data)
* NL.JS.escape(data)
* NL.XML.escapeAttribute(data)

## Schutz Ihres neuen Datenmodells

### Ordnerbasis

Siehe folgende Seiten:

* [Ordnerzugriffseigenschaften](../../platform/using/access-management.md)
* [Verknüpfte Ordner](../../configuration/using/configuration.md#linked-folder)

### Spezifische Berechtigungen

Zusätzlich zum ordnerbasierten Sicherheitsmodell können Sie Benutzeraktionen auch mit spezifischen Berechtigungen einschränken:

* Sie können einige Filter (sysFilter) hinzufügen, um zu verhindern, dass Daten gelesen/geschrieben werden (siehe [diese Seite](../../configuration/using/filtering-schemas.md)).

   ```
   <sysFilter name="writeAccess">    
       <condition enabledIf="hasNamedRight('myNewRole')=false" expr="FALSE"/>  
   </sysFilter>
   ```

* Sie können auch einige Aktionen (SOAP-Methode) schützen, die in Schemas definiert sind. Legen Sie einfach das Attribut access mit dem entsprechenden Namen right als Wert fest.

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
>Sie können Spezifische Berechtigungen im Befehlsknoten in einem navtree verwenden. Es bietet eine bessere Benutzererfahrung, bietet aber keinen Schutz (nur clientseitig verwenden, um sie auszublenden/zu deaktivieren). Sie müssen das Attribut access verwenden.

### Überlauftabelle

Wenn Sie vertrauliche Daten (Teil eines Schemas) je nach Zugriffsebene des Operators schützen müssen, sollten Sie sie nicht in der Formulardefinition ausblenden (enabledIf/visibleIf-Bedingungen).

Die vollständige Entität wird vom Bildschirm geladen, Sie können sie auch in der Spaltendefinition anzeigen. Dazu müssen Sie eine Überlauftabelle erstellen. Lesen Sie [diese Seite](../../configuration/using/examples-of-schemas-edition.md#overflow-table).

## Hinzufügen von Captchas in Webanwendungen

Es ist empfehlenswert, öffentlichen Landingpages und Anmeldeseiten ein Captcha hinzuzufügen. Leider ist dies in DCE-Seiten (Digital Content Editor) nicht einfach. Wir zeigen Ihnen, wie Sie ein v5 Captcha oder ein Google reCAPTCHA hinzufügen.

Im Allgemeinen wird ein Captcha im DCE hinzugefügt, indem ein Gestaltungsbaustein erstellt wird, mit dem es in den Seiteninhalt integriert werden kann. Sie müssen außerdem eine **Script**-Aktivität und einen **Test** hinzufügen.

### Gestaltungsbaustein

1. Gehen Sie zu **[!UICONTROL Ressourcen]** > **[!UICONTROL Kampagnenverwaltung]** > **[!UICONTROL Gestaltungsbausteine]** und erstellen Sie einen neuen Gestaltungsbaustein.

1. Verwenden Sie den Content-Typ **[!UICONTROL Webanwendung]** und aktivieren Sie **[!UICONTROL Sichtbar in den Anpassungsmenüs]**.

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
   * Mit Zeile 4 können Sie die Größe des grauen Captcha-Feldes (Breite/Höhe) sowie die Länge des erzeugten Worts ändern (minWordSize/maxWordSize).
   * Bevor Sie Google reCAPTCHA verwenden, müssen Sie sich bei Google registrieren und eine neue reCAPTCHA-Site erstellen.

      `<div class="g-recaptcha" data-sitekey="YOUR_SITE_KEY"></div>`
   Sie sollten die Überprüfungsschaltfläche deaktivieren können. Da jedoch keine Standardschaltfläche/-verknüpfung vorhanden ist, ist es besser, dies im HTML-Code selbst zu tun. Weitere Informationen dazu finden Sie auf [dieser Seite](https://developers.google.com/recaptcha/).

### Webanwendung aktualisieren

1. Greifen Sie auf die Eigenschaften Ihrer Webanwendung zu, um eine boolesche Variable mit dem Namen **captchaValid** hinzuzufügen.

   ![](assets/scripting-captcha.png)

1. Fügen Sie zwischen der letzten Seite und der **[!UICONTROL Datenspeicherung]**-Aktivität ein **[!UICONTROL Script]** und einen **[!UICONTROL Test]** hinzu.

   Schließen Sie die Verzweigung **[!UICONTROL True]** an die **[!UICONTROL Datenspeicherung]** und die andere an die Seite an, die die captcha enthält.

   ![](assets/scripting-captcha2.png)

1. Bearbeiten Sie die Bedingung der Verzweigung True mit `"[vars/captchaValid]"` gleich True.

   ![](assets/scripting-captcha3.png)

1. Bearbeiten Sie die Aktivität **[!UICONTROL Script]**. Der Inhalt hängt von der gewählten Captcha-Engine ab.

1. Schließlich können Sie Ihren personalisierten Block auf der Seite hinzufügen: verweisen Sie auf [diese Seite](../../web/using/editing-content.md).

   ![](assets/scripting-captcha4.png)

   ![](assets/scripting-captcha5.png)

>[!IMPORTANT]
>
>Für die reCAPTCHA-Integration müssen Sie clientseitiges JavaScript im HTML hinzufügen (in `<head>...</head>`):
>
>`<script src="https://www.google.com/recaptcha/api.js" async defer></script>`

### Kampagne captcha

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

### Google rekaptcha

Bitte lesen Sie die [offizielle Dokumentation](https://developers.google.com/recaptcha/docs/verify).

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

Seit Build 8797 müssen Sie zur Verwendung der Verifizierungs-API-URL diese auf die Zulassungsliste in der serverConf-Datei setzen, indem Sie sie im Knoten urlPermission hinzufügen:

`<url dnsSuffix="www.google.com" urlRegEx="https://www.google.com/recaptcha/api/siteverify"/>`

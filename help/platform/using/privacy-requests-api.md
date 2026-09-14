<?xml version="1.0" encoding="UTF-8"?>
<xliff xmlns="urn:oasis:names:tc:xliff:document:1.2" xmlns:okp="okapi-framework:xliff-extensions" xmlns:its="http://www.w3.org/2005/11/its" xmlns:itsxlf="http://www.w3.org/ns/its-xliff/" version="1.2" its:version="2.0">
<file original="help/platform/using/privacy-requests-api.md.mdsc" source-language="en-US" target-language="en-XX" datatype="x-text/markdown">
<body>
<trans-unit id="tu17" xml:space="preserve">
<source xml:lang="en-US">https://experienceleague.adobe.com/de/tools/campaign-api</source>
<target xml:lang="en-XX">https://experienceleague.adobe.com/de/tools/campaign-api</target>
</trans-unit>
<trans-unit id="tu1" restype="x-YAML_METADATA_HEADER_VALUE" xml:space="preserve">
<source xml:lang="en-US">Automatic Privacy request process</source>
<target xml:lang="en-XX">Automatischer Prozess für Datenschutzanfragen</target>
</trans-unit>
<trans-unit id="tu2" restype="x-YAML_METADATA_HEADER_VALUE" xml:space="preserve">
<source xml:lang="en-US">Learn how to setup an automatic Privacy request process</source>
<target xml:lang="en-XX">Erfahren Sie, wie Sie einen automatischen Prozess für Datenschutzanfragen einrichten</target>
</trans-unit>
<trans-unit id="tu3" xml:space="preserve">
<source xml:lang="en-US">Automatic Privacy request process</source>
<target xml:lang="en-XX">Automatischer Prozess für Datenschutzanfragen</target>
</trans-unit>
<trans-unit id="tu4" xml:space="preserve">
<source xml:lang="en-US">Adobe Campaign provides an <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>API<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> which allows you to setup an automatic Privacy request process.</source>
<target xml:lang="en-XX">Adobe Campaign verfügt über eine <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>API<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph>, mit der ein automatischer Prozess für Datenschutzanfragen eingerichtet werden kann.</target>
</trans-unit>
<trans-unit id="tu5" xml:space="preserve">
<source xml:lang="en-US">With the API, the general Privacy process is the same as <ph id="1" ctype="x-LINK">[</ph>using the interface<ph id="2" ctype="x-LINK">](privacy-requests-ui.md)</ph>. The only difference is the creation of the Privacy request. Instead of creating the request in Adobe Campaign, a POST containing the request information is sent to Campaign. For every request, a new entry is added in the <ph id="3" ctype="x-STRONG_EMPHASIS">**[!UICONTROL </ph>Privacy Requests<ph id="5" ctype="x-LINK_REF">]**</ph> screen. The Privacy technical workflows then process the request, the same way as for a request added using the interface.</source>
<target xml:lang="en-XX">Der allgemeine Datenschutzprozess mit der API ist mit dem der <ph id="1" ctype="x-LINK">[</ph>Benutzeroberfläche<ph id="2" ctype="x-LINK">](privacy-requests-ui.md)</ph> identisch. Der einzige Unterschied besteht in der Erstellung der Datenschutzanfrage. Statt die Anfrage in Adobe Campaign zu erstellen, werden die Informationen über eine POST-Anfrage an Campaign gesendet. Für jede Anfrage wird ein neuer Eintrag auf dem Bildschirm <ph id="3" ctype="x-STRONG_EMPHASIS">**[!UICONTROL </ph>Datenschutzanfragen<ph id="5" ctype="x-LINK_REF">]**</ph> hinzugefügt. Die technischen Datenschutz-Workflows verarbeiten daraufhin die Anfrage auf dieselbe Weise wie eine über die Benutzeroberfläche eingegebene Anfrage.</target>
</trans-unit>
<trans-unit id="tu6" xml:space="preserve">
<source xml:lang="en-US">If you're using the API to submit Privacy requests, we recommend that you leave the <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>2-step process<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> activated for the first Delete requests, in order to test the returned data. When your tests are finished, you can deactivate the 2-step process so that the Delete request process can run automatically.</source>
<target xml:lang="en-XX">Wenn Sie die API zum Senden von Datenschutzanfragen verwenden, wird empfohlen, den <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>zweistufigen Prozess<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> für die ersten Löschanfragen aktiviert zu lassen, um den Datenabruf zu testen. Wenn Ihre Tests abgeschlossen sind, können Sie den zweistufigen Prozess deaktivieren, damit der Prozess für Löschanfragen automatisch ausgeführt werden kann.</target>
</trans-unit>
<trans-unit id="tu7" xml:space="preserve">
<source xml:lang="en-US">The <ph id="1" ctype="x-STRONG_EMPHASIS">**[!UICONTROL </ph>CreateRequestByName<ph id="3" ctype="x-LINK_REF">]**</ph> JS API is defined as follows.</source>
<target xml:lang="en-XX">Die JS API <ph id="1" ctype="x-STRONG_EMPHASIS">**[!UICONTROL </ph>CreateRequestByName<ph id="3" ctype="x-LINK_REF">]**</ph> ist folgendermaßen definiert.</target>
</trans-unit>
<trans-unit id="tu8" xml:space="preserve">
<source xml:lang="en-US"><ph id="1" ctype="x-regxph" equiv-text="&lbrack;!NOTE">[!NOTE]</ph></source>
<target xml:lang="en-XX"><ph id="1" ctype="x-regxph" equiv-text="&lbrack;!NOTE">[!NOTE]</ph></target>
</trans-unit>
<trans-unit id="tu9" xml:space="preserve">
<source xml:lang="en-US">If you were using the <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>gdprRequest<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> API, you can still use it but it is recommended to use the new <ph id="3" ctype="x-STRONG_EMPHASIS">**</ph>privacyRequest<ph id="4" ctype="x-STRONG_EMPHASIS">**</ph> API.</source>
<target xml:lang="en-XX">Wenn Sie bisher die <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>gdprRequest<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph>-API verwendet haben, können Sie dies weiterhin tun. Es wird jedoch empfohlen, auf die neue <ph id="3" ctype="x-STRONG_EMPHASIS">**</ph>privacyRequest<ph id="4" ctype="x-STRONG_EMPHASIS">**</ph>-API umzusteigen.</target>
</trans-unit>
<trans-unit id="tu10" xml:space="preserve">
<source xml:lang="en-US"><ph id="1" ctype="x-regxph" equiv-text="&lbrack;!IMPORTANT">[!IMPORTANT]</ph></source>
<target xml:lang="en-XX"><ph id="1" ctype="x-regxph" equiv-text="&lbrack;!IMPORTANT">[!IMPORTANT]</ph></target>
</trans-unit>
<trans-unit id="tu11" xml:space="preserve">
<source xml:lang="en-US">The <ph id="1" ctype="x-STRONG_EMPHASIS">**[!UICONTROL </ph>Privacy Data Right<ph id="3" ctype="x-LINK_REF">]**</ph> named right is required to use the API.</source>
<target xml:lang="en-XX">Für die Verwendung der API ist die spezifische Berechtigung <ph id="1" ctype="x-STRONG_EMPHASIS">**[!UICONTROL </ph>Datenschutzrecht<ph id="3" ctype="x-LINK_REF">]**</ph> erforderlich.</target>
</trans-unit>
<trans-unit id="tu12" xml:space="preserve">
<source xml:lang="en-US"><ph id="1" ctype="x-regxph" equiv-text="&lbrack;!NOTE">[!NOTE]</ph></source>
<target xml:lang="en-XX"><ph id="1" ctype="x-regxph" equiv-text="&lbrack;!NOTE">[!NOTE]</ph></target>
</trans-unit>
<trans-unit id="tu13" xml:space="preserve">
<source xml:lang="en-US">The 'regulation' field is only available if you are using Campaign Classic 20.2 (build 9178+).</source>
<target xml:lang="en-XX">Das Feld "Verordnung" steht nur zur Verfügung, wenn Sie Campaign Classic 20.2 (Build 9178 oder höher) verwenden.</target>
</trans-unit>
<trans-unit id="tu14" xml:space="preserve">
<source xml:lang="en-US">If you are migrating to 20.2 and if you were already using the API, you must add the ‘regulation’ field as shown above. If you are using a previous build, you can continue to use the API without the ‘regulation’ field.</source>
<target xml:lang="en-XX">Wenn Sie auf 20.2 migrieren und die API bereits verwendet haben, müssen Sie das Feld „Vorschrift“ wie oben gezeigt hinzufügen. Wenn Sie einen früheren Build verwenden, können Sie die API weiterhin ohne das Feld „Vorschrift“ verwenden.</target>
</trans-unit>
<trans-unit id="tu15" xml:space="preserve">
<source xml:lang="en-US">Invoking the API externally</source>
<target xml:lang="en-XX">Die API extern aufrufen</target>
</trans-unit>
<trans-unit id="tu16" xml:space="preserve">
<source xml:lang="en-US">Here is an example of how you can invoke the API externally (authentication via the API and details about the Privacy API specifically). For more information on the Privacy API, consult the <ph id="1" ctype="x-LINK">&lbrack;</ph>API documentation<ph id="2" ctype="x-LINK">[#$tu17]</ph>. You can also consult the <ph id="3" ctype="x-LINK">[</ph>Web service calls documentation<ph id="4" ctype="x-LINK">](../../configuration/using/web-service-calls.md)</ph>.</source>
<target xml:lang="en-XX">Im Folgenden finden Sie ein Beispiel dafür, wie Sie die API extern aufrufen können (Authentifizierung über die API und Details zur Datenschutz-API). Weitere Informationen über die Datenschutz-API finden Sie in der <ph id="1" ctype="x-LINK">&lbrack;</ph>API-Dokumentation<ph id="2" ctype="x-LINK">[#$tu17]</ph>. Lesen Sie auch die <ph id="3" ctype="x-LINK">[</ph>Dokumentation zu Web-Dienst-Aufrufen<ph id="4" ctype="x-LINK">](../../configuration/using/web-service-calls.md)</ph>.</target>
</trans-unit>
<trans-unit id="tu18" xml:space="preserve">
<source xml:lang="en-US">First of all, you need to perform the authentication via the API:</source>
<target xml:lang="en-XX">Führen Sie zuerst die Authentifizierung über die API durch.</target>
</trans-unit>
<trans-unit id="tu19" xml:space="preserve">
<source xml:lang="en-US">Download the <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>xtk<ph id="2" ctype="x-inline-directive">:session**</ph> WSDL via this url: <ph id="4" ctype="x-STRONG_EMPHASIS">**`&lt;server url>`</ph>/nl/jsp/schemawsdl.jsp?schema=xtk<ph id="6" ctype="x-inline-directive">:session**</ph>.</source>
<target xml:lang="en-XX">Laden Sie die <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>xtk<ph id="2" ctype="x-inline-directive">:session**</ph>-WSDL über diese URL herunter: <ph id="4" ctype="x-STRONG_EMPHASIS">**`&lt;server url>`</ph>/nl/jsp/schemawsdl.jsp?schema=xtk<ph id="6" ctype="x-inline-directive">:session**</ph>.</target>
</trans-unit>
<trans-unit id="tu20" xml:space="preserve">
<source xml:lang="en-US">Use the "Logon" method and pass in a username and password as parameters in the request. You will get a response containing a session token. Here is an example using SoapUI.</source>
<target xml:lang="en-XX">Verwenden Sie die Anmeldemethode und geben Sie in der Anfrage einen Benutzernamen und ein Passwort als Parameter ein. Sie erhalten eine Antwort mit einem Sitzungs-Token. Dies ist ein Beispiel mit SoapUI.</target>
</trans-unit>
<trans-unit id="tu21" xml:space="preserve">
<source xml:lang="en-US"><ph id="1" ctype="x-IMAGE">![](assets/do-not-localize/privacy-api.png)</ph></source>
<target xml:lang="en-XX"><ph id="1" ctype="x-IMAGE">![](assets/do-not-localize/privacy-api.png)</ph></target>
</trans-unit>
<trans-unit id="tu22" xml:space="preserve">
<source xml:lang="en-US">Use the returned Session Token as the authentication for all subsequence API calls. It expires after 24 hours.</source>
<target xml:lang="en-XX">Verwenden Sie dieses Sitzungs-Token zur Authentifizierung für alle folgenden API-Aufrufe. Es läuft nach 24 Stunden ab.</target>
</trans-unit>
<trans-unit id="tu23" xml:space="preserve">
<source xml:lang="en-US">Then invoke the Privacy API:</source>
<target xml:lang="en-XX">Rufen Sie dann die Datenschutz-API auf:</target>
</trans-unit>
<trans-unit id="tu24" xml:space="preserve">
<source xml:lang="en-US">Download the WSDL from this URL: <ph id="1" ctype="x-STRONG_EMPHASIS">**`&lt;server url>`</ph>/nl/jsp/schemawsdl.jsp?schema=nms<ph id="3" ctype="x-inline-directive">:privacyRequest**</ph>.</source>
<target xml:lang="en-XX">Laden Sie die WSDL von dieser URL herunter: <ph id="1" ctype="x-STRONG_EMPHASIS">**`&lt;server url>`</ph>/nl/jsp/schemawsdl.jsp?schema=nms<ph id="3" ctype="x-inline-directive">:privacyRequest**</ph>.</target>
</trans-unit>
<trans-unit id="tu25" xml:space="preserve">
<source xml:lang="en-US">Use <ph id="1" ctype="x-STRONG_EMPHASIS">**[!UICONTROL </ph>CreateRequestByName<ph id="3" ctype="x-LINK_REF">]**</ph> to create a specific Privacy request.</source>
<target xml:lang="en-XX">Verwenden Sie <ph id="1" ctype="x-STRONG_EMPHASIS">**[!UICONTROL </ph>CreateRequestByName<ph id="3" ctype="x-LINK_REF">]**</ph>, um eine Datenschutzanfrage zu erstellen.</target>
</trans-unit>
<trans-unit id="tu26" xml:space="preserve">
<source xml:lang="en-US">Here is an example using the <ph id="1" ctype="x-STRONG_EMPHASIS">**[!UICONTROL </ph>CreateRequestByName<ph id="3" ctype="x-LINK_REF">]**</ph>. Note how we use the session token provided above as authentication. The response is the ID of the created request.</source>
<target xml:lang="en-XX">In diesem Beispiel wird <ph id="1" ctype="x-STRONG_EMPHASIS">**[!UICONTROL </ph>CreateRequestByName<ph id="3" ctype="x-LINK_REF">]**</ph> verwendet. Beachten Sie, wie das oben bereitgestellte Sitzungs-Token zur Authentifizierung verwendet wird. In der Antwort erhalten Sie die ID der erstellten Anfrage.</target>
</trans-unit>
<trans-unit id="tu27" xml:space="preserve">
<source xml:lang="en-US"><ph id="1" ctype="x-IMAGE">![](assets/do-not-localize/privacy-api-2.png)</ph></source>
<target xml:lang="en-XX"><ph id="1" ctype="x-IMAGE">![](assets/do-not-localize/privacy-api-2.png)</ph></target>
</trans-unit>
<trans-unit id="tu28" xml:space="preserve">
<source xml:lang="en-US">To help you perform the steps above, consider the following:</source>
<target xml:lang="en-XX">Beachten Sie bei der Durchführung der oben erläuterten Schritte Folgendes:</target>
</trans-unit>
<trans-unit id="tu29" xml:space="preserve">
<source xml:lang="en-US">You can use a <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>queryDef<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> on the <ph id="3" ctype="x-STRONG_EMPHASIS">**</ph>nms<ph id="4" ctype="x-inline-directive">:gdprRequest**</ph> schema to check the status of the Access request.</source>
<target xml:lang="en-XX">Sie können ein <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>queryDef<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> im <ph id="3" ctype="x-STRONG_EMPHASIS">**</ph>nms<ph id="4" ctype="x-inline-directive">:gdprRequest**</ph>-Schema verwenden, um den Status der Zugriffsanfrage zu überprüfen.</target>
</trans-unit>
<trans-unit id="tu30" xml:space="preserve">
<source xml:lang="en-US">You can use a <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>queryDef<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> on the <ph id="3" ctype="x-STRONG_EMPHASIS">**</ph>nms<ph id="4" ctype="x-inline-directive">:gdprRequestData**</ph> schema to get the result of the Access request.</source>
<target xml:lang="en-XX">Sie können ein <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>queryDef<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> im <ph id="3" ctype="x-STRONG_EMPHASIS">**</ph>nms<ph id="4" ctype="x-inline-directive">:gdprRequestData**</ph>-Schema verwenden, um das Ergebnis der Zugriffsanfrage abzurufen.</target>
</trans-unit>
<trans-unit id="tu31" xml:space="preserve">
<source xml:lang="en-US">To be able to download the XML file from <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>"$(serverUrl)'/nms/gdpr.jssp?id='@id"<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph>, you must be logged in and accessing it from an IP that is included in the allowlist. To do this, create a web application allowing you to access the file generated by the JSSP.</source>
<target xml:lang="en-XX">Um die XML-Datei von <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>"$(serverUrl)'/nms/gdpr.jssp?id='@id"<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> herunterladen zu können, müssen Sie angemeldet sein und der Zugriff muss von einer in der Zulassungsliste enthaltenen IP-Adresse erfolgen. Erstellen Sie dazu ein Web-Programm für den Zugriff auf die von der JSSP generierte Datei.</target>
</trans-unit>
<trans-unit id="tu32" xml:space="preserve">
<source xml:lang="en-US">Invoking the API from a JS</source>
<target xml:lang="en-XX">Die API über ein JS abrufen</target>
</trans-unit>
<trans-unit id="tu33" xml:space="preserve">
<source xml:lang="en-US">Here is an example of how you can invoke the API from a JS within Campaign Classic.</source>
<target xml:lang="en-XX">Hier ist ein Beispiel dafür, wie Sie die API innerhalb von Campaign Classic über ein JS abrufen können.</target>
</trans-unit>
<trans-unit id="tu34" xml:space="preserve">
<source xml:lang="en-US"><ph id="1" ctype="x-regxph" equiv-text="&lbrack;!NOTE">[!NOTE]</ph></source>
<target xml:lang="en-XX"><ph id="1" ctype="x-regxph" equiv-text="&lbrack;!NOTE">[!NOTE]</ph></target>
</trans-unit>
<trans-unit id="tu35" xml:space="preserve">
<source xml:lang="en-US">The 'regulation' field is only available if you are using Campaign Classic 20.2 (build 9178+).</source>
<target xml:lang="en-XX">Das Feld "Verordnung" steht nur zur Verfügung, wenn Sie Campaign Classic 20.2 (Build 9178 oder höher) verwenden.</target>
</trans-unit>
<trans-unit id="tu36" xml:space="preserve">
<source xml:lang="en-US">If you are migrating to 20.2 and if you were already using the API, you must add the ‘regulation’ field. If you are using a previous build, you can continue to use the API without the ‘regulation’ field.</source>
<target xml:lang="en-XX">Wenn Sie auf Version 20.2 migrieren und die API bereits verwendet haben, müssen Sie das Feld "Verordnung" hinzufügen. Wenn Sie einen früheren Build verwenden, können Sie die API weiterhin ohne das Feld "Verordnung" verwenden.</target>
</trans-unit>
<trans-unit id="tu37" xml:space="preserve">
<source xml:lang="en-US">If you are <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>using a previous build (with GDPR package)<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph>, you can continue to use the API without the ‘regulation’ field as shown below:</source>
<target xml:lang="en-XX">Wenn Sie <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>einen früheren Build verwenden (der ein DSGVO-Package beinhaltet)<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph>, können Sie die API weiterhin ohne das Feld "Verordnung" verwenden, wie unten dargestellt:</target>
</trans-unit>
<trans-unit id="tu38" xml:space="preserve">
<source xml:lang="en-US">If you are <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>migrating to 20.2<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> and if you were already using the API, you must add the ‘regulation’ field as shown below:</source>
<target xml:lang="en-XX">Wenn Sie <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>auf Version 20.2 migrieren<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph> und die API bereits verwendet haben, müssen Sie das Feld "Verordnung" hinzufügen, wie unten dargestellt:</target>
</trans-unit>
<trans-unit id="tu39" xml:space="preserve">
<source xml:lang="en-US">If you are <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>using Campaign Classic 20.2 (build 9178+) or above<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph>, the 'regulation' field is optional, as shown below:</source>
<target xml:lang="en-XX">Wenn Sie <ph id="1" ctype="x-STRONG_EMPHASIS">**</ph>Campaign Classic 20.2 oder höher (Build 9178 oder höher) verwenden<ph id="2" ctype="x-STRONG_EMPHASIS">**</ph>, ist das Feld "Verordnung" optional, wie unten dargestellt:</target>
</trans-unit>
</body>
</file>
</xliff>
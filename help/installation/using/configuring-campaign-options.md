---
product: campaign
title: Campaign-Optionen konfigurieren
description: Erfahren Sie, wie Sie Campaign-Optionen konfigurieren
audience: installation
content-type: reference
topic-tags: appendices
exl-id: a979cd99-afa7-4ce6-ba0f-9495089cba08
source-git-commit: 8610d29a3df1080f1622a2cb3685c0961fb40092
workflow-type: tm+mt
source-wordcount: '3994'
ht-degree: 13%

---

# Liste der Optionen von Campaign Classic{#configuring-campaign-options}

![](../../assets/v7-only.svg)

Die **[!UICONTROL Administration/Plattform/Optionen]** -Knoten ermöglicht die Konfiguration von Adobe Campaign-Optionen. Einige sind bei der Installation von Campaign integriert, andere können bei Bedarf manuell hinzugefügt werden. Die verfügbaren Optionen variieren je nach den mit Ihrer Instanz installierten Packages.


>[!CAUTION]
>
>* Optionen, die nicht auf dieser Seite aufgeführt sind, sind nur intern und **darf nicht geändert werden**.
>
>* Das Ändern oder Aktualisieren von Adobe Campaign-Optionen kann nur von erfahrenen Benutzern durchgeführt werden.


## Versand {#delivery}

<table> 
 <thead> 
  <tr> 
   <th> Optionsname </th> 
   <th> Beschreibung </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgDate</span> <br /> </td> 
   <td> Datum des letzten von der Zustellbarkeitsinstanz abgerufenen broadLogMsg.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgSent</span> <br /> </td> 
   <td> Datum des letzten broadLogMsg, das an die Zustellbarkeitsinstanz gesendet wurde.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_cuid</span> <br /> </td> 
   <td> Kennung der Versandberichte. Wenden Sie sich an den Support, um Ihre Kennung zu erhalten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_SeedTargets</span> <br /> </td> 
   <td> Liste der Schemas, für die Sie Testadressen für das Inbox Rendering verwenden möchten. (Elementnamen sind durch Kommas getrennt) Beispiel: custom_nms_recipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> BCC-E-Mail-Adresse, an die der Enhanced MTA eine Rohkopie der gesendeten E-Mails sendet. <br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NMS_ActivateOwnerConfirmation</span> <br /> </td> 
   <td><p> Hiermit können Sie dem für den Versand verantwortlichen Benutzer die Validierung des Versands gestatten, wenn in den Versandeigenschaften ein bestimmter Benutzer oder eine Benutzergruppe für den Start eines Versands bestimmt ist.</p><p> Aktivieren Sie dazu die Option, indem Sie "1" als Wert eingeben. Um diese Option zu deaktivieren, geben Sie "0" ein.</p><p> Der Sendebestätigungsprozess funktioniert dann standardmäßig: Nur der Benutzer oder die Benutzergruppe, der bzw. die in den Versandeigenschaften für den Versand bestimmt ist (oder ein Administrator), kann den Versand bestätigen und durchführen. Weitere Informationen finden Sie in <a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">diesem Abschnitt</a>.</p> </td> 
   <tr> 
   <td> <span class="uicontrol">Nms_DefaultRcpSchema</span> <br /> </td> 
   <td> Adobe Campaign verwendet eine globale Variable "Nms_DefaultRcpSchema", um ein Dialogfeld mit der standardmäßigen Empfängerdatenbank (nms:recipient) zu erstellen.<br /> Der Optionswert muss dem Namen des Schemas entsprechen, das der externen Empfängertabelle entspricht.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBilling_MainActionThreshold</span> <br /> </td> 
   <td> Mindestanzahl von Empfängern, damit ein Versand als Hauptversand im Abrechnungsbericht betrachtet werden kann.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_DefaultProvider</span> <br /> </td> 
   <td> Standard-Routing-Dienstleister für neue Vorlagen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransac</span> <br /> </td> 
   <td> Anzahl der BroadLogs, die für einen Versand gleichzeitig erstellt werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransac</span> <br /> </td> 
   <td> Fügen Sie Logs (broadLogs) pro Transaktionen (in die Tabelle) ein: Anzahl der Zeilen, die pro Batch verarbeitet werden sollen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span> <br /> </td> 
   <td> Gruppierungsgröße von Versandteilen bei der Analyse von Mid-Sourcing-Sendungen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgValidityDuration</span> <br /> </td> 
   <td> Standard-Versandzeitraum für einen Versand (in Sekunden).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RegexRules</span> <br /> </td> 
   <td> Regulärer Ausdruck zur Bereinigung der Versandnachrichten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveBlackList</span> <br /> </td> 
   <td> Durch Eingabe von "1"als Wert können Sie Empfänger ausschließen, die nicht mehr kontaktiert werden möchten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicatesRecipients</span> <br /> </td> 
   <td> Wenn Sie als Wert "1"eingeben, können Sie Dubletten automatisch ignorieren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ErrorAddressMask</span> <br /> </td> 
   <td> Hier können Sie die Syntax der Fehleradresse definieren, die bei der Beantwortung einer Nachricht verwendet wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_FromAddressMask</span> <br /> </td> 
   <td> Ermöglicht die Definition der Syntax der Absenderadresse, die beim Senden einer Nachricht verwendet wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageServerTimeout</span> <br /> </td> 
   <td> Ermöglicht die Festlegung eines Timeout-Limits (in Sekunden) für die Antwort vom Server beim Abrufen eines Bildes, das von einer personalisierten URL heruntergeladen und an eine E-Mail angehängt wurde. Wenn dieser Wert überschritten wird, kann die Nachricht nicht gesendet werden. Der Standardwert ist 60 Sekunden.<br /> </td> 
  </tr> 
 <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxDownloadedImageSize</span> <br /> </td> 
   <td> Ermöglicht die Definition der maximalen Größe (in Byte) für ein Bild, das von einer personalisierten URL heruntergeladen und an eine E-Mail angehängt wird. Der Standardwert ist 100.000 Bytes. Beim Testversand und Herunterladen des bzw. der Bilder zur Verarbeitung der E-Mail, wenn die Größe eines Bildes diesen Wert überschreitet oder wenn ein Download-Problem vorliegt, wird in den Versandlogs ein Fehler angezeigt und der Testversand schlägt fehl.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRecommendedAttachments</span> <br /> </td> 
   <td> Ermöglicht die Festlegung einer maximalen Anzahl von Anhängen in einer E-Mail- oder Transaktions-E-Mail-Vorlage. Wenn dieser Wert überschritten wird, wird in den Versandanalysenprotokollen oder bei der Publikation der Transaktions-E-Mail-Vorlage ein Warnhinweis angezeigt. Der Standardwert ist 1 Anlage.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRetry</span> <br /> </td> 
   <td> Maximale Anzahl weiterer Versuche während der Analyse.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_PublishingScript</span> <br /> </td> 
   <td> Veröffentlichungs-Script.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_NoCountBroadLogMsgPush</span> <br /> </td> 
   <td> broadLogMsg-Zählung für Push-Nachrichten deaktivieren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDeliveryWizard_ShowDeliveryWeight</span> <br /> </td> 
   <td> Die Nachrichtengewichtung wird im Versand-Assistenten angezeigt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultErrorAddr</span> <br /> </td> 
   <td> Die Standard-E-Mail-Adresse "Fehler"auf Instanzebene, die für den E-Mail-Versand verwendet wird, wenn sie vom Benutzer leer gelassen wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAddr</span> <br /> </td> 
   <td> Die Standard-E-Mail-Adresse "von"auf der Ebene der Instanz, die für den E-Mail-Versand verwendet wird, wenn sie vom Benutzer leer gelassen wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span> <br /> </td> 
   <td> Die Standard-E-Mail-Adresse "Antwort"auf Ebene der Instanz, die für den E-Mail-Versand verwendet wird, wenn sie vom Benutzer leer gelassen wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganisation</span> <br /> </td> 
   <td> Gebrauchsname des Kunden. Wird in einigen Warnmeldungen verwendet, die den Empfängern angezeigt werden.<br /> "Sie erhalten diese Nachricht, weil Sie mit **** oder einem verbundenen Unternehmen in Kontakt gekommen sind. So empfangen Sie keine Nachrichten mehr von ****".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span> <br /> </td> 
   <td> Die standardmäßige E-Mail-Bezeichnung "Von"auf Ebene der Instanz, die für den E-Mail-Versand verwendet wird, wenn sie vom Benutzer leer gelassen wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span> <br /> </td> 
   <td> Die standardmäßige E-Mail-Bezeichnung "Antwort"auf der Ebene der Instanz, die für den E-Mail-Versand verwendet wird, wenn sie vom Benutzer leer gelassen wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryCount</span> <br /> </td> 
   <td> Zeitraum zwischen zwei weiteren Versuchen einer E-Mail-Nachricht (in Sekunden).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryPeriod</span> <br /> </td> 
   <td> Zeitraum der weiteren Versuche für E-Mail-Nachrichten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsForecast_MsgWeightFormula</span> <br /> </td> 
   <td> Formel zur Berechnung der Gewichtung einer Nachricht in einem geplanten Versand.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_AllowlistEmails</span> <br /> </td> 
   <td> Liste der autorisierten E-Mail-Adressen für die Weiterleitung (vom Modul für die Verarbeitung eingehender E-Mails). Die Adressen müssen durch Kommas getrennt werden (oder *, um alle zuzulassen). z. B. xyz@abc.com, pqr@abc.com.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span> <br /> </td> 
   <td> Im 'lineImage'-Servlet für die URL-Verschlüsselung verwendeter AES-Schlüssel (LINE-Kanal).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailMaxError</span> <br /> </td> 
   <td> Im Kanal "E-Mail"(als Standard verwenden) : Maximale Anzahl an Fehlern, die bei SOFT-Fehlern beim Versand akzeptiert werden, bevor der Empfänger unter Quarantäne gestellt wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailSignificantErrorDelay</span> <br /> </td> 
   <td> Im Kanal "E-Mail"(als Standard verwenden) : Minimaler Zeitraum, der seit dem zuvor referenzierten SOFT-Fehler verbracht wurde, bevor ein neuer SOFT-Fehler berücksichtigt wurde.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileMaxError</span> <br /> </td> 
   <td> Auf Kanal "mobile" : Maximale Anzahl an Fehlern, die bei SOFT-Fehlern beim Versand akzeptiert werden, bevor der Empfänger unter Quarantäne gestellt wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileSignificantErrorDelay</span> <br /> </td> 
   <td> Auf Kanal "mobile" : Minimaler Zeitraum, der seit dem zuvor referenzierten SOFT-Fehler verbracht wurde, bevor ein neuer SOFT-Fehler berücksichtigt wurde.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_LogsPeriodHour</span> <br /> </td>
   <td> Ermöglicht die Angabe eines maximalen Zeitraums (in Stunden), um die Anzahl der bei Ausführung des Synchronisations-Workflows abgerufenen Broadlogs zu begrenzen.</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_PrepareFlow</span> <br /> </td> 
   <td> Maximale Anzahl der Aufrufe in der MidSourcing-Sitzung, die parallel ausgeführt werden können (standardmäßig 3).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMTA_Alert_Delay</span> <br /> </td> 
   <td> Benutzerdefinierte Verzögerung (in Minuten), nach der ein Versand als "verzögert"gilt, standardmäßig 30 Minuten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_DeliveryPreparationWindow</span> <br /> </td> 
   <td><p>Diese Option wird von der <span class="uicontrol"><a href="../../workflow/using/about-technical-workflows.md">operationMgt</a></span> technischer Workflow bei der Zählung der Anzahl laufender Sendungen.</p>Sie können damit die Anzahl der Tage festlegen, ab denen Sendungen mit inkonsistentem Status von der Zählung laufender Sendungen ausgeschlossen werden.</p><p>Standardmäßig ist der Wert auf "7"gesetzt, was bedeutet, dass inkonsistente Sendungen, die älter als 7 Tage sind, ausgeschlossen werden.</p></td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine1</span> <br /> </td> 
   <td> Zeile 1 der Absenderadresse.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine3</span> <br /> </td> 
   <td> Zeile 3 der Absenderadresse.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine4</span> <br /> </td> 
   <td> Zeile 4 der Absenderadresse.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine6</span> <br /> </td> 
   <td> Zeile 6 der Absenderadresse.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine7</span> <br /> </td> 
   <td> Zeile 7 der Absenderadresse.<br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsServer_MirrorPageUrl</span> <br /> </td> 
   <td> URL des Mirrorseiten-Servers (standardmäßig sollte mit NmsTracking_ServerUrl identisch sein).<br /> Dies ist der Standardwert von E-Mail-Sendungen, wenn die URL in der Routing-Definition nicht angegeben ist.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_Priority</span> <br /> </td> 
   <td> Parameter gesendeter SMS-Nachrichten: Informationen, die an das SMS-Gateway übermittelt werden, um die Priorität der Nachricht anzugeben.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span> <br /> </td> 
   <td> Anzahl der weiteren Zustellversuche beim Versand von SMS-Nachrichten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span> <br /> </td> 
   <td> Zeitraum, in dem erneute Zustellversuche für SMS-Nachrichten durchgeführt werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsUserAgentStats_LastConsolidation</span> <br /> </td> 
   <td> Letztes Konsolidierungstermin für <span class="uicontrol">NmsUserAgent</span> Statistiken.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsWebSegments_LastStates</span> <br /> </td> 
   <td> Name der Option, die die Websegmente und deren Status enthält.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkBarcode_SpecialChar</span> <br /> </td> 
   <td> Aktivieren/deaktivieren Sie die Unterstützung für Sonderzeichen für Code128.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkEmail_Characters</span> <br /> </td> 
   <td> Gültige Zeichen für eine E-Mail-Adresse.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Restrict_EditXML</span> </td> 
   <td> Fügen Sie diese Option mit dem Wert "0" hinzu, um die Bearbeitung des XML-Codes von Sendungen zu deaktivieren (Rechtsklick / <span class="uicontrol">XML-Quelle bearbeiten</span> oder <span class="uicontrol">STRG + F4</span> Verknüpfung).<br /> </td> 
  </tr>  
 </tbody> 
</table>

<!--<tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> BCC email address for Momentum to send a raw copy of the sent emails. <br /> </td> 
  </tr>
-->

## Ressourcen {#resources}

<table> 
 <thead> 
  <tr> 
   <th> Optionsname </th> 
   <th> Beschreibung </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDir</span> <br /> </td> 
   <td> Speicherort der Ressourcen für die Veröffentlichung in der Adobe Campaign-Clientkonsole. Weitere Informationen finden Sie in <a href="../../delivery/using/formatting.md#image-referencing">diesem Abschnitt</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDirPreview</span> <br /> </td> 
   <td> Speicherort der Ressourcen für die Vorschau in der Adobe Campaign-Clientkonsole. Weitere Informationen finden Sie in <a href="../../delivery/using/formatting.md#image-referencing">diesem Abschnitt</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_DefaultIgnoriertImage</span> <br /> </td> 
   <td> Liste der URL-Masken für beim Online-Stellen ignorierte Bilder.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImagePublishing</span> </td> 
   <td> Konfiguration zum Online-Stellen der Bilder. Die Werte können none/tracking/script/list sein (sie können durch die optionalen Einstellungen des Operators überschrieben werden). </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageSubDirectory</span> <br /> </td> 
   <td> Ordner zum Speichern der Bilder auf dem Server.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LogoPath</span> <br /> </td> 
   <td> Logo-Platzierung.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmPublishingDir</span> <br /> </td> 
   <td> Wurzelordner für Veröffentlichungen.<br /> Weitere Informationen zur Erstellung von HTML- und Textinhalten finden Sie unter <a href="../../delivery/using/using-a-content-template.md">diesem Abschnitt</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkImageUrl</span> <br /> </td> 
   <td> Hiermit können Sie den Server definieren, auf dem die in den Sendungen verwendeten Bilder gespeichert werden, damit sie vom Browser abgerufen werden können.<br /> Für Build-Versionen &lt;= 5098 verwenden wir die URL der Bilder, die auf die Instanz hochgeladen wurden.<br /> Für Build-Versionen &gt; 5098 verwenden wir stattdessen die öffentliche URL des Versands oder die <span class="uicontrol">XtkFileRes_Public_URL</span> URL der Option.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaInstance</span> <br /> </td> 
   <td> Hiermit können Sie den Instanznamen für das Hochladen von Bildern konfigurieren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaPassword</span> <br /> </td> 
   <td> Ermöglicht die Konfiguration des Kennworts für das Hochladen von Bildern.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaServers</span> <br /> </td> 
   <td> Ermöglicht die Konfiguration der Medien-URL(s) zum Hochladen von Bildern.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgWebValidityDuration</span> <br /> </td> 
   <td> Standardgültigkeitsdauer für Online-Ressourcen eines Versands (in Sekunden).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkFileRes_Public_URL</span> <br /> </td> 
   <td> Neue URL der Dateien mit öffentlichen Ressourcen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Kampagnen- und Workflow-Management {#campaign-e-workflow-management}

<table> 
 <thead> 
  <tr> 
   <th> Optionsname </th> 
   <th> Beschreibung </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">CrmMarketingActivityWindow</span> <br /> </td> 
   <td> Für diese Anzahl von Monaten angezeigter Marketingverlauf.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_Duration</span> <br /> </td> 
   <td> Standardgültigkeitsdauer einer Kampagne (in Sekunden).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_LimitConcurrency</span> <br /> </td> 
   <td> Maximale Anzahl an Versand-/Workflow-/Hypothesen-/Simulationsvorgängen, die gleichzeitig verarbeitet werden können, gestartet durch den operationMgt-Workflow.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span> <br /> </td> 
   <td> Ermöglicht es Ihnen, die <a href="../../workflow/using/about-technical-workflows.md">operationMgt</a> technische Workflow-Ausführung. Bei Aktivierung (Wert "1") werden die Ausführungsinformationen in den Workflow-Auditprotokollen protokolliert.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span> <br /> </td> 
   <td> Zeitraum für Targeting- und Extraktionsbedingungen im terminierten Modus.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Workflow_AnalysisThreshold</span> <br /> </td> 
   <td> Anzahl an Datensatzänderungen, die eine automatische Aktualisierung der Statistiken auslöst<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkReport_Logo</span> <br /> </td> 
   <td> Logo, das in der oberen rechten Ecke der exportierten Berichte angezeigt werden soll.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span> <br /> </td> 
   <td> Anzahl der Tage, die zwischen den Prüfungen auf angehaltene Workflows gewartet werden sollen<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCampaign_Activate_OwnerConfirmation</span> <br /> </td> 
   <td> Aktivieren Sie die Validierung der Sendungen durch den Eigentümer des Vorgangs, indem Sie "1"als Wert eingeben. Um diese Option zu deaktivieren, geben Sie "0" ein.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsAsset_JavascriptExt</span> <br /> </td> 
   <td> Zusätzliche JS-Bibliothek, die in die Workflow-Aktivität "Benachrichtigungen bezüglich Marketing-Ressourcen"geladen wird.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Sicherheit {#security}

<table> 
 <thead> 
  <tr> 
   <th> Optionsname </th> 
   <th> Beschreibung </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">RestrictEditingOTBSchema</span> <br /> </td> 
   <td> (ab Version 21.1.3) Wenn 1 ausgewählt ist (Standardwert), deaktiviert diese Option die Bearbeitung von integrierten Schemas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">RestrictEditingOTBJavascript</span> <br /> </td> 
   <td> (ab Version 21.1.3) Wenn 1 ausgewählt ist (Standardwert), deaktiviert diese Option die Bearbeitung von integrierten JavaScript-Codes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkAcceptOldPasswords</span> <br /> </td> 
   <td> (Kompatibilitätsmodus installieren: build&gt;6000) Bei Aktivierung (Wert "1") ermöglicht diese Option die Verwendung alter, in der Datenbank gespeicherter Passwörter für die Verbindung zu externen Konten oder zur Instanz.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span> <br /> </td> 
   <td> Dieser Schlüssel wird zum Verschlüsseln der meisten Kennwörter in der Datenbank verwendet. (externe Konten, LDAP-Kennwort...).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Allow_PrivilegeEscalation</span> <br /> </td> 
   <td> Wenn 1 ausgewählt ist, aktivieren Sie diese Option, um die PrivilegeEscalation in JavaScript zu ermöglichen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_ControlsOnFileDownload</span> <br /> </td> 
   <td> Wenn 1 ausgewählt ist, deaktivieren Sie diese Option die ACL-Steuerelemente während eines Dateidownloads (über fileDownload.jsp).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_JSFileSandboxing</span> <br /> </td> 
   <td> Wenn 1 ausgewählt ist, deaktivieren Sie diese Option die Datei-Sandbox in JavaScript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_SaveOptions_AllowNonAdmin</span> <br /> </td> 
   <td> Wenn der Wert auf "true"gesetzt ist, darf der Benutzer ohne Administratorrechte die xtkOption-Werte über den Softwareverteilungs-Assistenten aktualisieren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Unsafe_DecryptString</span> <br /> </td> 
   <td> Wenn 1 ausgewählt ist, kann diese Option decryptString verwenden, um einige Passwörter zu entschlüsseln.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkTraceDeleteLogin</span> <br /> </td> 
   <td> Geben Sie den Wert "1"ein, um das Löschen von Elementen mit Audit-Protokollinformationen in den mData durch Änderung des Felds "Geändert von"vor dem Löschen des Datensatzes zu verfolgen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Message Center {#message-center}

<table> 
 <thead> 
  <tr> 
   <th> Optionsname </th> 
   <th> Beschreibung </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">MC_EnrichmentCustomJs</span> <br /> </td> 
   <td> JavaScript-Bibliothek, die für die Anreicherung von Ereignissen personalisiert werden soll. Muss die Implementierung dieser beiden Funktionen enthalten:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">enrichRtEvents(aiEventId);</span> : Ereignisse in der Datenbank anreichert und speichert (wobei <span class="uicontrol">aiEventId</span> entspricht der Tabelle der verarbeiteten Echtzeit-Ereignisse).</p> </li> 
     <li> <p> <span class="uicontrol">enrichBatchEvents(aiEventId);</span> : Ereignisse in der Datenbank anreichert und speichert (wobei <span class="uicontrol">aiEventId</span> entspricht der ID-Tabelle der verarbeiteten Batch-Ereignisse).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span> <br /> </td> 
   <td> Datum des letzten Updates der Ereignisstatus aus den Versandlogs<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RoutingCustomJs</span> <br /> </td> 
   <td> JavaScript-Bibliothek, die für Routing-Ereignisse personalisiert werden soll. Muss die Implementierung dieser beiden Funktionen enthalten:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">dispatcherRtEvent(iEventId);</span> : gibt den internen Namen der Transaktionsnachricht zurück, die zur Verarbeitung des Echtzeit-Ereignisses ausgewählt wurde (wobei <span class="uicontrol">iEventId</span> entspricht der ID des verarbeiteten Echtzeit-Ereignisses).</p> </li> 
     <li> <p> <span class="uicontrol">dispatchBatchEvent(iEventId);</span> : gibt den internen Namen der für die Verarbeitung des Batch-Ereignisses ausgewählten Transaktionsnachricht zurück (wobei <span class="uicontrol">iEventId</span> entspricht der Kennung des verarbeiteten Batch-Ereignisses).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeAlert</span> <br /> </td> 
   <td> Warnschwellenwert der durchschnittlichen Sendezeit von Echtzeit-Ereignissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeWarning</span> <br /> </td> 
   <td> Warnungsschwelle für die durchschnittliche Sendezeit von Echtzeit-Ereignissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeAlert</span> <br /> </td> 
   <td> Warnschwelle für die durchschnittliche Verarbeitungsdauer von Echtzeitereignissen<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeWarning</span> <br /> </td> 
   <td> Hinweisschwelle für die durchschnittliche Verarbeitungsdauer von Echtzeitereignissen<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueAlert</span> <br /> </td> 
   <td> Warnschwelle für die durchschnittliche Anzahl von Echtzeitereignissen in der Warteschlange<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeAlert</span> <br /> </td> 
   <td> Warnschwellenwert für die durchschnittliche Wartezeit von Echtzeit-Ereignissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeWarning</span> <br /> </td> 
   <td> Warnungsschwelle für die durchschnittliche Wartezeit von Echtzeit-Ereignissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueWarning</span> <br /> </td> 
   <td> Hinweisschwelle für die durchschnittliche Anzahl von Echtzeitereignissen in der Warteschlange<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorAlert</span> <br /> </td> 
   <td> Warnschwelle für Verarbeitungsfehler bei Echtzeitereignissen<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorWarning</span> <br /> </td> 
   <td> Hinweisschwelle für Verarbeitungsfehler bei Echtzeitereignissen<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueAlert</span> <br /> </td> 
   <td> Warnschwelle für die maximale Anzahl von Echtzeitereignissen in der Warteschlange<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueWarning</span> <br /> </td> 
   <td> Warnschwellenwert für die maximale Anzahl von Echtzeit-Ereignissen in der Warteschlange.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueAlert</span> <br /> </td> 
   <td> Warnschwellenwert für die Mindestanzahl von Echtzeit-Ereignissen in der Warteschlange.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueWarning</span> <br /> </td> 
   <td> Warnschwellenwert für die Mindestanzahl von Echtzeit-Ereignissen in der Warteschlange.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueAlert</span> <br /> </td> 
   <td> Warnschwelle für Echtzeit-Ereignisse in der Warteschlange<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span> <br /> </td> 
   <td> Hinweisschwelle für Echtzeit-Ereignisse in der Warteschlange<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputAlert</span> <br /> </td> 
   <td> Warnschwelle für den Datendurchsatz von Echtzeitereignissen<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputWarning</span> <br /> </td> 
   <td> Hinweisschwelle für den Datendurchsatz von Echtzeitereignissen<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMessageCenter_RoutingBatchSize</span> <br /> </td> 
   <td> Größe der Gruppierung für das Ereignis-Routing.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastRtEventStat</span> <br /> </td> 
   <td> Aktualisieren Sie den Zeiger des RtEvent-Status (Datum des letzten Abrufs bis zum Abruf der Daten).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_MessageCenterURL</span> <br /> </td> 
   <td> Message Center-Server-URL, die zum Senden von Willkommensnachrichten verwendet wird (LINE-Kanal).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Datenbank {#database}

<table> 
 <thead> 
  <tr> 
   <th> Optionsname </th> 
   <th> Beschreibung </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_LastCleanup</span> <br /> </td> 
   <td> Defines the last time the cleanup process was run.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_BroadLogPurgeDelay</span> <br /> </td> 
   <td> <p>Hier können Sie die Verzögerung definieren, nach der das Broadlog aus der Datenbank gelöscht wird.</p><p>Diese Option wird automatisch erstellt, sobald die Verzögerung in der Benutzeroberfläche geändert wurde. Wenn Sie den Wert aus der Optionsliste ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventHistoPurgeDelay</span> <br /> </td> 
   <td><p> Hier können Sie die Verzögerung definieren, nach der der Ereignisverlauf aus der Datenbank gelöscht wird.</p><p>
   Diese Option wird automatisch erstellt, sobald die Verzögerung in der Benutzeroberfläche geändert wurde. Wenn Sie den Wert aus der Optionsliste ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventPurgeDelay</span> <br /> </td> 
   <td><p> Hier können Sie die Verzögerung definieren, nach der Ereignisse aus der Datenbank gelöscht werden.</p><p>Diese Option wird automatisch erstellt, sobald die Verzögerung in der Benutzeroberfläche geändert wurde. Wenn Sie den Wert aus der Optionsliste ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventStatPurgeDelay</span> <br /> </td> 
   <td><p> Hier können Sie die Verzögerung definieren, nach der die Ereignisstatistiken aus der Datenbank gelöscht werden.</p><p>Diese Option wird automatisch erstellt, sobald die Verzögerung in der Benutzeroberfläche geändert wurde. Wenn Sie den Wert aus der Optionsliste ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_PropositionPurgeDelay</span> <br /> </td> 
   <td><p> Hier können Sie die Verzögerung definieren, nach der Vorschläge aus der Datenbank gelöscht werden.</p><p> Diese Option wird automatisch erstellt, sobald die Verzögerung in der Benutzeroberfläche geändert wurde. Wenn Sie den Wert aus der Optionsliste ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_QuarantineMailboxFull</span> <br /> </td> 
   <td> <p>Hier können Sie die Verzögerung definieren, nach der die Quarantänen aus der Datenbank gelöscht werden.</p><p> Diese Option wird automatisch erstellt, sobald die Verzögerung in der Benutzeroberfläche geändert wurde. Wenn Sie den Wert aus der Optionsliste ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RecycledDeliveryPurgeDelay</span> <br /> </td> 
   <td> <p>Hier können Sie die Verzögerung definieren, nach der wiederverwertete Sendungen aus der Datenbank gelöscht werden.</p><p> Diese Option wird automatisch erstellt, sobald die Verzögerung in der Benutzeroberfläche geändert wurde. Wenn Sie den Wert aus der Optionsliste ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RejectsPurgeDelay</span> <br /> </td> 
   <td> <p>Hier können Sie die Verzögerung definieren, nach der Zurückweisungen aus der Datenbank gelöscht werden.</p><p>Diese Option wird automatisch erstellt, sobald die Verzögerung in der Benutzeroberfläche geändert wurde. Wenn Sie den Wert aus der Optionsliste ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingLogPurgeDelay</span> <br /> </td> 
   <td> <p>Hier können Sie die Verzögerung definieren, nach der Trackinglogs aus der Datenbank gelöscht werden.</p><p>Diese Option wird automatisch erstellt, sobald die Verzögerung in der Benutzeroberfläche geändert wurde. Wenn Sie den Wert aus der Optionsliste ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingStatPurgeDelay</span> <br /> </td> 
   <td><p> Hier können Sie die Verzögerung definieren, nach der Trackingstatistiken aus der Datenbank gelöscht werden.</p><p> Diese Option wird automatisch erstellt, sobald die Verzögerung in der Benutzeroberfläche geändert wurde. Wenn Sie den Wert aus der Optionsliste ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_VisitorPurgeDelay</span> <br /> </td> 
   <td> <p>Hier können Sie die Verzögerung definieren, nach der Besucher aus der Datenbank gelöscht werden.</p><p> Diese Option wird automatisch erstellt, sobald die Verzögerung in der Benutzeroberfläche geändert wurde. Wenn Sie den Wert aus der Optionsliste ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_WorkflowResultPurgeDelay</span> <br /> </td> 
   <td> <p>Hier können Sie die Verzögerung definieren, nach der Workflow-Ergebnisse aus der Datenbank gelöscht werden.</p><p> Diese Option wird automatisch erstellt, sobald die Verzögerung in der Benutzeroberfläche geändert wurde. Wenn Sie den Wert aus der Optionsliste ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_AzureDw</span> <br /> </td> 
   <td> Azure SQL Data Warehouse-Connector-Optionen.<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span> <br /> </td> 
   <td>Sie können das Verhalten "Unbedingter Stopp"bei allen Workflows und PostgreSQL-Datenbankabfragen gemäß den folgenden potenziellen Werten beeinflussen:<ul>
    <li><p>0 - Standard: Beendet den Workflow-Prozess, keine Auswirkungen auf die Datenbank<p></li>
    <li><p>1 - pg_cancel_backend: stoppt den Workflow-Prozess und bricht die Abfrage in der Datenbank ab<p></li>
    <li><p>2 - pg_terminate_backend: Beendet den Workflow-Prozess und beendet die Abfrage in der Datenbank<p></li></ul></td> 
  </tr>  
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span> <br /> </td> 
   <td> Name des Tablespace, der die Daten der Adobe Campaign-OTB-Tabellen enthalten soll.<br />Siehe <a href="../../installation/using/creating-and-configuring-the-database.md">Datenbank erstellen und konfigurieren</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span> <br /> </td> 
   <td> Name des Tablespace, der die Indizes der Adobe Campaign-OOTB-Tabellen enthalten soll.<br />Siehe <a href="../../installation/using/creating-and-configuring-the-database.md">Datenbank erstellen und konfigurieren</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWork</span> <br /> </td> 
   <td> Tablespace-Name für die Arbeitstabellen-Daten in Adobe Campaign.<br />See <a href="../../installation/using/creating-and-configuring-the-database.md">Creating and configuring the database</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWorkIndex</span> <br /> </td> 
   <td> Tablespace-Name für die Arbeitstabellen-Indexe in Adobe Campaign.<br />Siehe <a href="../../installation/using/creating-and-configuring-the-database.md">Datenbank erstellen und konfigurieren</a>.</td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TempDbName</span> <br /> </td> 
   <td> Ermöglicht die Konfiguration einer separaten Datenbank für Arbeitstabellen auf Microsoft SQL Server, um Backups und Replikation zu optimieren. Die Option entspricht dem Namen der temporären Datenbank: Arbeitstabellen werden, falls angegeben, in diese Datenbank geschrieben. Beispiel: "tempdb.dbo". (Beachten Sie, dass der Name mit einem Punkt enden muss). <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server">Mehr dazu</a> <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcTimeZone</span> <br /> </td> 
   <td> Zeitzone der Adobe Campaign-Instanz. Siehe <a href="../../installation/using/time-zone-management.md#configuration" target="_blank">Konfiguration</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseNChar</span> <br /> </td> 
   <td> Werden die Zeichenfolgenfelder der Datenbank mit NChar definiert?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseTimeStampWithTZ</span> <br /> </td> 
   <td> Speichern die "datetime"-Felder der Datenbank Zeitzoneninformationen?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkDatabaseId</span> <br /> </td> 
   <td> Kennung der Datenbank. Beginnt bei Unicode DataBase mit "u".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkInstancePrefix</span> <br /> </td> 
   <td> Den internen Namen wurde automatisch ein Präfix hinzugefügt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkQuery_Schema_LineCount</span> <br /> </td> 
   <td> Maximale Anzahl der von einer Abfrage von xtk:schema und xtk:srcSchema zurückgegebenen Ergebnisse.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSequence_AutoGeneration</span> <br /> </td> 
   <td> Alle benutzerdefinierten Schemata, die nach dieser Zeit mit autopk="true" und ohne das Attribut "pkSequence" erstellt wurden, erhalten eine automatisch generierte Sequenz "auto_ 
    &lt;schemanamespace&gt; 
     &lt;schemaname&gt;
       _seq. 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NlMigration_KeepFolderStructure</span> <br /> </td> 
   <td> Während der Migration wird die Baumstruktur automatisch basierend auf den neuen Versionsstandards neu organisiert.<br /> Mit dieser Option können Sie die automatische Migration der Navigationsstruktur deaktivieren. Wenn Sie es verwenden, müssen Sie nach der Migration veraltete Ordner löschen, die neuen Ordner hinzufügen und alle erforderlichen Prüfungen durchführen.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">Datentyp:</span> Ganzzahl</p> </li> 
     <li> <p> <span class="uicontrol">Wert (text)</span> : 1 </p> </li> 
    </ul> Diese Option sollte nur verwendet werden, wenn die native Navigationsstruktur zu vielen Änderungen unterzogen wurde.<br /> Weiterführende Informationen hierzu finden Sie in <a href="../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11">diesem Abschnitt</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatCoalesce</span> <br /> </td> 
   <td> Letztes Verarbeitungsdatum des <span class="uicontrol">NmsEmailErrorStat</span> Tabellenbereinigung.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PostUpgradeLastError</span> <br /> </td> 
   <td> Informationen zum Fehler, der beim Postupgrade aufgetreten ist, entsprechend der folgenden Syntax:<br /> <strong>{Build number}:{mode: pre/post/...}:{The 'lessThan'/'greaterOrEquelThan' where error occur + sub-step}</strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkCleanup_NoStats</span> <br /> </td> 
   <td> Geben Sie den Wert "1" ein, damit die Aktualisierung der Statistiken nicht über den Bereinigungs-Workflow erfolgt.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Integration {#integration}

<table> 
 <thead> 
  <tr> 
   <th> Optionsname </th> 
   <th> Beschreibung </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">AEMResourceTypeFilter</span> <br /> </td> 
   <td> Typen von AEM Ressourcen, die in Adobe Campaign verwendet werden können. Die Werte müssen durch Kommas getrennt werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">nmsPipeline_config</span> <br /> </td> 
   <td> Ermöglicht die Konfiguration von Experience Cloud-Triggern. Der Datentyp ist "long text"und muss im JSON-Format vorliegen. Siehe <a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">Verwenden von Experience Cloud Trigger mit Adobe Campaign Classic</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</span> <br /> </td> 
   <td> Diese Option wird beim Import von Daten aus einem Drittanbietersystem über einen CRM-Connector verwendet. Durch Aktivierung dieser Option können nur die seit dem letzten Import geänderten Objekte erfasst werden. Diese Option muss manuell wie unten dargestellt erstellt und ausgefüllt werden: 
    <ul> 
     <li> <p> <span class="uicontrol">Interner Name</span> : LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</p> </li> 
     <li> <p> <span class="uicontrol">Wert (Feld)</span> : Datum des letzten Imports mit JJJJ/MM/TT HH:mm:ss-Format. </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_EdgeServer</span> <br /> </td> 
   <td> Für die Integration verwendeter Adobe Target-Server. Diese Option ist standardmäßig bereits ausgewählt. Dieser Wert entspricht dem Adobe Target Domain Server , gefolgt vom Wert /m2. Beispiel: tt.omtrdc.net/m2.<br /> Weitere Informationen finden Sie in <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">diesem Abschnitt</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_TenantName</span> <br /> </td> 
   <td> Name der Adobe Target-Organisation. Dieser Wert entspricht dem Adobe-Target-Client-Namen.<br /> Weitere Informationen finden Sie in <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">diesem Abschnitt</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DataSourceId</span> <br /> </td> 
   <td> Option, die für die Integration mit Adobe Audience Manager verwendet wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DestinationId</span> <br /> </td> 
   <td> Option, die für die Integration mit Adobe Audience Manager verwendet wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Teradata</span> <br /> </td> 
   <td> Optionen für Teradata-Connector.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Hive</span> <br /> </td> 
   <td> Hive connector options.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Angebote {#offers}

<table> 
 <thead> 
  <tr> 
   <th> Optionsname </th> 
   <th> Beschreibung </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsCoupons_MaxPerTransac</span> <br /> </td> 
   <td> Anzahl der Gutscheine, die pro SQL-Transaktion aktualisiert werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchControl_</span> <br /> </td> 
   <td> '+ [Vorschlagsschema] + "_" + extAccountSource.@executionInstanceId + [Schema des Vorschlags] + "_" + vars.executionInstanceIdFilter<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchExec_</span> <br /> </td> 
   <td> '+ [ Vorschlagsschema] + "_" + extAccountSource.@executionInstanceId + "_" + extAccountTarget@executionInstanceId<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_SynchWorkflowIds</span> <br /> </td> 
   <td> Tracking des Synchronisations-Workflows.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_UseDaemon</span> <br /> </td> 
   <td> Aktivieren/deaktivieren Sie das asynchrone Schreiben von Vorschlägen ("0" zur Deaktivierung, "1" zur Aktivierung).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsModule_CouponsEnabled</span> <br /> </td> 
   <td> Ermöglicht die Aktivierung von Coupons.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Server {#server}

<table> 
 <thead> 
  <tr> 
   <th> Optionsname </th> 
   <th> Beschreibung </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsExecutionInstanceId</span> <br /> </td> 
   <td> Kennung der Ausführungsinstanz.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_CustomerId</span> <br /> </td> 
   <td> Zum Versand des Fakturaberichts verwendete Kundenkennung.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_IntranetURL</span> <br /> </td> 
   <td> Basis-URL des internen Webservers.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LastPostUpgrade</span> <br /> </td> 
   <td> Build-Nummer der AC-Instanz vor der letzten Aktualisierung.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_URL</span> <br /> </td> 
   <td> Basis-URL des öffentlichen Webanwendungsservers.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkPassUnknownSQLFunctionsToRDBMS</span> <br /> </td> 
   <td> Ermöglicht Ihnen die weitere Verwendung alter nicht deklarierter SQL-Funktionen nach der Migration. Wir empfehlen dringend, diese Option aufgrund der mit ihr verbundenen Sicherheitsrisiken nicht zu verwenden.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Tracking {#tracking}

<table> 
 <thead> 
  <tr> 
   <th> Optionsname </th> 
   <th> Beschreibung </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Available</span> <br /> </td> 
   <td> Option zur Aktivierung des Trackings.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ClickFormula</span> <br /> </td> 
   <td> Berechnungs-Script der getrackten URLs.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ExtAccount</span> <br /> </td> 
   <td> Ermöglicht die Definition des externen Kontos des Trackingservers.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Instance</span> <br /> </td> 
   <td> Ermöglicht die Definition des Instanznamens auf dem Tracking-Server.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_LastConsolidation</span> <br /> </td> 
   <td> Letztes Mal wurden die Tracking-Informationen mit neuen Daten konsolidiert.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_OpenFormula</span> <br /> </td> 
   <td> Script zur Berechnung der Öffnungs-URL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Password</span> <br /> </td> 
   <td> Kennwort für den Tracking-Server<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Pointer</span> <br /> </td> 
   <td> Der Zeiger verfolgt die letzten Nachrichtenereignisse, die über ihre IDs und ihr Datum verarbeitet wurden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_SecureServerUrl</span> <br /> </td> 
   <td> Sichere URL des Frontaltracking-Servers.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrl</span> <br /> </td> 
   <td> URL des Frontaltracking-Servers<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrlList</span> <br /> </td> 
   <td> Liste der URLs, mit denen die Tracking-Server kontaktiert werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_UserAgentRules</span> <br /> </td> 
   <td> Regeln zur Browseridentifizierung.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebFormula</span> <br /> </td> 
   <td> Script zur Berechnung der Webtrackingtags.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingDelivery</span> <br /> </td> 
   <td> Name des virtuellen Versands, der für das Web-Tracking-Management entwickelt wurde.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingMode</span> <br /> </td> 
   <td> Hiermit können Sie den Webtracking-Modus definieren.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Datenschutz {#privacy}

<table> 
 <thead> 
  <tr> 
   <th> Optionsname </th> 
   <th> Beschreibung </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePending</span> <br /> </td> 
   <td> Wenn Option 1 ausgewählt ist, müssen Sie den Löschvorgang in der Benutzeroberfläche in einem zweiten Schritt manuell bestätigen. Andernfalls werden die Daten ohne Bestätigung gelöscht.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePendingDelay</span> <br /> </td> 
   <td> Wartezeit bis zur Löschbestätigung vor Stornierung der Anfrage<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_MaxErrorAllowed</span> <br /> </td> 
   <td> Die maximal zulässige Anzahl von Fehlern bei der Verarbeitung/Löschung einer Datenschutzanfrage<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">privacy_request_purgeDelay</span> <br /> </td> 
   <td> Wartezeit zwischen Anfrageerstellung in Warteschlange und Löschung der Anfragedaten<br /> </td> 
  </tr> 
 </tbody> 
</table>

## LDAP {#ldap}

<table> 
 <thead> 
  <tr> 
   <th> Optionsname </th> 
   <th> Beschreibung </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Active</span> <br /> </td> 
   <td> Aktivieren Sie die Verwendung des LDAP-Servers zum Authentifizieren von Benutzern und Bereitstellen von Berechtigungen für Benutzer.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppLogin</span> <br /> </td> 
   <td> Melden Sie sich an, um den Server für verschiedene Suchvorgänge zu kontaktieren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppPassword</span> <br /> </td> 
   <td> Verschlüsseltes Kennwort für die Anwendungsanmeldung.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AutoOperator</span> <br /> </td> 
   <td> Automatische Erstellung von Benutzern und Berechtigungen in Adobe Campaign aktivieren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DN</span> <br /> </td> 
   <td> Formel für die LDAP-Benutzerkennung (DN) basierend auf dem Login.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearch</span> <br /> </td> 
   <td> Aktivieren Sie die DN-Suche im Verzeichnis.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchBase</span> <br /> </td> 
   <td> Suchbasis.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchFilter</span> <br /> </td> 
   <td> DN-Suchfilter.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchScope</span> <br /> </td> 
   <td> Suchreichweite.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Mechanism</span> <br /> </td> 
   <td> Authentifizierungstyp für den LDAP-Server (plain, md5, lds, ntlm, dpa).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Rights</span> <br /> </td> 
   <td> Aktivieren Sie die Synchronisierung von Berechtigungen und Gruppen aus dem LDAP-Ordner mit spezifischen Berechtigungen in Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsAttr</span> <br /> </td> 
   <td> LDAP-Attribut des Berechtigungsnamens.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsBase</span> <br /> </td> 
   <td> Suchbasis.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsFilter</span> <br /> </td> 
   <td> Suchfilter für Benutzerberechtigungen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsMask</span> <br /> </td> 
   <td> Ausdruck zur Extraktion der Adobe-Campaign-Berechtigungsnamen ausgehend von den LDAP-Berechtigungsnamen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsScope</span> <br /> </td> 
   <td> Suchreichweite.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Server</span> <br /> </td> 
   <td> LDAP-Server-Adresse (es ist möglich, einen Port durch Angabe von ":"als Trennzeichen anzugeben).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Webformulare {#web-forms}

<table> 
 <thead> 
  <tr> 
   <th> Optionsname </th> 
   <th> Beschreibung </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkUseScrollBar</span> <br /> </td> 
   <td> Mit dem auf 1 festgelegten Wert kann die Bildlaufleiste zu Detailformularen hinzugefügt werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Instance</span> <br /> </td> 
   <td> Instanz, die für die Invalidierung eines Webformulars im Modus "Andere Server(s)"verwendet wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Password</span> <br /> </td> 
   <td> Kennwort der Instanz, die für die Invalidierung eines Webformulars im Modus "Andere Server(s)"verwendet werden soll.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersMode</span> <br /> </td> 
   <td> Option, die es ermöglicht, den Annullierungsmodus für Webformulare anzugeben: standardmäßig lokal, via Trackingserver, wenn die Option 'Tracking' angegeben ist, und über eine benutzerdefinierte Liste, wenn die Option 'Andere(r) Server' angegeben ist.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersURLs</span> <br /> </td> 
   <td> Personalisierte Adressliste der Server, die bei der Invalidierung eines Webformulars kontaktiert werden sollen ("anderer Server"-Modus).<br /> </td> 
  </tr> 
 </tbody> 
</table>

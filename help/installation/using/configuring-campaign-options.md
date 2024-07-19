---
product: campaign
title: Campaign-Optionen konfigurieren
description: Erfahren Sie, wie Sie Campaign-Optionen konfigurieren
feature: Installation, Application Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: a979cd99-afa7-4ce6-ba0f-9495089cba08
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '3834'
ht-degree: 1%

---

# Liste der Campaign Classic-Optionen{#configuring-campaign-options}

Im Knoten **[!UICONTROL Administration / Plattform / Optionen]** können Sie Adobe Campaign-Optionen konfigurieren. Einige sind bei der Installation von Campaign integriert, andere können bei Bedarf manuell hinzugefügt werden. Die verfügbaren Optionen variieren je nach den mit Ihrer Instanz installierten Packages.


>[!CAUTION]
>
>* Optionen, die nicht auf dieser Seite aufgeführt sind, sind nur intern und **dürfen nicht geändert werden**.
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
   <td> <span class="uicontrol">Zustellbarkeit_LastBroadLogMsgDate</span> <br /> </td> 
   <td> Datum des letzten von der Zustellbarkeitsinstanz abgerufenen broadLogMsg.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgSent</span> <br /> </td> 
   <td> Datum des letzten an die Zustellbarkeitsinstanz gesendeten broadLogMsg.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_cuid</span> <br /> </td> 
   <td> Kennung der Versandberichte. Wenden Sie sich an den Support, um Ihre Kennung zu erhalten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_SeedTargets</span> <br /> </td> 
   <td> Liste der Schemas, für die Sie Testadressen für das Inbox Rendering verwenden möchten. (Elementnamen werden durch Kommas getrennt) Beispiel: custom_nms_recipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> BCC-E-Mail-Adresse, an die der Enhanced MTA eine Rohkopie der gesendeten E-Mails sendet. <br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NMS_ActivateOwnerConfirmation</span> <br /> </td> 
   <td><p> Hiermit können Sie dem für den Versand verantwortlichen Benutzer die Validierung des Versands gestatten, wenn in den Versandeigenschaften ein bestimmter Benutzer oder eine Benutzergruppe für den Start eines Versands bestimmt ist.</p><p> Aktivieren Sie dazu die Option, indem Sie "1" als Wert eingeben. Um diese Option zu deaktivieren, geben Sie "0" ein.</p><p> Der Versandvalidierungsprozess funktioniert dann standardmäßig: Nur der in den Versandeigenschaften für den Versand bestimmte Benutzer oder die Benutzergruppe (oder ein Administrator) kann den Versand bestätigen und durchführen. Weitere Informationen finden Sie <a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">in diesem Abschnitt</a>.</p> </td> 
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
   <td> Standard-Routing-Dienstleister für die neuen Vorlagen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransac</span> <br /> </td> 
   <td> Minimale Batch-Größe (Anzahl Zeilen) für das Einfügen von broadLogs während einer Versandvorbereitung.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransac</span> <br /> </td> 
   <td> Schwelle der Batch-Dauer (Anzahl der Millisekunden), unter der sich die Batch-Größe für das Einfügen von broadLogs während einer Versandvorbereitung verdoppelt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span> <br /> </td> 
   <td> Gruppierungsgröße der Versandteile bei der Analyse von Mid-Sourcing-Sendungen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_msgValidityDuration</span> <br /> </td> 
   <td> Standard-Versandzeitraum für einen Versand (in Sekunden).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RegexRules</span> <br /> </td> 
   <td> Reguläre Ausdrücke zur Normalisierung von Versandnachrichten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveBlackList</span> <br /> </td> 
   <td> Durch Eingabe von "1" als Wert können Sie Empfänger ausschließen, die nicht mehr kontaktiert werden möchten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicatesRecipients</span> <br /> </td> 
   <td> Durch Eingabe von "1"als Wert können Sie Dubletten automatisch ignorieren.<br /> </td> 
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
   <td> Ermöglicht die Definition der maximalen Größe (in Byte) für ein Bild, das von einer personalisierten URL heruntergeladen und an eine E-Mail angehängt wird. Der Standardwert ist 100.000 Bytes (100 KB). Wenn Sie einen Testversand durchführen und das Bild/die Bilder herunterladen, um die E-Mail zu verarbeiten, wenn die Größe eines Bildes diesen Wert überschreitet oder wenn ein Download-Problem vorliegt, wird in den Versandlogs ein Fehler angezeigt und der Testversand schlägt fehl.<br /> </td> 
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
   <td> Veröffentlichungsskript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_NoCountBroadLogMsgPush</span> <br /> </td> 
   <td> Deaktivieren Sie die broadLogMsg-Anzahl für Push-Nachrichten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDeliveryWizard_ShowDeliveryWeight</span> <br /> </td> 
   <td> Zeigen Sie die Nachrichtengewichtung im Versand-Assistenten an.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultErrorAddr</span> <br /> </td> 
   <td> Standard-E-Mail-Adresse "Fehler"auf Instanzebene, die für den E-Mail-Versand verwendet wird, wenn vom Benutzer leer gelassen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAddr</span> <br /> </td> 
   <td> Die Standard-E-Mail-Adresse "von"auf Instanzebene, die für den E-Mail-Versand verwendet wird, wenn sie vom Benutzer leer gelassen wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span> <br /> </td> 
   <td> Standard-E-Mail-Adresse "Antwort auf" auf Instanzenebene, die für den E-Mail-Versand verwendet wird, wenn vom Benutzer leer gelassen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganisation</span> <br /> </td> 
   <td> Allgemeiner Name des Kunden. Wird in einigen Warnmeldungen verwendet, die den Empfängern angezeigt werden.<br /> "Sie erhalten diese Nachricht, weil Sie mit "Organisation"oder einem verbundenen Unternehmen in Kontakt gekommen sind. So empfangen Sie keine Nachrichten mehr von "Organisation"<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span> <br /> </td> 
   <td> Die standardmäßige E-Mail-Beschriftung "Von"auf Instanzebene, die für den E-Mail-Versand verwendet wird, wenn sie vom Benutzer leer gelassen wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span> <br /> </td> 
   <td> Die standardmäßige E-Mail-Bezeichnung "Antwort auf" auf Instanzenebene, die für den E-Mail-Versand verwendet wird, wenn sie vom Benutzer leer gelassen wird.<br /> </td> 
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
   <td> Formel zur Berechnung der Gewichtung einer Nachricht für einen vorläufigen Versand.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_AllowlistEmails</span> <br /> </td> 
   <td> Liste der autorisierten E-Mail-Adressen für die Weiterleitung (vom Modul für die Verarbeitung eingehender E-Mails). Die Adressen müssen durch Kommas getrennt werden (oder *, um alle zuzulassen). z. B. xyz@abc.com,pqr@abc.com.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span> <br /> </td> 
   <td> AES-Schlüssel, der im "lineImage"-Servlet verwendet wird, um die URLs zu kodieren (LINE-Kanal).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailMaxError</span> <br /> </td> 
   <td> Im Kanal "E-Mail"(Standard verwenden) : Maximale Anzahl an Fehlern, die akzeptiert werden, bei SOFT-Fehlern während des Versands, bevor der Empfänger unter Quarantäne gestellt wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailSignificantErrorDelay</span> <br /> </td> 
   <td> Im Kanal "E-Mail"(als Standard verwenden) : Minimale Dauer seit dem vorherigen referenzierten SOFT-Fehler, bevor ein neuer SOFT-Fehler berücksichtigt wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileMaxError</span> <br /> </td> 
   <td> Auf Kanal "Mobil" : Maximale Anzahl an Fehlern, die akzeptiert werden, bei SOFT-Fehlern beim Versand, bevor der Empfänger unter Quarantäne gestellt wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileSignificantErrorDelay</span> <br /> </td> 
   <td> Bei Kanal "mobile" : Minimale Dauer, die seit dem vorherigen referenzierten SOFT-Fehler verbracht wurde, bevor ein neuer SOFT-Fehler berücksichtigt wurde.<br /> </td> 
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
   <td><p>Diese Option wird vom technischen Workflow <span class="uicontrol"><a href="../../workflow/using/about-technical-workflows.md">operationMgt</a></span> verwendet, wenn die Anzahl der ausgeführten Sendungen gezählt wird.</p>Sie können damit die Anzahl der Tage festlegen, ab denen Sendungen mit inkonsistentem Status von der Zählung laufender Sendungen ausgeschlossen werden.</p><p>Standardmäßig ist der Wert auf "7"gesetzt, was bedeutet, dass inkonsistente Sendungen, die älter als 7 Tage sind, ausgeschlossen werden.</p></td> 
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
   <td> Parameter der gesendeten SMS-Nachrichten: Informationen, die an das SMS-Gateway übermittelt werden, um die Priorität der Nachricht anzugeben.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span> <br /> </td> 
   <td> Anzahl weiterer Zustellversuche beim Senden von SMS-Nachrichten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span> <br /> </td> 
   <td> Zeitraum, in dem erneute Zustellversuche für SMS-Nachrichten durchgeführt werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsUserAgentStats_LastConsolidation</span> <br /> </td> 
   <td> Letztes Konsolidierungsdatum für <span class="uicontrol">NmsUserAgent</span>-Statistiken.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsWebSegments_LastStates</span> <br /> </td> 
   <td> Name der Option, die die Websegmente und ihre Status enthält.<br /> </td> 
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
   <td> Fügen Sie diese Option mit dem Wert "0"hinzu, um die Bearbeitung des XML-Codes von Sendungen zu deaktivieren (Rechtsklick / <span class="uicontrol">XML-Quelle bearbeiten</span> oder Tastaturbefehl <span class="uicontrol">STRG + F4</span> ).<br /> </td> 
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
   <td> Speicherort der Ressourcen für die Veröffentlichung in der Adobe Campaign-Clientkonsole. Weitere Informationen finden Sie in <a href="../../delivery/using/formatting.md#image-referencing">diesem Abschnitt</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDirPreview</span> <br /> </td> 
   <td> Speicherort der Ressourcen für die Vorschau in der Adobe Campaign-Clientkonsole. Weitere Informationen finden Sie in <a href="../../delivery/using/formatting.md#image-referencing">diesem Abschnitt</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_DefaultIgnoriertImage</span> <br /> </td> 
   <td> Liste der URL-Masken für die beim Hochladen übersprungenen Bilder.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImagePublishing</span> </td> 
   <td> Konfiguration des Bild-Uploads. Die Werte können none/tracking/script/list sein (sie können durch die optionalen Einstellungen des Operators überschrieben werden). </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageSubDirectory</span> <br /> </td> 
   <td> Ordner, in dem die Bilder auf dem Server gespeichert werden sollen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LogoPath</span> <br /> </td> 
   <td> Platz zur Anzeige von Logos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmPublishingDir</span> <br /> </td> 
   <td> Stammordner für Veröffentlichungen.<br /> Weiterführende Informationen zur Erstellung von HTML- und Textinhalten finden Sie in <a href="../../delivery/using/using-a-content-template.md">diesem Abschnitt</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkImageUrl</span> <br /> </td> 
   <td> Hiermit können Sie den Server definieren, auf dem die in den Sendungen verwendeten Bilder gespeichert werden, damit sie vom Browser abgerufen werden können.<br /> Für Build-Versionen &lt;= 5098 verwenden wir die URL der Bilder, die in die Instanz hochgeladen wurden.<br /> Für Build-Versionen &gt; 5098 verwenden wir stattdessen die öffentliche URL des Versands oder die URL der Option <span class="uicontrol">XtkFileRes_Public_URL</span> .<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaInstance</span> <br /> </td> 
   <td> Hiermit können Sie den Instanznamen für das Hochladen von Bildern konfigurieren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaPassword</span> <br /> </td> 
   <td> Ermöglicht Ihnen die Konfiguration des Kennworts für das Hochladen von Bildern.<br /> </td> 
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
   <td> Neue URL für Dateien mit öffentlichen Ressourcen.<br /> </td> 
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
   <td> Standardgültigkeitszeitraum einer Kampagne (in Sekunden).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_LimitConcurrency</span> <br /> </td> 
   <td> Maximale Anzahl an Versand-/Workflow-/Hypothesen-/Simulationsvorgängen, die gleichzeitig verarbeitet werden können, gestartet durch den operationMgt-Workflow.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span> <br /> </td> 
   <td> Ermöglicht die Überwachung der Ausführung des technischen Workflows <a href="../../workflow/using/about-technical-workflows.md">operationMgt</a>. Bei Aktivierung (Wert "1") werden die Ausführungsinformationen in den Workflow-Auditprotokollen protokolliert.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span> <br /> </td> 
   <td> Zeitraum für Targeting- und Extraktionsbedingungen im geplanten Modus.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Workflow_AnalysisThreshold</span> <br /> </td> 
   <td> Anzahl der betroffenen Datensätze, nach denen Tabellenstatistiken automatisch neu berechnet werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkReport_Logo</span> <br /> </td> 
   <td> Logo, das in der oberen rechten Ecke der exportierten Berichte angezeigt werden soll.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span> <br /> </td> 
   <td> Anzahl der Tage, die zwischen den Prüfungen auf angehaltene Workflows gewartet werden sollen.<br /> </td> 
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
   <td> <span class="uicontrol">RestrictEditingOOTBSchema</span> <br /> </td> 
   <td> (ab Version 21.1.3) Wenn 1 ausgewählt ist (Standardwert), deaktiviert diese Option die Bearbeitung von integrierten Schemas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">RestrictEditingOTBJavascript</span> <br /> </td> 
   <td> (ab Version 21.1.3) Wenn 1 ausgewählt ist (Standardwert), deaktiviert diese Option die Bearbeitung von integrierten JavaScript-Codes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkAcceptOldPasswords</span> <br /> </td> 
   <td> (Kompatibilitätsmodus installieren: Build &gt; 6000) Wenn aktiviert (Wert "1"), ermöglicht diese Option die Verwendung alter in der Datenbank gespeicherter Kennwörter für die Verbindung zu externen Konten oder zur Instanz.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span> <br /> </td> 
   <td> Dieser Schlüssel wird zum Verschlüsseln der meisten Kennwörter in der Datenbank verwendet. (externe Konten, LDAP-Kennwort...).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Allow_PrivilegeEscalation</span> <br /> </td> 
   <td> Wenn 1 ausgewählt ist, aktivieren Sie diese Option, um die PrivilegeEscalation in JavaScript zuzulassen.<br /> </td> 
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
   <td> Wenn 1 ausgewählt ist, können Sie mit dieser Option decryptString verwenden, um einige Passwörter zu entschlüsseln.<br /> </td> 
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
     <li> <p> <span class="uicontrol">enrichRtEvents(aiEventId);</span> : Hiermit werden Ereignisse in der Datenbank angereichert und gespeichert (wobei <span class="uicontrol">aiEventId</span> der Tabelle der verarbeiteten Echtzeit-Ereignisse entspricht).</p> </li> 
     <li> <p> <span class="uicontrol">enrichBatchEvents(aiEventId);</span> : Hiermit werden Ereignisse angereichert und in der Datenbank gespeichert (wobei <span class="uicontrol">aiEventId</span> der ID-Tabelle der verarbeiteten Batch-Ereignisse entspricht).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span> <br /> </td> 
   <td> Datum der letzten Aktualisierung des Ereignisstatus über Versandlogs.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RoutingCustomJs</span> <br /> </td> 
   <td> JavaScript-Bibliothek, die für Routing-Ereignisse personalisiert wird. Muss die Implementierung dieser beiden Funktionen enthalten:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">patchRtEvent(iEventId);</span> : gibt den internen Namen der für die Verarbeitung des Echtzeit-Ereignisses ausgewählten Transaktionsnachricht zurück (wobei <span class="uicontrol">iEventId</span> der Kennung des verarbeiteten Echtzeit-Ereignisses entspricht).</p> </li> 
     <li> <p> <span class="uicontrol">dispatchBatchEvent(iEventId);</span> : gibt den internen Namen der für die Verarbeitung des Batch-Ereignisses ausgewählten Transaktionsnachricht zurück (wobei <span class="uicontrol">iEventId</span> der Kennung des verarbeiteten Batch-Ereignisses entspricht).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeAlert</span> <br /> </td> 
   <td> Warnschwellenwert für die durchschnittliche Versandzeit von Echtzeit-Ereignissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeWarning</span> <br /> </td> 
   <td> Warnungsschwelle für die durchschnittliche Versandzeit von Echtzeit-Ereignissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeAlert</span> <br /> </td> 
   <td> Warnschwellenwert für die durchschnittliche Verarbeitungszeit von Echtzeit-Ereignissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeWarning</span> <br /> </td> 
   <td> Warnschwellenwert für die durchschnittliche Verarbeitungszeit von Echtzeit-Ereignissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueAlert</span> <br /> </td> 
   <td> Schwellenwert für Warnhinweise für die durchschnittliche Anzahl von Echtzeit-Ereignissen in der Warteschlange.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeAlert</span> <br /> </td> 
   <td> Warnschwellenwert für die durchschnittliche Wartezeit von Echtzeit-Ereignissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeWarning</span> <br /> </td> 
   <td> Warnschwellenwert für die durchschnittliche Wartezeit von Echtzeit-Ereignissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueWarning</span> <br /> </td> 
   <td> Warnschwellenwert für die durchschnittliche Anzahl der Echtzeit-Ereignisse in der Warteschlange.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorAlert</span> <br /> </td> 
   <td> Warnschwellenwert für die Verarbeitung von Fehlern in Echtzeit-Ereignissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorWarning</span> <br /> </td> 
   <td> Warnschwellenwert für die Verarbeitung von Fehlern in Echtzeit-Ereignissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueAlert</span> <br /> </td> 
   <td> Warnschwellenwert für die maximale Anzahl von Echtzeit-Ereignissen in der Warteschlange.<br /> </td> 
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
   <td> Schwellenwert vor kritischer Bedingung für die Warteschlange ausstehender Echtzeit-Ereignisse.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span> <br /> </td> 
   <td> Schwellenwert vor Warnung für die Warteschlange ausstehender Echtzeit-Ereignisse.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputAlert</span> <br /> </td> 
   <td> Warnschwellenwert für den Echtzeit-Ereignisdurchsatz.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputWarning</span> <br /> </td> 
   <td> Warnschwellenwert für den Echtzeit-Ereignisdurchsatz.<br /> </td> 
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
   <td> Definiert, wann der Bereinigungsprozess zuletzt ausgeführt wurde.<br /> </td> 
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
   <td> Azure SQL Datawarehouse-Connector-Optionen.<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span> <br /> </td> 
   <td>Sie können das Verhalten "Unbedingter Stopp"bei allen Workflows und PostgreSQL-Datenbankabfragen gemäß den folgenden potenziellen Werten beeinflussen:<ul>
    <li><p>0 - Standard: Beendet den Workflow-Prozess, keine Auswirkungen auf die Datenbank<p></li>
    <li><p>1 - pg_cancel_backend: Hält den Workflow-Prozess an und bricht die Abfrage in der Datenbank ab<p></li>
    <li><p>2 - pg_terminate_backend: Beendet den Workflow-Prozess und beendet die Abfrage in der Datenbank<p></li></ul></td> 
  </tr>  
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span> <br /> </td> 
   <td> Name des Tablespace, der die Daten der Adobe Campaign-OTB-Tabellen enthalten soll.<br />Siehe <a href="../../installation/using/creating-and-configuring-the-database.md">Erstellen und Konfigurieren der Datenbank</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span> <br /> </td> 
   <td> Name des Tablespace, der die Indizes der Adobe Campaign-OOTB-Tabellen enthalten soll.<br />Siehe <a href="../../installation/using/creating-and-configuring-the-database.md">Erstellen und Konfigurieren der Datenbank</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWork</span> <br /> </td> 
   <td> Name des Tablespace, der die Daten der Adobe Campaign-Arbeitstabellen enthalten soll.<br />Siehe <a href="../../installation/using/creating-and-configuring-the-database.md">Erstellen und Konfigurieren der Datenbank</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWorkIndex</span> <br /> </td> 
   <td> Name des Tablespace, der die Indizes der Adobe Campaign-Arbeitstabellen enthalten soll.<br />Siehe <a href="../../installation/using/creating-and-configuring-the-database.md">Erstellen und Konfigurieren der Datenbank</a>.</td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TempDbName</span> <br /> </td> 
   <td> Ermöglicht die Konfiguration einer separaten Datenbank für Arbeitstabellen auf Microsoft SQL Server, um Backups und Replikation zu optimieren. Die Option entspricht dem Namen der temporären Datenbank: Arbeitstabellen werden in diese Datenbank geschrieben, falls angegeben. Beispiel: "tempdb.dbo". (Beachten Sie, dass der Name mit einem Punkt enden muss). <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server">mehr lesen</a> <br /> </td> 
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
   <td> Maximale Anzahl an Ergebnissen, die von einer Abfrage für xtk:schema und xtk:srcSchema zurückgegeben werden.<br /> </td> 
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
   <td> Während der Migration wird die Baumstruktur automatisch basierend auf den neuen Versionsstandards neu organisiert.<br /> Mit dieser Option können Sie die automatische Migration der Navigationsstruktur deaktivieren. Wenn Sie es verwenden, müssen Sie nach der Migration veraltete Ordner löschen, die neuen Ordner hinzufügen und alle erforderlichen Prüfungen ausführen.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">Datentyp:</span> Ganzzahl</p> </li> 
     <li> <p> <span class="uicontrol">Wert (text)</span> : 1 </p> </li> 
    </ul> Diese Option sollte nur verwendet werden, wenn die native Navigationsstruktur zu vielen Änderungen unterzogen wurde.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatCoalesce</span> <br /> </td> 
   <td> Letztes Verarbeitungsdatum der <span class="uicontrol">NmsEmailErrorStat</span> -Tabellenbereinigung.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PostUpgradeLastError</span> <br /> </td> 
   <td> Informationen zum Fehler, der im Postupgrade aufgetreten ist, entsprechend der unten stehenden Syntax:<br /> <strong>{Build number}:{mode: pre/post/..}:{The 'lessThan'/'greaterOrEquelThan' where error occur + sub step}</strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkCleanup_NoStats</span> <br /> </td> 
   <td> Geben Sie den Wert "1"ein, damit die Aktualisierung der Statistiken nicht über den Bereinigungs-Workflow erfolgt.<br /> </td> 
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
   <td> Ermöglicht die Konfiguration von Experience Cloud-Triggern. Der Datentyp ist "long text"und muss im JSON-Format vorliegen. Siehe <a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">Verwenden von Experience Cloud-Triggern mit Adobe Campaign Classic</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</span> <br /> </td> 
   <td> Diese Option wird beim Import von Daten aus einem Drittanbietersystem über einen CRM-Connector verwendet. Durch Aktivierung dieser Option können nur die seit dem letzten Import geänderten Objekte erfasst werden. Diese Option muss manuell wie unten dargestellt erstellt und ausgefüllt werden: 
    <ul> 
     <li> <p> <span class="uicontrol">Interner Name</span> : LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</p> </li> 
     <li> <p> <span class="uicontrol">Wert (Feld)</span> : Datum des letzten Imports mit dem Format jjj/MM/tt und h:mm:ss. </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_EdgeServer</span> <br /> </td> 
   <td> Für die Integration verwendeter Adobe Target-Server. Diese Option ist standardmäßig ausgefüllt. Dieser Wert entspricht dem Adobe Target Domain Server , gefolgt vom Wert /m2. Beispiel: tt.omtrdc.net/m2.<br /> Siehe <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">diesen Abschnitt</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_TenantName</span> <br /> </td> 
   <td> Name der Adobe Target-Organisation. Dieser Wert entspricht dem Namen des Adobe Target-Clients.<br /> Siehe <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">diesen Abschnitt</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DataSourceId</span> <br /> </td> 
   <td> Für die Integration mit Adobe Audience Manager verwendete Option.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DestinationId</span> <br /> </td> 
   <td> Für die Integration mit Adobe Audience Manager verwendete Option.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Teradata</span> <br /> </td> 
   <td> Teradata-Connector-Optionen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Hive</span> <br /> </td> 
   <td> Ausblenden von Connector-Optionen.<br /> </td> 
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
   <td> Ermöglicht Ihnen die Aktivierung von Gutscheinen.<br /> </td> 
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
   <td> Kundenkennung, die beim Senden des Abrechnungsberichts verwendet wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_IntranetURL</span> <br /> </td> 
   <td> Interne Basis-URL für den Zugriff auf den Anwendungsserver.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LastPostUpgrade</span> <br /> </td> 
   <td> Build-Nummer der AC-Instanz vor dem letzten Upgrade.<br /> </td> 
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
   <td> Option, die die Aktivierung des Trackings ermöglicht.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ClickFormula</span> <br /> </td> 
   <td> Berechnungsskript für getrackte URLs.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ExtAccount</span> <br /> </td> 
   <td> Ermöglicht die Definition des externen Kontos des Trackingservers.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Instance</span> <br /> </td> 
   <td> Hiermit können Sie den Instanznamen auf dem Tracking-Server definieren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_LastConsolidation</span> <br /> </td> 
   <td> Letztes Mal wurden die Tracking-Informationen mit neuen Daten konsolidiert.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_OpenFormula</span> <br /> </td> 
   <td> Öffnen Sie das URL-Berechnungsskript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Password</span> <br /> </td> 
   <td> Kennwort für den Tracking-Server<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_pointer</span> <br /> </td> 
   <td> Der Zeiger verfolgt die letzten Nachrichtenereignisse, die über ihre IDs und ihr Datum verarbeitet wurden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_SecureServerUrl</span> <br /> </td> 
   <td> Sichere URL des Frontaltracking-Servers.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrl</span> <br /> </td> 
   <td> URL des Frontaltracking-Servers.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrlList</span> <br /> </td> 
   <td> Liste der URLs, mit denen die Tracking-Server kontaktiert werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_UserAgentRules</span> <br /> </td> 
   <td> Regelsatz für die Browseridentifizierung.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebFormula</span> <br /> </td> 
   <td> Skript zur Berechnung von Web-Tracking-Tags.<br /> </td> 
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
   <td> Die Verzögerung zwischen der Anforderung, die auf das Löschen der Bestätigung wartet, und der Löschvorgang der Anforderung wird abgebrochen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_MaxErrorAllowed</span> <br /> </td> 
   <td> Die maximal zulässige Fehleranzahl beim Verarbeiten/Löschen einer Datenschutzanfrage.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">privacy_request_purgeDelay</span> <br /> </td> 
   <td> Die Verzögerung zwischen der Anforderung wird in der Warteschlange erstellt und die Anfragedaten werden gelöscht.<br /> </td> 
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
   <td> Berechnungsformel für LDAP DN basierend auf der Anmeldung.<br /> </td> 
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
   <td> Suchbereich.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Mechanism</span> <br /> </td> 
   <td> Authentifizierungstyp, der zum Herstellen einer Verbindung mit dem LDAP-Server verwendet wird (plain, md5, lds, ntlm, dpa).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Rights</span> <br /> </td> 
   <td> Aktivieren Sie die Synchronisierung von Berechtigungen und Gruppen aus dem LDAP-Ordner mit spezifischen Berechtigungen in Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsAttr</span> <br /> </td> 
   <td> LDAP-Attribut, das den Autorisierungsnamen enthält.<br /> </td> 
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
   <td> Ausdruck zum Extrahieren der Namen der Adobe Campaign-Berechtigungen aus den LDAP-Berechtigungen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsScope</span> <br /> </td> 
   <td> Suchbereich.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Server</span> <br /> </td> 
   <td> LDAP-Server-Adresse (es ist möglich, einen Port anzugeben, indem ":"als Trennzeichen angegeben wird).<br /> </td> 
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
   <td> Instanz, die für die Invalidierung eines Webformulars im Modus "Andere Server(s)"verwendet werden soll.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Password</span> <br /> </td> 
   <td> Kennwort der Instanz, die für die Invalidierung eines Webformulars im Modus "Andere Server(s)"verwendet werden soll.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersMode</span> <br /> </td> 
   <td> Option, mit der Sie den Invalidierungsmodus für Webformulare festlegen können: standardmäßig lokal, verwendet Trackingserver, wenn die Option 'tracking' ist, und verwendet eine personalisierte Liste mit der Option 'other server(s)'.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersURLs</span> <br /> </td> 
   <td> Personalisierte Adressliste der Server, die bei der Invalidierung eines Webformulars kontaktiert werden sollen ("Modus anderer Server(s)").<br /> </td> 
  </tr> 
 </tbody> 
</table>

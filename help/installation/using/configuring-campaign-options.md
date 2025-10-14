---
product: campaign
title: Kampagnenoptionen konfigurieren
description: Erfahren Sie, wie Sie Campaign-Optionen konfigurieren
feature: Installation, Application Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: a979cd99-afa7-4ce6-ba0f-9495089cba08
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '3837'
ht-degree: 1%

---

# Liste der Campaign Classic-Optionen{#configuring-campaign-options}

Mit **[!UICONTROL Knoten Administration / Plattform]** Optionen können Sie Adobe Campaign-Optionen konfigurieren. Einige davon sind bei der Installation von Campaign integriert und andere können bei Bedarf manuell hinzugefügt werden. Die verfügbaren Optionen variieren je nach den mit Ihrer Instanz installierten Paketen.


>[!CAUTION]
>
>* Optionen, die auf dieser Seite nicht aufgeführt sind, sind nur intern und **dürfen nicht geändert werden**.
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
   <td> Datum des letzten Abrufs von broadLogMsg der Zustellbarkeitsinstanz.<br /> </td> 
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
   <td> Liste der Schemata, für die Testadressen für das Inbox Rendering verwendet werden sollen. (Elementnamen werden durch Kommas getrennt) Z. B.: custom_nms_recipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> BCC-E-Mail-Adresse, an die der Enhanced MTA eine Rohkopie der gesendeten E-Mails sendet. <br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NMS_ActivateOwnerConfirmation</span> <br /> </td> 
   <td><p> Ermöglicht es dem für den Versand verantwortlichen Benutzer, den Versand zu bestätigen, wenn in den Versandeigenschaften ein bestimmter Benutzer oder eine Benutzergruppe für den Start eines Versands angegeben wurde.</p><p> Aktivieren Sie dazu die Option, indem Sie als Wert „1“ eingeben. Um diese Option zu deaktivieren, geben Sie „0“ ein.</p><p> Der Bestätigungsprozess für den Versand funktioniert dann standardmäßig: Nur der in den Versandeigenschaften für den Versand angegebene Benutzer oder die Benutzergruppe (oder ein Administrator) kann den Versand bestätigen und durchführen. Weitere Informationen finden Sie <a href="https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-deliveries.html?lang=de#start-a-delivery" target="_blank">in diesem Abschnitt</a>.</p> </td>

<tr> 
   <td> <span class="uicontrol">Nms_DefaultRcpSchema</span> <br /> </td> 
   <td> Adobe Campaign verwendet eine globale Variable „Nms_DefaultRcpSchema“ für den Dialog mit der standardmäßigen Empfängerdatenbank (nms:recipient).<br /> Der Wert der Option muss mit dem Namen des Schemas übereinstimmen, das mit der externen Empfängertabelle übereinstimmt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBilling_MainActionThreshold</span> <br /> </td> 
   <td> Mindestanzahl an Empfängern, damit ein Versand als Hauptversand im Abrechnungsbericht betrachtet werden kann.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_DefaultProvider</span> <br /> </td> 
   <td> Standardmäßiger Routing-Dienstleister für die neuen Vorlagen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransac</span> <br /> </td> 
   <td> Minimale Batch-Größe (Anzahl der Zeilen) zum Einfügen von broadLogs während einer Versandvorbereitung.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransac</span> <br /> </td> 
   <td> Schwellenwert für die Batch-Dauer (Anzahl Millisekunden), unter dem die Batch-Größe für das Einfügen von broadLogs während einer Versandvorbereitung verdoppelt wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span> <br /> </td> 
   <td> Gruppierungsgröße von Versandteilen bei der Analyse von Mid-Sourcing-Sendungen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgValidityDuration</span> <br /> </td> 
   <td> Standardversandzeitraum für einen Versand (in Sekunden).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RegexRules</span> <br /> </td> 
   <td> Reguläre Ausdrücke zum Normalisieren von Versandnachrichten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveBlackList</span> <br /> </td> 
   <td> Wenn Sie „1“ als Wert eingeben, können Sie Empfänger ausschließen, die nicht mehr kontaktiert werden möchten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicatesRecipients</span> <br /> </td> 
   <td> Wenn Sie „1“ als Wert eingeben, können Sie Dubletten automatisch ignorieren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ErrorAddressMasks</span> <br /> </td> 
   <td> Ermöglicht die Definition der Syntax der Fehleradresse, die für die Antwort auf eine Nachricht verwendet wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_FromAddressMasks</span> <br /> </td> 
   <td> Ermöglicht die Definition der Syntax der Absenderadresse, die zum Senden einer Nachricht verwendet wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageServerTimeout</span> <br /> </td> 
   <td> Ermöglicht die Definition eines Timeouts (in Sekunden) für den Empfang einer Antwort vom Server beim Abrufen eines Bildes, das von einer personalisierten URL heruntergeladen und an eine E-Mail angehängt wurde. Wenn dieser Wert überschritten wird, kann die Nachricht nicht gesendet werden. Der Standardwert ist 60 Sekunden.<br /> </td> 
  </tr> 
 <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxDownloadedImageSize</span> <br /> </td> 
   <td> Hier können Sie die maximale Größe (in Byte) festlegen, die für ein Bild zulässig ist, das von einer personalisierten URL heruntergeladen und an eine E-Mail angehängt wird. Der Standardwert ist 100.000 Byte (100 KB). Wenn beim Senden eines Testversands und beim Herunterladen der Bilder zur Verarbeitung der E-Mail die Größe eines Bildes diesen Wert überschreitet oder ein Download-Problem auftritt, wird ein Fehler in den Versandlogs angezeigt und der Testversand schlägt fehl.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRecommendedAttachments</span> <br /> </td> 
   <td> Ermöglicht die Festlegung einer maximalen Anzahl von Anhängen in einer E-Mail- oder Transaktions-E-Mail-Vorlage. Wenn dieser Wert überschritten wird, wird bei der Veröffentlichung der Transaktions-E-Mail-Vorlage in den Versandanalyseprotokollen eine Warnung angezeigt. Der Standardwert ist 1 Anlage.<br /> </td> 
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
   <td> Nachrichtengewichtung im Versand-Assistenten anzeigen<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultErrorAddr</span> <br /> </td> 
   <td> E-Mail-Standardadresse 'Fehler' auf Instanzebene wird für den E-Mail-Versand verwendet, wenn sie vom Benutzer leer gelassen wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAddr</span> <br /> </td> 
   <td> Standardmäßige „Von“-E-Mail-Adresse auf Instanzebene, die für den E-Mail-Versand verwendet wird, wenn sie vom Benutzer leer gelassen wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span> <br /> </td> 
   <td> Standardmäßige „Antwort-an“-E-Mail-Adresse auf Instanzebene, die für den E-Mail-Versand verwendet wird, wenn sie von Benutzenden leer gelassen wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganization</span> <br /> </td> 
   <td> Allgemeiner Name des Kunden. Wird in einigen Warnmeldungen verwendet, die den Empfängern angezeigt werden.<br /> „Sie erhalten diese Nachricht, weil Sie mit „Organisation“ oder einem verbundenen Unternehmen in Kontakt standen. So erhalten Sie keine Nachrichten mehr von „Organisation“<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span> <br /> </td> 
   <td> E-Mail-Standardbeschriftung 'Von' auf Instanzebene wird für den E-Mail-Versand verwendet, wenn sie von Benutzer leer gelassen wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span> <br /> </td> 
   <td> Standard-E-Mail-Beschriftung 'Antwort an' auf Instanzebene, die für den E-Mail-Versand verwendet wird, wenn sie von Benutzer leer gelassen wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryCount</span> <br /> </td> 
   <td> Zeitraum zwischen zwei erneuten Zustellversuchen einer E-Mail-Nachricht (in Sekunden).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryPeriod</span> <br /> </td> 
   <td> Zeitraum für weitere Zustellversuche für E-Mail-Nachrichten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsForecast_MsgWeightFormula</span> <br /> </td> 
   <td> Formel zur Berechnung der Gewichtung einer Nachricht für einen vorläufigen Versand.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_AllowlistEmails</span> <br /> </td> 
   <td> Liste der autorisierten Weiterleitungs-E-Mail-Adressen (aus dem Modul zur Verarbeitung eingehender E-Mails). Die Adressen müssen durch Kommas getrennt werden (oder *, um alle Adressen zu erlauben). z. B. xyz@abc.com,pqr@abc.com.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span> <br /> </td> 
   <td> AES-Schlüssel, der im „lineImage“-Servlet zur Codierung der URLs verwendet wird (LINE-Kanal).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailMaxError</span> <br /> </td> 
   <td> Bei Kanal „E-Mail“ (als Standard verwenden) : Maximale Anzahl von akzeptierten Fehlern für SOFT-Fehler beim Versand, bevor der Empfänger unter Quarantäne gestellt wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailSignificantErrorDelay</span> <br /> </td> 
   <td> Bei Kanal „E-Mail“ (als Standard verwenden) : Minimaler Zeitraum seit dem vorherigen referenzierten SOFT-Fehler, bevor ein neuer SOFT-Fehler berücksichtigt wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileMaxError</span> <br /> </td> 
   <td> Auf Kanal „mobil“ : Maximale Anzahl an akzeptierten Fehlern für SOFT-Fehler beim Versand, bevor der Empfänger unter Quarantäne gestellt wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileSignificantErrorDelay</span> <br /> </td> 
   <td> Auf Kanal „Mobile“ : Minimaler Zeitraum seit dem vorherigen referenzierten SOFT-Fehler, bevor ein neuer SOFT-Fehler berücksichtigt wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_LogsPeriodHour</span> <br /> </td>
   <td> Ermöglicht die Angabe eines maximalen Zeitraums (ausgedrückt in Stunden), um die Anzahl der bei jeder Ausführung des Synchronisierungs-Workflows wiederhergestellten Broadlogs zu begrenzen.</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_PrepareFlow</span> <br /> </td> 
   <td> Maximale Anzahl an Aufrufen in der Mid-Sourcing-Sitzung, die parallel ausgeführt werden kann (standardmäßig 3).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMTA_Alert_Delay</span> <br /> </td> 
   <td> Benutzerdefinierte Verzögerung (in Minuten), nach der ein Versand als „verzögert“ gilt, Standard: 30 Minuten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_DeliveryPreparationWindow</span> <br /> </td> 
   <td><p>Diese Option wird vom technischen Workflow <span class="uicontrol"><a href="https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/technical-workflows.html?lang=de" target="_blank">operationMgt</a></span> beim Zählen der Anzahl der laufenden Sendungen verwendet.</p>Damit können Sie die Anzahl der Tage festlegen, nach denen Sendungen mit dem Status Inkonsistent von der Zählung der laufenden Sendungen ausgeschlossen werden.</p><p>Standardmäßig ist der Wert auf „7“ festgelegt, was bedeutet, dass inkonsistente Sendungen, die älter als 7 Tage sind, ausgeschlossen werden.</p></td> 
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
   <td> URL des Mirrorseiten-Servers (standardmäßig sollte sie mit NmsTracking_ServerUrl identisch sein).<br /> Dies ist der Standardwert von E-Mail-Sendungen, wenn die URL in der Routing-Definition nicht angegeben ist.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_Priority</span> <br /> </td> 
   <td> Parameter der gesendeten SMS-Nachrichten: an das SMS-Gateway gesendete Informationen zur Angabe der Nachrichtenpriorität.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span> <br /> </td> 
   <td> Anzahl weiterer Zustellversuche beim Senden von SMS-Nachrichten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span> <br /> </td> 
   <td> Zeitraum, in dem weitere Zustellversuche für SMS-Nachrichten unternommen werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsUserAgentStats_LastConsolidation</span> <br /> </td> 
   <td> Letztes Konsolidierungsdatum für Statistiken <span class="uicontrol">NmsUserAgent</span>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsWebSegments_LastStates</span> <br /> </td> 
   <td> Name der Option, die die Web-Segmente und ihre Status enthält.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkBarcode_SpecialChar</span> <br /> </td> 
   <td> Aktivieren/Deaktivieren der Unterstützung für Sonderzeichen in Code128.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkEmail_Characters</span> <br /> </td> 
   <td> Gültige Zeichen für eine E-Mail-Adresse.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Restrict_EditXML</span> </td> 
   <td> Fügen Sie diese Option mit dem Wert „0“ hinzu, um die Bearbeitung des XML-Codes von Sendungen zu deaktivieren (Rechtsklick/<span class="uicontrol">XML-Quelle bearbeiten</span> oder <span class="uicontrol">Tastaturbefehl Strg+F4</span>).<br /> </td> 
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
   <td> <span class="uicontrol">NcmResourcesDir</span> <br /> </td> 
   <td> Speicherort der Ressourcen für die Veröffentlichung in der Adobe Campaign-Client-Konsole. Weitere Informationen finden Sie in <a href="../../delivery/using/formatting.md#image-referencing">diesem Abschnitt</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmResourcesDirPreview</span> <br /> </td> 
   <td> Speicherort der Ressourcen für die Vorschau in der Adobe Campaign-Client-Konsole. Weitere Informationen finden Sie in <a href="../../delivery/using/formatting.md#image-referencing">diesem Abschnitt</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_DefaultIgnoredImage</span> <br /> </td> 
   <td> Liste der URL-Masken für beim Hochladen übersprungene Bilder.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImagePublishing</span> </td> 
   <td> Konfiguration für das Hochladen von Bildern. Die Werte können „none“ oder „tracking“ oder „script“ oder „list“ sein (kann durch die optionalen Einstellungen des Operators überschrieben werden). </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageSubDirectory</span> <br /> </td> 
   <td> Ordner, in dem die Bilder auf dem Server gespeichert werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LogoPath</span> <br /> </td> 
   <td> Platz zum Anzeigen von Logos.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmPublishingDir</span> <br /> </td> 
   <td> Stammordner für Veröffentlichungen.<br /> Weiterführende Informationen zur Erstellung von HTML und Textinhalten finden Sie in <a href="../../delivery/using/using-a-content-template.md">diesem Abschnitt</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkImageUrl</span> <br /> </td> 
   <td> Ermöglicht die Definition des Servers, auf dem die im Versand verwendeten Bilder gespeichert werden, damit der Browser sie abrufen kann.<br /> Für Build-Versionen &lt;= 5098 verwenden wir die URL der Bilder, die auf die Instanz hochgeladen wurden.<br /> Für Build-Versionen &gt; 5098 verwenden wir stattdessen die öffentliche URL des Versands oder die URL <span class="uicontrol">XtkFileRes_Public_URL</span> Option.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaInstance</span> <br /> </td> 
   <td> Ermöglicht die Konfiguration des Instanznamens für das Hochladen von Bildern.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaPassword</span> <br /> </td> 
   <td> Ermöglicht die Konfiguration des Kennworts für das Hochladen von Bildern.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaServers</span> <br /> </td> 
   <td> Ermöglicht die Konfiguration der Medien-URL(s) für das Hochladen von Bildern.<br /> </td> 
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
   <td> Marketing-Verlauf für diese Anzahl von Monaten angezeigt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_Duration</span> <br /> </td> 
   <td> Standardmäßiger Gültigkeitszeitraum einer Kampagne (in Sekunden).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_LimitConcurrency</span> <br /> </td> 
   <td> Maximale Anzahl an Versand-/Workflow-/Hypothesen-/Simulationsaufträgen, die gleichzeitig verarbeitet werden können, gestartet von operationMgt Workflow.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span> <br /> </td> 
   <td> Ermöglicht die Überwachung der Ausführung <a href="https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/technical-workflows.html?lang=de" target="_blank"> technischen Workflows </a>operationMgt). Wenn aktiviert (Wert „1„), werden die Ausführungsinformationen in den Workflow-Auditprotokollen protokolliert.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span> <br /> </td> 
   <td> Zeitraum für die Zielgruppenbestimmungs- und Extraktionsbedingungen im geplanten Modus.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WORKFLOW_ANALYSISThreshold</span> <br /> </td> 
   <td> Anzahl der betroffenen Datensätze, nach denen die Tabellenstatistiken automatisch neu berechnet werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkReport_Logo</span> <br /> </td> 
   <td> Logo, das in der oberen rechten Ecke der exportierten Berichte angezeigt werden soll.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span> <br /> </td> 
   <td> Anzahl der Tage zwischen den Prüfungen auf pausierte Workflows.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCampaign_Activate_OwnerConfirmation</span> <br /> </td> 
   <td> Aktivieren Sie die Validierung der Sendungen durch den Inhaber des Vorgangs, indem Sie als Wert „1“ eingeben. Um diese Option zu deaktivieren, geben Sie „0“ ein.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsAsset_JavaScriptExt</span> <br /> </td> 
   <td> Zusätzliche JS-Bibliothek zum Laden in der Workflow-Aktivität „Marketing-Ressourcen-Benachrichtigungen“.<br /> </td> 
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
   <td> (ab Version 21.1.3) Wenn 1 ausgewählt ist (Standardwert), wird die Bearbeitung von integrierten Schemata durch diese Option deaktiviert.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">RestrictEditingOOTBJavascript</span> <br /> </td> 
   <td> (ab Version 21.1.3) Wenn „1“ ausgewählt ist (Standardwert), wird mit dieser Option die Bearbeitung von integrierten JavaScript-Codes deaktiviert.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkAcceptOldPasswords</span> <br /> </td> 
   <td> (Kompatibilitätsmodus für die Installation: build&gt;6000) Bei Aktivierung (Wert „1„) ermöglicht diese Option die Verwendung alter Kennwörter, die in der Datenbank für die Verbindung mit externen Konten oder der Instanz gespeichert sind.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span> <br /> </td> 
   <td> Dieser Schlüssel wird zum Verschlüsseln der meisten Kennwörter in der Datenbank verwendet. (externe Konten, LDAP-Kennwort …).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Allow_PrivilegeEscalation</span> <br /> </td> 
   <td> Wenn „1“ ausgewählt ist, wird diese Option aktiviert, um PrivilegeEscalation in JavaScript zuzulassen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_ControlsOnFileDownload</span> <br /> </td> 
   <td> Wenn „1“ ausgewählt ist, werden mit dieser Option die ACL-Steuerelemente während eines Datei-Downloads (über fileDownload.jsp) deaktiviert.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_JSFileSandboxing</span> <br /> </td> 
   <td> Wenn „1“ ausgewählt ist, deaktiviert diese Option die Datei-Sandbox in JavaScript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_SaveOptions_AllowNonAdmin</span> <br /> </td> 
   <td> Wenn auf „true“ gesetzt, autorisierter Benutzer ohne Administratorrechte, die xtkOption-Werte über den Bereitstellungsassistenten zu aktualisieren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Unsafe_DecryptString</span> <br /> </td> 
   <td> Wenn 1 ausgewählt ist, ermöglicht diese Option die Verwendung von decryptString zum Entschlüsseln einiger Kennwörter.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkTraceDeleteLogin</span> <br /> </td> 
   <td> Geben Sie den Wert „1“ ein, um das Löschen von Elementen mit Audit-Protokoll-Informationen in den mData nachzuverfolgen, indem Sie das Feld „geändert von“ vor dem Löschen des Datensatzes ändern.<br /> </td> 
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
   <td> <span class="uicontrol">MC_ENRICHMENTCustomJS</span> <br /> </td> 
   <td> JavaScript-Bibliothek wird zur Anreicherung von Ereignissen personalisiert Muss die Implementierung dieser beiden Funktionen enthalten:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">enrichRtEvents(aiEventId);</span> : reichert Ereignisse in der Datenbank an und speichert sie (wobei <span class="uicontrol">aiEventId</span> der Tabelle der verarbeiteten Echtzeit-Ereignisse entspricht).</p> </li> 
     <li> <p> <span class="uicontrol">enrichBatchEvents(aiEventId);</span> : reichert Ereignisse in der Datenbank an und speichert sie (wobei <span class="uicontrol">aiEventId</span> der ID-Tabelle der verarbeiteten Batch-Ereignisse entspricht).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span> <br /> </td> 
   <td> Datum der letzten Aktualisierung des Ereignisstatus über Versandlogs.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_ROUTINGCustomJS</span> <br /> </td> 
   <td> JavaScript-Bibliothek zum Personalisieren für Routing-Ereignisse. Muss die Implementierung dieser beiden Funktionen enthalten:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">dispatchRtEvent(iEventId);</span> : Gibt den internen Namen der Transaktionsnachricht zurück, die zur Verarbeitung des Echtzeit-Ereignisses ausgewählt wurde (wobei <span class="uicontrol">iEventId</span> der ID des verarbeiteten Echtzeit-Ereignisses entspricht).</p> </li> 
     <li> <p> <span class="uicontrol">dispatchBatchEvent(iEventId);</span> : Gibt den internen Namen der Transaktionsnachricht zurück, die zur Verarbeitung des Batch-Ereignisses ausgewählt wurde (wobei <span class="uicontrol">iEventId</span> der ID des verarbeiteten Batch-Ereignisses entspricht).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeAlert</span> <br /> </td> 
   <td> Warnschwelle für die durchschnittliche Sendungsdauer von Echtzeit-Ereignissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeWarning</span> <br /> </td> 
   <td> Hinweisschwelle für die durchschnittliche Sendungsdauer von Echtzeit-Ereignissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeAlert</span> <br /> </td> 
   <td> Warnschwelle für die durchschnittliche Verarbeitungsdauer von Echtzeit-Ereignissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeWarning</span> <br /> </td> 
   <td> Hinweisschwelle für die durchschnittliche Verarbeitungszeit von Echtzeit-Ereignissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueAlert</span> <br /> </td> 
   <td> Warnschwelle für die durchschnittliche Anzahl von Echtzeit-Ereignissen in der Warteschlange.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeAlert</span> <br /> </td> 
   <td> Warnschwelle für die durchschnittliche Verweildauer von Echtzeit-Ereignissen in der Warteschlange.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeWarning</span> <br /> </td> 
   <td> Hinweisschwelle für die durchschnittliche Verweildauer von Echtzeit-Ereignissen in der Warteschlange.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueWarning</span> <br /> </td> 
   <td> Hinweisschwelle für die durchschnittliche Anzahl von Echtzeit-Ereignissen in der Warteschlange.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorAlert</span> <br /> </td> 
   <td> Warnschwelle für Verarbeitungsfehler bei Echtzeit-Ereignissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorWarning</span> <br /> </td> 
   <td> Hinweisschwelle für Verarbeitungsfehler bei Echtzeit-Ereignissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueAlert</span> <br /> </td> 
   <td> Warnschwelle für die maximale Anzahl von Echtzeit-Ereignissen in der Warteschlange.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueWarning</span> <br /> </td> 
   <td> Hinweisschwelle für die maximale Anzahl von Echtzeit-Ereignissen in der Warteschlange.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueAlert</span> <br /> </td> 
   <td> Warnschwelle für die Mindestanzahl von Echtzeit-Ereignissen in der Warteschlange.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueWarning</span> <br /> </td> 
   <td> Hinweisschwelle für die Mindestanzahl von Echtzeit-Ereignissen in der Warteschlange.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueAlert</span> <br /> </td> 
   <td> Schwellenwert vor kritischer Bedingung für die Warteschlange ausstehender Echtzeit-Ereignisse.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span> <br /> </td> 
   <td> Hinweisschwelle für die Anzeige ausstehender Echtzeit-Ereignisse.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputAlert</span> <br /> </td> 
   <td> Warnschwelle für den Durchsatz von Echtzeit-Ereignissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputWarning</span> <br /> </td> 
   <td> Hinweisschwelle für den Durchsatz von Echtzeit-Ereignissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMessageCenter_RoutingBatchSize</span> <br /> </td> 
   <td> Größe der Neugruppierung für das Ereignis-Routing.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastRtEventStat</span> <br /> </td> 
   <td> Aktualisierungszeiger des RtEvent-Status (letztes Datum bis zum Abrufen der Daten).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_MessageCenterURL</span> <br /> </td> 
   <td> Message-Center-Server-URL für den Versand von Willkommensnachrichten (LINE-Kanal).<br /> </td> 
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
   <td> <p>Hier können Sie die Verzögerung festlegen, nach der Broadlogs aus der Datenbank gelöscht werden.</p><p>Diese Option wird automatisch erstellt, sobald die Verzögerung in der Benutzeroberfläche geändert wird. Wenn Sie den Wert in der Optionsliste ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventHistoPurgeDelay</span> <br /> </td> 
   <td><p> Ermöglicht die Definition der Verzögerung, nach der der Ereignisverlauf aus der Datenbank gelöscht wird.</p><p>
   Diese Option wird automatisch erstellt, sobald die Verzögerung in der Benutzeroberfläche geändert wird. Wenn Sie den Wert in der Optionsliste ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventPurgeDelay</span> <br /> </td> 
   <td><p> Hier können Sie die Verzögerung festlegen, nach der Ereignisse aus der Datenbank gelöscht werden.</p><p>Diese Option wird automatisch erstellt, sobald die Verzögerung in der Benutzeroberfläche geändert wird. Wenn Sie den Wert in der Optionsliste ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventStatPurgeDelay</span> <br /> </td> 
   <td><p> Hier können Sie die Verzögerung festlegen, nach der die Ereignisstatistiken aus der Datenbank gelöscht werden.</p><p>Diese Option wird automatisch erstellt, sobald die Verzögerung in der Benutzeroberfläche geändert wird. Wenn Sie den Wert in der Optionsliste ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_PropositionPurgeDelay</span> <br /> </td> 
   <td><p> Hier können Sie die Zeitspanne festlegen, nach der Vorschläge aus der Datenbank gelöscht werden.</p><p> Diese Option wird automatisch erstellt, sobald die Verzögerung in der Benutzeroberfläche geändert wird. Wenn Sie den Wert in der Optionsliste ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_QuarantineMailboxFull</span> <br /> </td> 
   <td> <p>Hier können Sie die Verzögerung festlegen, nach der die Quarantänen aus der Datenbank gelöscht werden.</p><p> Diese Option wird automatisch erstellt, sobald die Verzögerung in der Benutzeroberfläche geändert wird. Wenn Sie den Wert in der Optionsliste ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RecycledDeliveryPurgeDelay</span> <br /> </td> 
   <td> <p>Ermöglicht die Definition der Verzögerung, nach der wiederverwertete Sendungen aus der Datenbank gelöscht werden.</p><p> Diese Option wird automatisch erstellt, sobald die Verzögerung in der Benutzeroberfläche geändert wird. Wenn Sie den Wert in der Optionsliste ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RejectsPurgeDelay</span> <br /> </td> 
   <td> <p>Hier können Sie die Verzögerung festlegen, nach der Zurückweisungen aus der Datenbank gelöscht werden.</p><p>Diese Option wird automatisch erstellt, sobald die Verzögerung in der Benutzeroberfläche geändert wird. Wenn Sie den Wert in der Optionsliste ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingLogPurgeDelay</span> <br /> </td> 
   <td> <p>Hier können Sie die Verzögerung festlegen, nach der Trackinglogs aus der Datenbank gelöscht werden.</p><p>Diese Option wird automatisch erstellt, sobald die Verzögerung in der Benutzeroberfläche geändert wird. Wenn Sie den Wert in der Optionsliste ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingStatPurgeDelay</span> <br /> </td> 
   <td><p> Hier können Sie die Verzögerung festlegen, nach der Tracking-Statistiken aus der Datenbank gelöscht werden.</p><p> Diese Option wird automatisch erstellt, sobald die Verzögerung in der Benutzeroberfläche geändert wird. Wenn Sie den Wert in der Optionsliste ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_VisitorPurgeDelay</span> <br /> </td> 
   <td> <p>Hier können Sie die Verzögerung festlegen, nach der Besucher aus der Datenbank gelöscht werden.</p><p> Diese Option wird automatisch erstellt, sobald die Verzögerung in der Benutzeroberfläche geändert wird. Wenn Sie den Wert in der Optionsliste ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_WorkflowResultPurgeDelay</span> <br /> </td> 
   <td> <p>Hier können Sie die Verzögerung festlegen, nach der Workflow-Ergebnisse aus der Datenbank gelöscht werden.</p><p> Diese Option wird automatisch erstellt, sobald die Verzögerung in der Benutzeroberfläche geändert wird. Wenn Sie den Wert in der Optionsliste ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_AzureDw</span> <br /> </td> 
   <td> Azure SQL Datawarehouse Connector-Optionen.<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span> <br /> </td> 
   <td>Ermöglicht die Beeinflussung des unbedingten Stoppverhaltens für alle Workflows und PostgreSQL-Datenbankabfragen anhand der folgenden potenziellen Werte:<ul>
    <li><p>0 - Standard: Hält den Workflow-Prozess an, hat keine Auswirkungen auf die Datenbank<p></li>
    <li><p>1 - pg_cancel_backend: Hält den Workflow-Prozess an und bricht die Abfrage in der Datenbank ab<p></li>
    <li><p>2 - pg_terminate_backend: Hält den Workflow-Prozess an und beendet die Abfrage in der Datenbank<p></li></ul></td> 
  </tr>  
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span> <br /> </td> 
   <td> Name des Tablespaces, der die Daten der vorkonfigurierten Adobe Campaign-Tabellen enthalten soll.<br />Siehe <a href="../../installation/using/creating-and-configuring-the-database.md">Erstellen und Konfigurieren der Datenbank</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span> <br /> </td> 
   <td> Name des Tablespaces, der die Indizes der vorkonfigurierten Adobe Campaign-Tabellen enthalten soll.<br />Siehe <a href="../../installation/using/creating-and-configuring-the-database.md">Erstellen und Konfigurieren der Datenbank</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWork</span> <br /> </td> 
   <td> Name des Tablespaces, der die Daten der Adobe Campaign-Arbeitstabellen enthalten soll.<br />Siehe <a href="../../installation/using/creating-and-configuring-the-database.md">Erstellen und Konfigurieren der Datenbank</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWorkIndex</span> <br /> </td> 
   <td> Name des Tablespaces, der die Indizes der Adobe Campaign-Arbeitstabellen enthalten soll.<br />Siehe <a href="../../installation/using/creating-and-configuring-the-database.md">Erstellen und Konfigurieren der Datenbank</a>.</td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TempDbName</span> <br /> </td> 
   <td> Ermöglicht die Konfiguration einer separaten Datenbank für Arbeitstabellen auf Microsoft SQL Server, um Backups und Replikation zu optimieren. Die Option entspricht dem Namen der temporären Datenbank: Wenn angegeben, werden Arbeitstabellen in diese Datenbank geschrieben. Beispiel: 'tempdb.dbo.' (Beachten Sie, dass der Name mit einem Punkt enden muss.) <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server">Weitere Informationen</a> <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcTimeZone</span> <br /> </td> 
   <td> Zeitzone der Adobe Campaign-Instanz. Siehe <a href="../../installation/using/time-zone-management.md#configuration" target="_blank">Konfiguration</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseNChar</span> <br /> </td> 
   <td> Sind die Zeichenfolgenfelder der Datenbank mit NChar definiert?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseTimeStampWithTZ</span> <br /> </td> 
   <td> Speichern die 'datetime'-Felder der Datenbank Zeitzoneninformationen?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkDatabaseId</span> <br /> </td> 
   <td> Kennung der Datenbank. Beginnt mit „u“ für Unicode-Datenbank.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkInstancePrefix</span> <br /> </td> 
   <td> Zu automatisch generierten internen Namen hinzugefügtes Präfix.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkQuery_Schema_LineCount</span> <br /> </td> 
   <td> Maximale Anzahl von Ergebnissen, die von einer Abfrage für xtk:schema und xtk:srcSchema zurückgegeben werden<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSequence_AutoGeneration</span> <br /> </td> 
   <td> Alle benutzerdefinierten Schemata, die nach dieser Zeit mit autopk=„true“ und ohne das Attribut „pkSequence“ erstellt wurden, erhalten die automatisch generierte Sequenz „auto_ 
    &lt;schemaNamespace&gt; 
     &lt;schemaName&gt;
       _Sequenz. 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NlMigration_KeepFolderStructure</span> <br /> </td> 
   <td> Während der Migration wird die Baumstruktur automatisch auf der Grundlage der neuen Versionsstandards umstrukturiert.<br /> Mit dieser Option können Sie die automatische Migration des Navigationsbaums deaktivieren. Wenn Sie sie verwenden, müssen Sie nach der Migration veraltete Ordner löschen, die neuen Ordner hinzufügen und alle erforderlichen Prüfungen durchführen.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">Datentyp:</span> Integer</p> </li> 
     <li> <p> <span class="uicontrol">Wert (Text)</span> : 1 </p> </li> 
    </ul> Diese Option sollte nur verwendet werden, wenn der vordefinierte Navigationsbaum zu viele Änderungen erfahren hat.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatCoalesce</span> <br /> </td> 
   <td> Letztes Verarbeitungsdatum der <span class="uicontrol">NmsEmailErrorStat</span>-Tabellenbereinigung.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PostUpgradeLastError</span> <br /> </td> 
   <td> Informationen zum Fehler, der beim Postupgrade aufgetreten ist, gemäß der folgenden Syntax:<br /> <strong>{Build-Nummer}:{mode: pre/post/…}:{The 'lessThan'/'largerOrEquelThan' where error occured + sub-step}</strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkCleanup_NoStats</span> <br /> </td> 
   <td> Geben Sie den Wert „1“ ein, damit die Aktualisierung der Statistiken nicht über den Bereinigungs-Workflow durchgeführt wird.<br /> </td> 
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
   <td> Typen von AEM-Ressourcen, die in Adobe Campaign verwendet werden können. Die Werte müssen durch Kommas getrennt werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">nmsPipeline_config</span> <br /> </td> 
   <td> Ermöglicht die Konfiguration von Experience Cloud Trigger. Datentyp ist „long text“ und muss im JSON-Format vorliegen. Siehe <a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">Verwenden von Experience Cloud Trigger mit Adobe Campaign Classic</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</span> <br /> </td> 
   <td> Diese Option wird beim Importieren von Daten aus einem Drittanbietersystem über einen CRM-Connector verwendet. Durch Aktivierung dieser Option können Sie nur die seit dem letzten Import geänderten Objekte erfassen. Diese Option muss wie folgt manuell erstellt und ausgefüllt werden: 
    <ul> 
     <li> <p> <span class="uicontrol">Interner Name</span> : LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</p> </li> 
     <li> <p> <span class="uicontrol">Wert (Feld)</span> : Datum des letzten Imports im Format jjjj/MM/tt hh:mm:ss. </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_EdgeServer</span> <br /> </td> 
   <td> Für die Integration verwendeter Adobe Target-Server Diese Option ist standardmäßig ausgefüllt. Dieser Wert entspricht dem Adobe Target-Domänenserver, gefolgt vom Wert /m2. Beispiel: tt.omtrdc.net/m2.<br /> Siehe <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">diesen Abschnitt</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_TENANTName</span> <br /> </td> 
   <td> Adobe Target-Organisationsname. Dieser Wert entspricht dem Namen des Adobe Target-Clients.<br /> Siehe <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">diesen Abschnitt</a>.<br /> </td> 
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
   <td> Teradata Connector-Optionen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Hive</span> <br /> </td> 
   <td> Hive-Connector-Optionen.<br /> </td> 
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
   <td> Anzahl der Coupons, die pro SQL-Transaktion aktualisiert werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchControl_</span> <br /> </td> 
   <td> '+ [Schema der Proposition] + „_“ + extAccountSource.@executionInstanceId + [Schema der Proposition] + „_“ + vars.executionInstanceIdFilter<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchExec_</span> <br /> </td> 
   <td> '+ [ Schema der Proposition] + „_“ + extAccountSource.@executionInstanceId + „_“ + extAccountTarget.@executionInstanceId<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_SynchWorkflowIds</span> <br /> </td> 
   <td> Tracking des Synchronisations-Workflows.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_UseDaemon</span> <br /> </td> 
   <td> Asynchrone Vorschlagsbearbeitung aktivieren/deaktivieren („0“ zum Deaktivieren, „1“ zum Aktivieren).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsModule_CouponsEnabled</span> <br /> </td> 
   <td> Ermöglicht die Aktivierung von Gutscheinen.<br /> </td> 
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
   <td> Ausführungsinstanz-Kennung.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_CustomerId</span> <br /> </td> 
   <td> Kundenkennung, die beim Versand des Abrechnungsberichts verwendet wird.<br /> </td> 
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
   <td> Ermöglicht die Verwendung alter nicht deklarierter SQL-Funktionen nach der Migration. Wir empfehlen dringend, diese Option aufgrund der damit verbundenen Sicherheitsrisiken nicht zu verwenden.<br /> </td> 
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
   <td> Option zum Aktivieren des Trackings.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ClickFormula</span> <br /> </td> 
   <td> Berechnungs-Script der getrackten URL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ExtAccount</span> <br /> </td> 
   <td> Ermöglicht die Definition des externen Kontos des Tracking-Servers.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Instance</span> <br /> </td> 
   <td> Ermöglicht die Definition des Instanznamens auf dem Trackingserver.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_LastConsolidation</span> <br /> </td> 
   <td> Letztes Mal, wenn die Tracking-Informationen mit neuen Daten konsolidiert wurden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_OpenFormula</span> <br /> </td> 
   <td> URL-Berechnungsskript öffnen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Password</span> <br /> </td> 
   <td> Passwort des Trackingservers<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Pointer</span> <br /> </td> 
   <td> Der Zeiger verfolgt die letzten Nachrichtenereignisse, die über ihre IDs und ihr Datum verarbeitet wurden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_SecureServerUrl</span> <br /> </td> 
   <td> Sichere URL des Fronttrackingservers.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrl</span> <br /> </td> 
   <td> URL des frontalen Trackingservers.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrlList</span> <br /> </td> 
   <td> Liste der URLs, über die die Tracking-Server kontaktiert werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_UserAgentRules</span> <br /> </td> 
   <td> Regelsatz zur Browser-Identifizierung.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebFormula</span> <br /> </td> 
   <td> Script zur Berechnung der Webtracking-Tags.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingDelivery</span> <br /> </td> 
   <td> Name des virtuellen Versands, der für die Webtracking-Verwaltung entwickelt wurde.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingMode</span> <br /> </td> 
   <td> Ermöglicht die Definition des Webtracking-Modus.<br /> </td> 
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
   <td> <span class="uicontrol">PRIVACY_REQUEST_CONFIRMdeletePending</span> <br /> </td> 
   <td> Wenn Option 1 ausgewählt ist, müssen Sie den Löschvorgang in einem zweiten Schritt manuell in der Benutzeroberfläche bestätigen. Andernfalls werden Daten ohne Bestätigung gelöscht.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PRIVACY_REQUEST_CONFIRMdeletePendingDelay</span> <br /> </td> 
   <td> Wartezeit auf die Löschbestätigung vor Stornierung der Anfrage ist aufgehoben.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_MaxErrorAllowed</span> <br /> </td> 
   <td> Die maximale Anzahl von zulässigen Fehlern bei der Verarbeitung/Löschung einer Datenschutzanfrage.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_PurgeDelay</span> <br /> </td> 
   <td> Verzögerung zwischen der Anfrageerstellung in der Warteschlange und der Löschung der Anfragedaten.<br /> </td> 
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
   <td> Aktivieren Sie die Verwendung des LDAP-Servers zur Authentifizierung von Benutzern und zur Bereitstellung von Berechtigungen für Benutzer.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppLogin</span> <br /> </td> 
   <td> Anwendungs-Login, um den Server für verschiedene Suchvorgänge zu kontaktieren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppPassword</span> <br /> </td> 
   <td> Verschlüsseltes Passwort für den Anwendungs-Login.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AutoOperator</span> <br /> </td> 
   <td> Aktiviert die automatische Erstellung von Benutzenden und Rechten in Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DN</span> <br /> </td> 
   <td> Berechnungsformel für LDAP-DN basierend auf der Anmeldung.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearch</span> <br /> </td> 
   <td> DN-Suche in Verzeichnis aktivieren.<br /> </td> 
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
   <td> Authentifizierungstyp für die Verbindung mit dem LDAP-Server (plain, md5, lds, ntlm, dpa).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_rights</span> <br /> </td> 
   <td> Aktivieren Sie in Adobe Campaign die Synchronisierung von Berechtigungen und Gruppen aus dem LDAP-Ordner mit spezifischen Berechtigungen.<br /> </td> 
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
   <td> Suchfilter für Benutzerautorisierungen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsMask</span> <br /> </td> 
   <td> Ausdruck, um die Namen der Adobe Campaign-Berechtigungen aus den LDAP-Berechtigungen zu extrahieren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsScope</span> <br /> </td> 
   <td> Suchbereich.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Server</span> <br /> </td> 
   <td> LDAP-Server-Adresse (es ist möglich, einen Port durch Angabe von ":“ als Trennzeichen anzugeben).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Web-Formulare {#web-forms}

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
   <td> Wenn der Wert auf 1 festgelegt ist, kann zu Detailformularen eine Bildlaufleiste hinzugefügt werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Instance</span> <br /> </td> 
   <td> Bei der Annullierung von Webformularen im „Andere(r) Server“-Modus zu verwendende Instanz<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Password</span> <br /> </td> 
   <td> Kennwort der bei der Annullierung von Webformularen im „Andere(r) Server“-Modus zu verwendenden Instanz.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersMode</span> <br /> </td> 
   <td> Option, die es ermöglicht, den Annullierungsmodus für Webformulare anzugeben: standardmäßig lokal, via Trackingserver, wenn die Option „Tracking“ angegeben ist, und über eine benutzerdefinierte Liste, wenn die Option „Andere(r) Server“ angegeben ist.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersURLs</span> <br /> </td> 
   <td> Benutzerdefinierte Liste der Serveradressen, die bei der Annullierung von Webformularen im Modus 'Andere(r) Server' zu kontaktieren sind.<br /> </td> 
  </tr> 
 </tbody> 
</table>

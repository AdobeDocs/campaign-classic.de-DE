---
solution: Campaign Classic
product: campaign
title: Konfigurieren von Optionen für die Kampagne
description: Erfahren Sie, wie Sie die Optionen für die Kampagne konfigurieren
audience: installation
content-type: reference
topic-tags: appendices
translation-type: tm+mt
source-git-commit: a9d58e25ab17baaabf4ff8c109b53e83c7d93218
workflow-type: tm+mt
source-wordcount: '3930'
ht-degree: 12%

---


# Liste der Optionen von Campaign Classic{#configuring-campaign-options}

Mit dem Knoten **[!UICONTROL Administration/Platform/Options]** können Sie Adobe Campaign-Optionen konfigurieren.

>[!NOTE]
>
>Das Ändern oder Aktualisieren von Adobe Campaign-Optionen kann nur von Experten-Benutzern durchgeführt werden.

Einige von ihnen sind bei der Installation der Kampagne integriert, andere können bei Bedarf manuell hinzugefügt werden. Die verfügbaren Optionen variieren je nach installierten Paketen.

## Versand {#delivery}

<table> 
 <thead> 
  <tr> 
   <th> Optionsname </th> 
   <th> Beschreibung  </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgDate</span> <br /> </td> 
   <td> Datum des letzten von der Auslieferungsinstanz abgerufenen breitLogMsg.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgSent</span> <br /> </td> 
   <td> Datum des letzten breitLogMsg, das an die Bereitstellungsinstanz gesendet wurde.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_cuid</span> <br /> </td> 
   <td> Versandberichte-ID. Bitte wenden Sie sich an den Support, um Ihren Bezeichner zu erhalten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_SeedTargets</span> <br /> </td> 
   <td> Liste der Schema, für die Sie Testadressen für das Inbox-Rendering verwenden möchten. (Elementnamen werden durch Kommas getrennt) Beispiel: custom_nms_Empfänger.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NMS_ActivateOwnerConfirmation</span> <br /> </td> 
   <td><p> Ermöglicht es dem für den Versand zuständigen Operator, den Senden zu bestätigen, wenn ein bestimmter Operator oder eine bestimmte Benutzergruppe zum Starten eines Versands in den Eigenschaften des Versands vorgesehen ist.</p><p> Aktivieren Sie dazu die Option, indem Sie "1"als Wert eingeben. Um diese Option zu deaktivieren, geben Sie "0"ein.</p><p> Der Prozess zur Bestätigung des Sendevorgangs funktioniert dann standardmäßig: Nur der für den Versand bestimmte Operator oder die Benutzergruppe in den Eigenschaften des Versands (oder ein Administrator) kann den Versand bestätigen und durchführen. Siehe <a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">diesen Abschnitt</a>.</p> </td> 
   <tr> 
   <td> <span class="uicontrol">Nms_DefaultRcpSchema</span> <br /> </td> 
   <td> Adobe Campaign verwendet eine globale Variable "Nms_DefaultRcpSchema", um mit der standardmäßigen Empfänger-Datenbank (nms:Empfänger) zu kommunizieren.<br /> Der Optionswert muss mit dem Namen des Schemas übereinstimmen, der der Tabelle des externen Empfängers entspricht.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBilling_MainActionThreshold</span> <br /> </td> 
   <td> Mindestanzahl von Empfängern, damit ein Versand als der wichtigste im Abrechnungsbericht gilt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_DefaultProvider</span> <br /> </td> 
   <td> Standard-Routing-Dienstleister für neue Vorlagen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransac</span> <br /> </td> 
   <td> Anzahl der BroadLogs, die gleichzeitig für einen Versand erstellt werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransac</span> <br /> </td> 
   <td> Einfügen (in die Tabelle) von Protokollen (wideLogs) pro Transaktion: Anzahl der zu verarbeitenden Zeilen pro Stapel.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span> <br /> </td> 
   <td> Gruppieren von Versand-Teilen bei der Analyse von Mid-Sourcing-Versänden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgValidityDuration</span> <br /> </td> 
   <td> Standardzeitraum für Versand eines Versands (in Sekunden).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RegexRules</span> <br /> </td> 
   <td> Regulärer Ausdruck zur Bereinigung der Versandnachrichten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveBlackList</span> <br /> </td> 
   <td> Durch Eingabe von "1"als Wert können Sie Empfänger ausschließen, die keine Kontaktaufnahme mehr wünschen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicatesEmpfänger</span> <br /> </td> 
   <td> Durch Eingabe von "1"als Wert können Sie Dubletten automatisch ignorieren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ErrorAddressMask</span> <br /> </td> 
   <td> Hiermit können Sie die Syntax der Fehleradresse definieren, die beim Beantworten einer Nachricht verwendet wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_FromAddressMask</span> <br /> </td> 
   <td> Hiermit können Sie die Syntax der "Von"-Adresse definieren, die beim Senden einer Nachricht verwendet wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageServerTimeout</span> <br /> </td> 
   <td> Ermöglicht die Festlegung einer Timeout-Grenze (in Sekunden) für das Abrufen einer Antwort vom Server beim Abrufen eines Bildes, das von einer personalisierten URL heruntergeladen und an eine E-Mail angehängt wurde. Wenn dieser Wert überschritten wird, kann die Nachricht nicht gesendet werden. Der Standardwert ist 60 Sekunden.<br /> </td> 
  </tr> 
 <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxDownloadedImageSize</span> <br /> </td> 
   <td> Hiermit können Sie die maximale Größe (in Byte) festlegen, die für ein Bild zulässig ist, das von einer personalisierten URL heruntergeladen und an eine E-Mail angehängt wird. Der Standardwert ist 100.000 Byte. Wenn beim Senden eines Testversands und Herunterladen des bzw. der Bilder zur Verarbeitung der E-Mail die Bildgröße diesen Wert überschreitet oder ein Download-Problem auftritt, wird in den Versandlogs ein Fehler angezeigt, und der Testversand-Versand schlägt fehl.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRecommendedAttachments</span> <br /> </td> 
   <td> Ermöglicht die Festlegung einer maximalen Anzahl von Anlagen in einer E-Mail- oder Transaktionsvorlage. Wenn dieser Wert überschritten wird, wird eine Warnung in den Protokollen der Versand-Analyse oder beim Veröffentlichen der transaktionalen E-Mail-Vorlage angezeigt. Der Standardwert ist 1 Anlage.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRetry</span> <br /> </td> 
   <td> Maximale Anzahl weitere Zustellversuche während der Analyse.<br /> </td> 
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
   <td> Zeigen Sie die Gewichtung der Nachricht im Versand-Assistent an.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultErrorAddr</span> <br /> </td> 
   <td> StandardE-Mail-Adresse "Fehler"auf Instanzebene, die für E-Mail-Versand verwendet wird, wenn der Benutzer keine E-Mail-Adresse angegeben hat.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAdd</span> <br /> </td> 
   <td> Standardmäßige "von" E-Mail-Adresse auf Instanzebene, die für E-Mail-Versand verwendet wird, wenn der Benutzer keine E-Mail-Adresse angegeben hat.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span> <br /> </td> 
   <td> Standardmäßige E-Mail-Adresse auf Instanzebene für E-Mail-Versand, wenn vom Benutzer leer gelassen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganisation</span> <br /> </td> 
   <td> Allgemeiner Name des Kunden. Wird in einigen Warnmeldungen verwendet, die den Empfängern angezeigt werden.<br /> "Sie erhalten diese Nachricht, weil Sie mit ***** oder einer angeschlossenen Firma in Kontakt gekommen sind. So empfangen Sie keine Nachrichten mehr von ****".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span> <br /> </td> 
   <td> Die standardmäßige "von" E-Mail-Beschriftung auf Instanzebene, die für E-Mail-Versand verwendet wird, wenn der Benutzer keine Angabe enthält.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span> <br /> </td> 
   <td> Standardmäßige E-Mail-Antwort-E-Mail-Beschriftung auf Instanzebene, die für E-Mail-Versand verwendet wird, wenn vom Benutzer leer gelassen wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryCount</span> <br /> </td> 
   <td> Zeitraum zwischen zwei weiteren Zustellversuchen einer E-Mail-Nachricht (in Sekunden).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryPeriod</span> <br /> </td> 
   <td> Weitere Zustellversuche für E-Mail-Nachrichten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsForecast_MsgWeightFormel</span> <br /> </td> 
   <td> Formel zur Berechnung der Gewichtung einer Nachricht in einem geplanten Versand.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_AllowlistEmails</span> <br /> </td> 
   <td> Liste von autorisierten Weiterleitungs-E-Mail-Adressen (aus dem Modul für die Verarbeitung von eingehenden Nachrichten). Die Adressen müssen durch Kommas getrennt werden (oder *, um alle zuzulassen). Beispiel: xyz@abc.com,pqr@abc.com<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span> <br /> </td> 
   <td> Im 'lineImage'-Servlet für die URL-Verschlüsselung verwendeter AES-Schlüssel (LINE-Kanal).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailMaxError</span> <br /> </td> 
   <td> Auf Kanal "email"(als Standard verwenden): Maximale Anzahl der Fehler, die bei SOFT-Fehlern beim Senden akzeptiert werden, bevor der Empfänger in die Quarantäne gestellt wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailSignificantErrorDelay</span> <br /> </td> 
   <td> Auf Kanal "email"(als Standard verwenden): Minimaler Zeitraum, der seit dem vorherigen referenzierten SOFT-Fehler verbracht wird, bevor ein neuer SOFT-Fehler berücksichtigt wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileMaxError</span> <br /> </td> 
   <td> Kanal "mobile": Maximale Anzahl der Fehler, die bei SOFT-Fehlern beim Senden akzeptiert werden, bevor der Empfänger in die Quarantäne gestellt wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileSignificantErrorDelay</span> <br /> </td> 
   <td> Kanal "mobile": Minimaler Zeitraum, der seit dem vorherigen referenzierten SOFT-Fehler verbracht wird, bevor ein neuer SOFT-Fehler berücksichtigt wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_LogsPeriodHour</span> <br /> </td>
   <td> Ermöglicht die Angabe eines maximalen Zeitraums (in Stunden ausgedrückt), um die Anzahl der bei jeder Ausführung des Synchronisierungs-Workflows wiederhergestellten Broadlogs zu begrenzen.</a>.<br /> </td> 
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
   <td> <span class="uicontrol">NmsOperation_DeliveryVorbereitungsfenster</span> <br /> </td> 
   <td><p>Diese Option wird vom technischen Arbeitsablauf <span class="uicontrol"><a href="../../workflow/using/about-technical-workflows.md">operationMgt</a></span> beim Zählen der Anzahl der ausgeführten Versand verwendet.</p>Damit können Sie festlegen, nach wie vielen Tagen Versand mit inkonsistentem Status von der Anzahl laufender Versand ausgeschlossen werden.</p><p>Standardmäßig ist der Wert auf "7"gesetzt, d. h. inkonsistente Versand, die älter als 7 Tage sind, werden ausgeschlossen.</p></td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine1</span> <br /> </td> 
   <td> Zeile 1 der Adresse des Absenders.<br /> </td> 
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
   <td> URL des Mirrorseite-Servers (standardmäßig sollte identisch mit NmsTracking_ServerUrl sein).<br /> Dies ist der Standardwert von E-Mail-Versänden, wenn die URL in der Routing-Definition nicht angegeben ist.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_Priority</span> <br /> </td> 
   <td> Parameter der gesendeten SMS: Informationen, die an das SMS-Gateway übermittelt werden, um die Nachrichtenpriorität anzugeben.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span> <br /> </td> 
   <td> Anzahl der weitere Zustellversuche beim Senden von SMS-Nachrichten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span> <br /> </td> 
   <td> Zeitraum, in dem weitere Zustellversuche von SMS-Nachrichten ausgeführt werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsUserAgentStats_LastConsolidation</span> <br /> </td> 
   <td> Letztes Konsolidierungsdatum für <span class="uicontrol">NmsUserAgent</span> Statistik.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsWebSegments_LastStates</span> <br /> </td> 
   <td> Name der Option, die die Websegmente und deren Status enthält.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkBarcode_SpecialChar</span> <br /> </td> 
   <td> Unterstützung für Sonderzeichen für Code128 aktivieren/deaktivieren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkEmail_Characters</span> <br /> </td> 
   <td> Gültige Zeichen für eine E-Mail-Adresse.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Restrict_EditXML</span> </td> 
   <td> hinzufügen Sie diese Option mit dem Wert "0", um die Ausgabe des XML-Codes des Versands zu deaktivieren (Rechtsklick / <span class="uicontrol">XML-Quelle bearbeiten</span> oder <span class="uicontrol">STRL + F4</span>-Verknüpfung).<br /> </td> 
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
   <th> Beschreibung  </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDir</span> <br /> </td> 
   <td> Speicherort der Veröffentlichungsressourcen in der Adobe Campaign-Client-Konsole. Siehe <a href="../../delivery/using/formatting.md#image-referencing">diesen Abschnitt</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDirPreview</span> <br /> </td> 
   <td> Speicherort der Ressourcen für die Vorschau in der Adobe Campaign-Client-Konsole. Siehe <a href="../../delivery/using/formatting.md#image-referencing">diesen Abschnitt</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_DefaultIgnoredImage</span> <br /> </td> 
   <td> Liste der URL-Masken für beim Online-Stellen ignorierte Bilder.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImagePublishing</span> </td> 
   <td> Konfiguration zum Online-Stellen der Bilder. Die Werte können none / tracking / script / Liste sein (kann durch die optionalen Einstellungen des Operators überschrieben werden). </td> 
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
   <td> Wurzelordner für Veröffentlichungen.<br /> Weitere Informationen zur Erstellung von HTML- und Textinhalten finden Sie in  <a href="../../delivery/using/using-a-content-template.md">diesem Abschnitt</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkImageUrl</span> <br /> </td> 
   <td> Hiermit können Sie den Server definieren, auf dem die in den Versänden verwendeten Bilder gespeichert werden, damit der Browser sie abrufen kann.<br /> Für Buildversionen  &lt;&gt;<br /> Bei Buildversionen &gt; 5098 verwenden wir stattdessen die öffentliche URL des Versands oder die URL der  <span class="uicontrol">Option "XtkFileRes_Public_</span> URL".<br /> </td> 
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

## Kampagne- und Workflow-Management {#campaign-e-workflow-management}

<table> 
 <thead> 
  <tr> 
   <th> Optionsname </th> 
   <th> Beschreibung  </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">CrmMarketingActivityWindow</span> <br /> </td> 
   <td> Marketingverlauf für diese Anzahl Monate angezeigt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_Duration</span> <br /> </td> 
   <td> Standardgültigkeitsdauer einer Kampagne (in Sekunden).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_LimitConcurrency</span> <br /> </td> 
   <td> Maximale Anzahl von Versand-/Workflow-/Hypothese-/Simulation-Aufträgen, die zu einem Zeitpunkt verarbeitet werden können, der vom operationMgt-Workflow gestartet werden kann.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span> <br /> </td> 
   <td> Ermöglicht die Überwachung der Ausführung des technischen Workflows <a href="../../workflow/using/about-technical-workflows.md">operationMgt</a>. Bei Aktivierung (Wert "1") werden die Ausführungsinformationen in den Workflow-Prüfprotokollen protokolliert.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span> <br /> </td> 
   <td> Zeitraum für Targeting- und Extraktion-Bedingungen im geplanten Modus.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Workflow_AnalysisThreshold</span> <br /> </td> 
   <td> Anzahl der betroffenen Datensätze, nach denen Tabellenstatistiken automatisch neu berechnet werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkReport_Logo</span> <br /> </td> 
   <td> Das Logo, das in der oberen rechten Ecke des exportierten Berichts angezeigt werden soll.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span> <br /> </td> 
   <td> Anzahl der Tage, die zwischen den Prüfungen auf angehaltene Workflows gewartet werden sollen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCampaign_Activate_OwnerConfirmation</span> <br /> </td> 
   <td> Aktivieren Sie die Überprüfung der Versand durch den Eigentümer des Vorgangs, indem Sie "1"als Wert eingeben. Um diese Option zu deaktivieren, geben Sie "0"ein.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsAsset_JavascriptExt</span> <br /> </td> 
   <td> Zusätzliche JS-Bibliothek, die in der Aktivität "Marketing-Ressource-Benachrichtigungen"des Workflows geladen wird.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Sicherheit {#security}

<table> 
 <thead> 
  <tr> 
   <th> Optionsname </th> 
   <th> Beschreibung  </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkAcceptOldPasswords</span> <br /> </td> 
   <td> (Kompatibilitätsmodus installieren: build&gt;6000) Bei Aktivierung (Wert "1") ermöglicht diese Option die Verwendung alter Kennwörter, die in der Datenbank für die Verbindung zu Externen Konti oder zur Instanz gespeichert sind.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span> <br /> </td> 
   <td> Mit diesem Schlüssel werden die meisten Kennwörter in der Datenbank verschlüsselt. (Externe Konti, LDAP-Kennwort...).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Allow_PrivilegeEscalation</span> <br /> </td> 
   <td> Wenn 1 ausgewählt ist, aktivieren Sie diese Option, um "privilegeEskalation"in JavaScript zuzulassen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_ControlsOnFileDownload</span> <br /> </td> 
   <td> Wenn 1 ausgewählt ist, deaktivieren Sie diese Option die ACL-Steuerelemente während des Dateidownloads (über fileDownload.jsp).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_JSFileSandboxing</span> <br /> </td> 
   <td> Wenn 1 ausgewählt ist, deaktivieren Sie mit dieser Option die Datei-Sandbox in JavaScript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_SaveOptions_AllowNonAdmin</span> <br /> </td> 
   <td> Wenn "true"festgelegt ist, darf der Nicht-Admin-Operator die xtkOption-Werte über den Bereitstellungsassistenten aktualisieren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Unsafe_DecryptString</span> <br /> </td> 
   <td> Wenn 1 ausgewählt ist, können mit dieser Option einige Kennwörter mithilfe von decryptString entschlüsselt werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkTraceDeleteLogin</span> <br /> </td> 
   <td> Geben Sie den Wert "1"ein, um das Löschen von Elementen mit Audit-Trail-Informationen in mData durch Änderung des Felds "Geändert von"vor dem Löschen des Datensatzes zu verfolgen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Message Center {#message-center}

<table> 
 <thead> 
  <tr> 
   <th> Optionsname </th> 
   <th> Beschreibung  </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">MC_EnrichmentCustomJs</span> <br /> </td> 
   <td> JavaScript-Bibliothek, die zur Bereicherung von Ereignissen personalisiert werden soll. Muss die Implementierung dieser beiden Funktionen enthalten:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">enrichRtEvents(aiEventId);</span> : bereichert und speichert Ereignis in der Datenbank (wobei  <span class="uicontrol"></span> aiEventID der Tabelle der verarbeiteten Echtzeit-Ereignis entspricht).</p> </li> 
     <li> <p> <span class="uicontrol">enrichBatchEvents(aiEventId);</span> : bereichert und speichert Ereignis in der Datenbank (wobei  <span class="uicontrol"></span> aiEventID der ID-Tabelle der verarbeiteten Batch-Ereignis entspricht).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span> <br /> </td> 
   <td> Datum des letzten Updates der Ereignisstatus aus den Versandlogs<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RoutingCustomJs</span> <br /> </td> 
   <td> JavaScript-Bibliothek, die für Routing-Ereignis personalisiert werden soll. Muss die Implementierung dieser beiden Funktionen enthalten:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">dispatRtEvent(iEventId);</span> : gibt den internen Namen der Transaktionsnachricht zurück, die zur Verarbeitung des Echtzeit-Ereignisses ausgewählt wurde (wobei  <span class="uicontrol"></span> iEventId der ID des verarbeiteten Echtzeit-Ereignisses entspricht).</p> </li> 
     <li> <p> <span class="uicontrol">dispatchBatchEvent(iEventId);</span> : gibt den internen Namen der Transaktionsnachricht zurück, die zur Verarbeitung des Batch-Ereignisses ausgewählt wurde (wobei  <span class="uicontrol"></span> iEventId der ID des verarbeiteten Batch-Ereignisses entspricht).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeAlert</span> <br /> </td> 
   <td> Warnungsschwellenwert der durchschnittlichen Sendezeit von Echtzeit-Ereignissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeWarning</span> <br /> </td> 
   <td> Warnungsschwellenwert für die durchschnittliche Sendezeit von Echtzeit-Ereignissen.<br /> </td> 
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
   <td> Warnungsschwellenwert für die durchschnittliche Warteschlangenzeit von Echtzeit-Ereignissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeWarning</span> <br /> </td> 
   <td> Warnungsschwellenwert für die durchschnittliche Wartezeit von Echtzeit-Ereignissen.<br /> </td> 
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
   <td> Warnungsschwellenwert für die maximale Anzahl von Echtzeit-Ereignissen in der Warteschlange.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueAlert</span> <br /> </td> 
   <td> Warnungsschwellenwert für die Mindestanzahl von Echtzeit-Ereignissen in der Warteschlange.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueWarning</span> <br /> </td> 
   <td> Warnschwellenwert für die Mindestanzahl von Echtzeit-Ereignissen in der Warteschlange.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueAlert</span> <br /> </td> 
   <td> Schwellenwert vor kritischer Bedingung für die Warteschlange ausstehender Echtzeit-Ereignis.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span> <br /> </td> 
   <td> Schwellenwert vor Warnung für die Warteschlange ausstehender Echtzeit-Ereignis.<br /> </td> 
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
   <td> Aktualisieren Sie den Zeiger des RtEvent-Status (letztes Datum bis zum Abrufen der Daten).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_MessageCenterURL</span> <br /> </td> 
   <td> Message Center-Server-URL zum Senden von Begrüßungsmeldungen (LINE-Kanal).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Datenbank {#database}

<table> 
 <thead> 
  <tr> 
   <th> Optionsname </th> 
   <th> Beschreibung  </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_LastCleanup</span> <br /> </td> 
   <td> Definiert das letzte Mal, dass der Bereinigungsprozess ausgeführt wurde.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_BroadLogPurgeDelay</span> <br /> </td> 
   <td> <p>Hiermit können Sie die Verzögerung definieren, nach der die Erweiterung aus der Datenbank gelöscht wird.</p><p>Diese Option wird automatisch erstellt, sobald die Verzögerung in der Schnittstelle geändert wurde. Wenn Sie den Wert aus der Liste "Optionen"ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventHistoPurgeDelay</span> <br /> </td> 
   <td><p> Hiermit können Sie die Verzögerung definieren, nach der der Datenbankverlauf gelöscht wird.</p><p>
   Diese Option wird automatisch erstellt, sobald die Verzögerung in der Schnittstelle geändert wurde. Wenn Sie den Wert aus der Liste "Optionen"ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventPurgeDelay</span> <br /> </td> 
   <td><p> Hiermit können Sie die Verzögerung definieren, nach der Ereignis aus der Datenbank gelöscht werden.</p><p>Diese Option wird automatisch erstellt, sobald die Verzögerung in der Schnittstelle geändert wurde. Wenn Sie den Wert aus der Liste "Optionen"ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventStatPurgeDelay</span> <br /> </td> 
   <td><p> Hiermit können Sie die Verzögerung definieren, nach der die Datenbankstatistiken gelöscht werden.</p><p>Diese Option wird automatisch erstellt, sobald die Verzögerung in der Schnittstelle geändert wurde. Wenn Sie den Wert aus der Liste "Optionen"ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_PropositionPurgeDelay</span> <br /> </td> 
   <td><p> Hiermit können Sie die Verzögerung definieren, nach der Vorschläge aus der Datenbank gelöscht werden.</p><p> Diese Option wird automatisch erstellt, sobald die Verzögerung in der Schnittstelle geändert wurde. Wenn Sie den Wert aus der Liste "Optionen"ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_QuarantineMailboxFull</span> <br /> </td> 
   <td> <p>Hiermit können Sie die Verzögerung definieren, nach der die Quarantänen aus der Datenbank gelöscht werden.</p><p> Diese Option wird automatisch erstellt, sobald die Verzögerung in der Schnittstelle geändert wurde. Wenn Sie den Wert aus der Liste "Optionen"ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RecycledDeliveryPurgeDelay</span> <br /> </td> 
   <td> <p>Hiermit können Sie die Verzögerung definieren, nach der recycelte Versand aus der Datenbank gelöscht werden.</p><p> Diese Option wird automatisch erstellt, sobald die Verzögerung in der Schnittstelle geändert wurde. Wenn Sie den Wert aus der Liste "Optionen"ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RejectsPurgeDelay</span> <br /> </td> 
   <td> <p>Hiermit können Sie die Verzögerung definieren, nach der die Ablehnung aus der Datenbank gelöscht wird.</p><p>Diese Option wird automatisch erstellt, sobald die Verzögerung in der Schnittstelle geändert wurde. Wenn Sie den Wert aus der Liste "Optionen"ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingLogPurgeDelay</span> <br /> </td> 
   <td> <p>Hiermit können Sie die Verzögerung definieren, nach der Trackinglogs aus der Datenbank gelöscht werden.</p><p>Diese Option wird automatisch erstellt, sobald die Verzögerung in der Schnittstelle geändert wurde. Wenn Sie den Wert aus der Liste "Optionen"ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingStatPurgeDelay</span> <br /> </td> 
   <td><p> Hiermit können Sie die Verzögerung definieren, nach der Verfolgungsstatistiken aus der Datenbank gelöscht werden.</p><p> Diese Option wird automatisch erstellt, sobald die Verzögerung in der Schnittstelle geändert wurde. Wenn Sie den Wert aus der Liste "Optionen"ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_VisitorPurgeDelay</span> <br /> </td> 
   <td> <p>Hiermit können Sie die Verzögerung definieren, nach der Besucher aus der Datenbank gelöscht werden.</p><p> Diese Option wird automatisch erstellt, sobald die Verzögerung in der Schnittstelle geändert wurde. Wenn Sie den Wert aus der Liste "Optionen"ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_WorkflowResultPurgeDelay</span> <br /> </td> 
   <td> <p>Hiermit können Sie die Verzögerung definieren, nach der Workflow-Ergebnisse aus der Datenbank gelöscht werden.</p><p> Diese Option wird automatisch erstellt, sobald die Verzögerung in der Schnittstelle geändert wurde. Wenn Sie den Wert aus der Liste "Optionen"ändern, sollte er in Sekunden ausgedrückt werden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapability_AzurblausDw</span> <br /> </td> 
   <td> Azurblaue SQL Data Warehouse-Connector-Optionen.<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span> <br /> </td> 
   <td>Ermöglicht Ihnen, das Verhalten "Nicht-bedingter Stopp"bei allen Workflows- und PostgreSQL-Abfragen gemäß den folgenden potenziellen Werten zu beeinflussen:<ul>
    <li><p>0 - default: stoppt Workflow-Prozess, keine Auswirkung auf die Datenbank<p></li>
    <li><p>1 - pg_cancel_backend: stoppt den Workflow-Prozess und bricht die Abfrage in der Datenbank ab<p></li>
    <li><p>2 - pg_terminate_backend: beendet den Workflow-Prozess und beendet die Abfrage in der Datenbank<p></li></ul></td> 
  </tr>  
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span> <br /> </td> 
   <td> Name des Tablespace, der die Daten der Adobe Campaign-Standardtabellen enthalten soll.<br />Siehe  <a href="../../installation/using/creating-and-configuring-the-database.md">Erstellen und Konfigurieren der Datenbank</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span> <br /> </td> 
   <td> Tablespace-Name für die Standardtabellen-Indexe in Adobe Campaign.<br />Siehe  <a href="../../installation/using/creating-and-configuring-the-database.md">Erstellen und Konfigurieren der Datenbank</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWork</span> <br /> </td> 
   <td> Tablespace-Name für die Arbeitstabellen-Daten in Adobe Campaign.<br />Siehe  <a href="../../installation/using/creating-and-configuring-the-database.md">Erstellen und Konfigurieren der Datenbank</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWorkIndex</span> <br /> </td> 
   <td> Tablespace-Name für die Arbeitstabellen-Indexe in Adobe Campaign.<br />Siehe  <a href="../../installation/using/creating-and-configuring-the-database.md">Erstellen und Konfigurieren der Datenbank</a>.</td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TempDbName</span> <br /> </td> 
   <td> Damit können Sie eine separate Datenbank für Tabellen auf Microsoft SQL Server konfigurieren, um Backups und Replizierung zu optimieren. Die Option entspricht dem Namen der temporären Datenbank: Arbeitstabellen werden, falls angegeben, in diese Datenbank geschrieben. Beispiel: 'tempdb.dbo' (Beachten Sie, dass der Name mit einem Punkt enden muss). <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server">Mehr dazu</a> <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcTimeZone</span> <br /> </td> 
   <td> Zeitzone der Instanz des Adobe Campaigns. Siehe <a href="../../installation/using/time-zone-management.md#configuration" target="_blank">Konfiguration</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseNChar</span> <br /> </td> 
   <td> Sind die Zeichenfolgenfelder der Datenbank mit NChar definiert?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseTimeStampWithTZ</span> <br /> </td> 
   <td> Speichern die "datetime"-Felder der Datenbank Zeitzoneninformationen?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkDatabaseId</span> <br /> </td> 
   <td> ID der Datenbank. Beginnt mit 'u' für Unicode DataBase.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkInstancePrefix</span> <br /> </td> 
   <td> Präfix hinzugefügt, um interne Namen automatisch generiert zu werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkQuery_Schema_LineCount</span> <br /> </td> 
   <td> Maximale Anzahl der von einer Abfrage von xtk:schema und xtk:srcSchema zurückgegebenen Ergebnisse.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSequence_AutoGeneration</span> <br /> </td> 
   <td> Alle benutzerdefinierten Schema, die nach dieser Zeit mit autopk="true" und ohne das Attribut "pkSequence" erstellt wurden, erhalten eine automatisch generierte Sequenz "auto_ 
    &lt;schemanamespace&gt; 
     &lt;schemaname&gt;
       _seq. 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NlMigration_KeepFolderStructure</span> <br /> </td> 
   <td> Während der Migration wird die Baumstruktur automatisch auf der Grundlage der neuen Versionsstandards neu organisiert.<br /> Mit dieser Option können Sie die automatische Migration der Navigationsstruktur deaktivieren. Wenn Sie es verwenden, müssen Sie nach der Migration veraltete Ordner löschen, die neuen Ordner hinzufügen und alle erforderlichen Prüfungen ausführen.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">Datentyp:</span> Integer</p> </li> 
     <li> <p> <span class="uicontrol">Wert (Text)</span> : 1 </p> </li> 
    </ul> Diese Option sollte nur verwendet werden, wenn die vordefinierte Navigationsstruktur zu vielen Änderungen unterzogen wurde.<br /> Weiterführende Informationen hierzu finden Sie in <a href="../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure">diesem Abschnitt</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatCoalesce</span> <br /> </td> 
   <td> Letztes Verarbeitungsdatum der <span class="uicontrol">NmsEmailErrorStat</span>-Tabellenbereinigung.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PostUpgradeLastError</span> <br /> </td> 
   <td> Informationen zum Fehler, der nach der Aktualisierung aufgetreten ist, entsprechend der folgenden Syntax:<br /> <strong>{Build number}:{mode: pre/post/...}:{The 'lessThan'/'moreOrEquelThan' where error occur + sub-step}</strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkCleanup_NoStats</span> <br /> </td> 
   <td> Geben Sie den Wert "1"ein, damit die Aktualisierung der Statistiken nicht über den Bereinigungsarbeitsablauf durchgeführt wird.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Integration {#integration}

<table> 
 <thead> 
  <tr> 
   <th> Optionsname </th> 
   <th> Beschreibung  </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">AEMResourceTypeFilter</span> <br /> </td> 
   <td> Arten von AEM Ressourcen, die in Adobe Campaign verwendet werden können. Werte müssen durch Kommas getrennt werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">nmsPipeline_config</span> <br /> </td> 
   <td> Hiermit können Sie Experience Cloud-Auslöser konfigurieren. Der Datentyp ist "langer Text"und muss im JSON-Format vorliegen. Siehe <a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">So verwenden Sie Experience Cloud-Auslöser mit Adobe Campaign Classic</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;&gt;_&lt;&gt;</span> <br /> </td> 
   <td> Diese Option wird verwendet, wenn Daten von einem Drittanbietersystem über einen CRM-Connector importiert werden. Wenn Sie diese Option aktivieren, können Sie nur Objekte erfassen, die seit dem letzten Import geändert wurden. Diese Option muss manuell erstellt und wie folgt ausgefüllt werden: 
    <ul> 
     <li> <p> <span class="uicontrol">Interner Name</span> : LASTIMPORT_&lt;&gt;_&lt;&gt;</p> </li> 
     <li> <p> <span class="uicontrol">Wert (Feld)</span> : Datum des letzten Imports im Format JJJJ/MM/TT HH:mm:ss. </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_EdgeServer</span> <br /> </td> 
   <td> Adobe Target-Server, der für die Integration verwendet wird. Diese Option ist bereits standardmäßig ausgewählt. Dieser Wert entspricht dem Adobe Target-Domänenserver, gefolgt vom Wert /m2. Beispiel: tt.omtrdc.net/m2.<br /> Siehe <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">diesen Abschnitt</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_TenantName</span> <br /> </td> 
   <td> Name der Adobe Target-Organisation. Dieser Wert entspricht dem Adobe-Target-Client-Namen.<br /> Siehe <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">diesen Abschnitt</a>.<br /> </td> 
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
   <td> <span class="uicontrol">WdbcCapability_Teradata</span> <br /> </td> 
   <td> Optionen für Teradata-Connector.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapability_Hive</span> <br /> </td> 
   <td> Ausblenden von Connector-Optionen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Angebote {#offers}

<table> 
 <thead> 
  <tr> 
   <th> Optionsname </th> 
   <th> Beschreibung  </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsCoupons_MaxPerTransac</span> <br /> </td> 
   <td> Anzahl der Coupons, die pro SQL-Transaktion aktualisiert werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchControl_</span> <br /> </td> 
   <td> '+ [Schema des Vorschlags] + "_" + extAccountSource.@executeInstanceId + [Schema des Projekts] + "_" + vars.executeInstanceIdFilter<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchExec_</span> <br /> </td> 
   <td> '+ [ Schema des Vorschlags] + "_" + extAccountSource.@executeInstanceId + "_" + extAccountTarget.@executeInstanceId<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_SynchWorkflowIds</span> <br /> </td> 
   <td> Verfolgung des Synchronisierungs-Workflows.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_UseDaemon</span> <br /> </td> 
   <td> Aktivieren/deaktivieren Sie die asynchrone Propositionserstellung ("0" deaktivieren, "1" aktivieren).<br /> </td> 
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
   <th> Beschreibung  </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsExecutionInstanceId</span> <br /> </td> 
   <td> Ausführungsinstanz-ID.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_CustomerId</span> <br /> </td> 
   <td> Kunden-ID, die beim Senden des Rechnungsberichts verwendet wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_IntranetURL</span> <br /> </td> 
   <td> Basis-URL des internen Webservers.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LastPostUpgrade</span> <br /> </td> 
   <td> Erstellen Sie die Nummer der AC-Instanz vor der letzten Aktualisierung.<br /> </td> 
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
   <th> Beschreibung  </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Available</span> <br /> </td> 
   <td> Option zur Aktivierung der Verfolgung.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ClickFormel</span> <br /> </td> 
   <td> Verfolgtes URL-Berechnungsskript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ExtAccount</span> <br /> </td> 
   <td> Hiermit können Sie das Externe Konto des Tracking-Servers definieren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Instance</span> <br /> </td> 
   <td> Hiermit können Sie den Instanznamen auf dem Tracking-Server definieren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_LastConsolidation</span> <br /> </td> 
   <td> Letztes Mal wurden die Verfolgungsinformationen mit neuen Daten konsolidiert.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_OpenFormel</span> <br /> </td> 
   <td> Öffnen Sie das URL-Berechnungsskript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Password</span> <br /> </td> 
   <td> Kennwort für den Tracking-Server<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Pointer</span> <br /> </td> 
   <td> Der Zeiger verfolgt die zuletzt verarbeiteten Ereignis mit ihren IDs und ihrem Datum.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_SecureServerUrl</span> <br /> </td> 
   <td> Sichere URL des Frontalverfolgungsservers.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrl</span> <br /> </td> 
   <td> URL des Frontalverfolgungsservers.<br /> </td> 
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
   <td> <span class="uicontrol">NmsTracking_WebFormel</span> <br /> </td> 
   <td> Script zur Berechnung der Webtrackingtags.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingDelivery</span> <br /> </td> 
   <td> Name des virtuellen Versands, der für das Web-Tracking-Management entwickelt wurde.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingMode</span> <br /> </td> 
   <td> Hiermit können Sie den Web-Verfolgungsmodus definieren.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Datenschutz {#privacy}

<table> 
 <thead> 
  <tr> 
   <th> Optionsname </th> 
   <th> Beschreibung  </th> 
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
   <td> <span class="uicontrol">Privacy_Request_PurgeDelay</span> <br /> </td> 
   <td> Wartezeit zwischen Anfrageerstellung in Warteschlange und Löschung der Anfragedaten<br /> </td> 
  </tr> 
 </tbody> 
</table>

## LDAP {#ldap}

<table> 
 <thead> 
  <tr> 
   <th> Optionsname </th> 
   <th> Beschreibung  </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkLDAP_Active</span> <br /> </td> 
   <td> Aktivieren Sie den LDAP-Server, um Benutzer zu authentifizieren und Benutzern Autorisierungen bereitzustellen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppLogin</span> <br /> </td> 
   <td> Anmelden, um den Server für verschiedene Suchen zu kontaktieren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppPassword</span> <br /> </td> 
   <td> Verschlüsseltes Kennwort für die Anwendungsanmeldung.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AutoOperator</span> <br /> </td> 
   <td> Automatische Erstellung von Operatoren und Rechten in Adobe Campaign aktivieren.<br /> </td> 
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
   <td> <span class="uicontrol">XtkLDAP_Mechanism</span> <br /> </td> 
   <td> Authentifizierungstyp für den LDAP-Server (plain, md5, lds, ntlm, dpa).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLDAP_Rights</span> <br /> </td> 
   <td> Aktivieren Sie die Synchronisierung von Autorisierungen und Gruppen vom LDAP-Ordner zu Spezifische Berechtigungen im Adobe Campaign.<br /> </td> 
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
   <td> Filter nach Benutzerautorisierungen suchen.<br /> </td> 
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
   <td> <span class="uicontrol">XtkLDAP_Server</span> <br /> </td> 
   <td> LDAP-Serveradresse (es ist möglich, einen Anschluss anzugeben, indem Sie ":"als Trennzeichen angeben).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Webformulare {#web-forms}

<table> 
 <thead> 
  <tr> 
   <th> Optionsname </th> 
   <th> Beschreibung  </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkUseScrollBar</span> <br /> </td> 
   <td> Der auf 1 eingestellte Wert ermöglicht den Zusatz der Bildlaufleiste zu den Detailformularen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Instance</span> <br /> </td> 
   <td> Instanz, die für die Ungültigmachung eines Webformulars im Modus 'Andere Server(s)' verwendet wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Password</span> <br /> </td> 
   <td> Kennwort der Instanz, die für die Ungültigmachung eines Webformulars im Modus 'andere Server(s)' verwendet werden soll.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersMode</span> <br /> </td> 
   <td> Option, die es ermöglicht, den Annullierungsmodus für Webformulare anzugeben: standardmäßig lokal, via Trackingserver, wenn die Option 'Tracking' angegeben ist, und über eine benutzerdefinierte Liste, wenn die Option 'Andere(r) Server' angegeben ist.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersURLs</span> <br /> </td> 
   <td> Personalisierte Adressserver-Liste, die für die Ungültigmachung eines Webformulars kontaktiert werden sollen ("andere Server(s)'-Modus).<br /> </td> 
  </tr> 
 </tbody> 
</table>


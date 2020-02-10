---
title: Ursachen von fehlgeschlagenen Sendungen
seo-title: Ursachen von fehlgeschlagenen Sendungen
description: Ursachen von fehlgeschlagenen Sendungen
seo-description: null
page-status-flag: never-activated
uuid: 03a91f84-77fe-40a9-8be9-a6a35a873ae1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
discoiquuid: 78b58a7a-b387-4d5d-80d5-01c06f83d759
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 211556bbf023731ffeab2e90692410a852ab3555

---


# Ursachen von fehlgeschlagenen Sendungen{#understanding-delivery-failures}

## Über fehlgeschlagene Sendungen {#about-delivery-failures}

Wenn eine Nachricht (E-Mail, SMS, Push-Benachrichtigung) nicht an ein Profil gesendet werden kann, sendet der Remote-Server automatisch eine Fehlermeldung, die von der Adobe Campaign-Plattform abgerufen und qualifiziert wird, um zu bestimmen, ob die E-Mail-Adresse oder Telefonnummer in Quarantäne gestellt werden soll. See [Bounce mail management](#bounce-mail-management).

>[!NOTE]
>
>E-Mail-Fehlermeldungen (auch &quot;Bounces&quot; genannt) werden vom inMail-Prozess qualifiziert. SMS-Fehlermeldungen (auch &quot;SR&quot; für &quot;Status Report&quot; genannt) werden vom MTA-Prozess qualifiziert.

Nachdem eine Nachricht gesendet wurde, können Sie im Versandlogs-Tab den Versandstatus für jedes Profil sowie den damit verbundenen Fehlertyp und die Ursache einsehen.

Mitteilungen können während der Versandvorbereitung auch ausgeschlossen werden, wenn eine Adresse unter Quarantäne gestellt oder ein Profil auf die Blacklist gesetzt wurde. Ausgeschlossene Mitteilungen werden im Versand-Dashboard aufgeführt.

**Verwandte Themen:**

* [Protokolle und Versandverlauf](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history)
* [Status Fehlgeschlagen](../../delivery/using/monitoring-a-delivery.md#failed-status)
* [Typen und Ursachen für fehlgeschlagene Sendungen](#delivery-failure-types-and-reasons)

## Typen und Ursachen für fehlgeschlagene Sendungen {#delivery-failure-types-and-reasons}

Es gibt drei Arten von Fehlern, wenn eine Nachricht fehlschlägt. Jeder Fehlertyp bestimmt, ob eine Adresse an Quarantäne gesendet wird. Weitere Informationen finden Sie unter [Bedingungen für das Senden einer Adresse an die Quarantäne](../../delivery/using/understanding-quarantine-management.md#conditions-for-sending-an-address-to-quarantine)

* **Hard**: Dieser Fehlertyp tritt bei einer ungültigen Adresse auf. Fehlermeldung, die explizit eine ungültige Adresse anzeigt, beispielsweise &quot;Benutzer unbekannt&quot;.
* **Soft**: Fehler, der eventuell nur vorübergehend auftritt oder der nicht qualifiziert werden konnte, beispielsweise &quot;Ungültige Domain&quot;, &quot;Postfach voll&quot;.
* **Ignoriert**: Vorübergehender Fehler, beispielsweise &quot;Out of office&quot; oder technischer Fehler bei Absendern vom Typ &quot;Postmaster&quot;.

Mögliche Ursachen für fehlgeschlagene Sendungen sind:

<table> 
 <tbody> 
  <tr> 
   <td> Bezeichnung des Fehlers </td> 
   <td> Fehlertyp </td> 
   <td> Technischer Wert </td> 
   <td> Description </td> 
  </tr> 
  <tr> 
   <td> Konto deaktiviert </td> 
   <td> Softbounce / Hardbounce </td> 
   <td> 4 </td> 
   <td> Das mit der Adresse verknüpfte Konto ist nicht mehr aktiv. Wenn das Konto längere Zeit nicht abgefragt wird, kann es vom Internetanbieter geschlossen werden, was den Versand an diese Empfängeradresse unmöglich macht. Wenn das Konto vorübergehend wegen einer sechsmonatigen Inaktivität deaktiviert ist und wieder aktiviert werden kann, wird der Status "Mit Fehlern" zugewiesen und der Zustellversuch wird wiederholt, bis der Fehlerzähler 5 erreicht hat. Wenn aus den Fehlern hervorgeht, dass das Konto permanent deaktiviert ist, wird es sofort unter Quarantäne gestellt.<br /> </td> 
  </tr> 
  <tr> 
   <td> Adresse in Quarantäne </td> 
   <td> Hard </td> 
   <td> 9 </td> 
   <td> Die Adresse wurde unter Quarantäne gestellt.<br /> </td> 
  </tr> 
  <tr> 
   <td> Adresse nicht angegeben </td> 
   <td> Hard </td> 
   <td> 7 </td> 
   <td> Empfängeradresse fehlt.<br /> </td> 
  </tr> 
  <tr> 
   <td> Adresse schlechter Qualität </td> 
   <td> Ignoriert </td> 
   <td> 14 </td> 
   <td> Qualitätsindex der Postanschrift ist zu niedrig.<br /> </td> 
  </tr> 
  <tr> 
   <td> Adresse auf der Blacklist </td> 
   <td> Hard </td> 
   <td> 8 </td> 
   <td> Zum Versandzeitpunkt war die Adresse auf der Blacklist. Dieser Status wird zum Import von Daten aus externen Listen und Systemen in die Quarantäne-Liste verwendet.<br /> </td> 
  </tr> 
  <tr> 
   <td> Kontrollgruppenadresse </td> 
   <td> Ignoriert </td> 
   <td> 127 </td> 
   <td> Empfängeradresse ist Teil der Kontrollgruppe.<br /> </td> 
  </tr> 
  <tr> 
   <td> Doppelt </td> 
   <td> Ignoriert </td> 
   <td> 10 </td> 
   <td> Empfängeradresse bereits im Versand enthalten.<br /> </td> 
  </tr> 
  <tr> 
   <td> Fehler ignoriert </td> 
   <td> Kein Fehler </td> 
   <td> 25 </td> 
   <td> Die Adresse ist auf der Whitelist. Der Fehler wird deshalb ignoriert und eine E-Mail wird gesendet.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ausgeschlossen nach Schlichtung </td> 
   <td> Ignoriert </td> 
   <td> 12 </td> 
   <td> Der Empfänger wurde durch Anwendung einer Typologieregel vom Typ 'Schlichtung' ausgeschlossen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Von einer SQL-Regel ausgeschlossen </td> 
   <td> Ignoriert </td> 
   <td> 11 </td> 
   <td> Der Empfänger wurde durch Anwendung einer Typologieregel vom Typ 'SQL' ausgeschlossen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ungültige Domain </td> 
   <td> Soft </td> 
   <td> 2 </td> 
   <td> Die Domain der E-Mail-Adresse ist fehlerhaft oder existiert nicht mehr. An dieses Profil werden wiederholte Zustellversuche unternommen, bis die Fehleranzahl 5 erreicht. Danach wird der Datensatz in den Quarantänestatus versetzt und die Zustellversuche werden eingestellt.<br /> </td> 
  </tr> 
  <tr> 
   <td> Postfach voll </td> 
   <td> Soft </td> 
   <td> 5 </td> 
   <td> Das Postfach des Benutzers ist voll und kann keine Nachrichten mehr aufnehmen. An dieses Profil werden wiederholte Zustellversuche unternommen, bis die Fehleranzahl 5 erreicht. Danach wird der Datensatz in den Quarantänestatus versetzt und die Zustellversuche werden eingestellt.<br /> Dieser Fehlertyp wird von einem Bereinigungsprozess verwaltet. Die Adresse erhält nach 30 Tagen wieder einen gültigen Status.<br /> Achtung: Damit die Adresse automatisch aus der Quarantäne genommen werden kann, muss der technische Workflow Datenbankbereinigung (Cleanup) gestartet sein.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nicht angemeldet </td> 
   <td> Ignoriert </td> 
   <td> 6 </td> 
   <td> Das Mobiltelefon des Empfängers war beim Versand der Nachricht ausgeschaltet oder verfügte über keinen Netzempfang.<br /> </td> 
  </tr> 
  <tr> 
   <td> Unbestimmt </td> 
   <td> Unbestimmt </td> 
   <td> 0 </td> 
   <td> Die Qualifikation der Adresse ist noch nicht abgeschlossen, da die Fehler noch nicht inkrementiert wurden. Dieser Fehlertyp tritt auf, wenn der Server eine bis dahin unbekannte Fehlernachricht sendet. Hierbei kann es sich um einen einmaligen Fehler handeln. Sollte er sich jedoch wiederholen, wird der Fehlerzähler erhöht, was die zuständigen Mitarbeiter auf das Problem aufmerksam macht. Diese können dann die Nachricht analysieren und den Fehler über den Knoten <span class="uicontrol">Administration</span> / <span class="uicontrol">Kampagnen</span> / <span class="uicontrol">Unzustellbarkeitsverwaltung</span> qualifizieren.<br /> </td> 
  </tr> 
  <tr> 
   <td> Kommt nicht für die Angebote infrage </td> 
   <td> Ignoriert </td> 
   <td> 16 </td> 
   <td> Der Empfänger kommt für die Angebote im Versand nicht infrage.<br /> </td> 
  </tr> 
  <tr> 
   <td> Zurückgewiesen </td> 
   <td> Softbounce / Hardbounce </td> 
   <td> 20 </td> 
   <td> Die Adresse wurde wegen eines Sicherheits-Feedbacks unter Quarantäne gestellt, da die Nachricht als Spam gemeldet wurde. Je nach Fehler wird der Zustellversuch wiederholt, bis der Fehlerzähler 5 erreicht hat, oder die Adresse wird sofort unter Quarantäne gestellt.<br /> </td> 
  </tr> 
  <tr> 
   <td> Größe der Zielgruppe begrenzt </td> 
   <td> Ignoriert </td> 
   <td> 17 </td> 
   <td> Maximale Versandgröße wurde für den Empfänger erreicht.<br /> </td> 
  </tr> 
  <tr> 
   <td> Adresse nicht qualifiziert </td> 
   <td> Ignoriert </td> 
   <td> 15 </td> 
   <td> Postanschrift wurde nicht qualifiziert<br /> </td> 
  </tr> 
  <tr> 
   <td> Unerreichbar </td> 
   <td> Softbounce / Hardbounce </td> 
   <td> 3 </td> 
   <td> In der Verteilungskette der Nachricht ist ein Fehler aufgetreten. Hierbei kann es sich um einen Vorfall beim SMTP-Server oder eine zeitweilig unerreichbare Domain handeln etc. Je nach Fehler wird der Zustellversuch wiederholt, bis der Fehlerzähler 5 erreicht hat, oder die Adresse wird sofort unter Quarantäne gestellt.<br /> </td> 
  </tr> 
  <tr> 
   <td> Unbekannter Nutzer </td> 
   <td> Hard </td> 
   <td> 1 </td> 
   <td> Die Adresse existiert nicht. An dieses Profil werden keine weiteren Zustellversuche unternommen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Weitere Zustellversuche nach einem vorübergehend fehlgeschlagenen Versand {#retries-after-a-delivery-temporary-failure}

Wenn die Zustellung vorübergehend wegen eines **Softbounce** oder eines **ignorierten Fehlers** fehlschlägt, werden während der Versandlaufzeit erneute Zustellversuche vorgenommen.

>[!NOTE]
>
>Temporarily undelivered messages can only be related to a **Soft** or **Ignored** error, but not a **Hard** error (see [Delivery failure types and reasons](#delivery-failure-types-and-reasons)).

Gehen Sie zur Änderung der Versandlaufzeit in die erweiterten Eigenschaften des Versands oder seiner Vorlage und geben Sie im entsprechenden Feld die gewünschte Dauer ein. Weiterführende Informationen zu den erweiterten Versandeigenschaften finden Sie in [diesem Abschnitt](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period).

Standardmäßig sind innerhalb der ersten 24 Stunden fünf Versuche im Abstand von mindestens einer Stunde vorgesehen, an den vier folgenden Tagen je ein Versuch. Die Anzahl weiterer Versuche kann global geändert werden (kontaktieren Sie Ihren technischen Administrator von Adobe) oder für jeden Versand oder jede Versandvorlage (siehe [diesen Abschnitt](../../delivery/using/steps-sending-the-delivery.md#configuring-retries)).

## Synchrone und asynchrone Fehler {#synchronous-and-asynchronous-errors}

Ein Versand kann sofort fehlschlagen (synchroner Fehler) oder zu einem späteren Zeitpunkt nach dem Versand (asynchroner Fehler).

* Synchroner Fehler: Wenn der vom Adobe Campaign-Bereitstellungsserver kontaktierte Remote-E-Mail-Server sofort eine Fehlermeldung zurückgegeben hat, darf die Bereitstellung nicht an den Profilserver gesendet werden. Adobe Campaign qualifiziert jeden Fehler, um festzustellen, ob die betreffenden E-Mail-Adressen in Quarantäne gestellt werden sollen. Siehe [Bounce-Message-Qualifizierung](#bounce-mail-qualification).
* Asynchroner Fehler: Eine Bounce Message oder ein SR wird vom Remote-Server verzögert zurückgesendet. Diese E-Mail wird an ein spezifisches Postfach weitergeleitet, das automatisch von der Anwendung abgefragt wird, um die fehlerhaften Nachrichten zu erfassen. Asynchrone Fehler können bis zu einer Woche nach dem Versand auftreten.

   >[!NOTE]
   >
   >Die Konfiguration der Bounce-Adresse wird in [diesem Abschnitt](../../installation/using/deploying-an-instance.md#managing-bounced-emails) beschrieben.

   Der Feedback-Loop (Beschwerdenverwaltung) folgt dem gleichen Prinzip wie die Bounce Messages. Es besteht die Möglichkeit, in Adobe Campaign E-Mail-Regeln zu konfigurieren, um zukünftige Sendungen zu verhindern, wenn ein Empfänger eine E-Mail als unerwünscht kennzeichnet. Nachrichten an Empfänger, die bereits eine E-Mail als Spam gekennzeichnet haben, werden automatisch an ein speziell hierfür angelegtes Postfach weitergeleitet. Die Adressen dieser Empfänger werden auf die Blacklist gesetzt, auch wenn sie nicht auf den Abmelde-Link geklickt haben. Diese Blacklist-Adressen werden demzufolge in der Quarantänetabelle (**NmsAddress**) und nicht in der Empfängertabelle (**NmsRecipient**) gespeichert.

   >[!NOTE]
   >
   >Der Feedback Loop (Beschwerdenverwaltung) wird im Abschnitt [Verwaltung der Zustellbarkeit](../../delivery/using/about-deliverability.md) erläutert.

## Bounce-Message-Verwaltung {#bounce-mail-management}

Die Adobe Campaign-Plattform bietet mit der Bounce-Message-Funktion die Möglichkeit, Zustellprobleme zu verwalten. Wenn eine E-Mail nicht zugestellt werden kann, sendet der Remote-E-Mail-Server automatisch eine Fehlermeldung, eine s. g. Bounce Message, an die speziell für diesen Zweck konfigurierte technische E-Mail-Adresse. Adobe Campaign ruft diese Fehlermeldungen ab und qualifiziert sie mithilfe des inMail-Prozesses, um die Liste der E-Mail-Verwaltungsregeln anzureichern.

### Bounce-Message-Qualifizierung {#bounce-mail-qualification}

Wenn eine E-Mail nicht zugestellt werden kann, empfängt der Adobe Campaign-Versandserver eine Fehlermeldung vom Remote-Mail- oder -DNS-Server. Jeder Fehlermeldung wird ein Fehlertyp und -grund zugeordnet.

Diese Liste ist über den **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** Knoten verfügbar. Es enthält alle Regeln, die Adobe Campaign verwendet, um Auslieferungsfehler zu qualifizieren. Es ist nicht erschöpfend, wird regelmäßig von Adobe Campaign aktualisiert und kann auch vom Benutzer verwaltet werden.

![](assets/tech_quarant_rules_qualif.png)

* Die vom Remote-Server beim ersten Auftreten dieses Fehlertyps zurückgegebene Meldung wird in der **[!UICONTROL First text]** Spalte der **[!UICONTROL Delivery log qualification]** Tabelle angezeigt. Wenn diese Spalte nicht angezeigt wird, klicken Sie auf die **[!UICONTROL Configure list]** Schaltfläche am rechten Ende der Liste, um sie auszuwählen.

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign filtert diese Nachricht, um den variablen Inhalt (wie IDs, Daten, E-Mail-Adressen, Telefonnummern usw.) zu löschen. und zeigt das gefilterte Ergebnis in der **[!UICONTROL Text]** Spalte an. Die Variablen werden durch ersetzt **`#xxx#`**, mit Ausnahme der Adressen, die durch ersetzt werden **`*`**.

Dadurch können alle Fehlschläge desselben Typs zusammengefasst werden und mehrfache Einträge für ähnliche Fehler in die Versandlogqualifizierungs-Tabelle werden vermieden.

>[!NOTE]
>
>Das **[!UICONTROL Number of occurrences]** Feld zeigt die Anzahl der Vorkommen der Nachricht in der Liste an. Er ist auf 100 000 Vorkommen begrenzt. Sie können das Feld bearbeiten, um es beispielsweise zurückzusetzen.

Folgende Qualifikationsstatus von Bounce Messages treten auf:

* **[!UICONTROL To qualify]** : die Absprungmail konnte nicht qualifiziert werden. Die Qualifikation muss dem Bereitstellungs-Team zugewiesen werden, um eine effiziente Bereitstellung der Plattform zu gewährleisten. Solange sie nicht qualifiziert ist, wird die Absprungmail nicht dazu verwendet, die Liste der E-Mail-Verwaltungsregeln zu bereichern.
* **[!UICONTROL Keep]** : die Absprungmail wurde qualifiziert und wird vom Arbeitsablauf **Aktualisieren auf Zustellbarkeit** verwendet, um mit den vorhandenen E-Mail-Verwaltungsregeln verglichen und die Liste erweitert zu werden.
* **[!UICONTROL Ignore]** : die Absprungmail wurde qualifiziert, wird aber nicht vom Arbeitsablauf **Aktualisieren für Zustellbarkeit** verwendet. Es wird nicht an Client-Instanzen gesendet.

![](assets/deliverability_qualif_status.png)

>[!NOTE]
>
>Bei gehosteten oder hybriden Installationen werden die Absprungqualifikationen in der **[!UICONTROL Delivery log qualification]** Tabelle nicht mehr verwendet, wenn Sie auf die erweiterte MTA aktualisiert haben. Die erweiterte MTA bestimmt den Absprungtyp und die Qualifikation und sendet diese Informationen an Kampagne zurück.
>
>Weitere Informationen zur erweiterten MTA-Datei für Adobe Campaign finden Sie in diesem [Dokument](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html).

### E-Mail-Verwaltungsregeln {#email-management-rules}

Der Zugriff auf E-Mail-Regeln erfolgt über den **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** Knoten. E-Mail-Verwaltungsregeln werden im unteren Bereich des Fensters angezeigt.

In den Regeln sind die von Remote-Servern potenziell zurückgegebenen Strings enthalten, die die Qualifizierung der Fehler in **Hardbounce**, **Softbounce** oder **Ignoriert** erlauben.

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>Die Standardparameter der Plattform werden im Softwareverteilungs-Assistenten konfiguriert. Lesen Sie diesbezüglich auch [diesen Abschnitt](../../installation/using/deploying-an-instance.md).

Folgende Regeln sind in der Standardkonfiguration vorgesehen:

* **Eingehende E-Mails**

   Wenn die Zustellung einer E-Mail fehlschlägt, gibt der Remote-Server eine Fehlermeldung an die in den Plattform-Parametern angegebene Bounce-Adresse zurück. Adobe Campaign vergleicht den Inhalt jeder Bounce-E-Mail mit den in der Regelliste verzeichneten Strings und ordnet einen der drei Fehlertypen zu.

   Der Benutzer kann eigene Regeln erstellen.

   >[!CAUTION]
   >
   >Beim Import eines Packages und bei der Aktualisierung von Daten durch den **Zustellbarkeit**-Workflow werden benutzerdefinierte E-Mail-Regeln überschrieben.

* **Domain-Verwaltung**

   Domain-Verwaltungsregeln ermöglichen die Regulierung des Volumens der ausgehenden E-Mails nach Domains. Sie analysieren die Bounce Messages und blockieren falls nötig den Versand. Der Adobe-Campaign-E-Mail-Server wendet zunächst die spezifischen Domain-Regeln an und im Anschluss jene, die den Normalfall repräsentieren (durch * gekennzeichnet). Die Regeln für Hotmail und MSN sind standardmäßig in Adobe Campaign enthalten.

   Klicken Sie auf das **[!UICONTROL Detail]**-Symbol, um auf die Regelkonfiguration zuzugreifen.

   ![](assets/tech_quarant_domain_rules_02.png)

   Um eigene Domain-Verwaltungsregeln zu erstellen, sind die Angabe einer Schwelle und die Auswahl gewisser SMTP-Parameter erforderlich. Die **Schwelle** entspricht einem Prozentsatz an Fehlern, der bei Überschreiten den Versand an die betroffene Domain unterbricht.

   So wird beispielsweise der Versand drei Stunden lang unterbrochen, wenn bei einem Volumen von mindestens 300 Nachrichten die Fehlerquote 90% erreicht.

   Die **SMTP-Parameter** agieren wie die im Falle einer Blockierungsregel angewendeten Filter.

   * Sie haben die Möglichkeit, gewisse Authentifizierungsnormen und Verschlüsselungsschlüssel zu aktivieren, um den Domain-Namen zu prüfen: **Sender ID**, **DomainKeys**, **DKIM**, **S/MIME**.
   * **SMTP-Relais**: Zur Konfiguration der IP-Adresse und des Relais-Server-Ports für eine bestimmte Domain.

* **MX-Verwaltung**

   Weiterführende Informationen zur MX-Verwaltung erfahren Sie in [diesem Abschnitt](../../installation/using/email-deliverability.md#mx-configuration).

   >[!NOTE]
   >
   >Bei gehosteten oder hybriden Installationen werden die Regeln für den **[!UICONTROL MX management]** Bereitstellungsdurchsatz nicht mehr verwendet, wenn Sie auf die erweiterte MTA aktualisiert haben. Die erweiterte MTA verwendet ihre eigenen MX-Regeln, die es ermöglichen, Ihren Durchsatz nach Domäne basierend auf Ihrem eigenen historischen E-Mail-Ruf und dem Echtzeit-Feedback, das von den Domänen stammt, von denen Sie E-Mails senden, anzupassen.
   >
   >Weitere Informationen zur erweiterten MTA-Datei für Adobe Campaign finden Sie in diesem [Dokument](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html).

>[!CAUTION]
>
>* Nach Änderungen in der Konfiguration muss der Versandserver (MTA) neu gestartet werden.
>* Neuerstellung und Änderungen von Verwaltungsregeln sollten erfahrenen Benutzern vorbehalten bleiben.


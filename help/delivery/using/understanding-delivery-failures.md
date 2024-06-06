---
product: campaign
title: Ursachen für das Fehlschlagen von Sendungen
description: Erfahren Sie, wie Sie die Ursachen von fehlgeschlagenen Sendungen ermitteln können.
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Monitoring, Deliverability
role: User
exl-id: 86c7169a-2c71-4c43-8a1a-f39871b29856
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: ht
source-wordcount: '2618'
ht-degree: 100%

---

# Ursachen für das Fehlschlagen von Sendungen{#understanding-delivery-failures}

## Über fehlgeschlagene Sendungen {#about-delivery-failures}

Wenn einem Profil eine Nachricht (E-Mail, SMS, Push-Benachrichtigung) nicht zugestellt werden kann, sendet der Remote-Server automatisch eine Fehlermeldung, die von der Adobe Campaign-Plattform erfasst und qualifiziert wird, um festzustellen, ob die E-Mail-Adresse oder Telefonnummer unter Quarantäne gestellt werden soll. Siehe [Bounce-Message-Verwaltung](#bounce-mail-management).

>[!NOTE]
>
>**E-Mail**-Fehlermeldungen (oder &quot;Bounces&quot;) werden vom erweiterten MTA (synchrone Bounces) oder InMail-Prozess (asynchrone Bounces) qualifiziert.
>
>**SMS**-Fehlermeldungen (auch &quot;SR&quot; für &quot;Status Report&quot; genannt) werden vom MTA-Prozess qualifiziert.

Nachdem eine Nachricht gesendet wurde, können Sie im Versandlogs-Tab den Versandstatus für jedes Profil sowie den damit verbundenen Fehlertyp und die Ursache einsehen.

Nachrichten können während der Versandvorbereitung auch ausgeschlossen werden, wenn eine Adresse unter Quarantäne gestellt oder ein Profil auf die Blockierungsliste gesetzt wurde. Ausgeschlossene Nachrichten werden im Versand-Dashboard aufgeführt.

**Verwandte Themen:**

* [Protokolle und Versandverlauf](delivery-dashboard.md#delivery-logs-and-history)
* [Status &quot;Fehlgeschlagen&quot;](delivery-performances.md#failed-status)
* [Typen von fehlgeschlagenen Sendungen und deren Ursachen](#delivery-failure-types-and-reasons)

## Typen von fehlgeschlagenen Sendungen und deren Ursachen              {#delivery-failure-types-and-reasons}

Es gibt drei Typen von fehlgeschlagenen Sendungen. Vom jeweiligen Fehlertyp hängt es ab, ob eine Adresse in Quarantäne kommt. Weitere Informationen hierzu finden Sie unter [Ursachen für Quarantänen](understanding-quarantine-management.md#conditions-for-sending-an-address-to-quarantine)

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
   <td> Beschreibung </td> 
  </tr> 
  <tr> 
   <td> Konto deaktiviert </td> 
   <td> Softbounce / Hardbounce </td> 
   <td> 4 </td> 
   <td> Das mit der Adresse verknüpfte Konto ist nicht mehr aktiv. Wenn der Internetanbieter (IAP, Internet Access Provider) eine längere Inaktivität feststellt, kann er das Konto der Person schließen. Sendungen an die Adresse dieser Person sind dann nicht mehr möglich. Wenn das Konto aufgrund einer sechsmonatigen Inaktivität vorübergehend deaktiviert wurde und noch aktiviert werden kann, wird der Status „Mit Fehlern“ zugewiesen und der Zustellversuch wird wiederholt, bis der Fehlerzähler 5 erreicht. Wenn die Fehlermeldung besagt, dass das Konto permanent deaktiviert ist, wird es sofort unter Quarantäne gestellt.<br /> </td> 
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
   <td> Adresse, die auf die Blockierungsliste gesetzt wurde </td> 
   <td> Hard </td> 
   <td> 8 </td> 
   <td> Die Adresse wurde zum Zeitpunkt des Versands der Blockierungsliste hinzugefügt. Dieser Status wird zum Importieren von Daten aus externen Listen und externen Systemen in die Quarantäneliste von Adobe Campaign verwendet.<br /> </td> 
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
   <td> Ignoriert </td> 
   <td> 25 </td> 
   <td> Die Adresse befindet sich auf der Zulassungsliste. Der Fehler wird daher ignoriert und eine E-Mail gesendet.<br /> </td> 
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
   <td> Die Domain der E-Mail-Adresse ist fehlerhaft oder existiert nicht mehr. An dieses Profil werden wiederholte Zustellversuche unternommen, bis die Fehleranzahl 5 erreicht. Danach wird der Eintrag in den Quarantänestatus versetzt und die Zustellversuche werden eingestellt.<br /> </td> 
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
   <td> Die Adresse befindet sich in der Qualifizierungsphase, da Fehler noch nicht inkrementiert worden sind. Dieser Fehlertyp tritt auf, wenn der Server eine bis dahin unbekannte Fehlermeldung sendet: Hierbei kann es sich um einen einmaligen Fehler handeln. Sollte er sich jedoch wiederholen, wird der Fehlerzähler erhöht, was die zuständigen technischen Mitarbeitenden auf das Problem aufmerksam macht. Sie können dann über den Knoten <span class="uicontrol">Administration</span> / <span class="uicontrol">Campaign Management</span> / <span class="uicontrol">Unzustellbarkeitsverwaltung</span> in der Baumstruktur eine Nachrichtenanalyse durchführen und diesen Fehler qualifizieren.<br /> </td> 
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
   <td> In der Versandkette der Nachricht ist ein Fehler aufgetreten. Es könnte sich um einen Vorfall auf dem SMTP-Relais, eine zeitweilig unerreichbare Domain o. a. handeln. Je nach Fehler wird der Zustellversuch wiederholt, bis der Fehlerzähler 5 erreicht hat, oder die Adresse wird sofort unter Quarantäne gestellt.<br /> </td> 
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
>Vorübergehend unzustellbare Nachrichten können als Ursache nur einen **Softbounce** oder einen **ignorierten** Fehler haben, nicht aber einen **Hardbounce** (siehe [Typen und Ursachen für fehlgeschlagene Sendungen](#delivery-failure-types-and-reasons)).

>[!IMPORTANT]
>
>Bei gehosteten oder hybriden Installationen werden die Einstellungen für den erneuten Versuch im Versand nicht mehr von Campaign verwendet, wenn Sie auf den [Enhanced MTA](sending-with-enhanced-mta.md) aktualisiert haben. Weitere Zustellversuche aufgrund von Softbounces sowie die Zeitdauer zwischen ihnen werden durch den Enhanced MTA bestimmt, basierend auf Typ und Prioritätsstufe der Bounce-Antworten, die von der E-Mail-Domain der Nachricht zurückgegeben werden.

Gehen Sie bei On-Premise-Installationen und gehosteten/hybriden Installationen mit dem bestehenden Campaign-MTA zum Ändern der Versandlaufzeit zu den erweiterten Parametern des Versands oder der Versandvorlage und geben Sie die gewünschte Laufzeit in das entsprechende Feld ein. Weitere Informationen finden Sie unter [Gültigkeitszeitraum bestimmen](steps-sending-the-delivery.md#defining-validity-period).

Standardmäßig sind innerhalb der ersten 24 Stunden fünf Versuche im Abstand von mindestens einer Stunde vorgesehen, an den vier folgenden Tagen je ein Versuch. Die Anzahl weiterer Versuche kann global (kontaktieren Sie Ihren technischen Adobe-Administrator) oder einzeln für jeden Versand oder jede Versandvorlage geändert werden. Siehe [Konfigurieren von weiteren Zustellversuchen](steps-sending-the-delivery.md#configuring-retries).

## Synchrone und asynchrone Fehler     {#synchronous-and-asynchronous-errors}

Ein Versand kann sofort fehlschlagen (synchroner Fehler) oder zu einem späteren Zeitpunkt nach dem Versand (asynchroner Fehler).

* Synchroner Fehler: Der vom Adobe Campaign-Server angesprochene Remote-Mail-Server hat unmittelbar eine Fehlermeldung zurückgegeben, die Nachricht darf nicht an den Server des Profils gesendet werden. Adobe Campaign qualifiziert jeden Fehlschlag, um zu bestimmen, ob die betroffenen E-Mail-Adressen in Quarantäne kommen oder nicht. Siehe [Bounce-Message-Qualifizierung](#bounce-mail-qualification).
* Asynchroner Fehler: Eine Bounce Message oder ein SR wird vom Remote-Server verzögert zurückgesendet. Diese E-Mail wird an ein spezifisches Postfach weitergeleitet, das automatisch von der Anwendung abgefragt wird, um die fehlerhaften Nachrichten zu erfassen. Asynchrone Fehler können bis zu einer Woche nach dem Versand auftreten.

  >[!NOTE]
  >
  >Die Konfiguration der Bounce-Adresse wird in [diesem Abschnitt](../../installation/using/deploying-an-instance.md#managing-bounced-emails) beschrieben.

  Die [Feedback-Schleife](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=de#feedback-loops) funktioniert wie eine Bounce-E-Mail. Wenn ein Benutzer eine E-Mail als Spam einstuft, können Sie E-Mail-Regeln in Adobe Campaign so konfigurieren, dass alle Sendungen für diesen Benutzer blockiert werden. Nachrichten, die an Benutzer gesendet werden, die eine E-Mail als Spam eingestuft haben, werden automatisch an einen speziell dafür erstellten E-Mail-Eingang weitergeleitet. Die Adressen dieser Benutzer befinden sich auf der Blockierungsliste, obwohl sie nicht auf den Abmelde-Link geklickt haben. Adressen befinden sich in der Blockierungsliste der Quarantänetabelle (**NmsAddress**) und nicht der Empfängertabelle (**NmsRecipient**).

  >[!NOTE]
  >
  >Der Feedback Loop (Beschwerdenverwaltung) wird im Abschnitt [Verwaltung der Zustellbarkeit](about-deliverability.md) erläutert.

## Bounce-Message-Verwaltung {#bounce-mail-management}

Mit der Adobe Campaign-Plattform können Sie E-Mail-Versandfehler über die Bounce Message-Funktion verwalten.

Wenn eine E-Mail nicht an einen Empfänger gesendet werden kann, sendet der Remote-Messaging-Server automatisch eine Fehlermeldung (Bounce-Mail) an einen dafür vorgesehenen technischen Posteingang.

Bei On-Premise-Installationen und gehosteten/hybriden Installationen, die den bestehenden Campaign-MTA verwenden, werden Fehlermeldungen von der Adobe Campaign-Plattform gesammelt und durch den InMail-Prozess qualifiziert, um die Liste der E-Mail-Verwaltungsregeln zu erweitern.

>[!IMPORTANT]
>
>Bei gehosteten oder hybriden Installationen werden die meisten E-Mail-Verwaltungsregeln nicht mehr verwendet, wenn Sie ein Upgrade auf den [Enhanced MTA](sending-with-enhanced-mta.md) durchgeführt haben. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](#email-management-rules).

### Bounce-Message-Qualifizierung             {#bounce-mail-qualification}

>[!IMPORTANT]
>
>Bei gehosteten oder hybriden Installationen, wenn Sie ein Upgrade auf den [Enhanced MTA](sending-with-enhanced-mta.md) durchgeführt haben:
>
>* Die Bounce-Qualifizierungen in der Tabelle **[!UICONTROL Versandlogqualifizierung]** werden nicht mehr für Fehlernachrichten bei synchronen Sendungen verwendet. **** Der Enhanced MTA bestimmt den Bounce-Typ und die Qualifizierung und sendet diese Informationen an Campaign zurück.
>
>* **Asynchrone** Bounces werden weiterhin vom InMail-Prozess über die Regeln für **[!UICONTROL Eingehende E-Mails]** qualifiziert. Weiterführende Informationen dazu finden Sie im Abschnitt [E-Mail-Verwaltungsregeln](#email-management-rules).
>
>* Bei Instanzen, die den Enhanced MTA **ohne Webhooks** verwenden, dienen die Regeln für **[!UICONTROL eingehende E-Mails]** auch zur Verarbeitung der synchronen Bounce-E-Mails, die aus dem Enhanced MTA kommen, wobei dieselbe E-Mail-Adresse wie bei asynchronen Bounce-E-Mails genutzt wird.

Bei On-Premise-Installationen und gehosteten/hybriden Installationen, die den bestehenden Campaign-MTA verwenden, erhält der Adobe Campaign-Versand-Server eine Fehlermeldung vom Messaging-Server oder dem Remote-DNS-Server, wenn der Versand einer E-Mail fehlschlägt. Die Liste der Fehler besteht aus Zeichenfolgen, die in der vom Remote-Server zurückgegebenen Nachricht enthalten sind. Jeder Fehlermeldung sind Fehlertypen und Gründe zugeordnet.

Auf die entsprechende Liste kann im Knoten **[!UICONTROL Administration > Kampagnenverwaltung > Unzustellbarkeitsverwaltung > Versandlogqualifizierung]** zugegriffen werden. Sie enthält alle von Adobe Campaign für die Qualifizierung von fehlgeschlagenen Sendungen verwendeten Regeln. Die Liste erhebt keinen Anspruch auf Vollständigkeit. Sie wird jedoch regelmäßig von Adobe Campaign angereichert und kann auch vom Benutzer ergänzt werden.

![](assets/tech_quarant_rules_qualif.png)

Die vom Remote-Server beim ersten Auftreten dieses Fehlertyps zurückgegebene Nachricht wird in der Spalte **[!UICONTROL Erster Text]** der Tabelle **[!UICONTROL Versandlogqualifizierung]** angezeigt. Wird diese Spalte nicht angezeigt, wählen Sie in der Liste rechts unten die Schaltfläche **[!UICONTROL Liste konfigurieren]**, um die Spalte auszuwählen.

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign filtert diese Nachricht, um den variablen Inhalt zu löschen (wie IDs, Daten, E-Mail-Adressen, Telefonnummern usw.) und zeigt das gefilterte Ergebnis in der Spalte **[!UICONTROL Text]**. Die Variablen werden durch **`#xxx#`** ersetzt, mit Ausnahme der Adressen, die durch ersetzt **`*`** werden.

Dadurch können alle Fehlschläge desselben Typs zusammengefasst werden und mehrfache Einträge für ähnliche Fehler in die Versandlogqualifizierungs-Tabelle werden vermieden.

>[!NOTE]
>
>Im Feld **[!UICONTROL Trefferanzahl]** wird die Anzahl der Vorkommnisse der Nachricht in der Liste angezeigt. Die maximale Anzahl ist 100 000. Sie können das Feld bearbeiten, wenn Sie es beispielsweise zurücksetzen möchten.

Folgende Qualifikationsstatus von Bounce Messages treten auf:

* **[!UICONTROL Zu qualifizieren]**: die Bounce Message konnte nicht qualifiziert werden. Die Qualifizierung muss dem Zustellbarkeits-Team zugewiesen werden, um eine effiziente Zustellbarkeit der Plattform zu gewährleisten. Solange sie nicht qualifiziert ist, wird die Bounce-Nachricht nicht zur Anreicherung der Liste der E-Mail-Verwaltungsregeln herangezogen.
* **[!UICONTROL Beibehalten]**: Die Bounce Message wurde qualifiziert und wird vom Workflow **Zustellbarkeit** verwendet, um mit den existierenden E-Mail-Regeln verglichen zu werden und eventuell die Liste zu ergänzen.
* **[!UICONTROL Ignorieren]**: Die Bounce Message wird vom Campaign MTA ignoriert, was bedeutet, dass diese Bounce Message nie dazu führt, dass die Adresse des Empfängers unter Quarantäne gestellt wird. Sie wird vom Workflow **Zustellbarkeit** nicht verwendet und auch nicht an Client-Instanzen gesendet.

![](assets/deliverability_qualif_status.png)

>[!NOTE]
>
>Bei Ausfall eines ISP werden über Campaign gesendete E-Mails fälschlicherweise als Bounces gekennzeichnet. Um dies zu korrigieren, müssen Sie die Bounce-Qualifizierung aktualisieren. Weitere Informationen hierzu finden Sie auf [dieser Seite](update-bounce-qualification.md).

### E-Mail-Verwaltungsregeln {#email-management-rules}

>[!IMPORTANT]
>
>Bei gehosteten oder hybriden Installationen werden die meisten E-Mail-Verwaltungsregeln nicht mehr verwendet, wenn Sie ein Upgrade auf den [Enhanced MTA](sending-with-enhanced-mta.md) durchgeführt haben. Weitere Informationen finden Sie in den folgenden Abschnitten.

Auf E-Mail-Regeln kann im Knoten **[!UICONTROL Administration > Kampagnen > Unzustellbarkeitsverwaltung]** zugegriffen werden. Im unteren Teil des Fensters können Sie die Details der Regeln sehen.

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>Die Standardparameter der Plattform werden im Bereitstellungsassistenten konfiguriert. Weiterführende Informationen erhalten Sie in [diesem Abschnitt](../../installation/using/deploying-an-instance.md).

Folgende Regeln sind in der Standardkonfiguration vorgesehen.

>[!IMPORTANT]
>
>* Nach Änderungen in der Konfiguration muss der Versandserver (MTA) neu gestartet werden.
>* Neuerstellung und Änderungen von Verwaltungsregeln sollten erfahrenen Benutzern vorbehalten bleiben.

#### Eingehende E-Mails {#inbound-email}

<!--
STATEMENT ONLY TRUE with Momentum and EFS+:
For hosted or hybrid installations, if you have upgraded to the [Enhanced MTA](sending-with-enhanced-mta.md), and if your instance has **Webhooks** functionality, the **[!UICONTROL Inbound email]** rules are no longer used for synchronous delivery failure error messages. For more on this, see [this section](#bounce-mail-qualification).

For on-premise installations and hosted/hybrid installations using the legacy Campaign MTA, these rules contain the list of character strings which can be returned by remote servers and which let you qualify the error (**Hard**, **Soft** or **Ignored**).-->

Die **[!UICONTROL Regeln für eingehende E-Mails]** enthalten eine Liste von Zeichenfolgen, die von Remote-Servern zurückgegeben werden können und die es Ihnen ermöglichen, den Fehler zu qualifizieren (**Hardbounce**, **Softbounce** oder **Ignoriert**).

Wenn die Zustellung einer E-Mail fehlschlägt, sendet der Remote-Server eine Bounce-Nachricht an die in den [Plattform-Parametern](../../installation/using/deploying-an-instance.md) angegebene Adresse. Adobe Campaign vergleicht den Inhalt jeder Bounce Message mit den in der Regelliste verzeichneten Strings und ordnet ihn einem der drei [Fehlertypen](#delivery-failure-types-and-reasons) zu.

>[!NOTE]
>
>Der Benutzer kann eigene Regeln erstellen. Beim Import eines Packages und bei der Aktualisierung von Daten durch den Workflow **Zustellbarkeit** werden benutzerdefinierte E-Mail-Regeln überschrieben.

Weiterführende Informationen zur Bounce-Message-Qualifizierung finden Sie in [diesem Abschnitt](#bounce-mail-qualification).

#### Domain-Verwaltung {#domain-management}

>[!IMPORTANT]
>
>Bei gehosteten oder hybriden Installationen werden die Regeln für die **[!UICONTROL Domain-Verwaltung]** nicht mehr verwendet, wenn Sie ein Upgrade auf den [Enhanced MTA](sending-with-enhanced-mta.md) durchgeführt haben. Die Signierung zur E-Mail-Authentifizierung mit **DKIM (DomainKeys Identified Mail)** erfolgt durch den Enhanced MTA für alle Nachrichten mit allen Domains. Die Signierung erfolgt nicht mit **Sender ID**, **DomainKeys** oder **S/MIME**, es sei denn, auf der Ebene des Enhanced MTA ist etwas anderes angegeben.

Bei On-Premise-Installationen und gehosteten/hybriden Installationen, die den bestehenden Campaign-MTA verwenden, wendet der Adobe Campaign Messaging-Server eine einzige Regel zur **Domain-Verwaltung** auf alle Domains an.

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* Sie haben die Möglichkeit, gewisse Authentifizierungsnormen und Verschlüsselungsschlüssel zu aktivieren, um den Domain-Namen zu prüfen: **Sender ID**, **DomainKeys**, **DKIM**, **S/MIME**.
* Mit den **SMTP-Relais**-Parametern können Sie die IP-Adresse und den Relais-Server-Port für eine bestimmte Domain konfigurieren. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#smtp-relay).

Wenn Ihre Nachrichten in Outlook mit **[!UICONTROL im Namen von]** in der Absenderadresse angezeigt werden, vergewissern Sie sich, dass Sie Ihre E-Mails nicht mit der **Sender ID** signieren, dem veralteten proprietären Authentifizierungsstandard für E-Mails von Microsoft. Wenn die Option **[!UICONTROL Sender ID]** aktiviert ist, deaktivieren Sie das entsprechende Feld und wenden Sie sich an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Ihre Zustellbarkeit wird nicht beeinträchtigt.

#### MX-Verwaltung {#mx-management}

>[!IMPORTANT]
>
>Bei gehosteten oder hybriden Installationen werden die Versanddurchsatzregeln der **[!UICONTROL MX-Verwaltung]** nicht mehr verwendet, wenn Sie auf den [Enhanced MTA](sending-with-enhanced-mta.md) aktualisiert haben. Der Enhanced MTA verwendet eigene MX-Regeln. Mit diesen kann Ihr Durchsatz für jede Domain anhand Ihrer historischen E-Mail-Reputation und des Echtzeit-Feedbacks von den Domains angepasst werden, über die Sie E-Mails senden.

Bei On-Premise-Installationen und gehosteten/hybriden Installationen, die den bestehenden Campaign-MTA verwenden:

* MX-Verwaltungsregeln ermöglichen die Regulierung des Volumens der ausgehenden E-Mails nach Domains. Sie analysieren die Bounce Messages und blockieren falls nötig den Versand.

* Der Adobe-Campaign-E-Mail-Server wendet zunächst die spezifischen Domain-Regeln an und anschließend die Regeln für den allgemeinen Fall, der in der Liste der Regeln mit einem Sternchen (*) gekennzeichnet ist.

* Um eigene MX-Verwaltungsregeln zu erstellen, sind die Angabe einer Schwelle und die Auswahl gewisser SMTP-Parameter erforderlich. Die **Schwelle** entspricht einem Prozentsatz an Fehlern, der bei Überschreiten den Versand an die betroffene Domain unterbricht. So wird beispielsweise der Versand drei Stunden lang unterbrochen, wenn bei einem Volumen von mindestens 300 Nachrichten die Fehlerquote 90 % erreicht.

Weiterführende Informationen zur MX-Verwaltung erhalten Sie in [diesem Abschnitt](../../installation/using/email-deliverability.md#mx-configuration).

---
title: Technische Empfehlungen zur Verbesserung der Zustellbarkeit mit Adobe Campaign Classic
description: Discover-Techniken, -Konfigurationen und -Tools, mit denen Sie Ihre Auslieferungsrate mit Adobe Campaign Classic verbessern können.
page-status-flag: never-activated
uuid: 71be1087-e5ff-4a7a-85ca-36803839e72f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: fc95538b-b54d-44ec-81aa-f51b62982699
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3a4eb0cf49b81d720fa3925d48cd250e0c3fde32

---


# Technische Empfehlungen{#technical-recommendations}

Im Folgenden werden verschiedene Techniken, Konfigurationen und Tools aufgelistet, mit denen Sie Ihre Bereitstellungsrate verbessern können.

## Konfiguration {#configuration}

### Reverse DNS {#reverse-dns}

: Adobe Campaign prüft, ob für eine IP-Adresse ein Reverse-DNS angegeben ist und ob dieses wirklich auf die IP-Adresse zurückverweist.

Bei der Netzwerkkonfiguration ist es wichtig sicherzustellen, dass für jede der für ausgehende Nachrichten bestimmten IP-Adressen ein korrektes Reverse-DNS angegeben ist. Für eine bestimmte IP-Adresse existiert also ein Reverse-DNS Datensatz (PTR-Datensatz) mit einem passenden DNS (Datensatz), das auf die ursprüngliche IP zurückverweist.

Die Domänenauswahl für ein umgekehrtes DNS hat Auswirkungen auf bestimmte ISPs. Insbesondere akzeptiert AOL nur Feedback-Schleifen mit einer Adresse in derselben Domäne wie das umgekehrte DNS (siehe [Feedback-Schleife](#feedback-loop)).

A tool is available to verify the configuration of a domain: [https://mxtoolbox.com/SuperTool.aspx](https://mxtoolbox.com/SuperTool.aspx).

### MX-Regeln {#mx-rules}

MX-Regeln (Mail eXchanger) dienen zur Verwaltung der Kommunikation zwischen einem Sender- und einem Empfangs-Server.

Genauer gesagt, werden sie dazu verwendet, die Geschwindigkeit zu steuern, mit der die Kampagne MTA (Message Transfer Agent) E-Mails an jede einzelne E-Mail-Domäne oder jeden ISP sendet (z.B. hotmail.com, comcast.net). Diese Regeln basieren meist auf den von den ISPs veröffentlichten Beschränkungen (z. B. nicht mehr als 20 Nachrichten pro SMTP-Verbindung).

For more on MX management, refer to the [dedicated section](../../installation/using/email-deliverability.md#mx-configuration).

### TLS {#tls}

: TLS (Transport Layer Security) ist ein Verschlüsselungsprotokoll zur Sicherung der Verbindung zwischen zwei E-Mail-Servern. Damit wird sichergestellt, dass die E-Mail nur vom beabsichtigten Empfänger gelesen werden kann.

## Authentifizierung {#authentication}

### SPF {#spf}

: SPF (Sender Policy Framework) ist ein Standard für die E-Mail-Authentifizierung, mit dem der Inhaber einer Domain angeben kann, welche E-Mail-Server E-Mails im Namen dieser Domain senden dürfen. Bei diesem Standard wird die Domain in der Kopfzeile &quot;Return-Path&quot; der E-Mail (auch als &quot;Envelope From&quot;-Adresse bezeichnet) genutzt.

A tool is available to verify an SPF record: [https://www.kitterman.com/spf/validate.html](https://www.kitterman.com/spf/validate.html)

Der SPF ist eine Technik, mit der Sie in gewissem Umfang sicherstellen können, dass der in einer E-Mail verwendete Domänenname nicht gefälscht wird. Wenn eine Nachricht von einer Domäne empfangen wird, wird der DNS-Server der Domäne abgefragt. Die Antwort ist ein kurzer Datensatz (der SPF-Datensatz), der angibt, welche Server für das Senden von E-Mails aus dieser Domäne autorisiert sind. Wenn wir davon ausgehen, dass nur der Eigentümer der Domäne die Mittel hat, um diesen Datensatz zu ändern, können wir bedenken, dass diese Technik nicht erlaubt, die Absenderadresse gefälscht werden, zumindest nicht der Teil von der rechten Seite des &quot;@&quot;.

In der endgültigen [RFC 4408-Spezifikation](https://www.rfc-editor.org/info/rfc4408)werden zwei Elemente der Nachricht verwendet, um die Domäne zu bestimmen, die als Absender gilt: Die Domäne, die vom SMTP-Befehl &quot;HELO&quot; (oder &quot;EHLO&quot;) angegeben wird, und die Domäne, die von der Adresse des Headers &quot;Return-Path&quot;(oder &quot;MAIL VON&quot;) angegeben wird, die auch die Absprungadresse ist. Unterschiedliche Überlegungen ermöglichen es, nur einen dieser Werte zu berücksichtigen. Es wird empfohlen sicherzustellen, dass beide Quellen dieselbe Domäne angeben.

Durch die Überprüfung des SPF ist eine Evaluierung der Gültigkeit der Absender-Domain gewährleistet.

* **Keine**: Es konnte keine Bewertung durchgeführt werden,
* **Neutral**: Die abgefragte Domäne ermöglicht keine Auswertung,
* **Übergeben**: Die Domäne gilt als authentisch,
* **Fehler**: Die Domäne wird gefälscht und die Meldung sollte zurückgewiesen werden —
* **SoftFail**: Die Domain ist wahrscheinlich gefälscht, aber die Nachricht sollte nicht allein aufgrund dieses Ergebnisses abgelehnt werden,
* **TempError**: Ein temporärer Fehler stoppte die Auswertung. Die Nachricht kann abgelehnt werden.
* **PermError**: Die SPF-Aufzeichnungen der Domäne sind ungültig.

Bitte beachten Sie, dass es bis zu 48 Stunden in Anspruch nehmen kann, bis in der Umgebung von DNS-Servern gemachte Einträge berücksichtigt werden. Die Dauer hängt davon ab, mit welcher Häufigkeit die DNS-Caches der Empfangs-Server aktualisiert werden.

### DKIM {#dkim}

Die DKIM-Authentifizierung (DomainKeys Identified Mail) ist eine Nachfolgerin von SPF und verwendet eine Public-Key-Kryptographie, mit der der Empfänger-E-Mail-Server überprüfen kann, ob eine Nachricht tatsächlich von der Person oder Entität gesendet wurde, von der sie versendet wurde, und ob der Inhalt der Nachricht zwischen dem Zeitpunkt der ursprünglichen Versendung (und dem &quot;Signieren&quot; von DKIM) und dem Zeitpunkt des Eingangs geändert wurde. Bei diesem Standard wird in der Regel die Domain im &quot;Von&quot;- oder &quot;Absender&quot;-Header genutzt. Um die Sicherheitsstufe des DKIM zu gewährleisten, wird die Verschlüsselungsgröße 1024b empfohlen. Niedrigere DKIM-Schlüssel werden von den meisten Zugangsanbietern nicht als gültig angesehen.

DKIM geht auf eine Kombination der Authentifizierungsprinzipien DomainKeys von Yahoo! und Identified Internet Mail von Cisco zurück und dient der Prüfung der Authentizität von Absender-Domains sowie der Sicherstellung der Integrität von Nachrichten.

DKIM hat sozusagen die **DomainKeys**-Authentifizierung ersetzt.

>[!NOTE]
>
>Bei gehosteten oder hybriden Installationen erfolgt die DKIM-E-Mail-Authentifizierungssignatur durch die erweiterte MTA, wenn Sie auf die erweiterte MTA aktualisiert haben. Das DKIM-Signieren durch die native Kampagnen-MTA wird im Rahmen des erweiterten MTA-Upgrades in der **[!UICONTROL Domain management]** Tabelle deaktiviert.
>
>Weitere Informationen zur erweiterten MTA-Datei für Adobe Campaign finden Sie in diesem [Dokument](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html).

Für die Verwendung von DKIM müssen folgende Voraussetzungen gegeben sein:

* **Sicherheit**: Verschlüsselung ist ein Hauptelement von DKIM, und seit Frühjahr 2013 gewährleistet die in den Best Practices empfohlene Verschlüsselungsgröße von 1024b dessen hohen Sicherheitsstandard. DKIM-Schlüssel mit einer unter diesem Wert liegenden Größe werden von den meisten Zugangsanbietern als ungültig angesehen.
* **Reputation**: Die Reputation basiert auf dem IP und/oder der Domain, dabei bildet jedoch auch der weniger transparente DKIM-Selektor ein zu berücksichtigendes Schlüsselelement. Die Auswahl eines Selektors ist wichtig: Vermeiden Sie es, den &quot;default&quot;-Selektor beizubehalten, da er von jedem verwendet werden könnte und deshalb über eine schwache Reputation verfügt. Für die Kommunikationsarten **Retention vs. Akquise** und Authentifizierung ist die Implementierung von jeweils unterschiedlichen Selektoren erforderlich.
* **Deklaration von Optionen in Adobe Campaign**: Der private DKIM-Schlüssel basiert in Adobe Campaign auf einem DKIM-Selektor und einer Domain. Aktuell ist es nicht möglich, mehrere private Schlüssel für dieselbe Domain/Sub-Domain mit unterschiedlichen Selektoren zu erstellen. In der Plattform oder der E-Mail ist es nicht möglich zu definieren, welcher Selektor für die Authentifizierung verwendet werden soll. Die Plattform wählt alternativ einen der privaten Schlüssel aus, wodurch die Authentifizierung ein hohes Fehlschlagrisiko birgt.

>[!NOTE]
>
>* Sollten Sie DomainKeys für Ihre Adobe-Campaign-Instanz konfiguriert haben, müssen Sie lediglich **dkim** in den Regeln zur Verwaltung von Domains auswählen. Gehen Sie andernfalls bei der Konfiguration (privater/öffentlicher Schlüssel) genauso vor wie bei DomainKeys.
>* Es ist nicht notwendig, sowohl DomainKeys als auch DKIM für dieselbe Domain zu aktivieren, da es sich bei DKIM um eine verbesserte Version von DomainKeys handelt.
>* Folgende Domains validieren aktuell DKIM: AOL, Gmail.


### DMARC {#dmarc}

DMARC (Domain-based Message Authentication, Reporting and Conformance) ist die neueste Art der E-Mail-Authentifizierung. Bei der Entscheidung, ob eine E-Mail weitergeleitet wird oder fehlschlägt, kommt sowohl SPF- als auch DKIM-Authentifizierung zum Einsatz. DMARC ist in zwei wichtigen Bereichen einzigartig und extrem leistungsstark:

* Conformance (Konformität) – ermöglicht dem Absender, ISPs anzuweisen, was mit einer Nachricht passieren soll, die nicht authentifiziert werden kann (z. B. nicht akzeptieren).
* Reporting (Berichterstellung) – liefert dem Absender einen detaillierten Bericht mit allen Nachrichten, die die DMARC-Authentifizierung nicht bestanden haben, sowie die jeweils verwendete &quot;Von&quot;-Domain und IP-Adresse. Damit können Unternehmen legitime E-Mails erkennen, die nicht authentifiziert werden konnten und &quot;repariert&quot; werden müssen (z. B. durch Hinzufügen von IP-Adressen zu ihrem SPF-Datensatz), sowie die Quellen und das Vorkommen von Phishing-Versuchen auf ihren E-Mail-Domains identifizieren.

DMARC can leverage the reports generated by [250ok](https://250ok.com/).

<!--#### Configuring the application {#configuring-the-application}

To define the domain used for the HELO command, edit the instance's configuration file (conf/config-instance.xml) and define a "localDomain" attribute as follows:

```
<serverConf>
  <shared>
    <dnsConfig localDomain="mydomain.net"/>
  </shared>
</serverConf>
```

The MAIL FROM domain is the domain used in technical bounce messages. This address is defined in the deployment wizard or via the NmsEmail_DefaultErrorAddr option.

#### DNS configuration {#dns-configuration}

An SPF record can currently be defined on a DNS server as a TXT type record (code 16) or an SPF type record (code 99). An SPF record takes the form of a character string. For example:

```
v=spf1 ip4:12.34.56.78/32 ip4:12.34.56.79/32 ~all
```

defines the 2 IP addresses 12.34.56.78 and 12.34.56.79 as authorized to send emails for the domain. **~all** means that any other address should be interpreted as a SoftFail.

Recommendations for defining an SPF record:

* Add **~all** (SoftFail) or **-all** (Fail) at the end to reject all servers other than those defined. Without this, servers will be able to forge this domain (with a Neutral evaluation).
* Do not add **ptr** (openspf.org recommends against this as costly and unreliable).-->

## Feedback Loops {#feedback-loop}

Ein Feedback Loop funktioniert nach dem Prinzip, dass auf ISP-Niveau eine bestimmte E-Mail-Adresse für eine Reihe von für den E-Mail-Versand verwendeten IP-Adressen deklariert wird. An diese E-Mail-Adresse senden die ISPs ähnlich wie für Bounce Messages diejenigen Nachrichten, die von Empfängern als Spam erklärt werden. Die Plattform sollte so konfiguriert werden, dass zukünftige Sendungen an Benutzer, die sich beschwert haben, blockiert werden. Dabei ist es wichtig, dass diese Benutzer nicht länger kontaktiert werden, selbst wenn sie nicht den offiziellen Opt-out-Link verwendet haben. Diese Beschwerden bilden die Basis dafür, dass ISPs IP-Adressen auf die Blacklist setzen. Je nach ISP wird eine IP-Adresse bei einer ungefähren Beschwerderate von 1 % auf die Blacklist gesetzt.

A standard is currently being drawn up to define the format of feedback loop messages: the [Abuse Feedback Reporting Format (ARF)](https://tools.ietf.org/html/rfc6650).

Zur Implementierung eines Feedback Loops für eine Instanz sind folgende Elemente erforderlich:

* ein für die Instanz bestimmtes Postfach, bei dem es sich um das Bounce-Postfach handeln kann,
* für die Instanz bestimmte IP-Versandadressen.

Die Implementierung einer einfachen Feedback-Schleife in Adobe Campaign verwendet die Funktion der Absprungmeldung. Das Feedback-Schleifenfeld wird als Absprung-Mailbox verwendet und es wird eine Regel zur Erkennung dieser Nachrichten definiert. Die E-Mail-Adressen der Empfänger, die die Nachricht als Spam gemeldet haben, werden der Quarantäneliste hinzugefügt.

* Erstellen oder ändern Sie eine Absprung-Mail-Regel, **Feedback_loop**, in **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** mit dem Grund **Weigerung** und dem Typ **Hard**.
* If a mailbox has been defined specially for the feedback loop, define the parameters to access it by creating a new external Bounce Mails account in **[!UICONTROL Administration > Platform > External accounts]**.

Der Mechanismus zur Verarbeitung von Beschwerdebenachrichtigungen ist sofort funktionstüchtig. Um die korrekte Funktionsweise der Regel sicherzustellen, können Sie die Konten zeitweise deaktivieren, damit sie diese Nachrichten nicht abrufen. Sie können die Inhalte des Feedback-Loop-Postfachs dann manuell überprüfen. Führen Sie auf dem Server die folgenden Befehle aus:

```
nlserver stop inMail@instance,
nlserver inMail -instance:instance -verbose.
```

Sollten Sie gezwungen sein, eine einzige Feedback-Loop-Adresse für mehrere Instanzen zu verwenden, müssen Sie:

* die empfangenen Nachrichten auf so vielen Postfächern replizieren wie Instanzen vorhanden sind,
* dafür sorgen, dass jedes Postfach von einer einzigen Instanz abgerufen wird,
* Konfigurieren Sie die Instanzen so, dass sie nur die Meldungen verarbeiten, die sie betreffen: Die Instanzinformationen sind im Message-ID-Header der von Adobe Campaign gesendeten Nachrichten enthalten und befinden sich daher auch in den Feedback-Schleifenmeldungen. Geben Sie einfach den Parameter **checkInstanceName** in der Konfigurationsdatei der Instanz an (standardmäßig wird die Instanz nicht überprüft, was dazu führen kann, dass bestimmte Adressen falsch isoliert werden):

   ```
   <serverConf>
     <inMail checkInstanceName="true"/>
   </serverConf>
   ```

Der Zustellbarkeitsdienst in Adobe Campaign sorgt für die Verwaltung Ihrer Anmeldung für Feedback-Loop-Dienste für die folgenden ISPs: AOL, BlueTie, Comcast, Cox, EarthLink, FastMail, Gmail, Hotmail, HostedEmail, Libero, Mail.ru, MailTrust, OpenSRS, QQ, RoadRunner, Synacor, Telenor, Terra, UnitedOnline, USA, XS4ALL, Yahoo, Yandex, Zoho.

## List-Unsubscribe {#list-unsubscribe}

### Über List-Unsubscribe {#about-list-unsubscribe}

Zur optimalen Verwaltung der Zustellbarkeit ist das Hinzufügen eines SMTP-Headers namens **List-Unsubscribe** zwingend erforderlich.

Dieser Header kann alternativ zum Symbol &quot;Als Spam melden&quot; verwendet werden. Er wird innerhalb der E-Mail in Form eines Abmelde-Links angezeigt.

Die Verwendung dieser Funktion hilft dabei, Ihren Ruf zu schützen, und das Feedback wird wie eine Abmeldung ausgeführt.

>[!NOTE]
>
>Diese Funktion ist ab Build 6831 verfügbar.

Zur Verwendung von List-Unsubscribe ist die Eingabe einer Befehlszeile notwendig, die in etwa so aussieht:

```
List-Unsubscribe: mailto: client@newsletter.example.com?subject=unsubscribe?body=unsubscribe
```

>[!IMPORTANT]
>
>Das oben stehende Beispiel basiert auf der Empfängertabelle. Sollte die Datenbankimplementierung über eine andere Tabelle erfolgen, stellen Sie bitte sicher, dass Sie die Befehlszeile mit den korrekten Informationen umformulieren.

Die folgende Befehlszeile kann zum Zweck der Erstellung eines dynamischen **List-Unsubscribe** verwendet werden:

```
List-Unsubscribe: mailto: %=errorAddress%?subject=unsubscribe%=message.mimeMessageId%
```

Gmail, Outlook.com und Microsoft Outlook unterstützen diese Methode und eine Abmelde-Schaltfläche ist direkt in ihrer Benutzeroberfläche verfügbar. Durch diese Technik werden Beschwerderaten gesenkt.

![](assets/s_tn_del_msn_unsubscribe_list.png)

![](assets/s_tn_del_gmail_unsubscribe_list.png)

Die Implementierung von **List-Unsubscribe** erfolgt durch:

* das direkte Hinzufügen der Befehlszeile in der Versandvorlage (siehe [diesen Abschnitt](#adding-a-command-line-in-a-delivery-template)) oder
* das Erstellen einer Typologieregel (siehe [diesen Abschnitt](#creating-a-typology-rule)).

### Hinzufügen einer Befehlszeile in einer Versandvorlage {#adding-a-command-line-in-a-delivery-template}

Die Befehlszeile muss im Zusatzabschnitt des SMTP-Headers der E-Mail hinzugefügt werden.

Das kann entweder in jeder E-Mail oder in bereits existierenden Versandvorlagen erfolgen. Sie haben außerdem die Möglichkeit, eine neue diese Funktion beinhaltende Versandvorlage zu erstellen.

### Erstellung einer Typologieregel {#creating-a-typology-rule}

Die Regel muss das Script zur Erzeugung der Befehlszeile beinhalten und im E-Mail-Header enthalten sein.

>[!NOTE]
>
>Es wird empfohlen, eine Typologieregel zu erstellen: Die List-Unsubscribe-Funktion wird automatisch zu jeder E-Mail hinzugefügt.

1. List-Unsubscribe: &lt;mailto:unsubscribe@domain.com>

   Durch die Verwendung des **unsubscribe**-Links wird das Standard-E-Mail-Programm des Benutzers geöffnet. Diese Typologieregel muss in einer zur E-Mail-Erstellung verwendeten Typologie hinzugefügt werden.

1. List-Unsubscribe: `<https://domain.com/unsubscribe.jsp>`

   Durch die Verwendung des **unsubscribe**-Links wird der Benutzer zu Ihrem Abmeldeformular weitergeleitet.

   Beispiel:

   ![](assets/s_tn_del_unsubscribe_param.png)

## E-Mail-Optimierung {#email-optimization}

### SMTP {#smtp}

SMTP (Simple Mail Transfer Protocol) ist ein Internetstandard für die E-Mail-Übertragung.

Die SMTP-Fehler, die nicht von einer Regel überprüft werden, werden im Ordner **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Delivery log qualification]** angezeigt. Diese Fehlermeldungen werden standardmäßig als nicht erreichbare weiche Fehler interpretiert. Die häufigsten Fehler müssen identifiziert und eine entsprechende Regel unter **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > hinzugefügt werden, **[!UICONTROL Mail rule sets]** wenn Sie das Feedback von den SMTP-Servern korrekt qualifizieren möchten. Andernfalls führt die Plattform unnötige Wiederholungen durch (bei unbekannten Benutzern) oder platziert bestimmte Empfänger fälschlicherweise nach einer bestimmten Anzahl von Tests in Quarantäne.

### Dedizierte IP-Adressen {#dedicated-ips}

Adobe bietet jedem Kunden für die Anlaufphase eine dedizierte IP-Strategie zum Aufbau der Reputation und zur Optimierung der Zustellbarkeit.

## IP-Zertifizierung {#ip-certification}

Die IP-Zertifizierung ist ein Programm für die Whitelist- und Versendetechnik, mit dem sichergestellt wird, dass E-Mails ohne Blockierung durch Antispam-Filter oder andere E-Mail-Sperrsysteme empfangen werden.

Derzeit bieten zwei Anbieter eine IP-Zertifizierung an: Rückkehrpfad und Allianz der zertifizierten Sender.

Zertifizierte Absender werden E-Mail-Whitelists hinzugefügt, die von globalen Mailbox-Anbietern und E-Mail-Sicherheitsunternehmen verwendet werden. Diese kommerziellen Whitelists basieren auf einem System, das es dem Absender erlaubt, Antispam-Filter ganz zu umgehen oder inkrementelle Punkte zuzuweisen, wenn er in das System eintritt.

Das [Programm zur Zertifizierung](https://www.validity.com/products/returnpath/certification/) des Rückkehrpfads bietet eine Reihe von Vorteilen:

* Eine messbare Steigerung der Posteingangsplatzierung bei Top-Postfachanbietern wie Microsoft, AOL, Yahoo, Gmail, Comcast, Orange, Mail.ru und mehr
* Gute Reputation und Behandlung bei kritischen Filtern wie Cloudmark, SpamAssassin und Cisco Ironport
* Ein Compliance-Team, das rund um die Uhr überwacht, Sicherheitswarnungen bereitstellt und mit Ihnen durch die Lösung von Kompromissen zusammenarbeitet
* Postfach-Anbieterdaten mit detaillierten Informationen zu KPIs, Platzierung und Zertifizierungsleistung
* Vereinfachte und schnellere IP-Erwärmung, einschließlich besserer Ruf und Anerkennung bei der Migration oder beim Erhalt einer neuen IP-Adresse

Die [Zertifizierung der Senderallianz](https://certified-senders.org/certification-process/) bietet unter anderem folgende Vorteile:

* Zertifizierung von Absendern von kommerziellen E-Mails, die hohe Qualitätsstandards erfüllen können
* Verbesserte Auslieferung und Zustellbarkeit von kommerziellen E-Mails zur Erhöhung der Platzierungsrate im Posteingang und zur Reduzierung der Spam-Filterung
* Schutz vor rechtlichen und finanziellen Risiken durch vollständige Einhaltung der gesetzlichen Normen
* Schutz des Ruhestands durch Frühwarnungen des Beschwerdeamts der CSA und tägliche Berichte über Spam-Traps

ISPs können diese Dienste kostenlos nutzen, und die Anzahl der ISPs kann je nach Whitelist variieren.

Da jedoch immer mehr ISPs ihre Anti-Spam-Filter auf Grundlage des Verhaltens jedes Posteingangsbesitzers erstellen, anstatt den Inhalt der Nachricht selbst zu analysieren, kann die Verwendung der IP-Zertifizierung keine Garantie für die Platzierung des Posteingangs oder sogar für die Bereitstellung sein.

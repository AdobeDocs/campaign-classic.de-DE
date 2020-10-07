---
title: Email Deliverability
seo-title: Email Deliverability
description: Email Deliverability
seo-description: null
page-status-flag: never-activated
uuid: 983aec6b-60f6-4c9b-a75a-1693958626c2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 86c18986-1f65-40ff-80dc-1fbff37f406d
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '3047'
ht-degree: 21%

---


# Technische E-Mail-Konfigurationen{#email-deliverability}

## Übersicht {#overview}

Im folgenden Abschnitt erhalten Sie einen Überblick über die Konfiguration, die zur Steuerung der Ausgabe von Adobe Campaign-Instanzen bei der Bereitstellung von E-Mails erforderlich ist.

>[!NOTE]
>
>Einige Konfigurationen können nur von der Adobe für Bereitstellungen ausgeführt werden, die von der Adobe gehostet werden, z. B. für den Zugriff auf die Server- und Instanzkonfigurationsdateien. Weitere Informationen zu den verschiedenen Bereitstellungen finden Sie im Abschnitt [Hosting-Modelle](../../installation/using/hosting-models.md) oder in [diesem Artikel](https://helpx.adobe.com/de/campaign/kb/acc-on-prem-vs-hosted.html).

Weitere Informationen zu den Konzepten und Best Practices im Zusammenhang mit der Lieferbarkeit finden Sie in diesem [Abschnitt](../../delivery/using/about-deliverability.md).

Alle technischen Empfehlungen zum effizienten Versand und Empfangen von E-Mails durch eine Adobe Campaign-Plattform finden Sie in diesem [Abschnitt](../../delivery/using/technical-recommendations.md).

## Grundprinzip {#operating-principle}

Es ist möglich, die Ausgabe einer oder mehrerer Instanzen eines Adobe Campaigns zu steuern, um die Anzahl der gesendeten E-Mails je nach Domäne einzuschränken. Sie können beispielsweise die Ausgabe für **yahoo.com** -Adressen auf 20.000 pro Stunde beschränken und gleichzeitig 100.000 Nachrichten pro Stunde für alle anderen Domänen konfigurieren.

Die Nachrichtenausgabe muss für jede IP-Adresse gesteuert werden, die von den Versand-Servern verwendet wird (**mta**). Mehrere **Metadaten** , die auf mehreren Computern unterteilt sind und zu verschiedenen Adobe Campaign-Instanzen gehören, können dieselbe IP-Adresse für E-Mail-Versand verwenden: Es muss ein Prozess zur Koordinierung der Verwendung dieser IP-Adressen eingerichtet werden.

Das **statusmodul** tut Folgendes: es leitet alle Verbindungsanfragen und Nachrichten für eine Reihe von IP-Adressen an die Mailserver weiter. Der Statistikserver verfolgt die Versand und kann das Senden je nach festgelegten Quoten aktivieren oder deaktivieren.

![](assets/s_ncs_install_mta.png)

* Der Statistikserver (**stat**) ist mit einer Adobe Campaign-Basis verknüpft, um die Konfiguration zu laden.
* Die Versand-Server (**mta**) verwenden eine UDP, um einen Statistikserver zu kontaktieren, der nicht immer zu ihrer eigenen Instanz gehört.

### Versand-Server {#delivery-servers}

Das **mta** -Modul verteilt Nachrichten an seine untergeordneten **mtachild** -Module. Jede **mtachild** erstellt Nachrichten, bevor sie eine Autorisierung vom Statistikserver anfordert und sie sendet.

Zusammenfassend sind folgende Etappen zu durchlaufen:

1. Die **mta** wählt geeignete Nachrichten aus und weist ihnen eine verfügbare **mtachild** zu.
1. Das **Mtachild** lädt alle zum Erstellen der Nachricht erforderlichen Informationen (Inhalt, Personalisierungselemente, Anlagen, Bilder usw.) und leitet die Nachricht an den **E-Mail-Traffic-Shaper** weiter.
1. Sobald der E-Mail-Traffic-Gestalter die Autorisierung des Statistikservers (**SMTP STAT**) erhält, wird die Nachricht an den Empfänger gesendet.

![](assets/s_ncs_install_email_traffic_shaper.png)

### Statistiken und Einschränkungen des E-Mail-Servers {#email-server-statistics-and-limitations}

Der Statistikserver verwaltet die folgenden Statistiken für jeden E-Mail-Server, der Nachrichten erhält:

* Anzahl der offenen Point-in-Time-Verbindungen,
* Anzahl der in der letzten Stunde gesendeten Nachrichten,
* Rate erfolgreicher/abgelehnter Verbindungen,
* Anzahl der Verbindungen zu unerreichbar-Servern.

Gleichzeitig lädt das Modul eine Liste von Einschränkungen für bestimmte E-Mail-Server:

* Maximale Anzahl gleichzeitiger Verbindungen,
* maximale Anzahl von Nachrichten pro Stunde,
* Maximale Anzahl von Nachrichten pro Verbindung.

### Verwalten von IP-Adressen {#managing-ip-addresses}

Der Statistikserver kann mehrere Instanzen oder mehrere Computer mit derselben öffentlichen IP-Adresse kombinieren. Es ist daher nicht mit einer bestimmten Instanz verknüpft, sondern muss eine Instanz kontaktieren, um Einschränkungen pro Domäne wiederherzustellen.

Für jede Zielgruppe MX und für jede Quell-IP werden Versand-Statistiken gespeichert. Wenn die Zieldomäne beispielsweise 5 MX hat und die Plattform 3 verschiedene IP-Adressen verwenden kann, kann der Server bis zu 15 Reihen von Indikatoren für diese Domäne verwalten.

Die Quell-IP-Adresse stimmt mit der öffentlichen IP-Adresse überein, d. h. mit der Adresse, die vom Remote-E-Mail-Server angezeigt wird. Diese IP-Adresse kann sich von der Adresse des Computers unterscheiden, auf dem die **Metadaten** gehostet werden, wenn ein NAT-Router angegeben ist. Aus diesem Grund verwendet der Statistikserver eine Kennung, die mit der öffentlichen IP (**publicId**) übereinstimmt. Die Verbindung zwischen der lokalen Adresse und dieser Kennung wird in der Konfigurationsdatei &quot; **serverConf.xml** &quot;deklariert. Alle in der Datei **serverConf.xml** verfügbaren Parameter sind in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md)aufgeführt.

## Versand-Ausgabesteuerung {#delivery-output-controlling}

Um Nachrichten an E-Mail-Server zu senden, fordert die Komponente **Email Traffic Shaper** eine Verbindung vom Statistikserver an. Sobald die Anforderung akzeptiert wurde, wird die Verbindung geöffnet.

Vor dem Senden von Nachrichten fordert das Modul Token vom Server an. Dies sind im Allgemeinen Sätze von mindestens 10 Token, was die Anzahl der Abfragen auf den Server verringert.

Der Server speichert alle Statistiken zu Verbindungen und Versänden. Beim Neustart gehen die Informationen vorübergehend verloren: Jeder Kunde speichert eine lokale Kopie seiner Versandstatistik und gibt diese regelmäßig (alle 2 Minuten) an den Server zurück. Der Server kann die Daten dann erneut Aggregat machen.

Die folgenden Abschnitte beschreiben die Verarbeitung einer Nachricht durch die Komponente **E-Mail-Traffic-Shaper** .

### Message delivery {#message-delivery}

Wenn eine Nachricht gesendet wird, gibt es 3 mögliche Ergebnisse:

1. **Erfolg**: die Nachricht erfolgreich gesendet wurde. Die Nachricht wird aktualisiert.
1. **Meldung fehlgeschlagen**: der kontaktierte Server hat die Nachricht für den ausgewählten Empfänger abgelehnt. Dieses Ergebnis stimmt mit den Rückgabecodes 550 bis 599 überein, Ausnahmen können jedoch definiert werden.
1. **Sitzung fehlgeschlagen** (5.11 nach oben): Wenn die **Metrik** eine Antwort für diese Nachricht erhält, wird die Nachricht abgebrochen (siehe [Abbruch](#message-abandonment)der Nachricht). Die Nachricht wird an einen anderen Pfad gesendet oder auf &quot;Ausstehend&quot;eingestellt, wenn keine anderen Pfade verfügbar sind (siehe [Meldung ausstehend](#message-pending)).

   >[!NOTE]
   >
   >Ein **Pfad** ist eine Verbindung zwischen dem Adobe Campaign **mta** und der Zielgruppe **mta**. Die Adobe Campaign- **Metadaten** können aus mehreren Beginn-IPs und mehreren Zielgruppen-Domänen-IPs ausgewählt werden.

### Abbruch der Nachricht {#message-abandonment}

Abgebrochene Nachrichten werden an die **Metadaten** zurückgegeben und nicht mehr von der **mtachild** verwaltet.

Die **Metadaten** entscheiden über das Verfahren für diese Meldung (Wiederherstellung, Abbruch, Quarantäne usw.) abhängig vom Antwortcode und den Regeln.

### Meldung ausstehend {#message-pending}

Eine Meldung wird blockiert, wenn sie in die aktive Warteschlange gelangt und keine verfügbaren Pfade vorhanden sind.

Ein Pfad wird im Allgemeinen als für einen variablen Zeitraum nach einem Verbindungsfehler nicht verfügbar markiert. Die Dauer der Nichtverfügbarkeit hängt von der Häufigkeit und dem Alter der Fehler ab.

## Konfiguration des Statistikservers {#statistics-server-configuration}

Der Statistikserver kann von mehreren Instanzen verwendet werden: Es muss unabhängig von den Instanzen konfiguriert werden, die es verwenden werden.

Beginn durch Definieren der Adobe Campaign-Datenbank, in der die Konfiguration gehostet wird.

### Konfiguration des Beginns {#start-configuration}

Standardmäßig wird das **STAT** -Modul für jede Instanz gestartet. Wenn die Instanzen auf demselben Computer mutualisiert werden oder wenn Instanzen dieselbe IP-Adresse haben, wird ein einzelner Statistikserver verwendet: die anderen müssen deaktiviert sein.

### Definition des Serveranschlusses {#definition-of-the-server-port}

Standardmäßig überwacht der Statistikserver den Anschluss 7777. Dieser Anschluss kann in der Datei &quot; **serverConf.xml** &quot;geändert werden. Alle in der Datei **serverConf.xml** verfügbaren Parameter sind in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md)aufgeführt.

```
<stat port="1234"/>
```

## MX-Konfiguration {#mx-configuration}

### Über MX-Regeln {#about-mx-rules}

MX-Regeln (Mail eXchanger) dienen zur Verwaltung der Kommunikation zwischen einem Sender- und einem Empfangs-Server.

>[!IMPORTANT]
>
>Bei gehosteten oder hybriden Installationen werden die Versanddurchsatzregeln der **[!UICONTROL MX-Verwaltung]** nicht mehr verwendet, wenn Sie auf den Enhanced MTA aktualisiert haben. Der Enhanced MTA verwendet seine eigenen MX-Regeln. Mit diesen kann Ihr Durchsatz anhand Ihrer historischen E-Mail-Reputation und dem Echtzeit-Feedback, das von den Domänen stammt, von denen Sie E-Mails senden, angepasst werden.
>
>Weitere Informationen zum Adobe Campaign Enhanced MTA finden Sie in diesem [Dokument](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html).

Diese Regeln werden jeden Morgen um 6 Uhr (Serverzeit) automatisch neu geladen, um die Client-Instanz regelmäßig bereitzustellen.

Je nach Materialkapazitäten und internen Richtlinien akzeptieren ISP eine vordefinierte Anzahl an Verbindungen und Nachrichten pro Stunde. Diese Variablen können unter Umständen automatisch durch ISP-Systeme abgeändert werden, was von der Reputation der IP- und Sender-Domain abhängt. Über die Zustellbarkeitsplattform werden in Adobe Campaign pro ISP mehr als 150 spezifische Regeln und zusätzlich eine allgemeine Regel für andere Domains verwaltet.

Die maximale Verbindungsanzahl hängt nicht ausschließlich von der Anzahl der durch den MTA verwendeten öffentlichen IP-Adressen ab.

Wenn Sie z. B. fünf Verbindungen in den MX-Regeln festgelegt und zwei öffentliche IPs konfiguriert haben, könnte man annehmen, dass Sie für diese Domain nicht mehr als zehn Verbindungen gleichzeitig geöffnet haben können. Dem ist aber nicht so, tatsächlich bezieht sich die maximale Verbindungsanzahl auf einen Pfad, der eine Kombination aus einer unserer öffentlichen MTA-IPs und einer öffentlichen IP des Client-MTAs darstellt.

Im folgenden Beispiel hat der Benutzer zwei konfigurierte öffentliche IP-Adressen und yahoo.com als Domain.

```
user:~ user$ host -t mx yahoo.com
                yahoo.com mail is handled by 1 mta5.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta6.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta7.am0.yahoodns.net.
```

Aus den MX-Einträgen von yahoo.com geht hervor, dass yahoo.com drei Mail Exchanger aufweist. Um eine Verbindung zum Client-MX (Peer-MX) herzustellen, fragt der MTA dessen IP-Adresse im DNS ab.

```
user:~ user$ host -t a mta5.am0.yahoodns.net
                mta5.am0.yahoodns.net has address 98.136.216.26
                mta5.am0.yahoodns.net has address 98.136.217.202
                mta5.am0.yahoodns.net has address 98.138.112.38
                mta5.am0.yahoodns.net has address 66.196.118.37
                mta5.am0.yahoodns.net has address 63.250.192.46
                mta5.am0.yahoodns.net has address 66.196.118.240
                mta5.am0.yahoodns.net has address 98.136.217.203
                mta5.am0.yahoodns.net has address 98.138.112.35
```

Was diesen Eintrag angeht, kann der Benutzer acht Peer-IP-Adressen kontaktieren. Da er über zwei öffentliche IP-Adressen verfügt, ermöglicht ihm das sechzehn (8*2) Kombinationen zum Erreichen der E-Mail-Server von yahoo.com. Jede dieser Kombinationen nennt sich Pfad.

Der zweite MX-Eintrag stellt sich wie folgt dar:

```
user:~ user$ host -t a mta6.am0.yahoodns.net
                mta6.am0.yahoodns.net has address 98.138.112.38
                mta6.am0.yahoodns.net has address 98.136.216.26
                mta6.am0.yahoodns.net has address 63.250.192.46
                mta6.am0.yahoodns.net has address 66.196.118.35
                mta6.am0.yahoodns.net has address 98.136.217.203
                mta6.am0.yahoodns.net has address 98.138.112.32
                mta6.am0.yahoodns.net has address 98.138.112.37
                mta6.am0.yahoodns.net has address 66.196.118.33
```

Vier der acht IP-Adressen werden bereits in mta5 verwendet (98.136.216.26, 98.138.112.38, 63.250.192.46 und 98.136.217.203). Dieser Eintrag ermöglicht dem Benutzer die Verwendung von vier neuen IP-Adressen. Gleichermaßen verhält es sich mit dem dritten MX-Eintrag.

Insgesamt stehen dem Benutzer sechzehn Remote-IP-Adressen zur Verfügung. In Kombination mit den zwei lokalen öffentlichen IPs stehen zweiunddreißig Pfade zum Erreichen der E-Mail-Server von yahoo.com zur Verfügung.

>[!NOTE]
>
>Wenn sich zwei MX-Einträge auf dieselbe IP-Adresse beziehen, wird diese als ein Pfad gezählt, nicht als zwei.

Unten stehende Beispiele zeigen die Verwendung von MX-Regeln:

![](assets/s_ncs_examples_mx_rules.png)

Im folgenden Beispiel ist der Benutzer für eine bestimmte Domain auf 10.000 Nachrichten pro Stunde beschränkt, aber die MTA-Durchsatzkapazität liegt höher als diese Begrenzung.

In diesem Fall wird der Traffic für jede Stunde in zwölf Abschnitte von jeweils fünf Minuten unterteilt, wobei die reale Begrenzung bei 833 Nachrichten pro Abschnitt liegt.

Diese Nachrichten werden so schnell wie möglich gesendet.

![](assets/s_ncs_traffic_shaping.png)

### MX-Verwaltung konfigurieren {#configuring-mx-management}

Die für MX einzuhaltenden Regeln werden im **[!UICONTROL MX-Management]** -Dokument des Knotens &quot; **[!UICONTROL Administration&quot;> &quot;Kampagnenverwaltung&quot;> &quot;Verwaltung für nicht bereitgestellte Elemente&quot;> &quot;Mail-Regelsätze]** &quot;des Baums definiert.

Wenn das **[!UICONTROL MX-Management]** -Dokument nicht im Knoten vorhanden ist, können Sie es manuell erstellen. Gehen Sie dazu wie folgt vor:

1. Erstellen Sie einen neuen Satz von E-Mail-Regeln.
1. Wählen Sie den **[!UICONTROL MX-Management]** -Modus.

   ![](assets/s_ncs_install_mx_mgt_rule.png)

1. Geben Sie **defaultMXRules** in das Feld &quot; **[!UICONTROL Interner Name]** &quot;ein.

Damit Änderungen berücksichtigt werden, müssen Sie den Statistikserver neu starten.

Um die Konfiguration neu zu laden, ohne den Statistikserver neu zu starten, verwenden Sie den folgenden Befehl auf dem Computer, auf dem der Server gehostet wird: `nlserver stat -reload`

>[!NOTE]
>
>Diese Befehlszeile ist **nlserver restart** vorzuziehen. Sie beugt dem Verlust vor dem Neustart abgerufener statistischer Daten vor und verhindert Spitzenbelastungszeiten, die im Widerspruch zu den in den MX-Regeln definierten Kontingenten stehen können.

### Konfigurieren von MX-Regeln {#configuring-mx-rules}

Das **[!UICONTROL MX-Management]** -Dokument Liste alle Domänen, die mit einer MX-Regel verknüpft sind.

Die erste Regel, deren MX-Maske mit dem gewünschten MX kompatibel ist, wird angewendet.

Die folgenden Parameter stehen für jede Regel zur Verfügung:

* **[!UICONTROL MX-Maske]**: Domäne, auf die die Regel angewendet wird. Jede Regel definiert eine Adressenmaske des MX. Jeder MX, dessen Name dieser Adressenmaske entspricht, kommt somit infrage. Die Maske kann die Joker &quot;*&quot; und &quot;?&quot; enthalten.

   So sind die Adressen

   * a.mx.yahoo.com
   * b.mx.yahoo.com
   * c.mx.yahoo.com

   mit folgenden Masken kompatibel:

   * *.yahoo.com
   * ?.mx.yahoo.com

   Beispielsweise lautet bei der E-Mail-Adresse foobar@gmail.com die Domain gmail.com und der MX-Eintrag sieht folgendermaßen aus:

   ```
   gmail.com mail exchanger = 20 alt2.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 10 alt1.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 40 alt4.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 5  gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 30 alt3.gmail-smtp-in.l.google.com.
   ```

   In diesem Fall wird die MX-Regel verwendet `*.google.com` werden. Wie Sie sehen können, stimmt die MX-Regelmaske nicht unbedingt mit der Domäne in der E-Mail überein. Die MX-Regeln, die für gmail.com E-Mail-Adressen angewendet werden, sind die mit der Maske `*.google.com`.

* **[!UICONTROL Bereich der Bezeichner]**: Mit dieser Option können Sie die Bereiche der Bezeichner (publicID) angeben, für die die Regel gilt. Folgende Angaben sind möglich:

   * Eine Ziffer: Die Regel wird nur für diese publicId angewendet,
   * A range of numbers (**number1-number2**): the rule will apply to all publicIds between these two numbers.

   >[!NOTE]
   >
   >Wenn das Feld leer ist, gilt die Regel für alle Bezeichner.

   Bei einer öffentlichen Kennung handelt es sich um eine interne Kennung einer öffentlichen IP, die von einem oder mehreren MTAs verwendet wird. Diese Art von Kennungen wird in der Datei **config-instance.xml** von MTA-Servern definiert.

   ![](assets/s_ncs_install_mta_ips.png)

* **[!UICONTROL Freigegeben]**: definiert den Umfang der Eigenschaften für diese MX-Regel. Wenn diese Option aktiviert ist, werden alle Parameter für alle in der Instanz verfügbaren IPs freigegeben. Wenn diese Option deaktiviert ist, werden die MX-Regeln für jede IP-Adresse definiert. Die maximale Anzahl der Nachrichten wird mit der Anzahl der verfügbaren IPs multipliziert.
* **[!UICONTROL Maximale Anzahl Verbindungen]**: maximale Anzahl gleichzeitiger Verbindungen zur Domäne des Absenders.
* **[!UICONTROL Maximale Anzahl der Nachrichten]**: maximale Anzahl von Nachrichten, die bei einer Verbindung gesendet werden können. Wenn die Meldungen diese Zahl überschreiten, wird die Verbindung geschlossen und eine neue geöffnet.
* **[!UICONTROL Nachrichten pro Stunde]**: maximale Anzahl von Nachrichten, die innerhalb einer Stunde an die Domäne des Absenders gesendet werden können.
* **[!UICONTROL Zeitlimit für Verbindung]**: Zeitschwellenwert für die Verbindung mit einer Domäne.

   >[!NOTE]
   >
   >Windows kann vor diesem Schwellenwert eine **Zeitüberschreitung** ausgeben, was von Ihrer Windows-Version abhängt.

* **[!UICONTROL Zeitüberschreitungsdaten]**: maximale Wartezeit nach dem Senden des Nachrichteninhalts (Abschnitt &quot;DATEN&quot;des SMTP-Protokolls).
* **[!UICONTROL Timeout]**: maximale Wartezeit für andere Austausche mit dem SMTP-Server.
* **[!UICONTROL TLS]**: Das TLS-Protokoll, mit dem Sie E-Mail-Versand verschlüsseln können, kann selektiv aktiviert werden. Für jede MX-Maske stehen die folgenden Optionen zur Verfügung:

   * **[!UICONTROL Standardkonfiguration]**: Dies ist die allgemeine Konfiguration, die in der Konfigurationsdatei &quot;serverConf.xml&quot;angegeben ist, die angewendet wird.

      >[!IMPORTANT]
      >
      >Es wird nicht empfohlen, die Standardkonfiguration zu ändern.

   * **[!UICONTROL Deaktiviert]** : Die Nachrichten werden systematisch ohne Verschlüsselung gesendet.
   * **[!UICONTROL Opportunistisch]** : Message Versand wird verschlüsselt, wenn der empfangende Server (SMTP) das TLS-Protokoll generieren kann.

Konfigurationsbeispiel:

![](assets/s_ncs_install_mx_mgt_rule_details.png)

### Verwalten von E-Mail-Formaten {#managing-email-formats}

Sie können das Format der gesendeten Nachrichten definieren, sodass sich der angezeigte Inhalt automatisch an die Domäne der Adresse des jeweiligen Empfängers anpasst.

Gehen Sie dazu zum Dokument **[!UICONTROL Verwaltung von E-Mail-Formaten]** , das sich unter **[!UICONTROL Administration]** > **[!UICONTROL Kampagnenverwaltung]** > Verwaltung **** nicht bereitgestellter Produkte > **[!UICONTROL Mail-Regelsätze]** befindet.

Dieses Dokument enthält eine Liste aller vordefinierten Domänen, die den von Adobe Campaign verwalteten japanischen Formaten entsprechen. For more information, refer to [this document](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

![](assets/mail_rule_sets.png)

Mit dem Parameter **MIME structure** (Multizweck Internet Mail Extensions) können Sie die Nachrichtenstruktur definieren, die an die verschiedenen E-Mail-Clients gesendet wird. Dabei stehen drei Optionen zur Verfügung:

* **Mehrteilig**: Die Nachricht wird im Text- oder HTML-Format gesendet. Wenn das HTML-Format nicht akzeptiert wird, kann die Nachricht weiterhin im Textformat angezeigt werden.

   Standardmäßig ist die mehrteilige Struktur **mehrteilig/alternativ**, aber sie wird automatisch zu **mehrteiligen/verwandten** Elementen, wenn ein Bild der Nachricht hinzugefügt wird. Bestimmte Anbieter erwarten, dass das **mehrteilige/verwandte** Format standardmäßig verwendet wird. Die Option Mehrteilige **[!UICONTROL Teile erzwingen/verwandte]** Formate auch dann, wenn kein Bild angehängt wird.

* **HTML**: Es wird eine Nur-HTML-Nachricht gesendet. Wenn das HTML-Format nicht akzeptiert wird, wird die Meldung nicht angezeigt.
* **Text**: Es wird eine Meldung im Format &quot;Nur Text&quot;gesendet. Der Vorteil von Textformatmeldungen ist ihre sehr geringe Größe.

Wenn die **[!UICONTROL Bildeinschlussoption]** aktiviert ist, werden diese direkt im Textkörper der E-Mail angezeigt. Die Bilder werden dann hochgeladen und die URL-Verknüpfungen werden durch ihren Inhalt ersetzt.

Diese Option wird besonders vom japanischen Markt für **Deco-Mail**, **Decore Mail** oder **Design Mail** verwendet. Weitere Informationen finden Sie in [diesem Dokument](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

>[!IMPORTANT]
>
>Das Einfügen von Bildern in eine E-Mail vergrößert deren Größe erheblich.

## Serverkonfiguration für Versand {#delivery-server-configuration}

### Synchronisierung der Uhr {#clock-synchronization}

Die Uhren aller Server, aus denen die Adobe Campaign-Plattform (einschließlich der Datenbank) besteht, müssen synchronisiert und ihre Systeme auf dieselbe Zeitzone eingestellt werden.

### Koordinaten des Statistikservers {#coordinates-of-the-statistics-server}

Die Adresse des Statistikservers muss im **Metadaten angegeben werden**.

Mit der **statServerAddress** -Eigenschaft des **mta** -Elements der Konfiguration können Sie die Adresse und die Nummer des zu verwendenden Anschlusses angeben.

```
<mta statServerAddress="emailStatServer:7777">
   [...]
 </mta>
```

Um den Statistiserver auf demselben Computer zu verwenden, müssen Sie mindestens den Namen des Computers mit dem **Wert localhost** eingeben:

```
 <mta statServerAddress="localhost">
```

>[!IMPORTANT]
>
>Wenn dieses Feld nicht ausgefüllt wird, wird die **Metadaten** nicht Beginn.

### Liste der zu verwendenden IP-Adressen {#list-of-ip-addresses-to-use}

Die Konfiguration für das Traffic-Management befindet sich im **Element &quot;mta/child/smtp** &quot;der Konfigurationsdatei.

Für jedes **IPAffinity** -Element müssen Sie die IP-Adressen deklarieren, die für den Computer verwendet werden können.

Beispiel:

```
<IPAffinity localDomain="<domain>" name="default">
  <IP address="192.168.0.11" publicId="1" weight="5"/>
  <IP address="192.168.0.12" heloHost="revdns1.campaign.com" publicId="2" weight="5"/>
  <IP address="192.168.0.13" publicId="3" weight="1"/>
</IPAffinity>
```

Die Parameter lauten wie folgt:

* **Adresse**: dies ist die IP-Adresse des zu verwendenden MTA-Hostcomputers.
* **heloHost**: dieser Bezeichner stellt die IP-Adresse dar, wie sie vom SMTP-Server angezeigt wird.

* **publicId**: Diese Informationen sind nützlich, wenn eine IP-Adresse von mehreren Adobe Campaign- **mtas** hinter einem NAT-Router freigegeben wird. Der Statistikserver verwendet diesen Bezeichner, um die Verbindungsdaten zu speichern und Statistiken zwischen diesem Startpunkt und dem Zielgruppen-Server zu senden.
* **gewichtung**: können Sie die relative Häufigkeit der Verwendung der Adresse definieren. Standardmäßig haben alle Adressen eine Gewichtung von 1.

>[!NOTE]
>
>In der Datei &quot;serverConf.xml&quot;müssen Sie sicherstellen, dass eine IP einem einzelnen Helohost mit einer eindeutigen Kennung (public_id) entspricht. Es kann nicht mehreren Helohosts zugeordnet werden, was zu Problemen bei der Einschränkung des Versands führen kann.

Im vorherigen Beispiel werden die Adressen unter normalen Bedingungen wie folgt verteilt:

    * &quot;1&quot;: 5 / (5+5+1) = 45%
    * &quot;2&quot;: 5 / (5+5+1) = 45%
    * &quot;3&quot;: 1 / (5+5+1) = 10%

Wenn zum Beispiel die erste Adresse nicht für eine bestimmte MX verwendet werden kann, werden die Nachrichten wie folgt gesendet:

    * &quot;2&quot;: 5 / (5+1) = 83%
    * &quot;3&quot;: 1 / (5+1) = 17%

* **includeDomains**: können Sie diese IP-Adresse für E-Mails einer bestimmten Domäne reservieren. Dies ist eine Liste von Masken, die einen oder mehrere Platzhalter (&#39;*&#39;) enthalten können. Wenn das Attribut nicht angegeben ist, können alle Domänen diese IP-Adresse verwenden.

   Beispiel: **includeDomains=&quot;wanadoo.com,orange.com,yahoo.*&quot;**

* **excludeDomains**: schließt eine Liste von Domänen für diese IP-Adresse aus. Dieser Filter wird nach dem Filter **includeDomains** angewendet.

   ![](assets/s_ncs_install_mta_ips.png)

## Optimierung des E-Mail-Versands {#email-sending-optimization}

Die interne Architektur der Adobe Campaign- **Metadaten** wirkt sich auf die Konfiguration zur Optimierung des E-Mail-Versands aus. Hier finden Sie einige Tipps zur Verbesserung Ihrer Versand.

### Anpassen des Parameters maxWaitingMessages {#adjust-the-maxwaitingmessages-parameter}

Der Parameter **maxWaitingMessages** gibt die höchste Anzahl von Nachrichten an, die im Voraus von der **mtachild** vorbereitet wurden. Nachrichten werden erst dann aus dieser Liste gelöscht, wenn sie gesendet oder abgebrochen wurden.

Dieser Parameter ist sehr wichtig und besonders wichtig, wenn Nachrichten nicht nach Domäne sortiert werden.

Sobald der Schwellenwert **maxWorkingSetMb** (256) erreicht ist, beendet der Versand das Senden von Nachrichten. Die Leistung wird deutlich sinken, bis die **mtachild** -Beginn wieder ansteigen. Um dieses Problem zu umgehen, können Sie entweder den Schwellenwert des Parameters **maxWorkingSetMb** erhöhen oder den Schwellenwert des Parameters **maxWaitingMessages** verringern.

Der Parameter **maxWorkingSetMb** wird empirisch berechnet, indem die maximale Anzahl von Nachrichten mit der durchschnittlichen Nachrichtengröße multipliziert und das Ergebnis mit 2,5 multipliziert wird. Wenn beispielsweise eine Nachricht eine durchschnittliche Größe von 50 kB und der Parameter **maxWaitingMessages** 1.000 hat, beträgt der verwendete Speicher durchschnittlich 125 MB.

### Anpassen der Anzahl der mtachild {#adjust-the-number-of-mtachild}

Die Anzahl der Kinder sollte die Anzahl der Prozessoren in der Maschine nicht überschreiten (ca. 1000 Sitzungen). Es wird empfohlen, 8 **mtachild** nicht zu überschreiten. Anschließend können Sie die Anzahl der Meldungen pro **Kind** (**maxMsgPerChild**) erhöhen, um eine ausreichende Lebensdauer zu erreichen.

---
product: campaign
title: Technische E-Mail-Konfiguration
description: Erfahren Sie, wie Sie Campaign so konfigurieren, dass die Ausgabe Ihrer Instanzen beim Versand von E-Mails gesteuert wird.
feature: Installation, Deliverability
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 515adad2-6129-450a-bb9e-fc80127835af
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '3161'
ht-degree: 18%

---

# Technische E-Mail-Konfigurationen{#email-deliverability}



## Übersicht {#overview}

Im folgenden Abschnitt finden Sie einen Überblick über die Konfiguration, die zum Steuern der Ausgabe von Adobe Campaign-Instanzen beim Versand von E-Mails erforderlich ist.

>[!NOTE]
>
>Einige Konfigurationen können nur von Adobe für Bereitstellungen durchgeführt werden, die von Adobe gehostet werden, z. B. für den Zugriff auf Server- und Instanzkonfigurationsdateien. Weitere Informationen zu den verschiedenen Bereitstellungen finden Sie im Abschnitt [Hosting-Modelle](../../installation/using/hosting-models.md) oder auf [dieser Seite](../../installation/using/capability-matrix.md) .

Weitere Informationen zu Konzepten und Best Practices im Zusammenhang mit der Zustellbarkeit mit Adobe Campaign finden Sie in diesem [Abschnitt](../../delivery/using/about-deliverability.md).

Einen tieferen Einblick in die Zustellbarkeit, einschließlich aller technischen Empfehlungen zum effizienten Versand und Empfang von E-Mails durch eine Adobe-Plattform, finden Sie im [Best Practice-Handbuch zur Zustellbarkeit von Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=de).

## Grundprinzip {#operating-principle}

Die Ausgabe einer oder mehrerer Adobe Campaign-Instanzen kann gesteuert werden, um die Anzahl der gesendeten E-Mails auf die jeweilige Domain zu begrenzen. Sie können beispielsweise die Ausgabe für **yahoo.com** -Adressen auf 20.000 pro Stunde beschränken und gleichzeitig 100.000 Nachrichten pro Stunde für alle anderen Domänen konfigurieren.

Die Nachrichtenausgabe muss für jede von den Versandservern verwendete IP-Adresse gesteuert werden (**mta**). Mehrere auf mehrere Computer verteilte **mta**, die zu verschiedenen Adobe Campaign-Instanzen gehören, können dieselbe IP-Adresse für den E-Mail-Versand verwenden: Es muss ein Prozess eingerichtet werden, um die Verwendung dieser IP-Adressen zu koordinieren.

Das **stat**-Modul leitet alle Verbindungsanfragen und -nachrichten für eine Reihe von IP-Adressen an die E-Mail-Server weiter. Der Statistikserver verfolgt die Sendungen und kann den Versand auf der Grundlage festgelegter Kontingente aktivieren oder deaktivieren.

![](assets/s_ncs_install_mta.png)

* Der Statistikserver (**stat**) ist mit einer Adobe Campaign-Datenbank verknüpft, um die Konfiguration zu laden.
* Die Versandserver (**mta**) verwenden eine UDP, um einen Statistikserver zu kontaktieren, der nicht immer zu ihrer eigenen Instanz gehört.

### Versandserver {#delivery-servers}

Das Modul **mta** verteilt Nachrichten an seine untergeordneten **mtachild**-Module. Jeder **mtachild** bereitet Nachrichten vor, bevor er eine Autorisierung vom Statistikserver anfordert, und sendet sie.

Zusammenfassend sind folgende Etappen zu durchlaufen:

1. Die **mta** wählt die geeigneten Nachrichten aus und weist ihnen eine verfügbare **mtachild** zu.
1. Der **mtachild** lädt alle Informationen, die zum Erstellen der Nachricht erforderlich sind (Inhalt, Personalisierungselemente, Anhänge, Bilder usw.) leitet die Nachricht an den **Traffic-Shaper der E-Mail** weiter.
1. Sobald der E-Mail-Traffic-Planer die Autorisierung des Statistikservers (**smtp stat**) erhält, wird die Nachricht an den Empfänger gesendet.

![](assets/s_ncs_install_email_traffic_shaper.png)

### Statistiken zu E-Mail-Servern und Einschränkungen {#email-server-statistics-and-limitations}

Der Statistikserver verwaltet die folgenden Statistiken für jeden E-Mail-Server, der Nachrichten erhält:

* Anzahl der geöffneten Point-in-Time-Verbindungen,
* Anzahl der in der letzten Stunde gesendeten Nachrichten,
* Rate erfolgreicher/abgelehnter Verbindungen,
* Rate der Verbindungen zu unerreichbaren Servern.

Gleichzeitig lädt das Modul eine Liste von Einschränkungen für bestimmte E-Mail-Server:

* Maximale Anzahl simultaner Verbindungen,
* Maximale Nachrichtenanzahl pro Stunde,
* Maximale Anzahl an Nachrichten pro Verbindung.

### Verwalten von IP-Adressen {#managing-ip-addresses}

Der Statistikserver kann mehrere Instanzen oder mehrere Computer mit derselben öffentlichen IP-Adresse kombinieren. Sie ist daher nicht mit einer bestimmten Instanz verknüpft, muss sich jedoch an eine Instanz wenden, um die Einschränkungen pro Domäne wiederherzustellen.

Versandstatistiken werden für jeden Ziel-MX und für jede Quell-IP-Adresse aufbewahrt. Wenn die Zieldomäne beispielsweise über 5 MX verfügt und die Plattform 3 verschiedene IP-Adressen verwenden kann, kann der Server bis zu 15 verschiedene Indikatoren für diese Domäne verwalten.

Die Quell-IP-Adresse entspricht der öffentlichen IP-Adresse, d. h. der Adresse, wie sie vom Remote-E-Mail-Server angezeigt wird. Diese IP-Adresse kann sich von der Adresse des Computers unterscheiden, der als Host für die **mta** dient, wenn ein NAT-Router bereitgestellt wird. Aus diesem Grund verwendet der Statistikserver eine Kennung, die mit der öffentlichen IP (**publicId**) übereinstimmt. Die Verbindung zwischen der lokalen Adresse und dieser Kennung wird in der Konfigurationsdatei **serverConf.xml** deklariert. Alle in **serverConf.xml** verfügbaren Parameter sind in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.

## Ausgabesteuerung des Versands {#delivery-output-controlling}

Um Nachrichten an E-Mail-Server zu senden, fordert die Komponente **Traffic-förmig gestalten** eine Verbindung vom Statistikserver an. Sobald die Anfrage akzeptiert wurde, wird die Verbindung geöffnet.

Vor dem Senden von Nachrichten fordert das Modul &quot;Tokens&quot;vom Server an. Dies sind im Allgemeinen Sets von mindestens 10 Token, wodurch die Anzahl der Abfragen an den Server verringert wird.

Der Server speichert alle Statistiken bezüglich Verbindungen und Sendungen. Im Falle eines Neustart gehen die Informationen vorübergehend verloren: Jeder Kunde bewahrt eine lokale Kopie seiner Versandstatistiken auf und gibt sie regelmäßig (alle 2 Minuten) an den Server zurück. Der Server kann die Daten dann erneut aggregieren.

In den folgenden Abschnitten wird die Verarbeitung einer Nachricht durch die Komponente **Traffic-förmig für E-Mails** beschrieben.

### Nachrichtenversand {#message-delivery}

Wenn eine Nachricht gesendet wird, gibt es drei mögliche Ergebnisse:

1. **Erfolg**: Die Nachricht wurde erfolgreich gesendet. Die Nachricht wird aktualisiert.
1. **Nachricht fehlgeschlagen**: Der kontaktierte Server hat die Nachricht für den ausgewählten Empfänger abgelehnt. Dieses Ergebnis entspricht den Rückgabecodes 550 bis 599, es können jedoch Ausnahmen definiert werden.
1. **Sitzung fehlgeschlagen** (für 5.11 nach oben): Wenn die **mta** eine Antwort für diese Nachricht erhält, wird die Nachricht abgebrochen (siehe [Nachrichtenabbruch](#message-abandonment)). Die Nachricht wird an einen anderen Pfad gesendet oder auf &quot;Ausstehend&quot; gesetzt, wenn keine anderen Pfade verfügbar sind (siehe [Nachricht ausstehend](#message-pending)).

   >[!NOTE]
   >
   >Ein **Pfad** ist eine Verbindung zwischen dem Adobe Campaign **mta** und dem Ziel **mta**. Die Adobe Campaign **mta** kann aus mehreren Start-IPs und mehreren Ziel-Domain-IPs wählen.

### Abbruch einer Nachricht {#message-abandonment}

Abgebrochene Nachrichten werden an die **mta** zurückgegeben und nicht mehr von der **mtachild** verwaltet.

Die **mta** entscheidet über das Verfahren für diese Nachricht (Wiederherstellung, Abbruch, Quarantäne usw.) abhängig vom Antwort-Code und den Regeln.

### Nachricht ausstehend {#message-pending}

Wenn eine Nachricht in die aktive Warteschlange gelangt, wird sie ausgesetzt und es sind keine Pfade verfügbar.

Ein Pfad wird im Allgemeinen für einen variablen Zeitraum nach einem Verbindungsfehler als nicht verfügbar markiert. Die Dauer der Nichtverfügbarkeit hängt von der Häufigkeit und dem Alter der Fehler ab.

## Statistische Serverkonfiguration {#statistics-server-configuration}

Der Statistikserver kann von mehreren Instanzen verwendet werden: Er muss unabhängig von den Instanzen konfiguriert werden, die ihn verwenden.

Definieren Sie zunächst die Adobe Campaign-Datenbank, in der die Konfiguration gehostet wird.

### Konfiguration starten {#start-configuration}

Standardmäßig wird das Modul **stat** für jede Instanz gestartet. Wenn die Instanzen auf demselben Computer gepoolt werden oder Instanzen dieselbe IP-Adresse nutzen, wird ein einzelner Statistikserver verwendet: Die anderen müssen deaktiviert werden.

### Definition des Serveranschlusses {#definition-of-the-server-port}

Der Statistikserver überwacht standardmäßig den Port 7777. Dieser Anschluss kann in der Datei **serverConf.xml** geändert werden. Alle in **serverConf.xml** verfügbaren Parameter sind in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.

```
<stat port="1234"/>
```

## MX-Konfiguration {#mx-configuration}

>[!IMPORTANT]
>
>Bei gehosteten oder hybriden Installationen werden die Versanddurchsatzregeln der **[!UICONTROL MX-Verwaltung]** nicht mehr verwendet, wenn Sie auf den [Enhanced MTA](../../delivery/using/sending-with-enhanced-mta.md) aktualisiert haben. Der Enhanced MTA verwendet seine eigenen MX-Regeln. Mit diesen kann Ihr Durchsatz anhand Ihrer historischen E-Mail-Reputation und dem Echtzeit-Feedback, das von den Domains stammt, von denen Sie E-Mails senden, angepasst werden.

### Über MX-Regeln {#about-mx-rules}

>[!NOTE]
>
>Dieser Abschnitt und die folgenden Abschnitte gelten nur für On-Premise-Installationen und gehostete/hybride Installationen, die den veralteten Campaign MTA verwenden.

MX-Regeln (Mail eXchanger) dienen zur Verwaltung der Kommunikation zwischen einem Sende- und einem Empfangs-Server.

Diese Regeln werden automatisch jeden Morgen um 6 Uhr (Serverzeit) neu geladen, um die Client-Instanz regelmäßig bereitzustellen.

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

Für diesen Datensatz kann der Benutzer 8 Peer-IP-Adressen kontaktieren. Da der Benutzer über zwei öffentliche IP-Adressen verfügt, erhalten diese 8 * 2 = 16 Kombinationen, um die E-Mail-Server yahoo.com zu erreichen. Jede dieser Kombinationen wird als Pfad bezeichnet.

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

Im Folgenden finden Sie einige Beispiele für die Verwendung von MX-Regeln:

![](assets/s_ncs_examples_mx_rules.png)

Im folgenden Beispiel ist der Benutzer für eine bestimmte Domain auf 10.000 Nachrichten pro Stunde beschränkt, aber die MTA-Durchsatzkapazität liegt höher als diese Begrenzung.

In diesem Fall wird der Traffic für jede Stunde in zwölf Abschnitte von jeweils fünf Minuten unterteilt, wobei die reale Begrenzung bei 833 Nachrichten pro Abschnitt liegt.

Diese Nachrichten werden so schnell wie möglich gesendet.

![](assets/s_ncs_traffic_shaping.png)

### MX-Verwaltung konfigurieren {#configuring-mx-management}

Die für MX einzuhaltenden Regeln werden im Dokument **[!UICONTROL MX-Verwaltung]** des Knotens **[!UICONTROL Administration > Campaign Management > Unzustellbarkeitsverwaltung > E-Mail-Regelsätze]** des Navigationsbaums definiert.

Wenn das Dokument **[!UICONTROL MX management]** nicht im Knoten vorhanden ist, können Sie es manuell erstellen. Gehen Sie dazu wie folgt vor:

1. Erstellen Sie einen neuen Satz von E-Mail-Regeln.
1. Wählen Sie den Modus **[!UICONTROL MX-Verwaltung]** aus.

   ![](assets/s_ncs_install_mx_mgt_rule.png)

1. Geben Sie **defaultMXRules** in das Feld **[!UICONTROL Interner Name]** ein.

Damit Änderungen berücksichtigt werden können, müssen Sie den Statistikserver neu starten.

Um die Konfiguration neu zu laden, ohne den Statistikserver neu zu starten, verwenden Sie den folgenden Befehl auf dem Computer, der den Server hostet: `nlserver stat -reload`

>[!NOTE]
>
>Diese Befehlszeile ist **nlserver restart** vorzuziehen. Sie beugt dem Verlust vor dem Neustart abgerufener statistischer Daten vor und verhindert Spitzenbelastungszeiten, die im Widerspruch zu den in den MX-Regeln definierten Kontingenten stehen können.

### Konfigurieren von MX-Regeln {#configuring-mx-rules}

Das Dokument **[!UICONTROL MX-Verwaltung]** listet alle Domänen auf, die mit einer MX-Regel verknüpft sind.

Die erste Regel, deren MX-Maske mit dem gewünschten MX kompatibel ist, wird angewendet.

Die folgenden Parameter stehen für jede Regel zur Verfügung:

* **[!UICONTROL MX mask]**: Domäne, auf die die Regel angewendet wird. Jede Regel definiert eine Adressenmaske des MX. Jeder MX, dessen Name dieser Adressenmaske entspricht, kommt somit infrage. Die Maske kann &quot;&#42;&quot; und &quot;?&quot; enthalten. generische Zeichen.

  So sind die Adressen

   * a.mx.yahoo.com
   * b.mx.yahoo.com
   * c.mx.yahoo.com

  mit folgenden Masken kompatibel:

   * &#42;.yahoo.com
   * ?.mx.yahoo.com

  Beispielsweise lautet bei der E-Mail-Adresse foobar@gmail.com die Domain gmail.com und der MX-Eintrag sieht folgendermaßen aus:

  ```
  gmail.com mail exchanger = 20 alt2.gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 10 alt1.gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 40 alt4.gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 5  gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 30 alt3.gmail-smtp-in.l.google.com.
  ```

  In diesem Fall wird die MX-Regel `*.google.com` verwendet. Wie Sie sehen können, stimmt die MX-Regelmaske nicht unbedingt mit der Domain in der E-Mail überein. Die MX-Regeln, die für gmail.com E-Mail-Adressen angewendet werden, sind diejenigen mit der Maske &quot;`*.google.com`&quot;.

* **[!UICONTROL Bereich der Kennungen]**: Mit dieser Option können Sie die Bereiche der Kennungen (publicID) angeben, für die die Regel gilt. Folgende Angaben sind möglich:

   * Eine Zahl: Die Regel gilt nur für diese publicId,
   * Ein Zahlenbereich (**number1-number2**): Die Regel gilt für alle publicIDs zwischen diesen beiden Zahlen.

  >[!NOTE]
  >
  >Wenn das Feld leer ist, gilt die Regel für alle Kennungen.

  Eine öffentliche ID ist eine interne Kennung einer öffentlichen IP, die von einem oder mehreren MTAs verwendet wird. Diese Art von Kennungen wird in der Datei **config-instance.xml** von MTA-Servern definiert.

  ![](assets/s_ncs_install_mta_ips.png)

* **[!UICONTROL Freigegeben]**: definiert den Umfang der Eigenschaften für diese MX-Regel. Wenn diese Option aktiviert ist, werden alle Parameter für alle in der Instanz verfügbaren IPs freigegeben. Wenn diese Option deaktiviert ist, werden die MX-Regeln für jede IP-Adresse definiert. Die maximale Anzahl an Nachrichten wird mit der Anzahl der verfügbaren IPs multipliziert.
* **[!UICONTROL Maximale Verbindungsanzahl]**: Maximale Anzahl simultaner Verbindungen mit der Absenderdomäne.
* **[!UICONTROL Maximale Nachrichtenanzahl]**: Maximale Anzahl an Nachrichten, die bei einer Verbindung gesendet werden können. Wenn die Nachrichten diese Anzahl überschreiten, wird die Verbindung geschlossen und eine neue geöffnet.
* **[!UICONTROL Nachrichten pro Stunde]**: Maximale Anzahl an Nachrichten, die in einer Stunde an die Absenderdomäne gesendet werden können.
* **[!UICONTROL Verbindungszeitlimit]**: Zeitschwellenwert für die Verbindung zu einer Domäne.

  >[!NOTE]
  >
  >Windows kann vor diesem Schwellenwert einen **Timeout** ausgeben, was von Ihrer Windows-Version abhängt.

* **[!UICONTROL Timeout-Daten]**: Maximale Wartezeit nach dem Senden des Nachrichteninhalts (DATENabschnitt des SMTP-Protokolls).
* **[!UICONTROL Timeout]**: maximale Wartezeit für andere Austausche mit dem SMTP-Server.
* **[!UICONTROL TLS]**: Das TLS-Protokoll, mit dem Sie E-Mail-Sendungen verschlüsseln können, kann selektiv aktiviert werden. Für jede MX-Maske sind die folgenden Optionen verfügbar:

   * **[!UICONTROL Standardkonfiguration]**: Dies ist die allgemeine Konfiguration, die in der angewendeten Konfigurationsdatei serverConf.xml angegeben ist.

     >[!IMPORTANT]
     >
     >Es wird nicht empfohlen, die Standardkonfiguration zu ändern.

   * **[!UICONTROL Deaktiviert]** : Die Nachrichten werden systematisch ohne Verschlüsselung gesendet.
   * **[!UICONTROL Opportunistisch]** : Die Nachrichtenbereitstellung wird verschlüsselt, wenn der Empfangs-Server (SMTP) das TLS-Protokoll generieren kann.

Konfigurationsbeispiel:

![](assets/s_ncs_install_mx_mgt_rule_details.png)

>[!NOTE]
>
>Weitere Informationen zur Verwendung von MX-Servern mit Adobe Campaign finden Sie in [diesem Abschnitt](../../installation/using/using-mx-servers.md).

### Verwalten von E-Mail-Formaten {#managing-email-formats}

Sie können das Format der gesendeten Nachrichten definieren, sodass sich der angezeigte Inhalt automatisch an die Domain der Empfängeradresse anpasst.

Gehen Sie dazu zum Dokument **[!UICONTROL Verwaltung der E-Mail-Formate]**, das sich unter **[!UICONTROL Administration]** > **[!UICONTROL Kampagnenverwaltung]** > **[!UICONTROL Unzustellbarkeitsverwaltung]** > **[!UICONTROL E-Mail-Regelsätze]** befindet.

Dieses Dokument enthält eine Liste aller vordefinierten Domänen, die den von Adobe Campaign verwalteten japanischen Formaten entsprechen. Weitere Informationen finden Sie in [diesem Dokument](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

![](assets/mail_rule_sets.png)

Mit dem Parameter **MIME structure** (Multizweck Internet Mail Extensions) können Sie die Nachrichtenstruktur definieren, die an die verschiedenen E-Mail-Clients gesendet wird. Dabei stehen drei Optionen zur Verfügung:

* **Multipart**: Die Nachricht wird im Text- oder HTML-Format gesendet. Wenn das HTML-Format nicht akzeptiert wird, kann die Nachricht weiterhin im Textformat angezeigt werden.

  Standardmäßig ist die mehrteilige Struktur **multipart/alternative**, sie wird jedoch automatisch zu **multipart/related**, wenn ein Bild zur Nachricht hinzugefügt wird. Einige Provider erwarten standardmäßig das Format **multipart/related** , die Option **[!UICONTROL Multipart/related erzwingen]** legt dieses Format auch dann fest, wenn kein Bild angehängt ist.

* **HTML**: Es wird nur eine HTML-Nachricht gesendet. Wenn das HTML-Format nicht akzeptiert wird, wird die Nachricht nicht angezeigt.
* **Text**: Eine Nachricht im Nur-Text-Format wird gesendet. Der Vorteil von Textformat-Nachrichten besteht in ihrer sehr geringen Größe.

Wenn die Option **[!UICONTROL Bildeinschluss]** aktiviert ist, werden diese direkt im Textkörper der E-Mail angezeigt. Die Bilder werden dann hochgeladen und die URL-Links werden durch ihren Inhalt ersetzt.

Diese Option wird besonders vom japanischen Markt für **Deco-mail**, **Decore Mail** oder **Decoration Mail** verwendet. Weitere Informationen finden Sie in [diesem Dokument](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

>[!IMPORTANT]
>
>Das Einfügen von Bildern in eine E-Mail vergrößert diese erheblich.

## Konfiguration des Versandservers {#delivery-server-configuration}

### Synchronisierung der Uhr {#clock-synchronization}

Die Uhren aller Server, aus denen die Adobe Campaign-Plattform besteht (einschließlich der Datenbank), müssen synchronisiert und ihre Systeme auf dieselbe Zeitzone eingestellt werden.

### Koordinaten des Statistikservers {#coordinates-of-the-statistics-server}

Die Adresse des Statistikservers muss in der Datei **mta** angegeben werden.

Mit der Eigenschaft **statServerAddress** des Elements **mta** der Konfiguration können Sie die Adresse und die Nummer des zu verwendenden Ports angeben.

```
<mta statServerAddress="emailStatServer:7777">
   [...]
 </mta>
```

Um den Statistikserver auf demselben Computer zu verwenden, müssen Sie mindestens den Namen des Computers mit dem Wert **localhost** eingeben:

```
 <mta statServerAddress="localhost">
```

>[!IMPORTANT]
>
>Wenn dieses Feld nicht ausgefüllt ist, wird der **mta** nicht gestartet.

### Liste der zu verwendenden IP-Adressen {#list-of-ip-addresses-to-use}

Die Konfiguration für das Traffic-Management befindet sich im Element **mta/child/smtp** der Konfigurationsdatei.

Für jedes Element **IPAffinity** müssen Sie die IP-Adressen deklarieren, die für den Computer verwendet werden können.

Beispiel:

```
<IPAffinity localDomain="<domain>" name="default">
  <IP address="192.168.0.11" publicId="1" weight="5"/>
  <IP address="192.168.0.12" heloHost="revdns1.campaign.com" publicId="2" weight="5"/>
  <IP address="192.168.0.13" publicId="3" weight="1"/>
</IPAffinity>
```

Die Parameter lauten wie folgt:

* **address**: Dies ist die IP-Adresse des zu verwendenden MTA-Hostcomputers.
* **heloHost**: Diese Kennung stellt die IP-Adresse dar, wie sie vom SMTP-Server angezeigt wird.

* **publicId**: Diese Informationen sind nützlich, wenn eine IP-Adresse von mehreren Adobe Campaign **mtas** hinter einem NAT-Router freigegeben wird. Der Statistikserver verwendet diese Kennung, um die Verbindung zu speichern und Statistiken zwischen diesem Startpunkt und dem Zielserver zu senden.
* **weight**: ermöglicht die Bestimmung der relativen Häufigkeit der Verwendung der Adresse. Standardmäßig haben alle Adressen eine Gewichtung von 1.

>[!NOTE]
>
>In der Datei &quot;serverConf.xml&quot;müssen Sie überprüfen, ob eine IP einem einzelnen Helohost mit einer eindeutigen Kennung (public_id) entspricht. Er kann nicht mehreren Helohosts zugeordnet werden, was zu Problemen bei der Versanddrosselung führen kann.

Im vorherigen Beispiel werden die Adressen unter normalen Bedingungen wie folgt verteilt:

    * &quot;1&quot;: 5 / (5+5+1) = 45%
    * &quot;2&quot;: 5 / (5+5+1) = 45%
    * &quot;3&quot;: 1 / (5+5+1) = 10%

Wenn beispielsweise die erste Adresse nicht für einen bestimmten MX verwendet werden kann, werden Nachrichten wie folgt gesendet:

    * &quot;2&quot;: 5 / (5+1) = 83%
    * &quot;3&quot;: 1 / (5+1) = 17%

* **includeDomains**: ermöglicht die Reservierung dieser IP-Adresse für E-Mails, die zu einer bestimmten Domäne gehören. Dies ist eine Liste von Masken, die einen oder mehrere Platzhalter (&#39;&#42;&#39;) enthalten können. Wenn das Attribut nicht angegeben ist, können alle Domänen diese IP-Adresse verwenden.

  Beispiel: **includeDomains=&quot;wanadoo.com,orange.com,yahoo.&#42;&quot;**

* **excludeDomains**: Schließt eine Liste von Domänen für diese IP-Adresse aus. Dieser Filter wird nach dem Filter **includeDomains** angewendet.

  ![](assets/s_ncs_install_mta_ips.png)

## E-Mail-Versandoptimierung {#email-sending-optimization}

Die interne Architektur von Adobe Campaign **mta** wirkt sich auf die Konfiguration zur Optimierung des E-Mail-Versands aus. Im Folgenden finden Sie einige Tipps zur Verbesserung Ihrer Sendungen.

### Parameter maxWaitingMessages anpassen {#adjust-the-maxwaitingmessages-parameter}

Der Parameter **maxWaitingMessages** gibt die höchste Anzahl von Nachrichten an, die im Voraus von der **mtachild** vorbereitet wurden. Nachrichten werden erst dann aus dieser Liste gelöscht, wenn sie gesendet oder abgebrochen wurden.

Dieser Parameter ist sehr wichtig und besonders wichtig, wenn Nachrichten nicht nach Domain sortiert werden.

Sobald der Schwellenwert von **maxWorkingSetMb** (256) erreicht ist, stoppt der Versandserver den Nachrichtenversand. Die Leistung nimmt erheblich ab, bis der **mtachild** erneut gestartet wird. Um dieses Problem zu umgehen, können Sie entweder den Schwellenwert des Parameters **maxWorkingSetMb** erhöhen oder den Schwellenwert des Parameters **maxWaitingMessages** verringern.

Der Parameter **maxWorkingSetMb** wird empirisch berechnet, indem die maximale Nachrichtenanzahl mit der durchschnittlichen Nachrichtengröße multipliziert und das Ergebnis mit 2,5 multipliziert wird. Wenn beispielsweise eine Nachricht eine durchschnittliche Größe von 50 kB und der Parameter **maxWaitingMessages** gleich 1.000 hat, beträgt der verwendete Speicher durchschnittlich 125 MB.

### Anzahl der mtachild anpassen {#adjust-the-number-of-mtachild}

Die Anzahl der Kinder sollte nicht die Anzahl der Prozessoren in der Maschine (ca. 1000 Sitzungen). Es wird empfohlen, nicht mehr als 8 **mtachild** zu verwenden. Anschließend können Sie die Anzahl der Nachrichten pro **untergeordnetes Element** (**maxMsgPerChild**) erhöhen, um eine ausreichende Lebensdauer zu erreichen.

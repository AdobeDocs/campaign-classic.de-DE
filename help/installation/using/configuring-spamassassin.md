---
solution: Campaign Classic
product: campaign
title: SpamAssassin konfigurieren
description: SpamAssassin konfigurieren
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 0%

---


# SpamAssassin konfigurieren{#configuring-spamassassin}

>[!NOTE]
>
>Einige Konfigurationen können nur von der Adobe für Bereitstellungen ausgeführt werden, die von der Adobe gehostet werden. So können Sie beispielsweise auf die Konfigurationsdateien des Servers und der Instanz zugreifen. Weitere Informationen zu den verschiedenen Bereitstellungen finden Sie im Abschnitt [Hosting models](../../installation/using/hosting-models.md) oder auf [dieser Seite](../../installation/using/capability-matrix.md).

## Übersicht {#overview}

SpamAssassin ist eine Software zum Filtern unerwünschter E-Mails. In Verbindung mit dieser Software kann Adobe Campaign E-Mails eine Punktzahl zuweisen und feststellen, ob eine Nachricht vor dem Starten des Versands als unerwünscht angesehen werden kann. Dazu muss SpamAssassin auf dem bzw. den Anwendungsservern von Adobe Campaign installiert und konfiguriert sein und eine bestimmte Anzahl zusätzlicher Perl-Module benötigen.

Die Bereitstellung und Integration von SpamAssassin, wie in diesem Kapitel beschrieben, basieren auf der standardmäßigen Softwareinstallation, ebenso wie Filter- und Scoring-Regeln, die von SpamAssassin ohne Änderungen oder Optimierungen bereitgestellt werden. Score Attribution und Message Qualification basieren ausschließlich auf der Konfiguration von SpamAssassin Optionen und Filterregeln. Netzwerkadministratoren sind für die Anpassung an die Bedürfnisse ihrer Firma verantwortlich.

>[!IMPORTANT]
>
>Die Einstufung von E-Mails als unerwünscht durch SpamAssassin basiert ausschließlich auf Filter- und Bewertungsregeln.
>
>Diese Regeln müssen daher mindestens einmal täglich aktualisiert werden, damit Ihre SpamAssassin-Installation und ihre Integration in Adobe Campaign voll funktionsfähig sind und die Relevanz der Ergebnisse, die Ihren Versänden zugewiesen wurden, vor dem Versand gewährleistet ist.
>
>Für dieses Update ist der Serveradministrator verantwortlich, der SpamAssassin hostet.

Die Verwendung von SpamAssassin in Adobe Campaign gibt Aufschluss über das mögliche Verhalten von Mail-Servern, die SpamAssassin verwenden, wenn sie per Adobe Campaign gesendete E-Mails empfangen. Es ist jedoch möglich, dass die Mailserver von Internetanbietern oder Online-Mail-Servern die von Adobe Campaign gesendeten Nachrichten als unerwünscht betrachten.

Für die Bereitstellung von SpamAssassin und seinen Modulen in Perl sind Adobe Campaign-Anwendungsserver erforderlich, die über eine HTTP-Verbindung (TCP/80 flow) mit Internetzugang ausgestattet sind.

## Installieren auf einem Windows-Computer {#installing-on-a-windows-machine}

Gehen Sie wie folgt vor, um SpamAssassin unter Windows zu installieren und zu konfigurieren, um die Integration mit Adobe Campaign zu aktivieren:

1. SpamAssassin installieren
1. SpamAssassin in Adobe Campaign integrieren

### Installieren von SpamAssassin {#installing-spamassassin}

1. Stellen Sie eine Verbindung zum [Software-Distributionsportal](https://experience.adobe.com/downloads) mit Ihren Benutzeranmeldeinformationen her. Weitere Informationen zur Softwareverteilung finden Sie auf [dieser Seite](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).
1. Laden Sie die Datei **Neolane Spam Assassin (Windows-Installation) (2.0)** (neolane_spamassassin.2.0.zip) herunter.
1. Kopieren Sie diese Datei auf den Adobe Campaign-Server und dekomprimieren Sie sie.

   >[!NOTE]
   >
   >Sie können die Datei an jeder gewünschten Stelle entzippen, vorausgesetzt, der Pfad besteht aus einem der folgenden regulären Ausdruck: **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**. Der Installationspfad darf keine Leerzeichen enthalten.

1. Wechseln Sie zu der Datei, in der Sie die ZIP-Datei entpackt haben, und klicken Sie dann mit der Dublette auf die Datei **run_me.bat**, um das Installationsskript zu starten.

   Wenn eine Windows-Shell angezeigt wird und für einige Sekunden weiterhin angezeigt wird, warten Sie, bis die Installation und das Update abgeschlossen sind, und klicken Sie dann auf **Geben Sie** ein.

   Wenn die Windows-Shell nicht angezeigt wird oder nicht angezeigt wird, bevor sie sofort ausgeblendet wird, führen Sie die folgenden Schritte aus. Klicken Sie bei gedrückter Dublette auf die Datei **portableShell.bat**, um eine Windows-Shell anzuzeigen, und überprüfen Sie, ob der Shell-Pfad dem Ordner entspricht, in dem die Datei **spamassassin.zip** entpackt wurde. Ist dies nicht der Fall, greifen Sie mit dem Befehl **cd** darauf zu.

   Geben Sie **run_me.bat** ein und klicken Sie dann auf **Geben Sie** ein, um den Installations- und Aktualisierungsprozess Beginn. Der Vorgang gibt einen der folgenden Werte zurück, um das Ergebnis der Aktualisierung anzugeben.

   * **0**: eine Aktualisierung durchgeführt wurde.
   * **1**: Keine neue Aktualisierung verfügbar.
   * **2**: kein neues Update verfügbar.
   * **3**: Aktualisierung bei vorheriger Überprüfung fehlgeschlagen.
   * **4** oder mehr: ein Fehler aufgetreten ist.

1. Um zu überprüfen, ob die Installation von SpamAssassin erfolgreich war, verwenden Sie den GTUBE-Test (Generischer Test für nicht angeforderte Massen-E-Mail) mit folgendem Verfahren:

   1. Erstellen Sie eine Textdatei und speichern Sie sie unter **C:\TestSpamMail.txt**.
   1. Fügen Sie den folgenden Inhalt in die Datei ein:

      ```
      Subject: Test Spam Mail (GTUBE)
      Message-ID: <1010101@example.net>
      Date: MM-DD-YY
      From: Sender <sender@example.net>
      To: Recipient <recipient@example.net>
      Precedence: junk
      MIME-Version: 1.0
      Content-Type: text/plain; charset=us-ascii
      Content-Transfer-Encoding: 7bit
      
      XJS*C4JDBQADN1.NSBN3*2IDNEN*GTUBE-STANDARD-ANTI-UBE-TEST-EMAIL*C.34X
      ```

   1. Klicken Sie bei gedrückter Dublette auf die Datei **portableShell.bat**, um eine Windows Shell anzuzeigen, und starten Sie dann den folgenden Befehl (oder &quot;`<root>`&quot;bezeichnet den erstellten Ordner beim Entpacken der Datei **spamassassin.zip**):

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      Der Inhalt dieser Test-E-Mail Trigger eine Punktzahl von 1.000 Punkten von SpamAssassin. Dies bedeutet, dass es als unerwünscht erkannt wurde und dass die Installation erfolgreich war und voll funktionsfähig ist.

### Integrieren von SpamAssassin in Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. Bearbeiten Sie die Datei **`[INSTALL]/conf/serverConf.xml`**. Alle in **serverConf.xml** verfügbaren Parameter sind in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.
1. Ändern Sie den Wert des Attributs **spamCheck** elements&#39; **command** im Knoten **Web**. Führen Sie dazu den folgenden Befehl aus:

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >Alle Pfade müssen absolut sein.

   Beenden Sie den **[!UICONTROL Adobe Campaign]**-Dienst und Beginn ihn.

1. Um die Integration von SpamAssassin in Adobe Campaign zu überprüfen, verwenden Sie einen GTBUE-Test (Generischer Test für nicht angeforderte Massen-E-Mail):

   Klicken Sie mit der Dublette auf die Datei **portableshell.bat**. Dies Trigger die Anzeige einer Windows Shell. Führen Sie dann den folgenden Befehl aus:

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   Der Inhalt dieser Test-E-Mail-Trigger 1.000 von SpamAssassin zugewiesene Punkte. Dies bedeutet, dass sie als unerwünscht erkannt wurde und dass die Integration in Adobe Campaign erfolgreich war und voll funktionsfähig ist.

1. SpamAssassin-Filter- und Bewertungsregeln aktualisieren

   Für eine erste Aktualisierung der Filter- und Bewertungsregeln führen Sie Beginn **portableShell.bat** aus und führen Sie den folgenden Befehl aus:

   ```
   sa-update --no-gpg
   ```

   Um eine automatische Aktualisierung von Filter- und Bewertungsregeln auszuführen, verwenden Sie denselben Befehl in einer geplanten Aufgabe des Systems:

   ```
   sa-update --no-gpg
   ```

## Installieren auf einem Linux-Computer {#installing-on-a-linux-machine}

### Installationsschritte in Debian {#installation-steps-in-debian}

* Installieren Sie bei Bedarf Perl und SpamAssassin mit dem folgenden Befehl:

   ```
   apt-get install spamassassin libxml-writer-perl
   ```

* Ändern Sie in der Datei **serverConf.xml** (verfügbar in `/usr/local/[INSTALL]/nl6/conf/`) die Zeile **spamCheck** wie folgt:

   ```
   <spamCheck command="perl
   /usr/local/[NSTALL]/nl6/bin/spamcheck.pl"/>
   ```

### Installationsschritte in RHEL/CentOS {#installation-steps-in-rhel-centos}

Installieren Sie bei Bedarf Perl und stellen Sie die Pakete mithilfe von CPAN wieder her:

```
cpan Digest::SHA1
cpan HTML::Parser
cpan Net::DNS
cpan Mail::SPF 
cpan XML::LibXML
cpan XML::Writer
cpan Mail::SpamAssassin
```

### Aktualisieren von Filterregeln {#updating-filter-rules}

Filterregeln können mit dem Tool **sa-update** automatisch aktualisiert werden. Weitere Informationen finden Sie auf der offiziellen SpamAssassin-Website [http://spamassassin.apache.org/](http://spamassassin.apache.org/).

In Debian finden Aktualisierungen jeden Tag automatisch statt.

Wenn dies nicht der Fall ist (z. B. wenn Debian manuell installiert wird), erstellen Sie ein Skript, um Regelaktualisierungen zu automatisieren.

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

Fügen Sie dieses Skript mit dem folgenden Befehl in **crontab** ein:

```
crontab-e
```

### Leistungsoptimierung {#performance-optimization}

Um die Leistung unter Linux zu verbessern, bearbeiten Sie die Datei **/etc/spamassassin/local.cf** und fügen Sie am Dateiende die folgende Zeile hinzu:

```
dns_available no
```


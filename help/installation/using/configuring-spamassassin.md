---
product: campaign
title: SpamAssassin konfigurieren
description: SpamAssassin konfigurieren
feature: Installation, Instance Settings
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 1f1004e2-dcd2-4ec5-98ec-720c205646d5
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 1%

---

# SpamAssassin konfigurieren{#configuring-spamassassin}



>[!NOTE]
>
>Einige Konfigurationen können nur von Adobe für Bereitstellungen durchgeführt werden, die von Adobe gehostet werden. Beispielsweise um auf die Server- und Instanzkonfigurationsdateien zuzugreifen. Weitere Informationen zu den verschiedenen Implementierungen finden Sie im Abschnitt [Hosting-Modelle](../../installation/using/hosting-models.md) oder [diese Seite](../../installation/using/capability-matrix.md).

## Übersicht {#overview}

SpamAssassin ist eine Software zur Filterung unerwünschter E-Mails. In Verbindung mit dieser Software kann Adobe Campaign E-Mails eine Punktzahl zuweisen und feststellen, ob eine Nachricht vor dem Start des Versands wahrscheinlich als unerwünscht erachtet wird. Dazu muss SpamAssassin auf den Anwendungsservern von Adobe Campaign installiert und konfiguriert werden und eine bestimmte Anzahl zusätzlicher Perl-Module erfordern.

Die Implementierung und Integration von SpamAssassin, wie in diesem Kapitel beschrieben, basieren auf der standardmäßigen Software-Installation, ebenso wie Filter- und Scoring-Regeln, die von SpamAssassin ohne Änderungen oder Optimierungen bereitgestellt werden. Die Zuordnung der Punktzahl und die Qualifizierung der Nachricht basieren ausschließlich auf der Konfiguration der SpamAssassin-Optionen und den Filterregeln. Netzwerkadministratoren sind für die Anpassung an die Anforderungen ihres Unternehmens verantwortlich.

>[!IMPORTANT]
>
>Die Einstufung von E-Mails als unerwünscht durch SpamAssassin basiert ausschließlich auf Filter- und Scoring-Regeln.
>
>Diese Regeln müssen daher mindestens einmal täglich aktualisiert werden, damit Ihre SpamAssassin-Installation und ihre Integration in Adobe Campaign voll funktionsfähig sind und die Relevanz der für Ihre Sendungen zugewiesenen Bewertungen vor dem Versand gewährleistet ist.
>
>Für diese Aktualisierung ist der Serveradministrator verantwortlich, der SpamAssassin hostet.

Die Verwendung von SpamAssassin in Adobe Campaign gibt Aufschluss über das mögliche Verhalten von E-Mail-Servern, die SpamAssassin verwenden, wenn sie von Adobe Campaign gesendete E-Mails erhalten. Es ist jedoch möglich, dass die Mailserver von Internetanbietern oder Online-Mail-Servern die von Adobe Campaign gesendeten Nachrichten als unerwünscht betrachten.

Die Bereitstellung von SpamAssassin und seinen Modulen in Perl erfordert Adobe Campaign-Anwendungsserver, die über eine HTTP-Verbindung (TCP/80-Fluss) mit Internetzugang ausgestattet sind.

## Installieren auf einem Windows-Computer {#installing-on-a-windows-machine}

Gehen Sie wie folgt vor, um SpamAssassin unter Windows zu installieren und zu konfigurieren, um die Integration mit Adobe Campaign zu ermöglichen:

1. SpamAssassin installieren
1. SpamAssassin in Adobe Campaign integrieren

### SpamAssassin installieren {#installing-spamassassin}

1. Stellen Sie eine Verbindung zum [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html) Verwendung Ihrer Benutzeranmeldeinformationen. Weitere Informationen zur Softwareverteilung finden Sie unter [diese Seite](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=de).
1. Laden Sie die **Neolane Spam Assassin (Windows-Installation) (2.0)** Datei (neolane_spamassassin.2.0.zip).
1. Kopieren Sie diese Datei auf den Adobe Campaign-Server und dekomprimieren Sie sie dann.

   >[!NOTE]
   >
   >Sie können die Datei an allen Stellen dekomprimieren, an denen Sie möchten, vorausgesetzt, der Pfad besteht aus einem der folgenden Zeichen für reguläre Ausdrücke: **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**. Der Installationspfad darf keine Leerzeichen enthalten.

1. Gehen Sie zur Datei, in der Sie die Datei entpackt haben, und doppelklicken Sie auf die **run_me.bat** -Datei, um das Installationsskript zu starten.

   Wenn eine Windows Shell angezeigt wird und einige Sekunden lang weiterhin angezeigt wird, warten Sie, bis die Installation und Aktualisierung abgeschlossen sind, und klicken Sie auf **Eingabe**.

   Wenn die Windows Shell nicht angezeigt wird oder nicht angezeigt wird, bevor sie sofort verschwindet, führen Sie die folgenden Schritte aus, indem Sie auf die **portableShell.bat** -Datei, um eine Windows Shell anzuzeigen und zu überprüfen, ob der Shell-Pfad dem Ordner entspricht, in dem die **spamassassassin.zip** wurde entpackt. Wenn dies nicht der Fall ist, greifen Sie mithilfe der **cd** Befehl.

   Eingabe **run_me.bat** Klicken Sie dann auf **Eingabe** um den Installations- und Aktualisierungsprozess zu starten. Der Vorgang gibt einen der folgenden Werte zurück, um das Ergebnis der Aktualisierung anzuzeigen.

   * **0**: Aktualisierung durchgeführt.
   * **1**: Es ist kein neues Update verfügbar.
   * **2**: keine neue Aktualisierung verfügbar.
   * **3**: Aktualisierung schlug während der vorherigen Überprüfung fehl.
   * **4** oder mehr: Es ist ein Fehler aufgetreten.

1. Um sicherzustellen, dass die SpamAssassin-Installation erfolgreich war, verwenden Sie den GTUBE-Test (Generischer Test für nicht angeforderte Massen-E-Mail) wie folgt:

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

   1. Doppelklicken Sie auf die **portableShell.bat** -Datei, um eine Windows-Shell anzuzeigen, und starten Sie dann den folgenden Befehl (oder &quot;`<root>`&quot; bezeichnet den erstellten Ordner beim Entpacken der  **spamassassassin.zip** Datei):

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      Der Inhalt dieser Test-E-Mail-Trigger enthält eine Punktzahl von 1.000 Punkten von SpamAssassin. Dies bedeutet, dass es als unerwünscht erkannt wurde und dass die Installation erfolgreich war und voll funktionsfähig ist.

### Integrieren von SpamAssassin in Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. Bearbeiten Sie die **`[INSTALL]/conf/serverConf.xml`** -Datei. Alle in der **serverConf.xml** in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md).
1. Ändern Sie den Wert der **spamCheck** elements&#39; **command** -Attribut im **Web** Knoten. Führen Sie dazu den folgenden Befehl aus:

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >Alle Pfade müssen absolut sein.

   Stoppen und starten Sie die **[!UICONTROL Adobe Campaign]** -Dienst.

1. Um die Integration von SpamAssassin in Adobe Campaign zu überprüfen, verwenden Sie einen GTBUE-Test (Generischer Test für nicht angeforderte Massen-E-Mail):

   Doppelklicken Sie auf die **portableshell.bat** -Datei. Dadurch wird die Anzeige einer Windows Shell Trigger. Führen Sie dann den folgenden Befehl aus:

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   Der Inhalt dieser Test-E-Mail-Trigger 1.000 von SpamAssassin zugewiesene Punkte. Dies bedeutet, dass sie als unerwünscht erkannt wurde und dass die Integration in Adobe Campaign erfolgreich war und voll funktionsfähig ist.

1. Aktualisierung der Filter- und Scoring-Regeln für SpamAssassin

   Für eine erste Aktualisierung der Filter- und Scoring-Regeln starten Sie **portableShell.bat** und führen Sie den folgenden Befehl aus:

   ```
   sa-update --no-gpg
   ```

   Um eine automatische Aktualisierung von Filter- und Scoring-Regeln auszuführen, verwenden Sie denselben Befehl in einer geplanten Systemaufgabe:

   ```
   sa-update --no-gpg
   ```

## Installieren auf einem Linux-Computer {#installing-on-a-linux-machine}

### Installationsschritte in Debian {#installation-steps-in-debian}

* Installieren Sie bei Bedarf Perl und SpamAssassin mit dem folgenden Befehl:

  ```
  apt-get install spamassassin libxml-writer-perl
  ```

* Im **serverConf.xml** Datei (verfügbar in `/usr/local/[INSTALL]/nl6/conf/`), ändern Sie die **spamCheck** folgende Zeile:

  ```
  <spamCheck command="perl
  /usr/local/[NSTALL]/nl6/bin/spamcheck.pl"/>
  ```

### Installationsschritte in RHEL/CentOS {#installation-steps-in-rhel-centos}

Installieren Sie bei Bedarf Perl und rufen Sie die Pakete mithilfe von CPAN ab:

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

Filterregeln können automatisch mit dem **sa-update** -Tool. Siehe offizielle SpamAssassin-Website [https://spamassassin.apache.org/](https://spamassassin.apache.org/) für weitere Informationen.

In Debian finden Aktualisierungen automatisch jeden Tag statt.

Wenn dies nicht der Fall ist (z. B. wenn Debian manuell installiert wird), erstellen Sie ein Skript, um Regelaktualisierungen zu automatisieren.

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

Dieses Skript einfügen in **crontab** mit dem folgenden Befehl:

```
crontab-e
```

### Leistungsoptimierung {#performance-optimization}

Um die Leistung unter Linux zu verbessern, bearbeiten Sie die **/etc/spamassassin/local.cf** und fügen Sie die folgende Zeile am Ende der Datei hinzu:

```
dns_available no
```

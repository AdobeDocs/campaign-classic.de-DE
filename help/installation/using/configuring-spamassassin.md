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
>Einige Konfigurationen können nur von Adobe für Bereitstellungen durchgeführt werden, die von Adobe gehostet werden. Beispielsweise für den Zugriff auf die Konfigurationsdateien des Servers und der Instanz. Weitere Informationen zu den verschiedenen Bereitstellungen finden Sie im Abschnitt [Hosting](../../installation/using/hosting-models.md) oder auf [dieser Seite](../../installation/using/capability-matrix.md).

## Übersicht {#overview}

SpamAssassin ist eine Software zum Filtern unerwünschter E-Mails. In Verbindung mit dieser Software kann Adobe Campaign E-Mails eine Punktzahl zuweisen und bestimmen, ob eine Nachricht vor dem Start des Versands als unerwünscht eingestuft wird. Dazu muss SpamAssassin auf den Anwendungsservern von Adobe Campaign installiert und konfiguriert werden und benötigt eine gewisse Anzahl zusätzlicher Perl-Module.

Die Bereitstellung und Integration von SpamAssassin, wie in diesem Kapitel beschrieben, basieren auf der Standardsoftware-Installation sowie auf Filter- und Bewertungsregeln, die von SpamAssassin ohne Änderungen oder Optimierungen bereitgestellt werden. Die Punktzahl-Attribution und die Nachrichtenqualifizierung basieren ausschließlich auf der Konfiguration von SpamAssassin-Optionen und auf Filterregeln. Netzwerkadministratoren sind dafür verantwortlich, sie an die Anforderungen ihres Unternehmens anzupassen.

>[!IMPORTANT]
>
>Die Qualifizierung von E-Mails als unerwünscht durch SpamAssassin basiert ausschließlich auf Filter- und Bewertungsregeln.
>
>Diese Regeln müssen daher mindestens einmal täglich aktualisiert werden, damit Ihre SpamAssassin-Installation und ihre Integration in Adobe Campaign voll funktionsfähig sind und die Relevanz der Ihren Sendungen vor dem Versand zugewiesenen Bewertungen gewährleistet ist.
>
>Dieses Update liegt in der Verantwortung des Serveradministrators, der SpamAssassin hostet.

Die Verwendung von SpamAssassin in Adobe Campaign liefert einen Hinweis auf das mögliche Verhalten von E-Mail-Servern, die SpamAssassin verwenden, wenn sie von Adobe Campaign gesendete E-Mails erhalten. Es ist jedoch möglich, dass die Mailserver von Internetanbietern oder Online-Mailservern die von Adobe Campaign gesendeten Nachrichten weiterhin als unerwünscht betrachten.

Für die Bereitstellung von SpamAssassin und seinen Modulen in Perl sind Adobe Campaign-Anwendungsserver erforderlich, die über eine HTTP-Verbindung (TCP/80-Fluss) mit Internetzugang ausgestattet sind.

## Installieren auf einem Windows-Computer {#installing-on-a-windows-machine}

Gehen Sie wie folgt vor, um SpamAssassin unter Windows zu installieren und zu konfigurieren, um die Integration mit Adobe Campaign zu aktivieren:

1. SpamAssassin installieren
1. SpamAssassin in Adobe Campaign integrieren

### Installieren von SpamAssassin {#installing-spamassassin}

1. Stellen Sie mithilfe Ihrer Benutzeranmeldeinformationen eine Verbindung [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html)Portal) her. Weitere Informationen zur Software-Verteilung finden [ auf dieser Seite ](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=de).
1. Laden Sie die Datei **Neolane Spam Assassin (Windows-Installation) (2.0)** (neolane_spamassassin.2.0.zip) herunter.
1. Kopieren Sie diese Datei auf den Adobe Campaign-Server und entpacken Sie sie dann.

   >[!NOTE]
   >
   >Sie können die Datei an beliebiger Stelle entpacken, vorausgesetzt, der Pfad besteht aus einem der folgenden Zeichen für reguläre Ausdrücke: **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**. Der Installationspfad darf keine Leerzeichen enthalten.

1. Gehen Sie zu der Datei, in die Sie die Datei entpackt haben, und doppelklicken Sie dann auf die Datei **run_me.bat**, um das Installationsskript zu starten.

   Wenn eine Windows Shell angezeigt wird und noch einige Sekunden angezeigt wird, warten Sie, bis die Installation und das Update abgeschlossen sind, und klicken Sie dann auf **Enter**.

   Wenn die Windows Shell nicht angezeigt wird oder nicht angezeigt wird, bevor sie sofort ausgeblendet wird, führen Sie die folgenden Schritte aus, doppelklicken Sie auf die Datei **portableShell.bat**, um eine Windows Shell anzuzeigen, und überprüfen Sie, ob der Shell-Pfad dem Ordner entspricht, in dem die Datei **spamassassin.zip** entpackt wurde. Wenn dies nicht der Fall ist, greifen Sie mit dem Befehl **cd** darauf zu.

   Geben Sie **run_me.bat** ein und klicken Sie auf **Enter**, um den Installations- und Aktualisierungsprozess zu starten. Der Vorgang gibt einen der folgenden Werte zurück, um das Ergebnis der Aktualisierung anzugeben.

   * **0**: Es wurde eine Aktualisierung durchgeführt.
   * **1**: Keine neue Aktualisierung verfügbar.
   * **2**: Kein neues Update verfügbar.
   * **3**: Update ist bei der vorherigen Überprüfung fehlgeschlagen.
   * **4** oder mehr: Ein Fehler ist aufgetreten.

1. Um zu überprüfen, ob die SpamAssassin-Installation erfolgreich war, verwenden Sie den GTUBE-Test (Generic Test for Unsolicited Bulk Email) mit dem folgenden Verfahren:

   1. C:\TestSpamMail.txt Erstellen Sie eine Textdatei und speichern Sie sie unter ****.
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

   1. Doppelklicken Sie auf die Datei **portableShell.bat**, um eine Windows Shell anzuzeigen, und starten Sie dann den folgenden Befehl (oder &quot;`<root>`&quot; bezeichnet den erstellten Ordner beim Entpacken der Datei **spamassassin.zip**):

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      Der Inhalt dieser Test-E-Mail Trigger eine Punktzahl von 1.000 von SpamAssassin. Dies bedeutet, dass es als unerwünscht erkannt wurde und dass die Installation erfolgreich war und voll funktionsfähig ist.

### Integrieren von SpamAssassin in Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. Bearbeiten Sie die **`[INSTALL]/conf/serverConf.xml`**. Alle in der Datei **serverConf.xml** verfügbaren Parameter werden in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.
1. Ändern Sie den Wert des **spamCheck**-Elements **command** im **Web**-Knoten. Führen Sie dazu den folgenden Befehl aus:

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >Alle Pfade müssen absolut sein.

   Beenden und starten Sie den **[!UICONTROL Adobe Campaign]**-Service.

1. Um die Integration von SpamAssassin in Adobe Campaign zu überprüfen, verwenden Sie einen GTBUE-Test (generischer Test für unerwünschte Massen-E-Mails):

   Doppelklicken Sie auf die Datei **portableshell.bat**. Dadurch wird die Anzeige einer Windows Shell Trigger. Führen Sie dann den folgenden Befehl aus:

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   Der Inhalt dieser Test-E-Mail Trigger 1.000 von SpamAssassin zugewiesene Punkte. Dies bedeutet, dass sie als unerwünscht erkannt wurde und dass die Integration in Adobe Campaign erfolgreich war und voll funktionsfähig ist.

1. SpamAssassin-Filter- und Bewertungsregeln aktualisieren

   Um eine erste Aktualisierung der Filter- und Bewertungsregeln durchzuführen, starten Sie **portableShell.bat** und führen Sie den folgenden Befehl aus:

   ```
   sa-update --no-gpg
   ```

   Verwenden Sie in einer geplanten Systemaufgabe denselben Befehl, um eine automatische Aktualisierung der Filter- und Bewertungsregeln durchzuführen:

   ```
   sa-update --no-gpg
   ```

## Installieren auf einem Linux-Computer {#installing-on-a-linux-machine}

### Installationsschritte in Debian {#installation-steps-in-debian}

* Installieren Sie bei Bedarf Perl und SpamAssassin mit dem folgenden Befehl:

  ```
  apt-get install spamassassin libxml-writer-perl
  ```

* Ändern Sie in der **serverConf.xml**-Datei (verfügbar in `/usr/local/[INSTALL]/nl6/conf/`) die Zeile **spamCheck** wie folgt:

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

### Filterregeln aktualisieren {#updating-filter-rules}

Filterregeln können automatisch mit dem Tool **sa-update** aktualisiert werden. Weitere Informationen finden Sie auf der offiziellen SpamAssassin](https://spamassassin.apache.org/)Website [https://spamassassin.apache.org/.

In Debian werden Aktualisierungen automatisch jeden Tag durchgeführt.

Wenn dies nicht der Fall ist (zum Beispiel wenn Debian manuell installiert wird), erstellen Sie ein Skript, um Regelaktualisierungen zu automatisieren.

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

Fügen Sie dieses Skript mithilfe **folgenden Befehls in** crontab“ ein:

```
crontab-e
```

### Leistungsoptimierung {#performance-optimization}

Um die Leistung in Linux zu verbessern, bearbeiten Sie die Datei **/etc/spamassassin/local.cf** und fügen Sie am Ende der Datei die folgende Zeile hinzu:

```
dns_available no
```

---
solution: Campaign Classic
product: campaign
title: Migration in Linux zu Adobe Campaign v7
description: Migration in Linux zu Adobe Campaign v7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1890'
ht-degree: 1%

---


# Migration in Linux zu Adobe Campaign v7{#migrating-in-linux-for-adobe-campaign-v}

## Allgemeines Verfahren {#general-procedure}

Unter Linux werden die folgenden Migrationsschritte ausgeführt:

1. Dienste beenden: siehe [Dienstunterbrechung](#service-stop).
1. Datenbank speichern: Siehe Datenbank und vorhandene Installation [sichern](#back-up-the-database-and-the-existing-installation).
1. Deinstallieren Sie ältere Adobe Campaign-Versionspakete: finden Sie unter [Deinstallieren von Adobe Campaign-Paketen](#uninstalling-adobe-campaign-previous-version-packages)früherer Versionen.
1. Plattform migrieren: Siehe [Bereitstellen von Adobe Campaign v7](#deploying-adobe-campaign-v7).
1. Beginn-Dienst: finden Sie unter Dienste [neu starten](#re-starting-services).

## Dienstunterbrechung {#service-stop}

Beenden Sie zunächst alle Prozesse mit Zugriff auf die Datenbank auf allen betroffenen Computern.

1. Melden Sie sich als **Stamm** an.
1. Alle Server, die das Umleitungsmodul (**webmdl** -Dienst) verwenden, müssen gestoppt werden. Führen Sie für Apache den folgenden Befehl aus:

   ```
   /etc/init.d/apache2 stop
   ```

1. Melden Sie sich erneut als **root** an.
1. Beenden Sie die Dienste der vorherigen Adobe Campaign-Version auf allen Servern.

   ```
   /etc/init.d/nlserver6 stop
   ```

   Wenn Sie von Version 5.11 migrieren, führen Sie den folgenden Befehl aus:

   ```
   /etc/init.d/nlserver5 stop
   ```

1. Stellen Sie sicher, dass die Adobe Campaign-Dienste auf jedem Server beendet werden.

   ```
   ps waux | grep nlserver
   ```

   Die Liste aktiver Prozesse wird zusammen mit ihrer ID (PID) angezeigt.

1. Wenn ein oder mehrere Adobe Campaign-Prozesse nach einigen Minuten noch aktiv oder blockiert sind, beenden Sie sie.

   ```
   killall nlserver
   ```

1. Wenn einige Prozesse nach einigen Minuten noch aktiv sind, können Sie sie mithilfe des Befehls zum Schließen zwingen:

   ```
   killall -9 nlserver
   ```

## Datenbank und vorhandene Installation sichern {#back-up-the-database-and-the-existing-installation}

Die Vorgehensweise hängt von der vorherigen Version Ihres Adobe Campaigns ab.

### Migration von Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Erstellen Sie eine Sicherung der Adobe Campaign-Datenbank.
1. Melden Sie sich als **neolane** an und erstellen Sie mithilfe des folgenden Befehls eine Sicherung des Ordners **nl5** :

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >Als Vorsichtsmaßnahme empfehlen wir, den Ordner **nl5.back** zu zippen und ihn an einem anderen sicheren Speicherort als dem Server zu speichern.

1. Bearbeiten Sie die Datei **config-`<instance name>`.xml** (im Ordner **nl5.back** ), um die **Dateien mta**, **wfserver**, **** statusw. zu verhindern. Dienste automatisch starten. Ersetzen Sie beispielsweise **autoStart** durch **_autoStart** (immer noch als **neolane**).

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

### Migration von Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Erstellen Sie eine Sicherung der Adobe Campaign-Datenbank.
1. Melden Sie sich als **neolane** an und erstellen Sie mithilfe des folgenden Befehls eine Sicherung des Ordners **nl6** :

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Als Vorsichtsmaßnahme empfehlen wir, den Ordner **nl6.back** zu komprimieren und ihn an einem anderen sicheren Speicherort als dem Server zu speichern.

1. Bearbeiten Sie **config-`<instance name>`.xml** (im Ordner **nl6.back** ), um die **Dateien mta**, **wfserver**, **** statusw. zu verhindern. Dienste automatisch starten. Ersetzen Sie beispielsweise **autoStart** durch **_autoStart** (immer noch als **Adobe Campaign**).

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

### Migration von Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6-1}

1. Erstellen Sie eine Sicherung der Adobe Campaign-Datenbank.
1. Melden Sie sich als **neolane** an und erstellen Sie mithilfe des folgenden Befehls eine Sicherung des Ordners **nl6** :

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Als Vorsichtsmaßnahme empfehlen wir, den Ordner **nl6.back** zu komprimieren und ihn an einem anderen sicheren Speicherort als dem Server zu speichern.

## Deinstallieren von Adobe Campaign-Versionspaketen {#uninstalling-adobe-campaign-previous-version-packages}

Die Vorgehensweise hängt von der vorherigen Version Ihres Adobe Campaigns ab.

### Deinstallieren von Adobe Campaign v5-Paketen {#uninstalling-adobe-campaign-v5-packages}

1. Melden Sie sich als **Stamm** an.
1. Identifizieren Sie die Adobe Campaign-Pakete, die mit dem folgenden Befehl installiert wurden.

   * In **Debian**:

      ```
      dpkg -l | grep nl
      ```

      Die Liste der installierten Pakete wird angezeigt:

      ```
      ii  nlserver5                       5762                     nlserver5-5762
      ii  nlthirdparty5                   5660                     nlthirdparty5-5660
      ```

   * In **Red Hat**:

      ```
      rpm -qa | grep nl
      ```

1. Deinstallieren Sie Adobe Campaign v5-Pakete.

   * In **Debian**:

      ```
      dpkg --purge nlserver5 nlthirdparty5
      ```

   * In **Red Hat**:

      ```
      rprm -ev nlserver5 nlthirdparty5
      ```

### Deinstallieren von Adobe Campaign v6-Paketen {#uninstalling-adobe-campaign-v6-packages}

Dieser Abschnitt zeigt, wie Adobe Campaign-Pakete der Version 6.02 oder 6.1 deinstalliert werden.

1. Melden Sie sich als **Stamm** an.
1. Identifizieren Sie die Adobe Campaign-Pakete, die mit dem folgenden Befehl installiert wurden.

   * In **Debian**:

      ```
      dpkg -l | grep nl
      ```

      Die Liste der installierten Pakete wird angezeigt:

      ```
      ii  nlserver6                       XXXX                     nlserver6-XXXX
      ii  nlthirdparty6                   XXXX                     nlthirdparty6-XXXX
      ```

   * In **Red Hat**:

      ```
      rpm -qa | grep nl
      ```

1. Deinstallieren Sie Adobe Campaign v6-Pakete.

   * In **Debian**:

      ```
      dpkg --purge nlserver6 nlthirdparty6
      ```

   * In **Red Hat**:

      ```
      rprm -ev nlserver6 nlthirdparty6
      ```

## Bereitstellen von Adobe Campaign v7 {#deploying-adobe-campaign-v7}

Die Vorgehensweise hängt von der vorherigen Version Ihres Adobe Campaigns ab.

### Migration von Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-1}

Die Bereitstellung von Adobe Campaign erfolgt in zwei Schritten:

* Installieren von Adobe Campaign v7-Paketen: dieser Vorgang muss auf jedem Server ausgeführt werden.
* Nach der Aktualisierung: Dieser Befehl muss auf jeder Instanz gestartet werden.

Gehen Sie wie folgt vor, um Adobe Campaign bereitzustellen:

1. Installieren Sie die neuesten Adobe Campaign v7-Pakete mit dem folgenden Befehl:

   * In **Debian**:

      ```
      dpkg -i nlserver6-XXXX-linux-2.6-intel.deb
      ```

   * In **Red Hat**:

      ```
      rpm -Uvh nlserver6-XXXX-0.x86_64.rpm
      ```
   >[!IMPORTANT]
   >
   >Sie müssen die Pakete erfolgreich installieren, bevor Sie mit dem nächsten Schritt fortfahren können.

   >[!NOTE]
   >
   >Beim Migrieren von Version 5.11 wird Adobe Campaign standardmäßig im Ordner **/usr/local/neolane/nl6/** installiert.
   >
   >Nachdem die Pakete installiert wurden, wird die folgende Meldung angezeigt: **Die Option &quot;WdbcTimeZone&quot;fehlt**. Das ist normal.

1. Um das Programm für die Installation der Clientkonsole verfügbar zu machen, kopieren Sie es in den Installationsordner des Adobe Campaigns:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Weitere Informationen zur Installation von Adobe Campaign unter Linux finden Sie in [diesem Abschnitt](../../installation/using/installing-campaign-standard-packages.md).

1. Ändern Sie die **.bashrd** -Datei, die dem **neolanen** Benutzer entspricht. Melden Sie sich als **neolane** an und führen Sie den folgenden Befehl aus:

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >Wenn Sie sich als **Neolan** anmelden, wird die folgende Meldung angezeigt: **nl5/env.sh : Keine solche Datei oder kein Verzeichnis**. Das ist normal.

   Ersetzen Sie am Ende der Datei **nl5/env.sh** durch **nl6/env.sh**.

1. Melden Sie sich als **Stamm** an und bereiten Sie die Instanz mithilfe der folgenden Befehle vor:

   ```
   /etc/init.d/nlserver6 start   
   Starting nlserver6: [  OK  ]
   ```

   ```
   /etc/init.d/nlserver6 stop
   Stopping nlserver6: [  OK  ]
   ```

   >[!NOTE]
   >
   >Mit diesen Befehlen können Sie das interne Dateisystem des Adobe Campaigns v6 erstellen: **Ordner conf** (mit den Dateien **config-default.xml** und **serverConf.xml** ), **var** .

1. Wechseln Sie zum Sicherungsordner **nl5.back** und kopieren Sie die Konfigurationsdateien und Unterordner jeder Instanz (überschreiben). Melden Sie sich als **neolane** an und führen Sie den folgenden Befehl aus:

   >[!IMPORTANT]
   >
   >Kopieren Sie für den ersten Befehl unten nicht die Datei &quot; **config-default.xml** &quot;.

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. Wenden Sie in den Adobe Campaign-Dateien v7 **serverConf.xml** und **config-default.xml** die spezifischen Konfigurationen an, die Sie für Adobe Campaign v5 hatten. Verwenden Sie für die Datei &quot; **serverConf.xml** &quot;die Datei &quot; **nl5/conf/serverConf.xml.diff** &quot;.

   >[!NOTE]
   >
   >Stellen Sie bei Berichte-Konfigurationen von Adobe Campaign v5 bis Adobe Campaign v7 sicher, dass die Pfade zu den physischen Ordnern zu Adobe Campaign v7 und nicht zu Adobe Campaign v5 führen.

1. Da Migration keine allgemeine Installation ist, müssen Sie den Neustart des **Trackinglogd** -Dienstes erzwingen. Öffnen Sie dazu die **Datei &quot;nl6/conf/config-default.xml** &quot;und stellen Sie sicher, dass der **TrackingLogd** -Dienst aktiviert ist (nur auf dem/den Tracking-/Weiterleitungsserver):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Wenn der **trackinglogd** -Dienst nicht auf dem Tracking-Server gestartet wird, werden keine Verfolgungsinformationen weitergeleitet.

1. Laden Sie die Adobe Campaign v7-Konfiguration mit dem folgenden Befehl neu:

   ```
   nlserver config -reload
   ```

1. Beginn des Nachbearbeitungsprozesses mit dem folgenden Befehl (immer noch als **Neolan**):

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!IMPORTANT]
   >
   >Sie müssen angeben, welche Zeitzone als Referenz während der Nachrüstung verwendet werden soll (unter Verwendung der Option **-timezone** ). In diesem Fall verwenden wir die Zeitzone Europa/Paris **: &quot;Europa/Paris&quot;**.

   >[!NOTE]
   >
   >Wir empfehlen dringend, Ihre Basis auf &quot;multi timezone&quot; zu aktualisieren. Weitere Informationen zu Zeitzonenoptionen finden Sie im Abschnitt [Zeitzonen](../../migration/using/general-configurations.md#time-zones) .

>[!IMPORTANT]
>
>Beginn-Adobe Campaign-Dienste noch nicht: Änderungen müssen noch in Apache vorgenommen werden.

### Migration von Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-1}

Die Bereitstellung von Adobe Campaign erfolgt in zwei Schritten:

* Installieren von Adobe Campaign v7-Paketen: dieser Vorgang muss auf jedem Server ausgeführt werden.
* Nach der Aktualisierung: Dieser Befehl muss auf jeder Instanz gestartet werden.

Gehen Sie wie folgt vor, um Adobe Campaign bereitzustellen:

1. Installieren Sie die neuesten Adobe Campaign v7-Pakete mit dem folgenden Befehl:

   * In **Debian**:

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * In **Red Hat**:

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >Sie müssen die Pakete erfolgreich installieren, bevor Sie mit dem nächsten Schritt fortfahren können.

   >[!NOTE]
   >
   >Adobe Campaign v7 wird standardmäßig im selben Ordner wie Adobe Campaign v6.02 installiert: **/usr/local/neolane/nl6/**.

1. Um das Programm für die Installation der Clientkonsole verfügbar zu machen, kopieren Sie es in den Installationsordner des Adobe Campaigns:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Weitere Informationen zur Installation von Adobe Campaign unter Linux finden Sie in [diesem Abschnitt](../../installation/using/installing-campaign-standard-packages.md).

1. Da Migration keine allgemeine Installation ist, müssen Sie den Neustart des **Trackinglogd** -Dienstes erzwingen. Öffnen Sie dazu die **Datei &quot;nl6/conf/config-default.xml** &quot;und stellen Sie sicher, dass der **TrackingLogd** -Dienst aktiviert ist (nur auf dem/den Tracking-/Weiterleitungsserver):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Wenn der **trackinglogd** -Dienst nicht auf dem Tracking-Server gestartet wird, werden keine Verfolgungsinformationen weitergeleitet.

1. Wechseln Sie zum Sicherungsordner **nl6.back** und kopieren Sie die Konfigurationsdateien und Unterordner jeder Instanz (überschreiben). Melden Sie sich als **neolane** an und führen Sie den folgenden Befehl aus:

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Laden Sie die Adobe Campaign v7-Konfiguration mit dem folgenden Befehl neu:

   ```
   nlserver config -reload
   ```

1. Beginn des Nachbearbeitungsprozesses mit dem folgenden Befehl (immer noch als **Neolan**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

   >[!NOTE]
   >
   >Der &quot;multi timezone&quot;-Modus war nur in Version 6.02 für PostgreSQL-Datenbankmaschinen verfügbar. Es ist jetzt unabhängig von der verwendeten Version der Datenbank-Engine verfügbar. Wir empfehlen dringend, Ihre Basis auf &quot;multi timezone&quot; zu aktualisieren. Weitere Informationen zu Zeitzonenoptionen finden Sie im Abschnitt [Zeitzonen](../../migration/using/general-configurations.md#time-zones) .

### Migration von Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-1}

Die Bereitstellung von Adobe Campaign erfolgt in zwei Schritten:

* Installieren von Adobe Campaign v7-Paketen: dieser Vorgang muss auf jedem Server ausgeführt werden.
* Nach der Aktualisierung: Dieser Befehl muss auf jeder Instanz gestartet werden.

Gehen Sie wie folgt vor, um Adobe Campaign bereitzustellen:

1. Installieren Sie die neuesten Adobe Campaign v7-Pakete mit dem folgenden Befehl:

   * In **Debian**:

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * In **Red Hat**:

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >Sie müssen die Pakete erfolgreich installieren, bevor Sie mit dem nächsten Schritt fortfahren können.

   >[!NOTE]
   >
   >Adobe Campaign v7 wird standardmäßig im Ordner **/usr/local/neolane/nl6/** installiert.

1. Um das Programm für die Installation der Clientkonsole verfügbar zu machen, kopieren Sie es in den Installationsordner des Adobe Campaigns:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Weitere Informationen zur Installation von Adobe Campaign unter Linux finden Sie in [diesem Abschnitt](../../installation/using/installing-campaign-standard-packages.md).

1. Wechseln Sie zum Sicherungsordner **nl6.back** und kopieren Sie die Konfigurationsdateien und Unterordner jeder Instanz (überschreiben). Melden Sie sich als **neolane** an und führen Sie den folgenden Befehl aus:

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Laden Sie die Adobe Campaign v7-Konfiguration mit dem folgenden Befehl neu:

   ```
   nlserver config -reload
   ```

1. Beginn des Nachbearbeitungsprozesses mit dem folgenden Befehl (immer noch als **Neolan**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

## Migrieren des Umleitungsservers (Apache) {#migrating-the-redirection-server--apache-}

>[!NOTE]
>
>Dieser Abschnitt gilt nur bei der Migration von Adobe Campaign v5.11.

Zum gegenwärtigen Zeitpunkt muss der Apache gestoppt werden. Siehe: [Dienstunterbrechung](#service-stop).

1. Melden Sie sich als **Stamm** an.
1. Ändern Sie die Apache-Umgebung, damit sie mit dem **nl6** -Ordner verknüpft werden.

   * In **Debian**:

      ```
      vi /etc/apache2/envvars
      ```

   * In **Red Hat**:

      ```
      vi /usr/local/apache2/bin/envvars
      ```

1. Führen Sie dann die folgenden Befehle aus:

   * In **Debian**:

      Ersetzen Sie in der Datei **nlsrv.load** **nl5** durch **nl6**.

      ```
      vi /etc/apache2/mods-available/nlsrv.load
      ```

      Löschen Sie den Link der Datei &quot; **nlsrv.conf** &quot;und erstellen Sie eine neue Datei.

      ```
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

   * In **Red Hat**:

      Wechseln Sie zum Ordner **/usr/local/apache2/conf** , bearbeiten Sie die Datei **http.conf** und ersetzen Sie in den folgenden Zeilen **nl5** durch **nl6** .

      In **RHEL 7/Debian 8**:

      ```
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. Wechseln Sie zur Datei **alias.conf** und ersetzen Sie alle **nl5** durch **nl6**. Um dies in Debian zu tun, führen Sie den folgenden Befehl aus:

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

## Sicherheitszonen {#security-zones}

Wenn Sie eine Migration von Version 6.02 oder früher durchführen, müssen Sie Ihre Sicherheitszonen konfigurieren, bevor Sie Dienste starten. Weitere Informationen finden Sie unter [Sicherheit](../../migration/using/general-configurations.md#security).

## Dienste neu starten {#re-starting-services}

Die Vorgehensweise hängt von der vorherigen Version Ihres Adobe Campaigns ab.

### Migration von Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-2}

Aktivieren Sie in den **Dateien &quot;config-`<instance name>`.xml** &quot;den automatischen Start von **mta**, **wfserver**, **stat** usw. Dienste.

```
<?xml version='1.0'?>
<serverconf>
  <shared>
    <dataStore hosts="myServer*" lang="en_US">
      <dataSource name="default">
        <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
      </dataSource>
    </dataStore>
  </shared>

  <mta autoStart="true" statServerAddress="localhost"/>
  <stat autoStart="true"/>
  <wfserver autoStart="true"/>
  <inMail autoStart="true"/>
  <sms autoStart="false"/>
</serverconf>
```

Beginn Apache- und Adobe Campaign-Dienste auf jedem der folgenden Server:

1. Tracking- und Weiterleitungsserver.
1. Mid-Sourcing-Server.
1. Marketing-Server.

Bevor Sie mit dem nächsten Schritt fortfahren, führen Sie einen vollständigen Test der neuen Installation durch, stellen Sie sicher, dass es keine Regressionen gibt und dass alles funktioniert, indem Sie alle Empfehlungen im Abschnitt [Allgemeine Konfigurationen](../../migration/using/general-configurations.md) befolgen.

### Migration von Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-2}

Aktivieren Sie in den **Dateien &quot;config-`<instance name>`.xml** &quot;den automatischen Start von **mta**, **wfserver**, **stat** usw. Dienste.

```
<?xml version='1.0'?>
<serverconf>
  <shared>
    <dataStore hosts="myServer*" lang="en_US">
      <dataSource name="default">
        <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
      </dataSource>
    </dataStore>
  </shared>

  <mta autoStart="true" statServerAddress="myStatServer"/>
  <stat autoStart="true"/>
  <wfserver autoStart="true"/>
  <inMail autoStart="true"/>
  <sms autoStart="false"/>
</serverconf>
```

Beginn Apache- und Adobe Campaign-Dienste auf jedem der folgenden Server:

1. Tracking- und Weiterleitungsserver.
1. Mid-Sourcing-Server.
1. Marketing-Server.

Testen Sie die Neuinstallation vollständig, überprüfen Sie, ob sie nicht rückgängig gemacht wird, und stellen Sie sicher, dass alles korrekt funktioniert, indem Sie alle Empfehlungen im Abschnitt [Allgemeine Konfigurationen](../../migration/using/general-configurations.md) befolgen.

### Migration von Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-2}

Beginn Apache- und Adobe Campaign-Dienste auf jedem der folgenden Server:

1. Tracking- und Weiterleitungsserver.
1. Mid-Sourcing-Server.
1. Marketing-Server.

Testen Sie die Neuinstallation vollständig, überprüfen Sie, ob sie nicht rückgängig gemacht wird, und stellen Sie sicher, dass alles korrekt funktioniert, indem Sie alle Empfehlungen im Abschnitt [Allgemeine Konfigurationen](../../migration/using/general-configurations.md) befolgen.

## Löschen und Datenbereingung Adobe Campaign v5 {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>Dieser Abschnitt gilt nur bei der Migration von Adobe Campaign v5.11.

Bevor Sie die Adobe Campaign v5-Installation löschen und bereinigen, müssen Sie die folgenden Empfehlungen anwenden:

* Besorgen Sie sich die Funktionsteams, um eine vollständige Prüfung der neuen Installation durchzuführen.
* Deinstallieren Sie Adobe Campaign v5 nur, wenn Sie sicher sind, dass kein Rollback erforderlich ist.

Löschen Sie den **Ordner &quot;nl5.back** &quot;. Melden Sie sich als **neolane** an und führen Sie den folgenden Befehl aus:

```
su - neolane
rm -rf nl5.back
```

Beginn Sie den Server erneut an.

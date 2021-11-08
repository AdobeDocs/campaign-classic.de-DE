---
product: campaign
title: Migration in Linux zu Adobe Campaign v7
description: Migration in Linux zu Adobe Campaign v7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 9dc0699c-0fbf-4f8e-81f7-8ca3d7e98798
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1890'
ht-degree: 1%

---

# Migration in Linux zu Adobe Campaign v7{#migrating-in-linux-for-adobe-campaign-v}

![](../../assets/v7-only.svg)

## Allgemeines Verfahren {#general-procedure}

Die Migration unter Linux erfolgt wie folgt:

1. Dienste anhalten: see [Service stop](#service-stop).
1. Speichern Sie die Datenbank: see [Datenbank und bestehende Installation sichern](#back-up-the-database-and-the-existing-installation).
1. Deinstallieren Sie frühere Adobe Campaign-Versionspakete: see [Deinstallieren früherer Adobe Campaign-Versionspakete](#uninstalling-adobe-campaign-previous-version-packages).
1. Migrieren Sie die Plattform: verweisen auf [Bereitstellen von Adobe Campaign v7](#deploying-adobe-campaign-v7).
1. Neustart des Dienstes: verweisen auf [Neustart von Diensten](#re-starting-services).

## Service stop {#service-stop}

Beenden Sie zunächst alle Prozesse mit Zugriff auf die Datenbank auf allen betroffenen Computern.

1. Anmelden als **root**.
1. Alle Server, die das Umleitungsmodul (**webmdl** -Dienst) angehalten werden. Führen Sie für Apache den folgenden Befehl aus:

   ```
   /etc/init.d/apache2 stop
   ```

1. Melden Sie sich erneut als **root**.
1. Beenden Sie die bisherigen Adobe Campaign-Versionsdienste auf allen Servern.

   ```
   /etc/init.d/nlserver6 stop
   ```

   Wenn Sie von Version 5.11 migrieren, führen Sie den folgenden Befehl aus:

   ```
   /etc/init.d/nlserver5 stop
   ```

1. Stellen Sie sicher, dass die Adobe Campaign-Dienste auf jedem Server angehalten werden.

   ```
   ps waux | grep nlserver
   ```

   Die Liste der aktiven Prozesse wird zusammen mit ihrer ID (PID) angezeigt.

1. Wenn ein oder mehrere Adobe Campaign-Prozesse nach einigen Minuten noch aktiv sind oder blockiert werden, beenden Sie sie.

   ```
   killall nlserver
   ```

1. Wenn einige Prozesse nach einigen Minuten noch aktiv sind, können Sie sie mithilfe des Befehls zum Schließen zwingen:

   ```
   killall -9 nlserver
   ```

## Datenbank und bestehende Installation sichern {#back-up-the-database-and-the-existing-installation}

Das Verfahren hängt von Ihrer vorherigen Adobe Campaign-Version ab.

### Migration von Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Erstellen Sie eine Sicherungskopie der Adobe Campaign-Datenbank.
1. Anmelden als **Neolan** und eine Sicherungskopie der **nl5** Verzeichnis mit dem folgenden Befehl:

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >Als Vorsichtsmaßnahme empfehlen wir Ihnen, die **nl5.back** und speichern Sie sie an einem anderen sicheren Speicherort als dem Server.

1. Bearbeiten Sie die **config-`<instance name>`.xml** (im **nl5.back** -Ordner), um die **mta**, **wfserver**, **stat** usw. Dienste automatisch starten. Ersetzen Sie beispielsweise **autoStart** mit **_autoStart** (still as **Neolan**).

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

1. Erstellen Sie eine Sicherungskopie der Adobe Campaign-Datenbank.
1. Anmelden als **Neolan** und eine Sicherungskopie der **nl6** Verzeichnis mit dem folgenden Befehl:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Als Vorsichtsmaßnahme empfehlen wir Ihnen, die **nl6.back** und speichern Sie sie an einem anderen sicheren Speicherort als dem Server.

1. Bearbeiten Sie die **config-`<instance name>`.xml** (im **nl6.back** -Ordner), um die **mta**, **wfserver**, **stat**, usw. Dienste automatisch starten. Ersetzen Sie beispielsweise **autoStart** mit **_autoStart** (still as **Adobe Campaign**).

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

1. Erstellen Sie eine Sicherungskopie der Adobe Campaign-Datenbank.
1. Anmelden als **Neolan** und eine Sicherungskopie der **nl6** Verzeichnis mit dem folgenden Befehl:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Als Vorsichtsmaßnahme empfehlen wir Ihnen, die **nl6.back** und speichern Sie sie an einem anderen sicheren Speicherort als dem Server.

## Deinstallieren früherer Adobe Campaign-Versionspakete {#uninstalling-adobe-campaign-previous-version-packages}

Das Verfahren hängt von Ihrer vorherigen Adobe Campaign-Version ab.

### Deinstallieren von Adobe Campaign v5-Paketen {#uninstalling-adobe-campaign-v5-packages}

1. Anmelden als **root**.
1. Identifizieren Sie die installierten Adobe Campaign-Pakete mit dem folgenden Befehl.

   * In **Debian**:

      ```
      dpkg -l | grep nl
      ```

      Die Liste der installierten Packages wird angezeigt:

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

In diesem Abschnitt erfahren Sie, wie Sie Adobe Campaign v6.02- oder v6.1-Pakete deinstallieren.

1. Anmelden als **root**.
1. Identifizieren Sie die installierten Adobe Campaign-Pakete mit dem folgenden Befehl.

   * In **Debian**:

      ```
      dpkg -l | grep nl
      ```

      Die Liste der installierten Packages wird angezeigt:

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

Das Verfahren hängt von Ihrer vorherigen Adobe Campaign-Version ab.

### Migration von Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-1}

Die Bereitstellung von Adobe Campaign erfolgt in zwei Schritten:

* Installieren von Adobe Campaign v7-Paketen: Dieser Vorgang muss auf jedem Server ausgeführt werden.
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
   >Sie müssen die Pakete erfolgreich installieren, bevor Sie mit dem nächsten Schritt fortfahren.

   >[!NOTE]
   >
   >Bei der Migration von v5.11 wird Adobe Campaign im **/usr/local/neolane/nl6/** -Verzeichnis standardmäßig.
   >
   >Nachdem die Pakete installiert wurden, wird die folgende Meldung angezeigt: **Die Option &quot;WdbcTimeZone&quot;fehlt**. Das ist normal.

1. Um das Installationsprogramm der Clientkonsole verfügbar zu machen, kopieren Sie es in den Adobe Campaign-Installationsordner:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Weitere Informationen zur Installation von Adobe Campaign unter Linux finden Sie unter [diesem Abschnitt](../../installation/using/installing-campaign-standard-packages.md).

1. Ändern Sie die **.bashrd** -Datei, die mit dem **Neolan** Benutzer. Anmelden als **Neolan** und führen Sie den folgenden Befehl aus:

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >Bei der Anmeldung als **Neolan**, wird die folgende Meldung angezeigt: **nl5/env.sh : Keine solche Datei oder Verzeichnis**. Das ist normal.

   Ersetzen Sie am Ende der Datei **nl5/env.sh** mit **nl6/env.sh**.

1. Anmelden als **root** und bereiten Sie die Instanz mithilfe der folgenden Befehle vor:

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
   >Mit diesen Befehlen können Sie das interne Dateisystem Adobe Campaign v6 erstellen: **conf** Verzeichnis (mit dem **config-default.xml** und **serverConf.xml** -Dateien), **var** Verzeichnis.

1. Navigieren Sie zu **nl5.back** Backup-Ordner erstellen und die Konfigurationsdateien und Unterordner jeder Instanz kopieren (überschreiben). Anmelden als **Neolan** und führen Sie den folgenden Befehl aus:

   >[!IMPORTANT]
   >
   >Kopieren Sie für den ersten folgenden Befehl nicht die **config-default.xml** -Datei.

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. In Adobe Campaign v7 **serverConf.xml** und **config-default.xml** -Dateien verwenden, wenden Sie die spezifischen Konfigurationen an, die Sie für Adobe Campaign v5 hatten. Für **serverConf.xml** -Datei, verwenden Sie die **nl5/conf/serverConf.xml.diff** -Datei.

   >[!NOTE]
   >
   >Stellen Sie beim Reporting von Konfigurationen von Adobe Campaign v5 bis Adobe Campaign v7 sicher, dass die Pfade zu den physischen Ordnern zu Adobe Campaign v7 und nicht zu Adobe Campaign v5 führen.

1. Da die Migration keine generische Installation ist, müssen Sie den Neustart der **trackinglogd** Dienst. Öffnen Sie dazu die **nl6/conf/config-default.xml** und stellen Sie sicher, dass **trackinglogd** -Dienst aktiviert ist (nur auf dem/den Tracking-/Weiterleitungsserver):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Wenn die Variable **trackinglogd** -Dienst nicht auf dem Tracking-Server gestartet wurde, werden keine Tracking-Informationen weitergeleitet.

1. Laden Sie die Adobe Campaign v7-Konfiguration mit dem folgenden Befehl neu:

   ```
   nlserver config -reload
   ```

1. Starten Sie den Postupgrade-Prozess mit dem folgenden Befehl (weiterhin als **Neolan**):

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!IMPORTANT]
   >
   >Sie müssen angeben, welche Zeitzone während des Postupgrades als Referenz verwendet werden soll (mithilfe der **-timezone** -Option). In diesem Fall verwenden wir die Zeitzone Europa/Paris . **-timezone: &quot;Europa/Paris&quot;**.

   >[!NOTE]
   >
   >Wir empfehlen dringend, Ihre Basis auf &quot;Multi-Timezone&quot;zu aktualisieren. Weiterführende Informationen zu Zeitzonenoptionen finden Sie im Abschnitt [Zeitzonen](../../migration/using/general-configurations.md#time-zones) Abschnitt.

>[!IMPORTANT]
>
>Starten Sie die Adobe Campaign-Dienste noch nicht: In Apache müssen noch Änderungen vorgenommen werden.

### Migration von Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-1}

Die Bereitstellung von Adobe Campaign erfolgt in zwei Schritten:

* Installieren von Adobe Campaign v7-Paketen: Dieser Vorgang muss auf jedem Server ausgeführt werden.
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
   >Sie müssen die Pakete erfolgreich installieren, bevor Sie mit dem nächsten Schritt fortfahren.

   >[!NOTE]
   >
   >Adobe Campaign v7 wird standardmäßig im selben Ordner wie Adobe Campaign v6.02 installiert: **/usr/local/neolane/nl6/**.

1. Um das Installationsprogramm der Clientkonsole verfügbar zu machen, kopieren Sie es in den Adobe Campaign-Installationsordner:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Weitere Informationen zur Installation von Adobe Campaign unter Linux finden Sie unter [diesem Abschnitt](../../installation/using/installing-campaign-standard-packages.md).

1. Da die Migration keine generische Installation ist, müssen Sie den Neustart der **trackinglogd** Dienst. Öffnen Sie dazu die **nl6/conf/config-default.xml** und stellen Sie sicher, dass **trackinglogd** -Dienst aktiviert ist (nur auf dem/den Tracking-/Weiterleitungsserver):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Wenn die Variable **trackinglogd** -Dienst nicht auf dem Tracking-Server gestartet wurde, werden keine Tracking-Informationen weitergeleitet.

1. Navigieren Sie zu **nl6.back** Backup-Ordner erstellen und die Konfigurationsdateien und Unterordner jeder Instanz kopieren (überschreiben). Anmelden als **Neolan** und führen Sie den folgenden Befehl aus:

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

1. Starten Sie den Postupgrade-Prozess mit dem folgenden Befehl (weiterhin als **Neolan**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

   >[!NOTE]
   >
   >Der Modus &quot;Multi-Timezone&quot;war nur in v6.02 für PostgreSQL-Datenbank-Engines verfügbar. Es ist jetzt unabhängig von der verwendeten Version der Datenbank-Engine verfügbar. Wir empfehlen dringend, Ihre Basis auf &quot;Multi-Timezone&quot;zu aktualisieren. Weiterführende Informationen zu Zeitzonenoptionen finden Sie im Abschnitt [Zeitzonen](../../migration/using/general-configurations.md#time-zones) Abschnitt.

### Migration von Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-1}

Die Bereitstellung von Adobe Campaign erfolgt in zwei Schritten:

* Installieren von Adobe Campaign v7-Paketen: Dieser Vorgang muss auf jedem Server ausgeführt werden.
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
   >Sie müssen die Pakete erfolgreich installieren, bevor Sie mit dem nächsten Schritt fortfahren.

   >[!NOTE]
   >
   >Adobe Campaign v7 wird im **/usr/local/neolane/nl6/** -Verzeichnis standardmäßig.

1. Um das Installationsprogramm der Clientkonsole verfügbar zu machen, kopieren Sie es in den Adobe Campaign-Installationsordner:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Weitere Informationen zur Installation von Adobe Campaign unter Linux finden Sie unter [diesem Abschnitt](../../installation/using/installing-campaign-standard-packages.md).

1. Navigieren Sie zu **nl6.back** Backup-Ordner erstellen und die Konfigurationsdateien und Unterordner jeder Instanz kopieren (überschreiben). Anmelden als **Neolan** und führen Sie den folgenden Befehl aus:

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

1. Starten Sie den Postupgrade-Prozess mit dem folgenden Befehl (weiterhin als **Neolan**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

## Migrieren des Weiterleitungsservers (Apache) {#migrating-the-redirection-server--apache-}

>[!NOTE]
>
>Dieser Abschnitt gilt nur bei der Migration von Adobe Campaign v5.11.

In dieser Phase muss Apache gestoppt werden. Siehe: [Service stop](#service-stop).

1. Anmelden als **root**.
1. Ändern Sie die Apache-Umgebungsvariablen, damit sie mit der **nl6** Verzeichnis.

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

      Im **nlsrv.load** Datei ersetzen **nl5** mit **nl6**.

      ```
      vi /etc/apache2/mods-available/nlsrv.load
      ```

      Link der **nlsrv.conf** und erstellen Sie eine neue.

      ```
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

   * In **Red Hat**:

      Navigieren Sie zu **/usr/local/apache2/conf** Verzeichnis, bearbeiten Sie die **http.conf** Datei und ersetzen **nl5** mit **nl6** in den folgenden Zeilen.

      In **RHEL 7/Debian 8**:

      ```
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. Navigieren Sie zu **alias.conf** alle **nl5** mit **nl6**. Führen Sie dazu in Debian den folgenden Befehl aus:

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

## Sicherheitszonen {#security-zones}

Wenn Sie von v6.02 oder früher migrieren, müssen Sie Ihre Sicherheitszonen konfigurieren, bevor Sie Dienste starten. Weitere Informationen finden Sie unter [Sicherheit](../../migration/using/general-configurations.md#security).

## Neustart von Diensten {#re-starting-services}

Das Verfahren hängt von Ihrer vorherigen Adobe Campaign-Version ab.

### Migration von Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-2}

Im **config-`<instance name>`.xml** Dateien, den automatischen Start der **mta**, **wfserver**, **stat**, usw. Dienste.

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

Starten Sie die Apache- und Adobe Campaign-Dienste auf jedem der folgenden Server:

1. Tracking- und Weiterleitungsserver.
1. Mid-Sourcing-Server.
1. Marketing-Server.

Bevor Sie mit dem nächsten Schritt fortfahren, führen Sie einen vollständigen Test der neuen Installation durch, stellen Sie sicher, dass keine Regressionen vorhanden sind und dass alles funktioniert, indem Sie alle Empfehlungen im Abschnitt [Allgemeine Konfigurationen](../../migration/using/general-configurations.md) Abschnitt.

### Migration von Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-2}

Im **config-`<instance name>`.xml** Dateien, den automatischen Start der **mta**, **wfserver**, **stat**, usw. Dienste.

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

Starten Sie die Apache- und Adobe Campaign-Dienste auf jedem der folgenden Server:

1. Tracking- und Weiterleitungsserver.
1. Mid-Sourcing-Server.
1. Marketing-Server.

Testen Sie die Neuinstallation vollständig, vergewissern Sie sich, dass sie nicht rückgängig gemacht wird, und stellen Sie sicher, dass alles ordnungsgemäß funktioniert, indem Sie alle Empfehlungen im Abschnitt [Allgemeine Konfigurationen](../../migration/using/general-configurations.md) Abschnitt.

### Migration von Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-2}

Starten Sie die Apache- und Adobe Campaign-Dienste auf jedem der folgenden Server:

1. Tracking- und Weiterleitungsserver.
1. Mid-Sourcing-Server.
1. Marketing-Server.

Testen Sie die Neuinstallation vollständig, vergewissern Sie sich, dass sie nicht rückgängig gemacht wird, und stellen Sie sicher, dass alles ordnungsgemäß funktioniert, indem Sie alle Empfehlungen im Abschnitt [Allgemeine Konfigurationen](../../migration/using/general-configurations.md) Abschnitt.

## Löschen und Bereinigen von Adobe Campaign v5 {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>Dieser Abschnitt gilt nur bei der Migration von Adobe Campaign v5.11.

Bevor Sie die Adobe Campaign v5-Installation löschen und bereinigen, müssen Sie die folgenden Empfehlungen beachten:

* Holen Sie sich die Funktionsteams, um eine vollständige Prüfung der Neuinstallation durchzuführen.
* Deinstallieren Sie Adobe Campaign v5 nur, wenn Sie sicher sind, dass kein Rollback erforderlich ist.

Löschen Sie die **nl5.back** Verzeichnis. Anmelden als **Neolan** und führen Sie den folgenden Befehl aus:

```
su - neolane
rm -rf nl5.back
```

Starten Sie den Server neu.

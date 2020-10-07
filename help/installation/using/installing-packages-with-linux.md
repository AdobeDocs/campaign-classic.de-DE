---
title: Installieren von Paketen mit Linux
seo-title: Installieren von Paketen mit Linux
description: Installieren von Paketen mit Linux
seo-description: null
page-status-flag: never-activated
uuid: d83f00b5-500b-406a-a3d6-ea5639f244f0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 04faa9f3-d160-4060-b26e-44333f2faf71
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1214'
ht-degree: 1%

---


# Installieren von Paketen mit Linux{#installing-packages-with-linux}

Installieren Sie für eine Linux 32-Bit-Plattform Adobe Campaign 32 Bit. Installieren Sie für eine 64-Bit-Linux-Plattform Adobe Campaign 64 Bit.

Für jede dieser Versionen enthält Adobe Campaign ein Paket: **nlserver**. Dieses Paket enthält die Binärdateien und Konfigurationsdateien für eine bestimmte Version.

Mit den Installationsbefehlen können Sie:

* Kopieren Sie die Dateien nach **/usr/local/neolane**
* Erstellen Sie ein Adobe Campaign-Linux-Konto (und die zugehörige Gruppe), das mit **/usr/local/neolane** als Basisordner erstellt wird
* Erstellen Sie ein automatisches Skript **/etc/init.d/nlserver6** zur Verwendung beim Start oder erstellen Sie eine Systemeinheit (ab 20.1).

>[!NOTE]
>
>Der **neolane** Systembenutzer darf nicht erstellt worden sein, bevor der Befehl ausgeführt wurde. Der **neolane** Benutzer wird während der Installation automatisch erstellt.
>
>Der **Basisordner** , der mit dem **neolanen** Benutzer verknüpft ist, wird ebenfalls automatisch in **[!UICONTROL /usr/local/neolane]** erstellt. Stellen Sie sicher, dass ausreichend Speicherplatz auf der **[!UICONTROL /usr/lokalen]** Festplatte (mehrere GB) vorhanden ist.

Sie können den **Ping-`hostname`** Befehl ausführen, um sicherzustellen, dass der Server sich selbst erreichen kann.

## Verteilung auf Basis von RPM-Paketen {#distribution-based-on-rpm--packages}

Gehen Sie wie folgt vor, um Adobe Campaign auf einem RPM-Betriebssystem (RHEL, CentOS und SUSE) zu installieren:

1. Zuerst müssen Sie das Adobe Campaign-Paket abrufen.

   Die Datei hat den folgenden Namen, wobei **XXXX** die Adobe Campaign-Buildnummer ist:

   * **nlserver6-v7-XXXX-0.x86_64.rpm** für v7.
   * **nlserver6-XXXX-0.x86_64.rpm** für v6.1.

   >[!CAUTION]
   >
   >Stellen Sie sicher, dass Sie den richtigen Dateinamen für Ihre Adobe Campaign-Version in den Befehlsbeispielen dieses Abschnitts verwenden.

1. Um es zu installieren, verbinden Sie es mit dem **Stammordner** und führen Sie den folgenden Befehl aus (wobei **XXXX** die Buildnummer des Adobe Campaigns ist):

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   Die rpm-Datei hat Abhängigkeiten von Paketen, die Sie in CentOS/Red Hat-Distributionen finden können. Wenn Sie einige dieser Abhängigkeiten nicht verwenden möchten (z. B. wenn Sie Oracle JDK anstelle von OpenJDK verwenden möchten), müssen Sie möglicherweise die Option &quot;nodeps&quot;von rpm verwenden:

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

Der Befehl &#39;bc&#39;, der zum Ausführen des netreport benötigt wird (weitere Informationen finden Sie in [diesem Abschnitt](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts) ), ist nicht standardmäßig auf allen Linux-Distributionen verfügbar. Um zu überprüfen, ob der Befehl verfügbar ist, führen Sie den Befehl &#39;which bc&#39; aus. Ist dies nicht der Fall, müssen Sie es installieren.

Bei CentOS müssen Sie das Paket bc.x86_64 installieren: als **Stamm** verbinden und folgenden Befehl ausführen:

```
yum install bc.x86_64
```

## Distribution basierend auf APT (Debian) {#distribution-based-on-apt--debian-}

### In Debian 64 Bit {#in-debian-64-bits}

Um Adobe Campaign 64 Bit auf einem 64-Bit-Debian-Betriebssystem zu installieren, führen Sie die folgenden Schritte aus:

1. Zuerst müssen Sie das Adobe Campaign-Paket abrufen.

   * **nlserver6-v7-XXXX-linux-2.6-amd64.deb** für v7.
   * **nlserver6-XXXX-linux-2.6-amd64.deb** für v6.1.

   **XXXX** ist die Buildnummer des Adobe Campaigns.

   >[!CAUTION]
   >
   >Stellen Sie sicher, dass Sie den richtigen Dateinamen für Ihre Adobe Campaign-Version in den Befehlsbeispielen dieses Abschnitts verwenden.

1. Um es zu installieren, verbinden Sie es mit dem **Stammordner** und führen Sie den folgenden Befehl aus (wobei **XXXX** die Buildnummer des Adobe Campaigns ist):

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

   Wenn Abhängigkeiten fehlen, führen Sie den folgenden Befehl aus:

   ```
   apt-get install -f
   ```

**Debian 8/9-Spezifikationen**

Berücksichtigen Sie bei der Installation von Adobe Campaign auf einem Debian 8/9-Betriebssystem Folgendes:

* OpenSSL muss vorher installiert werden.
* Installieren Sie libicu52 (Debian 8) oder libicu57 (Debian 9), libprotobuf9 (Debian8) und libc-ares2 mit den folgenden Befehlen:

   ```
   aptitude install libicu52 (Debian 8) libicu57 (Debian 9)
   ```

   ```
   aptitude install libc-ares2
   ```

   ```
   aptitude install libprotobuf9 (only Debian 8)
   ```

* Installieren Sie JDK7 mit dem folgenden Befehl:

   ```
   aptitude install openjdk-7-jdk (Debian 8)
   ```

   ```
   aptitude install openjdk-7-jdk (Debian 9)
   ```

## Parameter personalisieren {#personalizing-parameters}

Einige Parameter können über die Datei &quot; **customer.sh** &quot;personalisiert werden

Wenn Sie die Installation zum ersten Mal durchführen, ist die Datei &quot; **customer.sh** &quot;möglicherweise noch nicht auf dem Server vorhanden. Erstellen Sie es und stellen Sie sicher, dass es über Ausführungsrechte verfügt. Ist dies nicht der Fall, geben Sie folgenden Befehl ein:

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### Serverkodierung {#server-encoding}

Standardmäßig wird der Server in einer ISO8859-15-Umgebung gestartet. Dennoch kann der Server in einer UTF-8-Umgebung gestartet werden.

>[!CAUTION]
>
>Diese Änderung betrifft die Interaktionen mit dem Dateisystem (Dateien, die über einen Workflow oder ein JavaScript-Skript geladen werden) und mit der Dateikodierung. Wir empfehlen daher die Verwendung der standardmäßigen Umgebung.

Dennoch müssen Sie zur Erstellung einer **japanischen Instanz** eine UTF-8-Umgebung verwenden.

Um die UTF-8-Umgebung zu aktivieren, verwenden Sie den folgenden Befehl:

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### Standardsprache für den Server {#default-language-for-the-server}

Die Installation unterstützt sowohl Englisch als auch Französisch. Englisch wird standardmäßig verwendet.

Um auf Französisch zu wechseln, geben Sie die folgenden Befehle ein:

```
su - neolane
vi nl6/customer.sh
```

und fügen Sie die folgende Zeile hinzu:

```
export neolane_LANG=fra
```

Um sicherzustellen, dass Systemmeldungen korrekt gelesen werden, müssen sich die Konsolen auf einer Codepage befinden, die der Sprache entspricht (ISO-8859-1 oder -15 für Französisch).

### Umgebungsvariablen {#environment-variables}

Die folgenden Umgebung müssen korrekt definiert werden.

Bestimmte Kombinationen erfordern Änderungen an der Umgebung, die zum Ausführen von Adobe Campaign verwendet wird. Eine bestimmte Datei (`/usr/local/neolane/nl6/customer.sh`) kann erstellt und bearbeitet werden, um spezifische Änderungen zur Adobe Campaign-Umgebung hinzuzufügen.

Bearbeiten Sie bei Bedarf die Datei &quot; **customer.sh** &quot;mit dem Befehl **vi customer.sh** und passen Sie die Konfiguration an oder fügen Sie fehlende Zeilen hinzu:

* Für den Oracle-Client:

   ```
   export ORACLE_HOME=/usr/local/instantclient_10_2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
   ```

   Der Inhalt der Variablen ORACLE_HOME Umgebung stimmt mit dem Installationsordner von Oracle überein.

   Der Inhalt der Variablen &quot;TNS_ADMIN&quot;muss mit dem Speicherort der Datei &quot; **tnsnames.ora** &quot;übereinstimmen.

* Für LibreOffice:

   Um Adobe Campaign auf einer bestehenden Version von LibreOffice auszuführen, sind zusätzliche Konfigurationen erforderlich: müssen Sie die Zugriffspfade zum Installationsordner angeben. Beispiel:

   * Debian

      Standardwerte für OOO_INSTALL_DIR, OOO_BASIS_INSTALL_DIR, OOO_URE_INSTALL_DIR werden bereitgestellt. Sie können sie in **customer.sh** außer Kraft setzen, wenn Ihr Layout der LibreOffice-Installation anders ist:

      ```
      export OOO_BASIS_INSTALL_DIR=/usr/lib/libreoffice/ 
      export OOO_INSTALL_DIR=/usr/lib/libreoffice/
      export OOO_URE_INSTALL_DIR=/usr/lib/ure/share/
      ```

   * CentOs

      Verwenden Sie die folgenden Standardwerte:

      ```
      export OOO_BASIS_INSTALL_DIR=/usr/lib64/libreoffice/
      export OOO_INSTALL_DIR=/usr/lib64/libreoffice/
      export OOO_URE_INSTALL_DIR=/usr/lib64/libreoffice/ure/share/
      ```

* Für Java Development Kit (JDK):

   Standardmäßig sucht das Konfigurationsskript der Adobe Campaign Umgebung (`~/nl6/env.sh`) nach dem JDK-Installationsordner. Da dieses Verhalten nicht hundertprozentig zuverlässig ist, müssen Sie angeben, welches JDK verwendet werden soll. Dazu können Sie die Variable **JDK_HOME** -Umgebung mithilfe des folgenden Befehls erzwingen:

   ```
   export JDK_HOME=/usr/java/jdk1.6.0_07
   ```

   >[!NOTE]
   >
   >Das ist ein Beispiel. Stellen Sie sicher, dass die verwendete JDK-Version mit dem Ordnernamen übereinstimmt.

   Um die JDK-Konfiguration zu testen, melden Sie sich mit dem folgenden Befehl als Systembenutzer des Adobe Campaigns an:

   ```
   su - neolane
   ```

Sie müssen den Adobe Campaign-Dienst neu starten, damit die Änderungen berücksichtigt werden.

Die Befehle lauten wie folgt:

```
/etc/init.d/nlserver6 stop
/etc/init.d/nlserver6 start
```

Ab 20.1 sollten stattdessen die folgenden Befehle verwendet werden:

```
systemctl stop nlserver
systemctl start nlserver
```

### Oracle Client unter Linux {#oracle-client-in-linux}

Bei Verwendung von Oracle mit Adobe Campaign müssen Sie die Oracle-Clientebenen unter Linux konfigurieren.

* Vollständiger Client verwenden
* TNS-Definition

   Die TNS-Definitionen müssen während der Installationsphase hinzugefügt werden. Verwenden Sie dazu die folgenden Befehle:

   ```
   cd /etc
   mkdir oracle
   cd oracle
   vi tnsnames.ora
   ```

* Umgebungsvariablen

   Siehe [Umgebung](../../installation/using/installing-packages-with-linux.md#environment-variables).

* Konfiguration für Adobe Campaign

   Um die Installation des Oracle-Client zum Adobe Campaign abzuschließen, müssen Sie einen symbolischen Link für die von Adobe Campaign verwendete **.so** -Datei erstellen.

   Verwenden Sie dazu die folgenden Befehle:

   ```
   cd /usr/lib/oracle/10.2.0.4/client/lib
   ln -s libclntsh.so.10.1 libclntsh.so
   ```

Wenn ein Problem auftritt, stellen Sie sicher, dass die in der [Oracle-Installationsdokumentation](https://www.oracle.com/pls/db112/portal.portal_db?selected=11) aufgelisteten Pakete ordnungsgemäß installiert sind.

## Installationsprüfungen {#installation-checks}

Sie können jetzt einen ersten Installationstest mit den folgenden Befehlen durchführen:

```
su - neolane
nlserver pdump
```

Wenn das Adobe Campaign nicht gestartet wird, lautet die Antwort:

```
no task
```

## Erster Beginn des Servers {#first-start-up-of-the-server}

Geben Sie nach Abschluss des Installationstests den folgenden Befehl ein:

```
nlserver web
```

Anschließend werden die folgenden Informationen angezeigt:

```
17:11:03 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
17:11:03 >   Web server start (pid=17546, tid=-151316352)...
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/config-default.xml' via '/usr/local/[INSTALL]/nl6/conf/models/config-default.xml'
17:11:03 >   Server started
17:11:08 >   Stop requested (pid=17546)
17:11:08 >   Web server stop(pid=17546, tid=-151316352)...
```

Mit diesen Befehlen können Sie **Konfigurationsdateien &quot;config-default.xml** &quot;und &quot; **serverConf.xml** &quot;erstellen. Alle in der Datei **serverConf.xml** verfügbaren Parameter sind in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md)aufgeführt.

Drücken Sie **Strg+C** , um den Prozess zu beenden, und geben Sie dann den folgenden Befehl ein:

```
nlserver start web
```

Anschließend werden die folgenden Informationen angezeigt:

```
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Running task 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') in a new process
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

Geben Sie zum Beenden Folgendes ein:

```
nlserver stop web
```

Anschließend werden die folgenden Informationen angezeigt:

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Kennwort für die interne ID {#password-for-the-internal-identifier}

Der Adobe Campaign-Server definiert eine technische Anmeldung mit der Bezeichnung **internal** , die alle Berechtigungen für alle Instanzen besitzt. Kurz nach der Installation hat die Anmeldung kein Passwort. Es ist obligatorisch, eine zu definieren.

Siehe Abschnitt [Interne Kennung](../../installation/using/campaign-server-configuration.md#internal-identifier).

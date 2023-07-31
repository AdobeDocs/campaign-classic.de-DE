---
product: campaign
title: Installieren von Paketen mit Linux
description: Installieren von Paketen mit Linux
feature: Installation, Application Settings
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
badge-v7-prem: label="On-Premise und Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: f41c7510-5ad7-44f3-9485-01f54994b6cb
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1211'
ht-degree: 3%

---

# Installieren von Paketen mit Linux{#installing-packages-with-linux}



Installieren Sie für eine Linux-32-Bit-Plattform Adobe Campaign 32 Bit. Installieren Sie für eine Linux-64-Bit-Plattform Adobe Campaign 64 Bit.

Für jede dieser Versionen ist Adobe Campaign mit einem Paket ausgestattet: **nlserver**. Dieses Paket enthält die Binärdateien und Konfigurationsdateien für eine bestimmte Version.

Mit den Installationsbefehlen können Sie:

* Kopieren Sie die Dateien nach **/usr/local/neolane**
* Erstellen Sie ein Adobe Campaign Linux-Konto (und die zugehörige Gruppe), das mit **/usr/local/neolane** als Basisverzeichnis
* Erstellen eines automatischen Skripts **/etc/init.d/nlserver6** zur Verwendung beim Start oder zur Erstellung einer Systemeinheit (ab 20.1).

>[!NOTE]
>
>Die **Neolan** Der Systembenutzer darf nicht erstellt worden sein, bevor der Befehl ausgeführt wurde. Die **Neolan** Der Benutzer wird während der Installation automatisch erstellt.
>
>Die **home** Verzeichnis, das mit dem **Neolan** Der Benutzer wird auch automatisch in **[!UICONTROL /usr/local/neolane]**. Stellen Sie sicher, dass auf der **[!UICONTROL /usr/local]** Disk (mehrere GB).

Sie können die **ping`hostname`** -Befehl, um sicherzustellen, dass der Server selbst erreicht werden kann.

## Verteilung basierend auf RPM-Paketen {#distribution-based-on-rpm--packages}

Gehen Sie wie folgt vor, um Adobe Campaign auf einem RPM-Betriebssystem (RHEL, CentOS und SUSE) zu installieren:

1. Sie müssen zunächst das Adobe Campaign-Paket abrufen.

   Die Datei erhält den Namen wie folgt, wobei **XXXX** ist die Adobe Campaign-Build-Nummer: **nlserver6-v7-XXXX-0.x86_64.rpm**.

   >[!CAUTION]
   >
   >Stellen Sie sicher, dass Sie in den Beispielbefehlen dieses Abschnitts den richtigen Dateinamen für Ihre Adobe Campaign-Version verwenden.

1. Um es zu installieren, verbinden Sie sich mit **root** und führen Sie den folgenden Befehl aus (wobei **XXXX** ist die Adobe Campaign-Build-Nummer):

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   Die rpm-Datei hat Abhängigkeiten von Paketen, die Sie in CentOS/Red Hat-Distributionen finden können. Wenn Sie einige dieser Abhängigkeiten nicht verwenden möchten (z. B. wenn Sie Oracle JDK anstelle von OpenJDK verwenden möchten), müssen Sie möglicherweise die Option &quot;nodeps&quot;von rpm verwenden:

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

Der Befehl &#39;bc&#39;, der zur Ausführung des netreport erforderlich ist (siehe [diesem Abschnitt](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts) für weitere Informationen), ist nicht standardmäßig in allen Linux-Distributionen verfügbar. Um zu überprüfen, ob der Befehl verfügbar ist, führen Sie den Befehl &#39;which bc&#39; aus. Wenn nicht, müssen Sie es installieren.

Bei CentOS müssen Sie das Paket bc.x86_64 installieren: connect as **root** und führen Sie den folgenden Befehl aus:

```
yum install bc.x86_64
```

## Verteilung basierend auf APT (Debian) {#distribution-based-on-apt--debian-}

### In Debian 64 Bit {#in-debian-64-bits}

Gehen Sie wie folgt vor, um Adobe Campaign 64 Bit auf einem 64-Bit-Debian-Betriebssystem zu installieren:

1. Sie müssen zunächst das Adobe Campaign-Paket abrufen: **nlserver6-v7-XXXX-linux-2.6-amd64.deb**, wobei **XXXX** ist die Build-Nummer.

   >[!CAUTION]
   >
   >Stellen Sie sicher, dass Sie in den Beispielbefehlen dieses Abschnitts den richtigen Dateinamen für Ihre Adobe Campaign-Version verwenden.

1. Um es zu installieren, verbinden Sie sich mit **root** und führen Sie den folgenden Befehl aus (wobei **XXXX** ist die Adobe Campaign-Build-Nummer):

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

   Wenn fehlende Abhängigkeiten vorhanden sind, führen Sie den folgenden Befehl aus:

   ```
   apt-get install -f
   ```

**Debian 8/9-Besonderheiten**

Beachten Sie bei der Installation von Adobe Campaign auf einem Debian 8/9-Betriebssystem Folgendes:

* OpenSSL muss zuvor installiert werden.
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

Einige Parameter können über die **customer.sh** file

Wenn Sie die Installation zum ersten Mal durchführen, wird die **customer.sh** auf dem Server möglicherweise noch nicht vorhanden ist. Erstellen Sie sie und stellen Sie sicher, dass sie über Ausführungsrechte verfügt. Ist dies nicht der Fall, geben Sie den folgenden Befehl ein:

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### Serverkodierung {#server-encoding}

Standardmäßig wird der Server in einer ISO8859-15-Umgebung gestartet. Dennoch kann der Server in einer UTF-8-Umgebung gestartet werden.

>[!CAUTION]
>
>Diese Änderung betrifft die Interaktionen mit dem Dateisystem (Dateien, die über einen Workflow oder ein JavaScript geladen werden) und die Dateikodierung. Es wird daher empfohlen, die Standardumgebung zu verwenden.

Für die Schaffung eines **Japanische Instanz**, müssen Sie eine UTF-8-Umgebung verwenden.

Verwenden Sie den folgenden Befehl, um die UTF-8-Umgebung zu aktivieren:

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### Standardsprache für den Server {#default-language-for-the-server}

Die Installation unterstützt sowohl Englisch als auch Französisch. Englisch wird standardmäßig verwendet.

Geben Sie die folgenden Befehle ein, um auf Französisch zu wechseln:

```
su - neolane
vi nl6/customer.sh
```

und fügen Sie die folgende Zeile hinzu:

```
export neolane_LANG=fra
```

Um sicherzustellen, dass Systemnachrichten korrekt gelesen werden, müssen sich die Konsolen auf einer Codepage befinden, die der Sprache entspricht (ISO-8859-1 oder -15 für Französisch).

### Umgebungsvariablen {#environment-variables}

Die folgenden Umgebungsvariablen müssen korrekt definiert sein.

Bestimmte Kombinationen erfordern Änderungen an der Umgebung, die für die Ausführung von Adobe Campaign verwendet wird. Eine bestimmte Datei (`/usr/local/neolane/nl6/customer.sh`) können erstellt und bearbeitet werden, um spezifische Änderungen für die Adobe Campaign-Umgebung hinzuzufügen.

Bearbeiten Sie bei Bedarf die **customer.sh** -Datei mithilfe der **vi customer.sh** und passen Sie die Konfiguration an oder fügen Sie fehlende Zeilen hinzu:

* Für den Oracle-Client:

  ```
  export ORACLE_HOME=/usr/local/instantclient_10_2
  export TNS_ADMIN=/etc/oracle
  export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
  ```

  Der Inhalt der Umgebungsvariablen ORACLE_HOME entspricht dem Installationsordner von Oracle.

  Der Inhalt der Variable TNS_ADMIN muss mit dem Speicherort der Variablen **tnsnames.ora** -Datei.

* Für LibreOffice:

  Um Adobe Campaign auf einer bestehenden LibreOffice-Version ausführen zu können, sind zusätzliche Konfigurationen erforderlich: Sie müssen die Zugriffspfade zum Installationsordner angeben. Beispiel:

   * Debian

     Standardwerte für OOO_INSTALL_DIR und OOO_BASIS_INSTALL_DIR werden bereitgestellt. Sie können sie in **customer.sh** wenn Ihr Layout der LibreOffice-Installation anders ist:

     ```
     export OOO_BASIS_INSTALL_DIR=/usr/lib/libreoffice/ 
     export OOO_INSTALL_DIR=/usr/lib/libreoffice/
     ```

   * CentOs

     Verwenden Sie die folgenden Standardwerte:

     ```
     export OOO_BASIS_INSTALL_DIR=/usr/lib64/libreoffice/
     export OOO_INSTALL_DIR=/usr/lib64/libreoffice/
     ```

* Für Java Development Kit (JDK):

  Standardmäßig ist das Konfigurationsskript der Adobe Campaign-Umgebung (`~/nl6/env.sh`) sucht nach dem JDK-Installationsordner. Da dieses Verhalten nicht zu 100 % zuverlässig ist, müssen Sie angeben, welches JDK verwendet werden soll. Dazu können Sie die **JDK_HOME** Umgebungsvariable mithilfe des folgenden Befehls:

  ```
  export JDK_HOME=/usr/java/jdk1.6.0_07
  ```

  >[!NOTE]
  >
  >Dies ist ein Beispiel. Stellen Sie sicher, dass die verwendete JDK-Version mit dem Ordnernamen übereinstimmt.

  Um die JDK-Konfiguration zu testen, melden Sie sich mit dem folgenden Befehl als Adobe Campaign-Systembenutzer an:

  ```
  su - neolane
  ```

Sie müssen den Adobe Campaign-Dienst neu starten, damit die Änderungen berücksichtigt werden.

Die Befehle lauten wie folgt:

```
/etc/init.d/nlserver6 stop
/etc/init.d/nlserver6 start
```

Ab Version 20.1 wird empfohlen, stattdessen die folgenden Befehle zu verwenden:

```
systemctl stop nlserver
systemctl start nlserver
```

### Oracle Client unter Linux {#oracle-client-in-linux}

Bei Verwendung von Oracle mit Adobe Campaign müssen Sie die Oracle-Client-Ebenen in Linux konfigurieren.

* Vollständigen Client verwenden
* TNS-Definition

  Die TNS-Definitionen müssen während der Installationsphase hinzugefügt werden. Verwenden Sie dazu die folgenden Befehle:

  ```
  cd /etc
  mkdir oracle
  cd oracle
  vi tnsnames.ora
  ```

* Umgebungsvariablen

  Siehe Abschnitt [Umgebungsvariablen](../../installation/using/installing-packages-with-linux.md#environment-variables).

* Konfiguration für Adobe Campaign

  Um die Installation des Oracle-Clients für Adobe Campaign abzuschließen, müssen Sie eine symbolische Verknüpfung für die **.so** von Adobe Campaign verwendete Datei.

  Verwenden Sie dazu die folgenden Befehle:

  ```
  cd /usr/lib/oracle/10.2.0.4/client/lib
  ln -s libclntsh.so.10.1 libclntsh.so
  ```

Wenn ein Problem auftritt, stellen Sie sicher, dass die Pakete, die im [Oracle-Installationsdokumentation](https://docs.oracle.com/) korrekt installiert sind.

## Installationsprüfungen {#installation-checks}

Sie können jetzt einen ersten Installationstest mit den folgenden Befehlen durchführen:

```
su - neolane
nlserver pdump
```

Wenn Adobe Campaign nicht gestartet wird, lautet die Antwort:

```
no task
```

## Erstmaliger Start des Servers {#first-start-up-of-the-server}

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

Mit diesen Befehlen können Sie **config-default.xml** und **serverConf.xml** Konfigurationsdateien. Alle in der **serverConf.xml** in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md).

Presse **Strg+C** um den Prozess zu beenden, geben Sie folgenden Befehl ein:

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

Geben Sie zum Anhalten Folgendes ein:

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

## Kennwort für die interne Kennung {#password-for-the-internal-identifier}

Der Adobe Campaign-Server definiert eine technische Anmeldung mit dem Namen **intern** , das alle Rechte für alle Instanzen hat. Kurz nach der Installation hat die Anmeldung kein Passwort. Es ist obligatorisch, eine zu definieren.

Weiterführende Informationen finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

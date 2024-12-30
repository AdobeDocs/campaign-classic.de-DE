---
product: campaign
title: Integration in einen Webserver für Linux
description: Informationen zur Integration von Campaign in einen Webserver (Linux)
feature: Installation, Instance Settings
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: 4f8ea358-a38d-4137-9dea-f398e60c5f5d
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 3%

---

# Integration in einen Webserver für Linux {#integration-into-a-web-server-for-linux}


Adobe Campaign enthält Apache Tomcat, das über HTTP (und SOAP) als Einstiegspunkt im Anwendungsserver fungiert.

Sie können diesen integrierten Tomcat-Server verwenden, um HTTP-Anfragen zu bearbeiten.

In diesem Fall:

* Der standardmäßige Überwachungs-Port ist 8080. Informationen zu Änderungen finden Sie [diesem Abschnitt](configure-tomcat.md).
* Die Client-Konsolen stellen dann über eine URL eine Verbindung her, z. B.:

  ```
  https://<computer>:8080
  ```

Aus Sicherheits- und Verwaltungsgründen empfehlen wir jedoch die Verwendung eines dedizierten Webservers als Haupteinstiegspunkt für den HTTP-Traffic, wenn der Computer, auf dem Adobe Campaign ausgeführt wird, im Internet verfügbar ist und Sie den Zugriff auf die Konsole außerhalb Ihres Netzwerks öffnen möchten.

Mit einem Webserver können Sie auch die Vertraulichkeit der Daten mit dem HTTPs-Protokoll gewährleisten.

Ebenso müssen Sie einen Webserver verwenden, wenn Sie die Tracking-Funktion verwenden möchten, die nur als Erweiterungsmodul für einen Webserver verfügbar ist.

>[!NOTE]
>
>Wenn Sie die Tracking-Funktion nicht verwenden, können Sie eine Standardinstallation von Apache oder IIS mit einer Umleitung zu Campaign durchführen. Das Erweiterungsmodul Webserver-Tracking ist nicht erforderlich.

## Konfigurieren des Apache-Webservers mit Debian {#configuring-the-apache-web-server-with-debian}

Dieser Prozess gilt, wenn Sie Apache unter einer auf APT basierenden Distribution installiert haben.

Gehen Sie wie folgt vor:

1. Deaktivieren Sie die standardmäßig geladenen Module mithilfe des folgenden Befehls:

   ```
   a2dismod auth_basic authn_file authz_default authz_user autoindex cgi dir env negotiation userdir
   ```

   Stellen Sie sicher, **die Module** alias **, auth_host** und **mime** weiterhin aktiviert sind. Verwenden Sie dazu den folgenden Befehl:

   ```
   a2enmod  alias authz_host mime
   ```

1. Erstellen Sie die Datei **nlsrv.load** in **/etc/apache2/mods-available** und fügen Sie den folgenden Inhalt ein:

   In Debian 8:

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. Erstellen Sie die Datei **nlsrv.conf** in **/etc/apache2/mods-available** mit folgendem Befehl:

   ```
   ln -s /usr/local/[INSTALL]/nl6/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. Aktivieren Sie dieses Modul mit dem folgenden Befehl:

   ```
    a2enmod nlsrv
   ```

   Wenn Sie das Modul **mod_rewrite** für Adobe Campaign-Seiten verwenden, müssen Sie die Dateien **nlsrv.load** und **nlsrv.conf** in **zz-nlsrv.load** und **zz-nlsrv.conf** umbenennen. Um das Modul zu aktivieren, führen Sie den folgenden Befehl aus:

   ```
   a2enmod zz-nlsrv
   ```

1. Bearbeiten Sie die Datei **/etc/apache2/envars** und fügen Sie die folgenden Zeilen hinzu:

   ```
   # Added Neolane
   if [ "$LD_LIBRARY_PATH" != "" ]; then export LD_LIBRARY_PATH="/usr/local/neolane/nl6/lib:$LD_LIBRARY_PATH"; else export LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib; fi
   export USERPATH=/usr/local/neolane
   ```

   Speichern Sie die Änderungen.

1. Fügen Sie dann Adobe Campaign-Benutzer mithilfe des folgenden Befehlstyps zur Apache-Benutzergruppe hinzu und umgekehrt:

   ```
   usermod neolane -G www-data
   usermod www-data -G neolane
   ```

1. Apache neu starten:

   ```
   invoke-rc.d apache2 restart
   ```

## Konfigurieren des Apache-Webservers in RHEL {#configuring-apache-web-server-in-rhel}

Dieses Verfahren gilt, wenn Sie Apache unter einem auf RPM (RHEL, CentOS und Suse) basierenden Paket installiert und gesichert haben.

Gehen Sie wie folgt vor:

1. Aktivieren Sie in der `httpd.conf`-Datei die folgenden Apache-Module:

   ```
   alias
   authz_host
   mime
   ```

1. Deaktivieren Sie die folgenden Module:

   ```
   auth_basic
   authn_file
   authz_default
   authz_user
   autoindex
   cgi
   dir
   env
   negotiation
   userdir
   ```

   Kommentieren Sie die Funktionen, die mit deaktivierten Modulen verknüpft sind:

   ```
   DirectoryIndex
   IndexOptions    
   AddIconByEncoding    
   AddIconByType    
   AddIcon    
   DefaultIcon    
   ReadmeName    
   HeaderName    
   IndexIgnore    
   LanguagePriority    
   ForceLanguagePriority
   ```

1. Erstellen Sie eine Adobe Campaign-spezifische Konfigurationsdatei im `/etc/httpd/conf.d/`. Beispiel: `CampaignApache.conf`

1. Fügen Sie **RHEL7** die folgenden Anweisungen in der Datei hinzu:

   ```
   LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
   Include /usr/local/neolane/nl6/conf/apache_neolane.conf
   ```

1. Für **RHEL7**:

   Fügen Sie die `/etc/systemd/system/httpd.service` Datei mit folgendem Inhalt hinzu:

   ```
   .include /usr/lib/systemd/system/httpd.service
   
   [Service]
   Environment=USERPATH=/usr/local/neolane LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib
   ```

   Aktualisieren Sie das von den Systemen verwendete Modul:

   ```
   systemctl daemon-reload
   ```

1. Fügen Sie dann Adobe Campaign-Operatoren zur Apache-Operatorgruppe hinzu und umgekehrt, indem Sie den Befehl ausführen:

   ```
   usermod -a -G neolane apache
   usermod -a -G apache neolane
   ```

   Die zu verwendenden Gruppennamen hängen von der Apache-Konfiguration ab.

1. Führen Sie Apache und Adobe Campaign aus.

   Für RHEL7:

   ```
   systemctl start httpd
   systemctl start nlserver
   ```

## Starten des Webservers und Testen der Konfiguration{#launching-the-web-server-and-testing-the-configuration}

Sie können die Konfiguration jetzt testen, indem Sie Apache starten. Das Adobe Campaign-Modul sollte nun sein Banner auf der Konsole anzeigen (zwei Banner auf bestimmten Betriebssystemen):

```
 /etc/init.d/apache start
```

Daraufhin werden die folgenden Informationen angezeigt:

```sql
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
```

Überprüfen Sie als Nächstes, ob es reagiert, indem Sie eine Test-URL senden.

Sie können dies über die Befehlszeile testen, indem Sie Folgendes ausführen:

```
 telnet localhost 80  
```

Sie sollten Folgendes erhalten:

```
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
```

Geben Sie dann ein:

```
GET /r/test
```

Daraufhin werden die folgenden Informationen angezeigt:

```
<redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='' localHost='XXXX'/>
Connection closed by foreign host.
```

Sie können die URL-`https://myserver.adobe.com/r/test` auch über einen Webbrowser anfordern.

---
title: Integration in einen Webserver für Linux
seo-title: Integration in einen Webserver für Linux
description: Integration in einen Webserver für Linux
seo-description: null
page-status-flag: never-activated
uuid: 7b18d176-4458-46a8-8da4-3621f90c6b13
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 752ba848-aee9-4bb0-b2c5-490f3124f74e
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 6%

---


# Integration in einen Webserver für Linux{#integration-into-a-web-server-for-linux}

Adobe Campaign enthält Apache Tomcat, der als Einstiegspunkt im Anwendungsserver über HTTP (und SOAP) fungiert.

Sie können diesen integrierten Tomcat-Server verwenden, um HTTP-Anforderungen zu erfüllen.

In diesem Fall:

* Der standardmäßige Listening-Anschluss ist 8080. Informationen zum Ändern finden Sie unter [Konfigurieren von Tomcat](../../installation/using/configuring-campaign-server.md#configuring-tomcat).
* Der Client Konsolen verbindet sich dann mit einer URL wie:

   ```
   http://<computer>:8080
   ```

Aus Sicherheits- und Verwaltungsgründen sollten Sie jedoch einen dedizierten Webserver als Haupteinstiegspunkt für HTTP-Traffic verwenden, wenn der Computer, auf dem Adobe Campaign ausgeführt wird, im Internet verfügbar ist und Sie den Zugriff auf die Konsole außerhalb Ihres Netzwerks öffnen möchten.

Mit einem Webserver können Sie auch die Vertraulichkeit von Daten mit dem HTTP-Protokoll gewährleisten.

Ebenso müssen Sie einen Webserver verwenden, wenn Sie die Verfolgungsfunktion verwenden möchten, die nur als Erweiterungsmodul für einen Webserver verfügbar ist.

>[!NOTE]
>
>Wenn Sie die Verfolgungsfunktion nicht verwenden, können Sie eine Standardinstallation von Apache oder IIS mit einer Weiterleitung zur Kampagne durchführen. Das Tracking-Webserver-Erweiterungsmodul ist nicht erforderlich.

## Konfigurieren des Apache-Webservers mit Debian {#configuring-the-apache-web-server-with-debian}

Dieser Vorgang gilt, wenn Sie Apache unter einer auf APT basierenden Distribution installiert haben.

Gehen Sie wie folgt vor:

1. Deaktivieren Sie die standardmäßig geladenen Module mit dem folgenden Befehl:

   ```
   a2dismod auth_basic authn_file authz_default authz_user autoindex cgi dir env negotiation userdir
   ```

   Stellen Sie sicher, dass die Module **alias**, **authz_host** und **mime** weiterhin aktiviert sind. Verwenden Sie dazu den folgenden Befehl:

   ```
   a2enmod  alias authz_host mime
   ```

1. Erstellen Sie die Datei **nlsrv.load** in **/etc/apache2/mods-available** und fügen Sie den folgenden Inhalt ein:

   In Debian 8:

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. Erstellen Sie die Datei **nlsrv.conf** in **/etc/apache2/mods-available** mit dem folgenden Befehl:

   ```
   ln -s /usr/local/[INSTALL]/nl6/tomcat-7/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. Aktivieren Sie dieses Modul mit dem folgenden Befehl:

   ```
    a2enmod nlsrv
   ```

   Wenn Sie das Modul **mod_rewrite** für Adobe Campaign-Seiten verwenden, müssen Sie die Dateien **nlsrv.load** und **nlsrv.conf** in **zz-nlsrv.load** und **zz-nlsrv.conf** umbenennen. Führen Sie zum Aktivieren des Moduls den folgenden Befehl aus:

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

1. Fügen Sie dann Adobe Campaign-Benutzer zur Apache-Benutzergruppe hinzu und umgekehrt, indem Sie den folgenden Befehlstyp verwenden:

   ```
   usermod neolane -G www-data
   usermod www-data -G neolane
   ```

1. Apache neu starten:

   ```
   invoke-rc.d apache2 restart
   ```

## Apache-Webserver in RHEL konfigurieren {#configuring-apache-web-server-in-rhel}

Dieses Verfahren gilt, wenn Sie Apache unter einem RPM (RHEL, CentOS und Suse)-basierten Paket installiert und gesichert haben.

Gehen Sie wie folgt vor:

1. Aktivieren Sie in der `httpd.conf` Datei die folgenden Apache-Module:

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

   Funktionen kommentieren, die mit deaktivierten Modulen verknüpft sind:

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

1. Erstellen Sie eine Adobe Campaign-spezifische Konfigurationsdatei im `/etc/httpd/conf.d/` Ordner. Beispiel `CampaignApache.conf`

1. Fügen Sie für **RHEL7** die folgenden Anweisungen in die Datei ein:

   ```
   LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
   Include /usr/local/neolane/nl6/tomcat-7/conf/apache_neolane.conf
   ```

1. Für **RHEL7**:

   hinzufügen die `/etc/systemd/system/httpd.service` Datei mit folgendem Inhalt:

   ```
   .include /usr/lib/systemd/system/httpd.service
   
   [Service]
   Environment=USERPATH=/usr/local/neolane LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib
   ```

   Aktualisieren Sie das von system verwendete Modul:

   ```
   systemctl daemon-reload
   ```

1. Fügen Sie dann der Gruppe der Apache-Operatoren Adobe Campaign-Operatoren hinzu und umgekehrt, indem Sie den Befehl ausführen:

   ```
   usermod -a -G neolane apache
   usermod -a -G apache neolane
   ```

   Die zu verwendenden Gruppennamen hängen von der Konfiguration des Apache ab.

1. Führen Sie Apache und den Adobe Campaign-Server aus.

   RHEL7:

   ```
   systemctl start httpd
   systemctl start nlserver
   ```

## Webserver starten und Konfiguration testen{#launching-the-web-server-and-testing-the-configuration}

Sie können die Konfiguration jetzt testen, indem Sie Apache starten. Das Adobe Campaign-Modul sollte nun sein Banner auf der Konsole anzeigen (zwei Banner auf bestimmten Betriebssystemen):

```
 /etc/init.d/apache start
```

Die folgenden Informationen werden angezeigt:

```
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
```

Überprüfen Sie dann, ob die Antwort durch Senden einer Test-URL erfolgt.

Sie können dies über die Befehlszeile testen, indem Sie:

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

Die folgenden Informationen werden angezeigt:

```
<redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='' localHost='XXXX'/>
Connection closed by foreign host.
```

Sie können die URL auch [`https://<computer>`](https://machine/r/test) über einen Webbrowser anfordern.

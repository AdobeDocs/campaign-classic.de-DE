---
product: campaign
title: Integration in einen Webserver für Linux
description: Erfahren Sie, wie Sie Campaign in einen Webserver (Linux) integrieren.
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: 4f8ea358-a38d-4137-9dea-f398e60c5f5d
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 4%

---

# Integration in einen Webserver für Linux{#integration-into-a-web-server-for-linux}

Adobe Campaign enthält Apache Tomcat, der über HTTP (und SOAP) als Einstiegspunkt im Anwendungsserver fungiert.

Sie können diesen integrierten Tomcat-Server verwenden, um HTTP-Anforderungen zu erfüllen.

In diesem Fall:

* Der standardmäßige Listening-Anschluss ist 8080. Weiterführende Informationen dazu finden Sie in [diesem Abschnitt](configure-tomcat.md).
* Die Clientkonsole Konsolen stellt dann eine Verbindung über eine URL her, z. B.:

   ```
   http://<computer>:8080
   ```

Aus Sicherheits- und Verwaltungsgründen empfehlen wir jedoch die Verwendung eines dedizierten Webservers als Haupteinstiegspunkt für HTTP-Traffic, wenn der Computer, auf dem Adobe Campaign ausgeführt wird, im Internet verfügbar ist und Sie den Zugriff auf die Konsole außerhalb Ihres Netzwerks öffnen möchten.

Mit einem Webserver können Sie auch die Vertraulichkeit von Daten mit dem HTTP-Protokoll gewährleisten.

Ebenso müssen Sie einen Webserver verwenden, wenn Sie die Tracking-Funktion verwenden möchten, die nur als Erweiterungsmodul für einen Webserver verfügbar ist.

>[!NOTE]
>
>Wenn Sie die Tracking-Funktion nicht verwenden, können Sie eine Standardinstallation von Apache oder IIS mit einer Umleitung zu Campaign durchführen. Das Tracking-Webserver-Erweiterungsmodul ist nicht erforderlich.

## Konfigurieren des Apache-Webservers mit Debian {#configuring-the-apache-web-server-with-debian}

Dieser Prozess wird angewendet, wenn Sie Apache unter einer auf APT basierenden Distribution installiert haben.

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
   ln -s /usr/local/[INSTALL]/nl6/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. Aktivieren Sie dieses Modul mit dem folgenden Befehl:

   ```
    a2enmod nlsrv
   ```

   Wenn Sie das Modul **mod_rewrite** für Adobe Campaign-Seiten verwenden, müssen Sie die Dateien **nlsrv.load** und **nlsrv.conf** in **zz-nlsrv.load** und **zz-nlsrv.umbenennen. conf**. Um das Modul zu aktivieren, führen Sie den folgenden Befehl aus:

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

1. Fügen Sie dann Adobe Campaign-Benutzer zur Apache-Benutzergruppe hinzu und umgekehrt mithilfe des folgenden Befehlstyps:

   ```
   usermod neolane -G www-data
   usermod www-data -G neolane
   ```

1. Starten Sie Apache neu:

   ```
   invoke-rc.d apache2 restart
   ```

## Konfigurieren des Apache-Webservers in RHEL {#configuring-apache-web-server-in-rhel}

Dieses Verfahren wird angewendet, wenn Sie Apache unter einem RPM-Paket (RHEL, CentOS und Suse) installiert und gesichert haben.

Gehen Sie wie folgt vor:

1. Aktivieren Sie in der Datei `httpd.conf` die folgenden Apache-Module:

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

   Kommentieren Sie die mit deaktivierten Modulen verknüpften Funktionen:

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

1. Erstellen Sie eine Adobe Campaign-spezifische Konfigurationsdatei im Ordner `/etc/httpd/conf.d/` . Beispiel `CampaignApache.conf`

1. Fügen Sie für **RHEL7** die folgenden Anweisungen in die Datei ein:

   ```
   LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
   Include /usr/local/neolane/nl6/conf/apache_neolane.conf
   ```

1. Für **RHEL7**:

   Fügen Sie die Datei `/etc/systemd/system/httpd.service` mit folgendem Inhalt hinzu:

   ```
   .include /usr/lib/systemd/system/httpd.service
   
   [Service]
   Environment=USERPATH=/usr/local/neolane LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib
   ```

   Aktualisieren Sie das von systemd verwendete Modul:

   ```
   systemctl daemon-reload
   ```

1. Fügen Sie dann Adobe Campaign-Operatoren zur Gruppe der Apache-Operatoren hinzu und umgekehrt, indem Sie den Befehl ausführen:

   ```
   usermod -a -G neolane apache
   usermod -a -G apache neolane
   ```

   Die zu verwendenden Gruppennamen hängen von der Konfiguration von Apache ab.

1. Führen Sie Apache und den Adobe Campaign-Server aus.

   Für RHEL7:

   ```
   systemctl start httpd
   systemctl start nlserver
   ```

## Starten des Webservers und Testen der Konfiguration{#launching-the-web-server-and-testing-the-configuration}

Sie können die Konfiguration jetzt testen, indem Sie Apache starten. Das Adobe Campaign-Modul sollte jetzt sein Banner in der Konsole anzeigen (zwei Banner auf bestimmten Betriebssystemen):

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

Überprüfen Sie als Nächstes, ob die Antwort durch Senden einer Test-URL erfolgt.

Sie können dies über die Befehlszeile testen, indem Sie Folgendes ausführen:

```
 telnet localhost 80  
```

Sie sollten Folgendes abrufen:

```
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
```

Geben Sie dann Folgendes ein:

```
GET /r/test
```

Die folgenden Informationen werden angezeigt:

```
<redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='' localHost='XXXX'/>
Connection closed by foreign host.
```

Sie können die URL [`https://<computer>`](https://myserver.adobe.com/r/test) auch über einen Webbrowser anfordern.

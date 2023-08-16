---
product: campaign
title: Integration in einen Webserver für Linux
description: Erfahren Sie, wie Sie Campaign in einen Webserver (Linux) integrieren.
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
badge-v7-prem: label="On-Premise und Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: 4f8ea358-a38d-4137-9dea-f398e60c5f5d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 8%

---

# Integration in einen Webserver für Linux{#integration-into-a-web-server-for-linux}



Adobe Campaign enthält Apache Tomcat, der über HTTP (und SOAP) als Einstiegspunkt im Anwendungsserver fungiert.

Sie können diesen integrierten Tomcat-Server verwenden, um HTTP-Anforderungen zu erfüllen.

In diesem Fall:

* Der standardmäßige Listening-Anschluss ist 8080. Informationen zu ihrer Änderung finden Sie unter [diesem Abschnitt](configure-tomcat.md).
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

   Stellen Sie sicher, dass **alias**, **authz_host** und **mime** -Module sind weiterhin aktiviert. Verwenden Sie dazu den folgenden Befehl:

   ```
   a2enmod  alias authz_host mime
   ```

1. Datei erstellen **nlsrv.load** in **/etc/apache2/mods-available** und fügen Sie den folgenden Inhalt ein:

   In Debian 8:

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. Datei erstellen **nlsrv.conf** in **/etc/apache2/mods-available** mit dem folgenden Befehl:

   ```
   ln -s /usr/local/[INSTALL]/nl6/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. Aktivieren Sie dieses Modul mit dem folgenden Befehl:

   ```
    a2enmod nlsrv
   ```

   Wenn Sie die **mod_rewrite** -Modul für Adobe Campaign-Seiten verwenden, müssen Sie die **nlsrv.load** und **nlsrv.conf** Dateien in **zz-nlsrv.load** und **zz-nlsrv.conf**. Um das Modul zu aktivieren, führen Sie den folgenden Befehl aus:

   ```
   a2enmod zz-nlsrv
   ```

1. Bearbeiten Sie die **/etc/apache2/envars** die folgenden Zeilen hinzufügen:

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

1. Im `httpd.conf` -Datei, aktivieren Sie die folgenden Apache-Module:

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

1. Erstellen Sie eine Adobe Campaign-spezifische Konfigurationsdatei im `/etc/httpd/conf.d/` Ordner. Beispiel `CampaignApache.conf`

1. Für **RHEL7** Fügen Sie der Datei die folgenden Anweisungen hinzu:

   ```
   LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
   Include /usr/local/neolane/nl6/conf/apache_neolane.conf
   ```

1. Für **RHEL7**:

   Fügen Sie die `/etc/systemd/system/httpd.service` -Datei mit folgendem Inhalt:

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

## Webserver starten und Konfiguration testen{#launching-the-web-server-and-testing-the-configuration}

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

Sie können auch die URL anfordern `https://myserver.adobe.com/r/test` von einem Webbrowser aus.

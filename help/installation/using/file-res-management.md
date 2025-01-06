---
product: campaign
title: Datei- und Ressourcenverwaltung
feature: Installation, Application Settings
description: Erfahren Sie, wie Sie die Datei- und Ressourcenverwaltung in Campaign konfigurieren
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 236afdfe-fb23-4ebb-b000-76e14bf01d9e
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 2%

---

# Datei- und Ressourcenverwaltung{#file-and-resmanagement}



## Upload-Dateiformat begrenzen {#limiting-uploadable-files}

Verwenden Sie das **uploadWhiteList**-Attribut, um die Dateitypen einzuschränken, die für den Upload auf den Adobe Campaign-Server verfügbar sind.

Dieses Attribut ist im **dataStore** der Datei **serverConf.xml** verfügbar. Alle in der Datei **serverConf.xml** verfügbaren Parameter werden in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.

Der Standardwert dieses Attributs ist **.+** und ermöglicht den Upload beliebiger Dateitypen.

Um die möglichen Formate zu begrenzen, ersetzen Sie den Attributwert durch einen gültigen regulären Java-Ausdruck. Sie können mehrere Werte eingeben, indem Sie sie durch ein Komma trennen.

Beispiel: **uploadWhiteList=&quot;.&#42;.png,.&#42;.jpg“** ermöglicht das Hochladen von PNG- und JPG-Formaten auf den Server. Andere Formate werden nicht akzeptiert.

Sie können das Hochladen wichtiger Dateien auch verhindern, indem Sie den Webserver konfigurieren. [Weitere Informationen](web-server-configuration.md)

>[!NOTE]
>
>Das **uploadWhiteList**-Attribut beschränkt die Dateitypen, die auf dem Adobe Campaign-Server hochgeladen werden können. Wenn der Veröffentlichungsmodus jedoch **Tracking-Server(**) oder **Andere(r) Adobe Campaign-Server** ist, muss das Attribut **uploadWhitelist** auch auf diesen Servern aktualisiert werden.

## Proxy-Verbindungskonfiguration {#proxy-connection-configuration}

Sie können den Campaign-Server über einen Proxy mit einem externen System verbinden, z. B **mithilfe einer Workflow** Aktivität vom Typ „Dateiübertragung“. Dazu müssen Sie den Abschnitt **proxyConfig** der Datei **serverConf.xml** mit einem bestimmten Befehl konfigurieren. Alle in der Datei **serverConf.xml** verfügbaren Parameter werden in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.

Die folgenden Proxy-Verbindungen sind möglich: HTTP, HTTPS, FTP, SFTP. Beachten Sie, dass ab Campaign-Version 20.2 die HTTP- und HTTPS-Protokollparameter nicht **verfügbar**. Diese Parameter werden weiter unten erwähnt, da sie in früheren Builds verfügbar bleiben - einschließlich 9032.

>[!CAUTION]
>
>Es wird nur der Standardauthentifizierungsmodus unterstützt. NTLM-Authentifizierung wird nicht unterstützt.
>
>SOCKS-Proxys werden nicht unterstützt.
>

Sie können den folgenden Befehl verwenden:

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

Protokollparameter können „http“, „https“ oder „ftp“ sein.

Wenn Sie FTP auf demselben Port wie HTTP/HTTPS-Traffic einrichten, können Sie Folgendes verwenden:

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

Die Optionen „http“ und „https“ werden nur verwendet, wenn der Protokollparameter „ftp“ ist und angeben, ob das Tunneling am angegebenen Port über HTTPS oder über HTTP durchgeführt wird.

Wenn Sie unterschiedliche Ports für FTP-/SFTP- und HTTP/HTTPS-Traffic über den Proxy-Server verwenden, sollten Sie den Protokollparameter „ftp“ einstellen.


Beispiel:

```
nlserver config -setproxy:ftp/198.51.100.0:8080/user:’http’
```

Geben Sie dann das Kennwort ein.

HTTP-Verbindungen werden im ProxyHTTP-Parameter definiert:

```
<proxyConfig enabled=“1” override=“localhost*” useSingleProxy=“0”>
<proxyHTTP address=“198.51.100.0" login=“user” password=“*******” port=“8080”/>
</proxyConfig>
```

HTTPS-Verbindungen werden im Parameter proxyHTTPS definiert:

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyHTTPS address=“198.51.100.0” login=“user” password=“******” port=“8080"/>
</proxyConfig>
```

FTP-/FTPS-Verbindungen werden im ProxyFTP-Parameter definiert:

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

Wenn Sie denselben Proxy für mehrere Verbindungstypen verwenden, wird nur der Proxy-HTTP definiert, wobei useSingleProxy auf „1“ oder „true“ gesetzt ist.

Wenn Sie interne Verbindungen haben, die nicht über den Proxy gehen sollen, fügen Sie diese im Parameter „override“ hinzu.

Wenn Sie die Proxy-Verbindung vorübergehend deaktivieren möchten, setzen Sie den enabled-Parameter auf „false“ oder „0“.

Wenn Sie den iOS HTTP/2-Connector über einen Proxy verwenden müssen, werden die folgenden HTTP-Proxy-Modi unterstützt:

* HTTP ohne Authentifizierung
* HTTP-Standardauthentifizierung

Um den Proxy-Modus zu aktivieren, muss die folgende Änderung in der `serverconf.xml`-Datei vorgenommen werden:

```
<nmac useHTTPProxy="true">
```

Weitere Informationen zu diesem iOS HTTP/2-Connector finden Sie auf [Seite](../../delivery/using/about-mobile-app-channel.md).

## Öffentliche Ressourcen verwalten {#managing-public-resources}

Um öffentlich verfügbar zu sein, müssen die in E-Mails verwendeten Bilder und die mit den Kampagnen verknüpften öffentlichen Ressourcen auf einem extern zugänglichen Server vorhanden sein. Sie können dann für externe Empfänger oder Benutzer verfügbar sein. [Weitere Informationen](../../installation/using/deploying-an-instance.md#managing-public-resources).

Öffentliche Ressourcen werden im Verzeichnis **/var/res/instance** des Adobe Campaign-Installationsverzeichnisses gespeichert.

Die entsprechende URL lautet: **http://server/res/instance** wobei **instance** der Name der Tracking-Instanz ist.

Sie können ein anderes Verzeichnis angeben, indem Sie der Datei **conf-`<instance>`.xml** einen Knoten hinzufügen, um den Speicher auf dem Server zu konfigurieren. Dies bedeutet, dass die folgenden Zeilen hinzugefügt werden:

```
<serverconf>
  <shared>
    <dataStore hosts="media*" lang="fra">
      <virtualDir name="images" path="/var/www/images"/>
     <virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)/"/>
    </dataStore>
  </shared>
</serverconf>
```

In diesem Fall sollte die neue URL für die öffentlichen Ressourcen im oberen Teil des Fensters des Bereitstellungsassistenten auf diesen Ordner verweisen.

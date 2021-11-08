---
product: campaign
title: Datei- und Ressourcenverwaltung
description: Erfahren Sie, wie Sie die Datei- und Ressourcenverwaltung in Campaign konfigurieren
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 236afdfe-fb23-4ebb-b000-76e14bf01d9e
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# Datei- und Ressourcenverwaltung{#file-and-resmanagement}

![](../../assets/v7-only.svg)

## Dateiformat des Uploads begrenzen {#limiting-uploadable-files}

Verwenden Sie die **uploadWhiteList** -Attribut, um die für den Upload auf den Adobe Campaign-Server verfügbaren Dateitypen zu beschränken.

Dieses Attribut ist im **dataStore** -Element **serverConf.xml** -Datei. Alle in der **serverConf.xml** sind in dieser [Abschnitt](../../installation/using/the-server-configuration-file.md).

Der Standardwert dieses Attributs ist **.+** und ermöglicht den Upload beliebiger Dateitypen.

Um die möglichen Formate einzuschränken, ersetzen Sie den Attributwert durch einen gültigen regulären Java-Ausdruck. Sie können mehrere Werte eingeben, indem Sie sie durch ein Komma trennen.

Beispiel: **uploadWhiteList=&quot;.*.png,*.jpg&quot;** ermöglicht Ihnen das Hochladen von PNG- und JPG-Formaten auf den Server. Es werden keine anderen Formate akzeptiert.

>[!NOTE]
>
>In Internet Explorer muss der vollständige Dateipfad durch den regulären Ausdruck überprüft werden.

Sie können auch verhindern, dass wichtige Dateien hochgeladen werden, indem Sie den Webserver konfigurieren. [Weitere Informationen](web-server-configuration.md)

## Proxy-Verbindungskonfiguration {#proxy-connection-configuration}

Sie können den Campaign-Server über einen Proxy mit einem externen System verbinden, indem Sie eine **Dateiübertragung** Workflow-Aktivität. Dazu müssen Sie die **proxyConfig** Abschnitt **serverConf.xml** Datei über einen bestimmten Befehl. Alle in der Variablen **serverConf.xml** sind in dieser [Abschnitt](../../installation/using/the-server-configuration-file.md).

Die folgenden Proxy-Verbindungen sind möglich: HTTP, HTTPS, FTP, SFTP. Bitte beachten Sie, dass ab Campaign-Version 20.2 die HTTP- und HTTPS-Protokollparameter **nicht mehr verfügbar**. Diese Parameter werden weiter unten erwähnt, da sie in früheren Builds - einschließlich 9032 - weiterhin verfügbar sind.

>[!CAUTION]
>
>Nur der grundlegende Authentifizierungsmodus wird unterstützt. Die NTLM-Authentifizierung wird nicht unterstützt.
>
>SOCKS-Proxys werden nicht unterstützt.

Sie können den folgenden Befehl verwenden:

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

Protokollparameter können &quot;http&quot;, &quot;https&quot;oder &quot;ftp&quot;sein.

Wenn Sie FTP für denselben Port wie HTTP/HTTPS-Traffic einrichten, können Sie Folgendes verwenden:

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

Die Optionen &quot;http&quot;und &quot;https&quot;werden nur verwendet, wenn der Protokollparameter &quot;ftp&quot;ist und angibt, ob die Tunnelung am angegebenen Port über HTTPS oder HTTP erfolgt.

Wenn Sie für FTP/SFTP- und HTTP/HTTPS-Traffic über den Proxyserver unterschiedliche Ports verwenden, sollten Sie den Protokollparameter &quot;ftp&quot;festlegen.


Beispiel:

```
nlserver config -setproxy:ftp/198.51.100.0:8080/user:’http’
```

Geben Sie dann das Kennwort ein.

HTTP-Verbindungen werden im Parameter proxyHTTP definiert:

```
<proxyConfig enabled=“1” override=“localhost*” useSingleProxy=“0”>
<proxyHTTP address=“198.51.100.0" login=“user” password=“*******” port=“8080”/>
</proxyConfig>
```

HTTPS-Verbindungen werden im ProxyHTTPS-Parameter definiert:

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyHTTPS address=“198.51.100.0” login=“user” password=“******” port=“8080"/>
</proxyConfig>
```

FTP-/FTPS-Verbindungen werden im Parameter proxyFTP definiert:

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

Wenn Sie denselben Proxy für mehrere Verbindungstypen verwenden, wird nur proxyHTTP mit useSingleProxy definiert, dessen Wert auf &quot;1&quot; oder &quot;true&quot; festgelegt ist.

Wenn Sie interne Verbindungen haben, die durch den Proxy gehen sollen, fügen Sie sie im Parameter override hinzu.

Wenn Sie die Proxy-Verbindung vorübergehend deaktivieren möchten, setzen Sie den aktivierten Parameter auf &quot;false&quot; oder &quot;0&quot;.

Wenn Sie den iOS HTTP/2-Connector über einen Proxy verwenden müssen, werden die folgenden HTTP-Proxymodi unterstützt:

* HTTP ohne Authentifizierung
* Grundlegende HTTP-Authentifizierung

Um den Proxy-Modus zu aktivieren, muss die folgende Änderung im `serverconf.xml` Datei:

```
<nmac useHTTPProxy="true">
```

Weitere Informationen zu diesem iOS HTTP/2-Connector finden Sie in diesem [page](../../delivery/using/about-mobile-app-channel.md).

## Verwalten öffentlicher Ressourcen {#managing-public-resources}

Um öffentlich verfügbar zu sein, müssen die Bilder, die in E-Mails und öffentlichen Ressourcen verwendet werden, die mit Kampagnen verknüpft sind, auf einem extern zugänglichen Server vorhanden sein. Sie können dann externen Empfängern oder Benutzern zur Verfügung stehen. [Weitere Informationen](../../installation/using/deploying-an-instance.md#managing-public-resources).

Öffentliche Ressourcen werden im **/var/res/instance** Ordner des Adobe Campaign-Installationsordners.

Die entsprechende URL lautet: **http://server/res/instance** where **instance** ist der Name der Tracking-Instanz.

Sie können einen anderen Ordner angeben, indem Sie dem **conf-`<instance>`.xml** -Datei, um den Speicher auf dem Server zu konfigurieren. Dies bedeutet, dass die folgenden Zeilen hinzugefügt werden:

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

In diesem Fall sollte die im oberen Teil des Fensters des Softwareverteilungs-Assistenten angegebene neue URL für die öffentlichen Ressourcen auf diesen Ordner verweisen.

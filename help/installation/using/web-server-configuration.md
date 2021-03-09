---
solution: Campaign Classic
product: campaign
title: Konfiguration des Webservers
description: Erfahren Sie mehr über die Best Practices zur Konfiguration von Webservern.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 32%

---


# Konfiguration des Webservers {#web-server-configuration}

Nachstehend finden Sie einige der wichtigsten Best Practices für die Konfiguration des Webservers (Apache/IIS).

* Ändern Sie Standard-Fehlerseiten.

* Alte SSL-Version und -Ziffern deaktivieren:

   **Bearbeiten Sie auf Apache** /etc/apache2/mods-available/ssl.conf. Hier ein Beispiel:

   * SSLProtocol all -SSLv2 -SSLv3 -TLSv1
   * SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1

   **Führen Sie auf IIS**  (siehe  [Dokumentation](https://support.microsoft.com/en-us/kb/245030)) die folgende Konfiguration durch:

   * Fügen Sie einen Registrierungs-Unterschlüssel in HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL hinzu.
   * Damit das System die Protokolle verwenden kann, die nicht standardmäßig ausgehandelt werden (z. B. TLS 1.2), ändern Sie die DWORD-Wertdaten des DisabledByDefault-Werts in den folgenden Registrierungsschlüsseln unter dem Schlüssel **Protokolle** in 0x0:

      SCHANNEL\Protocols\TLS 1.2\Client

      SCHANNEL\Protocols\TLS 1.2\Server
   **Deaktivieren Sie SSL x.0**

   SCHANNEL\Protocols\SSL 3.0\Client: DisabledByDefault: DWORD (32-Bit) Wert zu 1

   SCHANNEL\Protocols\SSL 3.0\Server: Enabled: DWORD (32-Bit) Wert zu 0

* Entfernen Sie die **TRACE**-Methode:

   **Bearbeiten Sie auf Apache** unter /etc/apache2/conf.d/security: TraceEnable  **Off**

   **Führen Sie auf IIS**  (siehe  [Dokumentation](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)) die folgende Konfiguration durch:

   * Achten Sie darauf, dass der **Request-Filtering**-Rollendienst oder die entsprechende Funktion installiert ist.
   * Klicken Sie im Bereich **Anforderungsfilter** auf die Registerkarte HTTP-Verbs und dann auf Verb ablehnen. Geben Sie im Aktionsbereich im Dialogfeld &quot;Öffnen&quot;TRACE ein.

* Entfernen Sie das Banner:

   **Bearbeiten Sie auf Apache** /etc/apache2/conf.d/security:

   * ServerSignature auf **Off**
   * ServerTokens auf **Prod**

   **Führen Sie auf IIS**  (siehe  [Dokumentation](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)) die folgende Konfiguration durch:

   * Installieren Sie **URLScan**.
   * Ändern Sie die Datei **Urlscan.ini** in **RemoveServerHeader=1**.


* Begrenzen Sie die Größe der Abfrage, um zu verhindern, dass wichtige Dateien hochgeladen werden.

   **Fügen Sie auf Apache**  (siehe  [Dokumentation](http://httpd.apache.org/docs/2.2/mod/core.html#limitrequestbody)) die  **** LimitRequestBodydirektive (Größe in Byte) in / Verzeichnis hinzu.

   ```
   <Directory />
       Options FollowSymLinks
       AllowOverride None
       LimitRequestBody 10485760
   </Directory>
   ```

   **Stellen Sie auf IIS**  (siehe  [Dokumentation](http://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)) die Optionen  **maxAllowedContentLength** (maximal zulässige Inhaltslänge) in den Inhaltsfilteroptionen ein.

Verwandte Themen:

* [Adobe Marketing Cloud Compliance-Übersicht](https://marketing.adobe.com/resources/help/en_US/xref/Adobe-Marketing-Cloud-Privacy-and-Security-Overview.pdf)  (PDF)
* [Adobe Campaign Security - Überblick](https://wwwimages.adobe.com/content/dam/acom/en/marketing-cloud/campaign/pdfs/54658.en.campaign.wp.adb-security.pdf)  (PDF)

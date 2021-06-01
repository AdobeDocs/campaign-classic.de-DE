---
product: campaign
title: Konfiguration des Webservers
description: Erfahren Sie mehr über die wichtigsten Best Practices bei der Konfiguration von Webservern.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 34%

---

# Konfiguration des Webservers {#web-server-configuration}

Nachfolgend finden Sie einige der wichtigsten Best Practices im Zusammenhang mit der Konfiguration des Webservers (Apache/IIS).

* Ändern Sie Standard-Fehlerseiten.

* Alte SSL-Version und -Ziffern deaktivieren:

   **Bearbeiten Sie auf Apache** /etc/apache2/mods-available/ssl.conf. Im Folgenden finden Sie ein Beispiel:

   * SSLProtocol all -SSLv2 -SSLv3 -TLSv1
   * SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1

   **Führen Sie auf IIS**  (siehe die  [Dokumentation](https://support.microsoft.com/en-us/kb/245030)) die folgende Konfiguration durch:

   * Fügen Sie einen Registrierungs-Unterschlüssel in HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL hinzu.
   * Damit das System die Protokolle verwenden kann, die nicht standardmäßig ausgehandelt werden (z. B. TLS 1.2), ändern Sie in den folgenden Registrierungsschlüsseln unter dem Schlüssel **Protokolle** die DWORD-Wertdaten des Wertes DisabledByDefault in 0x0:

      SCHANNEL\Protocols\TLS 1.2\Client

      SCHANNEL\Protocols\TLS 1.2\Server
   **Deaktivieren Sie SSL x.0**

   SCHANNEL\Protocols\SSL 3.0\Client: DisabledByDefault: DWORD (32-Bit) Wert zu 1

   SCHANNEL\Protocols\SSL 3.0\Server: Enabled: DWORD (32-Bit) Wert zu 0

* Entfernen Sie die **TRACE**-Methode:

   **Bearbeiten Sie auf Apache** in /etc/apache2/conf.d/security: TraceEnable  **Off**

   **Führen Sie auf IIS**  (siehe die  [Dokumentation](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)) die folgende Konfiguration durch:

   * Achten Sie darauf, dass der **Request-Filtering**-Rollendienst oder die entsprechende Funktion installiert ist.
   * Klicken Sie im Bereich **Request Filtering** auf die Registerkarte HTTP verbs und dann auf Deny Verb . Geben Sie im Bereich &quot;Aktionen&quot;im Dialogfeld &quot;Öffnen&quot;TRACE ein.

* Entfernen Sie das Banner:

   **Bearbeiten Sie auf Apache** /etc/apache2/conf.d/security:

   * ServerSignature auf **Off**
   * ServerTokens auf **Prod**

   **Führen Sie auf IIS** die folgende Konfiguration durch:

   * Installieren Sie **URLScan**.
   * Ändern Sie die Datei **Urlscan.ini** in **RemoveServerHeader=1**.


* Begrenzen Sie die Größe der Abfrage, um zu verhindern, dass wichtige Dateien hochgeladen werden.

   **Fügen Sie auf Apache** die Anweisung  **** LimitRequestBodydirektion (Größe in Byte) in / Verzeichnis hinzu.

   ```
   <Directory />
       Options FollowSymLinks
       AllowOverride None
       LimitRequestBody 10485760
   </Directory>
   ```

   **Legen Sie auf IIS**  (siehe die  [Dokumentation](http://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)) die  **maxAllowedContentLength**  (maximal zulässige Inhaltslänge) in den Inhaltsfilteroptionen fest.

Verwandte Themen:

* [Adobe Marketing Cloud Compliance Overview](https://marketing.adobe.com/resources/help/en_US/xref/Adobe-Marketing-Cloud-Privacy-and-Security-Overview.pdf)  (PDF)
* [Adobe Campaign-Sicherheitsübersicht](https://wwwimages.adobe.com/content/dam/acom/en/marketing-cloud/campaign/pdfs/54658.en.campaign.wp.adb-security.pdf)  (PDF)

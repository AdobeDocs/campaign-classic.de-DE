---
product: campaign
title: Konfiguration des Webservers
description: Erfahren Sie mehr über die wichtigsten Best Practices für die Konfiguration von Webservern
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 31%

---

# Konfiguration des Webservers {#web-server-configuration}



Nachfolgend finden Sie einige der wichtigsten Best Practices im Zusammenhang mit der Konfiguration des Webservers (Apache/IIS).

* Ändern Sie Standard-Fehlerseiten.

* Alte SSL-Version und -Ziffern deaktivieren:

  **Auf Apache**, bearbeiten Sie /etc/apache2/mods-available/ssl.conf. Im Folgenden finden Sie ein Beispiel:

   * SSLProtocol all -SSLv2 -SSLv3 -TLSv1
   * SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1

  **Bei IIS** (siehe [Dokumentation](https://support.microsoft.com/en-us/kb/245030)), führen Sie die folgende Konfiguration durch:

   * Fügen Sie einen Registrierungs-Unterschlüssel in HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL hinzu.
   * Damit das System die Protokolle verwenden kann, die nicht standardmäßig ausgehandelt werden (z. B. TLS 1.2), ändern Sie die DWORD-Wertdaten des Wertes DisabledByDefault in 0x0 in den folgenden Registrierungsschlüsseln unter **Protokolle** key:

     SCHANNEL\Protocols\TLS 1.2\Client

     SCHANNEL\Protocols\TLS 1.2\Server

  **Deaktivieren Sie SSL x.0**

  SCHANNEL\Protocols\SSL 3.0\Client: DisabledByDefault: DWORD (32-Bit) Wert zu 1

  SCHANNEL\Protocols\SSL 3.0\Server: Enabled: DWORD (32-Bit) Wert zu 0

* Entfernen Sie die **TRACE**-Methode:

  **Auf Apache**, bearbeiten Sie in /etc/apache2/conf.d/security: TraceEnable **Aus**

  **Bei IIS** (siehe [Dokumentation](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)), führen Sie die folgende Konfiguration durch:

   * Achten Sie darauf, dass der **Request-Filtering**-Rollendienst oder die entsprechende Funktion installiert ist.
   * Im **Anforderungsfilterung** auf die Registerkarte &quot;HTTP Verbs&quot;und klicken Sie dann auf &quot;Verb verweigern&quot;. Geben Sie im Bereich &quot;Aktionen&quot;im Dialogfeld &quot;Öffnen&quot;TRACE ein.

* Entfernen Sie das Banner:

  **Auf Apache**, bearbeiten Sie /etc/apache2/conf.d/security:

   * ServerSignature auf **Off**
   * ServerTokens auf **Prod**

  **Bei IIS**, führen Sie die folgende Konfiguration durch:

   * Installieren Sie **URLScan**.
   * Ändern Sie die Datei **Urlscan.ini** in **RemoveServerHeader=1**.

* Begrenzen Sie die Größe der Abfrage, um zu verhindern, dass wichtige Dateien hochgeladen werden.

  **Auf Apache**, fügen Sie die **LimitRequestBody** Anweisung (Größe in Byte) in / Verzeichnis.

  ```
  <Directory />
      Options FollowSymLinks
      AllowOverride None
      LimitRequestBody 10485760
  </Directory>
  ```

  **Bei IIS** (siehe [Dokumentation](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)), legen Sie die **maxAllowedContentLength** (maximal zulässige Inhaltslänge) in den Inhaltsfilteroptionen.

Verwandte Themen:

* [Übersicht über die Einhaltung von Adobe Marketing Cloud](https://experienceleague.adobe.com/docs/core-services/assets/Adobe-Marketing-Cloud-Privacy-and-Security-Overview.pdf) (PDF)
* [Sicherheitsübersicht für Adobe Campaign](https://www.adobe.com/content/dam/cc/en/security/pdfs/ADB-CampaignSecurity-WP.pdf) (PDF)

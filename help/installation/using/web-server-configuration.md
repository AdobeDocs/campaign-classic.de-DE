---
product: campaign
title: Konfiguration des Webservers
description: Erfahren Sie mehr über die wichtigsten Best Practices für die Konfiguration von Webservern
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
source-git-commit: dba90a154e08400ae6ab6478623a50d48d72207c
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 32%

---

# Konfiguration des Webservers {#web-server-configuration}



Nachfolgend finden Sie einige der wichtigsten Best Practices im Zusammenhang mit der Konfiguration des Webservers (Apache/IIS).

* Ändern Sie Standard-Fehlerseiten.

* Alte SSL-Version und -Ziffern deaktivieren:

  **Bearbeiten Sie auf Apache** /etc/apache2/mods-available/ssl.conf. Hier ein Beispiel:

   * `SSLProtocol all -SSLv2 -SSLv3 -TLSv1`
   * `SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1`

  **Führen Sie auf IIS** (siehe die [Dokumentation](https://support.microsoft.com/en-us/kb/245030)) die folgende Konfiguration durch:

   * Fügen Sie einen Registrierungs-Unterschlüssel in HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL hinzu.
   * Damit das System die Protokolle verwenden kann, die nicht standardmäßig ausgehandelt werden (z. B. TLS 1.2), ändern Sie in den folgenden Registrierungsschlüsseln unter dem Schlüssel **Protokolle** die DWORD-Wertdaten des Wertes DisabledByDefault in 0x0:

     SCHANNEL\Protokolle\TLS 1.2\Client

     SCHANNEL\Protokolle\TLS 1.2\Server

  **SSL x.0** deaktivieren

  SCHANNEL\Protocols\SSL 3.0\Client: DisabledByDefault: DWORD (32-Bit) Wert zu 1

  SCHANNEL\Protocols\SSL 3.0\Server: Enabled: DWORD (32-Bit) Wert zu 0

* Entfernen Sie die **TRACE**-Methode:

  **Bearbeiten Sie auf Apache** in /etc/apache2/conf.d/security: TraceEnable **Off**

  **Führen Sie auf IIS** (siehe die [Dokumentation](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)) die folgende Konfiguration durch:

   * Achten Sie darauf, dass der **Request-Filtering**-Rollendienst oder die entsprechende Funktion installiert ist.
   * Klicken Sie im Bereich **Anforderungsfilter** auf die Registerkarte &quot;HTTP-Verben&quot;und dann auf &quot;Verb verweigern&quot;. Geben Sie im Bereich &quot;Aktionen&quot;im Dialogfeld &quot;Öffnen&quot;TRACE ein.

* Entfernen Sie das Banner:

  **Bearbeiten Sie auf Apache** /etc/apache2/conf.d/security:

   * ServerSignature auf **Off**
   * ServerTokens auf **Prod**

  **Führen Sie auf IIS** die folgende Konfiguration durch:

   * Installieren Sie **URLScan**.
   * Ändern Sie die Datei **Urlscan.ini** in **RemoveServerHeader=1**.

* Begrenzen Sie die Größe der Abfrage, um zu verhindern, dass wichtige Dateien hochgeladen werden.

  **Fügen Sie auf Apache** die Anweisung **LimitRequestBody** (Größe in Byte) in / Verzeichnis hinzu.

  ```
  <Directory />
      Options FollowSymLinks
      AllowOverride None
      LimitRequestBody 10485760
  </Directory>
  ```

  **Legen Sie auf IIS** (siehe die [Dokumentation](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)) die **maxAllowedContentLength** (maximal zulässige Inhaltslänge) in den Inhaltsfilteroptionen fest.

Verwandte Themen:

* [Adobe Marketing Cloud Compliance Overview](https://experienceleague.adobe.com/en/docs/experience-platform/landing/governance-privacy-security/overview#privacy)
* [Adobe Campaign-Sicherheitsübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/landing/governance-privacy-security/overview#security)

---
product: campaign
title: Technote – Aktivieren von Microsoft Edge Chromium in Ihrer Campaign-Umgebung
description: Campaign – Edge Chromium
feature: Technote, Upgrade
exl-id: 22f4cbaf-ca37-47b9-b7dd-1ee73d5b348d
source-git-commit: 8734e6ef26a7342042a5242d54854b7d3a5e6244
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 92%

---

# Wie Sie Microsoft Edge Chromium in Ihrer Umgebung aktivieren {#edge-conf}

## Was hat sich geändert?

Nach dem Auslaufen von Microsoft Internet Explorer 11 verwendet die HTML-Render-Engine für Dashboards in der Client-Konsole nun Edge Chromium, beginnend mit Campaign Classic v7.3.

Zusätzlich zur Installation der Microsoft Edge Webview 2-Laufzeit, die jetzt [für jede Client-Konsolen-Installation erforderlich ist](../../installation/using/installing-the-client-console.md#webview), muss Microsoft Edge Chromium in Ihren Instanzen aktiviert sein.

>[!NOTE]
>
>Nach der Aktivierung von Microsoft Edge Chromium wird die `Ctrl+F` (Windows) oder `Command+F` (Mac) verwenden, um das Suchdialogfeld des Browsers zu öffnen, funktioniert nicht mehr.

## Sind Sie betroffen?

Wenn Ihre Umgebung auf Campaign Classic v7.3 (oder höher) aktualisiert wurde, sind Sie betroffen.

## Wie wird die Aktualisierung durchgeführt?

* Wenn Sie als Kundin oder Kunde **gehostet** werden, hat Adobe in Ihren Instanzen bereits Microsoft Edge Chromium aktiviert. Es sind keine weiteren Maßnahmen erforderlich.

* Als **On-Premise/Hybrid**-Kundin oder -Kunde müssen Sie Microsoft Edge Chromium in Ihren Instanzen aktivieren.

  Bei der Aktualisierung auf Campaign Classic v7.3 (und höher) ist ein neues `webView2Mode`-Attribut in der Konfigurationsdatei `serverConf.xml` des Campaign-Servers verfügbar. Dieses Attribut muss aktiviert sein.

  Gehen Sie dazu für alle Ihre Umgebungen (MKT, MID, RT) wie folgt vor:

   1. Bearbeiten Sie die Konfigurationsdatei des Campaign-Servers (`serverConf.xml`)
   1. Legen Sie im `<web>`-Modul `webView2Mode = "1"` fest
   1. Führen Sie den folgenden Befehl aus, um die Server-Konfiguration neu zu laden:

      ```
      nlserver config -reload
      ```

   1. Führen Sie den folgenden Befehl aus, um den Webserver neu zu starten:

      ```
      nlserver restart web
      ```

   1. Wenn Ihre Umgebung Apache als Webserver verwendet, führen Sie den folgenden Befehl aus, um Apache neu zu starten:

      ```
      /etc/init.d/apache2 restart
      ```


>[!NOTE]
>
>Wenden Sie sich bei Fragen zu diesen Änderungen an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>

## Verwandte Themen

* [Upgrade Ihrer Umgebung](../../production/using/build-upgrade.md)
* [Häufig gestellte Fragen zum Build-Upgrade](../../platform/using/faq-build-upgrade.md)
* [Installieren der Campaign-Client-Konsole](../../installation/using/installing-the-client-console.md)

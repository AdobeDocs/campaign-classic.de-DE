---
product: campaign
title: Technote - Aktivierung von Microsoft Edge Chromium in Ihrer Campaign-Umgebung
description: Campaign - Edge Chromium
hide: true
hidefromtoc: true
source-git-commit: d9f57d4e5b6f880907040344ece40546456a2321
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 16%

---


# Aktivieren von Microsoft Edge Chromium in Ihrer Umgebung {#edge-conf}

![](../../assets/v7-only.svg)


## Was hat sich geändert?

Nach dem Ende der Nutzungsdauer von Microsoft Internet Explorer 11 verwendet die HTML-Rendering-Engine für Adobe Services (Anmeldeseite) in der Clientkonsole jetzt Microsoft Edge Chromium und startet Campaign Classic v7.3.

Zusätzlich zur Installation der Microsoft Edge Webview 2-Laufzeit, die jetzt [für jede Client Console-Installation erforderlich](../../installation/using/installing-the-client-console.md#webview), muss Microsoft Edge Chromium in Ihren Instanzen aktiviert sein.

## Sind Sie betroffen?

Wenn Ihre Umgebung auf Campaign Classic v7.3 (oder höher) aktualisiert wurde, sind Sie betroffen.

## Wie wird die Aktualisierung durchgeführt?

* Als **gehostet** -Kunde, Adobe hat Microsoft Edge Chromium bereits auf Ihren Instanzen aktiviert.

* Als **On-Premise/Hybrid** -Kunde, müssen Sie Microsoft Edge Chromium in Ihren Instanzen aktivieren.

   Bei der Aktualisierung auf Campaign Classic v7.3 (und höher) wird eine neue `webView2Mode` Attribut ist in der Konfigurationsdatei des Campaign-Servers verfügbar `serverConf.xml`. Dieses Attribut muss aktiviert sein.

   Gehen Sie dazu wie folgt auf alle Ihre Umgebungen (MKT, MID, RT) vor:

   1. Bearbeiten Sie die Konfigurationsdatei des Campaign-Servers (`serverConf.xml`)
   1. Im `<web>` Modul, Satz `webView2Mode = "1"`
   1. Serverkonfiguration neu laden

      ```
      nlserver config -reload
      ```

   1. Webserver neu starten

      ```
      nlserver restart web
      ```

   1. Wenn Ihre Umgebung auf Apache ausgeführt wird, starten Sie Apache neu

      ```
      /etc/init.d/apache2 restart
      ```


>[!NOTE]
>
>Wenden Sie sich bei Fragen zu diesen Änderungen an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Verwandte Themen

* [Upgrade Ihrer Umgebung](../../production/using/build-upgrade.md)
* [Häufig gestellte Fragen zum Build-Upgrade](../../platform/using/faq-build-upgrade.md)
* [Campaign-Client-Konsole installieren](../../installation/using/installing-the-client-console.md)


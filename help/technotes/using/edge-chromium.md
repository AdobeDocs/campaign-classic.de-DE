---
product: campaign
title: Technote - Aktivierung von Microsoft Edge Chromium in Ihrer Campaign-Umgebung
description: Campaign - Edge Chromium
source-git-commit: a4a5e014d8055cf29bdbf7debb72eb20388c9b19
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 15%

---


# Aktivieren von Microsoft Edge Chromium in Ihrer Umgebung {#edge-conf}

![](../../assets/v7-only.svg)


## Was hat sich geändert?

Nach dem Ende der Nutzungsdauer von Microsoft Internet Explorer 11 verwendet die HTML-Rendering-Engine für Dashboards in der Clientkonsole Edge Chromium und startet Campaign Classic v7.3.

Zusätzlich zur Installation der Microsoft Edge Webview 2-Laufzeit, die jetzt [für jede Client Console-Installation erforderlich](../../installation/using/installing-the-client-console.md#webview), muss Microsoft Edge Chromium in Ihren Instanzen aktiviert sein.

## Sind Sie betroffen?

Wenn Ihre Umgebung auf Campaign Classic v7.3 (oder höher) aktualisiert wurde, sind Sie betroffen.

## Wie wird die Aktualisierung durchgeführt?

* Als **gehostet** -Kunde, Adobe hat Microsoft Edge Chromium bereits auf Ihren Instanzen aktiviert. Es sind keine weiteren Maßnahmen erforderlich.

* Als **On-Premise/Hybrid** -Kunde, müssen Sie Microsoft Edge Chromium in Ihren Instanzen aktivieren.

   Bei der Aktualisierung auf Campaign Classic v7.3 (und höher) wird eine neue `webView2Mode` Attribut ist in der Konfigurationsdatei des Campaign-Servers verfügbar `serverConf.xml`. Dieses Attribut muss aktiviert sein.

   Gehen Sie dazu wie folgt auf alle Ihre Umgebungen (MKT, MID, RT) vor:

   1. Bearbeiten Sie die Konfigurationsdatei des Campaign-Servers (`serverConf.xml`)
   1. Im `<web>` Modul, Satz `webView2Mode = "1"`
   1. Führen Sie den folgenden Befehl aus, um die Serverkonfiguration neu zu laden:

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

## Verwandte Themen

* [Upgrade Ihrer Umgebung](../../production/using/build-upgrade.md)
* [Häufig gestellte Fragen zum Build-Upgrade](../../platform/using/faq-build-upgrade.md)
* [Campaign-Client-Konsole installieren](../../installation/using/installing-the-client-console.md)


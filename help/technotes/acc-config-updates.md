---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 849a95c718f9dc58aeabc8a49d3bf8290ea79b86
workflow-type: tm+mt
source-wordcount: '1031'
ht-degree: 14%

---


# Adobe Campaign-Konfigurationsaktualisierungen - März 2021 {#acc-config-updates}

Sie müssen Ihre Infrastruktur und Einstellungen mit den neuesten Builds und Produktverbesserungen aktualisieren. Diese Korrekturen sind obligatorisch, um die Dienstkontinuität und Sicherheit zu gewährleisten. Darüber hinaus müssen Sie Ihre Implementierung an Änderungen von Drittanbietern anpassen.

Als gehosteter Kunde informiert Sie die Adobe in regelmäßigen Abständen über erforderliche Buildaktualisierungen. Sie müssen ein Upgrade gemäß den Empfehlungen durchführen, um die Einhaltung der Vorschriften sicherzustellen.

Als Kunde vor Ort/Hybrid müssen Sie aus Sicherheitsgründen auf eine der auf dieser Seite aufgeführten Versionen aktualisieren. Darüber hinaus müssen einige manuelle Aufgaben durchgeführt werden, um sicherzustellen, dass Ihre Umgebung sicher ist und auf zukünftige Änderungen von Adobe- oder Drittanbietersystemen vorbereitet ist.

>[!NOTE]
>
>Wenden Sie sich bei Fragen zu diesen Änderungen an den [Adobe Kundendienst](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Sicherheitsaktualisierungen

Neueste Versionen der Kampagne enthalten eine Sicherheitskorrektur, die den Schutz vor Problemen mit der serverseitigen Anforderungsfälschung (SSRF) verstärkt. Weiterführende Informationen finden Sie auf [dieser Seite](https://helpx.adobe.com/de/security/products/campaign/apsb21-04.html).

**Sind Sie betroffen?**

Wenn sich Ihre Umgebung auf einem niedrigeren Build befindet als die unten aufgeführten, werden Sie davon betroffen sein:

* Gold Standard 11. [Mehr dazu](../rn/using/gold-standard.md)
* Campaign-Version 21.1.1. [Mehr dazu](../rn/using/latest-release.md)
* Campaign-Version 20.3.3. [Mehr dazu](../rn/using/release--20-3.md)
* Campaign-Version 20.2.4. [Mehr dazu](../rn/using/release--20-2.md)
* Campaign-Version 20.1.4. [Mehr dazu](../rn/using/release--20-1.md)
* Campaign-Version 19.2.4. [Mehr dazu](../rn/using/release--19-2.md)
* Campaign-Version 19.1.8. [Mehr dazu](../rn/using/release--19-1.md)

**Wie lässt sich das Update durchführen?**

Sie müssen auf eine der neueren Builds aktualisieren, die oben aufgeführt sind.

* Als Hybridkunde wird die Adobe die Mid-Sourcing-Instanz auf die neue Version aktualisieren, und es wird dringend empfohlen, auch deren Marketinginstanz zu aktualisieren.

   Der neue Build ist mit mindestens Campaign Classic 17.9 kompatibel. Um Sicherheitslücken zu vermeiden, empfiehlt Adobe jedoch dringend, alle Instanzen auf einen neuen Build zu aktualisieren. 

* Als lokaler Kunde werden Sie aufgefordert, die Marketing- und Mid-Sourcing-Instanzen auf einen neueren Build zu aktualisieren.

>[!CAUTION]
>
>Wenn Sie noch kein Upgrade durchführen können, müssen Sie sich an das Kundenservice-Team von Adobe wenden, um eine Sicherheitskorrektur für Ihre Instanzen durchzuführen.****


## Aktualisierung der Kampagne Client Console

Der neueste Gold Standard 11-Build behebt eine Regression, die die Verwendung einiger Komponenten der Client-Konsole verhinderte, z. B. die Datumsauswahl und die Bildverwaltung in Versänden. Die Konsolenaktualisierung ist obligatorisch.

[Weitere Informationen](../rn/using/gold-standard.md).

>[!NOTE]
>
>Die neue Client-Konsole für andere Versionen wird demnächst verfügbar sein.

## Adobe Identity Management System (IMS)-Update

Adobe Identity Service (IMS) beendet die Unterstützung alter Internet Explorer Versionen ab dem 30. Juni 2021 **.** [Weitere Informationen](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html).

Kampagne Client Console wurde aktualisiert, um die Kompatibilität mit Adobe IMS in den folgenden Kampagnen sicherzustellen:

**Sind Sie betroffen?**

Wenn Sie über ein Adobe ID](../integrations/using/about-adobe-id.md) über den Identitätsdienst (IMS) eine Verbindung zur Kampagne [herstellen, ist ein Upgrade auf eine der folgenden neuen Versionen obligatorisch:

* Gold Standard 11. [Mehr dazu](../rn/using/gold-standard.md)
* Campaign-Version 21.1.1. [Mehr dazu](../rn/using/latest-release.md)
* Campaign-Version 20.3.3. [Mehr dazu](../rn/using/release--20-3.md)
* Campaign-Version 20.2.4. [Mehr dazu](../rn/using/release--20-2.md)
* Campaign-Version 20.1.4. [Mehr dazu](../rn/using/release--20-1.md)
* Campaign-Version 19.2.4. [Mehr dazu](../rn/using/release--19-2.md)
* Campaign-Version 19.1.8. [Mehr dazu](../rn/using/release--19-1.md)

Diese Versionen enthalten ein neues Verbindungsprotokoll: Aktualisierung ist erforderlich, damit sowohl der Kampagne- als auch die Client-Konsole nach dem 30. Juni 2021 **eine Verbindung zur Kampagne herstellen können.**

**Wie lässt sich das Update durchführen?**

Als gehosteter Kunde ist keine Aktion erforderlich: Adobe hat Ihre Instanz(en) bereits auf eine neuere Version aktualisiert.

Als On-Premise-/Hybrid-Kunde müssen Sie auf eine der neueren Versionen aktualisieren, um von der neuen Client Console profitieren zu können und eine nahtlose Transition **vor dem 30. Juni 2021** sicherzustellen.

Sobald alle Instanzen aktualisiert wurden, muss auch die Client-Konsole auf diese Version aktualisiert werden.

* Näheres zum Zugriff auf die Adobe Softwareverteilung finden Sie [hier](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).

* [Erfahren Sie, wie Sie Kampagne Client Console](../installation/using/installing-the-client-console.md) installieren.

## Integration mit Experience Cloud-Triggern

Der veraltete Auth-Authentifizierungsdienst hat das Lebenszyklusende erreicht. Trigger-Integrationsauthentifizierung, die ursprünglich auf der Einrichtung der Auth-Authentifizierung für den Zugriff auf die Pipeline basiert, wurde in die Adobe I/O verschoben. Sie wird am 30. April 2021 **eingestellt.** [Weitere Informationen](https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md?mv=email).

**Sind Sie betroffen?**

Wenn Ihre Instanzen mit einer **älteren Version als Kampagne 19.1.8, 20.2.4, Gold Standard 11** ausgeführt werden, verwenden Sie eine ältere Version der Trigger-Integration mithilfe der Auth-Authentifizierung: **Sie müssen auf eine neuere Version aktualisieren und zu Adobe I/O** wechseln.

Die Aktualisierung auf eine der folgenden neuen Versionen ist obligatorisch:

* Gold Standard 11. [Mehr dazu](../rn/using/gold-standard.md)
* Campaign-Version 21.1.1. [Mehr dazu](../rn/using/latest-release.md)
* Campaign-Version 20.3.3. [Mehr dazu](../rn/using/release--20-3.md)
* Campaign-Version 20.2.4. [Mehr dazu](../rn/using/release--20-2.md)
* Campaign-Version 19.1.8. [Mehr dazu](../rn/using/release--19-1.md)

**Wie lässt sich das Update durchführen?**

Sobald die Instanzen auf eine neuere Version aktualisiert wurden, müssen alle Kunden dem [Verfahren folgen und in den neuen Authentifizierungsmodus wechseln. ](../integrations/using/configuring-adobe-io.md) Hierfür muss das neue Adoben I/O-Token generiert und in der Implementierung verwendet werden.  

Kunden mit Hybrid-Umgebungen müssen darüber hinaus sicherstellen, dass Pipeline auf einer Mid-Sourcing-Instanz konfiguriert ist. [Weitere Informationen](../integrations/using/configuring-pipeline.md).

[Erfahren Sie, wie Sie zu Adobe I/O wechseln](../integrations/using/configuring-adobe-io.md).

## APNs-Aktualisierungen

### API für HTTP/2-basierte APNs-Provider

Der Apple Push Notification Service (APNs) unterstützt das Legacy-Binärprotokoll ab dem 31. März 2021 **nicht mehr.** [Mehr dazu](https://developer.apple.com/news/?id=c88acm2b).

**Sind Sie betroffen?**

Wenn Ihre Instanzen auf einer **älteren Version als Kampagne 21.1,** ausgeführt werden und Push-Benachrichtigungen mit dem alten Apple-Binärprotokoll gesendet werden, müssen Sie auf die HTTP/2-basierte API des APNs-Providers aktualisieren.

**Wie lässt sich das Update durchführen?**

Als gehosteter Kunde ist keine Aktion erforderlich: Adobe hat Ihre Instanz(en) bereits auf die HTTP/2-basierte API aktualisiert.

Als lokal/gehosteter Kunde müssen Sie Ihre Konfiguration aktualisieren. [Erfahren Sie, wie Sie zu HTTP/2 migrieren.](https://helpx.adobe.com/de/campaign/kb/migrate-to-apns-http2.html)

### Aktualisierung des Stammzertifikats von APN

Am 29. März 2021 wirkt sich ein Infrastrukturupdate des Apple Push Notification Service (APNs) auf den Adobe Campaign Classic iOS-Kanal aus. Eine Änderung der Betriebssystemkonfiguration ist **obligatorisch**, um einen Ausfall des iOS-Push-Kanals zu vermeiden.

Erfahren Sie mehr über die APNs-Änderungen [auf dieser Seite](https://developer.apple.com/news/?id=7gx0a2lp).

**Sind Sie betroffen?**

Wenn Sie Kampagne zum Senden von Push-Benachrichtigungen auf iOS-Geräten verwenden, sind Sie davon betroffen.

**Wie lässt sich das Update durchführen?**

Als gehosteter Kunde ist keine Aktion erforderlich: Adobe hat das neue Stammzertifikat bereits in Ihre Umgebung integriert.

Als Vor-Ort-/Hybridkunde müssen Sie Ihre Konfiguration aktualisieren, um eine nahtlose Transition **vor dem 29. März 2021** sicherzustellen.

[Erfahren Sie, wie Sie das neue Zertifikat](ios-certificate-update.md) integrieren.


## Nützliche Links

* [Umgebung aktualisieren](../production/using/build-upgrade.md)
* [Häufig gestellte Fragen zum Build-Upgrade](../platform/using/faq-build-upgrade.md)
* [Campaign Classic-Build herunterladen](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html)
* [Neue Client-Konsole für Benutzer verfügbar machen](../installation/using/client-console-availability-for-windows.md)

---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 87844fae046dff69193d3462c802057499f406ef
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 11%

---


# Adobe Campaign-Konfigurationsaktualisierungen - März 2021 {#acc-config-updates}

Sie müssen Ihre Infrastruktur und Einstellungen mit den neuesten Builds und Produktverbesserungen aktualisieren. Diese Korrekturen sind obligatorisch, um die Dienstkontinuität und Sicherheit zu gewährleisten.

Kampagne Anwender müssen auf eine der folgenden Versionen aktualisieren:

* Gold Standard 11. [Mehr dazu](../rn/using/gold-standard.md)
* Campaign-Version 21.1.1. [Mehr dazu](../rn/using/latest-release.md)
* Campaign-Version 20.3.3. [Mehr dazu](../rn/using/release--20-3.md)
* Campaign-Version 20.2.4. [Mehr dazu](../rn/using/release--20-2.md)
* Campaign-Version 20.1.4. [Mehr dazu](../rn/using/release--20-1.md)
* Campaign-Version 19.2.4. [Mehr dazu](../rn/using/release--19-2.md)
* Campaign-Version 19.1.8. [Mehr dazu](../rn/using/release--19-1.md)

Diese Gebäude gewährleisten die Kontinuität bestimmter Kampagnen: Integration von Experience Cloud-Triggern, APNs-Authentifizierung und das neue Verbindungsprotokoll, das sich auf den Authentifizierungsmechanismus des Adobe Identity Management Service (IMS) auswirkt.

Als gehosteter Kunde ist keine Aktion erforderlich: Adobe besitzt die Build-Aktualisierung und Konfigurationsaktualisierungen für Sie.

Als Kunde vor Ort/Hybrid müssen Sie auf eine der oben aufgeführten Versionen aktualisieren. Darüber hinaus müssen Sie einige manuelle Aufgaben durchführen, um sicherzustellen, dass Ihre Umgebung sicher ist und auf zukünftige Änderungen von Adobe- oder Drittanbietersystemen vorbereitet ist.

## Sicherheitsaktualisierungen

Neueste Versionen der Kampagne enthalten eine Sicherheitskorrektur, die den Schutz vor Problemen mit der serverseitigen Anforderungsfälschung (SSRF) verstärkt. Weiterführende Informationen finden Sie auf [dieser Seite](https://helpx.adobe.com/de/security/products/campaign/apsb21-04.html).

**Sind Sie betroffen?**

Wenn sich Ihre Umgebung auf einem niedrigeren Build befindet als Kampagne 21.1, werden Sie davon betroffen sein.

**Wie lässt sich das Update durchführen?**

Sie müssen auf eine der neueren Builds aktualisieren, die oben aufgeführt sind.

* Als Hybridkunde wird die Adobe die Mid-Sourcing-Instanz auf die neue Version aktualisieren, und es wird dringend empfohlen, auch deren Marketinginstanz zu aktualisieren.

   Der neue Build ist mit mindestens Campaign Classic 17.9 kompatibel. Um Sicherheitslücken zu vermeiden, empfiehlt Adobe jedoch dringend, alle Instanzen auf einen neuen Build zu aktualisieren. 

* Als lokaler Kunde werden Sie aufgefordert, die Marketing- und Mid-Sourcing-Instanzen auf einen neuen Build zu aktualisieren.

>[!CAUTION]
>
>Wenn Sie noch kein Upgrade durchführen können, müssen Sie sich an das Kundendienstteam von Adobe wenden, um eine Sicherheitskorrektur für Ihre Instanzen vorzunehmen.****


## Aktualisierung der Kampagne Client Console

Der neueste Build aus Gold Standard 11 behebt eine Regression, die die Verwendung einiger Konsolenkomponenten wie der Datumsauswahl und der Bildverwaltung in Versänden verhinderte. Die Konsolenaktualisierung ist obligatorisch.

[Weitere Informationen](../rn/using/gold-standard.md).

## Verbindung zur Kampagne über das IMS

Adobe Identity Service (IMS) wird ab dem 30. Juni 2021 keine alten Internet Explorer-Versionen mehr unterstützen. [Mehr dazu](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html). Kampagne Console wurde aktualisiert, um die Kompatibilität mit IMS sicherzustellen.

**Sind Sie betroffen?**

Wenn Sie über einen Adobe ID](../integrations/using/about-adobe-id.md) über den Adobe Identity Service (IMS) eine Verbindung zur Kampagne [herstellen, ist eine Aktualisierung auf eine der oben aufgeführten neuen Versionen erforderlich, damit sowohl der Kampagne- als auch die Client-Konsole nach dem 30. Juni 2021 **eine Verbindung zur Kampagne herstellen können.**

**Wie lässt sich das Update durchführen?**

Als gehosteter Kunde ist keine Aktion erforderlich: Adobe hat Ihre Instanz(en) bereits auf eine neuere Version aktualisiert.

Als On-Premise-/Hybrid-Kunde müssen Sie auf eine der neueren Versionen aktualisieren, um von der neuen Client Console profitieren zu können und eine nahtlose Transition **vor dem 31. März 2021** sicherzustellen.

## Integration mit Experience Cloud-Triggern

Der veraltete Auth-Authentifizierungsdienst hat das Lebensende erreicht und wird am 30. Juni 2021 eingestellt. [Weitere Informationen](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411).

**Sind Sie betroffen?**

Wenn Sie eine ältere Version der Trigger-Integration über die Auth-Authentifizierung verwenden, müssen Sie **zu Adobe I/O** wechseln.

**Wie lässt sich das Update durchführen?**

[Erfahren Sie, wie Sie zu Adobe I/O wechseln](../integrations/using/configuring-adobe-io.md).

## API für HTTP/2-basierte APNs-Provider

Ab dem 31. März 2021 wird die ältere Version des Binärprotokolls nicht mehr vom Apple Push Notification Service (APNs) unterstützt. [Mehr dazu](https://developer.apple.com/news/?id=c88acm2b).

**Sind Sie betroffen?**

Wenn Ihre Instanzen auf einer älteren Version als Kampagne 21.1 ausgeführt werden und Push-Benachrichtigungen mit dem alten Apple-Binärprotokoll gesendet werden, müssen Sie auf die HTTP/2-basierte API des APNs-Anbieters aktualisieren.

**Wie lässt sich das Update durchführen?**

Als gehosteter Kunde ist keine Aktion erforderlich: Adobe hat Ihre Instanz(en) bereits auf die HTTP/2-basierte API aktualisiert.

Als lokal/gehosteter Kunde müssen Sie Ihre Konfiguration aktualisieren. [Erfahren Sie, wie Sie zu HTTP/2 migrieren.](https://helpx.adobe.com/de/campaign/kb/migrate-to-apns-http2.html)

## Aktualisierung des Stammzertifikats von APN

Am 29. März 2021 wirkt sich ein Infrastrukturupdate des Apple Push Notification Service (APNs) auf den Adobe Campaign Classic iOS-Kanal aus. Eine Änderung der Betriebssystemkonfiguration ist **obligatorisch**, um einen Ausfall des iOS-Push-Kanals zu vermeiden.

Erfahren Sie mehr über die APNs-Änderungen [auf dieser Seite](https://developer.apple.com/news/?id=7gx0a2lp).

**Sind Sie betroffen?**

Wenn Sie Kampagne zum Senden von Push-Benachrichtigungen auf iOS-Geräten verwenden, sind Sie davon betroffen.

**Wie lässt sich das Update durchführen?**

Als gehosteter Kunde ist keine Aktion erforderlich: Adobe hat das neue Stammzertifikat bereits in Ihre Umgebung integriert.

Als Vor-Ort-/Hybridkunde müssen Sie Ihre Konfiguration aktualisieren, um eine nahtlose Transition **vor dem 29. März 2021** sicherzustellen.

[Erfahren Sie, wie Sie das neue Zertifikat integrieren.](ios-certificate-update.md)

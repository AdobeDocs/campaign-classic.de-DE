---
product: campaign
title: Technote – Adobe Campaign-Konfigurationsaktualisierungen
description: Adobe Campaign-Konfigurationsaktualisierungen
feature: Technote, Upgrade
hide: true
hidefromtoc: true
exl-id: 7db02123-2e2a-40d9-8385-728ff69985e4
source-git-commit: 8de62db2499449fc9966b6464862748e2514a774
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 100%

---

# Adobe Campaign-Konfigurationsaktualisierungen 2021 {#acc-config-updates}



Infrastruktur und Einstellungen sollten regelmäßig mit den neuesten Builds und Produktkorrekturen aktualisiert werden. Diese Korrekturen sind notwendig, um die Kontinuität des Dienstes und der Sicherheit zu gewährleisten. Darüber hinaus sind Upgrades erforderlich, um die Software an Änderungen von Drittanbietern anzupassen.

Als **gehosteter oder Managed Services-Kunde** werden Sie von Adobe in regelmäßigen Abständen über erforderliche Upgrades von Builds informiert. Sie müssen Upgrades gemäß den Empfehlungen durchführen, um die Konformität des Systems sicherzustellen.

Als **On-Premise- oder Hybrid-Kunde** sollten Sie Ihre Implementierung in regelmäßigen Abständen entsprechend den neuesten veröffentlichten Builds aktualisieren.

Aus Sicherheitsgründen müssen Sie jetzt ein Upgrade auf eine der folgenden Versionen vornehmen. Zusätzlich zu den standardmäßigen Upgrade-Schritten müssen einige manuelle Aufgaben durchgeführt werden, um sicherzustellen, dass Ihre Umgebung sicher und auf zukünftige Änderungen von Adobe- oder Drittanbietersystemen vorbereitet ist.

>[!NOTE]
>
>Wenden Sie sich bei Fragen zu diesen Änderungen an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>

## Sicherheitsaktualisierungen {#acc-security-updates}

Die neuesten Campaign-Versionen enthalten ein Sicherheits-Update, das verstärkten Schutz vor Problemen durch Server-seitige Anfragefälschungen (Server Side Request Forgery, SSRF) bietet. Weiterführende Informationen finden Sie auf [dieser Seite](https://helpx.adobe.com/de/security/products/campaign/apsb21-04.html).

**Sind Sie betroffen?**

Wenn Ihre Umgebung einen älteren Build als die unten aufgeführten verwendet, sind Sie betroffen:

* Gold Standard 11. [Weitere Informationen](../../rn/using/gold-standard.md)
* Campaign-Version 21.1.1. [Weitere Informationen](../../rn/using/latest-release.md)
* Campaign-Version 20.2.5.
* Campaign-Version 20.1.4.
* Campaign-Version 19.2.4.
* Campaign-Version 19.1.8.

[In diesem Abschnitt](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) erfahren Sie, wie Sie Ihre Version überprüfen.

**Wie wird die Aktualisierung durchgeführt?**

Sie müssen ein Upgrade auf einen der neueren Builds durchführen, die oben aufgeführt sind.

* Als Hybrid-Kunde werden Sie von Adobe über die geplanten Upgrade-Termine für Ihre Mid-Sourcing-Instanzen informiert. Adobe empfiehlt dringend, auch Ihre Marketing-Instanz zu aktualisieren.

  Der neue Build ist abwärtskompatibel mit Campaign Classic 17.9. Adobe empfiehlt jedoch dringend, alle Instanzen zu aktualisieren, um Sicherheitslücken zu beheben

* Als On-Premise-Kunde werden Sie aufgefordert, die Marketing- und Mid-Sourcing-Instanzen auf den neuesten Build zu aktualisieren.

>[!CAUTION]
>
>Wenn Sie eine Aktualisierung nicht innerhalb des empfohlenen Zeitraums durchführen können, **sollten Sie sich an die Adobe-Kundenunterstützung wenden, um eine kurzfristige manuelle Sicherheitskorrektur auf Ihre Instanzen anzuwenden**.
>

## Aktualisierung der Client-Konsole von Campaign Classic   {#acc-cc-updates}

Die folgenden **jetzt verfügbaren** Konsolenversionen sollten installiert werden, um eine kürzlich identifizierte Fehlfunktion zu beheben. Diese Fehlfunktion verhinderte die Verwendung einiger Komponenten der Client-Konsole, wie z. B. der Datumsauswahl und der Bildverwaltung in Sendungen. Das **Konsolen-Upgrade** ist obligatorisch.

* Neuester Gold Standard 11-Build 9032@10c2709. [Weitere Informationen](../../rn/using/gold-standard.md)
* Campaign-Version 20.1.4.
* Campaign-Version 19.2.4.
* Campaign-Version 19.1.8.

## Aktualisierung von Adobe Identity Management System (IMS)

Adobe Identity Service (IMS) beendet am **30. Juni 2021** die Unterstützung alter Internet Explorer-Versionen. [Weitere Informationen](https://helpx.adobe.com/de/x-productkb/global/update-operating-system-and-browser.html).

Um die Kompatibilität mit Adobe IMS sicherzustellen, ist ein Upgrade der Client-Konsole von Campaign erforderlich.

**Sind Sie betroffen?**

Wenn Sie [per Adobe ID](../../integrations/using/about-adobe-id.md) über Adobe Identity Management Service (IMS) eine Verbindung zu Campaign herstellen, ist ein Upgrade auf eine der folgenden neuen Versionen obligatorisch:

* Gold Standard 11. [Weitere Informationen](../../rn/using/gold-standard.md)
* Campaign-Version 21.1.1. [Weitere Informationen](../../rn/using/latest-release.md)
* Campaign-Version 20.2.5.
* Campaign-Version 20.1.4.
* Campaign-Version 19.2.4.
* Campaign-Version 19.1.8.

Diese Versionen umfassen ein neues Verbindungsprotokoll. Daher müssen sowohl der Campaign-Server als auch die Client-Konsole aktualisiert werden, damit nach dem **30. Juni 2021** weiterhin eine Verbindung zu Campaign hergestellt werden kann.

[In diesem Abschnitt](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) erfahren Sie, wie Sie Ihre Version überprüfen.

**Wie wird die Aktualisierung durchgeführt?**

Wenn Sie ein gehosteter Kunde sind, wird Adobe in Kürze auf Sie zukommen, um Ihre Instanz(en) auf die neuere Version zu aktualisieren.

Als On-Premise-/Hybrid-Kunde müssen Sie ein Upgrade auf eine der neueren Versionen durchführen, um von der neuen Client-Konsole zu profitieren und einen reibungslosen Umstieg **vor dem 30. Juni 2021** sicherzustellen.

Sobald alle Instanzen aktualisiert wurden, muss auch die Client-Konsole auf diese Version aktualisiert werden.

* Erfahren Sie, wie Sie auf die [Adobe-Software-Verteilung](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=de) zugreifen.

* [Erfahren Sie, wie Sie die Campaign-Client-Konsole installieren](../../installation/using/installing-the-client-console.md).

## Integration mit Experience Cloud-Triggern {#acc-triggers-updates}

Der ältere OAuth-Authentifizierungsdienst hat das Lebenszyklusende erreicht. Die Authentifizierung für die Triggers-Integration, die ursprünglich auf der OAuth-Authentifizierung für den Zugriff auf die Pipeline basierte, wurde zu Adobe I/O verschoben. Die alte OAuth-Authentifizierungsmethode mit Campaign wurde im **September 2021** [eingestellt](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411?profile.language=de). Gehostete Umgebungen profitieren von einer Verlängerung bis zum **23. Februar 2022**. Wenden Sie sich als On-Premise- oder Hybrid-Kunde an die Kundenunterstützung von Adobe, um den Support bis Februar 2022 zu verlängern. Dazu müssen Sie Adobe [die AppID der OAuth-Anwendung](../../integrations/using/configuring-pipeline.md#step-optional) nennen.

**Sind Sie betroffen?**

Wenn Ihre Instanzen mit einer **älteren Version als Campaign 19.1.8, 20.2.4 oder Gold Standard 11** ausgeführt werden, verwenden Sie eine ältere Version der Trigger-Integration über OAuth-Authentifizierung: **Sie müssen auf eine neuere Version aktualisieren und zu Adobe I/O wechseln**.

Das Upgrade auf eine der folgenden neuen Versionen ist obligatorisch:

* Gold Standard 11. [Weitere Informationen](../../rn/using/gold-standard.md)
* Campaign-Version 21.1.1. [Weitere Informationen](../../rn/using/latest-release.md)
* Campaign-Version 20.2.5.
* Campaign-Version 19.1.8.

[In diesem Abschnitt](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) erfahren Sie, wie Sie Ihre Version überprüfen.

**Wie wird die Aktualisierung durchgeführt?**

Sobald die Instanzen auf eine neuere Version aktualisiert wurden, müssen alle Kunden das [Verfahren zum Wechsel in den neuen Authentifizierungsmodus](../../integrations/using/about-triggers.md#implement) befolgen. Hierfür muss das neue Adobe I/O-Token generiert und in der Implementierung verwendet werden. 

Kunden mit Hybrid-Umgebungen müssen darüber hinaus sicherstellen, dass Pipeline auf einer Mid-Sourcing-Instanz konfiguriert ist. [Weitere Informationen](../../integrations/using/configuring-pipeline.md).

[Erfahren Sie, wie Sie zu Adobe I/O migrieren](../../integrations/using/about-triggers.md#implement).

## APNs-Aktualisierungen {#acc-apns-updates}

### HTTP/2-basierte APNs-Provider-API

Seit dem **31. März 2021** unterstützt der Push-Benachrichtigungsdienst von Apple (Apple Push Notification service, APNs) das alte Binärprotokoll nicht mehr. [Mehr dazu](https://developer.apple.com/news/?id=c88acm2b).

**Sind Sie betroffen?**

Wenn Ihre Instanzen auf einer **älteren Version als Campaign 21.1** ausgeführt werden und Push-Benachrichtigungen mit dem veralteten Binärprotokoll von Apple gesendet werden, müssen Sie auf die HTTP/2-basierte APNs-Provider-API aktualisieren.

[In diesem Abschnitt](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) erfahren Sie, wie Sie Ihre Version überprüfen.

**Wie wird die Aktualisierung durchgeführt?**

Wenn Sie als gehosteter Kunde ein Upgrade auf den neuen Build durchgeführt haben, hat Adobe Ihre Instanz(en) bereits auf die HTTP/2-basierte API aktualisiert.

Als On-Premise-/Hybrid-Kunde müssen Sie Ihre Konfiguration aktualisieren.

### Aktualisierungen des APNs-Stammzertifikats

Am 29. März 2021 wirkte sich eine Infrastrukturaktualisierung des Push-Benachrichtigungsdienstes von Apple (Apple Push Notification service, APNs) auf den iOS-Kanal von Adobe Campaign Classic aus. Eine Anpassung der Konfiguration des Betriebssystems ist **obligatorisch**, um einen Ausfall des iOS-Push-Kanals zu vermeiden.

Weitere Informationen zu den APNs-Änderungen finden Sie [auf dieser Seite](https://developer.apple.com/news/?id=7gx0a2lp).

**Sind Sie betroffen?**

Wenn Sie Campaign zum Senden von Push-Benachrichtigungen an iOS-Geräte verwenden, sind Sie betroffen.

**Wie wird die Aktualisierung durchgeführt?**

Als gehosteter Kunde besteht kein Handlungsbedarf: Adobe hat das neue Stammzertifikat bereits in Ihre Umgebung integriert.

Als On-Premise-/Hybrid-Kunde müssen Sie Ihre Konfiguration aktualisieren, um einen nahtlosen Übergang **vor dem 29. März 2021** zu gewährleisten.

[Erfahren Sie, wie Sie das neue Zertifikat integrieren](ios-certificate-update.md).

## Nützliche Links

* [Upgrade Ihrer Umgebung](../../production/using/build-upgrade.md)
* [Häufig gestellte Fragen zum Build-Upgrade](../../platform/using/faq-build-upgrade.md)
* [Campaign Classic-Build herunterladen](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html)
* [Neue Client-Konsole für Benutzer verfügbar machen](../../installation/using/client-console-availability-for-windows.md)

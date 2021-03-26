---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: bdd746120f2162cf48eeb9d519513656bd4e75aa
workflow-type: tm+mt
source-wordcount: '1114'
ht-degree: 58%

---


# Adobe Campaign-Konfigurationsaktualisierungen – März 2021 {#acc-config-updates}

Infrastruktur und Einstellungen sollten regelmäßig mit den neuesten Builds und Produktverbesserungen aktualisiert werden. Diese Korrekturen sind notwendig, um die Kontinuität des Dienstes und der Sicherheit zu gewährleisten. Darüber hinaus sind Upgrades erforderlich, um Änderungen von Drittanbietern anzupassen.

Als Kunde von **Hosted oder Managed Services** informiert Sie die Adobe regelmäßig über Buildaktualisierungen. Um die Einhaltung der Vorschriften sicherzustellen, müssen Sie die entsprechenden Aktualisierungen vornehmen.

Als **On-Premise- oder Hybrid-Kunde** sollten Sie Ihre Implementierung in regelmäßigen Abständen entsprechend den neuesten veröffentlichten Builds aktualisieren.

Aus Sicherheitsgründen müssen Sie jetzt auf eine der folgenden Versionen aktualisieren. Zusätzlich zu den standardmäßigen Aktualisierungsschritten müssen einige manuelle Aufgaben durchgeführt werden, um sicherzustellen, dass Ihre Umgebung sicher ist und auf zukünftige Änderungen von Adobe- oder Drittanbietersystemen vorbereitet ist.

>[!NOTE]
>
>Wenden Sie sich bei Fragen zu diesen Änderungen an den [Adobe Kundendienst](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).


## Sicherheitsaktualisierungen {#acc-security-updates}

Die neuesten Versionen der Kampagne enthalten eine Sicherheitskorrektur, die den Schutz vor Problemen mit der serverseitigen Anforderungsfälschung (SSRF) verstärkt. Weitere Infos finden Sie auf [dieser Seite](https://helpx.adobe.com/de/security/products/campaign/apsb21-04.html).

**Sind Sie betroffen?**

Sie sind betroffen, wenn Ihre Umgebung sich auf einem niedrigeren Build als den unten aufgeführten befindet:

* Gold Standard 11. [Weitere Infos](../rn/using/gold-standard.md)
* Campaign-Version 21.1.1. [Weitere Infos](../rn/using/latest-release.md)
* Campaign-Version 20.3.3. [Weitere Infos](../rn/using/release--20-3.md)
* Campaign-Version 20.2.4. [Weitere Infos](../rn/using/release--20-2.md)
* Campaign-Version 20.1.4. [Weitere Infos](../rn/using/release--20-1.md)
* Campaign-Version 19.2.4. [Weitere Infos](../rn/using/release--19-2.md)
* Campaign-Version 19.1.8. [Weitere Infos](../rn/using/release--19-1.md)

Erfahren Sie, wie Sie Ihre Version [in diesem Abschnitt](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) überprüfen.

**Wie lässt sich das Update durchführen?**

Sie müssen auf einen der neueren Builds aktualisieren, die oben aufgeführt sind.

* Als Hybridkunde informiert Sie die Adobe über die geplanten Upgradedaten für Ihre Mid-Sourcing-Instanzen. Adobe empfiehlt dringend, auch Ihre Marketinginstanz zu aktualisieren.

   Der neue Build ist abwärtskompatibel mit Campaign Classic 17.9. Die Adobe empfiehlt jedoch dringend, alle Instanzen zu aktualisieren, um Sicherheitslücken zu beheben

* Als lokaler Kunde werden Sie aufgefordert, die Marketing- und Mid-Sourcing-Instanzen auf den neuesten Build zu aktualisieren.

>[!CAUTION]
>
>Wenn Sie eine Aktualisierung nicht innerhalb des empfohlenen Zeitrahmens durchführen können, sollten Sie sich an das Kundendienstteam von Adobe wenden, um eine kurzfristige manuelle Sicherheitskorrektur auf Ihre Instanzen anzuwenden.****


## Campaign Classic-Client-Konsolenaktualisierung {#acc-cc-updates}

Die folgenden Konsolenversionen **sind jetzt verfügbar** sollten installiert werden, um eine kürzlich identifizierte Regression zu beheben. Diese Regression verhinderte die Verwendung einiger Komponenten der Client-Konsole, z. B. der Datumsauswahl und der Bildverwaltung in Versänden. **Das Upgrade der Konsole ist obligatorisch.**

* Neueste Gold Standard 11 Build 9032@10c2709. [Weitere Infos](../rn/using/gold-standard.md)
* Campaign-Version 20.1.4. [Weitere Infos](../rn/using/release--20-1.md)
* Campaign-Version 19.2.4. [Weitere Infos](../rn/using/release--19-2.md)
* Campaign-Version 19.1.8. [Weitere Infos](../rn/using/release--19-1.md)

## Aktualisierung von Adobe Identity Management System (IMS)

Adobe Identity Service (IMS) beendet die Unterstützung alter Internet Explorer-Versionen von **30. Juni 2021**. [Weitere Infos](https://helpx.adobe.com/de/x-productkb/global/update-operating-system-and-browser.html).

Um die Kompatibilität mit Adobe IMS sicherzustellen, ist ein Upgrade der Kampagne Client Console erforderlich.

**Sind Sie betroffen?**

Wenn Sie sich mit Campaign [über eine Adobe ID](../integrations/using/about-adobe-id.md) durch Adobe Identity Management Service (IMS) verbinden, ist ein Upgrade auf eine der folgenden neuen Versionen zwingend erforderlich:

* Gold Standard 11. [Weitere Infos](../rn/using/gold-standard.md)
* Campaign-Version 21.1.1. [Weitere Infos](../rn/using/latest-release.md)
* Campaign-Version 20.3.3. [Weitere Infos](../rn/using/release--20-3.md)
* Campaign-Version 20.2.4. [Weitere Infos](../rn/using/release--20-2.md)
* Campaign-Version 20.1.4. [Weitere Infos](../rn/using/release--20-1.md)
* Campaign-Version 19.2.4. [Weitere Infos](../rn/using/release--19-2.md)
* Campaign-Version 19.1.8. [Weitere Infos](../rn/using/release--19-1.md)

Diese Versionen beinhalten ein neues Verbindungsprotokoll. Daher müssen sowohl der Campaign-Server als auch die Client-Konsole aktualisiert werden, damit auch nach dem **30. Juni 2021** eine Verbindung zu Campaign hergestellt werden kann.

Erfahren Sie, wie Sie Ihre Version [in diesem Abschnitt](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) überprüfen.

**Wie lässt sich das Update durchführen?**

Als gehosteter Kunde arbeitet Adobe in Kürze mit Ihnen zusammen, um Ihre Instanz(en) auf die neuere Version zu aktualisieren.

Als On-Premise- oder Hybrid-Kunde müssen Sie auf eine der neueren Versionen aktualisieren, um von der neuen Client-Konsole profitieren zu können und einen nahtlosen Übergang **vor dem 30. Juni 2021** sicherzustellen.

Sobald alle Instanzen aktualisiert worden sind, muss auch die Client-Konsole auf diese Version aktualisiert werden.

* Erfahren Sie, wie Sie auf die [Adobe Softwareverteilung](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=de) zugreifen können.

* [Erfahren Sie, wie Sie die Campaign-Client-Konsole installieren](../installation/using/installing-the-client-console.md).

## Integration mit Experience Cloud Triggers {#acc-triggers-updates}

Der veraltete OAuth-Authentifizierungs-Service hat das Lebenszyklusende erreicht. Die Authentifizierung für die Triggers-Integration, die ursprünglich auf der Einrichtung der OAuth-Authentifizierung für den Zugriff auf die Pipeline basierte, wurde auf Adobe I/O umgestellt. Die Einstellung des Service erfolgt am **30. November 2021**. [Weitere Infos](https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md?mv=email).

**Sind Sie betroffen?**

Wenn Ihre Instanzen mit einer **älteren Version als Campaign 19.1.8, 20.2.4, Gold Standard 11** ausgeführt werden, haben Sie eine ältere Version der Triggers-Integration, die mithilfe der OAuth-Authentifizierung durchgeführt wird. Sie müssen in dem Fall **auf eine neuere Version aktualisieren und zu Adobe I/O wechseln**.

Die Aktualisierung auf eine der folgenden neuen Versionen ist zwingend erforderlich:

* Gold Standard 11. [Weitere Infos](../rn/using/gold-standard.md)
* Campaign-Version 21.1.1. [Weitere Infos](../rn/using/latest-release.md)
* Campaign-Version 20.3.3. [Weitere Infos](../rn/using/release--20-3.md)
* Campaign-Version 20.2.4. [Weitere Infos](../rn/using/release--20-2.md)
* Campaign-Version 19.1.8. [Weitere Infos](../rn/using/release--19-1.md)

Erfahren Sie, wie Sie Ihre Version [in diesem Abschnitt](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) überprüfen.

**Wie lässt sich das Update durchführen?**

Sobald die Instanzen auf eine neuere Version aktualisiert worden sind, müssen alle Kunden die [Vorgehensweise befolgen, um auf den neuen Authentifizierungsmodus umzustellen](../integrations/using/configuring-adobe-io.md). Hierfür müssen Sie das neue Adoben I/O-Token generieren und in der Implementierung verwenden.  

Kunden mit Hybrid-Umgebungen müssen darüber hinaus sicherstellen, dass Pipeline auf einer Mid-Sourcing-Instanz konfiguriert ist. [Weitere Infos](../integrations/using/configuring-pipeline.md).

[Erfahren Sie, wie Sie zu Adobe I/O wechseln](../integrations/using/configuring-adobe-io.md).

## APNs-Aktualisierungen  {#acc-apns-updates}

### API für HTTP/2-basierte APNs-Provider

Ab dem **31. März 2021** wird das alte Binärprotokoll nicht mehr vom Apple Push Notification Service (APNs) unterstützt. [Weitere Infos](https://developer.apple.com/news/?id=c88acm2b).

**Sind Sie betroffen?**

Wenn Ihre Instanzen auf einer **älteren Version als Kampagne 21.1 und** ausgeführt werden und Sie Push-Benachrichtigungen mit dem alten Apple-Binärprotokoll senden, müssen Sie auf die HTTP/2-basierte API des APNs-Providers aktualisieren.

Erfahren Sie, wie Sie Ihre Version [in diesem Abschnitt](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) überprüfen.

**Wie lässt sich das Update durchführen?**

Als gehosteter Kunde haben Sie nach einem Upgrade auf den neuen Build Ihre Instanz(en) bereits auf die HTTP/2-basierte API aktualisiert.

Als On-Premise-/gehosteter Kunde müssen Sie Ihre Konfiguration aktualisieren. [Erfahren Sie, wie Sie zu HTTP/2 migrieren](https://helpx.adobe.com/de/campaign/kb/migrate-to-apns-http2.html)

### Aktualisierungen des APNs-Stammzertifikats

Ab dem 29. März 2021 wird sich ein Infrastruktur-Update des Apple Push Notification Service (APNs) auf den iOS-Kanal von Adobe Campaign Classic auswirken. Eine Änderung der Betriebssystemkonfiguration ist **zwingend erforderlich**, um einen Ausfall des iOS-Push-Kanals zu vermeiden.

Weitere Infos über die APNs-Änderungen erhalten Sie [auf dieser Seite](https://developer.apple.com/news/?id=7gx0a2lp).

**Sind Sie betroffen?**

Wenn Sie Campaign zum Senden von Push-Benachrichtigungen auf iOS-Geräte verwenden, sind Sie davon betroffen.

**Wie lässt sich das Update durchführen?**

Als gehosteter Kunde sind keine Maßnahmen erforderlich: Adobe hat das neue Stammzertifikat bereits in Ihre Umgebung integriert.

Als On-Premise- oder Hybrid-Kunde müssen Sie Ihre Konfiguration aktualisieren, um einen nahtlosen Übergang **vor dem 29. März 2021** zu gewährleisten.

[Erfahren Sie, wie Sie das neue Zertifikat einbinden](ios-certificate-update.md).

## Nützliche Links

* [Aktualisieren Ihrer Umgebung](../production/using/build-upgrade.md)
* [Häufig gestellte Fragen zum Build-Upgrade](../platform/using/faq-build-upgrade.md)
* [Campaign Classic-Build herunterladen](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html)
* [Neue Client-Konsole für Benutzer verfügbar machen](../installation/using/client-console-availability-for-windows.md)

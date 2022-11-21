---
product: campaign
title: Technote - Adobe Campaign-Systemaktualisierungen
description: Adobe Campaign-Systemaktualisierung
hide: true
hidefromtoc: true
source-git-commit: b119d52b94d95086261fcdc1744698a78296df9c
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 12%

---

# Systemaktualisierung für Adobe Campaign 2023 {#ac-system-upgrade}

Die Campaign-Infrastruktur beruht auf Drittanbietersystemen, die regelmäßig mit den Systemversionen und -korrekturen aktualisiert werden müssen. Diese Aktualisierungen sind obligatorisch, um die Kontinuität des Diensts und die Sicherheit von Campaign-Umgebungen vor Sicherheitsrisiken zu gewährleisten. Darüber hinaus sind Aktualisierungen erforderlich, um Änderungen am System von Drittanbietern zu berücksichtigen.

Als **Kunden mit gehosteten oder verwalteten Cloud Services**, informiert Sie Adobe über diese Aktualisierungen, wenn sie benötigt werden. Sie müssen Ihre Umgebungen entsprechend den Empfehlungen aktualisieren, um die Einhaltung der Vorschriften sicherzustellen.

Als **On-Premise- oder Hybrid-Kunde** empfiehlt Adobe dringend, Ihre System- und Campaign-Versionen entsprechend demselben Kalender zu aktualisieren.

Aus Sicherheitsgründen müssen Sie [Installieren des aktuellen Campaign-Builds](#ac-upgrade), und aktualisieren Sie anschließend Ihre [Betriebssystem](#os-upgrade) und/oder Ihre [Relation Database Management System (RDBMS)](#pg-upgrade).

>[!NOTE]
>
>Wenden Sie sich bei Fragen zu diesen Änderungen an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Campaign-Build-Upgrade {#ac-upgrade}

**Sind Sie betroffen?**

Wenn Sie von der [Betriebssystemaktualisierung](#os-upgrade) und/oder [Datenbanksystemaktualisierung](#pg-upgrade) Im Folgenden wird beschrieben, wie Sie Ihre Campaign-Umgebungen auf die neueste Version 7.3.2 aktualisieren müssen, die mit diesen Systemen kompatibel ist.

**Wie wird die Aktualisierung durchgeführt?**

* Als gehosteter oder verwalteter Cloud Services kontaktiert Adobe Sie und aktualisiert Ihre Campaign-Version.
* Als Hybrid-Kunde informiert Sie Adobe über die geplanten Build-Upgradedaten für Ihre Mid-Sourcing-Umgebung. Außerdem müssen Sie Ihre Marketing-Umgebung auf dieselbe Version aktualisieren.
* Als On-Premise-Kunde werden Sie aufgefordert, Ihre Campaign-Umgebungen auf die neueste Version 7.3.2 zu aktualisieren.


## Betriebssystemaktualisierung {#os-upgrade}

**Sind Sie betroffen?**

Wenn Sie Campaign auf einem Debian-Betriebssystem ausführen, müssen Sie Ihre Campaign-Infrastruktur auf **Debian 11**. Beachten Sie, dass Debian 9 am 30. Juni 2022 das Ende der Lebensdauer erreicht hat und keine Sicherheitskorrekturen mehr bietet.

**Wie wird die Aktualisierung durchgeführt?**

* Als gehosteter oder verwalteter Cloud Services-Kunde kontaktiert Adobe Sie und aktualisiert Ihre Umgebung.
* Als Hybrid-Kunde informiert Sie Adobe über die geplanten Upgradedaten für Ihre Mid-Sourcing-Umgebung. Wenn Ihre Marketing-Umgebung auch auf Debian läuft, müssen Sie es auch auf Debian 11 aktualisieren.
* Als On-Premise-Kunde werden Sie aufgefordert, Ihre Umgebungen auf Debian 11 zu aktualisieren.

## Aktualisierung des Datenbanksystems {#pg-upgrade}

**Sind Sie betroffen?**

Wenn Ihr Campaign-Datenbanksystem PostgreSQL ist, müssen Sie ein Upgrade auf **PostgreSQL 14**. Beachten Sie, dass PostreSQL 11 am 30. November 2022 das Ende der Lebensdauer erreichen wird.

**Wie wird die Aktualisierung durchgeführt?**

* Als gehosteter oder verwalteter Cloud Services-Kunde kontaktiert Adobe Sie und aktualisiert Ihr Datenbanksystem von PostgreSQL 11 auf PostgreSQL 14.
* Wenn Ihr Marketing-Datenbanksystem als Hybrid-Kunde PostgreSQL ist, müssen Sie es auf PostgreSQL 14 aktualisieren.
* Als On-Premise-Kunde werden Sie aufgefordert, Ihr Datenbanksystem auf PostgreSQL 14 zu aktualisieren. ../integrations/using/configuring-adobe-io.md).


## Nützliche Links

* [Upgrade Ihrer Umgebung](../../production/using/build-upgrade.md)
* [Häufig gestellte Fragen zum Build-Upgrade](../../platform/using/faq-build-upgrade.md)
* [Campaign Classic-Build herunterladen](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html)
* [Neue Client-Konsole für Benutzer verfügbar machen](../../installation/using/client-console-availability-for-windows.md)

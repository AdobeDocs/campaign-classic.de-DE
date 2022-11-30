---
product: campaign
title: Technote - Adobe Campaign-Systemaktualisierungen
description: Adobe Campaign-Systemaktualisierung
hide: true
hidefromtoc: true
exl-id: 78949d94-60b3-44f1-8e5a-d61b5b723e87
source-git-commit: 7948f6423b80788adf26a53afcd380953c8b8463
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 11%

---

# Umgebungs-Upgrades für Adobe Campaign 2023 {#ac-system-upgrade}

Die Campaign-Infrastruktur beruht auf Drittanbietersystemen, die regelmäßig mit den neuesten Versionen und Fehlerbehebungen aktualisiert werden müssen. Diese Aktualisierungen sind obligatorisch, um die Kontinuität des Diensts und die Sicherheit von Campaign-Umgebungen vor Sicherheitsrisiken zu gewährleisten. Außerdem ist ein Campaign-Upgrade erforderlich, um die Kompatibilität mit Systemänderungen von Drittanbietern sicherzustellen.

Als **Kunden mit gehosteten oder verwalteten Cloud Services**, informiert Sie Adobe über diese Aktualisierungen, wenn sie benötigt werden. Sie müssen Ihre Umgebungen entsprechend den Empfehlungen aktualisieren, um die Einhaltung der Vorschriften sicherzustellen.

Als **On-Premise- oder Hybrid-Kunde** empfiehlt Adobe dringend, Ihre System- und Campaign-Versionen entsprechend demselben Kalender zu aktualisieren.

Aus Sicherheitsgründen müssen Sie [Installieren des aktuellen Campaign-Builds](#ac-upgrade), und aktualisieren Sie anschließend Ihre [Betriebssystem](#os-upgrade) und/oder Ihre [Relation Database Management System (RDBMS)](#pg-upgrade).

>[!NOTE]
>
>Wenden Sie sich bei Fragen zu diesen Änderungen an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Siehe auch [Häufig gestellte Fragen zum Build-Upgrade](../../platform/using/faq-build-upgrade.md).

## Campaign-Build-Upgrade {#ac-upgrade}

**Sind Sie betroffen?**

Wenn Sie von der [Betriebssystemaktualisierung](#os-upgrade) und/oder [Datenbanksystemaktualisierung](#pg-upgrade) Im Folgenden wird beschrieben, wie Sie Ihre Campaign-Umgebungen auf [die neueste Version 7.3.2](../../rn/using/latest-release.md#release-7-3-2), die mit diesen Systemen kompatibel ist.

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

Wenn Ihr Campaign-Datenbanksystem PostgreSQL ist, müssen Sie ein Upgrade auf **PostgreSQL 14**. Beachten Sie, dass PostreSQL 11 am 9. November 2023 das Ende der Lebensdauer erreichen wird.

**Wie wird die Aktualisierung durchgeführt?**

* Als gehosteter oder verwalteter Cloud Services-Kunde kontaktiert Adobe Sie und aktualisiert Ihr Datenbanksystem von PostgreSQL 11 auf PostgreSQL 14.
* Wenn Ihr Marketing-Datenbanksystem als Hybrid-Kunde PostgreSQL ist, müssen Sie es auf PostgreSQL 14 aktualisieren.
* Als On-Premise-Kunde werden Sie aufgefordert, Ihr Datenbanksystem auf PostgreSQL 14 zu aktualisieren.


## Nützliche Links

* [Upgrade Ihrer Umgebung](../../production/using/build-upgrade.md)
* [Häufig gestellte Fragen zum Build-Upgrade](../../platform/using/faq-build-upgrade.md)
* [Herunterladen des neuesten Campaign Classic-Builds](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html)
* [Neue Client-Konsole für Benutzer verfügbar machen](../../installation/using/client-console-availability-for-windows.md)

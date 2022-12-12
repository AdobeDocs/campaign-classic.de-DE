---
product: campaign
title: Technote – Adobe Campaign-System-Upgrades
description: Adobe Campaign-System-Upgrade
hide: true
hidefromtoc: true
exl-id: 78949d94-60b3-44f1-8e5a-d61b5b723e87
source-git-commit: bffad77458ab0b4d40490a52c64c99a0fe882d22
workflow-type: ht
source-wordcount: '499'
ht-degree: 100%

---

# Umgebung-Upgrades für Adobe Campaign 2023 {#ac-system-upgrade}

Die Campaign-Infrastruktur beruht auf Drittanbietersystemen, die regelmäßig mit den neuesten Versionen und Fehlerbehebungen aktualisiert werden müssen. Diese Aktualisierungen sind obligatorisch, um die Kontinuität des Service und den Schutz von Campaign-Umgebungen vor Sicherheitsgefahren zu gewährleisten. Außerdem ist ein Campaign-Upgrade erforderlich, um die Kompatibilität mit Systemänderungen von Drittanbietern sicherzustellen.

Als **Kunde von Hosted oder Managed Cloud Services** werden Sie von Adobe über diese Upgrades informiert, wenn sie benötigt werden. Sie müssen Umgebungs-Upgrades gemäß den Empfehlungen durchführen, um die Konformität des Systems sicherzustellen.

Für **On-Premise- oder Hybrid-Kunden** empfiehlt Adobe dringend, die System- und Campaign-Versionen entsprechend demselben Kalender zu aktualisieren.

Aus Sicherheitsgründen müssen Sie [das neueste Campaign-Build installieren](#ac-upgrade), und anschließend Ihr [Betriebssystem](#os-upgrade) und/oder Ihr [Relation Database Management System (RDBMS)](#pg-upgrade) aktualisieren.

>[!NOTE]
>
>Wenden Sie sich bei Fragen zu diesen Änderungen an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Siehe auch [häufig gestellte Fragen zum Build-Upgrade](../../platform/using/faq-build-upgrade.md).

## Campaign-Build-Upgrade {#ac-upgrade}

**Sind Sie betroffen?**

Beim [Betriebssystem-Upgrade](#os-upgrade) und/oder [Datenbanksystem-Upgrade](#pg-upgrade) – wie im Folgenden genauer beschrieben – müssen Campaign-Umgebungen auf [die neueste Version 7.3.2](../../rn/using/latest-release.md#release-7-3-2) aktualisiert werden, die mit diesen Systemen kompatibel ist.

**Wie wird die Aktualisierung durchgeführt?**

* Als Kunde von Hosted oder Managed Cloud Services wird Adobe Sie kontaktieren und Ihre Campaign-Version aktualisieren.
* Als Hybrid-Kunde werden Sie von Adobe über die geplanten Upgrade-Termine für Ihre Mid-Sourcing-Instanzen informiert. Außerdem müssen Sie Ihre Marketing-Umgebung auf dieselbe Version aktualisieren.
* Als On-Premise-Kunde werden Sie aufgefordert, die Marketing- und Mid-Sourcing-Instanzen auf den neuesten Build 7.3.2 zu aktualisieren.


## Betriebssystem-Upgrade {#os-upgrade}

**Sind Sie betroffen?**

Wenn Sie Campaign auf einem Debian-Betriebssystem ausführen, müssen Sie Ihre Campaign-Infrastruktur auf **Debian 11** aktualisieren, um von den neuesten Debian-Sicherheitsaktualisierungen zu profitieren. Bitte beachten, dass die Sicherheitsunterstützung für Debian 9 nur bis zum 30. Juni 2023 verfügbar sein wird.

**Wie wird die Aktualisierung durchgeführt?**

* Als Kunde von Hosted oder Managed Cloud Services wird Adobe Sie kontaktieren und Ihre Umgebung aktualisieren.
* Als Hybrid-Kunde werden Sie von Adobe über die geplanten Upgrade-Termine für Ihre Mid-Sourcing-Instanzen informiert. Wenn Ihre Marketing-Umgebung auch auf Debian läuft, müssen Sie sie auch auf Debian 11 aktualisieren.
* Als On-Premise-Kunde werden Sie aufgefordert, Ihre Umgebungen auf Debian 11 zu aktualisieren.

## Upgrade des Datenbanksystems {#pg-upgrade}

**Sind Sie betroffen?**

Wenn Ihr Campaign-Datenbanksystem PostgreSQL ist, müssen Sie auf **PostgreSQL 14** aktualisieren, um in den Genuss der neuesten PostgreSQL-Innovationen und -Sicherheitsaktualisierungen zu gelangen. Bitte beachten, dass für PostgreSQL 11 am 9. November 2023 das Ende der Lebensdauer und damit der Unterstützung erreicht sein wird.

**Wie wird die Aktualisierung durchgeführt?**

* Als Kunde von Hosted oder Managed Cloud Services wird Adobe Sie kontaktieren und Ihr Datenbanksystem von PostgreSQL 11 auf PostgreSQL 14 aktualisieren.
* Wenn Sie Hybrid-Kunde sind und Ihr Marketing-Datenbanksystem PostgreSQL ist, müssen Sie es auf PostgreSQL 14 aktualisieren.
* Als On-Premise-Kunde werden Sie aufgefordert, Ihr Datenbanksystem auf PostgreSQL 14 zu aktualisieren.


## Nützliche Links

* [Upgrade Ihrer Umgebung](../../production/using/build-upgrade.md)
* [Häufig gestellte Fragen zum Build-Upgrade](../../platform/using/faq-build-upgrade.md)
* [Herunterladen des neuesten Campaign Classic-Builds](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html)
* [Neue Client-Konsole für Benutzende verfügbar machen](../../installation/using/client-console-availability-for-windows.md)

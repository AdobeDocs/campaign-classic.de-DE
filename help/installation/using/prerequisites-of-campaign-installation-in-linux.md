---
product: campaign
title: Voraussetzungen für die Campaign-Installation unter Linux
description: Voraussetzungen für die Campaign-Installation unter Linux
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
badge-v7-prem: label="On-Premise und Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: acbd2873-7b1c-4d81-bc62-cb1246c330af
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '914'
ht-degree: 4%

---

# Voraussetzungen für die Installation von Campaign unter Linux{#prerequisites-of-campaign-installation-in-linux}



## Softwarevoraussetzungen {#software-prerequisites}

In diesem Abschnitt werden die Vorkonfigurationsschritte beschrieben, die vor der Installation von Adobe Campaign erforderlich sind.

Die für die Installation von Adobe Campaign erforderlichen technischen und Softwarekonfigurationen werden im Abschnitt [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md).

Zur Erinnerung: Die folgenden Komponenten müssen installiert und korrekt konfiguriert werden:

* Apache, siehe [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md),
* Java JDK und OpenJDK, siehe [Java Development Kit - JDK](../../installation/using/application-server.md#java-development-kit---jdk),
* Bibliotheken, siehe [Bibliotheken](#libraries),
* Datenbankzugriffsschichten, siehe [Datenbankzugriffsebenen](#database-access-layers),
* LibreOffice, siehe [Installieren von LibreOffice für Debian](#installing-libreoffice-for-debian) und [Installieren von LibreOffice für CentOS](#installing-libreoffice-for-centos),
* Schriftarten, siehe [Schriftarten für MTA-Statistiken](#fonts-for-mta-statistics) und [Schriftarten für japanische Instanzen](#fonts-for-japanese-instances).

>[!NOTE]
>
>Um einen Build zu installieren, der kleiner oder gleich 8709 auf CentOS 7- und Debian 8-Plattformen ist, muss das apache access_compat-Modul aktiviert sein.

### Bibliotheken {#libraries}

Um Adobe Campaign unter Linux zu installieren, stellen Sie bitte sicher, dass Sie über die erforderlichen Bibliotheken verfügen.

* Bibliothek C muss den TLS-Modus (Thread Local Storage) unterstützen können. Dieser Modus ist in den meisten Fällen aktiv, mit Ausnahme einiger Kernels, für die die Xen-Unterstützung deaktiviert wurde.

  Um dies zu überprüfen, können Sie die **uname -a | grep xen** -Befehl.

  Wenn der Befehl nichts zurückgibt (leere Zeile), bedeutet dies, dass die Konfiguration korrekt ist.

* Sie müssen über die OpenSSL-Version verfügen. **1,0,2** oder höher.

  Für RHEL 7/8-Distributionen ist Version 1.0 von OpenSSL erforderlich.

* Für die Verwendung von Adobe Campaign benötigen Sie die **libicu** Bibliothek installiert.

  Die folgenden Versionen von **libicu** werden unterstützt (32 Bit oder 64 Bit):

   * RHEL 7/8, CentOS 7: libicu50
   * Debian 8: libicu52
   * Debian 9: libicu57

  Um Adobe Campaign zu verwenden, müssen Sie die Bibliothek libc-ares installiert haben. Führen Sie unter RHEL/CentOS den folgenden Befehl aus:

  ```
  yum install c-ares
  ```

  Unter Debian:

  ```
  aptitude install libc-ares2
  ```

### SELinux {#selinux}

Bei Verwendung muss das SELinux-Modul ordnungsgemäß konfiguriert sein.

Melden Sie sich dazu als Root an und geben Sie den folgenden Befehl ein:

```
echo 0 >/selinux/enforce
```

Darüber hinaus wird im **/etc/sysconfig/httpd** -Datei wurde die folgende Zeile hinzugefügt, um auf das Adobe Campaign-Umgebungskonfigurationsskript zu verweisen:

```
. ~neolane/nl6/env.sh
```

In RHEL und CentOS wurden bei Aktivierung von SELinux Kompatibilitätsprobleme mit den Client-Ebenen von Datenbanken festgestellt. Um sicherzustellen, dass Adobe Campaign ordnungsgemäß funktioniert, empfehlen wir, SELinux zu deaktivieren.

**Gehen Sie wie folgt vor:**

* Datei bearbeiten **/etc/selinux/config**

* Ändern Sie die SELINUX-Zeile wie folgt:

```
SELINUX=disabled
```

### Schriftarten für MTA-Statistiken {#fonts-for-mta-statistics}

Damit Berichte zu MTA-Statistiken (nms/fra/jsp/stat.jsp) korrekt angezeigt werden, fügen Sie Schriftarten hinzu.

Fügen Sie in Debian den Befehl hinzu:

```
aptitude install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

Verwenden Sie in Redhat den folgenden Befehl:

* Für CentOS/RHEL 7:

  ```
  yum install xorg-x11-fonts-base xorg-x11-fonts-75dpi bitstream-vera-fonts dejavu-lgc-fonts
  ```

* Für RHEL 8:

  ```
  dnf install xorg-x11-fonts-misc xorg-x11-fonts-75dpi dejavu-lgc-sans-fonts  dejavu-sans-fonts dejavu-sans-mono-fonts dejavu-serif-fonts
  ```

### Schriftarten für japanische Instanzen {#fonts-for-japanese-instances}

Spezifische Schriften sind für die japanischen Instanzen erforderlich, um die Berichte in das PDF-Format zu exportieren.

Fügen Sie in Debian den Befehl hinzu:

```
aptitude install fonts-ipafont
```

Fügen Sie in Red Hat den Befehl hinzu:

* Für RHEL 7:

  ```
  yum install ipa-gothic-fonts ipa-mincho-fonts
  ```

* Für RHEL 8:

  ```
  dnf install vlgothic-fonts
  ```

### Installieren von LibreOffice für Debian {#installing-libreoffice-for-debian}

Für Debian sind die folgenden Konfigurationen erforderlich:

1. Installieren Sie die folgenden Standardpakete:

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. Installieren Sie die folgenden Schriftarten (optional, jedoch dringend empfohlen für japanische Instanzen):

   ```
   apt-get install fonts-ipafont
   ```

### Installieren von LibreOffice für CentOS {#installing-libreoffice-for-centos}

Die folgenden Konfigurationen sind mit CentOS erforderlich:

```
yum install libreoffice-headless libreoffice-writer libreoffice-calc
```

## Datenbankzugriffsebenen {#database-access-layers}

Die Zugriffsebenen für die verwendete Datenbank-Engine müssen auf Ihrem Server installiert sein und über das Adobe Campaign-Konto zugänglich sein. Versionen und Installationsmodi variieren je nach verwendeter Datenbank-Engine.

Die unterstützte Pilotversion wird in [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md) erläutert.

Überprüfen Sie auch die allgemeine [Datenbank](../../installation/using/database.md) Abschnitt.

### PostgreSQL {#postgresql}

Adobe Campaign unterstützt alle Versionen der PostgreSQL-Client-Bibliotheken ab Version 7.2: (**libpq.so.5**, **libpq.so.4**, **libpq.so.3.2** und **libpq.so.3.1**).

Für die Verwendung von PostgreSQL mit Adobe Campaign ist auch die Installation der entsprechenden **pgcrypto** -Bibliotheken.

### Oracle {#oracle}

Rufen Sie die Bibliotheksversion für 64-Bit Debian ab, d. h.: **libclntsh.so**, **libclntsh.so.11.1** und **libclntsh.so.10.1**.

Sie können ein Linux RPM-Paket vom Oracle Technology Network erhalten.

>[!NOTE]
>
>Wenn Sie den Oracle-Client bereits installiert haben, die globale Umgebung (z. B. /etc/profile) jedoch nicht ordnungsgemäß konfiguriert ist, können Sie fehlende Informationen zum **nl6/customer.sh** script Weitere Informationen hierzu finden Sie unter [Umgebungsvariablen](../../installation/using/installing-packages-with-linux.md#environment-variables).

**Fehlerbehebung und Best Practices**

Probleme können nach einem Oracle-Client oder einer Serveraktualisierung, einer Versionsänderung oder der ersten Installation der Instanz auftreten.

Wenn Sie in der Clientkonsole feststellen, dass unerwartete Zeitverzögerungen (eine oder mehrere Stunden) in den Protokollen, der letzten Verarbeitung des Workflows, der nächsten Verarbeitung usw. auftreten, kann es zu einem Problem zwischen der Bibliothek des Oracle-Clients und dem Oracle-Server kommen. Um solche Probleme zu vermeiden

1. Stellen Sie sicher, dass die **Vollständiger Client**.

   Bei der Verwendung der Oracle Instant Client-Version wurden verschiedene Probleme identifiziert. Darüber hinaus ist es unmöglich, die Zeitzonen-Datei auf dem Instant Client zu ändern.

1. Stellen Sie sicher, dass die Variable **Clientversion** und **Datenbankserverversion** sind **same**.

   Es ist bekannt, dass das Mischen von Versionen trotz der Kompatibilitätsmatrix von Oracle und der Empfehlung zur Ausrichtung von Client- und Serverversionen Probleme verursacht.

   Überprüfen Sie auch den Wert ORACLE_HOME , um sicherzustellen, dass er auf die erwartete Clientversion verweist (falls mehrere Versionen auf dem Computer installiert sind).

1. Stellen Sie sicher, dass Client und Server dasselbe verwenden **timezone file**.

### DB2 {#db2}

Die unterstützte Bibliotheksversion ist **libdb2.so**.

## Implementierungsschritte {#implementation-steps}

Adobe Campaign-Installationen für Linux müssen in der folgenden Reihenfolge durchgeführt werden: Serverinstallation gefolgt von Instanzkonfiguration.

Der Installationsprozess wird in diesem Kapitel beschrieben. Die Installationsschritte lauten wie folgt:

* Schritt 1: Installieren des Anwendungsservers, siehe [Installieren von Paketen mit Linux](../../installation/using/installing-packages-with-linux.md).
* Schritt 2: Integration mit einem Webserver (optional, je nach bereitgestellter Komponente).

Nach Abschluss der Installationsschritte müssen Sie die Instanzen, die Datenbank und den Server konfigurieren. Weitere Informationen hierzu finden Sie unter [Über die Erstkonfiguration](../../installation/using/about-initial-configuration.md).

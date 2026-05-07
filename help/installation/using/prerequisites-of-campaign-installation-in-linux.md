---
product: campaign
title: Voraussetzungen für die Campaign-Installation unter Linux
description: Voraussetzungen für die Campaign-Installation unter Linux
feature: Installation, Instance Settings
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: acbd2873-7b1c-4d81-bc62-cb1246c330af
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 5%

---

# Voraussetzungen für die Installation von Campaign unter Linux{#prerequisites-of-campaign-installation-in-linux}

## Voraussetzungen für die Software {#software-prerequisites}

In diesem Abschnitt werden die vorbereitenden Konfigurationsschritte beschrieben, die vor der Installation von Adobe Campaign erforderlich sind.

Die für die Installation von Adobe Campaign erforderliche technische Konfiguration und Softwarekonfiguration werden in der [Kompatibilitätsmatrix) &#x200B;](../../rn/using/compatibility-matrix.md).

Zur Erinnerung: Die folgenden Komponenten müssen installiert und ordnungsgemäß konfiguriert sein:

* Apache, siehe [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md)
* Java JDK und OpenJDK, siehe [Java Development Kit - JDK](../../installation/using/application-server.md#jdk),
* Bibliotheken, siehe [Bibliotheken](#libraries),
* Datenbankzugriffsebenen, siehe [Datenbankzugriffsebenen](#database-access-layers),
* LibreOffice, siehe [Installieren von LibreOffice für Debian](#installing-libreoffice-for-debian) und [Installieren von LibreOffice für CentOS](#installing-libreoffice-for-centos),
* Schriftarten, siehe [Schriftarten für MTA-](#fonts-for-mta-statistics)) und [Schriftarten für japanische Instanzen](#fonts-for-japanese-instances).


### Bibliotheken {#libraries}

Stellen Sie zum Installieren von Adobe Campaign unter Linux sicher, dass Sie über die erforderlichen Bibliotheken verfügen.

* Bibliothek C muss den TLS-Modus (Thread Local Storage) unterstützen. Dieser Modus ist in den meisten Fällen aktiv, mit Ausnahme einiger Kernels, für die die Xen-Unterstützung deaktiviert wurde.

  Um dies zu überprüfen, können Sie den Befehl **uname -a | grep xen** zum Beispiel verwenden.

  Wenn der Befehl keine leere Zeile zurückgibt, bedeutet dies, dass die Konfiguration korrekt ist.

* Sie müssen die OpenSSL-Version **1.0.2** oder höher haben.

  Für RHEL-Distributionen ist Version 1.0 von OpenSSL erforderlich.

* Um Adobe Campaign verwenden zu können, muss die Bibliothek **libicu** installiert sein.

### SELinux {#selinux}

Wenn das SELinux-Modul verwendet wird, muss es ordnungsgemäß konfiguriert sein.

Melden Sie sich dazu als root an und geben Sie den folgenden Befehl ein:

```
echo 0 >/selinux/enforce
```

Darüber hinaus wurde in der Datei &quot;**/etc/sysconfig/httpd** die folgende Zeile hinzugefügt, um auf das Konfigurationsskript der Adobe Campaign-Umgebung zu verweisen:

```
. ~neolane/nl6/env.sh
```

In RHEL und CentOS wurden Kompatibilitätsprobleme mit den Client-Ebenen von Datenbanken festgestellt, wenn SELinux aktiviert ist. Um sicherzustellen, dass Adobe Campaign ordnungsgemäß funktionieren kann, empfehlen wir, SELinux zu deaktivieren.

**Gehen Sie wie folgt vor:**

* Bearbeiten Sie die Datei **/etc/selinux/config**

* Ändern Sie die SELINUX-Zeile wie folgt:

```
SELINUX=disabled
```

### Schriftarten für MTA-Statistiken {#fonts-for-mta-statistics}

Damit Berichte zu MTA-Statistiken (nms/fra/jsp/stat.jsp) korrekt angezeigt werden, fügen Sie Schriftarten hinzu.

Fügen Sie in Debian den Befehl hinzu:

```
apt install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

Verwenden Sie den folgenden Befehl für RHEL:

```
dnf install xorg-x11-fonts-misc xorg-x11-fonts-75dpi dejavu-lgc-sans-fonts  dejavu-sans-fonts dejavu-sans-mono-fonts dejavu-serif-fonts
```

### Schriftarten für japanische Instanzen {#fonts-for-japanese-instances}

Für japanische Instanzen sind die Schriftarten bestimmter Zeichen erforderlich, um die Berichte in das PDF-Format zu exportieren.

Fügen Sie in Debian den Befehl hinzu:

```
apt install fonts-ipafont
```

Fügen Sie für RHEL den folgenden Befehl hinzu:

```
dnf install epel-release # if required
dnf install vlgothic-fonts
```

### Installieren von LibreOffice für Debian {#installing-libreoffice-for-debian}

Für Debian sind die folgenden Konfigurationen erforderlich:

1. Installieren Sie die folgenden Standardpakete:

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. Installieren Sie die folgenden Schriftarten (optional, wird aber für japanische Instanzen dringend empfohlen):

   ```
   apt-get install fonts-ipafont
   ```

### Installieren von LibreOffice für CentOS {#installing-libreoffice-for-centos}

Die folgenden Konfigurationen sind mit CentOS erforderlich:

```
yum install libreoffice-headless libreoffice-writer libreoffice-calc
```

## Datenbankzugriffsebenen {#database-access-layers}

Die Zugriffsebenen für die von Ihnen verwendete Datenbank-Engine müssen auf Ihrem Server installiert sein und über das Adobe Campaign-Konto zugänglich sein. Versionen und Installationsmodi können je nach verwendeter Datenbank-Engine variieren.

Die unterstützte Pilotversion wird in [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md) erläutert.

Überprüfen Sie auch den Abschnitt [Datenbank](../../installation/using/database.md).

### PostgreSQL {#postgresql}

Adobe Campaign unterstützt alle Versionen der PostgreSQL-Client-Bibliotheken von Version 9.6: **libpq.so.5**.

Die Verwendung von PostgreSQL mit Adobe Campaign erfordert auch die Installation der entsprechenden **pgcrypto**-Bibliotheken.

### Oracle {#oracle}

Rufen Sie die Bibliotheksversion für 64-Bit-Debian ab, d. h.: **libclntsh.so**, **libclntsh.so.19.1**, **libclntsh.so.18.1**, **libclntsh.so.12.1**, **libclntsh.so.11.1** oder **libclntsh.so.10.1**.

Sie können ein Linux RPM-Paket über das Oracle Technology Network erhalten.

>[!NOTE]
>
>Wenn Sie den Oracle-Client bereits installiert haben, die globale Umgebung (z. B.: /etc/profile) jedoch nicht ordnungsgemäß konfiguriert ist, können Sie dem Skript **nl6/customer.sh** fehlende Informationen hinzufügen. Weitere Informationen hierzu finden Sie unter [Umgebungsvariablen](../../installation/using/installing-packages-with-linux.md#environment-variables).

**Fehlerbehebung und Best Practices**

Probleme können nach einem Oracle Client- oder Server-Update, einer Versionsänderung oder bei der ersten Installation der Instanz auftreten.

Wenn Sie in der Client-Konsole feststellen, dass es unerwartete Zeitverzögerungen (eine oder mehrere Stunden) in den Protokollen, bei der letzten Workflow-Verarbeitung, bei der nächsten Verarbeitung usw. gibt, kann es ein Problem zwischen der Bibliothek des Oracle-Clients und dem Oracle-Server geben. So vermeiden Sie solche Probleme

1. Stellen Sie sicher, dass Sie den **Full Client** verwenden.

   Bei der Verwendung der Oracle Instant Client-Version wurden verschiedene Probleme festgestellt. Darüber hinaus ist es unmöglich, die Zeitzonendatei auf dem Instant Client zu ändern.

1. Stellen Sie sicher, dass **Client-Version** und die **Datenbankserver-Version** identisch **&#x200B;**.

   Das Mischen von Versionen trotz der Kompatibilitätsmatrix von Oracle und der Empfehlung, Client- und Serverversionen aufeinander abzustimmen, verursacht bekanntermaßen Probleme.

   Überprüfen Sie außerdem den Wert für ORACLE_HOME, um sicherzustellen, dass er auf die erwartete Client-Version verweist (falls mehrere Versionen auf dem Computer installiert sind).

1. Stellen Sie sicher, dass der Client und der Server dieselbe **Zeitzonendatei** verwenden.

## Implementierungsschritte {#implementation-steps}

Adobe Campaign-Installationen für Linux müssen in der folgenden Reihenfolge ausgeführt werden: Serverinstallation gefolgt von Instanzkonfiguration.

Der Installationsprozess wird in diesem Kapitel beschrieben. Die Installationsschritte lauten wie folgt:

* Schritt 1: Installieren des Anwendungs-Servers, siehe [Installieren von Paketen mit Linux](../../installation/using/installing-packages-with-linux.md).
* Schritt 2: Integrieren mit einem Webserver (optional, je nach den bereitgestellten Komponenten).

Sobald die Installationsschritte abgeschlossen sind, müssen Sie die Instanzen, die Datenbank und den Server konfigurieren. Weitere Informationen hierzu finden Sie unter [Über die Erstkonfiguration](../../installation/using/about-initial-configuration.md).

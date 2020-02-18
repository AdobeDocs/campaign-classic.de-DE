---
title: Voraussetzungen für die Campaign-Installation unter Linux
seo-title: Voraussetzungen für die Campaign-Installation unter Linux
description: Voraussetzungen für die Campaign-Installation unter Linux
seo-description: null
page-status-flag: never-activated
uuid: 65c7af3f-ca1d-4255-b54a-6a3c83af40ae
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 3e2ccb70-6c0c-435f-9c06-f3e5e40367bb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: de04b5d3ceb883a571ee665f630be931a68a5a3e

---


# Voraussetzungen für die Campaign-Installation unter Linux{#prerequisites-of-campaign-installation-in-linux}

## Softwarevoraussetzungen {#software-prerequisites}

In diesem Abschnitt werden die Schritte für die Vorkonfiguration beschrieben, die vor der Installation von Adobe Campaign erforderlich sind.

Die für die Installation von Adobe Campaign erforderliche technische und Softwarekonfiguration ist in der [Kompatibilitätsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)beschrieben.

Zur Erinnerung: Die folgenden Komponenten müssen installiert und korrekt konfiguriert sein:

* Apache, siehe [Kompatibilitätsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html),
* Java JDK und OpenJDK, siehe [Java Development Kit - JDK](../../installation/using/application-server.md#java-development-kit---jdk),
* Bibliotheken, siehe [Bibliotheken](#libraries),
* Ebenen für den Datenbankzugriff, siehe Ebenen für den [Datenbankzugriff](#database-access-layers),
* LibreOffice, siehe [Installing LibreOffice for Debian](#installing-libreoffice-for-debian) and [Installing LibreOffice for CentOS](#installing-libreoffice-for-centos),
* Schriftarten finden Sie unter [Schriftarten für MTA-Statistiken](#fonts-for-mta-statistics) und [Schriftarten für japanische Instanzen](#fonts-for-japanese-instances).

>[!NOTE]
>
>Um einen Build unter oder gleich 8709 auf CentOS 7- und Debian 8-Plattformen zu installieren, muss das Modul apache access_compat aktiviert sein.

### Bibliotheken {#libraries}

Um Adobe Campaign unter Linux zu installieren, stellen Sie sicher, dass Sie über die erforderlichen Bibliotheken verfügen.

* Bibliothek C muss den TLS-Modus (Thread Local Storage) unterstützen können. Dieser Modus ist in den meisten Fällen aktiv, außer bei einigen Kerneln, für die Xen-Unterstützung deaktiviert wurde.

   Um dies zu überprüfen, können Sie den **unamen -a| grep xen** Befehl zum Beispiel.

   Wenn der Befehl nichts zurückgibt (leere Zeile), bedeutet dies, dass die Konfiguration korrekt ist.

* Sie müssen über die **Version 0.9.8** oder **1.0** von OpenSSL verfügen.

   Für RHEL 7-Distributionen ist Version 1.0 von OpenSSL erforderlich.

* Um Adobe Campaign verwenden zu können, muss die **libicu** -Bibliothek installiert sein.

   Die folgenden Versionen von **libicu** werden unterstützt (32 Bit oder 64 Bit):

   * RHEL 7, CentOS 7: libicu50
   * Debian 8: libicu52
   * Debian 9: libicu57
   Um Adobe Campaign verwenden zu können, muss die Bibliothek libc-ares installiert sein. Führen Sie unter RHEL/CentOS den folgenden Befehl aus:

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

Zusätzlich wurde in der Datei **/etc/sysconfig/httpd** die folgende Zeile hinzugefügt, um auf das Konfigurationsskript für die Adobe Campaign-Umgebung zu verweisen:

```
. ~neolane/nl6/env.sh
```

In RHEL und CentOS wurden Kompatibilitätsprobleme mit den Client-Ebenen von Datenbanken festgestellt, wenn SELinux aktiviert ist. Um sicherzustellen, dass Adobe Campaign ordnungsgemäß funktioniert, sollten Sie SELinux deaktivieren.

**Wenden Sie den folgenden Vorgang an:**

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

```
yum install xorg-x11-fonts-base xorg-x11-fonts-75dpi bitstream-vera-fonts dejavu-lgc-fonts
```

### Schriftarten für japanische Instanzen {#fonts-for-japanese-instances}

Schriftarten bestimmter Zeichen sind für die japanischen Instanzen erforderlich, um die Berichte in das PDF-Format zu exportieren.

Fügen Sie in Debian den Befehl hinzu:

```
aptitude install fonts-ipafont
```

Fügen Sie in Red Hat den Befehl hinzu:

```
yum install ipa-gothic-fonts ipa-mincho-fonts
```

### Installieren von LibreOffice für Debian {#installing-libreoffice-for-debian}

Für Debian sind die folgenden Konfigurationen erforderlich:

1. Installieren Sie die folgenden Standardpakete:

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. Installieren Sie die folgenden Schriftarten (optional, jedoch für japanische Instanzen dringend empfohlen):

   ```
   apt-get install fonts-ipafont
   ```

### Installieren von LibreOffice für CentOS {#installing-libreoffice-for-centos}

Die folgenden Konfigurationen sind mit CentOS erforderlich:

1. Installieren Sie die folgenden Standardpakete:

   ```
   yum install libreoffice-headless libreoffice-writer libreoffice-calc
   ```

1. Installieren Sie die folgenden Schriftarten (optional, jedoch für japanische Instanzen dringend empfohlen):

   ```
   yum install ipa-gothic-fonts ipa-mincho-fonts
   ```

## Ebenen für den Datenbankzugriff {#database-access-layers}

Die Zugriffsebenen für die verwendete Datenbank-Engine müssen auf Ihrem Server installiert sein und über das Adobe Campaign-Konto zugänglich sein. Versionen und Installationsmodi können je nach verwendeter Datenbank-Engine variieren.

Die unterstützte Pilotversion wird in [Kompatibilitätsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) erläutert.

Überprüfen Sie auch den Abschnitt &quot;Allgemeine [Datenbank](../../installation/using/database.md) &quot;.

### PostgreSQL {#postgresql}

Adobe Campaign unterstützt alle Versionen der PostgreSQL-Client-Bibliotheken ab Version 7.2: (**libpq.so.5**, **libpq.so.4**, **libpq.so.3.2** und **libpq.so.3.1**).

Für die Verwendung von PostgreSQL mit Adobe Campaign müssen auch die entsprechenden **pgcrypto** -Bibliotheken installiert werden.

### Oracle {#oracle}

Rufen Sie die Bibliotheksversion für 64-Bit Debian ab, d.h.: **libclntsh.so**, **libclntsh.so.11.1** und **libclntsh.so.10.1**.

Sie können ein Linux RPM-Paket vom Oracle Technology Network abrufen.

>[!NOTE]
>
>Wenn Sie den Oracle-Client bereits installiert haben, aber die globale Umgebung (z. B.: /etc/profile) nicht richtig konfiguriert ist, können Sie fehlende Informationen zum **nl6/customer.sh** -Skript hinzufügen. Weitere Informationen finden Sie unter [Umgebungsvariablen](../../installation/using/installing-packages-with-linux.md#environment-variables).

**Fehlerbehebung und Best Practices**

Probleme können nach einem Oracle-Client oder einem Server-Update, einer Versionsänderung oder der ersten Installation der Instanz auftreten.

Wenn Sie in der Client-Konsole feststellen, dass unerwartete Zeitverzögerungen (eine oder mehrere Stunden) in den Protokollen, letzte Verarbeitung des Workflows, nächste Verarbeitung usw. auftreten, kann es zu einem Problem zwischen der Bibliothek des Oracle-Clients und dem Oracle-Server kommen. Um solche Probleme zu vermeiden

1. Achten Sie darauf, den **vollständigen Client** zu verwenden.

   Bei der Verwendung der Version Oracle Instant Client wurden verschiedene Probleme identifiziert. Darüber hinaus ist es nicht möglich, die Zeitzonendatei auf einem Instant-Client zu ändern.

1. Vergewissern Sie sich, dass die **Clientversion** und die **Datenbankserverversion** **identisch** sind.

   Das Mischen von Versionen trotz der Kompatibilitätsmatrix und der Empfehlung von Oracle, Client- und Serverversionen auszurichten, verursacht bekanntermaßen Probleme.

   Überprüfen Sie auch den Wert ORACLE_HOME, um sicherzustellen, dass er auf die erwartete Clientversion verweist (falls mehrere Versionen auf dem Computer installiert sind).

1. Stellen Sie sicher, dass Client und Server dieselbe **Zeitzonendatei** verwenden.

### DB2 {#db2}

Die unterstützte Bibliotheksversion ist **libdb2.so**.

## Umsetzung {#implementation-steps}

Adobe Campaign-Installationen für Linux müssen in der folgenden Reihenfolge durchgeführt werden: Serverinstallation gefolgt von Instanzkonfiguration.

Der Installationsprozess wird in diesem Kapitel beschrieben. Die Installationsschritte lauten wie folgt:

* Schritt 1: Informationen zum Installieren des Anwendungsservers finden Sie unter [Installieren von Paketen mit Linux](../../installation/using/installing-packages-with-linux.md).
* Schritt 2: Integration mit einem Webserver (optional, je nach bereitgestellter Komponenten).

Nach Abschluss der Installationsschritte müssen Sie die Instanzen, die Datenbank und den Server konfigurieren. For more on this, refer to [About initial configuration](../../installation/using/about-initial-configuration.md).

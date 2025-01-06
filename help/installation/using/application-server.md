---
product: campaign
title: Anwendungs-Server
description: Anwendungs-Server
feature: Installation
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 2%

---

# Anwendungs-Server{#application-server}

Die erforderlichen Datenbankzugriffsebenen müssen auf dem Server installiert sein und vom Adobe Campaign-Konto aus zugänglich sein.

## Java Development Kit - JDK {#jdk}

Das Java Development Kit (JDK) ist ein Software Development Kit. Sie ist die grundlegende Komponente, die die Entwicklung von Java-Anwendungen und Java-Applets ermöglicht.

Der dynamische Web-Seiten-Generator verwendet die JSP-Technologie. Dazu ist eine Tomcat-Engine (von Apache) im Programm enthalten. Dazu ist ein Java Development Kit (JDK) erforderlich, das auf allen Servern installiert ist, auf denen die Adobe Campaign-Anwendung installiert ist.

Sie müssen zunächst ein JDK auf den Computern installieren, auf denen Sie den Adobe Campaign-Anwendungsserver ausführen möchten (**nlserver web** process), da es den Servlet-Container Apache Tomcat enthält, mit dem dynamische Web-Seiten (Berichte, Web-Formulare usw.) generiert werden.

Die Anwendung wurde für das von Oracle entwickelte Java Development Kit (JDK) sowie für **OpenJDK** genehmigt.

Die unterstützten Versionen werden in der Campaign-[ (Kompatibilitätsmatrix) ](../../rn/using/compatibility-matrix.md).


>[!AVAILABILITY]
>
>* Ab Version 7.4.1 erfordert Campaign mindestens **Java JDK 11**. Wenn Ihr Campaign-Server in einer Windows-Umgebung installiert ist, wird die Java Runtime (JRE) nicht mehr automatisch erkannt. Die Umgebungsvariable JRE_HOME muss auf den Ordner festgelegt sein, in dem Campaign die `bin/server/jvm.dll`-Datei finden kann. Wenn beispielsweise Ihr JDK 11 im Ordner `C:\Program Files\Java\jdk-11` installiert ist, muss Ihr JRE_HOME `C:\Program Files\Java\jdk-11` sein.
>
>* Ab Version 7.4.1 ist Tomcat 10.1 die Standardversion.
>

### Empfehlungen

Befolgen Sie bei der Installation und Aktualisierung Ihres Java Development Kits die folgenden Empfehlungen:

* Das Java Development Kit kann mit der entsprechenden JDK-Version installiert werden, die bereits von anderen Anwendungen auf dem Computer verwendet wird.

* Bei der Installation des JDK ist die Integration in die Webbrowser nicht erforderlich.

* Auf einem Computer, der nur Versandagenten (**nlserver mta**-Prozess) oder den Workflow-Server (**nlserver wfserver**-Prozess) ausführt, ist die Installation eines JDK nicht erforderlich.

* Beim Upgrade der Java-Version müssen Sie zunächst die vorherige Version deinstallieren. Beide auf demselben Computer installierten Java-Versionen können Konflikte verursachen.

  Als On-Premise-Kunde können Sie überprüfen, ob `LD_LIBRARY_PATH` [Umgebungsvariable](installing-packages-with-linux.md#environment-variables) auf die neueste Version festgelegt ist (z. B. Java11). Wenn eine frühere Version verwendet wird (z. B. Java8), dann muss es aktualisiert werden. Für JDK 11 lautet der Pfad zum Suchen von JDK-Bibliotheken `/usr/lib/jvm/java-11-openjdk-amd64/lib`.


### Installationsschritte

Java Development Kit ist plattformspezifisch: Für jedes Betriebssystem sind separate Installationsprogramme erforderlich.

Um JDK herunterzuladen, verbinden Sie sich mit der [Oracle-Website](https://www.oracle.com/technetwork/java/javase/downloads/index.html){target="_blank"}.

>[!CAUTION]
>
> Stellen Sie sicher, dass Sie ein Java Development Kit (JDK) und keine Java Runtime Environment (JRE) herunterladen.


Um JDSL in einer Linux-Umgebung zu installieren, empfiehlt Adobe die Verwendung eines Package Managers.

Verwenden Sie für Debian den folgenden Befehl:

```sql
apt install openjdk-11-jdk-headless
```

Verwenden Sie für RHEL den folgenden Befehl:

```sql
dnf install java-11-openjdk-headless
```



## Berichte exportieren {#exporting-reports}

Sie können Adobe Campaign verwenden, um Berichte in Microsoft Excel und Adobe PDF zu exportieren.

* Für das Microsoft Excel-Format stützt sich Adobe Campaign auf **LibreOffice**.

* Für das Adobe PDF-Format verwendet Adobe Campaign den **PhantomJS**-Konverter. PhantomJs ist im Werkspaket enthalten und LibreOffice muss auf dem/den Computer(n) installiert sein, auf dem/denen der Adobe Campaign-Anwendungsserver ausgeführt wird (**nlserver-**).

>[!NOTE]
>
>Für Linux müssen Sie Schriftarten hinzufügen. Weitere Informationen hierzu finden Sie unter [ für MTA-Statistiken](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

Mit SpamAssassin können Sie E-Mails eine Punktzahl zuweisen, um festzustellen, ob eine Nachricht von Anti-Spam-Tools, die beim Empfang verwendet werden, als unerwünscht eingestuft werden könnte. Die Installation ist optional.

Die Qualifizierung von E-Mails als unerwünscht durch SpamAssassin basiert ausschließlich auf Filter- und Bewertungsregeln. Diese Regeln müssen daher mindestens einmal täglich aktualisiert werden, damit Ihre SpamAssassin-Installation und ihre Integration in Adobe Campaign voll funktionsfähig sind und die Relevanz der Ihren Sendungen vor dem Versand zugewiesenen Bewertungen gewährleistet ist. Dieses Update liegt in der Verantwortung des Serveradministrators, der SpamAssassin hostet.

Die unterstützte Mindestversion ist: **3.4**

SpamAssassin benötigt einen HTTP-Internetzugang (TCP/80).

Die Installations- und Konfigurationsphasen von SpamAssassin werden unter [Konfigurieren von SpamAssassin](../../installation/using/configuring-spamassassin.md) beschrieben.

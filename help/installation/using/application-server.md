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
source-git-commit: 387bcf39c13cc1f9544433b9441769f4b16b52ca
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 2%

---

# Anwendungs-Server{#application-server}

Die erforderlichen Datenbankzugriffsebenen müssen auf dem Server installiert sein und über das Adobe Campaign-Konto zugänglich sein.

## Java Development Kit - JDK {#jdk}

Java Development Kit (JDK) ist ein Software Development Kit. Es ist die grundlegende Komponente, die die Java-Anwendungs- und Java-Applet-Entwicklung ermöglicht.

Der dynamische Web-Seiten-Generator verwendet die JSP-Technologie. Dazu ist eine Tomcat-Engine (von Apache) in der Anwendung enthalten. Dazu ist ein Java Development Kit (JDK) erforderlich, das auf allen Servern installiert ist, auf denen die Adobe Campaign-Anwendung installiert ist.

Sie müssen zunächst ein JDK auf den Computern installieren, auf denen Sie den Adobe Campaign-Anwendungsserver ausführen möchten (**nlserver web** -Prozess), da es einen Servlet-Container, Apache Tomcat, enthält, der zum Generieren dynamischer Webseiten (Berichte, Webformulare usw.) verwendet wird.

Die Anwendung wurde für das von Oracle entwickelte Java Development Kit (JDK) sowie für **OpenJDK** genehmigt.

Die unterstützten Versionen werden in der Campaign [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md) beschrieben.


>[!AVAILABILITY]
>
>* Ab Version 7.4.1 erfordert Campaign mindestens **Java JDK 11**. Wenn Ihr Campaign-Server in einer Windows-Umgebung installiert ist, wird Java Runtime (JRE) nicht mehr automatisch erkannt. Die Umgebungsvariable JRE_HOME muss auf den Ordner festgelegt werden, in dem Campaign die Datei `bin/server/jvm.dll` finden kann. Wenn beispielsweise Ihr JDK 11 im Ordner &quot;`C:\Program Files\Java\jdk-11`&quot;installiert ist, muss Ihr JRE_HOME &quot;`C:\Program Files\Java\jdk-11`&quot;lauten.
>
>* Ab Version 7.4.1 ist Tomcat 10.1 die Standardversion.
>

### Empfehlungen

Wenden Sie beim Installieren und Aktualisieren Ihres Java Development Kits die folgenden Empfehlungen an:

* Java Development Kit kann mit der entsprechenden JDK-Version installiert werden, die bereits von anderen Anwendungen auf dem Computer verwendet wird.

* Bei der Installation des JDK ist die Integration mit den Webbrowsern nicht erforderlich.

* Auf einem Computer, auf dem nur Versandagenten (**nlserver mta** -Prozess) oder der Workflow-Server (**nlserver wfserver** -Prozess) ausgeführt werden, ist die Installation eines JDK nicht erforderlich.

* Beim Aktualisieren Ihrer Java-Version müssen Sie zunächst die vorherige Version deinstallieren. Beide Versionen von Java, die auf demselben Computer installiert sind, können Konflikte verursachen.

  Als On-Premise-Kunde können Sie überprüfen, ob die Umgebungsvariable `LD_LIBRARY_PATH` [2} auf die neueste Version eingestellt ist (z. B. ](installing-packages-with-linux.md#environment-variables) java11). Wenn sie auf eine frühere Version festgelegt ist (z. B. Java8), dann muss sie aktualisiert werden. Für JDK 11 lautet der Pfad zum Suchen von JDK-Bibliotheken `/usr/lib/jvm/java-11-openjdk-amd64/lib`.


### Installationsschritte

Java Development Kit ist plattformspezifisch: Für jedes Betriebssystem sind separate Installationsprogramme erforderlich.

Um JDK herunterzuladen, stellen Sie eine Verbindung zur [Oracle-Website](https://www.oracle.com/technetwork/java/javase/downloads/index.html){target="_blank"} her.

>[!CAUTION]
>
> Laden Sie unbedingt ein Java Development Kit (JDK) herunter, nicht eine Java Runtime Environment (JRE).


Um die JDSL in einer Linux-Umgebung zu installieren, empfiehlt Adobe die Verwendung eines Paketmanagers.

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

* Beim Excel-Format für Microsoft verlässt sich Adobe Campaign auf **LibreOffice**.

* Für das Adobe PDF-Format verwendet Adobe Campaign den Konverter **PhantomJS** . PhantomJs ist im Factory-Paket enthalten und LibreOffice muss auf den Computern installiert sein, auf denen der Adobe Campaign-Anwendungsserver ausgeführt wird (**nlserver web** -Prozess).

>[!NOTE]
>
>Für Linux müssen Sie Schriftarten hinzufügen. Weitere Informationen hierzu finden Sie unter [Schriftarten für MTA-Statistiken](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

Mit SpamAssassin können Sie E-Mails eine Punktzahl zuweisen, um festzustellen, ob eine Nachricht von Anti-Spam-Tools, die beim Empfang verwendet werden, als unerwünscht betrachtet werden kann. Die Installation ist optional.

Die Einstufung von E-Mails als unerwünscht durch SpamAssassin basiert ausschließlich auf Filter- und Scoring-Regeln. Diese Regeln müssen daher mindestens einmal täglich aktualisiert werden, damit Ihre SpamAssassin-Installation und ihre Integration in Adobe Campaign voll funktionsfähig sind und die Relevanz der für Ihre Sendungen zugewiesenen Bewertungen vor dem Versand gewährleistet ist. Für diese Aktualisierung ist der Serveradministrator verantwortlich, der SpamAssassin hostet.

Die mindestens unterstützte Version ist: **3.4**

SpamAssassin benötigt einen HTTP-Internetzugang (tcp/80).

Die Installations- und Konfigurationsschritte für SpamAssassin finden Sie unter [SpamAssassin konfigurieren](../../installation/using/configuring-spamassassin.md) .

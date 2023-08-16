---
product: campaign
title: Anwendungs-Server
description: Anwendungs-Server
feature: Installation
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
badge-v7-prem: label="On-Premise und Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 6%

---

# Anwendungs-Server{#application-server}



Die erforderlichen Datenbankzugriffsebenen müssen auf dem Server installiert sein und über das Adobe Campaign-Konto zugänglich sein.

## Java Development Kit - JDK {#java-development-kit---jdk}

Der dynamische Web-Seiten-Generator verwendet die JSP 1.2-Technologie. Dazu ist eine Tomcat-Engine (von Apache) in der Anwendung enthalten. Dazu ist ein Java Development Kit (JDK) erforderlich, das auf allen Servern installiert ist, auf denen die Adobe Campaign-Anwendung installiert ist.

Sie müssen zunächst ein JDK auf den Computern installieren, auf denen Sie den Adobe Campaign-Anwendungsserver ausführen möchten (**nlserver web** Prozess), da er einen Servlet-Container, Apache Tomcat, enthält, der zum Generieren dynamischer Webseiten (Berichte, Webformulare usw.) verwendet wird.

Der Antrag wurde für das Java Development Kit (JDK) genehmigt, das von Oracle entwickelt wurde, sowie für **OpenJDK**.

Die unterstützten Versionen werden in Campaign beschrieben. [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md).

>[!NOTE]
>
>Es kann mit der entsprechenden JDK-Version installiert werden, die bereits von anderen Anwendungen auf dem Computer verwendet wird.
>  
>Bei der Installation müssen Sie die Integration mit den Webbrowsern nicht durchführen.
>
>Auf einem Computer, der nur Versandagenten ausführt (**nlserver mta** Prozess) oder dem Workflow-Server (**nlserver wfserver** Prozess), ist die Installation eines JDK nicht erforderlich.

Um Java JDK herunterzuladen, verbinden Sie sich mit: [https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

**Warnung: Sie müssen ein JDK herunterladen, kein JRE.**

>[!CAUTION]
>
>Um die Leistung des Plattformbetriebs zu erhalten und die Kompatibilität mit der installierten Version sicherzustellen, müssen Sie die automatischen JDK-Aktualisierungsfunktionen in Windows und Linux deaktivieren.

Um JDSL in einer Linux-Umgebung zu installieren, ist es vorzuziehen, einen Package Manager zu verwenden.

Verwenden Sie in Debian 8 und 9 den folgenden Befehl:

```
aptitude install openjdk-8-jdk
```

Verwenden Sie für RHEL 7 den folgenden Befehl:

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

Unter Linux muss OpenSSL installiert sein. Adobe Campaign unterstützt OpenSSL-Version 1.0.2 oder höher.

## Berichtexport {#exporting-reports}

Mit Adobe Campaign können Sie Plattformberichte im Microsoft Excel- und Adobe PDF-Format exportieren. Für das Microsoft Excel-Format verwendet Adobe Campaign **LibreOffice**. Für das Adobe PDF-Format verwendet Adobe Campaign die **PhantomJS** Konverter. PhantomJs ist im Factory-Paket enthalten und LibreOffice muss auf den Computern installiert sein, auf denen der Adobe Campaign-Anwendungsserver ausgeführt wird (**nlserver web** Prozess).

>[!NOTE]
>
>Für Linux müssen Sie Schriftarten hinzufügen. Weitere Informationen hierzu finden Sie unter [Schriftarten für MTA-Statistiken](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

Mit SpamAssassin können Sie E-Mails eine Punktzahl zuweisen, um festzustellen, ob eine Nachricht von Anti-Spam-Tools, die beim Empfang verwendet werden, als unerwünscht betrachtet werden kann. Die Installation ist optional.

Die Einstufung von E-Mails als unerwünscht durch SpamAssassin basiert ausschließlich auf Filter- und Scoring-Regeln. Diese Regeln müssen daher mindestens einmal täglich aktualisiert werden, damit Ihre SpamAssassin-Installation und ihre Integration in Adobe Campaign voll funktionsfähig sind und die Relevanz der für Ihre Sendungen zugewiesenen Bewertungen vor dem Versand gewährleistet ist. Für diese Aktualisierung ist der Serveradministrator verantwortlich, der SpamAssassin hostet.

Die mindestens unterstützte Version ist: **3,4**

SpamAssassin benötigt einen HTTP-Internetzugang (tcp/80).

Die Installations- und Konfigurationsschritte für SpamAssassin finden Sie in [SpamAssassin konfigurieren](../../installation/using/configuring-spamassassin.md).

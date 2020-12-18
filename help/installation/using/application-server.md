---
solution: Campaign Classic
product: campaign
title: Anwendungs-Server
description: Anwendungs-Server
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 1%

---


# Anwendungs-Server{#application-server}

Die erforderlichen Datenbankzugriffsebenen müssen auf dem Server installiert sein und über das Adobe Campaign-Konto zugänglich sein.

## Java Development Kit - JDK {#java-development-kit---jdk}

Der dynamische Webseiten-Generator verwendet die JSP 1.2-Technologie. Hierfür wird eine Tomcat-Engine (aus dem Apache) in den Antrag aufgenommen. Es ist ein Java Development Kit (JDK) erforderlich, das auf allen Servern installiert ist, auf denen die Adobe Campaign-Anwendung installiert ist.

Sie müssen zuerst ein JDK auf den Computern installieren, auf denen Sie den Adobe Campaign-Anwendungsserver ausführen möchten (**nlserver web**), da dieser einen Servlet-Container, Apache Tomcat, enthält, der zum Generieren dynamischer Webseiten (Berichte, Webformulare usw.) verwendet wird.

Der Antrag wurde für das von Oracle entwickelte Java Development Kit (JDK) sowie für **OpenJDK** genehmigt.

Die unterstützten Versionen sind in Kampagne [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md) aufgeführt.

>[!NOTE]
>
>Es kann mit der entsprechenden JDK-Version installiert werden, die bereits von anderen Anwendungen auf dem Computer verwendet wird.
>  
>Bei der Installation müssen Sie die Integration nicht mit den Webbrowsern durchführen.
>
>Auf einem Computer, auf dem nur Versand-Agenten (**nlserver-mta**-Prozess) oder der Workflow-Server (**nlserver-wfserver**-Prozess) ausgeführt werden, muss kein JDK installiert werden.

So laden Sie Java JDK herunter: [https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

**Warnung: Sie müssen ein JDK herunterladen, kein JRE.**

>[!CAUTION]
>
>Um die Leistung des Plattformbetriebs zu erhalten und die Kompatibilität mit der installierten Version sicherzustellen, müssen Sie die automatischen JDK-Aktualisierungsfunktionen in Windows und Linux deaktivieren.

Um die JDSL in einer Linux-Umgebung zu installieren, sollten Sie vorzugsweise einen Package Manager verwenden.

Verwenden Sie in Debian 8 und 9 den folgenden Befehl:

```
aptitude install openjdk-8-jdk
```

Verwenden Sie für RHEL 7 den folgenden Befehl:

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

Unter Linux muss OpenSSL installiert werden. Die von Adobe Campaign unterstützten Versionen sind **OpenSSL 1.0.1** und **OpenSSL 0.9.8**. Die Unterversionen 0.9.8g bis 0.9.8o werden akzeptiert.

## Berichtexport {#exporting-reports}

Mit Adobe Campaign können Sie Plattformberichte im Microsoft Excel- und Adobe PDF-Format exportieren. Für das Microsoft Excel-Format verwendet Adobe Campaign **LibreOffice**. Für das Adobe PDF-Format verwendet Adobe Campaign den Konverter **PhantomJS**. PhantomJs ist im Factory-Paket enthalten, und LibreOffice muss auf den Computern installiert sein, auf denen der Adobe Campaign-Anwendungsserver ausgeführt wird (**nlserver web**).

>[!NOTE]
>
>Unter Linux müssen Sie Schriftarten hinzufügen. Weitere Informationen finden Sie unter [Schriftarten für MTA-Statistiken](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

Mit SpamAssassin können Sie E-Mails eine Punktzahl zuweisen, um festzustellen, ob eine Nachricht von den Anti-Spam-Tools, die bei der Rezeption verwendet werden, als unerwünscht eingestuft werden könnte. Die Installation ist optional.

Die Einstufung von E-Mails als unerwünscht durch SpamAssassin basiert ausschließlich auf Filter- und Bewertungsregeln. Diese Regeln müssen daher mindestens einmal täglich aktualisiert werden, damit Ihre SpamAssassin-Installation und ihre Integration in Adobe Campaign voll funktionsfähig sind und die Relevanz der Ergebnisse, die Ihren Versänden zugewiesen wurden, vor dem Versand gewährleistet ist. Für dieses Update ist der Serveradministrator verantwortlich, der SpamAssassin hostet.

Die Mindestversion wird unterstützt: **3.4**

SpamAssassin benötigt einen HTTP-Internetzugang (tcp/80).

Installations- und Konfigurationsschritte für SpamAssassin finden Sie unter [SpamAssassin konfigurieren](../../installation/using/configuring-spamassassin.md).

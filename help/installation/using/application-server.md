---
title: Anwendungsserver
seo-title: Anwendungsserver
description: Anwendungsserver
seo-description: null
page-status-flag: never-activated
uuid: 837c6a5c-53a4-4d1b-a084-9cf77e7a0eee
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 7a9e028c-255d-4aad-9827-d19f9a7897b2
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Application server{#application-server}

Die erforderlichen Datenbankzugriffsebenen müssen auf dem Server installiert sein und über das Adobe Campaign-Konto zugänglich sein.

## Java Development Kit - JDK {#java-development-kit---jdk}

Der dynamische Webseiten-Generator verwendet die JSP 1.2-Technologie. Hierfür wird eine Tomcat-Engine (aus dem Apache) in den Antrag aufgenommen. Es ist ein Java Development Kit (JDK) erforderlich, das auf allen Servern installiert ist, auf denen die Adobe Campaign-Anwendung installiert ist.

Sie müssen zuerst ein JDK auf den Computern installieren, auf denen Sie den Adobe Campaign-Anwendungsserver (**nlserver-Webprozess** ) ausführen möchten, da es einen Servlet-Container, Apache Tomcat, enthält, der zum Generieren dynamischer Webseiten (Berichte, Webformulare usw.) verwendet wird.

Die Anwendung wurde für das von Oracle entwickelte Java Development Kit (JDK) sowie für **OpenJDK** genehmigt.

The supported versions are detailed in the [Compatibility matrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

>[!NOTE]
>
>Es kann mit der entsprechenden JDK-Version installiert werden, die bereits von anderen Anwendungen auf dem Computer verwendet wird.
>  
>Bei der Installation müssen Sie die Integration nicht mit den Webbrowsern durchführen.
>
>Auf einem Computer, auf dem nur Auslieferungsagenten (**nlserver-mta** -Prozess) oder der Workflow-Server (**nlserver-wfserver** -Prozess) ausgeführt werden, ist die Installation eines JDK nicht erforderlich.

So laden Sie Java JDK herunter: [https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

**Warnung: Sie müssen ein JDK herunterladen, kein JRE.**

>[!CAUTION]
>
>Um die Leistung des Plattformbetriebs zu erhalten und die Kompatibilität mit der installierten Version sicherzustellen, müssen Sie die automatischen JDK-Aktualisierungsfunktionen in Windows und Linux deaktivieren.

Um JDSL in einer Linux-Umgebung zu installieren, sollten Sie vorzugsweise einen Package Manager verwenden.

Verwenden Sie in Debian 7 und 8 den folgenden Befehl:

```
aptitude install openjdk-7-jdk
```

Verwenden Sie für RHEL 6 den folgenden Befehl:

```
yum install java-1.8.0-openjdk
```

Verwenden Sie für RHEL 7 den folgenden Befehl:

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

Unter Linux muss OpenSSL installiert werden. Die von Adobe Campaign unterstützten Versionen sind **OpenSSL 1.0.1** und **OpenSSL 0.9.8**. Die Unterversionen 0.9.8g bis 0.9.8o werden akzeptiert.

>[!NOTE]
>
>Für RHEL 6 und CentOS 6 ist openSSL 1.0 erforderlich.

## Berichtexport {#exporting-reports}

Mit Adobe Campaign können Sie Plattformberichte im Microsoft Excel- und Adobe PDF-Format exportieren. Für das Microsoft Excel-Format verwendet Adobe Campaign **LibreOffice**. Für das Adobe PDF-Format verwendet Adobe Campaign den **PhantomJS** -Konverter. PhantomJs ist im Factory-Paket enthalten, und LibreOffice muss auf den Computern installiert sein, auf denen der Adobe Campaign-Anwendungsserver ausgeführt wird (**nlserver-Webprozess** ).

>[!NOTE]
>
>Unter Linux müssen Sie Schriftarten hinzufügen. Weitere Informationen dazu finden Sie in den [Schriftarten für MTA-Statistiken](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

Mit SpamAssassin können Sie E-Mails eine Punktzahl zuweisen, um festzustellen, ob eine Nachricht von den Anti-Spam-Tools, die bei der Rezeption verwendet werden, als unerwünscht eingestuft werden könnte. Die Installation ist optional.

Die Einstufung von E-Mails als unerwünscht durch SpamAssassin basiert ausschließlich auf Filter- und Bewertungsregeln. Diese Regeln müssen daher mindestens einmal täglich aktualisiert werden, damit Ihre SpamAssassin-Installation und ihre Integration in Adobe Campaign voll funktionsfähig sind und die Relevanz der Ergebnisse, die Ihren Auslieferungen zugewiesen wurden, vor dem Versand gewährleistet ist. Für dieses Update ist der Serveradministrator verantwortlich, der SpamAssassin hostet.

Folgende Versionen werden mindestens unterstützt: **3.2.5** und **3.3.2**.

SpamAssassin benötigt einen HTTP-Internetzugang (tcp/80).

Installations- und Konfigurationsschritte für SpamAssassin finden Sie unter SpamAssassin [konfigurieren](../../installation/using/configuring-spamassassin.md).

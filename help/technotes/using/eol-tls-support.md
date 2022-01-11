---
product: campaign
title: Beendigung der Unterstützung für TLS 1.0 und 1.1
description: Beendigung der Unterstützung für TLS 1.0 und 1.1
audience: delivery
content-type: reference
topic-tags: tracking-messages
source-git-commit: 70240d5f62fd3d7b755389b5ad8c4b499c94657d
workflow-type: ht
source-wordcount: '842'
ht-degree: 100%

---

# Beendigung der Unterstützung für TLS 1.0 und 1.1{#eol-tls-support}

![](../../assets/v7-only.svg)

Adobe unterstützt keine Benutzersysteme und Client-Systeme mehr, die nicht mit dem Protokoll Transport Layer Security (TLS) 1.2 konform sind. Falls Sie weiterhin ältere Versionen von TLS verwenden, könnten Sie den Zugriff auf alle Produkte und Services von Adobe verlieren.

## Warum wird diese Seite angezeigt?

Wenn Sie die Meldung sehen: **Diese Seite kann nicht angezeigt werden**, bedeutet dies, dass die Anwendungen, Web-Seiten oder Services von Adobe, auf die Sie zugreifen möchten, eine sicherere Netzwerkverbindung mit Ihrem Web-Browser, Betriebssystem oder Programm erfordern. Für sichere Netzwerkkommunikation und Datenaustausch zwischen Benutzersystemen und Anwendungen und Web-Services von Adobe ist die Verwendung von **TLS 1.2** zwingend erforderlich.

Adobe unterstützt jetzt niedrigere Versionen von TLS (einschließlich TLS 1.0 und 1.1) nicht mehr. Technische Details zum Protokoll TLS 1.2 finden Sie unter [Häufig gestellte Fragen](#faq).

## Was kann ich tun, um den Service wieder aufzunehmen?

Moderne Webbrowser unterstützen TLS 1.2. Durch eine Aktualisierung Ihres Browsers können Sie auf diese Anwendungen und Services zugreifen.

Sie können einen der folgenden gängigen Browser herunterladen und installieren:

* [Google Chrome](https://www.google.com/chrome/)
* [Apple Safari](https://www.apple.com/safari/)
* [Firefox](https://www.mozilla.org/de/firefox/new/)
* [Microsoft Edge](https://www.microsoft.com/de-de/edge)

Wenn Sie einen anderen Browser verwenden möchten, stellen Sie sicher, dass dieser TLS 1.2 unterstützt.

Ihr Betriebssystem und Ihre Anwendungen müssen auch TLS 1.2 unterstützen. Wenn die Aktualisierung Ihres Browsers Ihr Problem nicht behebt, prüfen Sie, ob Ihr Computer die in der [Kompatibilitätsmatrix für Campaign](../../rn/using/compatibility-matrix.md) aufgeführten Systemanforderungen erfüllt.

## Häufig gestellte Fragen{#faq}

* **Was ist Transport Layer Security (TLS)?**

   [Transport Layer Security](https://de.wikipedia.org/wiki/Transport_Layer_Security) (TLS) ist ein Sicherheitsprotokoll, das Datenschutz und Datenintegrität zwischen zwei kommunizierenden Anwendungen ermöglicht. Dieses Protokoll wird häufig für Webbrowser und andere Anwendungen eingesetzt, bei denen Daten sicher über ein Netzwerk ausgetauscht werden müssen.

   Gemäß der Protokollspezifikation umfasst TLS zwei Ebenen: das TLS-Record-Protokoll und das TLS-Handshake-Protokoll. Das Record-Protokoll bietet Verbindungssicherheit. Das Handshake-Protokoll ermöglicht es dem Server und Client, sich gegenseitig zu authentifizieren und vor dem Datenaustausch Verschlüsselungsalgorithmen und kryptografische Schlüssel auszuhandeln.

* **Wie wirkt sich das aus?**

   Die Sicherheitsstandards von Adobe erfordern seit Mai 2018 die Beendigung älterer Protokolle und schreiben die Verwendung von TLS 1.2 als aktueller Version vor. Wenn Ihr System nicht TLS 1.2-kompatibel ist, ist der Zugriff auf einige Adobe-Anwendungen und -Services eingeschränkt.

* **Wie wirkt sich TLS auf Sie aus?**

   Sie können mit einigen Adobe-Anwendungen und -Services nur über eine sichere Netzwerkverbindung interagieren. Mit TLS können Sie sicherstellen, dass die Verbindung zwischen Ihrem Browser und diesen Anwendungen und Web-Services sicher und zuverlässig ist.

   Mit der Veröffentlichung neuer Browser und Betriebssysteme werden die Sicherheitsstandards aktualisiert, um ein höheres Maß an Datenschutz und Datenintegrität zu gewährleisten. Ältere Versionen dieser Browser oder Betriebssysteme werden jedoch nicht aktualisiert und enthalten nicht die neuesten Standards.

   Da das Sicherheitsniveau steigt, werden diese älteren, weniger sicheren Browser-Versionen und Anwendungen nicht mehr unterstützt.

   Um eine Verbindung mit sicheren Websites herstellen zu können, aktualisieren Sie Ihre Betriebssystem- und Browser-Versionen.

* **Ist TLS anfällig für Hacker?**

   Es wurden Angriffe auf TLS 1.0 mit seiner älteren Verschlüsselungsmethode dokumentiert, und die älteren Versionen sind anfälliger als TLS 1.2. Weitere Informationen finden Sie unter „Angriffe auf TLS/SSL“.

* **Warum deaktiviert Adobe die Unterstützung für TLS 1.0 und 1.1?**

   Adobe verfolgt Sicherheitsstandards, die die Beendigung der Unterstützung älterer Protokolle erfordern. Einer dieser Standards gewährleistet die Konformität mit der Zahlungskartenindustrie (Payment Card Industry, PCI). PCI Adaptation Server umfasst eine Reihe von Sicherheitsstandards, die von Organisationen eingehalten werden müssen, die Kreditkartendaten annehmen, verarbeiten, speichern oder übertragen, um eine sichere Umgebung zu gewährleisten.

   Aufgrund der obligatorischen Einhaltung von PCI ist die Verwendung von TLS 1.1 oder höher ab Mai 2018 erforderlich.

* **Warum schreibt Adobe die Verwendung von TLS 1.2 vor, anstatt TLS 1.1 oder TLS 1.0 zuzulassen?**

   Die meisten Anforderungen für Anwendungen und Web-Services von Adobe stammen aus TLS 1.2-kompatiblen Benutzersystemen, während der Datentransfer von TLS 1.1-Systemen gering ist.

   Adobe hat auf TLS 1.2 umgestellt, um die Sicherheit bei der Nutzung von Anwendungen und Web-Services zu erhöhen.

* **Bis wann kann ich eine ältere Version von TLS verwenden?**

   Adobe empfiehlt Benutzern, die älteren Versionen möglichst schnell zu aktualisieren, um Sicherheitsprobleme zu vermeiden. Weitere Informationen erhalten Sie bei der Kundenunterstützung von Adobe oder Ihrem Customer Success Manager.

* **Welche Fehlermeldung wird angezeigt, wenn ich einen Browser verwende, der nicht für TLS 1.2 konfiguriert ist?**

   Das hängt vom verwendeten Browser ab. Alle in der [Campaign-Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md) genannten Browser sind für die Verwendung von TLS 1.2 konfiguriert. Wenn Sie eine Version verwenden, die nicht in der Liste aufgeführt ist, aktualisieren Sie Ihren Browser.

   Adobe hat keine Kontrolle über Fehlermeldungen, die von der SSL-Kommunikationsschicht generiert wurden. Der Browser generiert diese Nachrichten, bevor er eine Verbindung zu Anwendungen und Services von Adobe herstellt. Hier ist ein Beispiel für einen Fehler, der mit Internet Explorer 11 unter Windows 7 auftreten kann:

   ![](assets/do-not-translate/page-not-displayed.png)

   TLS 1.2 ist in Internet Explorer 11 standardmäßig aktiviert, aber falls es deaktiviert ist, können Sie es aktivieren. Aktivieren Sie in diesem Fall TLS 1.2 über das Dialogfeld „Erweiterte Einstellungen“, anstatt andere Optionen zu verwenden. Es können auch andere Fehler wie der folgende auftreten:

   * Verbindung mit dem Service unmöglich
   * Service ist nicht verfügbar
   * Verbindungsfehler

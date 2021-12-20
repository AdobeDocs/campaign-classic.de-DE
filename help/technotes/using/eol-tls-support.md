---
product: campaign
title: Unterstützung von TLS 1.0 und 1.1 wird eingestellt
description: Unterstützung von TLS 1.0 und 1.1 wird eingestellt
audience: delivery
content-type: reference
topic-tags: tracking-messages
source-git-commit: 70240d5f62fd3d7b755389b5ad8c4b499c94657d
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 1%

---

# Unterstützung von TLS 1.0 und 1.1 wird eingestellt{#eol-tls-support}

![](../../assets/v7-only.svg)

Adobe unterstützt keine Benutzersysteme und Clientsysteme mehr, die nicht mit dem Transport Layer Security (TLS) 1.2-Protokoll konform sind. Wenn Sie weiterhin ältere Versionen von TLS verwenden, könnten Sie den Zugriff auf alle Adobe-Produkte und -Dienste verlieren.

## Warum wird diese Seite angezeigt?

Wenn die folgende Meldung angezeigt wird: **Diese Seite kann nicht angezeigt werden** bedeutet dies, dass die Adobe Apps, Webseiten oder Dienste, auf die Sie zugreifen möchten, eine sicherere Netzwerkverbindung mit Ihrem Webbrowser, Betriebssystem oder Ihrer App erfordern. Die Verwendung von **TLS 1.2** für sichere Netzwerkkommunikation und Datenaustausch zwischen Benutzersystemen und Adobe-Apps und Webdiensten.

Adobe unterstützt jetzt niedrigere Versionen von TLS (einschließlich TLS 1.0 und 1.1). Technische Details zum TLS 1.2-Protokoll finden Sie unter [Häufig gestellte Fragen](#faq).

## Was kann ich tun, um den Dienst wieder aufzunehmen?

Moderne Webbrowser unterstützen TLS 1.2. Durch die Aktualisierung Ihres Browsers können Sie auf diese Apps und Dienste zugreifen.

Sie können einen der folgenden gängigen Browser herunterladen und installieren:

* [Google Chrome](https://www.google.com/chrome/)
* [Apple Safari](https://www.apple.com/safari/)
* [Firefox](https://www.mozilla.org/en-US/firefox/new/)
* [Microsoft Edge](https://www.microsoft.com/en-us/edge)

Wenn Sie einen anderen Browser verwenden, stellen Sie sicher, dass dieser TLS 1.2 unterstützt.

Ihr Betriebssystem und Ihre Anwendungs-Frameworks müssen auch TLS 1.2 unterstützen. Wenn das Upgrade Ihres Browsers Ihr Problem nicht behebt, stellen Sie sicher, dass Ihr Computer die in [Campaign-Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md).

## Häufig gestellte Fragen{#faq}

* **Was ist Transport Layer Security (TLS)?**

   [Transport Layer Security](https://en.wikipedia.org/wiki/Transport_Layer_Security) (TLS) ist ein Sicherheitsprotokoll, das Datenschutz und Datenintegrität zwischen zwei kommunizierenden Anwendungen ermöglicht. Sie wird für Webbrowser und andere Anwendungen weit verbreitet, bei denen Daten sicher über ein Netzwerk ausgetauscht werden müssen.

   Gemäß der Protokollspezifikation umfasst TLS zwei Ebenen: das TLS-Record-Protokoll und das TLS-Handshake-Protokoll. Das Protokoll &quot;Record&quot;bietet Verbindungssicherheit. Das Handshake-Protokoll ermöglicht es dem Server und Client, sich gegenseitig zu authentifizieren und Verschlüsselungsalgorithmen und kryptografische Schlüssel vor dem Datenaustausch auszuhandeln.

* **Wie wirkt sich das aus?**

   Die Sicherheitsstandards der Adobe erfordern die Einstellung älterer Protokolle ab Mai 2018 und schreiben die Verwendung von TLS 1.2 als aktueller Version vor. Wenn Ihr System nicht TLS 1.2-kompatibel ist, ist der Zugriff auf einige Adobe-Apps und -Dienste eingeschränkt.

* **Wie wirkt sich TLS auf Sie aus?**

   Sie können nur über eine sichere Netzwerkverbindung mit einigen Adobe-Apps und -Diensten interagieren. Mit TLS können Sie sicherstellen, dass die Verbindung zwischen Ihrem Browser und diesen Apps und Webdiensten sicher und zuverlässig ist.

   Mit der Veröffentlichung neuer Browser und Betriebssysteme werden die Sicherheitsstandards aktualisiert, um ein höheres Maß an Privatsphäre und Datenintegrität zu gewährleisten. Ältere Versionen dieser Browser oder Betriebssysteme werden jedoch nicht aktualisiert und enthalten nicht die neuesten Standards.

   Mit zunehmender akzeptabler Sicherheit bleiben diese älteren, weniger sicheren Browserversionen und -anwendungen zurück.

   Um eine Verbindung mit sicheren Websites herstellen zu können, aktualisieren Sie Ihre Betriebssystem- und Browserversionen.

* **Ist TLS anfällig für Hacker?**

   Es wurden dokumentierte Angriffe auf TLS 1.0 mithilfe einer älteren Verschlüsselungsmethode durchgeführt, und die älteren Versionen sind anfälliger als TLS 1.2. Weitere Informationen finden Sie unter Angriffe auf TLS/SSL.

* **Warum deaktiviert Adobe die Unterstützung für TLS 1.0 und 1.1?**

   Adobe verfügt über Sicherheitsstandards, die die Deaktivierung der Unterstützung älterer Protokolle erfordern. Ein solcher Standard gewährleistet die Einhaltung der Payment Card Industry (PCI). PCI Adaption Server ist eine Reihe von Sicherheitsstandards, die von Unternehmen verlangen, Kreditkarteninformationen zu akzeptieren, zu verarbeiten, zu speichern oder zu übertragen, um eine sichere Umgebung zu gewährleisten.

   Aufgrund der PCI-Compliance ist die Verwendung von TLS 1.1 oder höher ab Mai 2018 erforderlich.

* **Warum schreibt die Adobe die Verwendung von TLS 1.2 vor, anstatt TLS 1.1 oder TLS 1.0 zuzulassen?**

   Die meisten Anforderungen für Adobe Apps und Webdienste stammen aus TLS 1.2-kompatiblen Benutzersystemen mit geringem Traffic von TLS 1.1-Systemen.

   Adobe wurde auf TLS 1.2 migriert, sodass die Apps und Webdienste sicherer aufgerufen werden können.

* **Welches Datum ist das letzte Datum, an dem ich eine ältere Version von TLS verwenden kann?**

   Adobe ermutigt Benutzer, die älteren Versionen schnell aufzugeben, um Sicherheitslücken zu vermeiden. Weitere Informationen erhalten Sie bei der Kundenunterstützung von Adobe oder Ihrem Kundenerfolgsmanager.

* **Welche Fehlermeldung wird angezeigt, wenn ich einen Browser verwende, der nicht für TLS 1.2 konfiguriert ist?**

   Das hängt vom verwendeten Browser ab. Alle in [Campaign-Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md) sind für die Verwendung von TLS 1.2 konfiguriert. Wenn Sie einen Browser oder eine Version verwenden, die nicht in der Liste aufgeführt ist, aktualisieren Sie Ihren Browser.

   Adobe steuert keine Fehlermeldungen, die von der SSL-Kommunikationsschicht generiert wurden. Der Browser generiert diese Nachrichten, bevor er eine Verbindung zu Adobe-Apps und -Diensten herstellt. Hier ist ein Beispiel für einen Fehler, der mit Internet Explorer 11 unter Windows 7 auftreten kann:

   ![](assets/do-not-translate/page-not-displayed.png)

   TLS 1.2 ist in Internet Explorer 11 standardmäßig aktiviert, kann aber bei ausgeschaltetem Internet Explorer aktiviert werden. Aktivieren Sie in diesem Fall TLS 1.2 über das Dialogfeld &quot;Erweiterte Einstellungen&quot;, anstatt andere Optionen zu verwenden. Es können auch andere Fehler wie die folgenden auftreten:

   * Verbindung zum Dienst kann nicht hergestellt werden
   * Service ist nicht verfügbar
   * Verbindungsfehler

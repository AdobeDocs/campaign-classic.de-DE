---
title: ' Gold Standard Version '
seo-title: ' Gold Standard Version '
description: ' Gold Standard Version '
seo-description: null
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 890153a5b30594a1cb90606db4be8fd1ec19267b
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 79%

---


#  Gold Standard Version {#gold-standard}

Als Gold Standard-Benutzer profitieren Sie automatisch von der Gold Standard-Aktualisierung mit der neuesten stabilen Version ohne Aktion.

Auch Kunden mit Präsenzen und Hybrid können von den Gold Standard Versionen profitieren.

Dies ist unsere Long-Term Support-Version. Wenn Sie von einem alten Build migrieren, empfehlen wir Ihnen, zuerst auf diese Version zu aktualisieren.

Diese Seite Liste Gold Standard-Versionen.

Weitere Informationen zum Gold Standard-Upgrade finden Sie in diesem [Artikel](https://helpx.adobe.com/de/campaign/kb/gold-standard.html).

## ![](assets/do-not-localize/limited.png) Gold Standard Version 10{#gs-10}

_7. Juli 2020_

Der Build 9032@efd8a94 beinhaltet die folgende Fehlerbehebung:

Es wurde ein Fehler behoben, der dazu führte, dass die Verfolgung nicht funktionierte, wenn die Signaturfunktion deaktiviert war oder wenn eine alte Marketing-Instanz mit einer kürzlich verwendeten Mitte verwendet wurde. (NEO-26411)

>[!CAUTION]
>
>Es wird empfohlen, die Clientkonsole mit der in dieser Version verfügbaren zu aktualisieren. Mehr dazu erfahren Sie auf [dieser Seite](../../installation/using/installing-the-client-console.md)

## ![](assets/do-not-localize/red_2.png) Gold Standard Version 9{#gs-9}

_22. Juni 2020_

Der Build 9032@800be2e beinhaltet die folgenden Fehlerbehebungen:

* Der iOS-HTTP2-Connector wurde verbessert (Updates von Drittanbietern und Fehlerverwaltung). (NEO-25904, NEO-25903, NEO-25799)

Die folgenden Fehlerkorrekturen beziehen sich auf den Sicherheitsmechanismus von Trackinglinks (siehe die [Checkliste für Sicherheit und Datenschutz](https://helpx.adobe.com/de/campaign/kb/acc-security.html#signature-mechanism)):

* Fehlerkorrektur – Tracking von &quot;Benachrichtigungsklicks&quot; (iOS- und Android-Push-Benachrichtigungen) funktioniert jetzt. (NEO-25965)
* Fehlerkorrektur – Tracking-URLs können geöffnet/geklickt werden, wenn bestimmte veraltete Outlook-Versionen verwendet werden. (NEO-25688)
* Fehlerkorrektur – Tracking von URLs mithilfe von Fragmenten in Personalisierungsparametern (Anker-Tags mit Rautenzeichen) funktioniert jetzt. (NEO-25774)
* Fehlerkorrektur – Es wurde ein Problem mit dem Anti-Phishing-Dienst behoben. (NEO-25283)
* Fehlerkorrektur – Es wurde ein Problem beim Tracking mit spezifischen benutzerdefinierten Tracking-Formeln behoben. (NEO-25277)

## ![](assets/do-not-localize/red_2.png) Gold Standard Version 8{#gs-8}

_29. April 2020_

Der Build 9032@3a9dc9c beinhaltet die folgenden Fehlerbehebungen:

* Verbesserte Sicherheit bei Tracking-Links in E-Mails. Dies ist für alle Kunden standardmäßig aktiviert. Es gibt eine zusätzliche, erweiterte Sicherheitsfunktion, die Sie aktivieren können, indem Sie sich an die Kundenunterstützung wenden. Weiterführende Informationen zu der Funktion und den Schritten zur Aktivierung für nicht gehostete Kunden finden Sie in der [Prüfliste für Sicherheit und Datenschutz](https://helpx.adobe.com/de/campaign/kb/acc-security.html#signature-mechanism).

>[!CAUTION]
>
>Wenn Sie Probleme mit Push-Benachrichtigungen unter Verwendung von Tracking-Links oder mit dem Versand mittels Anker-Tags haben, wird empfohlen, den neuen Signaturmechanismus für Trackinglinks zu deaktivieren. Das Verfahren wird auf dieser [Seite](https://helpx.adobe.com/de/campaign/kb/acc-security.html#signature-mechanism) beschrieben.

* Fehlerkorrektur – Die Anzeige von Bildern in Line-Sendungen wird jetzt nicht mehr verhindert. (NEO-23207)
* Fehlerkorrektur – Bei der Aktivität **Dateiübertragung** funktioniert jetzt die SFTP-Schlüssel-basierte Authentifizierung bei Debian 9. (NEO-23183)
* Fehlerkorrektur – Bei Push-Benachrichtigungen, die mit hoher Häufigkeit gesendet werden, tritt jetzt kein Problem mehr auf. (NEO-20516)
* Fehlerkorrektur – Die Verwaltung von Angebotsantworten führt jetzt nicht mehr zu Webserver-Abstürzen. (NEO-19482)
* Fehlerkorrektur – In der LibreOffice-Verwaltung ist jetzt das Exportieren von Berichten möglich. (NEO-20982)
* Fehlerkorrektur – Beim Aktualisieren verschiedener Workflows mit einer Umfrageaktivität tritt jetzt kein Fehler mehr auf.
* Die LibreOffice-Verwaltung wurde verbessert, um Fehler bei der E-Mail-Vorschau mit .odt-Dateien zu verhindern.
* Die Verwaltung der Apache-Verbindung wurde verbessert, um Latenzzeiten beim Web-Dienst zu vermeiden.
* Die Anzeige des Version-Tags (siebenstellig) im Menü **Versionsinformationen** wurde verbessert.
* Fehlerkorrektur – Es wurde ein Regressionsfehler bei der Listenverwaltung behoben, der die Publizierung von Angeboten verhinderte.
* Fehlerkorrektur – Es wurde ein Regressionsfehler behoben, der zum Absturz des Bereinigungs-Workflows führte.
* Fehlerkorrektur – Es wurde ein geringfügiger Regressionsfehler in den Bereinigungs-Workflow-Logs behoben.

## ![](assets/do-not-localize/green_2.png) Gold Standard Version 6{#gs-6}

_9. März 2020_

Der Build 9032@19f73c5 beinhaltet die folgende Fehlerbehebung:

* Fehlerkorrektur – Es gibt kein Problem mehr mit externen Konten, die FTP über SSL verwenden. (NEO-20498)

## ![](assets/do-not-localize/orange_2.png) Gold Standard Version 5{#gs-5}

_17. Dezember 2019_

Der Build 9032@d6b8062 beinhaltet die folgende Fehlerbehebung:

* Fehlerkorrektur – Tracking-Fehler bei folgenden Kommunikationskanälen tritt nicht mehr auf: Mobile (SMS, MMS), Push (iOS, Android) und soziale Netzwerke (Facebook, Twitter). (NEO-19595)

## ![](assets/do-not-localize/orange_2.png) Gold Standard Version 4{#gs-4}

_11. Dezember 2019_

Der Build 9032@bc4a935 beinhaltet die folgende Fehlerbehebung:

* Fehlerkorrektur – Keine Leistungsprobleme mehr beim Senden von Nachrichten mit einer MSSQL-Datenbank. (NEO-17558)

## ![](assets/do-not-localize/orange_2.png) Gold Standard Version 3{#gs-3}

_20. November 2019_

Der Build 9032@3468c7b beinhaltet die folgenden Fehlerbehebungen:

* Fehlerkorrektur – Die Anmeldung per IMS-Authentifizierung funktioniert nun. (NEO-17312)
* Fehlerkorrektur – Kumulative Berichte zu mehreren Sendungen werden nun richtig angezeigt. (NEO-18165)
* Fehlerkorrektur – Der Webserver wird nicht mehr blockiert oder zum Absturz gebracht.

## ![](assets/do-not-localize/red_2.png) Gold Standard Version 2{#gs-2}

_19. September 2019_

Der Build 9032@cee805c beinhaltet die folgenden Fehlerbehebungen:

* Fehlerkorrektur – Die Verwendung von CRM-Connector für Salesforce funktioniert nun problemlos. (NEO-17712)
* Fehlerkorrektur – Ein Indexfehler verursacht beim Senden von Transaktionsnachrichten keine Leistungsprobleme mehr.

## ![](assets/do-not-localize/red_2.png) Version 19.1.4 – Build 9032{#release-19-1-4-build-9032}

_13. August 2019_

Der ursprüngliche Build 19.1.4 beinhaltet die folgenden Fehlerbehebungen:

* Fehlerkorrektur – In der Planungsaktivität werden jetzt bei der Konfiguration des Assistenten keine unbeabsichtigten Fehlernachrichten mehr erzeugt. Update NEO-11662 wurde rückgängig gemacht. (NEO-17097)
* Regressionskorrektur – Jetzt tritt kein durch NEO-12727 verursachter Fehler mehr auf, bei dem Workflows angehalten wurden, wenn eine Testaktivität zweimal ausgeführt wird. (NEO-16835)
* Fehlerkorrektur – Jetzt wird kein fehlerhafter HTTP-Code mehr zurückgegeben (HTTP 200 OK statt HTTP 403 Forbidden), wenn ein ungültiges oder abgelaufenes Sitzungstoken in API-Aufrufen verwendet wird. (NEO-16826)
* Fehlerkorrektur – Der DKIM-Schlüssel wird jetzt in E-Mails eingebettet, sodass der Versand fehlerfrei funktioniert. (NEO-16804)
* Fehlerkorrektur – Die Workflow-Planung funktioniert jetzt wieder einwandfrei, sodass Workflows entsprechend ihrer Konfiguration ausgeführt werden. (NEO-16619, NEO-16426)

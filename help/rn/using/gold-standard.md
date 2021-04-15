---
solution: Campaign Classic
product: campaign
title: '[!DNL Gold Standard] In den Versionshinweisen'
description: Versionshinweise für Campaign Classic [!DNL Gold Standard]
feature: Übersicht
role: Business Practitioner
level: Beginner
exl-id: 9e3a11b1-3070-4d90-91d5-7c559bdd500e
translation-type: tm+mt
source-git-commit: 113a3535cd197f9b654fc1e50e20886e76ee886a
workflow-type: tm+mt
source-wordcount: '1058'
ht-degree: 94%

---

# [!DNL Gold Standard] In den Versionshinweisen{#gold-standard}

Diese Seite Liste [!DNL Gold Standard] Versionen. Weitere Informationen zur Kampagne [!DNL Gold Standard] [auf dieser Seite](gs-overview.md).

## ![](assets/do-not-localize/green_2.png) [!DNL Gold Standard] Version 11{#gs-11}

_14. April 2021_

Der Build 9032@d030c36 beinhaltet die folgende Fehlerbehebung:

* Korrektur der Client-Konsolenregression, die im IMS-Verbindungsbildschirm dauerhafte Fehlermeldungen verursachte. (NEO-34821)

**Es ist nur eine Konsolenaktualisierung obligatorisch. Eine Serveraktualisierung ist nicht erforderlich.**

_2. März 2021_

Build 9032@10c2709 umfasst die folgende Fehlerkorrektur:

* Korrektur einer Regression, die die Verwendung einiger Konsolenkomponenten wie der Datumsauswahl und der Bildverwaltung in Sendungen verhinderte. (NEO-31453, NEO-31454)

**Es ist nur eine Konsolenaktualisierung obligatorisch. Eine Serveraktualisierung ist nicht erforderlich.**

>[!NOTE]
>
> Stellen Sie eine Verbindung zu [Adobe Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html) her, um die neue Version herunterzuladen. Erfahren Sie [auf dieser Seite](../../installation/using/client-console-availability-for-windows.md), wie Sie die Konsolenaktualisierung allen Endbenutzern vorschlagen können.

_22. Dezember 2020_

>[!CAUTION]
>
> * Diese Version enthält ein neues Verbindungsprotokoll: Wenn Sie über Adobe Identity Service (IMS) eine Verbindung zu Campaign herstellen, ist sowohl für den Campaign-Server als auch für die Client-Konsole eine Aktualisierung zwingend erforderlich, um auch nach dem **30. Juni 2021** eine Verbindung zu Campaign herstellen zu können.
> * Diese Version enthält eine [Sicherheitskorrektur](https://helpx.adobe.com/de/security/products/campaign/apsb21-04.html): Die Aktualisierung ist zwingend erforderlich, um die Sicherheit Ihrer Umgebung zu erhöhen.
> * Wenn Sie die Experience Cloud-Triggers-Integration über die OAuth-Authentifizierung verwenden, müssen Sie wie [auf dieser Seite](../../integrations/using/configuring-adobe-io.md) beschrieben zu Adobe I/O wechseln. Der alte OAuth-Authentifizierungsmodus mit Campaign wird am **30. November 2021** eingestellt.

>
>
Weitere Informationen finden Sie in den [[!DNL Gold Standard] 11 Upgrade FAQ](https://helpx.adobe.com/de/campaign/kb/gold-standard-upgrade.html).

Der Build 9032@d3b452f umfasst die folgenden Verbesserungen und Fehlerbehebungen:

* Das Verbindungsprotokoll wurde aktualisiert, sodass es dem neuen IMS-Authentifizierungsmechanismus entspricht.

* Die Authentifizierung der Triggers-Integration, die ursprünglich auf der oAUTH-Authentifizierung basierte und für den Zugriff auf Pipeline eingerichtet wurde, wurde geändert und in Adobe I/O verschoben. [Weitere Infos](../../integrations/using/configuring-adobe-io.md)

* Nach dem [Ende der Unterstützung für das ältere Binärprotokoll von iOS-APNs](https://developer.apple.com/news/?id=c88acm2b) werden alle Instanzen, die dieses Protokoll verwenden, während des Postupgrades auf das HTTP/2-Protokoll aktualisiert.

* Fehlerkorrektur – Es wurde ein Sicherheitsproblem behoben, um den Schutz vor SSRF-Problemen (Server Side Request Forgery) zu verbessern. (NEO-27777)

* Fehlerkorrektur – Workflows schlagen beim Ausführen einer Aktivität vom Typ **Anreicherung** jetzt nicht mehr fehl. (NEO-17338)

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] Version 10{#gs-10}

_7. Juli 2020_

Build 9032@efd8a94 umfasst die folgende Fehlerkorrektur:

Fehlerkorrektur – Tracking funktioniert jetzt, wenn die Signaturfunktion deaktiviert ist. (NEO-26411)

>[!CAUTION]
>
>Es wird empfohlen, die Clientkonsole mit der in dieser Version verfügbaren zu aktualisieren. Mehr dazu erfahren Sie auf [dieser Seite](../../installation/using/installing-the-client-console.md).

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 9 Release{#gs-9}

_22. Juni 2020_

Build 9032@800be2e umfasst die folgenden Fehlerkorrekturen:

* Der iOS-HTTP2-Connector wurde verbessert (Updates von Drittanbietern und Fehlerverwaltung). (NEO-25904, NEO-25903, NEO-25799)

Die folgenden Fehlerkorrekturen beziehen sich auf den Sicherheitsmechanismus von Trackinglinks (weitere Informationen finden Sie in der [Checkliste für Sicherheit und Datenschutz](https://helpx.adobe.com/de/campaign/kb/acc-security.html#signature-mechanism)):

* Fehlerkorrektur – Tracking von &quot;Benachrichtigungsklicks&quot; (iOS- und Android-Push-Benachrichtigungen) funktioniert jetzt. (NEO-25965)
* Fehlerkorrektur – Tracking-URLs können geöffnet/geklickt werden, wenn bestimmte veraltete Outlook-Versionen verwendet werden. (NEO-25688)
* Fehlerkorrektur – Tracking von URLs mithilfe von Fragmenten in Personalisierungsparametern (Anker-Tags mit Rautenzeichen) funktioniert jetzt. (NEO-25774)
* Fehlerkorrektur – Es wurde ein Problem mit dem Anti-Phishing-Dienst behoben. (NEO-25283)
* Fehlerkorrektur – Es wurde ein Problem beim Tracking mit spezifischen benutzerdefinierten Tracking-Formeln behoben. (NEO-25277)





## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 8 Release{#gs-8}

_29. April 2020_

Build 9032@3a9dc9c umfasst die folgenden Fehlerkorrekturen:

* Verbesserte Sicherheit bei Tracking-Links in E-Mails. Dies ist für alle Kunden standardmäßig aktiviert. Es gibt eine zusätzliche, erweiterte Sicherheitsfunktion, die Sie aktivieren können, indem Sie sich an die Kundenunterstützung wenden. Weiterführende Informationen zu der Funktion und den Schritten zur Aktivierung für nicht gehostete Kunden finden Sie in der [Prüfliste für Sicherheit und Datenschutz](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism).

>[!CAUTION]
>
>Wenn Sie Probleme mit Push-Benachrichtigungen unter Verwendung von Tracking-Links oder mit dem Versand mittels Anker-Tags haben, wird empfohlen, den neuen Signaturmechanismus für Trackinglinks zu deaktivieren. Das Verfahren wird auf [dieser Seite](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism) beschrieben.

* Fehlerkorrektur – Die Anzeige von Bildern in Line-Sendungen wird jetzt nicht mehr verhindert. (NEO-23207)
* Fehlerkorrektur – Bei der Aktivität **Dateiübertragung** funktioniert jetzt die SFTP-Schlüssel-basierte Authentifizierung bei Debian 9. (NEO-23183)
* Fehlerkorrektur – Bei Push-Benachrichtigungen, die mit hoher Häufigkeit gesendet werden, tritt jetzt kein Problem mehr auf. (NEO-20516)
* Fehlerkorrektur – Die Verwaltung von Angebotsantworten führt jetzt nicht mehr zu Webserver-Abstürzen. (NEO-19482)
* Fehlerkorrektur – In der LibreOffice-Verwaltung ist jetzt das Exportieren von Berichten möglich. (NEO-20982)
* Fehlerkorrektur – Beim Aktualisieren verschiedener Workflows mit einer Umfrageaktivität tritt jetzt kein Fehler mehr auf.
* Die LibreOffice-Verwaltung wurde verbessert, um Fehler bei der E-Mail-Vorschau mit .odt-Dateien zu verhindern.
* Die Verwaltung der Apache-Verbindung wurde verbessert, um Latenzzeiten beim Web-Dienst zu vermeiden.
* Die Anzeige des Version-Tags (siebenstellig) im Menü **Versionsinformationen** wurde verbessert.
* Fehlerkorrektur – Es wurde ein Regressionsfehler bei der Listenverwaltung behoben, der die Veröffentlichung von Angeboten verhinderte.
* Fehlerkorrektur – Es wurde ein Regressionsfehler behoben, der zum Absturz des Bereinigungs-Workflows führte.
* Fehlerkorrektur – Es wurde ein geringfügiger Regressionsfehler in den Bereinigungs-Workflow-Logs behoben.

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 6 Release{#gs-6}

_9. März 2020_

Build 9032@19f73c5 umfasst die folgende Fehlerkorrektur:

* Fehlerkorrektur – Es gibt kein Problem mehr mit externen Konten, die FTP über SSL verwenden. (NEO-20498)

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 5 Release{#gs-5}

_17. Dezember 2019_

Build 9032@d6b8062 umfasst die folgende Fehlerkorrektur:

* Fehlerkorrektur – Tracking-Fehler bei folgenden Kommunikationskanälen tritt nicht mehr auf: Mobile (SMS, MMS), Push (iOS, Android) und soziale Netzwerke (Facebook, Twitter). (NEO-19595)

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 4 Release{#gs-4}

_11. Dezember 2019_

Build 9032@bc4a935 umfasst die folgende Fehlerkorrektur:

* Fehlerkorrektur – Keine Leistungsprobleme mehr beim Senden von Nachrichten mit einer MSSQL-Datenbank. (NEO-17558)

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 3 Release{#gs-3}

_20. November 2019_

Build 9032@3468c7b umfasst die folgenden Fehlerkorrekturen:

* Fehlerkorrektur – Die Anmeldung per IMS-Authentifizierung funktioniert nun. (NEO-17312)
* Fehlerkorrektur – Kumulative Berichte zu mehreren Sendungen werden nun richtig angezeigt. (NEO-18165)
* Fehlerkorrektur – Der Webserver wird nicht mehr blockiert oder zum Absturz gebracht.

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 2 Release{#gs-2}

_19. September 2019_

Build 9032@cee805c umfasst die folgenden Fehlerkorrekturen:

* Fehlerkorrektur – Die Verwendung von CRM-Connector für Salesforce funktioniert nun problemlos. (NEO-17712)
* Fehlerkorrektur – Ein Indexfehler verursacht beim Senden von Transaktionsnachrichten keine Leistungsprobleme mehr.

## ![](assets/do-not-localize/red_2.png) Version 19.1.4 – Build 9032{#release-19-1-4-build-9032}

_13. August 2019_

Der erste Build 19.1.4 enthält die folgenden Fehlerkorrekturen:

* Fehlerkorrektur – In der Planungsaktivität werden jetzt bei der Konfiguration des Assistenten keine unbeabsichtigten Fehlernachrichten mehr erzeugt. Update NEO-11662 wurde rückgängig gemacht. (NEO-17097)
* Regressionskorrektur – Jetzt tritt kein durch NEO-12727 verursachter Fehler mehr auf, bei dem Workflows angehalten wurden, wenn eine Testaktivität zweimal ausgeführt wird. (NEO-16835)
* Fehlerkorrektur – Jetzt wird kein fehlerhafter HTTP-Code mehr zurückgegeben (HTTP 200 OK statt HTTP 403 Forbidden), wenn ein ungültiges oder abgelaufenes Sitzungstoken in API-Aufrufen verwendet wird. (NEO-16826)
* Fehlerkorrektur – Der DKIM-Schlüssel wird jetzt in E-Mails eingebettet, sodass der Versand fehlerfrei funktioniert. (NEO-16804)
* Fehlerkorrektur – Die Workflow-Planung funktioniert jetzt wieder einwandfrei, sodass Workflows entsprechend ihrer Konfiguration ausgeführt werden. (NEO-16619, NEO-16426)

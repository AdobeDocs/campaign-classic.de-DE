---
solution: Campaign Classic
product: campaign
title: Häufig gestellte Fragen zum Build-Upgrade
description: Häufige Fragen im Zusammenhang mit Campaign-Build-Upgrades
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2023'
ht-degree: 100%

---


# Häufig gestellte Fragen zum Build-Upgrade{#build-upgrade-faq}

Adobe Campaign wird regelmäßig aktualisiert. Wenn Sie unsere veröffentlichten [Versionshinweise](../../rn/using/rn-overview.md) kennen, wissen Sie wahrscheinlich, dass jedes Jahr im Schnitt zwei bis drei kleinere Versionen mit neuen Funktionen, Verbesserungen und Korrekturen herausgebracht werden. Zusätzlich veröffentlichen wir regelmäßig Builds, die ausschließlich Fehlerkorrekturen enthalten. Durch diese regelmäßige Bereitstellung von Updates soll sichergestellt werden, dass Sie stets die beste und neueste Version nutzen, sodass Ihre Umgebung sicher ist und Ihre Zufriedenheit bei der Nutzung unserer Produkte laufend steigt.

Deshalb erachten wir es als entscheidend, dass unsere Kunden stets die neueste Version von Adobe Campaign verwenden. Dadurch sind wir beim Auftreten von Problemen in der Lage, Ihnen effizient zu helfen. Denn es ist normalerweise zeitaufwändiger, einen Fehler in einem alten Build zu identifizieren, zu reproduzieren und zu beheben. Außerdem besteht die Möglichkeit, dass dieser Fehler im aktuellen Build bereits behoben wurde.

Aus diesem Grund haben wir das [Gold Standard](https://helpx.adobe.com/de/campaign/kb/gold-standard.html)-Programm ins Leben gerufen, durch das wir gemeinsam mit unseren Kunden deren Arbeitsumgebungen proaktiv und regelmäßig aktualisieren können. 

## Was ist ein Build-Upgrade?

Bei einem Build-Upgrade wird die Adobe Campaign Classic-Software auf die aktuelle, sichere Build-Nummer aktualisiert, wobei die Versionsnummer unverändert bleibt. Beispiel: Campaign Classic v7 Build 9026 auf Campaign v7 Build 9032.

Weitere Informationen finden Sie in [diesem Abschnitt](../../rn/using/rn-overview.md).

## Was ist die aktuelle Version von Adobe Campaign Classic?

Die aktuelle Version von Campaign Classic, einschließlich neuer Funktionen und der Dokumentation, wird in den [Versionshinweisen](../../rn/using/latest-release.md) näher beschrieben.

## Wie finde ich heraus, welche Version ich verwende?

Rufen Sie in der Client-Konsole von Adobe Campaign **[!UICONTROL Hilfe > Versionsinformationen...]** auf. Das Feld **[!UICONTROL Versionsinformationen]** enthält Details zur Version und zum Build der Client-Konsole und des Servers.

Weitere Informationen finden Sie in [diesem Abschnitt](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Was bedeutet der Build-Status?

Ab Campaign Classic 19.2 wird jedem Build ein Status zugeordnet.

Weitere Informationen finden Sie in [diesem Abschnitt](../../rn/using/rn-overview.md).

## Ist ein Upgrade des Builds dasselbe wie das Upgrade einer Version?

Nein. Ein Build-Upgrade ist eine schrittweise Aktualisierung innerhalb einer Version. Ein Upgrade einer Version ist hingegen der Wechsel von einer Version zu einer anderen. Build-Upgrades sind unkompliziert, da sie normalerweise keine Änderungen an der Architektur, den technischen Gegebenheiten oder dem Datenmodell erfordern.

Upgrades von Versionen dagegen bedeuten normalerweise erhebliche technische Änderungen. Je nach Konfigurationsumfang erfordern sie unter Umständen umfassende Änderungen an der Konfiguration und/oder die teilweise erneute Implementierung.

Bezogen auf die Serverinformationen im Screenshot aus dem vorherigen Abschnitt würde dies Folgendes bedeuten:

* Ein Build-Upgrade würde bedeuten, dass Sie von Build 6880 zu einem Build höher als 6880 wechseln. Beispiel: von v6.1.1 Build 8222 zu v6.1.1 Build 8666.

* Durch das Upgrade der Version würden Sie von Version 6.0.2 zu einer Version höher als 6.0.2 wechseln. Beispiel: von v6.0.1 Build 2222 zu v6.1.1 Build 8666

## Sollte ich meine Daten vor diesen Aktualisierungen sichern?

Adobe erstellt vor etwaigen Änderungen ein Backup Ihres Systems. Wenn sich jedoch wichtige Projekte außerhalb Ihres Produktionssystems befinden (Entwicklungs- oder Staging-Server), wird DRINGEND EMPFOHLEN, diese vor dem Upgrade als Package zu exportieren.

In diesem [Anleitungsvideo](https://helpx.adobe.com/de/campaign/classic/how-to/generate-packages-in-acv6.html) erhalten Sie weitere Informationen.

## Wann werden die Upgrades vorgenommen?

Kunden wird ein Zeitraum angeboten, innerhalb dessen sie einen Termin auswählen können. Änderungen am Produktionssystem werden nur an Werktagen vorgenommen.

Build-Upgrades können von Montag bis Donnerstag durchgeführt werden. Freitags werden ausschließlich Nicht-Produktionsinstanzen aktualisiert. 

## Wie lange dauert das Build-Upgrade?

Die Dauer eines Build-Upgrades hängt von mehreren Faktoren ab:

* Die Größe der Datenbank, die gesichert oder wiederhergestellt werden muss. (Größere Datenbanken erfordern mehr Zeit für das Upgrade.)
* Die Größe der Umgebungen. (Viele unserer Kunden haben mehrere unterschiedliche Server, von denen jeder spezifische Funktionen ausführt; größere Umgebungen benötigen mehr Zeit für das Upgrade.)
* Die Komplexität des Systems. (Manche Systeme haben mehrere Dienste und Verbindungen, die überprüft werden müssen und auch die Überprüfung der Systemstabilität und -leistung erfordern.)

Das Build-Upgrade ist ein zweistufiger Vorgang:

1. Vorbereitung des Systems auf das Upgrade: Unter Berücksichtigung der Gegebenheiten Ihrer Arbeitsumgebung wird in einer Nicht-Produktionsumgebung ein vollständiges Upgrade durchgeführt. Sobald die aktualisierte Umgebung von einem technischen und funktionellen Standpunkt aus grünes Licht erhalten hat, erfolgt der zweite Schritt. Diese Phase kann abhängig von den zuvor genannten Faktoren von einigen Tagen bis zu mehreren Wochen dauern. 

1. Das Upgrade selbst: Die Produktionsumgebung wird aktualisiert. Diese Phase dauert normalerweise einige Stunden. Für sehr komplexe Umgebungen muss mit einer längeren Ausfallzeit gerechnet werden. Zur Absicherung gegenüber Fehlern im Prozess wird eine Rollback-Strategie bestimmt, die im Ernstfall angewendet werden kann.

Weitere Informationen finden Sie in [diesem Dokument](https://helpx.adobe.com/de/campaign/kb/acc-build-upgrade.html).

## Welche Ressourcen sind für das Build-Upgrade erforderlich?

Für das Build-Upgrade sind die folgenden Ressourcen erforderlich:

* Adobe-Architekt: Im Fall von gehosteten oder Cloud Messaging-/Hybridarchitekturen muss sich der Architekt mit der Adobe-Kundenunterstützung arrangieren.
* Projekt-Manager: Gehostet: Das Hosting-Team arbeitet mit der Adobe-Kundenunterstützung und dem Kunden zusammen, um für alle Instanzen den Zeitrahmen festzulegen.
* Adobe Campaign-Administrator – Gehostet: Das Hosting-Team nimmt das Upgrade vor.
* Benutzer/Marketing-Benutzer von Adobe Campaign: Der Benutzer führt Tests auf Entwicklungs-, Test- und Produktionsinstanzen durch.

## Wie bereite ich das Build-Upgrade vor?

Exportieren Sie in Ihren Entwicklungs- und Staging-Systemen alle Projekte, die wichtig sind und erhalten werden müssen. Weitere Informationen dazu finden Sie in diesem [Video](https://helpx.adobe.com/de/campaign/classic/how-to/generate-packages-in-acv6.html).

Frischen Sie Ihr Wissen über die wichtigsten Pfad-Workflows und Sendungen auf, die in Ihren Runbooks (oder durch Ihr Beraterteam/Ihren Partner) entwickelt wurden, indem Sie die Dokumentation lesen, die Ihrem Team nach der Implementierung bereitgestellt wird.

Ermitteln Sie Zeiten mit geringem Datenvolumen oder Traffic, die sich ideal für Wartungsfenster eignen, da sie die Geschäftstätigkeit am wenigsten beeinträchtigen.

Gehen Sie unsere unten aufgeführte [Upgrade-Checkliste](#check-list) und Ihre Testpläne durch und stellen Sie sicher, dass Ressourcen, die diese Tests durchführen können, innerhalb von 24 bis 48 Stunden ab dem Ende des Upgrades verfügbar sind.

Weitere Informationen finden Sie in [diesem Dokument](https://helpx.adobe.com/de/campaign/kb/acc-build-upgrade.html).

## Können Build-Upgrades nachts oder außerhalb der Geschäftszeiten durchgeführt werden?

Upgrades können außerhalb der Geschäftszeiten durchgeführt werden. Es ist generell empfehlenswert, die Umgebung außerhalb der Geschäftszeiten zu aktualisieren, wenn keine Benutzer mit der Instanz verbunden sind.

## Welche Kosten sind mit einem Build-Upgrade verbunden?

Für gehostete Kunden fallen für die Installation des Build-Upgrades keine Kosten an. Wenn am System benutzerdefinierte Entwicklungen vorgenommen werden, muss der Kunde Ressourcen bereitstellen, die diese Entwicklungen nach dem Upgrade testen und nötigenfalls etwaige Probleme beheben können. 

## Kann während des Upgrade-Prozesses auf die Instanz zugegriffen werden?

Nein. Der Server wird während des Upgrades deaktiviert, um die Datenintegrität zu schützen. Danach wird er neu gestartet und alle Dienste werden fortgesetzt.

## Werden während des Upgrades weiterhin E-Mails von Message Center gesendet?

Wenn Message Center (RT) aktualisiert wird, werden keine E-Mails von dieser Instanz gesendet. Hinweis: Alle Prozesse, die angehalten werden, wenn das Campaign-System abgeschaltet wird, werden automatisch wieder fortgesetzt, wenn das System wieder aktiviert wird. Hierzu zählen auch aktive oder geplante Sendungen, das Tracking und die Berechnung von Metriken für zuvor durchgeführte Sendungen.

## Werden Workflows und Sendungen weiterhin durchgeführt?

Nein. Während des Build-Upgrades werden sowohl Workflows als auch Mail-Dienste angehalten. Das bedeutet, dass weder Workflows noch Sendungen durchgeführt werden. Diese werden fortgesetzt, sobald das System wieder gestartet wurde. Adobe empfiehlt jedoch, dass alle kritischen Pfad-Workflows nach dem Upgrade überprüft werden, um sicherzustellen, dass sie aktiv und fehlerfrei sind.

## Funktionieren meine Tracking-Links während des Upgrades?

Tracking-Links funktionieren während des Upgrades. Während des Upgrades können zwar keine neuen E-Mails gesendet werden, aber Tracking-Links in bereits gesendeten E-Mails funktionieren.

## Muss ich während des Build-Upgrades verfügbar sein?

Ja. Kunden sollten Adobe während oder unmittelbar nach dem Upgrade der Produktionsinstanz eine Kontaktperson zur Verfügung stellen.  Adobe kontaktiert diese Person per E-Mail, außer es wurden andere Vereinbarungen getroffen. Dies ermöglicht eine reibungslose Aktualisierung und eine unmittelbare Überprüfung kritischer Aufgaben. Adobe kontaktiert den Kunden, sobald das Build-Upgrade abgeschlossen ist. 

## Muss ich die Client-Konsole aktualisieren?

Ja. Die Client-Konsole muss denselben oder einen höheren Build haben als die Server-Instanz. Nach dem Upgrade sollten Sie von Ihrer Client-Konsole aufgefordert werden, eine Aktualisierung auf die aktuelle Build-Version durchzuführen, damit sie zum Server-Build passt.

## Wie sieht der Rollback-Plan aus? Werden Backups meiner Daten aufbewahrt?

Der Rollback-Plan sieht vor, das System mit der zuletzt verfügbaren Sicherungskopie wiederherzustellen. Sicherungskopien werden für Rechenzentrumskunden sieben Tage lang und für auf Amazon Web Services (AWS) gehostete Kunden 14 Tage lang aufbewahrt. 

## Wie lange dauert das Rollback?

Das hängt von der Größe des Datenbank-Backups ab. Im Schnitt sind dafür 4 Stunden zu veranschlagen.

## Welche Tests werden nach dem Upgrade auf meinem System durchgeführt?

Näheres hierzu finden Sie in der weiter unten aufgeführten [Checkliste für Build-Upgrades](#check-list).

## Welche Tests muss ich nach meinem Upgrade durchführen?

Die Entwicklungs- und Staging-Umgebungen werden entweder nacheinander oder gemeinsam aktualisiert. Vor dem Upgrade der Produktionsinstanz muss jedoch deren Korrektheit bestätigt werden. Dadurch können Kunden ausführliche Tests durchführen, bevor etwaige Änderungen an die Produktionsumgebung weitergegeben werden.

Beachten Sie die [Checkliste für Build-Upgrades](#check-list) weiter unten. Kunden sollten solcherlei sowie zusätzliche, für ihre Umgebung benötigte Tests durchführen.

## Wie oft muss ich ein Build-Upgrade durchführen?

Um eine optimale Leistung, Verfügbarkeit und Sicherheit des Systems zu gewährleisten, sorgt Adobe gemeinsam mit seinen Kunden dafür, dass das System zumindest einmal jährlich aktualisiert wird.

## Muss das System bei einem Build-Upgrade heruntergefahren werden?

Ja. Der Server wird während des Upgrades deaktiviert, um die Datenintegrität zu schützen. Danach wird er neu gestartet und alle Dienste werden fortgesetzt.

## Wen sollte ich kontaktieren, wenn ich ein Ticket wegen einem Build-Upgrade erstellen möchte?

Wenn nach einem Build-Upgrade Probleme auftreten, wenden Sie sich an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Die Adobe-Kundenunterstützung plant den Vorgang und erstellt das Ticket zum Build-Upgrade.

Weitere Informationen finden Sie in den [Hilfe- und Support-Optionen für Campaign Classic](https://helpx.adobe.com/de/campaign/kb/ac-support.html#acc-support-req).

## Checkliste für Build-Upgrades {#check-list}

### Checkliste für den Cloud Messaging Server nach dem Upgrade:

1. Führen Sie einen Testversand durch.
   1. Überprüfen Sie, ob die Versand-Logs und der damit verbundene Workflow korrekt ist.
   1. Überprüfen Sie, ob die Tracking-Logs aktualisiert werden.
   1. Überprüfen Sie die Mirror-Seite und die Tracking-Links.
1. Überprüfen Sie, ob alle technischen Workflows den Status &quot;Gestartet&quot; aufweisen.
1. Stellen Sie sicher, dass auch alle Prozesse aktiv sind.

### Checkliste für den Marketing-Server nach dem Upgrade:

* Können Sie sic h beim Server anmelden? Stellen Sie sicher, dass die Client-Konsole fehlerfrei funktioniert bzw. keine Fehlerwarnungen angezeigt werden.
* Achten Sie darauf, dass die Konsole und der Build nach dem Upgrade dieselbe Version aufweisen.
* Haben Sie Webanwendungen, die Daten zur Campaign-Datenbank hinzufügen? Wenn ja, führen Sie sie aus und überprüfen Sie, ob neue Datensätze per API hinzugefügt werden können.
* Können Sie eine Test-E-Mail versenden? Erstellen Sie einen neuen Versand mit einer bekannten Vorlage, senden Sie die Nachricht an einen Testempfänger, überprüfen Sie die Personalisierung und stellen Sie sicher, dass der Abmelde-Link und die Mirror-Seite funktionieren.
* Werden alle Ihre kritischen Pfad-Workflows ausgeführt? Überprüfen Sie Workflows, öffnen Sie das Workflow-Protokoll und stellen Sie sicher, dass keine Fehler vorliegen.
* Sind alle Ordner vorhanden, sichtbar und aufrufbar? Durchsuchen Sie unterschiedliche Ordner und stellen Sie sicher,
dass alle Inhalte vorhanden sind und angezeigt werden.
* Werden Ihre Sendungen mit der richtigen Zeitzone zugestellt?

   * Überprüfen Sie das Erstellungsdatum und das Änderungsdatum einschließlich Zeitstempel und Zeitzone.
   * Überprüfen Sie, ob die geplante Ausführung eines Workflows zum angegebenen Zeitpunkt funktioniert.
   * Rufen Sie die Liste der Workflows ab, die den Status AUSGESETZT und FEHLGESCHLAGEN aufweisen. Starten Sie diese und beobachten Sie sie.
   * Führen Sie für ein Szenario einen A/B-Test durch.
   * Testen Sie Push-Benachrichtigungen und ihre Tracking-Funktionen für Deeplinks.
   * Testen Sie das Versenden von SMS-Nachrichten.
   * Wenn eine externe FDA-Lösung verbunden ist, testen Sie, ob die Daten in beide Richtungen gesendet werden.
   * Wenn Sie Integrationen (wie zwischen Adobe Campaign und Adobe Experience Manager oder Adobe Campaign und Adobe Analytics) nutzen, testen Sie, ob diese funktionieren wie bisher.

**Siehe auch**

* [Durchführen eines Build-Upgrades](../../production/using/build-upgrade.md)
* [Versionshinweise zu Campaign Classic ](../../rn/using/rn-overview.md)
* [Hilfe- und Support-Optionen für Campaign Classic](https://helpx.adobe.com/de/campaign/kb/ac-support.html#acc-support-req)
* [Gold Standard-Programm](https://helpx.adobe.com/de/campaign/kb/gold-standard.html)
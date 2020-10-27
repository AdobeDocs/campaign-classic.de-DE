---
title: Häufig gestellte Fragen zur Aktualisierung
description: Häufige Fragen im Zusammenhang mit Kampagnen-Build-Upgrades
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
translation-type: tm+mt
source-git-commit: cb96a238f4c8e413377ce6102b065b91badfe6db
workflow-type: tm+mt
source-wordcount: '2023'
ht-degree: 8%

---


# Häufig gestellte Fragen zur Aktualisierung erstellen {#build-upgrade-faq}

Adobe Campaign wird regelmäßig aktualisiert. If you are familiar with our published [Release Notes](../../rn/using/rn-overview.md), you are probably aware of the fact that on the average 2/3 minor versions packed with new features, improvements and fixes are released every year. Darüber hinaus veröffentlichen wir regelmäßig Builds nur mit kumulativen Fehlerbehebungen. Diese regelmäßige Aktualisierung zielt darauf ab, das Beste und Beste in Ihren Händen zu halten, Ihre Umgebung vollkommen sicher zu halten und Ihre Erfahrung mit unserem Produkt zu verbessern.

Es ist äußerst wichtig, dass unsere Kunden die neueste Version von Adobe Campaign ausführen. Es ermöglicht auch Adobe, bei Problemen viel effizienter zu helfen - die Identifizierung, Reproduktion und Behebung eines Problems in einem alten Build dauert normalerweise länger, ganz zu schweigen davon, dass einige Probleme, die Sie möglicherweise bereits in einem kürzlich erstellten Build hatten, sehr wohl behoben wurden.

Deshalb haben wir mit dem [Gold Standard](https://helpx.adobe.com/de/campaign/kb/gold-standard.html) Programm begonnen, mit unseren Kunden zusammenzuarbeiten, um ihre Umgebung proaktiv und regelmäßig zu aktualisieren.

## Was ist ein Build-Upgrade?

Bei einem Build-Upgrade wird die Adobe Campaign Classic-Software auf die neueste sichere Buildnummer aktualisiert, bleibt jedoch im gleichen Hauptaufbau/Nebenaufbau-Level. Beispiel: Campaign Classic v7 Build 9026 auf Campaign v7 Build 9032.

Weiterführende Informationen finden Sie [in diesem Abschnitt](../../rn/using/rn-overview.md).

## Was ist die neueste Version von Adobe Campaign Classic?

Die neueste Campaign Classic-Version, einschließlich neuer Funktionen und Dokumentation, ist in den neuesten [Versionshinweisen](../../rn/using/latest-release.md)ausführlich beschrieben.

## Woher weiß ich, welche Version ich verwende?

Überprüfen Sie Ihre Version unter **[!UICONTROL Hilfe > Info...]** in der Adobe Campaign Client-Konsole. Das Feld **[!UICONTROL Info]** enthält detaillierte Informationen zur Version und zum Build, die Sie sowohl für die Konsole als auch für den Server ausführen.

Weiterführende Informationen finden Sie [in diesem Abschnitt](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Was bedeutet der Build-Status?

Ab Campaign Classic 19.2 wird jedem Build ein Status zugeordnet.

Weiterführende Informationen finden Sie [in diesem Abschnitt](../../rn/using/rn-overview.md).

## Entspricht ein Build-Upgrade dem Upgrade einer Version?

Nein. Ein Build-Upgrade ist eine inkrementelle Aktualisierung innerhalb einer gegebenen Hauptversion, während ein Versionsupgrade eine Änderung von einer Hauptversion zu einer anderen darstellt. Build-Upgrades sind einfach, da sie in der Regel keine größeren Änderungen an Architekturen, technischen oder Datenmodellen beinhalten.

Versionsaktualisierungen werden dagegen in der Regel mit erheblichen technischen Änderungen verbunden und erfordern je nach der Konfigurationstiefe für einen bestimmten Kunden möglicherweise erhebliche Konfigurationsänderungen und/oder eine teilweise Neuimplementierung.

Verwenden Sie zum Beispiel die Serverinformationen aus dem Screenshot im vorherigen Abschnitt:

* Ein Build-Upgrade würde den Übergang von Build 6880 zu jedem Build größer als 6880 beinhalten. Beispiel: Version 6.1.1 Build 8222 bis Version 6.1.1 Build 8666

* Bei einem Upgrade der Version würde von Version 6.0.2 auf eine Version über 6.0.2 umgestellt.  Beispiel: v6.0.1 Build 2222 bis v6.1.1 Build 8666

## Sollte ich meine Daten vor diesen Aktualisierungen sichern?

Adobe wird vor jeder Änderung eine Systemsicherung durchführen. Wenn Ihr Nicht-Produktionssystem (Entwicklungs- oder Staging-Server) jedoch eine wichtige Anpassungsarbeit leistet, EMPFIEHLT ES SICH, dass Sie diese Arbeit vor jeder Aktualisierung als Paket exportieren.

Weitere Informationen finden Sie [in diesem Video](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html).

## Wann werden die Upgrades durchgeführt?

Den Kunden wird ein Datumsbereich zur Auswahl angeboten. Änderungen am Produktionssystem werden nicht an Feiertagen durchgeführt.

Build-Upgrades können von Montag bis Donnerstag durchgeführt werden, und Freitage werden nur für Nicht-Produktionsinstanzen verwendet.

## Wie lange dauert die Build-Aktualisierung?

Die für die Durchführung einer Buildaktualisierung erforderliche Zeit hängt von verschiedenen Faktoren ab:

* Die Größe der zu sichernden oder wiederherzustellenden Datenbank (größere Datenbanken benötigen mehr Zeit zum Aktualisieren)
* Die Größe der Umgebung (viele unserer Kunden verfügen über mehrere verschiedene Server, auf denen jeder bestimmte Funktionen handhat, wobei größere Umgebung mehr Zeit zum Upgrade benötigen)
* Die Komplexität des Systems (einige Systeme verfügen über abhängigere Dienste und Verbindungen, die überprüft werden müssen, was eine Überprüfung der Stabilität und Leistung dieser Systeme erfordert)

Die Build-Aktualisierung erfolgt in zwei Schritten:

1. Vorbereiten des Systems für die Aktualisierung - Unter Berücksichtigung der Besonderheiten Ihrer Umgebung führt diese Phase im Wesentlichen zu einer vollqualifizierten Aktualisierung auf einer Nicht-Produktionsversion-Umgebung. Sobald die aktualisierte Umgebung aus technischer und funktioneller Sicht neu beleuchtet wurde, kann Phase 2 stattfinden. Diese erste Phase kann je nach den oben genannten Faktoren einige Tage bis ein paar Wochen dauern.

1. Die Aktualisierung selbst - Die Umgebung der Produktion wird aktualisiert. Diese Phase wird in der Regel nach einigen Stunden durchgeführt. Für sehr komplexe Umgebung sollte eine längere Ausfallzeit erwartet werden. Im Ereignis, dass etwas schiefgeht, wird eine Rollback-Strategie definiert und kann ausgeführt werden.

For more information, [refer to this document](https://helpx.adobe.com/de/campaign/kb/acc-build-upgrade.html).

## Welche Ressourcen sind für die Build-Aktualisierung erforderlich?

Für die Build-Aktualisierung sind die folgenden Ressourcen erforderlch:

* Architektur der Adobe - Bei gehosteten oder Cloud Messaging-/Hybrid-Architekturen muss sich der Architekt mit der Kundenunterstützung abstimmen.
* Projektmanager - Hosted: das Hosting-Team wird mit dem Kundendienst und dem Kunden zusammenarbeiten, um die Aktualisierungszeitschiene für alle Instanzen zu koordinieren.
* Adobe Campaign-Administrator - Hosted: das Hosting-Team die Aktualisierung durchführt.
* Adobe Campaign operator\marketing user - Der Operator führt Tests für Entwicklungs-, Test- und Produktionsinstanzen durch.

## Wie kann ich mich auf die Build-Aktualisierung vorbereiten?

Exportieren Sie in Ihren Entwicklungs- und Staging-Systemen alle wichtigen und zu erhaltenden Arbeiten. Für weitere Informationen [sehen Sie sich bitte dieses Video](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html)an.

Aktualisieren Sie Ihr Wissen über den kritischen Pfad, den Workflows und die Versand in Ihren Ausführungsbüchern (oder durch Ihr Beratungsteam/Ihren Partner) entwickelt haben, indem Sie die Dokumentation überprüfen, die Ihrem Team am Ende Ihrer Implementierung zur Verfügung gestellt wird.

Identifizieren Sie niedrige oder niedrige Traffic-Zeiten, die sich ideal für Wartungsfenster eignen, da sie die geringsten geschäftlichen Auswirkungen haben.

Überprüfen Sie unsere [Checkliste für die Aktualisierung unten](#check-list) und Ihre Testpläne und stellen Sie sicher, dass die Ressourcen, die diese Tests durchführen können, innerhalb von 24-48 Stunden verfügbar sind. nach Abschluss der Aktualisierung.

For more information, [refer to this document](https://helpx.adobe.com/de/campaign/kb/acc-build-upgrade.html).

## Kann man nachts oder außerhalb der Geschäftszeiten Upgrades durchführen?

Upgrades können außerhalb der Arbeitszeit durchgeführt werden. Es wird immer empfohlen, die Umgebung während der Geschäftszeiten zu aktualisieren, wenn keine Geschäftsbenutzer mit der Instanz verbunden sind.

## Welche Kosten sind mit einer Build-Aktualisierung verbunden?

Die Installation des Build-Upgrades für gehostete Kunden ist kostenfrei. Bei kundenspezifischen Entwicklungen im System muss der Kunde die Ressourcen ermitteln, die zum Testen dieser Entwicklungen nach der Aktualisierung erforderlich sind, und alle Probleme, die bei diesen benutzerspezifischen Entwicklungen auftreten, beheben.

## Kann während des Aktualisierungsprozesses auf die Instanz zugegriffen werden?

Nein. Der Server wird während der Aktualisierung heruntergefahren, um sicherzustellen, dass die Datenintegrität erhalten bleibt, während das Produkt aktualisiert wird. Nach Abschluss wird er neu gestartet und alle Dienste werden fortgesetzt.

## Werden die E-Mails während des Aktualisierungsprozesses weiterhin vom Message Center gesendet?

Wenn die Aktualisierung für Message Center (RT) erfolgt, werden keine E-Mails von der Instanz gesendet. Beachten Sie, dass alle Prozesse, die beim Herunterfahren eines Kampagne-Systems gestoppt werden, beim Neustart des Systems automatisch fortgesetzt werden. Dazu gehören aktive oder geplante Versand, Verfolgungsmethoden und Metrikberechnungen für zuvor gesendete Versand.

## Werden die Workflows und Sendungen weiterhin durchgeführt?

Nein. Während der Buildaktualisierung werden Workflow- und E-Mail-Dienste gestoppt. Das bedeutet, dass Workflows nicht ausgeführt werden und keine Versand gesendet werden. Sie werden nach dem Neustart des Systems fortgesetzt. Adobe empfiehlt jedoch dringend, dass alle kritischen Pfade nach einer Aktualisierung überprüft Workflows, um sicherzustellen, dass sie ausgeführt und gesund sind.

## Funktionieren meine Tracking-Links während der Aktualisierung?

Nachverfolgungslinks funktionieren während der Aktualisierung. Während der Aktualisierung können keine neuen E-Mails gesendet werden, aber Tracking-Links, die in bereits gesendeten E-Mails enthalten sind, funktionieren.

## Muss ich während der Build-Aktualisierung verfügbar sein?

Ja. Kunden sollten der Adobe einen Ansprechpartner während oder unmittelbar nach der Aktualisierung ihrer Produktionsinstanz zur Verfügung stellen.  Adobe wird diese Person per E-Mail kontaktieren, es sei denn, es werden andere Vorkehrungen getroffen. Dadurch wird eine reibungslose Transition und sofortige Validierung kritischer Aufgaben gewährleistet. Die Adobe wird den Kunden kontaktieren, sobald die Build-Aktualisierung abgeschlossen ist, um eine Bestätigung zu erhalten.

## Muss ich die Client-Konsole aktualisieren?

Ja. Die Client-Konsole muss sich auf demselben Build oder neueren Build wie die Serverinstanz befinden. Nachdem die Aktualisierung abgeschlossen ist, sollten Sie von Ihrer Client-Konsole aufgefordert werden, auf den neuesten Build zu aktualisieren, um sicherzustellen, dass dieser weiterhin mit dem Serveraufbau abgestimmt ist.

## Wie sieht der Rollback-Plan aus? Werden Sicherungskopien meiner Daten gespeichert?

Der Rollback-Plan besteht darin, das System mit der neuesten verfügbaren Sicherung wiederherzustellen. Backups werden für Kunden im Rechenzentrum 7 Tage und für Kunden 14 Tage über den Amazon Web Service (AWS) gespeichert.

## Wie lange dauert das Rollback?

Es hängt von der Größe der Datenbanksicherung ab. Die durchschnittliche Dauer bis zum Abschluss beträgt 4 Stunden.

## Welche Testtypen werden nach der Aktualisierung auf meinem System durchgeführt?

Lesen Sie die Checkliste für die [Build-Aktualisierung weiter unten](#check-list).

## Welche Art von Test muss ich nach der Aktualisierung durchführen?

Entwicklungs- und Stage-Umgebung werden entweder nacheinander oder zusammen aktualisiert, es ist jedoch eine Anmeldung erforderlich, bevor die Produktionsinstanz aktualisiert wird. Dadurch kann jeder Kunde gründliche Tests durchführen, bevor er Änderungen an der Produktion abzeichnet.

Siehe [Checkliste für die Aktualisierung der Liste weiter unten](#check-list). Die Kunden sollten ähnliche Tests durchführen, wie andere, die sie für die Umgebung benötigen.

## Wie oft muss ich eine Build-Aktualisierung durchführen?

Um eine optimale Systemleistung, -verfügbarkeit und -sicherheit zu gewährleisten, arbeitet Adobe mit Kunden zusammen, um sicherzustellen, dass die Systeme mindestens einmal jährlich aktualisiert werden.

## Wird es für eine Buildaktualisierung einen Shutdown geben?

Ja. Der Server wird während der Aktualisierung heruntergefahren, um sicherzustellen, dass die Datenintegrität erhalten bleibt, während das Produkt aktualisiert wird. Nach Abschluss wird er neu gestartet und alle Dienste werden fortgesetzt.

## An wen wende ich mich, um das Upgrade-Ticket für Build zu öffnen?

Wenden Sie sich an den Kundendienst der [Adobe, wenn Probleme nach einem Build-Upgrade auftreten](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Der Kundendienst plant die Builddaten und öffnet Tickets zum Erstellen von Upgrades.

Weitere Informationen finden Sie in den [Hilfe- und Unterstützungsoptionen für Campaign Classic](https://helpx.adobe.com/campaign/kb/ac-support.html#acc-support-req)

## Checkliste für die Aktualisierung erstellen {#check-list}

### Checkliste für den Cloud Messaging-Server nach der Aktualisierung

1. Senden eines Test-Versands
   1. Validieren der Versandlogs und des zugehörigen Workflows
   1. Überprüfen, ob die Trackinglogs aktualisiert wurden
   1. Mirrorseiten- und Verfolgungslinks überprüfen
1. Vergewissern Sie sich, dass alle Technischen Workflows gestartet sind
1. Überprüfen Sie, ob auch alle Prozesse aktiv sind

### Checkliste für die Aktualisierung des Marketingservers nach der Aktualisierung

* Können Sie sich beim Server anmelden? Überprüfen Sie, ob die Kampagne Client Console ohne Fehler-/Warnmeldungen funktioniert.
* Achten Sie darauf, nach der Aktualisierung dieselbe Konsolenversion wie die Buildversion zu verwenden.
* Haben Sie Webanwendungen, die Daten in die Datenbank der Kampagne einfügen? Wenn ja, führen Sie sie aus und vergewissern Sie sich, dass sie neue Datensätze über die API einfügen können.
* Können Sie eine Test-E-Mail erfolgreich versenden? Erstellen Sie einen neuen Versand mit einer bekannten Vorlage, senden Sie ihn an einen Test-Empfänger, überprüfen Sie die Personalisierung, heben Sie die Verknüpfung auf, Mirrorseite alle Arbeit.
* Laufen alle Ihre kritischen Pfade Workflows? Überprüfen Sie Workflows, öffnen Sie das Workflow-Protokoll und stellen Sie sicher, dass keine Fehler vorliegen.
* Sind alle Ordner vorhanden, sichtbar und verfügbar? Durchsuchen Sie verschiedene Ordner und überprüfen Sie sie.
alle Inhalte angezeigt und vorhanden sind.
* Werden Ihre Versand mit der richtigen Zeitzone durchkommen?

   * Erstellungsdatum und Änderungsdatum mit Zeitstempel und Zeitzone überprüfen
   * Überprüfen Sie, ob die Ausführung der Planung zum angegebenen Zeitpunkt in einem Workflow funktioniert
   * Rufen Sie die Liste von Workflows ab, die sich im Status PAUSED und FAILED befinden. Beginn und Überwachung
   * Ausführen von AB-Tests für ein Szenario
   * Testen von Push-Benachrichtigungen mit ihren Verfolgungsfunktionen für Deep Links
   * Versenden von SMS
   * Wenn eine externe FDA verbunden ist, testen Sie, ob die Daten auf beide Arten gesendet werden
   * Wenn Sie Integrationen wie Adobe Campaign-Adobe Experience Manager, Adobe Campaign-Adobe Analytics verwenden, testen Sie, ob sie weiterhin wie zuvor funktionieren

**Siehe auch**

* [Durchführen eines Build-Upgrades](../../production/using/build-upgrade.md)
* [Versionshinweise zu Campaign Classic ](../../rn/using/rn-overview.md)
* [Hilfe- und Supportoptionen für Campaign Classic](https://helpx.adobe.com/campaign/kb/ac-support.html#acc-support-req)
* [Gold Standard-Programm](https://helpx.adobe.com/de/campaign/kb/gold-standard.html)
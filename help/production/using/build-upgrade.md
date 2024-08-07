---
product: campaign
title: Erste Schritte mit Build-Upgrades
description: Wichtige Schritte zum Upgrade auf einen neuen Build
feature: Monitoring, Upgrade
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: c5a9c99a-4078-45d8-847b-6df9047a2fe2
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '2324'
ht-degree: 37%

---

# Durchführen eines Build-Upgrades{#performing-a-build-upgrade}



In diesem Abschnitt erhalten Sie eine ausführliche Anleitung zum Upgrade-Prozess und zu den Schritten zur Ermittlung und Lösung von Konflikten.

Das Build-Upgrade muss mit Vorsicht durchgeführt werden, seine Auswirkungen müssen im Voraus umfassend berücksichtigt werden und das Verfahren muss mit einem hohen Maß an Disziplin abgeschlossen werden. Um eine erfolgreiche Aktualisierung sicherzustellen, stellen Sie sicher, dass nur erfahrene Benutzer die unten beschriebenen Schritte ausführen. Darüber hinaus empfehlen wir dringend, sich mit der [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) in Verbindung zu setzen, bevor Sie mit einem Upgrade beginnen.

Folgende Voraussetzungen sind erforderlich:

* Kenntnis der Campaign-Architektur
* Kenntnis der Systeme und Server
* Administratorrechte und Berechtigungen

Weitere Informationen finden Sie in den folgenden Abschnitten: [Aktualisieren von Adobe Campaign](../../production/using/upgrading.md), [Migrieren zu einer neuen Version](../../migration/using/about-migration.md).

Bei gehosteten und hybriden Instanzen müssen Sie das Build-Upgrade beim Adobe Technical Operations-Team anfordern. Weitere Informationen hierzu finden Sie im Abschnitt Häufig gestellte Fragen am unteren Rand dieser Seite. Lesen Sie auch die [FAQ zum Build-Upgrade](../../platform/using/faq-build-upgrade.md).

## Vorbereiten des Upgrades

![](assets/do-not-localize/icon_planification.png)

Vor Beginn des Build-Upgrades müssen Sie eine vollständige Vorbereitung wie unten beschrieben durchführen.
Sobald das System für die Aktualisierung bereit ist, dauert ein Build-Upgrade **mindestens** 2 Stunden.

Für das Build-Upgrade sind die folgenden Ressourcen erforderlich:

* ein Adobe-Architekt, der die Datenbankstrukturen (vordefinierte Schemas und alle hinzugefügten zusätzlichen Schemas, Kampagnenentwürfe und alle wichtigen Pfadfunktionen, die in einer bestimmten Reihenfolge gestartet und getestet werden müssen) versteht.
* Projektmanager - Wenn das Build-Upgrade viele verschiedene Instanzen (Produktion, Staging, Tests) und andere Drittanbieter-Server und -Anwendungen (Datenbanken, SFTP-Sites, Messaging-Service-Provider) umfasst, gilt ein Projektmanager zur Koordinierung aller Tests als Best Practice.
* ein Adobe-Campaign-Administrator: Er kennt die Konfiguration des Servers, u. a. Anforderungen in Bezug auf Sicherheit, Ordneraufbau, Reporting und den Import und Export. Bitte nehmen Sie kein Build-Upgrade ohne Ihren Administrator vor.
* ein Adobe Campaign-Benutzer (Marketing-Benutzer): Ein erfolgreiches Upgrade hängt von der Fähigkeit des Benutzers ab, seine täglichen Aufgaben erfolgreich durchzuführen. Aus diesem Grund sollten Sie mindestens einen Ihrer täglichen Benutzer in Ihre Tests der aktualisierten Server einbeziehen.

### Planung

Dies sind die wichtigsten Schritte zur Planung eines Build-Upgrades:

1. Planen Sie mindestens zwei Stunden für das Upgrade ein.
1. Stellen Sie Kontaktdetails für Adobe- und Kundenmitarbeiter bereit.
1. Für gehostete Instanzen: die Adobe- und Kundenmitarbeiter bestimmen den Zeitpunkt des Upgrades sowie die Person, die ihn durchführt.
1. Für On-Premise-Instanzen: die Kundenmitarbeiter führen den gesamten Prozess aus. Wenn Hilfe beim Testen benutzerdefinierter Workflows und Sendungen benötigt wird, sollten Beratungsdienste in Anspruch genommen werden.
1. Ermitteln und bestätigen Sie, auf welche Version von Adobe Campaign Sie aktualisieren möchten - lesen Sie die [Adobe Campaign Classic-Versionshinweise](../../rn/using/rn-overview.md).
1. Bestätigen Sie das Vorhandensein ausführbarer Upgrade-Dateien.

### Wichtige Personen

Für das Build-Upgrade müssen die folgenden Personen beteiligt sein:

* Adobe-Architekt: Bei gehosteten oder hybriden Architekturen muss sich der Architekt mit der Adobe Campaign-Kundenunterstützung abstimmen.

* Projektmanager:
   * für On-Premise-Installationen: Der interne Projektleiter des Kunden leitet die Aktualisierung und verwaltet Lebenszyklustests.

   * für gehostete Installationen: Das Hosting-Team arbeitet mit dem Adobe Campaign Client Care-Team und dem Kunden zusammen, um den Zeitplan für die Aktualisierung für alle Instanzen zu koordinieren.

* Adobe Campaign-Administrator:
   * für On-Premise-Installationen: Der Administrator führt das Upgrade durch.

   * für gehostete Installationen: Das Hosting-Team führt das Upgrade durch.

* Adobe Campaign-Benutzer/Marketing-Benutzer: Der Benutzer führt Tests für Entwicklungs-, Test- und Produktionsinstanzen durch.

### Build-Aktualisierung vorbereiten

Vor Beginn der Build-Aktualisierung müssen On-Premise-Kunden die folgende Vorbereitung durchführen:

1. Vergewissern Sie sich, dass alle Entwicklungsarbeiten exportiert werden können, bevor das Upgrade durchgeführt wird. Führen Sie den Export als Packages durch.

1. Führen Sie eine vollständige Sicherung der Datenbanken für alle Instanzen der Quell- und Zielumgebungen durch.

1. Rufen Sie die neueste Version Ihrer [Server-Konfigurationsdatei](../../installation/using/the-server-configuration-file.md) ab.

1. [Laden Sie den neuesten Build herunter](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html). [Weitere Informationen](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=de).

Außerdem müssen Sie alle [nützlichen Befehlszeilen](../../installation/using/command-lines.md) kennen, bevor Sie mit einem Build-Upgrade beginnen:

* **nlserver pdump**: listet aktuelle Prozesse auf
* **nlserver pdump -who**: listet aktive Client-Sitzungen auf
* **nlserver monitor -missing**: listet fehlende Eigenschaften auf
* **nlserver start process@instance-name**: startet einen Prozess
* **nlserver stop process@instance-name**: stoppt einen Prozess
* **nlserver restart process@instance-name**: startet einen Prozess neu
* **nlserver shutdown**: beendet alle Campaign-Prozesse
* **nlserver watchdog -svc**: startet den Watchdog-Prozess (nur UNIX)

## Führen Sie das Upgrade durch

![](assets/do-not-localize/icon_process.png)

Die folgenden Verfahren werden nur von **On-Premise** -Kunden durchgeführt. Für gehostete Kunden wird dies vom Hosting-Team übernommen. Um Adobe Campaign auf einen neuen Build zu aktualisieren, wird das entsprechende Verfahren unten beschrieben.

### Umgebung duplizieren

So duplizieren Sie eine Adobe Campaign-Umgebung, um eine Quellumgebung in eine Zielumgebung wiederherzustellen, was zu zwei identischen Arbeitsumgebungen führt.

Gehen Sie dazu wie folgt vor:

1. Erstellen Sie eine Kopie der Datenbanken auf allen Instanzen in der Quellumgebung.

1. Stellen Sie diese Kopien auf allen Instanzen der Zielumgebung wieder her.

1. Führen Sie das Warnungsskript **nms:freezeInstance.js** in der Zielumgebung aus, bevor Sie es starten. Dadurch werden alle Prozesse beendet, die mit der Außenwelt interagieren: Protokolle, Tracking, Sendungen, Kampagnen-Workflows usw.

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. Überprüfen Sie die Vorsicht wie folgt:

   * Vergewissern Sie sich, dass der einzige Lieferteil der ist, für den die ID auf **0** festgelegt ist:

     ```
     SELECT * FROM neolane.nmsdeliverypart;
     ```

   * Vergewissern Sie sich, dass die Versandstatus-Aktualisierung korrekt ist:

     ```
     SELECT iSate, count(*) FROM neolane.nmsdeliveryGroup By iProd;
     ```

   * Vergewissern Sie sich, dass die Workflow-Status-Aktualisierung korrekt ist:

     ```
     SELECT iState, count (*) FROM neolane.xtkworkflowGROUP BY iState;
     SELECT iStatus, count (*) FROM neolane.xtkworkflowGROUP BY iStatus;
     ```

### Dienste beenden

Um alle Dateien durch die neue Version zu ersetzen, müssen alle Instanzen des nlserverservice beendet werden.

1. Beenden Sie die folgenden Dienste:

   * Webdienste (IIS): **iisreset /stop**
   * Adobe-Campaign-Dienst: **net stop nlserver6**

   >[!NOTE]
   >
   >Stellen Sie sicher, dass der Weiterleitungsserver (webmdl) angehalten ist, damit die von IIS verwendete Datei nlsrvmod.dll durch die neue Version ersetzt werden kann.
   >

1. Vergewissern Sie sich, dass keine Aufgaben aktiv sind, indem Sie den Befehl **nlserver pdump** ausführen. Wenn keine Aufgaben vorhanden sind, sollte die Ausgabe wie folgt aussehen:

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. Überprüfen Sie den Windows Task Manager, um sicherzustellen, dass alle Prozesse beendet wurden.

### Aktualisieren der Adobe Campaign-Serveranwendung

1. Führen Sie die Datei **Setup.exe** aus. Wenn Sie diese Datei herunterladen müssen, rufen Sie [das Download-Center](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html) auf.

1. Wählen Sie den Installationsmodus aus: **Aktualisieren** oder **Reparieren**.

1. Klicken Sie auf **Weiter**.

1. Wählen Sie **Beenden** aus: Die neue Datei wird vom Installationsprogramm kopiert.

1. Wählen Sie nach Abschluss des Vorgangs die Option **Beenden** aus.

### Ressourcen synchronisieren

1. Öffnen Sie die Befehlszeile.

1. Führen Sie **nlserver config -postupgrade -allinstances** aus, um Folgendes durchzuführen:

   * Ressourcen synchronisieren
   * Schemata aktualisieren
   * Aktualisieren der Datenbank

   >[!NOTE]
   >
   >Dieser Vorgang sollte nur einmal und nur auf einem nlserverweb-Anwendungsserver ausgeführt werden.
   >

   Um nur eine Datenbank zu synchronisieren, führen Sie den folgenden Befehl aus:

   ```
   nlserver config -postupgrade -instance: <instance_name>
   ```

1. Überprüfen Sie, ob bei der Synchronisierung Fehler oder Warnungen aufgetreten sind.

### Dienste wieder starten

Die folgenden Dienste müssen wieder gestartet werden:

* Webdienste (IIS): **issreset /start**
* Adobe-Campaign-Dienst: **net start nlserver6**

### Aktualisierung der Client-Konsolen

Die Client-Konsole muss denselben Build haben wie die Server-Instanz.

Laden Sie auf der Maschine, auf der der Adobe Campaign-Anwendungsserver installiert ist (nlserverweb), diese Datei herunter und kopieren Sie sie:

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```

Wenn das nächste Mal Clientkonsolen verbunden werden, werden die Benutzer darauf hingewiesen, dass eine neue Aktualisierung verfügbar ist, und erhalten die Möglichkeit, diese herunterzuladen und zu installieren.

### Spezifische zusätzliche Aufgaben

Einige Konfigurationen erfordern bestimmte zusätzliche Aufgaben, um auf einen neuen Build aktualisiert zu werden.

#### Transaktionsnachrichtenversand

Wenn Transaktionsnachrichten (Message Center) in Ihrer Campaign-Instanz aktiviert ist, müssen Sie die folgenden zusätzlichen Schritte ausführen, um eine Aktualisierung durchzuführen:

1. Aktualisieren Sie den Message-Center-Produktionsserver auf die gewünschte Version.
1. Führen Sie die Postupgrade-Scripts aus.
1. Führen Sie Tests durch und stellen Sie sicher, dass der E-Mail-Empfang über die Message-Center-Produktionsinstanz funktioniert.
1. Aktualisieren Sie die Clients und leeren Sie den Cache.
1. Packages exportieren:
   * Packages mithilfe des Client-Package-Export-Tools exportieren
   * Schema-Package importieren
   * Client trennen und erneut verbinden
   * Datenbank aktualisieren
   * Trennen und erneutes Verbinden
   * Admin-Package importieren
   * Inhaltspaket importieren
   * Import Content Management Package
   * Trennen und erneutes Verbinden
   * Durchführen einer schnellen Überprüfung der Workflows

1. Publizieren Sie Message-Center-Vorlagen, um sicherzugehen, dass die Schnittstelle zwischen den Servern und der Message-Center-Instanz funktioniert.
1. Führen Sie Tests durch, um sicherzustellen, dass E-Mails erfolgreich über die Message-Center-Produktionsinstanz empfangen werden.
1. Führen Sie Workflow-Tests bei der Produktion durch, um sicherzugehen, dass der Nachrichtenempfang funktioniert.

#### Mid-Sourcing

Im Kontext einer Mid-Sourcing-Umgebung müssen Sie die folgenden zusätzlichen Schritte ausführen, um eine Aktualisierung durchzuführen:

1. Wenden Sie sich an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html), um die Aktualisierung des Mid-Sourcing-Servers zu koordinieren.
1. Überprüfen Sie, ob die Version aktualisiert wurde, indem Sie einen Test-Link ausführen. Beispiel:

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>Der Mid-Sourcing-Server muss immer dieselbe Version (oder eine neuere Version) wie die Marketing-Server ausführen.
>

## Bei Konflikten

### Konflikte identifizieren

Sie müssen das Synchronisierungsergebnis überprüfen. Dieser Schritt wird nur von On-Premise-Kunden ausgeführt. Für gehostete Kunden übernimmt diese Aufgabe das Hosting-Team. Es gibt zwei Möglichkeiten, das Synchronisationsergebnis anzuzeigen:

In der Befehlszeilenschnittstelle werden Fehler durch ein dreifaches Chevron &quot;>>>&quot;materialisiert und die Synchronisation wird automatisch angehalten. Warnungen werden durch ein doppeltes Chevron &quot;>>&quot;erzeugt und müssen nach Abschluss der Synchronisation behoben werden. Am Ende des Postupgrades wird an der Eingabeaufforderung eine Zusammenfassung angezeigt. Sie kann wie folgt aussehen:

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

Wenn die Warnung einen Ressourcenkonflikt betrifft, muss der Benutzer darauf achten, ihn zu beheben.

Die Datei **postupgrade_ServerVersionNumber_TimeOfPostupgrade.log** enthält das Synchronisierungsergebnis. Sie ist standardmäßig im folgenden Ordner verfügbar: **installationDirectory/var/`<instance-name>`/postupgrade**. Fehler und Warnungen werden durch die Fehler- und Warnattribute angezeigt.

### Konflikte analysieren

**Wie wird ein Konflikt gefunden?**

Konflikte finden Sie auf dem betreffenden Server im postupgrade.log oder in der Campaign-Client-Oberfläche (Administration > Konfiguration > Package-Management > Konflikte bearbeiten).

Das Dokument mit der Kennung ‘stockOverview’ vom Typ ‘nms:webApp’ steht im Konflikt mit der neuen Version.

Wenn ein Konflikt gefunden wird, prüfen Sie, ob Folgendes zutrifft:

* Wurde das Objekt vom Kunden geändert oder personalisiert?
* Wurde das Objekt innerhalb des Produkts geändert?

Wenn keine dieser Fragen bejaht wird, ist dies eine Falschmeldung und es besteht kein Konflikt. Wenn beide dieser Fragen bejaht werden, besteht tatsächlich ein Konflikt.

**Wurde das Objekt vom Kunden geändert?**

1. Identifizieren Sie das Objekt, das den Konflikt auslöst.
1. Fragen Sie den Kunden, ob er das Objekt verändert hat.
1. Ist an dem Objekt etwas ungewöhnlich?
1. Ist das letzte Änderungsdatum im Code des Objekts angegeben?
1. Prüfen Sie den XML-Code des Konflikts auf &quot;_conflict&quot;-Attribute. Sieht es wie eine Anpassung aus?

**Wurde das Objekt im neuen Build geändert?**

1. Prüfen Sie die üblichen Verursacher: integrierte Web-Anwendungen oder Berichte (z. B.: &#39;deliveryValidation&#39;, &#39;deliveryOverview&#39;, &#39;budget&#39;).
1. Prüfen Sie die Änderungsprotokolle auf Updates.
1. Fragen Sie Adobe Campaign-Experten.
1. Führen Sie einen &quot;Diff&quot;-Befehl für den Code aus.

### Beheben eines Konflikts

Gehen Sie wie folgt vor, um einen Konflikt zu lösen:

1. Gehen Sie im Adobe-Campaign-Explorer zu **Administration > Konfiguration > Packageverwaltung > Konflikte bearbeiten**.

1. Wählen Sie in der Liste den Konflikt aus, den Sie lösen möchten.
Es gibt drei Optionen zum Auflösen von Konflikten: **Akzeptieren der neuen Version**, **Behalten Sie die aktuelle Version**, **Zusammenführen des Codes (und deklarieren Sie ihn als aufgelöst)**, **Ignorieren Sie den Konflikt (nicht empfohlen)**.

**Wann kann ich die neue Version akzeptieren?**

* Wenn Sie die Standardfunktionen beibehalten möchten.
* Wenn Sie keine Personalisierungen durchgeführt haben (alle Personalisierungen werden entfernt)

**Wann kann ich die aktuelle Version beibehalten?**

* Wenn Sie Personalisierungen durchgeführt haben
* Wenn Sie keine Zusammenführung durchführen möchten
* Wenn Sie das Konflikt auslösende Objekt nicht im Postupgrade korrigieren müssen

**Wann soll eine Zusammenführung durchgeführt werden?**

* Nur Formulare, Berichte und Webanwendungen können zusammengeführt werden.
* Einige geringfügige Zusammenführungen können durchgeführt werden, ohne den Code zu verstehen.
* Kompliziertere Zusammenführungen sollten jedoch von einer Fachkraft durchgeführt werden.
* Siehe [Führen Sie eine Zusammenführung durch](#perform-a-merge).

**Was passiert, wenn ich die Konflikte ignoriere?**

* Der Konflikt bleibt bestehen.
* Das Objekt wird nicht aktualisiert.
* Langfristige Auswirkungen: Inkompatibilität der Versionen, der Kunde profitiert nicht von Fehlerkorrekturen.

>[!IMPORTANT]
>Es wird dringend empfohlen, Konflikte zu lösen.
>

### Zusammenführen{#perform-a-merge}

Es gibt verschiedene Arten von Zusammenführungen:

1. Einfache Zusammenführung: Benutzerdefinierte und neue Elemente sind klein und nicht miteinander verbunden und es ist keine Kodierung erforderlich.
1. Keine Änderungen: die neue Version wird akzeptiert, nur letztes Aktualisierungsdatum wurde geändert, nur Kommentare, Tabs, Leerzeichen oder neue Zeilen. Beispiel: irrtümliches Speichern.
1. Triviale Änderungen: nur eine einzige Zeile wurde geändert. Beispiel: xpathToLoad
1. Komplexe Zusammenführung: wenn eine Kodierung erforderlich ist. Entwicklungsfähigkeiten sind erforderlich. Siehe [Komplexe Zusammenführungen](#complex-merges).

#### Wie erfolgt die Zusammenführung?

1. Rufen Sie alle drei Versionen ab: die Originalversion, die neue Version und die benutzerdefinierte Version.
1. Führen Sie einen &quot;Vergleich&quot;zwischen der ursprünglichen und der neuen Version aus.
1. Isolieren Sie die Änderungen.
1. Wenn keine Änderungen vorhanden sind, lösen Sie den Konflikt, indem Sie die aktuelle Version beibehalten.

#### Wo finden Sie den Code?

1. Integrierter Code wird in XML-Dateien im Ordner datakit gespeichert. Suchen Sie die XML-Datei, die dem widersprüchlichen Objekt entspricht. Beispiel: installationDirectory\datakit\nms\fra\form\recipient.xml
1. Rufen Sie die Originalversion ab: über das [Download-Center](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html) oder eine andere nicht aktualisierte Installation des Produkts.
1. Rufen Sie die neue Version ab: über das [Download-Center](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) oder die vom Kunden installierten Dateien.
1. Rufen Sie die benutzerdefinierte Version ab: Rufen Sie den Quellcode des Objekts vom Campaign-Client ab.

### Wie erstelle ich eine Diff-Datei?

1. Installieren Sie einen Text- oder Merge-Editor, z. B. Notepad ++, AraxisMerge oder WinMerge.
1. Öffnen Sie die Originaldatei und die neue Datei im Editor.
1. Führen Sie den Diff-Befehl aus (vergleichen Sie die beiden Dateien).
1. Stellen Sie etwaige Unterschiede fest.

### Wie erfolgt die Zusammenführung?

1. Beginnen Sie mit der benutzerdefinierten Version.
1. Wenden Sie die Änderungen an.
1. Lösen Sie den Konflikt, indem Sie ihn als gelöst erklären.
1. Auf Nicht-Regressionen prüfen.

Wenn Sie den Konflikt manuell lösen möchten, gehen Sie folgendermaßen vor:

1. Suchen Sie im unteren Abschnitt des Fensters nach **_conflict_string_** , um die Entitäten mit Konflikten zu finden. Die mit der neuen Version installierte Entität enthält das neue Argument. Die Entität, die mit der vorherigen Version übereinstimmt, enthält das benutzerdefinierte Argument.
1. Löschen Sie die Version, die Sie nicht beibehalten möchten. Löschen Sie die Zeichenfolge **_conflict_argument_** der Entität, die Sie beibehalten.
1. Gehen Sie zu dem Konflikt, den Sie gelöst haben. Klicken Sie auf das Symbol **Aktionen** und wählen Sie **Als aufgelöst erklären** aus.
1. Speichern Sie Ihre Änderungen: Der Konflikt ist jetzt gelöst.

#### Komplexe Zusammenführungen{#complex-merges}

1. Erfahren Sie, was die Änderung bewirkt: Sie können die Änderungen rückgängig machen, die Änderungsprotokolle untersuchen und mit Adobe Campaign-Experten zusammenarbeiten.
1. Entscheiden Sie, was mit der Änderung zu tun ist.
1. Machen Sie sich mit den Anpassungen vertraut: Reverse Engineering der Änderungen

So nehmen Sie eine komplexe Zusammenführung vor:

1. Codebits aus dem Änderungssatz kopieren
1. In die angepasste Version einfügen
1. Prüfung auf Nichtregressionen der Anpassung
1. Prüfung auf Funktionsfähigkeit von Änderungen
1. Durchführen von Benutzerakzeptanztests
1. Führen Sie die Zusammenführung in einer Testumgebung durch.


>[!IMPORTANT]
>Für komplexe Zusammenführungen sind Entwicklungsfähigkeiten erforderlich.
>

**Verwandte Themen** 

* [Häufig gestellte Fragen zur Build-Aktualisierung](../../platform/using/faq-build-upgrade.md)
* [Versionshinweise zu Campaign Classic](../../rn/using/rn-overview.md)
* [Hilfe- und Support-Optionen für Campaign Classic](../../support.md)
* [Jährliches Upgrade-Programm für Campaign](../../rn/using/rn-overview.md)

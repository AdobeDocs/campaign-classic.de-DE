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



In diesem Abschnitt finden Sie eine ausführliche Anleitung zum Upgrade-Prozess und zu den Schritten zum Identifizieren und Beheben von Konflikten.

Das Build-Upgrade muss mit Vorsicht durchgeführt werden, seine Auswirkungen müssen zuvor vollständig berücksichtigt werden und das Verfahren muss mit einem hohen Maß an Disziplin abgeschlossen werden. Um ein erfolgreiches Upgrade sicherzustellen, stellen Sie sicher, dass nur erfahrene Benutzer die unten beschriebenen Schritte ausführen. Darüber hinaus empfehlen wir dringend, sich vor einem Upgrade an die [Adobe](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)Kundenunterstützung zu wenden.

Die folgenden Voraussetzungen sind erforderlich:

* Kenntnis der Campaign-Architektur
* Kenntnis der Systeme und Server
* Administratorrechte und Berechtigungen

Adobe Campaign Weitere Informationen finden Sie in den folgenden Abschnitten: [Aktualisieren von ](../../production/using/upgrading.md), [Migrieren zu einer neuen Version](../../migration/using/about-migration.md).

Bei gehosteten und hybriden Instanzen müssen Sie das Build-Upgrade an das Team für technische Vorgänge in Adobe anfordern. Weiterführende Informationen hierzu finden Sie im Abschnitt Häufig gestellte Fragen unten auf dieser Seite. Lesen Sie auch die [häufig gestellte Fragen zum Build-Upgrade](../../platform/using/faq-build-upgrade.md).

## Upgrade vorbereiten

![](assets/do-not-localize/icon_planification.png)

Bevor Sie mit dem Build-Upgrade beginnen, müssen Sie eine vollständige Vorbereitung wie unten beschrieben durchführen.
Sobald das System für ein Upgrade bereit ist, dauert ein Build-Upgrade **mindestens** 2 Stunden.

Für das Build-Upgrade sind die folgenden Ressourcen erforderlich:

* Ein Adobe-Architekt: Zum Verständnis der Datenbankstrukturen (vordefinierte Schemata und alle zusätzlichen Schemata, die hinzugefügt wurden, Kampagnendesigns und alle kritischen Pfadfunktionen, die in einer bestimmten Reihenfolge gestartet und getestet werden müssen).
* Projektmanager: Für den Fall, dass das Build-Upgrade viele verschiedene Instanzen (Produktion, Staging, Tests) und andere Server und Anwendungen von Drittanbietern (Datenbanken, SFTP-Sites, Messaging-Service-Provider) umfasst, ist es als Best Practice zu betrachten, einen Projektmanager zu haben, der alle Tests koordiniert.
* ein Adobe-Campaign-Administrator: Er kennt die Konfiguration des Servers, u. a. Anforderungen in Bezug auf Sicherheit, Ordneraufbau, Reporting und den Import und Export. Bitte nehmen Sie kein Build-Upgrade ohne Ihren Administrator vor.
* Ein Adobe Campaign-Benutzer (Marketing-Benutzer): Für ein erfolgreiches Upgrade ist die Fähigkeit des Benutzers erforderlich, seine täglichen Aufgaben erfolgreich auszuführen. Aus diesem Grund sollten Sie immer mindestens einen Ihrer täglichen Benutzer in Ihre Tests der aktualisierten Server einbeziehen.

### Planung

Dies sind die wichtigsten Schritte zur Planung eines Build-Upgrades:

1. Planen Sie mindestens zwei Stunden für das Upgrade ein.
1. Stellen Sie Kontaktdetails für Adobe- und Kundenmitarbeiter bereit.
1. Für gehostete Instanzen: die Adobe- und Kundenmitarbeiter bestimmen den Zeitpunkt des Upgrades sowie die Person, die ihn durchführt.
1. Für On-Premise-Instanzen: die Kundenmitarbeiter führen den gesamten Prozess aus. Wenn Hilfe beim Testen benutzerdefinierter Workflows und Sendungen benötigt wird, sollten Beratungsdienste in Anspruch genommen werden.
1. Ermitteln und bestätigen Sie, auf welche Version von Adobe Campaign Sie ein Upgrade durchführen möchten - lesen Sie die [Versionshinweise zu Adobe Campaign Classic](../../rn/using/rn-overview.md).
1. Bestätigen Sie das Vorhandensein ausführbarer Upgrade-Dateien.

### Schlüsselpersonen

Für den Build-Upgrade-Prozess müssen die folgenden Personen beteiligt sein:

* Adobe-Architekt: Bei gehosteten oder hybriden Architekturen muss sich der Architekt mit der Adobe Campaign-Kundenunterstützung abstimmen.

* Projektmanager:
   * Bei On-Premise-Installationen: Der interne Projektleiter des Kunden leitet das Upgrade und verwaltet Lebenszyklustests.

   * bei gehosteter Installation: Das Hosting-Team arbeitet mit dem Adobe Campaign-Kundenunterstützungs-Team und dem Kunden zusammen, um den Zeitplan für die Aktualisierung für alle Instanzen zu koordinieren.

* Adobe Campaign-Administrator:
   * Bei On-Premise-Installationen: Der Administrator führt das Upgrade durch.

   * für gehostete Installationen: Das Hosting-Team führt das Upgrade durch.

* Adobe Campaign-Benutzer/Marketing-Benutzer: Der Benutzer führt Tests für Entwicklungs-, Test- und Produktionsinstanzen durch.

### Build-Upgrade vorbereiten

Vor Beginn des Build-Upgrades müssen On-Premise-Kunden die folgende Vorbereitung durchführen:

1. Vergewissern Sie sich, dass alle Entwicklungsarbeiten exportiert werden können, bevor das Upgrade durchgeführt wird. Führen Sie den Export als Packages durch.

1. Führen Sie ein vollständiges Backup der Datenbanken für alle Instanzen der Quell- und Zielumgebung durch.

1. Erhalten Sie die neueste Version Ihrer [Server-Konfigurationsdatei](../../installation/using/the-server-configuration-file.md).

1. [Laden Sie den neuesten Build herunter](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html). [Weitere Informationen](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=de).

Außerdem müssen Sie alle [nützlichen Befehlszeilen“ kennen](../../installation/using/command-lines.md) bevor Sie ein Build-Upgrade starten:

* **nlserver pdump**: listet aktuelle Prozesse auf
* **nlserver pdump -who**: listet aktive Client-Sitzungen auf
* **nlserver monitor -missing**: listet fehlende Eigenschaften auf
* **nlserver start process@instance-name**: Startet einen Prozess
* **nlserver stop process@instance-name**: Beendet einen Prozess
* **nlserver restart process@instance-name**: Startet einen Prozess neu
* **nlserver shutdown**: Beendet alle Campaign-Prozesse
* **nlserver watchdog -svc**: startet den Watchdog-Prozess (nur UNIX)

## Durchführen des Upgrades

![](assets/do-not-localize/icon_process.png)

Die folgenden Verfahren werden nur von On **Premise-Kunden**. Für gehostete Kunden wird dies vom Hosting-Team übernommen. Um Adobe Campaign auf einen neuen Build zu aktualisieren, wird im Folgenden das detaillierte Verfahren beschrieben.

### Duplizieren der Umgebung

So duplizieren Sie eine Adobe Campaign-Umgebung, um eine Quellumgebung in einer Zielumgebung wiederherzustellen, was zu zwei identischen Arbeitsumgebungen führt.

Gehen Sie dazu wie folgt vor:

1. Erstellen Sie eine Kopie der Datenbanken auf allen Instanzen in der Quellumgebung.

1. Stellen Sie diese Kopien auf allen Instanzen der Zielumgebung wieder her.

1. Führen Sie **Skript &quot;:freezeInstance.js** vor dem Start in der Zielumgebung aus. Dadurch werden alle Prozesse gestoppt, die mit der Außenwelt interagieren: Protokolle, Tracking, Sendungen, Kampagnen-Workflows usw.

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. Die Kauterisierung wie folgt überprüfen:

   * Vergewissern Sie sich, dass nur der Versandteil mit der ID &quot;**&quot;**:

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

Um alle Dateien durch die neue Version zu ersetzen, müssen alle Instanzen des nlserverservice heruntergefahren werden.

1. Beenden Sie die folgenden Dienste:

   * Webdienste (IIS): **iisreset/stop**
   * Adobe-Campaign-Dienst: **net stop nlserver6**

   >[!NOTE]
   >
   >Stellen Sie sicher, dass der Weiterleitungsserver (webmdl) gestoppt ist, damit die von IIS verwendete Datei „nlsrvmod.dll“ durch die neue Version ersetzt werden kann.
   >

1. Überprüfen Sie, ob keine Aufgaben aktiv sind, indem Sie den Befehl **nlserver pdump** ausführen. Wenn keine Aufgaben vorhanden sind, sollte die Ausgabe der folgenden ähneln:

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. Überprüfen Sie im Windows Task-Manager, ob alle Prozesse angehalten wurden.

### Aktualisieren der Adobe Campaign-Serveranwendung

1. Führen Sie die Datei **Setup.exe** aus. Wenn Sie diese Datei herunterladen müssen, rufen Sie [Download-Center](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html) auf.

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
   >Dieser Vorgang sollte nur einmal und nur auf einem nlserverwebanwendungsserver ausgeführt werden.
   >

   Um nur eine Datenbank zu synchronisieren, führen Sie den folgenden Befehl aus:

   ```
   nlserver config -postupgrade -instance: <instance_name>
   ```

1. Überprüfen Sie, ob bei der Synchronisierung Fehler oder Warnungen erzeugt wurden.

### Dienste wieder starten

Die folgenden Dienste müssen wieder gestartet werden:

* Webdienste (IIS): **issreset /start**
* Adobe-Campaign-Dienst: **net start nlserver6**

### Aktualisierung der Client-Konsolen

Die Client-Konsole muss auf demselben Build wie die Server-Instanz erstellt werden.

Laden Sie auf der Maschine, auf der der Adobe Campaign-Anwendungsserver installiert ist (nlserverweb), diese Datei herunter und kopieren Sie sie:

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```

Wenn das nächste Mal Clientkonsolen verbunden werden, werden die Benutzer darauf hingewiesen, dass eine neue Aktualisierung verfügbar ist, und erhalten die Möglichkeit, diese herunterzuladen und zu installieren.

### Spezifische zusätzliche Aufgaben

Einige Konfigurationen erfordern bestimmte zusätzliche Aufgaben, um auf einen neuen Build zu aktualisieren.

#### Transaktionsnachrichten

Wenn Transaktionsnachrichten (Message Center) auf Ihrer Campaign-Instanz aktiviert ist, müssen Sie diese zusätzlichen Schritte ausführen, um ein Upgrade durchzuführen:

1. Aktualisieren Sie den Message-Center-Produktionsserver auf die gewünschte Version.
1. Führen Sie die Postupgrade-Scripts aus.
1. Führen Sie Tests durch und stellen Sie sicher, dass der E-Mail-Empfang über die Message-Center-Produktionsinstanz funktioniert.
1. Aktualisieren Sie die Clients und leeren Sie den Cache.
1. Packages exportieren:
   * Exportieren von Paketen mit dem Tool zum Exportieren von Clientpaketen
   * Schemapaket importieren
   * Client trennen und erneut verbinden
   * Datenbank aktualisieren
   * Trennen und erneut verbinden
   * Admin-Paket importieren
   * Inhaltspaket importieren
   * Content-Management-Paket importieren
   * Trennen und erneut verbinden
   * Durchführen einer schnellen Konsistenzprüfung von Workflows

1. Publizieren Sie Message-Center-Vorlagen, um sicherzugehen, dass die Schnittstelle zwischen den Servern und der Message-Center-Instanz funktioniert.
1. Führen Sie Tests durch, um sicherzustellen, dass E-Mails erfolgreich über die Produktionsinstanz von Message Center empfangen werden.
1. Führen Sie Workflow-Tests bei der Produktion durch, um sicherzugehen, dass der Nachrichtenempfang funktioniert.

#### Mid-Sourcing

Im Kontext einer Mid-Sourcing-Umgebung müssen Sie die folgenden zusätzlichen Schritte ausführen, um ein Upgrade durchzuführen:

1. Wenden Sie sich an die [Adobe](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)Kundenunterstützung, um das Upgrade des Mid-Sourcing-Servers zu koordinieren.
1. Überprüfen Sie, ob die Version aktualisiert wurde, indem Sie einen Test-Link ausführen. Beispiel:

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>Der Mid-Sourcing-Server muss immer dieselbe Version (oder eine neuere Version) ausführen wie die Marketing-Server.
>

## Bei Konflikten

### Konflikte identifizieren

Sie müssen das Synchronisierungsergebnis überprüfen. Dieser Schritt wird nur von On-Premise-Kunden ausgeführt. Für gehostete Kunden übernimmt diese Aufgabe das Hosting-Team. Es gibt zwei Möglichkeiten, das Synchronisationsergebnis anzuzeigen:

In der Befehlszeilenschnittstelle werden Fehler durch einen dreifachen Chevron &#39;>>>&#39; materialisiert und die Synchronisierung wird automatisch angehalten. Warnungen werden durch einen doppelten Pfeil &quot;>>&quot; materialisiert und müssen nach Abschluss der Synchronisierung aufgelöst werden. Am Ende des Postupgrades wird in der Eingabeaufforderung eine Zusammenfassung angezeigt. Er kann wie folgt aussehen:

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

Wenn die Warnung einen Ressourcenkonflikt betrifft, ist ein Eingreifen des Benutzers erforderlich, um ihn zu lösen.

Die Datei **postupgrade_ServerVersionNumber_TimeOfPostupgrade.log** enthält das Synchronisierungsergebnis. Sie ist standardmäßig im folgenden Verzeichnis verfügbar: **installationDirectory/var/`<instance-name>`/postupgrade**. Fehler und Warnungen werden durch die Attribute error und warning gekennzeichnet.

### Konflikte analysieren

**Wie kommt es zu einem Konflikt?**

Konflikte finden sich im Protokoll „postupgrade.log“ auf dem betreffenden Server oder in der Client-Benutzeroberfläche von Campaign (Administration > Konfiguration > Paketverwaltung > Konflikte bearbeiten).

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
1. Untersuchen Sie den XML-Code aus dem Konflikt auf „_konflikt“-Attribute. Sieht es wie eine Anpassung aus?

**Wurde das Objekt im neuen Build geändert?**

1. Prüfen Sie die üblichen Verursacher: integrierte Web-Anwendungen oder Berichte (z. B.: &#39;deliveryValidation&#39;, &#39;deliveryOverview&#39;, &#39;budget&#39;).
1. Prüfen Sie die Änderungsprotokolle auf Updates.
1. Fragen Sie Adobe Campaign-Fachleute.
1. Führen Sie einen &quot;Diff&quot;-Befehl für den Code aus.

### Konflikt lösen

Gehen Sie wie folgt vor, um einen Konflikt zu lösen:

1. Gehen Sie im Adobe-Campaign-Explorer zu **Administration > Konfiguration > Packageverwaltung > Konflikte bearbeiten**.

1. Wählen Sie in der Liste den Konflikt aus, den Sie auflösen möchten.
Es gibt drei Optionen zum Beheben von Konflikten: **Neue Version akzeptieren**, **Aktuelle Version beibehalten**, **Code zusammenführen (und als aufgelöst deklarieren)** **Konflikt ignorieren (nicht empfohlen)**.

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
* Siehe [Durchführen einer Zusammenführung](#perform-a-merge).

**Was ist, wenn ich die Konflikte ignoriere?**

* Der Konflikt bleibt bestehen.
* Das Objekt wird nicht aktualisiert.
* Langfristige Auswirkungen: Inkompatibilität der Versionen, der Kunde profitiert nicht von Fehlerkorrekturen.

>[!IMPORTANT]
>Es wird dringend empfohlen, Konflikte zu lösen.
>

### Zusammenführung durchführen{#perform-a-merge}

Es gibt verschiedene Arten von Zusammenführungen:

1. Einfaches Zusammenführen: Benutzerdefinierte und neue Elemente sind klein und nicht verwandt, und es ist keine Codierung erforderlich.
1. Keine Änderungen: die neue Version wird akzeptiert, nur letztes Aktualisierungsdatum wurde geändert, nur Kommentare, Tabs, Leerzeichen oder neue Zeilen. Beispiel: irrtümliches Speichern.
1. Triviale Änderungen: nur eine einzige Zeile wurde geändert. Beispiel: xpathToLoad
1. Komplexe Zusammenführung: wenn Kodierung erforderlich ist. Entwicklungsfähigkeiten sind erforderlich. Siehe [Komplexe Zusammenführungen](#complex-merges).

#### Wie erfolgt die Zusammenführung?

1. Rufen Sie alle drei Versionen ab: die Originalversion, die neue Version und die benutzerdefinierte Version.
1. Führen Sie einen „Unterschied“ zwischen der ursprünglichen und der neuen Version aus.
1. Isolieren Sie die Änderungen.
1. Wenn keine Änderungen vorhanden sind, lösen Sie den Konflikt, indem Sie die aktuelle Version beibehalten.

#### Wo finden Sie den Code?

1. Der integrierte Code wird in XML-Dateien im Datakit-Ordner gespeichert. Suchen Sie die XML-Datei, die dem widersprüchlichen Objekt entspricht. Beispiel: installationDirectory\datakit\nms\fra\form\recipient.xml
1. Rufen Sie die Originalversion ab: über [Download-Center](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html) oder eine andere nicht aktualisierte Installation des Produkts.
1. Rufen Sie die neue Version ab: über [Download-Center](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) oder die installierten Dateien des Kunden.
1. Rufen Sie die benutzerdefinierte Version ab: Rufen Sie den Quellcode des Objekts vom Campaign-Client ab.

### Wie erstelle ich eine Diff-Datei?

1. Installieren Sie einen Text- oder Merge-Editor, z. B. Notepad ++, AraxisMerge oder WinMerge.
1. Öffnen Sie die Originaldatei und die neue Datei im Editor.
1. Führen Sie den Diff-Befehl aus (vergleichen Sie die beiden Dateien).
1. Stellen Sie etwaige Unterschiede fest.

### Wie erfolgt die Zusammenführung?

1. Beginnen Sie mit der benutzerdefinierten Version.
1. Wenden Sie die Änderungen an.
1. Lösen Sie den Konflikt, indem Sie ihn für gelöst erklären.
1. Auf Nicht-Regressionen prüfen.

Wenn Sie den Konflikt manuell lösen möchten, gehen Sie folgendermaßen vor:

1. Suchen Sie im unteren Abschnitt des Fensters nach der **_CONFLICT_STRING_**, um die Entitäten mit Konflikten zu finden. Die mit der neuen Version installierte Entität enthält das neue Argument, die mit der vorherigen Version übereinstimmende Entität enthält das benutzerdefinierte Argument.
1. Löschen Sie die Version, die Sie nicht behalten möchten. Löschen Sie die **_CONFLICT_ARGUMENT_**-Zeichenfolge der Entität, die Sie beibehalten.
1. Navigieren Sie zu dem Konflikt, den Sie gelöst haben. Klicken Sie auf **Aktionen** und wählen Sie **Als aufgelöst deklarieren** aus.
1. Speichern Sie Ihre Änderungen: Der Konflikt ist jetzt gelöst.

#### Komplexe Zusammenführungen{#complex-merges}

1. Machen Sie sich mit den Auswirkungen der Änderung vertraut: Reverse Engineering der Änderungen, Prüfung der Änderungsprotokolle, Follow-up mit Adobe Campaign-Experten.
1. Entscheide, was mit der Änderung geschehen soll.
1. Verstehen, was die Anpassungen bewirken: Änderungen zurückentwickeln

So nehmen Sie eine komplexe Zusammenführung vor:

1. Kopieren Sie Code-Bits aus dem Änderungssatz
1. In die angepasste Version einfügen
1. Testen auf Nicht-Regressionen der Anpassung
1. Testen der Funktion von Änderungen
1. Durchführen von Benutzerakzeptanztests
1. Führen Sie die Zusammenführung in einer Testumgebung durch.


>[!IMPORTANT]
>Für komplexe Zusammenführungen sind Entwicklungsfähigkeiten erforderlich.
>

**Verwandte Themen** 

* [Häufig gestellte Fragen zur Build-Aktualisierung](../../platform/using/faq-build-upgrade.md)
* [Versionshinweise zu Campaign Classic](../../rn/using/rn-overview.md)
* [Hilfe- und Support-Optionen für Campaign Classic](../../support.md)
* [Campaign-Programm mit jährlichen Aktualisierungen](../../rn/using/rn-overview.md)

---
title: Erste Schritte mit Build-Upgrades
description: Wichtige Schritte zum Aktualisieren auf einen neuen Build
page-status-flag: never-activated
uuid: f24552d4-6bdf-411c-a1f2-b8f339c311f4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: f8e3633d-7232-44a5-842b-1a70c4f2bca2
translation-type: tm+mt
source-git-commit: 849e1ebf14f707d9e86c5a152de978acb6f1cb35
workflow-type: tm+mt
source-wordcount: '2355'
ht-degree: 47%

---


# Durchführen eines Build-Upgrades{#performing-a-build-upgrade}

In diesem Abschnitt erhalten Sie eine ausführliche Anleitung zum Aktualisierungsprozess und zu den Schritten zur Ermittlung und Lösung von Konflikten.

Die Bauaufrüstung muss mit Vorsicht durchgeführt werden, ihre Auswirkungen müssen im Vorfeld umfassend berücksichtigt werden, und das Verfahren muss mit einem hohen Maß an Disziplin abgeschlossen werden. Um eine erfolgreiche Aktualisierung sicherzustellen, stellen Sie sicher, dass nur sachkundige Benutzer die unten beschriebenen Schritte ausführen. Darüber hinaus empfehlen wir dringend, sich vor dem Upgrade mit der [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) in Verbindung zu setzen.

Folgende Voraussetzungen müssen gegeben sein:

* Kenntnis der Campaign-Architektur
* Kenntnis der Systeme und Server
* Administratorrechte und Berechtigungen

Weitere Informationen finden Sie in den folgenden Abschnitten: [Aktualisieren von Adobe Campaign](../../production/using/upgrading.md), [Migration zu einer neuen Version](../../migration/using/about-migration.md).

For hosted and hybrid instances, you must request the build upgrade to Adobe Technical Operations team. For more on this, refer to the Frequently Asked Questions section at the bottom if this page. Also consult the [build upgrade FAQ](../../platform/using/faq-build-upgrade.md).

## Aktualisierung vorbereiten

![](assets/do-not-localize/icon_planification.png)

Bevor Sie die Build-Aktualisierung starten, müssen Sie eine vollständige Vorbereitung durchführen, wie unten beschrieben.
Sobald das System für die Aktualisierung bereit ist, dauert die Aktualisierung **mindestens** 2 Stunden.

Für die Build-Aktualisierung sind die folgenden Ressourcen erforderlch:

* ein Adobe Architect - um die Datenbankstrukturen (vordefinierte Schema und alle hinzugefügten zusätzlichen Schema, Entwürfe von Kampagnen und alle kritischen Pfadfunktionen, die in einer bestimmten Reihenfolge gestartet und getestet werden müssen) zu verstehen.
* ein Projektmanager - In Fällen, in denen die Build-Aktualisierung viele verschiedene Instanzen (Produktion, Staging, Testen) und andere Drittanbieter-Server und -Anwendungen (Datenbanken, SFTP-Sites, Messaging-Dienstleister) umfasst, wird der Einsatz eines Projektmanagers zur Koordinierung aller Tests als Best Practice erachtet.
* ein Adobe-Campaign-Administrator: Er kennt die Konfiguration des Servers, u. a. Anforderungen in Bezug auf Sicherheit, Ordneraufbau, Reporting und den Import und Export. Bitte nehmen Sie kein Build-Upgrade ohne Ihren Administrator vor.
* ein Adobe Campaign-Operator (Marketing-Benutzer) - eine erfolgreiche Aktualisierung hängt von der Fähigkeit des  ab, seine täglichen Aufgaben erfolgreich durchzuführen. Aus diesem Grund sollten Sie mindestens einen Ihrer täglichen Operatoren in Ihre Tests der aktualisierten Server einbeziehen.

### Planung

Dies sind die wichtigsten Schritte zur Planung eines Build-Upgrades:

1. Planen Sie mindestens zwei Stunden für das Upgrade ein.
1. Stellen Sie Kontaktdetails für Adobe- und Kundenmitarbeiter bereit.
1. Für gehostete Instanzen: die Adobe- und Kundenmitarbeiter bestimmen den Zeitpunkt des Upgrades sowie die Person, die ihn durchführt.
1. Für On-Premise-Instanzen: die Kundenmitarbeiter führen den gesamten Prozess aus. Wenn Hilfe beim Testen benutzerdefinierter Workflows und Sendungen benötigt wird, sollten Beratungsdienste in Anspruch genommen werden.
1. Determine and confirm which version of Adobe Campaign you want to upgrade to - consult the [Adobe Campaign Classic release notes](../../rn/using/rn-overview.md).
1. Bestätigen Sie das Vorhandensein ausführbarer Upgrade-Dateien.

### Wichtigste Mitarbeiter

Für den Prozess der Build-Aktualisierung müssen die folgenden Personen beteiligt sein:

* Adobe Architect: bei gehosteten oder hybriden Architekturen muss sich der Architekt mit dem Adobe Campaign Client Care abstimmen.

* Projektmanager:
   * für Installationen am Standort: Der interne Projektleiter des Kunden leitet die Aktualisierung und verwaltet Lebenszyklustests.

   * für gehostete Installation: das Hosting-Team wird mit dem Adobe Campaign Client Care-Team und dem Kunden zusammenarbeiten, um die Aktualisierungszeitschiene für alle Instanzen zu koordinieren.

* Adobe-Campaign-Administrator:
   * für Installationen am Standort: der Administrator führt die Aktualisierung durch.

   * für gehostete Installationen: das Hosting-Team die Aktualisierung durchführt.

* Adobe Campaign-Operator\Marketing-Benutzer: der Bediener führt Tests für Entwicklungs-, Test- und Produktionsinstanzen durch.

### Build-Aktualisierung vorbereiten

Vor Beginn der Build-Aktualisierung müssen lokale Kunden die folgende Vorbereitung durchführen:

1. Vergewissern Sie sich, dass alle Entwicklungsarbeiten exportiert werden können, bevor das Upgrade durchgeführt wird. Führen Sie den Export als Packages durch.

1. Führen Sie eine vollständige Sicherung der Datenbanken für alle Instanzen der Quell- und Zielgruppe-Umgebung durch.

1. Rufen Sie die neueste Version Ihrer [Serverkonfigurationsdatei](../../installation/using/the-server-configuration-file.md)ab.

1. Laden Sie die neueste Version herunter. [Erfahren Sie mehr über das Download-Center](https://docs.adobe.com/content/help/de-DE/experience-cloud/software-distribution/home.html).

You also need to know all the [useful command lines](../../installation/using/command-lines.md) before starting a build upgrade:

* **nlserver pdump**: listet aktuelle Prozesse auf
* **nlserver pdump -who**: listet aktive Client-Sitzungen auf
* **nlserver monitor -missing**: listet fehlende Eigenschaften auf
* **nlserver-Beginn process@instanceName**: beginn eines Prozesses
* **nlserver stop process@instanceName**: stoppt einen Prozess
* **nlserver-Neustart process@instanceName**: einen Prozess neu starten
* **nlserver herunterfahren**: stoppt alle Kampagnen
* **nlserver watchdog -svc**: startet den Watchdog-Prozess (nur UNIX)

## Führen Sie die Aktualisierung durch

![](assets/do-not-localize/icon_process.png)

Nachstehende Verfahren werden nur von **Kunden vor Ort** durchgeführt. Für gehostete Kunden wird dies vom Hosting-Team übernommen. Um Adobe Campaign auf einen neuen Build zu aktualisieren, wird das detaillierte Verfahren unten beschrieben.

### Duplikat der Umgebung

Hier sehen Sie, wie Sie eine Adobe Campaign-Umgebung, um eine Quell-Umgebung zu einer Zielgruppe Umgebung, die zu zwei identischen Arbeit Umgebung.

Gehen Sie dazu wie folgt vor:

1. Erstellen Sie eine Kopie der Datenbanken auf allen Instanzen in der Quellumgebung.

1. Stellen Sie diese Kopien auf allen Instanzen der Zielumgebung wieder her.

1. Führen Sie das Warnskript **nms:frizeInstance.js** auf der Umgebung Zielgruppe aus, bevor Sie es starten. Dadurch werden alle Prozesse gestoppt, die mit der Außenseite interagieren: Protokolle, Verfolgung, Versände, Kampagnen-Workflows usw.

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. Überprüfen Sie die Vorsicht wie folgt:

   * Check that the only delivery part is the one which ID is set to **0**:

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

Um alle Dateien mit der neuen Version zu ersetzen, müssen alle Instanzen von nlserverservice beendet werden.

1. Beenden Sie die folgenden Dienste:

   * Webdienste (IIS): **iisreset /stop**
   * Adobe-Campaign-Dienst: **net stop nlserver6**

   >[!NOTE]
   >
   >Stellen Sie sicher, dass der Umleitungsserver (webmdl) gestoppt wird, damit die von IIS verwendete Datei &quot;nlsrvmod.dll&quot;durch die neue Version ersetzt werden kann.

1. Validate that no tasks are active by running the **nlserver pdump** command. If there are no tasks, then the output should resemble the following:

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. Überprüfen Sie im Windows Aufgabe Manager, ob alle Vorgänge beendet wurden.

### Aktualisieren der Adobe Campaign Server-Anwendung

1. Führen Sie die Datei **Setup.exe** aus. Wenn Sie diese Datei herunterladen müssen, rufen Sie [das Download-Center](https://docs.adobe.com/content/help/de-DE/experience-cloud/software-distribution/home.html)auf.

1. Select the installation mode: **Update** or **Repair**.

1. Klicken Sie auf **Weiter**.

1. Wählen Sie **Beenden** aus: Die neue Datei wird vom Installationsprogramm kopiert.

1. Wählen Sie nach Abschluss des Vorgangs die Option **Beenden** aus.

### Ressourcen synchronisieren

1. Öffnen Sie die Befehlszeile.

1. Führen Sie **nlserver config -postupgrade -allinstances** aus, um Folgendes durchzuführen:

   * Ressourcen synchronisieren
   * Schemata aktualisieren
   * Datenbank aktualisieren

   >[!NOTE]
   >
   >Dieser Vorgang sollte nur einmal und nur auf einem nlserverweb-Anwendungsserver ausgeführt werden.

   Um nur eine Datenbank zu synchronisieren, führen Sie den folgenden Befehl aus:

   ```
   nlserver config -postupgrade -instance: <instance_name>
   ```

1. Überprüfen Sie, ob die Synchronisierung Fehler oder Warnungen hervorgerufen hat.

### Dienste wieder starten

Die folgenden Dienste müssen wieder gestartet werden:

* Webdienste (IIS): **issreset /start**
* Adobe-Campaign-Dienst: **net start nlserver6**

### Aktualisierung der Client-Konsolen

Laden Sie auf der Maschine, auf der der Adobe Campaign-Anwendungsserver installiert ist (nlserverweb), diese Datei herunter und kopieren Sie sie:

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```


Wenn das nächste Mal Clientkonsolen verbunden werden, werden die Benutzer darauf hingewiesen, dass eine neue Aktualisierung verfügbar ist, und erhalten die Möglichkeit, diese herunterzuladen und zu installieren.

### Spezifische zusätzliche Aufgaben

Einige Konfigurationen erfordern spezielle zusätzliche Aufgaben, um auf einen neuen Build zu aktualisieren.

#### Transaktionsnachrichtenversand

Wenn Transactional Messaging (Message Center) auf Ihrer Kampagne-Instanz aktiviert ist, müssen Sie die folgenden zusätzlichen Schritte ausführen, um eine Aktualisierung durchzuführen:

1. Aktualisieren Sie den Message-Center-Produktionsserver auf die gewünschte Version.
1. Führen Sie die Postupgrade-Scripts aus.
1. Führen Sie Tests durch und stellen Sie sicher, dass der E-Mail-Empfang über die Message-Center-Produktionsinstanz funktioniert.
1. Aktualisieren Sie die Clients und leeren Sie den Cache.
1. Packages exportieren:
   * Exportieren Sie Packages mit dem Client-Package-Export-Tool
   * Importieren Sie das Schema-Package
   * Melden Sie sich vom Client ab und wieder an
   * Aktualisieren Sie die Datenbank
   * Melden Sie sich ab und wieder an
   * Importieren Sie das Admin-Package
   * Importieren Sie das Content-Package
   * Importieren Sie das Content-Management-Package
   * Melden Sie sich ab und wieder an
   * Führen Sie eine kurze Prüfung der Workflows durch

1. Publizieren Sie Message-Center-Vorlagen, um sicherzugehen, dass die Schnittstelle zwischen den Servern und der Message-Center-Instanz funktioniert.
1. Führen Sie Tests durch, um sicherzustellen, dass E-Mails über die Produktionsinstanz des Message Center erfolgreich empfangen werden.
1. Führen Sie Workflow-Tests bei der Produktion durch, um sicherzugehen, dass der Nachrichtenempfang funktioniert.

#### Mid-Sourcing

Im Kontext einer Mid-Sourcing-Umgebung müssen Sie die folgenden zusätzlichen Schritte ausführen, um eine Aktualisierung durchzuführen:

1. Wenden Sie sich an die [Adobe Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) , um die Aktualisierung des Mid-Sourcing-Servers zu koordinieren.
1. Überprüfen Sie, ob die Version aktualisiert wurde, indem Sie einen Test-Link ausführen. Beispiel:

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>Der Mid-Sourcing-Server muss immer dieselbe Version (oder neuere Version) wie die Marketing-Server ausführen.


## Bei Konflikten

### Konflikte identifizieren

Sie müssen das Synchronisierungsergebnis überprüfen. Dieser Schritt wird nur von On-Premise-Kunden ausgeführt. Für gehostete Kunden übernimmt diese Aufgabe das Hosting-Team. Es gibt zwei Möglichkeiten, das Synchronisationsergebnis anzuzeigen:

In der Befehlszeilenschnittstelle werden Fehler durch ein dreifaches chevron &quot;>>&quot;eingetreten und die Synchronisierung wird automatisch beendet. Warnungen werden durch eine Dublette chevron &#39;>>&#39; materialisiert und müssen nach Abschluss der Synchronisierung aufgelöst werden. Am Ende der Aktualisierung wird an der Eingabeaufforderung eine Zusammenfassung angezeigt. Es kann wie folgt aussehen:

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

Wenn ein Warnhinweis aufgrund eines Konflikts von Ressourcen ausgegeben wird, muss ihn der Benutzer lösen.

Die Datei **postupgrade_ServerVersionNumber_TimeOfPostupgrade.log** enthält das Synchronisierungsergebnis. Er ist standardmäßig im folgenden Verzeichnis verfügbar: **installationDirectory/var/instanceName/postupgrade**. Fehler und Warnungen werden durch die Fehler- und Warnattribute angezeigt.

### Konflikte analysieren

**Wie wird ein Konflikt festgestellt?**

Konflikte werden in der Datei postupgrade.log auf dem jeweiligen Server oder innerhalb der Adobe-Campaign-Clientkonsole festgestellt (Administration > Konfiguration > Packageverwaltung > Konflikte bearbeiten).

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
1. Prüfen Sie den XML-Code des Konflikts auf “_conflict”-Attribute. Sieht es nach einer Personalisierung aus?

**Wurde das Objekt im neuen Build geändert?**

1. Prüfen Sie die üblichen Verursacher: integrierte Web-Anwendungen oder Berichte (z. B.: &#39;deliveryValidation&#39;, &#39;deliveryOverview&#39;, &#39;budget&#39;).
1. Prüfen Sie die Änderungsprotokolle auf Updates.
1. Fragen Sie Adobe Campaign-Experten.
1. Führen Sie einen &quot;Diff&quot;-Befehl für den Code aus.

### Beheben eines Konflikts

Gehen Sie wie folgt vor, um einen Konflikt zu lösen:

1. Gehen Sie im Adobe-Campaign-Explorer zu **Administration > Konfiguration > Packageverwaltung > Konflikte bearbeiten**.

1. Wählen Sie in der Liste den Konflikt aus, den Sie lösen möchten.
Es gibt drei Optionen zur Lösung von Konflikten: **Akzeptieren Sie die neue Version**, **behalten Sie die aktuelle Version**, **Merge the code (und deklarieren Sie als aufgelöst)**, **ignorieren Sie den Konflikt (nicht empfohlen)**.

**Wann kann ich die neue Version akzeptieren?**

* Wenn Sie die Standardfunktionen beibehalten möchten.
* Wenn Sie keine Personalisierungen durchgeführt haben (alle Personalisierungen werden entfernt)

**Wann kann ich die aktuelle Version beibehalten?**

* Wenn Sie Personalisierungen durchgeführt haben
* Wenn Sie keine Zusammenführung durchführen möchten
* Wenn Sie das Konflikt auslösende Objekt nicht im Postupgrade korrigieren müssen

**Wann soll ich eine Zusammenführung durchführen?**

* Nur Formulare, Berichte und Webanwendungen können zusammengeführt werden.
* Einige geringfügige Zusammenführungen können durchgeführt werden, ohne den Code zu verstehen.
* Kompliziertere Zusammenführungen sollten jedoch von einer Fachkraft durchgeführt werden.
* Siehe [Durchführen einer Zusammenführung](#perform-a-merge).

**Was passiert, wenn ich Konflikte ignoriere?**

* Der Konflikt bleibt bestehen.
* Das Objekt wird nicht aktualisiert.
* Langfristige Auswirkungen: Inkompatibilität der Versionen, der Kunde profitiert nicht von Fehlerkorrekturen.

>[!IMPORTANT]
>Es wird dringend empfohlen, Konflikte zu lösen.


### Zusammenführen{#perform-a-merge}

Es gibt verschiedene Arten von Zusammenführungen:

1. Einfache Zusammenführung: benutzerdefinierte und neue Elemente sind klein und unabhängig voneinander, und es ist keine Kodierung erforderlich.
1. Keine Änderungen: die neue Version wird akzeptiert, nur letztes Aktualisierungsdatum wurde geändert, nur Kommentare, Tabs, Leerzeichen oder neue Zeilen. Beispiel: irrtümliches Speichern.
1. Triviale Änderungen: nur eine einzige Zeile wurde geändert. Beispiel: xpathToLoad
1. Kompliziertes Zusammenführen: wenn Code geschrieben werden muss. Entwicklerkenntnisse sind erforderlich. Siehe [Komplexe Zusammenführungen](#complex-merges).

#### Wie erfolgt die Zusammenführung?

1. Alle drei Versionen abrufen: die Originalversion, die neue Version und die benutzerdefinierte Version.
1. Führen Sie einen &quot;diff&quot; zwischen der ursprünglichen und der neuen Version aus.
1. Isolieren Sie die Änderungen.
1. Wenn keine Änderungen vorhanden sind, lösen Sie den Konflikt, indem Sie die aktuelle Version beibehalten.

#### Wo finden Sie den Code?

1. Integrierter Code wird in XML-Dateien im Ordner &quot;datakit&quot;gespeichert. Suchen Sie die XML-Datei, die mit dem Objekt übereinstimmt, das den Konflikt verursacht. Beispiel: installationDirectory\datakit\nms\fra\form\recipient.xml
1. Die Originalversion abrufen: über das [Download-Center](https://docs.adobe.com/content/help/de-DE/experience-cloud/software-distribution/home.html) oder eine andere nicht aktualisierte Installation des Produkts.
1. Die neue Version abrufen: über das [Download-Center](https://docs.adobe.com/content/help/de-DE/experience-cloud/software-distribution/home.html) oder die vom Kunden installierten Dateien.
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
1. Suchen Sie nach Nicht-Regressionen.

Wenn Sie den Konflikt manuell lösen möchten, gehen Sie folgendermaßen vor:

1. In the lower section of the window, search for the **_conflict_string_** to locate the entities with conflicts. The entity installed with the new version contains the new argument, the entity that matches the previous version contains the custom argument.
1. Delete the version you don&#39;t want to keep. Delete the **_conflict_argument_** string of the entity you are keeping.
1. Gehen Sie zum gelösten Konflikt. Klicken Sie auf das Symbol **Aktionen** und wählen Sie **Als gelöst deklarieren** aus.
1. Speichern Sie Ihre Änderungen: Der Konflikt ist jetzt gelöst.

#### Komplexe Zusammenführungen{#complex-merges}

1. Verstehen Sie, was die Änderung bewirkt: Reverse-Engineering der Änderungen, überprüfen Sie die Änderungsprotokolle, folgen Sie mit Adobe Campaign-Experten.
1. Entscheide, was mit der Änderung zu tun ist.
1. Machen Sie sich mit den Anpassungen vertraut: Reverse-Engineering der Änderungen

So nehmen Sie eine komplexe Zusammenführung vor:

1. Kopieren Sie Code aus der geänderten Version
1. Fügen Sie ihn in die benutzerdefinierte Version ein
1. Test auf Nichtregressionen der Anpassung
1. Überprüfen Sie die Funktionsfähigkeit der Änderungen
1. Benutzerakzeptanztests durchführen
1. Führen Sie die Zusammenführung in einer Testumgebung durch.


>[!IMPORTANT]
>Für komplexe Zusammenführungen sind Entwicklungskenntnisse erforderlich.


**Verwandte Themen**

* [Häufig gestellte Fragen zur Aktualisierung](../../platform/using/faq-build-upgrade.md)
* [Versionshinweise zu Campaign Classic ](../../rn/using/rn-overview.md)
* [Hilfe- und Supportoptionen für Campaign Classic](https://helpx.adobe.com/campaign/kb/ac-support.html#acc-support-req)
* [Gold Standard-Programm](https://helpx.adobe.com/de/campaign/kb/gold-standard.html)
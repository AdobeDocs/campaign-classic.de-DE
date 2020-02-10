---
title: Duplizieren von Umgebungen
seo-title: Duplizieren von Umgebungen
description: Duplizieren von Umgebungen
seo-description: null
page-status-flag: never-activated
uuid: b8fb8083-e3ec-4b1c-9449-73ac03508d89
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 9f7118f4-aef0-469c-bbe1-b62bed674faa
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 779d9162b7296339a796512838612ede1186ddcc

---


# Duplizieren von Umgebungen{#duplicating-environments}

## Einleitung {#introduction}

### Übersicht {#overview}

>[!CAUTION]
>
>Wenn Sie keinen Zugriff auf den Server und die Datenbank (gehostete Umgebungen) haben, können Sie die unten beschriebenen Verfahren nicht durchführen. Wenden Sie sich an Adobe.

Für die Verwendung von Adobe Campaign ist die Installation und Konfiguration einer oder mehrerer Umgebungen erforderlich: Entwicklung, Prüfung, Vorproduktion, Produktion usw.

Jede Umgebung enthält eine Adobe Campaign-Instanz und jede Adobe Campaign-Instanz ist mit einer oder mehreren Datenbanken verknüpft. Der Anwendungsserver kann einen oder mehrere Prozesse ausführen: Fast alle haben direkten Zugriff auf die Instanzdatenbank.

In diesem Abschnitt werden die Prozesse beschrieben, die auf die Duplizierung einer Adobe Campaign-Umgebung angewendet werden sollen, d. h. um eine Quellumgebung in einer Zielumgebung wiederherzustellen, was zu zwei identischen Arbeitsumgebungen führt.

Gehen Sie hierzu wie folgt vor:

1. Erstellen Sie eine Kopie der Datenbanken auf allen Instanzen in der Quellumgebung,
1. Stellen Sie diese Kopien auf allen Instanzen der Zielumgebung wieder her,
1. Führen Sie das Warnskript **nms:frizeInstance.js** in der Zielumgebung aus, bevor Sie es starten.

   Dieser Prozess hat keine Auswirkungen auf die Server und deren Konfiguration.

   >[!NOTE]
   >
   >Im Kontext von Adobe Campaign kombiniert eine **Warnung** Aktionen, mit denen Sie alle Prozesse stoppen können, die mit der Außenseite interagieren: Protokolle, Verfolgung, Auslieferungen, Kampagnen-Workflows usw.\
   >Dieser Schritt ist notwendig, um zu vermeiden, dass Nachrichten mehrmals gesendet werden (einmal aus der nominalen Umgebung und einmal aus der duplizierten Umgebung).

   >[!CAUTION]
   >
   >Eine Umgebung kann mehrere Instanzen enthalten. Jede Adobe Campaign-Instanz unterliegt einem Lizenzvertrag. Überprüfen Sie Ihre Lizenzvereinbarung, um zu sehen, wie viele Umgebungen Sie nutzen können.\
   >Mit dem unten beschriebenen Verfahren können Sie eine Umgebung übertragen, ohne die Anzahl der installierten Umgebungen und Instanzen zu beeinträchtigen.

### Bevor Sie beginnen {#before-you-start}

>[!CAUTION]
>
>Es wird dringend empfohlen, eine vollständige Sicherung der Datenbanken für alle Instanzen der Quell- und Zielumgebungen auszuführen, bevor der Transfer gestartet wird. Auf diese Weise können Sie bei einem Problem die Backups wiederherstellen und zur ursprünglichen Konfiguration zurückkehren.

Damit dieser Prozess ausgeführt werden kann, müssen die Quell- und Zielumgebungen über dieselbe Anzahl von Instanzen, denselben Zweck (Marketing-Instanz, Bereitstellungsinstanz) und ähnliche Konfigurationen verfügen. Die technische Konfiguration muss den Softwarevoraussetzungen entsprechen. Dieselben Komponenten müssen in beiden Umgebungen installiert werden.

## Umsetzung {#implementation}

### Transferverfahren {#transfer-procedure}

In diesem Abschnitt erfahren Sie, wie Sie mithilfe einer Fallstudie eine Quellumgebung in eine Zielumgebung übertragen können: Unser Ziel ist es hier, eine Produktionsumgebung (**prod** -Instanz) in einer Entwicklungsumgebung (**dev** -Instanz) wiederherzustellen, um in einem Kontext zu arbeiten, der der &quot;live&quot; Plattform so nahe wie möglich ist.

Die folgenden Schritte müssen mit größter Sorgfalt durchgeführt werden: Einige Prozesse werden möglicherweise noch ausgeführt, wenn die Quellumgebung-Datenbanken kopiert werden. Durch die Vorsicht (Schritt 3 unten) wird verhindert, dass Nachrichten zweimal gesendet werden, und die Datenkonsistenz bleibt erhalten.

>[!CAUTION]
>
>* Das folgende Verfahren ist in der Sprache PostgreSQL gültig. Wenn die SQL-Sprache unterschiedlich ist (z. B. Oracle), müssen die SQL-Abfragen angepasst werden.
>* Die folgenden Befehle gelten im Kontext einer **prod** -Instanz und einer **dev** -Instanz unter PostgreSQL.
>



### Schritt 1 - Erstellen einer Sicherung der Quellumgebung (Prod)-Daten {#step-1---make-a-backup-of-the-source-environment--prod--data}

Datenbanken kopieren

Kopieren Sie zunächst alle Quellumgebung-Datenbanken. Der Vorgang ist von der Datenbank-Engine abhängig und unterliegt der Verantwortung des Datenbankadministrators.

Unter PostgreSQL lautet der Befehl:

```
pg_dump mydatabase > mydatabase.sql
```

### Schritt 2: Exportieren der Konfiguration der Zielumgebung (dev) {#step-2---export-the-target-environment-configuration--dev-}

Die meisten Konfigurationselemente unterscheiden sich je nach Umgebung: externe Konten (Mid-Sourcing, Routing usw.), technische Optionen (Plattformname, DatabaseId, E-Mail-Adressen und Standard-URLs usw.).

Bevor Sie die Quelldatenbank in der Zieldatenbank speichern, müssen Sie die Konfiguration der Zielumgebung (dev) exportieren. Exportieren Sie dazu den Inhalt dieser beiden Tabellen: **xtkoption** und **nmsextaccount**.

Mit diesem Export können Sie die Dev-Konfiguration beibehalten und nur die Dev-Daten (Workflows, Vorlagen, Webanwendungen, Empfänger usw.) aktualisieren.

Führen Sie dazu einen Paketexport für die folgenden beiden Elemente durch:

* Exportieren Sie die Tabelle &quot; **xtk:option** &quot;in eine Datei &quot;options_dev.xml&quot;ohne die Datensätze mit den folgenden internen Namen: &#39;WdbcTimeZone&#39;, &#39;NmsServer_LastPostUpgrade&#39; und &#39;NmsBroadcast_RegexRules&#39;.
* Exportieren Sie in einer Datei &quot;extaccount_dev.xml&quot;die Tabelle **nms:extAccount** für alle Datensätze, deren ID nicht 0 (@id &lt;> 0) ist.

Überprüfen Sie, ob die Anzahl der exportierten Optionen/Konten der Anzahl der Zeilen entspricht, die in jeder Datei exportiert werden sollen.

>[!NOTE]
>
>Die Anzahl der zu exportierenden Zeilen in einem Paketexport beträgt 1000 Zeilen. Wenn die Anzahl der Optionen oder externen Konten mehr als 1000 beträgt, müssen Sie mehrere Exporte durchführen.
> 
>Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../platform/using/working-with-data-packages.md#exporting-packages).

### Schritt 3: Beenden der Zielumgebung (dev) {#step-3---stop-the-target-environment--dev-}

Sie müssen Adobe Campaign-Prozesse auf allen Servern der Zielumgebung beenden. Dieser Vorgang ist vom Betriebssystem abhängig.

Sie können alle Prozesse oder nur die Prozesse beenden, die in die Datenbank schreiben.

Verwenden Sie zum Beenden aller Prozesse die folgenden Befehle:

* Windows:

   ```
   net stop nlserver6
   ```

* Unter Linux:

   ```
   /etc/init.d/nlserver6 stop
   ```

Verwenden Sie den folgenden Befehl, um zu überprüfen, ob alle Prozesse beendet wurden:

```
nlserver pdump
```

>[!NOTE]
>
>Unter Windows kann der **webmdl** -Prozess weiterhin aktiv sein, ohne andere Vorgänge zu beeinträchtigen.

Sie können auch überprüfen, ob noch keine Systemprozesse ausgeführt werden.

Gehen Sie dazu wie folgt vor:

* Windows: Öffnen Sie den **Task-Manager** und überprüfen Sie, ob es keine **nlserver.exe** -Prozesse gibt.
* Unter Linux: Führen Sie die **ps aux aus| grep nlserver** Befehl und überprüfen Sie, ob es keine **nlserver** -Prozesse gibt.

### Schritt 4: Wiederherstellen der Datenbanken in der Zielumgebung (dev) {#step-4---restore-the-databases-in-the-target-environment--dev-}

Verwenden Sie den folgenden Befehl, um die Quelldatenbanken in der Zielumgebung wiederherzustellen:

```
psql mydatabase < mydatabase.sql
```

### Schritt 5: Vorsicht bei der Zielumgebung (dev) {#step-5---cauterize-the-target-environment--dev-}

Um Funktionsstörungen zu vermeiden, dürfen die Prozesse, die mit dem Senden und der Ausführung des Workflows verknüpft sind, nicht automatisch ausgeführt werden, wenn die Zielumgebung aktiviert wird.

Führen Sie dazu den folgenden Befehl aus:

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### Schritt 6: Vorsicht überprüfen {#step-6---check-cauterization}

1. Vergewissern Sie sich, dass der einzige Auslieferungsabschnitt derjenige ist, dessen ID auf 0 gesetzt ist:

   ```
   SELECT * FROM neolane.nmsdeliverypart;
   ```

1. Vergewissern Sie sich, dass die Versandstatus-Aktualisierung korrekt ist:

   ```
   SELECT iState, count(*) FROM neolane.nmsdelivery GROUP BY iState;
   ```

1. Vergewissern Sie sich, dass die Workflow-Status-Aktualisierung korrekt ist:

   ```
   SELECT iState, count(*) FROM neolane.xtkworkflow GROUP BY iState;
   SELECT iStatus, count(*) FROM neolane.xtkworkflow GROUP BY iStatus;
   ```

### Schritt 7: Webprozess der Zielumgebung neu starten (dev) {#step-7---restart-the-target-environment-web-process--dev-}

Starten Sie in der Zielumgebung die Adobe Campaign-Prozesse für alle Server neu.

>[!NOTE]
>
>Bevor Sie Adobe Campaign in der **dev** -Umgebung neu starten, können Sie ein zusätzliches Sicherheitsverfahren anwenden: nur das **Webmodul** starten.
>  
>Bearbeiten Sie dazu die Konfigurationsdatei Ihrer Instanz (**config-dev.xml**) und fügen Sie dann das Zeichen &quot;_&quot;vor den Optionen autoStart=&quot;true&quot;für jedes Modul (mta, stat usw.) hinzu.

Führen Sie den folgenden Befehl aus, um den Webprozess zu starten:

```
nlserver start web
```

Verwenden Sie den folgenden Befehl, um zu überprüfen, dass nur der Webprozess gestartet wurde:

```
nlserver pdump
```

Überprüfen Sie, ob der Zugriff auf die Funktionen der Client-Konsole möglich ist.

### Schritt 8: Optionen und externe Konten in die Zielumgebung (dev) importieren {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!CAUTION]
>
>In diesem Schritt sollte nur der Webprozess gestartet werden. Ist dies nicht der Fall, beenden Sie andere laufende Prozesse, bevor Sie fortfahren

Überprüfen Sie vor allem die Werte mehrerer Zeilen der Dateien, bevor Sie sie importieren (z. B.: &#39;NmsTracking_Zeiinter&#39; für die Optionstabelle und die Auslieferungs- oder Mid-Sourcing-Konten für die Tabelle des externen Kontos)

So importieren Sie die Konfiguration aus der Zielumgebungsdatenbank (dev):

1. Öffnen Sie die Admin-Konsole der Datenbank und leeren Sie die externen Konten (Tabelle nms:extAccount), deren ID nicht 0 (@id &lt;> 0) ist.
1. Importieren Sie in der Adobe Campaign-Konsole das Paket options_dev.xml, das zuvor über die Importpaket-Funktionalität erstellt wurde.

   Vergewissern Sie sich, dass die Optionen tatsächlich im **[!UICONTROL Administration > Platform > Options]** Knoten aktualisiert wurden.

1. Importieren Sie in die Adobe Campaign-Konsole die Datei &quot;extaccount_dev.xml&quot;, die Sie zuvor über die Importpaket-Funktion erstellt haben.

   Überprüfen Sie, ob externe Datenbanken tatsächlich in der importiert wurden **[!UICONTROL Administration > Platform > External accounts]** .

### Schritt 9: Alle Prozesse neu starten und Benutzer ändern (dev) {#step-9---restart-all-processes-and-change-users--dev-}

Verwenden Sie zum Starten der Adobe Campaign-Prozesse die folgenden Befehle:

* Windows:

   ```
   net start nlserver6
   ```

* Unter Linux:

   ```
   /etc/init.d/nlserver6 start
   ```

Verwenden Sie den folgenden Befehl, um zu überprüfen, ob die Prozesse gestartet wurden:

```
nlserver pdump
```

Ändern Sie Benutzer, um die Benutzer zu suchen, die bereits auf der dev-Plattform vorhanden waren.

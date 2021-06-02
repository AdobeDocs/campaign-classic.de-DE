---
product: campaign
title: Duplizieren von Umgebungen
description: Duplizieren von Umgebungen
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 2c933fc5-1c0a-4c2f-9ff2-90d09a79c55a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 5%

---

# Duplizieren von Umgebungen{#duplicating-environments}

## Einleitung {#introduction}

### Übersicht {#overview}

>[!IMPORTANT]
>
>Wenn Sie keinen Zugriff auf den Server und die Datenbank (gehostete Umgebungen) haben, können Sie die unten beschriebenen Verfahren nicht durchführen. Bitte kontaktieren Sie die Adobe.

Die Verwendung von Adobe Campaign erfordert die Installation und Konfiguration einer oder mehrerer Umgebungen: Entwicklung, Tests, Vorproduktion, Produktion usw.

Jede Umgebung enthält eine Adobe Campaign-Instanz und jede Adobe Campaign-Instanz ist mit einer oder mehreren Datenbanken verknüpft. Der Anwendungsserver kann einen oder mehrere Prozesse ausführen: Fast alle haben direkten Zugriff auf die Instanzdatenbank.

In diesem Abschnitt werden die Prozesse beschrieben, die auf das Duplizieren einer Adobe Campaign-Umgebung angewendet werden sollen, d. h. um eine Quellumgebung in einer Zielumgebung wiederherzustellen, was zu zwei identischen Arbeitsumgebungen führt.

Gehen Sie hierzu wie folgt vor:

1. Erstellen Sie eine Kopie der Datenbanken auf allen Instanzen in der Quellumgebung,
1. Stellen Sie diese Kopien auf allen Instanzen der Zielumgebung wieder her,
1. Führen Sie das Warnskript **nms:freezeInstance.js** in der Zielumgebung aus, bevor Sie es starten.

   Dieser Prozess hat keine Auswirkungen auf die Server und deren Konfiguration.

   >[!NOTE]
   >
   >Im Kontext von Adobe Campaign werden bei einer **Bluterguss** Aktionen kombiniert, die es ermöglichen, alle Prozesse zu stoppen, die mit der Außenwelt interagieren: Protokolle, Tracking, Sendungen, Kampagnen-Workflows usw.\
   >Dieser Schritt ist erforderlich, um zu verhindern, dass Nachrichten mehrmals gesendet werden (einmal in der nominalen Umgebung und einmal in der duplizierten Umgebung).

   >[!IMPORTANT]
   >
   >Eine Umgebung kann mehrere Instanzen enthalten. Jede Adobe Campaign-Instanz unterliegt einem Lizenzvertrag. Überprüfen Sie Ihren Lizenzvertrag, um zu sehen, wie viele Umgebungen Sie nutzen können.\
   >Mit dem unten beschriebenen Verfahren können Sie eine Umgebung übertragen, ohne die Anzahl der installierten Umgebungen und Instanzen zu beeinträchtigen.

### Bevor Sie {#before-you-start} starten

>[!IMPORTANT]
>
>Es wird dringend empfohlen, eine vollständige Sicherung der Datenbanken für alle Instanzen der Quell- und Zielumgebungen durchzuführen, bevor der Übertragungsprozess gestartet wird. Auf diese Weise können Sie, wenn ein Problem auftritt, die Backups wiederherstellen und zu Ihrer ursprünglichen Konfiguration zurückkehren.

Damit dieser Prozess funktioniert, müssen die Quell- und Zielumgebungen über dieselbe Anzahl von Instanzen, denselben Zweck (Marketing-Instanz, Versandinstanz) und ähnliche Konfigurationen verfügen. Die technische Konfiguration muss den Softwarevoraussetzungen entsprechen. Dieselben Komponenten müssen in beiden Umgebungen installiert sein.

## Umsetzung {#implementation}

### Übertragungsverfahren {#transfer-procedure}

In diesem Abschnitt erfahren Sie, wie Sie mithilfe einer Fallstudie eine Quellumgebung in eine Zielumgebung übertragen können: Unser Ziel besteht hier darin, eine Produktionsumgebung (**prod** Instanz) in einer Entwicklungsumgebung (**dev** Instanz) wiederherzustellen, um in einem Kontext zu arbeiten, der der &quot;Live&quot;-Plattform so nahe wie möglich ist.

Die folgenden Schritte müssen mit großer Sorgfalt ausgeführt werden: Einige Prozesse werden möglicherweise noch ausgeführt, wenn die Datenbanken der Quellumgebung kopiert werden. Durch die Vorsicht (Schritt 3 unten) wird verhindert, dass Nachrichten zweimal gesendet werden, und die Datenkonsistenz wird gewahrt.

>[!IMPORTANT]
>
>* Das folgende Verfahren ist in der Sprache PostgreSQL gültig. Wenn die SQL-Sprache unterschiedlich ist (z. B. Oracle), müssen die SQL-Abfragen angepasst werden.
>* Die folgenden Befehle gelten im Kontext einer **prod**-Instanz und einer **dev**-Instanz unter PostgreSQL.

>



### Schritt 1: Erstellen Sie eine Sicherung der Quellumgebungsdaten (prod) {#step-1---make-a-backup-of-the-source-environment--prod--data}

Datenbanken kopieren

Kopieren Sie zunächst alle Quellumgebungsdatenbanken. Der Vorgang hängt von der Datenbank-Engine ab und liegt in der Verantwortung des Datenbankadministrators.

Unter PostgreSQL lautet der Befehl:

```
pg_dump mydatabase > mydatabase.sql
```

### Schritt 2: Exportieren der Zielumgebungskonfiguration (dev) {#step-2---export-the-target-environment-configuration--dev-}

Die meisten Konfigurationselemente unterscheiden sich für jede Umgebung: externe Konten (Mid-Sourcing, Routing usw.), technische Optionen (Plattformname, DatabaseId, E-Mail-Adressen und Standard-URLs usw.).

Vor dem Speichern der Quelldatenbank in der Zieldatenbank müssen Sie die Konfiguration der Zielumgebung (dev) exportieren. Exportieren Sie dazu den Inhalt dieser beiden Tabellen: **xtkoption** und **nmsextaccount**.

Mit diesem Export können Sie die Entwicklungskonfiguration beibehalten und nur Entwicklungsdaten (Workflows, Vorlagen, Webanwendungen, Empfänger usw.) aktualisieren.

Führen Sie dazu einen Package-Export für die folgenden beiden Elemente durch:

* Exportieren Sie die Tabelle **xtk:option** in eine Datei &quot;options_dev.xml&quot;, ohne dass die Datensätze die folgenden internen Namen aufweisen: &#39;WdbcTimeZone&#39;, &#39;NmsServer_LastPostUpgrade&#39; und &#39;NmsBroadcast_RegexRules&#39;.
* Exportieren Sie in einer Datei &quot;extaccount_dev.xml&quot;die Tabelle **nms:extAccount** für alle Datensätze, deren Kennung nicht 0 ist (@id &lt;> 0).

Überprüfen Sie, ob die Anzahl der exportierten Optionen/Konten der Anzahl der Zeilen entspricht, die in jeder Datei exportiert werden sollen.

>[!NOTE]
>
>Die Anzahl der zu exportierenden Zeilen in einem Package-Export beträgt 1000 Zeilen. Bei mehr als 1000 Optionen oder externen Konten müssen mehrere Exporte durchgeführt werden.
> 
>Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../platform/using/working-with-data-packages.md#exporting-packages).

>[!NOTE]
>
>Beim Exportieren der nmsextaccount -Tabelle werden Kennwörter, die sich auf externe Konten beziehen (z. B. Kennwörter für Mid-Sourcing, Message Center Execution, SMPP, IMS und andere externe Konten), nicht exportiert. Vergewissern Sie sich im Voraus, dass Sie Zugriff auf die richtigen Passwörter haben, da diese möglicherweise erneut eingegeben werden müssen, nachdem die externen Konten wieder in die Umgebung importiert wurden.

### Schritt 3: Stoppen der Zielumgebung (dev) {#step-3---stop-the-target-environment--dev-}

Sie müssen Adobe Campaign-Prozesse auf allen Zielumgebungsservern stoppen. Dieser Vorgang hängt von Ihrem Betriebssystem ab.

Sie können alle Prozesse stoppen, oder nur die Prozesse, die in die Datenbank schreiben.

Verwenden Sie die folgenden Befehle, um alle Prozesse zu beenden:

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
>Unter Windows kann der Prozess **webmdl** weiterhin aktiv sein, ohne andere Vorgänge zu beeinträchtigen.

Sie können auch überprüfen, ob noch keine Systemprozesse ausgeführt werden.

Gehen Sie dazu wie folgt vor:

* Windows: Öffnen Sie den **Task Manager** und überprüfen Sie, ob keine **nlserver.exe**-Prozesse vorhanden sind.
* Unter Linux: Führen Sie die **ps-aux aus. | grep nlserver** Befehl und vergewissern Sie sich, dass keine **nlserver**-Prozesse vorhanden sind.

### Schritt 4: Wiederherstellen der Datenbanken in der Zielumgebung (dev) {#step-4---restore-the-databases-in-the-target-environment--dev-}

Verwenden Sie den folgenden Befehl, um die Quelldatenbanken in der Zielumgebung wiederherzustellen:

```
psql mydatabase < mydatabase.sql
```

### Schritt 5: Vorsicht bei der Zielumgebung (dev) {#step-5---cauterize-the-target-environment--dev-}

Um Fehlfunktionen zu vermeiden, dürfen Prozesse im Zusammenhang mit dem Versand und der Ausführung des Workflows bei der Aktivierung der Zielumgebung nicht automatisch ausgeführt werden.

Führen Sie dazu den folgenden Befehl aus:

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### Schritt 6: Überprüfen der Vorsicht {#step-6---check-cauterization}

1. Vergewissern Sie sich, dass der einzige Versandabschnitt derjenige ist, dessen Kennung auf 0 gesetzt ist:

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

### Schritt 7: Starten Sie den Webprozess der Zielumgebung (dev) {#step-7---restart-the-target-environment-web-process--dev-} neu.

Starten Sie in der Zielumgebung die Adobe Campaign-Prozesse für alle Server neu.

>[!NOTE]
>
>Bevor Sie Adobe Campaign in der **dev**-Umgebung neu starten, können Sie ein zusätzliches Sicherheitsverfahren anwenden: Starten Sie nur das Modul **web** .
>  
>Bearbeiten Sie dazu die Konfigurationsdatei Ihrer Instanz (**config-dev.xml**) und fügen Sie dann das Zeichen &quot;_&quot;vor den Optionen autoStart=&quot;true&quot; für jedes Modul (mta, stat usw.) hinzu.

Führen Sie den folgenden Befehl aus, um den Webprozess zu starten:

```
nlserver start web
```

Verwenden Sie den folgenden Befehl, um zu überprüfen, ob nur der Webprozess gestartet wurde:

```
nlserver pdump
```

Überprüfen Sie, ob der Zugriff auf die Clientkonsole funktioniert.

### Schritt 8: Importieren von Optionen und externen Konten in die Zielumgebung (dev) {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!IMPORTANT]
>
>In diesem Schritt sollte nur der Webprozess gestartet werden. Ist dies nicht der Fall, beenden Sie andere laufende Prozesse, bevor Sie fortfahren

Überprüfen Sie vor allem die Werte mehrerer Zeilen der Dateien, bevor Sie importieren (z. B.: &#39;NmsTracking_Pointer&#39; für die Optionstabelle und die Versand- oder Mid-Sourcing-Konten für die Tabelle des externen Kontos)

So importieren Sie die Konfiguration aus der Zielumgebungsdatenbank (dev):

1. Öffnen Sie die Admin Console der Datenbank und bereinigen Sie die externen Konten (Tabelle nms:extAccount), deren Kennung nicht 0 (@id &lt;> 0) ist.
1. Importieren Sie in der Adobe Campaign-Konsole das Package options_dev.xml , das Sie zuvor über die Package-Import-Funktion erstellt haben.

   Überprüfen Sie, ob die Optionen tatsächlich im Knoten **[!UICONTROL Administration > Plattform > Optionen]** aktualisiert wurden.

1. Importieren Sie in der Adobe Campaign-Konsole die zuvor über die Import-Paketfunktion erstellte Datei &quot;extaccount_dev.xml&quot;.

   Überprüfen Sie, ob externe Datenbanken tatsächlich in **[!UICONTROL Administration > Plattform > Externe Konten]** importiert wurden.

### Schritt 9: Alle Prozesse neu starten und Benutzer ändern (dev) {#step-9---restart-all-processes-and-change-users--dev-}

Verwenden Sie die folgenden Befehle, um die Adobe Campaign-Prozesse zu starten:

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

Ändern Sie Benutzer, um die Benutzer zu finden, die bereits auf der Entwicklungsplattform vorhanden waren.

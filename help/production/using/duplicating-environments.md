---
product: campaign
title: Duplizieren von Umgebungen
description: Duplizieren von Umgebungen
feature: Monitoring
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 2c933fc5-1c0a-4c2f-9ff2-90d09a79c55a
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '1318'
ht-degree: 4%

---

# Duplizieren von Umgebungen{#duplicating-environments}



## Einleitung {#introduction}

### Übersicht {#overview}

>[!IMPORTANT]
>
>Wenn Sie keinen Zugriff auf den Server und die Datenbank (gehostete Umgebungen) haben, können Sie die unten beschriebenen Verfahren nicht ausführen. Bitte kontaktieren Sie Adobe.

Die Verwendung von Adobe Campaign erfordert die Installation und Konfiguration einer oder mehrerer Umgebungen: Entwicklung, Test, Vorproduktion, Produktion usw.

Jede Umgebung enthält eine Adobe Campaign-Instanz und jede Adobe Campaign-Instanz ist mit einer oder mehreren Datenbanken verknüpft. Der Anwendungs-Server kann einen oder mehrere Prozesse ausführen: Fast alle von ihnen haben direkten Zugriff auf die Instanzdatenbank.

In diesem Abschnitt werden die Prozesse beschrieben, die zum Duplizieren einer Adobe Campaign-Umgebung angewendet werden sollen, d. h. zum Wiederherstellen einer Quellumgebung in einer Zielumgebung, was zu zwei identischen Arbeitsumgebungen führt.

Gehen Sie hierzu wie folgt vor:

1. eine Kopie der Datenbanken auf allen Instanzen in der Quellumgebung erstellen,
1. Stellen Sie diese Kopien auf allen Instanzen der Zielumgebung wieder her.
1. Führen Sie **Skript &quot;:freezeInstance.js** vor dem Start in der Zielumgebung aus.

   Dieser Prozess hat keine Auswirkungen auf die Server und deren Konfiguration.

   >[!NOTE]
   >
   >Im Kontext von Adobe Campaign kombiniert eine **Kauterisierung** Aktionen, die es Ihnen ermöglichen, alle Prozesse zu stoppen, die mit außen interagieren: Protokolle, Tracking, Sendungen, Kampagnen-Workflows usw.\
   >Dieser Schritt ist erforderlich, um zu vermeiden, dass Nachrichten mehrmals gesendet werden (einmal aus der nominalen Umgebung und einmal aus der duplizierten Umgebung).

   >[!IMPORTANT]
   >
   >Eine Umgebung kann mehrere Instanzen enthalten. Jede Adobe Campaign-Instanz unterliegt einem Lizenzvertrag. Überprüfen Sie Ihre Lizenzvereinbarung, um zu sehen, wie viele Umgebungen Sie haben können.\
   >Mit dem folgenden Verfahren können Sie eine Umgebung übertragen, ohne die Anzahl der installierten Umgebungen und Instanzen zu beeinträchtigen.

### Bevor Sie beginnen {#before-you-start}

>[!IMPORTANT]
>
>Es wird dringend empfohlen, vor Beginn des Übertragungsprozesses eine vollständige Sicherung der Datenbanken für alle Instanzen der Quell- und Zielumgebung durchzuführen. Auf diese Weise können Sie im Falle eines Problems die Sicherungskopien wiederherstellen und zu Ihrer ursprünglichen Konfiguration zurückkehren.

Damit dieser Prozess funktioniert, müssen die Quell- und Zielumgebung über dieselbe Anzahl von Instanzen, denselben Zweck (Marketing-Instanz, Versandinstanz) und ähnliche Konfigurationen verfügen. Die technische Konfiguration muss den Softwarevoraussetzungen entsprechen. In beiden Umgebungen müssen dieselben Komponenten installiert werden.

## Implementierung {#implementation}

### Übertragungsverfahren {#transfer-procedure}

In diesem Abschnitt werden die Schritte erläutert, die zum Übertragen einer Quellumgebung in eine Zielumgebung anhand einer Fallstudie erforderlich sind: Unser Ziel ist es hier, eine Produktionsumgebung (**prod**-Instanz) in einer Entwicklungsumgebung (**dev**-Instanz) wiederherzustellen, damit sie in einem Kontext funktioniert, der der „Live“-Plattform möglichst nahekommt.

Die folgenden Schritte müssen mit größter Sorgfalt ausgeführt werden: Einige Prozesse sind möglicherweise noch in Bearbeitung, wenn die Datenbanken der Quellumgebung kopiert werden. Durch die Kauterisierung (Schritt 3 unten) wird verhindert, dass Nachrichten zweimal gesendet werden, und die Datenkonsistenz wird gewahrt.

>[!IMPORTANT]
>
>* Das folgende Verfahren ist in der Sprache PostgreSQL gültig. Wenn die SQL-Sprache unterschiedlich ist (z. B. Oracle), müssen die SQL-Abfragen angepasst werden.
>* Die folgenden Befehle gelten im Kontext einer **prod**-Instanz und einer **dev**-Instanz unter PostgreSQL.
>

### Schritt 1: Erstellen Sie eine Sicherung der Quellumgebungsdaten (prod) {#step-1---make-a-backup-of-the-source-environment--prod--data}

Datenbanken kopieren

Kopieren Sie zunächst alle Datenbanken der Quellumgebung. Der Vorgang hängt von der Datenbank-Engine ab und liegt in der Verantwortung des Datenbank-Administrators.

Unter PostgreSQL lautet der Befehl:

```
pg_dump mydatabase > mydatabase.sql
```

### Schritt 2: Exportieren der Zielumgebungskonfiguration (dev) {#step-2---export-the-target-environment-configuration--dev-}

Die meisten Konfigurationselemente sind für jede Umgebung unterschiedlich: externe Konten (Mid-Sourcing, Routing usw.), technische Optionen (Plattformname, Datenbank-ID, E-Mail-Adressen und Standard-URLs usw.).

Bevor Sie die Quelldatenbank in der Zieldatenbank speichern, müssen Sie die Konfiguration der Zielumgebung (dev) exportieren. Exportieren Sie dazu den Inhalt dieser beiden Tabellen: **xtkoption** und **nmsextaccount**.

Mit diesem Export können Sie die Dev-Konfiguration beibehalten und nur Dev-Daten (Workflows, Vorlagen, Web-Anwendungen, Empfänger usw.) aktualisieren.

Führen Sie dazu einen Package-Export für die folgenden beiden Elemente durch:

* Exportieren Sie die **xtk:option**-Tabelle in eine Datei „options_dev.xml“ ohne die Einträge mit den folgenden internen Namen: „WdbcTimeZone“, „NmsServer_LastPostUpgrade“ und „NmsBroadcast_RegexRules“.
* Exportieren Sie in einer Datei „extaccount_dev.xml“ die Tabelle **nms:extAccount** für alle Datensätze, deren ID nicht 0 ist (@id &lt;> 0).

Überprüfen Sie, ob die Anzahl der exportierten Optionen/Konten der Anzahl der zu exportierenden Zeilen in jeder Datei entspricht.

>[!NOTE]
>
>In einem Package-Export sind 1.000 Zeilen zu exportieren. Wenn die Anzahl der Optionen oder externen Konten mehr als 1000 beträgt, müssen Sie mehrere Exporte durchführen.
> 
>Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../platform/using/working-with-data-packages.md#exporting-packages).

>[!NOTE]
>
>Wenn die Tabelle nmsextaccount exportiert wird, werden Passwörter für externe Konten (z. B. Passwörter für Mid-Sourcing, Message Center Execution, SMPP, IMS und andere externe Konten) nicht exportiert. Bitte vergewissern Sie sich, dass Sie im Voraus Zugriff auf die richtigen Passwörter haben, da diese möglicherweise nach dem Import der externen Konten in die Umgebung erneut eingegeben werden müssen.

### Schritt 3: Stoppen der Zielumgebung (dev) {#step-3---stop-the-target-environment--dev-}

Sie müssen die Adobe Campaign-Prozesse auf allen Zielumgebungsservern stoppen. Dieser Vorgang hängt von Ihrem Betriebssystem ab.

Sie können alle Prozesse stoppen, oder nur die, die in die Datenbank schreiben.

Um alle Prozesse zu stoppen, verwenden Sie die folgenden Befehle:

* Windows:

  ```
  net stop nlserver6
  ```

* Unter Linux:

  ```
  /etc/init.d/nlserver6 stop
  ```

Verwenden Sie den folgenden Befehl, um zu überprüfen, ob alle Prozesse angehalten wurden:

```
nlserver pdump
```

>[!NOTE]
>
>Unter Windows kann der **webmdl**-Prozess weiterhin aktiv sein, ohne dass andere Vorgänge betroffen sind.

Sie können auch überprüfen, ob noch keine Systemprozesse ausgeführt werden.

Gehen Sie dazu wie folgt vor:

* In Windows: Öffnen Sie den **Task-Manager** und stellen Sie sicher, dass keine **nlserver.exe**-Prozesse vorhanden sind.
* Unter Linux: **ps aux | grep nlserver** Befehl ein und stellen Sie sicher, dass es keine **nlserver**-Prozesse gibt.

### Schritt 4: Wiederherstellen der Datenbanken in der Zielumgebung (dev) {#step-4---restore-the-databases-in-the-target-environment--dev-}

Verwenden Sie den folgenden Befehl, um die Quelldatenbanken in der Zielumgebung wiederherzustellen:

```
psql mydatabase < mydatabase.sql
```

### Schritt 5: Verätzung der Zielumgebung (dev) {#step-5---cauterize-the-target-environment--dev-}

Um Störungen zu vermeiden, dürfen die mit dem Versand und der Workflow-Ausführung verknüpften Prozesse bei der Aktivierung der Zielumgebung nicht automatisch ausgeführt werden.

Führen Sie dazu den folgenden Befehl aus:

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### Schritt 6 - Kauterisierung überprüfen {#step-6---check-cauterization}

1. Vergewissern Sie sich, dass nur der Versandkontingent mit der ID 0 zugestellt wird:

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

### Schritt 7: Neustarten des Web-Prozesses (dev) für die Zielumgebung {#step-7---restart-the-target-environment-web-process--dev-}

Starten Sie in der Zielumgebung die Adobe Campaign-Prozesse für alle Server neu.

>[!NOTE]
>
>Bevor Sie Adobe Campaign in der **dev**-Umgebung neu starten, können Sie ein zusätzliches Sicherheitsverfahren anwenden: Starten Sie nur das **web**-Modul.
>  
>Bearbeiten Sie dazu die Konfigurationsdatei Ihrer Instanz (**config-dev.xml**) und fügen Sie dann das Zeichen „_“ vor den AutoStart=„true“-Optionen für jedes Modul (MTA, STAT usw.) hinzu.

Führen Sie den folgenden Befehl aus, um den Web-Prozess zu starten:

```
nlserver start web
```

Verwenden Sie den folgenden Befehl, um zu überprüfen, ob nur der Web-Prozess gestartet wurde:

```
nlserver pdump
```

Überprüfen Sie, ob der Zugriff auf die Client-Konsole funktioniert.

### Schritt 8: Optionen und externe Konten in die Zielumgebung importieren (dev) {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!IMPORTANT]
>
>In diesem Schritt sollte nur der Web-Prozess gestartet werden. Ist dies nicht der Fall, beenden Sie andere laufende Prozesse, bevor Sie fortfahren

Überprüfen Sie vor allem die Werte mehrerer Zeilen der Dateien, bevor Sie sie importieren (z. B.: &#39;NmsTracking_Pointer&#39; für die Optionstabelle und die Versand- oder Mid-Sourcing-Konten für die Tabelle des externen Kontos)

So importieren Sie die Konfiguration aus der Zielumgebungsdatenbank (dev):

1. Öffnen Sie die Admin Console der Datenbank und löschen Sie die externen Konten (Tabelle nms:extAccount), deren ID nicht 0 ist (@id &lt;> 0).
1. Importieren Sie in der Adobe Campaign-Konsole das zuvor über die Funktion „Package importieren“ erstellte Package options_dev.xml.

   Vergewissern Sie sich, dass die Optionen im Knoten **[!UICONTROL Administration > Plattform > Optionen]** tatsächlich aktualisiert wurden.

1. Importieren Sie in der Adobe Campaign-Konsole die zuvor über die Funktion „Package importieren“ erstellte Datei „extaccount_dev.xml“

   Überprüfen Sie, ob tatsächlich externe Datenbanken in die Datei **[!UICONTROL Administration > Plattform > Externe Konten]** importiert wurden.

### Schritt 9: Alle Prozesse neu starten und Benutzer wechseln (dev) {#step-9---restart-all-processes-and-change-users--dev-}

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

Ändern Sie die Benutzer, um die Benutzer zu finden, die bereits auf der Entwicklungsplattform vorhanden waren.

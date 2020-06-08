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
source-git-commit: cb44d439c6866d94f8e1201575ab3d3094d6ad79
workflow-type: tm+mt
source-wordcount: '1298'
ht-degree: 5%

---


# Duplizieren von Umgebungen{#duplicating-environments}

## Einleitung {#introduction}

### Übersicht {#overview}

>[!CAUTION]
>
>Wenn Sie keinen Zugriff auf den Server und die Datenbank haben (gehostete Umgebung), können Sie die unten beschriebenen Schritte nicht ausführen. Wenden Sie sich an Adobe.

Zur Verwendung von Adobe Campaign müssen eine oder mehrere Umgebung installiert und konfiguriert werden: Entwicklung, Prüfung, Vorproduktion, Produktion usw.

Jede Umgebung enthält eine Adobe Campaign-Instanz und jede Adobe Campaign-Instanz ist mit einer oder mehreren Datenbanken verknüpft. Der Anwendungsserver kann einen oder mehrere Prozesse ausführen: Fast alle haben direkten Zugriff auf die Instanzdatenbank.

In diesem Abschnitt werden die Verfahren beschrieben, die auf Duplikat und Adobe Campaign-Umgebung angewendet werden sollen, d. h. um eine Quell-Umgebung auf eine Zielgruppe-Umgebung wiederherzustellen, was zu zwei identischen Umgebung führt.

Gehen Sie hierzu wie folgt vor:

1. Erstellen Sie eine Kopie der Datenbanken auf allen Instanzen in der Quellumgebung,
1. Stellen Sie diese Kopien auf allen Instanzen der Zielumgebung wieder her,
1. Führen Sie das Warnskript **nms:frizeInstance.js** auf der Umgebung Zielgruppe aus, bevor Sie es starten.

   Dieser Prozess hat keine Auswirkungen auf die Server und deren Konfiguration.

   >[!NOTE]
   >
   >Im Kontext eines Adobe Campaigns kombiniert eine **Vorsicht** Aktionen, mit denen Sie alle Prozesse stoppen können, die mit der Außenseite interagieren: Protokolle, Verfolgung, Versände, Kampagnen-Workflows usw.\
   >Dieser Schritt ist notwendig, um zu vermeiden, dass Nachrichten mehrmals gesendet werden (einmal von der nominalen Umgebung und einmal von der duplizierten Umgebung).

   >[!CAUTION]
   >
   >Eine Umgebung kann mehrere Instanzen enthalten. Jede Instanz eines Adobe Campaigns unterliegt einem Lizenzvertrag. Prüfen Sie Ihre Lizenzvereinbarung, um zu sehen, wie viele Umgebung Sie haben können.\
   >Mit dem unten stehenden Verfahren können Sie eine Umgebung übertragen, ohne dass sich dies auf die Anzahl der installierten Umgebung und Instanzen auswirkt.

### Vor dem Beginn {#before-you-start}

>[!CAUTION]
>
>Es wird dringend empfohlen, eine vollständige Sicherung der Datenbanken für alle Instanzen der Quell- und Zielgruppe-Umgebung auszuführen, bevor der Transfervorgang gestartet wird. Auf diese Weise können Sie bei einem Problem die Backups wiederherstellen und zu Ihrer ursprünglichen Konfiguration zurückkehren.

Damit dieser Vorgang ausgeführt werden kann, müssen die Quell- und Zielgruppe-Umgebung dieselbe Anzahl von Instanzen, denselben Zweck (Marketing-Instanz, Versand-Instanz) und ähnliche Konfigurationen aufweisen. Die technische Konfiguration muss den Softwarevoraussetzungen entsprechen. Die gleichen Komponenten müssen auf beiden Umgebung installiert sein.

## Implementierung{#implementation}

### Transferverfahren {#transfer-procedure}

In diesem Abschnitt erfahren Sie, wie Sie mithilfe einer Fallstudie eine Quell-Umgebung in eine Zielgruppe-Umgebung übertragen können: Unser Ziel ist es hier, eine Produktions-Umgebung (**prod** Instanz) zu einer Umgebung (**dev** Instanz) wiederherzustellen, um in einem Kontext zu arbeiten, der der &quot;live&quot; Plattform so nahe wie möglich ist.

Die folgenden Schritte müssen mit größter Sorgfalt durchgeführt werden: Einige Prozesse werden möglicherweise noch ausgeführt, wenn die Quelldatenbanken der Umgebung kopiert werden. Durch die Vorsicht (Schritt 3 unten) wird verhindert, dass Nachrichten zweimal gesendet werden, und die Datenkonsistenz bleibt erhalten.

>[!CAUTION]
>
>* Das folgende Verfahren ist in der Sprache PostgreSQL gültig. Wenn die SQL-Abfrage unterschiedlich ist (z. B. Oracle), müssen die SQL-Einstellungen angepasst werden.
>* Die folgenden Befehle gelten im Kontext einer **prod** -Instanz und einer **dev** -Instanz unter PostgreSQL.

>



### Schritt 1 - Erstellen einer Sicherung der Quelldaten (Prod) der Umgebung {#step-1---make-a-backup-of-the-source-environment--prod--data}

Datenbanken kopieren

Beginn durch Kopieren aller Quelldatenbanken der Umgebung. Der Vorgang ist von der Datenbank-Engine abhängig und unterliegt der Verantwortung des Datenbankadministrators.

Unter PostgreSQL lautet der Befehl:

```
pg_dump mydatabase > mydatabase.sql
```

### Schritt 2: Exportieren der Konfiguration der Zielgruppe-Umgebung (dev) {#step-2---export-the-target-environment-configuration--dev-}

Die meisten Konfigurationselemente unterscheiden sich für jede Umgebung: Externe Konti (Mid-Sourcing, Routing usw.), technische Optionen (Plattformname, DatabaseId, E-Mail-Adressen und Standard-URLs usw.)

Vor dem Speichern der Quelldatenbank in der Zielgruppe müssen Sie die Dev-Konfiguration (Zielgruppe Umgebung) exportieren. Exportieren Sie dazu den Inhalt dieser beiden Tabellen: **xtkoption** und **nmsextaccount**.

Mit diesem Export können Sie die Dev-Konfiguration beibehalten und nur die Dev-Daten (Workflows, Vorlagen, Webanwendungen, Empfänger usw.) aktualisieren.

Führen Sie dazu einen Paketexport für die folgenden beiden Elemente durch:

* Exportieren Sie die Tabelle &quot; **xtk:option** &quot;in eine Datei &quot;options_dev.xml&quot;ohne die Datensätze mit den folgenden internen Namen: &#39;WdbcTimeZone&#39;, &#39;NmsServer_LastPostUpgrade&#39; und &#39;NmsBroadcast_RegexRules&#39;.
* Exportieren Sie in einer Datei &quot;extaccount_dev.xml&quot;die Tabelle **nms:extAccount** für alle Datensätze, deren ID nicht 0 (@id &lt;> 0) ist.

Überprüfen Sie, ob die Anzahl der exportierten Optionen/Konten der Anzahl der Zeilen entspricht, die in jeder Datei exportiert werden sollen.

>[!NOTE]
>
>Die Anzahl der zu exportierenden Zeilen in einem Paketexport beträgt 1000 Zeilen. Wenn die Anzahl der Optionen oder Externe Konti mehr als 1000 beträgt, müssen Sie mehrere Exporte durchführen.
> 
>Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../platform/using/working-with-data-packages.md#exporting-packages).

>[!NOTE]
>
>Beim Exportieren der nmsextaccount-Tabelle werden Kennwörter zu den Externen Konti (z. B. Kennwörter zum Mid-Sourcing, zur Ausführung des Nachrichtencenters, zu SMPP, IMS und anderen Externen Konti) nicht exportiert. Vergewissern Sie sich bitte, dass Sie im Voraus Zugriff auf die richtigen Passwörter haben, da diese ggf. erneut eingegeben werden müssen, nachdem die Externe Konti wieder in die Umgebung importiert wurden.

### Schritt 3: Beenden der Zielgruppe-Umgebung (dev) {#step-3---stop-the-target-environment--dev-}

Sie müssen Adobe Campaign-Prozesse auf allen Zielgruppe Umgebung-Servern beenden. Dieser Vorgang ist vom Betriebssystem abhängig.

Sie können alle Prozesse oder nur die Prozesse beenden, die in die Datenbank schreiben.

Um alle Prozesse zu beenden, verwenden Sie die folgenden Befehle:

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

* Windows: Öffnen Sie den **Aufgabe Manager** und überprüfen Sie, ob es keine **nlserver.exe** -Prozesse gibt.
* Unter Linux: Führen Sie die **ps aux aus | grep nlserver** Befehl und überprüfen Sie, ob es keine **nlserver** -Prozesse gibt.

### Schritt 4: Wiederherstellen der Datenbanken in der Umgebung Zielgruppe (dev) {#step-4---restore-the-databases-in-the-target-environment--dev-}

Um die Quelldatenbanken in der Umgebung Zielgruppe wiederherzustellen, verwenden Sie den folgenden Befehl:

```
psql mydatabase < mydatabase.sql
```

### Schritt 5: Umgebung der Zielgruppe (dev) {#step-5---cauterize-the-target-environment--dev-}

Um Funktionsstörungen zu vermeiden, dürfen die mit dem Senden des Versands und der Ausführung des Workflows verknüpften Vorgänge nicht automatisch ausgeführt werden, wenn die Umgebung der Zielgruppe aktiviert wird.

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

### Schritt 7: Zielgruppe Umgebung Web Process (dev) neu starten {#step-7---restart-the-target-environment-web-process--dev-}

Stellen Sie auf der Umgebung Zielgruppe einen erneuten Beginn der Adobe Campaign-Prozesse für alle Server bereit.

>[!NOTE]
>
>Bevor Sie das Adobe Campaign auf der **dev** -Umgebung neu starten, können Sie ein zusätzliches Sicherheitsverfahren anwenden: Beginn nur im **Webmodul** .
>  
>Bearbeiten Sie dazu die Konfigurationsdatei Ihrer Instanz (**config-dev.xml**) und fügen Sie dann das Zeichen &quot;_&quot;vor den Optionen autoStart=&quot;true&quot;für jedes Modul (mta, stat usw.) hinzu.

Führen Sie den folgenden Befehl aus, um den Webprozess Beginn:

```
nlserver start web
```

Verwenden Sie den folgenden Befehl, um zu überprüfen, dass nur der Webprozess gestartet wurde:

```
nlserver pdump
```

Überprüfen Sie, ob der Zugriff auf die Funktionen der Client-Konsole möglich ist.

### Schritt 8: Importieren von Optionen und Externen Konti in die Zielgruppe-Umgebung (dev) {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!CAUTION]
>
>In diesem Schritt sollte nur der Webprozess gestartet werden. Ist dies nicht der Fall, beenden Sie andere laufende Prozesse, bevor Sie fortfahren

Überprüfen Sie vor allem die Werte mehrerer Zeilen der Dateien, bevor Sie sie importieren (z. B.: &#39;NmsTracking_Pointer&#39; für die Optionstabelle und die Versand- oder Mid-Sourcing-Konten für die Externe Konto-Tabelle)

So importieren Sie die Konfiguration aus der Zielgruppe Umgebung-Datenbank (dev):

1. Öffnen Sie die Admin-Konsole der Datenbank und löschen Sie die Externe Konti (Tabelle nms:extAccount), deren ID nicht 0 (@id &lt;> 0) ist.
1. Importieren Sie in der Adobe Campaign-Konsole das Paket options_dev.xml, das zuvor über die Importpaket-Funktionalität erstellt wurde.

   Überprüfen Sie, ob die Optionen im Knoten **[!UICONTROL Administration > Plattform > Optionen]** tatsächlich aktualisiert wurden.

1. Importieren Sie in die Adobe Campaign-Konsole die Datei &quot;extaccount_dev.xml&quot;, die Sie zuvor über die Funktion des Importpakets erstellt haben.

   Vergewissern Sie sich, dass externe Datenbanken tatsächlich in **[!UICONTROL Administration > Plattform > Externe Konti]** importiert wurden.

### Schritt 9: Alle Prozesse neu starten und Benutzer ändern (dev) {#step-9---restart-all-processes-and-change-users--dev-}

Um die Adobe Campaign-Prozesse Beginn, verwenden Sie die folgenden Befehle:

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

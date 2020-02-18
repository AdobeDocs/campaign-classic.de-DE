---
title: Migrieren testen
seo-title: Migrieren testen
description: Migrieren testen
seo-description: null
page-status-flag: never-activated
uuid: 3ee6a10b-dea2-41c6-9aef-ee3ac922b459
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: 30e3082f-a367-4c3b-bff2-208ccf97acd4
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9f7cf3d530f141a661df5fcc8cbcf0bb4c8d3e89

---


# Migrieren testen{#testing-the-migration}

## Allgemeines Verfahren {#general-procedure}

Je nach Konfiguration gibt es verschiedene Möglichkeiten, Migrationstests durchzuführen.

Sie sollten über eine Test-/Entwicklungsumgebung verfügen, um Migrationstests durchzuführen. Entwicklungsumgebungen unterliegen einer Lizenz: Überprüfen Sie Ihren Lizenzvertrag oder wenden Sie sich an den Vertriebsdienst von Adobe Campaign.

1. Beenden Sie alle laufenden Entwicklungen und führen Sie sie in die Produktionsumgebung.
1. Erstellen Sie eine Sicherung der Datenbank der Entwicklungsumgebung.
1. Beenden Sie alle Adobe Campaign-Prozesse in der Entwicklungsinstanz.
1. Erstellen Sie eine Sicherung der Produktionsumgebung-Datenbank und stellen Sie sie als Entwicklungsumgebung wieder her.
1. Bevor Sie Adobe Campaign-Dienste starten, führen Sie das Warnskript **frizeInstance.js** aus, mit dem Sie die Datenbank aller Objekte löschen können, die beim Starten der Sicherung ausgeführt wurden.

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >Der Befehl wird standardmäßig im **trockenen** Modus gestartet und listet alle Anforderungen auf, die von diesem Befehl ausgeführt wurden, ohne sie zu starten. Verwenden Sie zum Ausführen von Warnungsanfragen den Befehl **run** .

1. Stellen Sie sicher, dass Ihre Sicherungen korrekt sind, indem Sie versuchen, sie wiederherzustellen. Stellen Sie sicher, dass Sie auf Ihre Datenbank, Ihre Tabellen, Ihre Daten usw. zugreifen können.
1. Testen Sie den Migrationsvorgang in der Entwicklungsumgebung.

   Die vollständigen Verfahren finden Sie im Abschnitt [Voraussetzungen für die Migration zu Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) .

1. Bei erfolgreicher Migration der Entwicklungsumgebung können Sie die Produktionsumgebung migrieren.

>[!IMPORTANT]
>
>Aufgrund von Änderungen an der Datenstruktur ist das Importieren und Exportieren von Datenpaketen zwischen einer v5- und einer v7-Plattform nicht möglich.

>[!NOTE]
>
>Mit dem Befehl zum Aktualisieren von Adobe Campaign (**nach der Aktualisierung**) können Sie Ressourcen synchronisieren und Schemata und die Datenbank aktualisieren. Dieser Vorgang kann nur einmal auf dem Anwendungsserver ausgeführt werden. Nach dem Synchronisieren von Ressourcen können Sie mit dem Befehl **nach der Aktualisierung** erkennen, ob die Synchronisierung Fehler oder Warnungen hervorruft.

## Migrationswerkzeuge {#migration-tools}

Mit verschiedenen Optionen können Sie die Auswirkungen einer Migration messen und potenzielle Probleme identifizieren. Diese Optionen sind auszuführen:

* im Befehl **config** :

   ```
   nlserver.exe config <option> -instance:<instanceName>
   ```

* oder nach der Aktualisierung:

   ```
   nlserver.exe config -postupgrade <option> -instance:<instanceName>
   ```

>[!NOTE]
>
>**Sie müssen die`<instanceame>`**-Instanz verwenden: auswählen. Es wird nicht empfohlen, die Option**-allinstances **zu verwenden.

### -showCustomEntities- und -showDeletedEntities-Optionen {#showcustomentities-and--showdeletedentities-options}

* Die Option **-showCustomEntities** zeigt die Liste aller nicht standardmäßigen Objekte an:

   ```
   nlserver.exe config -showCustomEntities -instance:<instanceName>
   ```

   Beispiel einer gesendeten Nachricht:

   ```
   xtk_migration:opsecurity2 xtk:entity
   ```

* Die Option **-showDeletedEntities** zeigt die Liste aller Standardobjekte an, die in der Datenbank oder im Dateisystem fehlen. Für jedes fehlende Objekt wird der Pfad angegeben.

   ```
   nlserver.exe config -showDeletedEntities -instance:<instanceName>
   ```

   Beispiel einer gesendeten Nachricht:

   ```
   Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
   ```

### Verification process {#verification-process}

Dieser Prozess, der als Standard in den Befehl nach der Aktualisierung integriert ist, ermöglicht Ihnen die Anzeige von Warnungen und Fehlern, die die Migration zum Fehler machen könnten. **Wenn Fehler angezeigt werden, wurde die Migration nicht ausgeführt.** In diesem Fall sollten Sie alle Fehler beheben und dann die Nachaktualisierung erneut starten.

Sie können den Verifizierungsprozess mit folgendem Befehl eigenständig (ohne Migration) starten:

```
nlserver.exe config -postupgrade -check -instance:<instanceName>
```

>[!NOTE]
>
>Bitte ignorieren Sie alle Warnungen und Fehler mit dem JST-310040-Code.

Die folgenden Ausdrücke werden gesucht (Groß-/Kleinschreibung beachten):

<table> 
 <thead> 
  <tr> 
   <th> Ausdruck<br /> </th> 
   <th> Fehlercode<br /> </th> 
   <th> Protokolltyp<br /> </th> 
   <th> Erklärung<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> .@<br /> </td> 
   <td> PU-0001<br /> </td> 
   <td> Warnhinweis<br /> </td> 
   <td> Diese Syntax wird bei der Personalisierung der Bereitstellung nicht mehr unterstützt. Siehe <a href="../../migration/using/general-configurations.md#javascript" target="_blank">JavaScript</a>. Überprüfen Sie andernfalls, ob der Werttyp korrekt ist.<br /> </td> 
  </tr> 
  <tr> 
   <td> common.js<br /> </td> 
   <td> PU-0002<br /> </td> 
   <td> Warnhinweis<br /> </td> 
   <td> Diese Bibliothek darf nicht verwendet werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> logon(<br /> </td> 
   <td> PU-0003<br /> </td> 
   <td> Warnhinweis<br /> </td> 
   <td> Diese Verbindungsmethode darf nicht mehr verwendet werden. Siehe <a href="../../migration/using/general-configurations.md#identified-web-applications" target="_blank">Identifizierte Webanwendungen</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> new SoapMethodCall(<br /> </td> 
   <td> PU-0004<br /> </td> 
   <td> Warnhinweis<br /> </td> 
   <td> Diese Funktion wird nur unterstützt, wenn sie im JavaScript-Code verwendet wird, der aus einer Sicherheitszone ausgeführt wird, die sich im <strong>sessionTokenOnly</strong> -Modus befindet.<br /> </td> 
  </tr> 
  <tr> 
   <td> sql=<br /> </td> 
   <td> PU-0005<br /> </td> 
   <td> Fehler<br /> </td> 
   <td> Dieser Fehlertyp führt zu einem Migrationsfehler. Siehe <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> SQLDATA<br /> </td> 
   <td> PU-0006<br /> </td> 
   <td> Fehler<br /> </td> 
   <td> Dieser Fehlertyp führt zu einem Migrationsfehler. Siehe <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>. Wenn Sie Übersichtsfehler-Fehlerprotokolle für Webanwendungen erhalten (Migration von Version 6.02), lesen Sie <a href="../../migration/using/specific-configurations-in-v6-02.md#web-applications" target="_blank">Webanwendungen</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Eine Datenbank- und Schemakonsistenz-Prüfung wird ebenfalls durchgeführt.

### Wiederherstellungsoption {#restoration-option}

Mit dieser Option können Sie vordefinierte Objekte wiederherstellen, wenn sie geändert wurden. Für jedes wiederhergestellte Objekt wird eine Sicherungskopie der Änderungen im ausgewählten Ordner gespeichert:

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instanceName>
```

>[!NOTE]
>
>Es wird dringend empfohlen, absolute Ordnerpfade zu verwenden und die Ordnerstruktur beizubehalten. Beispiel: backupFolder\nms\srcSchema\billing.xml.

### Migration fortsetzen {#resuming-migration}

Wenn Sie die Nachaktualisierung nach einem Migrationsfehler neu starten, wird sie von demselben Ort, an dem sie beendet wurde, wieder aufgenommen.

---
product: campaign
title: Testen der Migration
description: Testen der Migration
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: 228ee9e4-46a0-4d82-b8ba-b019bc0e7cac
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# Migrationstests{#testing-the-migration}



## Allgemeines Verfahren {#general-procedure}

Je nach Konfiguration gibt es mehrere Möglichkeiten, Migrationstests durchzuführen.

Sie sollten über eine Test-/Entwicklungsumgebung verfügen, um Migrationstests durchzuführen. Adobe Campaign-Umgebungen sind lizenzpflichtig: Überprüfen Sie Ihren Lizenzvertrag oder wenden Sie sich an den Adobe-Support.

1. Halten Sie alle laufenden Entwicklungen an und übertragen Sie sie in die Produktionsumgebung.
1. Erstellen Sie eine Sicherungskopie der Datenbank der Entwicklungsumgebung.
1. Beenden Sie alle Adobe Campaign-Prozesse auf der Entwicklungsinstanz.
1. Erstellen Sie ein Backup der Datenbank der Produktionsumgebung und stellen Sie sie als Entwicklungsumgebung wieder her.
1. Bevor Sie die Adobe Campaign-Services starten, führen Sie das Skript **freezeInstance.js** aus, mit dem Sie die Datenbank von allen Objekten löschen können, die beim Starten des Backups ausgeführt wurden.

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >Der Befehl wird standardmäßig im **-**-Modus gestartet und listet alle Anforderungen auf, die von diesem Befehl ausgeführt wurden, ohne sie zu starten. Verwenden Sie zum Ausführen von Kauterisierungsanfragen **Befehl** run“.

1. Stellen Sie sicher, dass Ihre Backups korrekt sind, indem Sie versuchen, sie wiederherzustellen. Stellen Sie sicher, dass Sie auf Ihre Datenbank, Ihre Tabellen, Ihre Daten usw. zugreifen können.
1. Testen Sie das Migrationsverfahren in der Entwicklungsumgebung.
1. Wenn die Migration der Entwicklungsumgebung erfolgreich war, können Sie die Produktionsumgebung migrieren.

>[!CAUTION]
>
>Aufgrund von Änderungen an der Datenstruktur ist der Import und Export von Datenpaketen zwischen einer v5- und einer v7-Plattform nicht möglich.


## Migrations-Tools {#migration-tools}

Verschiedene Optionen ermöglichen es Ihnen, die Auswirkungen einer Migration zu messen und die potenziellen Probleme zu identifizieren. Die folgenden Optionen sind auszuführen:

* Im Befehl **config**:

  ```
  nlserver.exe config <option> -instance:<instance-name>
  ```

* oder beim Postupgrade:

  ```
  nlserver.exe config -postupgrade <option> -instance:<instance-name>
  ```

>[!NOTE]
>
>* Sie müssen die Option **-instance:`<instanceame>`** verwenden. Es wird davon abgeraten, die Option **-allInstances** zu verwenden.
>* Mit dem Adobe Campaign-Aktualisierungsbefehl **postupgrade** können Sie Ressourcen synchronisieren und Schemas und die Datenbank aktualisieren. Dieser Vorgang kann nur einmal und nur auf dem Anwendungsserver ausgeführt werden. Nach der Synchronisierung von Ressourcen können Sie mit **Befehl** postupgrade“ erkennen, ob die Synchronisierung Fehler oder Warnungen erzeugt.

### Nicht standardmäßige oder fehlende Objekte

* Mit der Option **-showCustomEntities** wird die Liste aller nicht standardmäßigen Objekte angezeigt:

  ```
  nlserver.exe config -showCustomEntities -instance:<instance-name>
  ```

  Beispiel einer gesendeten Nachricht:

  ```
  xtk_migration:opsecurity2 xtk:entity
  ```

* Die Option **-showDeletedEntities** zeigt die Liste aller Standardobjekte an, die in der Datenbank oder im Dateisystem fehlen. Für jedes fehlende Objekt wird der Pfad angegeben.

  ```
  nlserver.exe config -showDeletedEntities -instance:<instance-name>
  ```

  Beispiel einer gesendeten Nachricht:

  ```
  Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
  ```

### Verifizierungsprozess {#verification-process}

Dieser Prozess ist standardmäßig im Postupgrade-Befehl integriert und ermöglicht die Anzeige von Warnungen und Fehlern, die zu einem Fehlschlagen der Migration führen können. **Wenn Fehler angezeigt werden, wurde die Migration nicht ausgeführt.** Wenn dies eintritt, korrigieren Sie alle Fehler und starten Sie das Postupgrade erneut.

Sie können den Verifizierungsprozess eigenständig (ohne Migration) mit dem Befehl starten:

```
nlserver.exe config -postupgrade -check -instance:<instance-name>
```

>[!NOTE]
>
>Sie können alle Warnungen und Fehler mit dem JST-310040-Code ignorieren.

Bei den folgenden Ausdrücken wird nach gesucht (von Schreibweise abhängig):

<table> 
 <thead> 
  <tr> 
   <th> Ausdruck<br /> </th> 
   <th> Fehlercode<br /> </th> 
   <th> Protokolltyp<br /> </th> 
   <th> Kommentare<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> .@<br /> </td> 
   <td> PU-0001<br /> </td> 
   <td> Warnung<br /> </td> 
   <td> Diese Art von Syntax wird bei der Versandpersonalisierung nicht mehr unterstützt. <br /> </td> 
  </tr> 
  <tr> 
   <td> common.js<br /> </td> 
   <td> PU-0002<br /> </td> 
   <td> Warnung<br /> </td> 
   <td> Diese Bibliothek darf nicht verwendet werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> LOGON(<br /> </td> 
   <td> PU-0003<br /> </td> 
   <td> Warnung<br /> </td> 
   <td> Diese Verbindungsmethode darf nicht mehr verwendet werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> new SoapMethodCall(<br /> </td> 
   <td> PU-0004<br /> </td> 
   <td> Warnung<br /> </td> 
   <td> Diese Funktion wird nur unterstützt, wenn sie in JavaScript-Code verwendet wird, der von einer Sicherheitszone im Modus <strong>sessionTokenOnly</strong> ausgeführt wird<br /> </td> 
  </tr> 
  <tr> 
   <td> SQL=<br /> </td> 
   <td> PU-0005<br /> </td> 
   <td> Fehler<br /> </td> 
   <td> Diese Art von Fehler führt zu einem Migrationsfehler.<br /> </td> 
  </tr> 
  <tr> 
   <td> crmDeploymentType=„OnPremise“<br /> </td> 
   <td> PU-0007<br /> </td> 
   <td> Fehler<br /> </td> 
   <td> Diese Art der Bereitstellung wird nicht mehr unterstützt. Der Bereitstellungstyp für Office 365- und On-Premise-Microsoft CRM-Connectoren wird jetzt nicht mehr unterstützt. 
   </br>Wenn Sie einen dieser veralteten Bereitstellungstypen in einem externen Konto verwenden, sollte dieses externe Konto gelöscht werden und Sie sollten dann den Befehl <b>postupgrade</b> ausführen. 
   </br>Informationen zum Ändern der Web-API-Bereitstellung finden Sie unter <a href="../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft" target="_blank">Web-Anwendungen</a>.<br /> </td>
  </tr> 
  <tr> 
   <td> CRM v1(mscrmWorkflow/sfdcWorkflow)<br /> </td> 
   <td> PU-0008<br /> </td> 
   <td> Fehler<br /> </td> 
   <td> Aktionsaktivitäten von Microsoft CRM, Salesforce, Oracle CRM On Demand sind nicht mehr verfügbar. Um die Datensynchronisation zwischen Adobe Campaign und einem CRM-System zu konfigurieren, müssen Sie die Zielgruppenbestimmungsaktivität <a href="../../workflow/using/crm-connector.md" target="_blank">CRM-Connector</a> verwenden.<br /> </td>
  </tr> 
 </tbody> 
</table>

Außerdem wird eine Datenbank- und Schemakohäsionsprüfung durchgeführt.

### Wiederherstellungsoption {#restoration-option}

Mit dieser Option können Sie vordefinierte Objekte wiederherstellen, wenn sie geändert wurden. Für jedes wiederhergestellte Objekt wird eine Sicherung Ihrer Änderungen im ausgewählten Ordner gespeichert:

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instance-name>
```

>[!NOTE]
>
>Es wird dringend empfohlen, absolute Ordnerpfade zu verwenden und die Ordnerbaumstruktur beizubehalten. Beispiel: backupFolder\nms\srcSchema\billing.xml.

### Fortsetzen der Migration {#resuming-migration}

Wenn Sie das Postupgrade nach einem Migrationsfehler neu starten, wird es an der Stelle fortgesetzt, an der es gestoppt wurde.

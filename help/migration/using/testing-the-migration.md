---
product: campaign
title: Testen der Migration
description: Testen der Migration
feature: Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: 228ee9e4-46a0-4d82-b8ba-b019bc0e7cac
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 1%

---

# Migrationstests{#testing-the-migration}



## Allgemeines Verfahren {#general-procedure}

Je nach Konfiguration gibt es mehrere Möglichkeiten, Migrationstests durchzuführen.

Sie sollten über eine Test-/Entwicklungsumgebung verfügen, um Migrationstests durchzuführen. Adobe Campaign-Umgebungen unterliegen einer Lizenz: Überprüfen Sie Ihren Lizenzvertrag oder kontaktieren Sie Ihren Adobe-Support-Mitarbeiter.

1. Stoppen Sie alle laufenden Entwicklungen und übertragen Sie sie in die Produktionsumgebung.
1. Erstellen Sie eine Sicherungskopie der Datenbank der Entwicklungsumgebung.
1. Beenden Sie alle Adobe Campaign-Prozesse auf der Entwicklungsinstanz.
1. Erstellen Sie eine Sicherungskopie der Datenbank der Produktionsumgebung und stellen Sie sie als Entwicklungsumgebung wieder her.
1. Führen Sie vor dem Starten der Adobe Campaign-Dienste den **freezeInstance.js** Warnhinweisskript, mit dem Sie die Datenbank aller Objekte löschen können, die beim Starten der Sicherung ausgeführt wurden.

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >Der Befehl wird standardmäßig in **trocken** und listet alle Anforderungen auf, die von diesem Befehl ausgeführt wurden, ohne sie zu starten. Verwenden Sie zum Ausführen von Warnungsanfragen **run** im -Befehl.

1. Stellen Sie sicher, dass Ihre Sicherungen korrekt sind, indem Sie versuchen, sie wiederherzustellen. Stellen Sie sicher, dass Sie Zugriff auf Ihre Datenbank, Ihre Tabellen, Ihre Daten usw. haben.
1. Testen Sie das Migrationsverfahren in der Entwicklungsumgebung.
1. Wenn die Migration der Entwicklungsumgebung erfolgreich ist, können Sie die Produktionsumgebung migrieren.

>[!CAUTION]
>
>Aufgrund von Änderungen an der Datenstruktur ist der Import und Export von Datenpaketen zwischen einer v5-Plattform und einer v7-Plattform nicht möglich.


## Migrationswerkzeuge {#migration-tools}

Mithilfe verschiedener Optionen können Sie die Auswirkungen einer Migration messen und potenzielle Probleme identifizieren. Diese Optionen werden ausgeführt:

* im **config** command:

  ```
  nlserver.exe config <option> -instance:<instance-name>
  ```

* oder beim Postupgrade:

  ```
  nlserver.exe config -postupgrade <option> -instance:<instance-name>
  ```

>[!NOTE]
>
>* Sie müssen die **-instance:`<instanceame>`** -Option. Es wird empfohlen, die **-allinstances** -Option.
>* Der Adobe Campaign-Aktualisierungsbefehl (**postupgrade**) ermöglicht die Synchronisierung von Ressourcen und die Aktualisierung von Schemata und der Datenbank. Dieser Vorgang kann nur einmal auf dem Anwendungsserver ausgeführt werden. Nach der Synchronisierung der Ressourcen wird die **postupgrade** -Befehl können Sie erkennen, ob die Synchronisation Fehler oder Warnungen erzeugt.

### Nicht standardmäßige oder fehlende Objekte

* Die **-showCustomEntities** zeigt die Liste aller Objekte an, die nicht dem Standard entsprechen:

  ```
  nlserver.exe config -showCustomEntities -instance:<instance-name>
  ```

  Beispiel einer gesendeten Nachricht:

  ```
  xtk_migration:opsecurity2 xtk:entity
  ```

* Die **-showDeletedEntities** zeigt die Liste aller Standardobjekte an, die in der Datenbank oder im Dateisystem fehlen. Für jedes fehlende Objekt wird der Pfad angegeben.

  ```
  nlserver.exe config -showDeletedEntities -instance:<instance-name>
  ```

  Beispiel einer gesendeten Nachricht:

  ```
  Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
  ```

### Überprüfungsverfahren {#verification-process}

Dieser Prozess ist standardmäßig in den Befehl postupgrade integriert und ermöglicht die Anzeige von Warnungen und Fehlern, die dazu führen können, dass die Migration fehlschlägt. **Wenn Fehler angezeigt werden, wurde die Migration nicht ausgeführt.** Korrigieren Sie in diesem Fall alle Fehler und starten Sie das Postupgrade erneut.

Mit dem folgenden Befehl können Sie den Verifizierungsprozess selbst (ohne Migration) starten:

```
nlserver.exe config -postupgrade -check -instance:<instance-name>
```

>[!NOTE]
>
>Mit dem JST-310040-Code können Sie alle Warnungen und Fehler ignorieren.

Die folgenden Ausdrücke werden gesucht (Groß-/Kleinschreibung beachten):

<table> 
 <thead> 
  <tr> 
   <th> Ausdruck<br /> </th> 
   <th> Fehler-Code<br /> </th> 
   <th> Protokolltyp<br /> </th> 
   <th> Kommentare<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> .@<br /> </td> 
   <td> PU-0001<br /> </td> 
   <td> Warnung<br /> </td> 
   <td> Diese Syntax wird bei der Versandpersonalisierung nicht mehr unterstützt. <br /> </td> 
  </tr> 
  <tr> 
   <td> common.js<br /> </td> 
   <td> PU-0002<br /> </td> 
   <td> Warnung<br /> </td> 
   <td> Diese Bibliothek darf nicht verwendet werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> logon(<br /> </td> 
   <td> PU-0003<br /> </td> 
   <td> Warnung<br /> </td> 
   <td> Diese Verbindungsmethode darf nicht mehr verwendet werden.<br /> </td> 
  </tr> 
  <tr> 
   <td> new SoapMethodCall(<br /> </td> 
   <td> PU-0004<br /> </td> 
   <td> Warnung<br /> </td> 
   <td> Diese Funktion wird nur unterstützt, wenn sie im JavaScript-Code verwendet wird, der aus einer Sicherheitszone ausgeführt wird, die sich in <strong>sessionTokenOnly</strong> -Modus.<br /> </td> 
  </tr> 
  <tr> 
   <td> sql=<br /> </td> 
   <td> PU-0005<br /> </td> 
   <td> Fehler<br /> </td> 
   <td> Dieser Fehlertyp führt zu einem Migrationsfehler.<br /> </td> 
  </tr> 
  <tr> 
   <td> crmDeploymentType="onpremise"<br /> </td> 
   <td> PU-0007<br /> </td> 
   <td> Fehler<br /> </td> 
   <td> Diese Art der Bereitstellung wird nicht mehr unterstützt. Der Bereitstellungstyp des CRM-Connectors für Office 365 und On-Premise Microsoft wurde eingestellt. 
   </br>Wenn Sie einen dieser veralteten Bereitstellungstypen in einem externen Konto verwenden, sollte dieses externe Konto gelöscht werden. Anschließend sollten Sie die <b>postupgrade</b> Befehl. 
   </br>Informationen zum Ändern der Web-API-Bereitstellung finden Sie unter <a href="../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft" target="_blank">Webanwendungen</a>.<br /> </td>
  </tr> 
  <tr> 
   <td> CRM v1(mscrmWorkflow/sfdcWorkflow)<br /> </td> 
   <td> PU-0008<br /> </td> 
   <td> Fehler<br /> </td> 
   <td> Die Aktionsaktivitäten Microsoft CRM, Salesforce und Oracle CRM On Demand sind nicht mehr verfügbar. Um die Datensynchronisation zwischen Adobe Campaign und einem CRM-System zu konfigurieren, müssen Sie die <a href="../../workflow/using/crm-connector.md" target="_blank">CRM-Connector</a> Zielgruppenbestimmung.<br /> </td>
  </tr> 
 </tbody> 
</table>

Außerdem wird eine Datenbank- und Schema-Konsistenz-Prüfung durchgeführt.

### Wiederherstellungsoption {#restoration-option}

Mit dieser Option können Sie native Objekte wiederherstellen, wenn sie geändert wurden. Für jedes wiederhergestellte Objekt wird eine Sicherung Ihrer Änderungen im ausgewählten Ordner gespeichert:

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instance-name>
```

>[!NOTE]
>
>Es wird dringend empfohlen, absolute Ordnerpfade zu verwenden und die Ordnerstruktur beizubehalten. Beispiel: backupFolder\nms\srcSchema\billing.xml.

### Migration fortsetzen {#resuming-migration}

Wenn Sie das Postupgrade nach einem Migrationsfehler neu starten, wird es von der Stelle fortgesetzt, an der es angehalten wurde.

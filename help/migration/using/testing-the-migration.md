---
product: campaign
title: Testen der Migration
description: Testen der Migration
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: 228ee9e4-46a0-4d82-b8ba-b019bc0e7cac
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 3%

---

# Testen der Migration{#testing-the-migration}

![](../../assets/v7-only.svg)

## Allgemeines Verfahren {#general-procedure}

Je nach Konfiguration gibt es mehrere Möglichkeiten, Migrationstests durchzuführen.

Sie sollten über eine Test-/Entwicklungsumgebung verfügen, um Migrationstests durchzuführen. Entwicklungsumgebungen unterliegen einer Lizenz: Überprüfen Sie Ihren Lizenzvertrag oder kontaktieren Sie den Vertriebsdienst von Adobe Campaign.

1. Stoppen Sie alle laufenden Entwicklungen und übertragen Sie sie in die Produktionsumgebung.
1. Erstellen Sie eine Sicherungskopie der Datenbank der Entwicklungsumgebung.
1. Beenden Sie alle Adobe Campaign-Prozesse auf der Entwicklungsinstanz.
1. Erstellen Sie eine Sicherungskopie der Datenbank der Produktionsumgebung und stellen Sie sie als Entwicklungsumgebung wieder her.
1. Führen Sie vor dem Starten der Adobe Campaign-Dienste das Warnskript **freezeInstance.js** aus, mit dem Sie die Datenbank aller Objekte löschen können, die beim Starten der Sicherung ausgeführt wurden.

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >Der Befehl wird standardmäßig im Modus **dry** gestartet und listet alle Anforderungen auf, die von diesem Befehl ausgeführt wurden, ohne sie zu starten. Verwenden Sie **run** im -Befehl, um Warnanfragen auszuführen.

1. Stellen Sie sicher, dass Ihre Sicherungen korrekt sind, indem Sie versuchen, sie wiederherzustellen. Stellen Sie sicher, dass Sie Zugriff auf Ihre Datenbank, Ihre Tabellen, Ihre Daten usw. haben.
1. Testen Sie das Migrationsverfahren in der Entwicklungsumgebung.

   Die vollständigen Verfahren werden im Abschnitt [Voraussetzungen für die Migration zu Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) beschrieben.

1. Wenn die Migration der Entwicklungsumgebung erfolgreich ist, können Sie die Produktionsumgebung migrieren.

>[!IMPORTANT]
>
>Aufgrund von Änderungen an der Datenstruktur ist der Import und Export von Datenpaketen zwischen einer v5-Plattform und einer v7-Plattform nicht möglich.

>[!NOTE]
>
>Mit dem Adobe Campaign-Aktualisierungsbefehl (**postupgrade**) können Sie Ressourcen synchronisieren und Schemas und die Datenbank aktualisieren. Dieser Vorgang kann nur einmal auf dem Anwendungsserver ausgeführt werden. Nach dem Synchronisieren von Ressourcen können Sie mit dem Befehl **postupgrade** erkennen, ob die Synchronisierung Fehler oder Warnungen erzeugt.

## Migrationswerkzeuge {#migration-tools}

Mithilfe verschiedener Optionen können Sie die Auswirkungen einer Migration messen und potenzielle Probleme identifizieren. Diese Optionen werden ausgeführt:

* im Befehl **config** :

   ```
   nlserver.exe config <option> -instance:<instanceName>
   ```

* oder beim Postupgrade:

   ```
   nlserver.exe config -postupgrade <option> -instance:<instanceName>
   ```

>[!NOTE]
>
>Sie müssen die Option **-instance:`<instanceame>`** verwenden. Es wird nicht empfohlen, die Option **-allinstances** zu verwenden.

### -showCustomEntities und -showDeletedEntities-Optionen {#showcustomentities-and--showdeletedentities-options}

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

### Überprüfungsverfahren {#verification-process}

Dieser Prozess ist standardmäßig in den Befehl postupgrade integriert und ermöglicht die Anzeige von Warnungen und Fehlern, die dazu führen können, dass die Migration fehlschlägt. **Wenn Fehler angezeigt werden, wurde die Migration nicht ausgeführt.** Korrigieren Sie in diesem Fall alle Fehler und starten Sie das Postupgrade erneut.

Mit dem folgenden Befehl können Sie den Verifizierungsprozess selbst (ohne Migration) starten:

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
   <th> Fehler-code<br /> </th> 
   <th> Logtyp<br /> </th> 
   <th> Erklärung<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> .@<br /> </td> 
   <td> PU-0001<br /> </td> 
   <td> Warnung<br /> </td> 
   <td> Diese Syntax wird bei der Versandpersonalisierung nicht mehr unterstützt. Siehe <a href="../../migration/using/general-configurations.md#javascript" target="_blank">JavaScript</a>. Überprüfen Sie andernfalls, ob der Werttyp korrekt ist.<br /> </td> 
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
   <td> Diese Verbindungsmethode darf nicht mehr verwendet werden. Siehe <a href="../../migration/using/general-configurations.md#identified-web-applications" target="_blank">Identifizierte Webanwendungen</a>.<br />. </td> 
  </tr> 
  <tr> 
   <td> new SoapMethodCall(<br /> </td> 
   <td> PU-0004<br /> </td> 
   <td> Warnung<br /> </td> 
   <td> Diese Funktion wird nur unterstützt, wenn sie im JavaScript-Code verwendet wird, der aus einer Sicherheitszone ausgeführt wird, die sich im Modus <strong>sessionTokenOnly</strong> befindet.<br /> </td> 
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
   <td> Dieser Fehlertyp führt zu einem Migrationsfehler. Siehe <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>. Wenn Sie Fehlerprotokolle für Webanwendungen vom Typ Übersicht erhalten (Migration von v6.02), finden Sie weitere Informationen unter <a href="../../migration/using/specific-configurations-in-v6-02.md#web-applications" target="_blank">Konfigurieren von Campaign</a>.<br />. </td> 
  </tr>
  <tr> 
   <td> crmDeploymentType="onpremise"<br /> </td> 
   <td> PU-0007<br /> </td> 
   <td> Fehler<br /> </td> 
   <td> Diese Art der Bereitstellung wird nicht mehr unterstützt. Der Bereitstellungstyp des CRM-Connectors für Office 365 und On-Premise Microsoft ist jetzt veraltet.</a>. Informationen zum Wechsel zur Web-API-Bereitstellung finden Sie unter <a href="../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft" target="_blank">Webanwendungen</a>.<br /> </td>
  </tr> 
 </tbody> 
</table>

Außerdem wird eine Datenbank- und Schema-Konsistenz-Prüfung durchgeführt.

### Wiederherstellungsoption {#restoration-option}

Mit dieser Option können Sie native Objekte wiederherstellen, wenn sie geändert wurden. Für jedes wiederhergestellte Objekt wird eine Sicherung Ihrer Änderungen im ausgewählten Ordner gespeichert:

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instanceName>
```

>[!NOTE]
>
>Es wird dringend empfohlen, absolute Ordnerpfade zu verwenden und die Ordnerstruktur beizubehalten. Beispiel: backupFolder\nms\srcSchema\billing.xml

### Migration fortsetzen {#resuming-migration}

Wenn Sie das Postupgrade nach einem Migrationsfehler neu starten, wird es von der Stelle fortgesetzt, an der es angehalten wurde.

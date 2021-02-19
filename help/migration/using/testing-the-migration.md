---
solution: Campaign Classic
product: campaign
title: Testen der Migration
description: Testen der Migration
audience: migration
content-type: reference
topic-tags: migration-procedure
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 3%

---


# Testen der Migration{#testing-the-migration}

## Allgemeines Verfahren {#general-procedure}

Je nach Konfiguration gibt es verschiedene Möglichkeiten, Migrationstests durchzuführen.

Sie sollten über eine Test-/Entwicklungs-Umgebung verfügen, um Migrationstests durchzuführen. Entwicklungs-Umgebung unterliegen einer Lizenz: Überprüfen Sie Ihren Lizenzvertrag oder wenden Sie sich an den Vertriebsservice von Adobe Campaign.

1. Beenden Sie alle laufenden Entwicklungen und führen Sie sie in die Umgebung der Produktion.
1. Erstellen Sie eine Sicherung der Development-Umgebung-Datenbank.
1. Beenden Sie alle Adobe Campaign-Prozesse auf der Entwicklungsinstanz.
1. Erstellen Sie eine Sicherungskopie der Produktionsdatenbank und stellen Sie sie als Umgebung der Umgebung wieder her.
1. Bevor Sie die Adobe Campaign-Dienste starten, führen Sie das Warnskript **frizeInstance.js** aus, mit dem Sie die Datenbank aller Objekte löschen können, die beim Starten der Sicherung ausgeführt wurden.

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >Der Befehl startet standardmäßig im Modus **dry** und Liste alle Anforderungen, die von diesem Befehl ausgeführt wurden, ohne sie zu starten. Um Warnanforderungen auszuführen, verwenden Sie **run** im Befehl.

1. Stellen Sie sicher, dass Ihre Sicherungen korrekt sind, indem Sie versuchen, sie wiederherzustellen. Stellen Sie sicher, dass Sie auf Ihre Datenbank, Ihre Tabellen, Ihre Daten usw. zugreifen können.
1. Testen Sie das Migrationsverfahren in der Development-Umgebung.

   Die vollständigen Verfahren finden Sie im Abschnitt [Voraussetzungen für die Migration zu Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md).

1. Wenn die Migration der Development-Umgebung erfolgreich ist, können Sie die Umgebung für die Produktion migrieren.

>[!IMPORTANT]
>
>Aufgrund von Änderungen an der Datenstruktur ist das Importieren und Exportieren von Datenpackagen zwischen einer v5- und einer v7-Plattform nicht möglich.

>[!NOTE]
>
>Mit dem Adobe Campaign-Aktualisierungsbefehl (**postupgrade**) können Sie Ressourcen synchronisieren und Schema und die Datenbank aktualisieren. Dieser Vorgang kann nur einmal und nur auf dem Anwendungsserver ausgeführt werden. Nach dem Synchronisieren von Ressourcen können Sie mit dem Befehl **postupgrade** erkennen, ob die Synchronisierung Fehler oder Warnungen hervorruft.

## Migrationstools {#migration-tools}

Mit verschiedenen Optionen können Sie die Auswirkungen einer Migration messen und potenzielle Probleme identifizieren. Diese Optionen sind auszuführen:

* im Befehl **config**:

   ```
   nlserver.exe config <option> -instance:<instanceName>
   ```

* oder nach der Aktualisierung:

   ```
   nlserver.exe config -postupgrade <option> -instance:<instanceName>
   ```

>[!NOTE]
>
>Sie müssen die Option **-instance:`<instanceame>`** verwenden. Es wird nicht empfohlen, die Option **-allinstances** zu verwenden.

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

### Überprüfungsprozess {#verification-process}

Dieser Prozess, der als Standard in den Befehl nach der Aktualisierung integriert ist, ermöglicht Ihnen die Anzeige von Warnungen und Fehlern, die die Migration zum Fehler machen könnten. **Wenn Fehler angezeigt werden, wurde die Migration nicht ausgeführt.** Wenn dies der Fall ist, korrigieren Sie alle Fehler und wiederholen Sie den Beginn nach der Aktualisierung.

Sie können den Verifizierungsprozess selbst (ohne Migration) mit dem folgenden Befehl Beginn ausführen:

```
nlserver.exe config -postupgrade -check -instance:<instanceName>
```

>[!NOTE]
>
>Bitte ignorieren Sie alle Warnungen und Fehler mit dem JST-310040-Code.

Nach den folgenden Ausdrücken wird gesucht (Groß-/Kleinschreibung beachten):

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
   <td> Diese Syntaxart wird bei der Personalisierung von Versänden nicht mehr unterstützt. Siehe <a href="../../migration/using/general-configurations.md#javascript" target="_blank">JavaScript</a>. Überprüfen Sie andernfalls, ob der Werttyp korrekt ist.<br /> </td> 
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
   <td> Diese Verbindungsmethode darf nicht mehr verwendet werden. Siehe <a href="../../migration/using/general-configurations.md#identified-web-applications" target="_blank">Identifizierte Webanwendungen</a>.<br /> </td> 
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
   <td> Dieser Fehlertyp führt zu einem Migrationsfehler. Siehe <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>. Wenn Sie Übersichtsfehler-Fehlerprotokolle für Webanwendungen erhalten (Migration von v6.02), lesen Sie <a href="../../migration/using/specific-configurations-in-v6-02.md#web-applications" target="_blank">Webanwendungen</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Außerdem wird eine Datenbank- und eine Schema-Kohärenzprüfung durchgeführt.

### Wiederherstellungs-Option {#restoration-option}

Mit dieser Option können Sie vordefinierte Objekte wiederherstellen, wenn sie geändert wurden. Für jedes wiederhergestellte Objekt wird eine Sicherungskopie der Änderungen im ausgewählten Ordner gespeichert:

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instanceName>
```

>[!NOTE]
>
>Es wird dringend empfohlen, absolute Ordnerpfade zu verwenden und die Ordnerstruktur beizubehalten. Beispiel: backupFolder\nms\srcSchema\billing.xml.

### Migration fortsetzen {#resuming-migration}

Wenn Sie die Nachaktualisierung nach einem Migrationsfehler neu starten, wird sie von demselben Ort, an dem sie beendet wurde, wieder aufgenommen.

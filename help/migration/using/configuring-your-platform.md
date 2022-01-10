---
product: campaign
title: Anpassen der Konfiguration
description: Erfahren Sie, wie Sie Ihre Konfiguration vor und nach einer Migration zu Campaign v7 anpassen.
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
source-git-commit: 327f220d6700242308ef3738a38cc95b970e3f46
workflow-type: tm+mt
source-wordcount: '1985'
ht-degree: 4%

---

# Anpassen der Konfiguration{#configuring-your-platform}

![](../../assets/v7-only.svg)

Bestimmte wichtige Änderungen in Adobe Campaign v7 erfordern eine spezifische Konfiguration. Diese Konfigurationen können vor oder nach der Migration erforderlich sein.

Detaillierte Konfigurationen, die in Adobe Campaign v7 bei der Migration von Campaign v5 oder v6 durchzuführen sind, finden Sie unter [diese Seite](general-configurations.md).


Während der Migration wird die Variable **NmsRecipient** -Tabelle aus der Schemadefinition neu erstellt. Änderungen an der SQL-Struktur dieser Tabelle außerhalb von Adobe Campaign gehen verloren.

Beispiel für zu prüfende Elemente:

* Wenn Sie eine Spalte (oder einen Index) zum **NmsRecipient** -Tabelle, aber Sie haben sie nicht im Schema detailliert, wird dies nicht gespeichert.
* Die **tablespace** -Attribut nimmt standardmäßig seine Werte zurück, d. h. die im Softwareverteilungs-Assistenten definierten Werte.
* Wenn Sie eine Referenzansicht zum **NmsRecipient** -Tabelle, müssen Sie sie vor der Migration löschen.


## Vor der Migration {#before-the-migration}

Bei der Migration zu Adobe Campaign v7 müssen die folgenden Elemente konfiguriert werden. Diese Elemente müssen vor dem Start der **postupgrade**.

* Zeitzonen

   Bei einer Migration von einer Plattform der Version 5.11 müssen Sie die Zeitzone angeben, die während des Postupgrades verwendet werden soll.

   Wenn Sie den Modus &quot;Multi-Timezone&quot;verwenden möchten, lesen Sie den Abschnitt [diesem Abschnitt](../../migration/using/general-configurations.md#time-zones).

   Wenn Sie Oracle als Datenbank verwenden, überprüfen Sie, ob die Oracle-Zeitzonendateien ordnungsgemäß zwischen dem Anwendungsserver und dem Datenbankserver synchronisiert wurden. [Weitere Informationen](../../migration/using/general-configurations.md#oracle)

* Sicherheitszonen

   Aus Sicherheitsgründen ist die Adobe Campaign-Plattform nicht mehr standardmäßig verfügbar: Sie müssen die Sicherheitszonen konfigurieren. Dazu müssen die Benutzer-IP-Adressen vor der Migration erfasst werden. [Weitere Informationen](../../migration/using/general-configurations.md#security)

* Syntax

   Einige JavaScript-Codes werden in der v7-Version möglicherweise nicht mehr akzeptiert, da ein neuer Interpreter verwendet wird. [Weitere Informationen](../../migration/using/general-configurations.md#javascript).

   In Adobe Campaign v7 wird eine neue Syntax eingeführt, die die SQLData-basierte Syntax ersetzt. Wenn Sie Code-Elemente mit dieser Syntax verwenden, müssen Sie sie anpassen. [Weitere Informationen](../../migration/using/general-configurations.md#sqldata)

* Passwörter

   Sie müssen die **Admin** und **intern** Kennwörter. [Weitere Informationen](../../migration/using/before-starting-migration.md#user-passwords)

* Baumstruktur

   Wenn Sie von einer Plattform der Version 5.11 migrieren, müssen Sie die Baumstrukturordner gemäß den Adobe Campaign v6-Normen neu organisieren. [Weitere Informationen](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11).

* Interaction

   Wenn Sie von Campaign v6.02 migrieren und die Variable  **Interaction** -Modul verwenden, müssen Sie alle 6.02 Schemareverweise löschen, die in v7 nicht mehr vorhanden sind. [Weitere Informationen](../../migration/using/general-configurations.md#interaction)

## Nach der Migration {#after-the-migration}

Nach Ausführung **postupgrade**, aktivieren und konfigurieren Sie die folgenden Elemente:

* Mirrorseiten

   Der Gestaltungsbaustein für die Mirrorseite wurde mit v6.x geändert. Diese neue Version verbessert die Sicherheit beim Zugriff auf diese Seiten.

   Wenn Sie den Gestaltungsbaustein v5 in Ihren Nachrichten verwendet haben, schlägt die Anzeige der Mirrorseite fehl. Adobe empfiehlt dringend, den neuen Gestaltungsbaustein beim Einfügen der Mirrorseite in Ihre Nachrichten zu verwenden.

   Als vorübergehende Problemumgehung (und da die Mirrorseiten noch live sind) können Sie jedoch zum alten Gestaltungsbaustein zurückkehren, um dieses Problem zu vermeiden, indem Sie die Option ändern **[!UICONTROL XtkAcceptOldPasswords]** und legen Sie **[!UICONTROL 1]**. Dies hat keine Auswirkungen auf die Verwendung des neuen Gestaltungsbausteins v6.x.

* Syntax

   Wenn während des Postupgrades Syntaxfehler auftreten, müssen Sie die **allowSQLInjection** in der **serverConf.xml** -Datei, da Sie dadurch Zeit haben, den Code neu zu schreiben. Nachdem der Code angepasst wurde, stellen Sie sicher, dass Sie die Sicherheit erneut aktivieren. [Weitere Informationen](../../migration/using/general-configurations.md#sqldata)

* Konflikte

   Die Migration wird durch ein Postupgrade durchgeführt und Konflikte können in Berichten, Formularen oder Webanwendungen auftreten. Diese Konflikte können über die Konsole gelöst werden. [Weitere Informationen](../../migration/using/general-configurations.md#conflicts)

* Tomcat

   Wenn Sie den Installationsordner angepasst haben, stellen Sie sicher, dass er nach der Migration korrekt aktualisiert wurde. [Weitere Informationen](../../migration/using/general-configurations.md#tomcat)

* Berichte

   Alle nativen Berichte verwenden derzeit die Rendering-Engine v6.x. Wenn Sie den Berichten JavaScript-Code hinzugefügt haben, können einige Elemente betroffen sein. [Weitere Informationen](../../migration/using/general-configurations.md#reports)

* Webanwendungen

   Wenn nach dem Postupgrade Probleme beim Herstellen einer Verbindung zu Ihren identifizierten Webanwendungen auftreten, müssen Sie die **allowUserPassword** und **sessionTokenOnly** Optionen in **serverConf.xml** -Datei. Um Sicherheitsprobleme zu vermeiden, müssen diese beiden Optionen reaktiviert werden, nachdem das Problem gelöst wurde. [Weitere Informationen](../../migration/using/general-configurations.md#identified-web-applications)

   Abhängig vom Typ der Webanwendungen und ihrer Konfiguration müssen Sie zusätzliche Manipulationen durchführen, um sicherzustellen, dass sie ordnungsgemäß funktionieren. [Weitere Informationen](../../migration/using/general-configurations.md#web-applications)

   Bei der Migration von einer v5.11-Plattform müssen zusätzliche Konfigurationen vorgenommen werden. [Weitere Informationen](../../migration/using/general-configurations.md#specific-configurations-in-v5-11.md)

* Sicherheitszonen

   Bevor Sie den Server starten, müssen Sie die Sicherheitszonen konfigurieren. [Weitere Infos](../../installation/using/security-zones.md) und [hier sehen](../../migration/using/general-configurations.md#security)

* Workflows

   Wenn Sie von einer Plattform der Version 5.11 migrieren, müssen Sie den Ordner &quot;Workflows&quot;überprüfen. [Weitere Informationen](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

* Tracking

   Bei der Migration von einer v5.11-Plattform müssen Sie den Tracking-Modus konfigurieren. [Weitere Informationen](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

* Interaction

   Wenn Sie **Interaction** müssen Sie alle Parameter nach der Migration anpassen. [Weitere Informationen](../../migration/using/general-configurations.md#interaction)

* Dashboards

   Wenn ein Clientfehler angezeigt wird, müssen Sie entweder Ihre Dashboards mit dem neuen Adobe Campaign v7-Code aktualisieren oder die folgenden Dateien manuell von der v6.02-Instanz in die v7-Instanz kopieren:

   ```
   v6.02 files and spaces:
   /usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
   /usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
   v6.1 files and spaces:
   /usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
   /usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
   ```


## Spezifische Konfigurationen von v5.11 bis v7{#specific-configurations-in-v5-11}

![](../../assets/v7-only.svg)

In diesem Abschnitt wird die zusätzliche Konfiguration beschrieben, die für die Migration von Version 5.11 erforderlich ist. Sie sollten auch die Einstellungen konfigurieren, die im Abschnitt [Allgemeine Konfigurationen](../../migration/using/general-configurations.md) Abschnitt.

### Web-Anwendungen {#web-applications-v5}

Die folgende Warnung wird während der Migration automatisch angezeigt:

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side JavaScript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Einige Komponenten von Webanwendungen, z. B. die verschiedenen Formelfelder, haben @id-Attribute. Diese werden im XML-Code von Webanwendungen verwendet und nicht mehr auf die gleiche Weise generiert. Sie sind in der Benutzeroberfläche nicht sichtbar und dürfen normalerweise nicht verwendet werden. In einigen Fällen können jedoch @id-Attribute verwendet worden sein, um das Rendering von Webanwendungen zu personalisieren, z. B. über ein Stylesheet oder mit JavaScript-Code.

Während der Migration **must** Überprüfen Sie den in der Warnung angegebenen Pfad der Protokolldatei:

* **Die Datei ist nicht leer**: Es enthält Warnungen, die sich auf Inkonsistenzen beziehen, die vor der Migration aufgezeichnet wurden und noch existieren. Dies kann JavaScript-Code in einer Webanwendung sein, der auf eine nicht vorhandene ID verweist. Jeder Fehler muss überprüft und korrigiert werden.
* **Die Datei ist leer**: Dies bedeutet, dass Adobe Campaign keine Probleme erkannt hat.

Unabhängig davon, ob die Datei leer ist oder nicht, müssen Sie sicherstellen, dass diese IDs nicht für die Konfiguration an anderer Stelle verwendet werden (und die Konfiguration anpassen, falls dies der Fall ist).

### Workflows {#workflows}

Da sich der Name des Adobe Campaign-Installationsordners geändert hat, funktionieren einige Workflows nach der Migration möglicherweise nicht mehr. Wenn ein Workflow in einer seiner Aktivitäten auf das Verzeichnis nl5 verweist, wird ein Fehler ausgegeben. Ersetzen Sie diese Referenz durch **build**. Sie können eine SQL-Abfrage ausführen, um diese Workflows zu identifizieren (PostgreSQL-Beispiel):

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

### MySQL {#mysql}

>[!CAUTION]
>
>MySQL wird nur in v7 als wichtigste Datenbank-Engine bei der Migration von Version 6.02 oder 5.11 mithilfe dieser Engine unterstützt.

MySQL verwaltet keine Zeitzonen standardmäßig. Führen Sie den folgenden Befehl aus, um die Zeitzonenverwaltung zu aktivieren:

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>Weitere Informationen finden Sie im Abschnitt [https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html) Seite.

Wenn Änderungen an der Datenbankstruktur vorgenommen wurden, beispielsweise während der Konfiguration (Erstellung spezifischer Indizes, Erstellung von SQL-Ansichten usw.), sollten bei der Migration bestimmte Vorsichtsmaßnahmen getroffen werden. Gewisse Änderungen können aus Inkompatibilitäten mit dem Migrationsprozess hervorgehen. Erstellen von SQL-Ansichten mit **Zeitstempel** -Felder sind nicht mit der **usetimestamptz** -Option. Wir empfehlen Ihnen daher, die folgenden Empfehlungen zu befolgen:

1. Sichern Sie die Datenbank, bevor Sie mit der Migration beginnen.
1. Löschen Sie SQL-Änderungen.
1. Führen Sie das Postupgrade durch
   >[!NOTE]
   >
   >Sie müssen die in [diesem Abschnitt](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md).
1. SQL-Änderungen neu integrieren.

In diesem Beispiel wird eine **NmcTrackingLogMessages** -Ansicht erstellt wurde und diese **Zeitstempel** Feld namens **tslog**. In diesem Fall schlägt der Migrationsprozess fehl und die folgende Fehlermeldung wird angezeigt:

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

Um sicherzustellen, dass das Postupgrade funktioniert, müssen Sie die Ansicht vor der Migration löschen und nach der Migration neu erstellen und sie gleichzeitig an den TIMESTAMP MIT TIMEZONE-Modus anpassen.

### Tracking {#tracking}

Die Tracking-Formel wurde geändert. Bei der Migration wird die alte Formel (v5) durch die neue (v7) ersetzt. Wenn Sie eine personalisierte Formel in Adobe Campaign v5 verwenden, muss diese Konfiguration in Adobe Campaign v7 angepasst werden (**NmsTracking_ClickFormula** und **NmsTracking_OpenFormula** Optionen).

Auch die Webtracking-Verwaltung wurde geändert. Nachdem die Migration zu v7 durchgeführt wurde, müssen Sie den Softwareverteilungs-Assistenten starten, um die Konfiguration des Webtrackings abzuschließen.

![](assets/migration_web_tracking.png)

Drei Modi sind verfügbar:

* **Sitzungs-Webtracking**: Wenn die Variable **[!UICONTROL Leads]** -Paket nicht installiert wurde, ist diese Option standardmäßig aktiviert. Diese Option ist hinsichtlich der Leistung am besten geeignet und ermöglicht es Ihnen, die Größe der Trackinglogs zu begrenzen.
* **Dauerhaftes Webtracking**
* **Anonym Web Tracking**: Wenn die Variable **[!UICONTROL Leads]** installiert ist, ist diese Option standardmäßig aktiviert. Dies ist die ressourcenintensivste Option. Wie oben gezeigt, wird die **sSourceId** -Spalte muss indiziert sein (in der Tracking-Tabelle und der **CrmIncomingLead** Tabelle).

>[!NOTE]
>
>Weitere Informationen zu diesen drei Modi finden Sie unter [diesem Abschnitt](../../configuration/using/about-web-tracking.md).

### Baumstruktur von Adobe Campaign v7 {#campaign-vseven-tree-structure}

Während der Migration wird die Baumstruktur automatisch basierend auf den v7-Standards neu organisiert. Die neuen Ordner werden hinzugefügt, die veralteten Ordner werden gelöscht und ihr Inhalt wird im Ordner &quot;Zu verschieben&quot;abgelegt. Alle Elemente in diesem Ordner müssen nach der Migration überprüft werden. Der Berater muss entscheiden, sie entweder zu behalten oder sie zu löschen. Die zu pflegenden Gegenstände müssen dann an den richtigen Ort verschoben werden.

Es wurde eine Option zum Deaktivieren der automatischen Migration der Navigationsstruktur hinzugefügt. Dieser Vorgang ist jetzt manuell. Veraltete Ordner werden nicht gelöscht und neue Ordner werden nicht hinzugefügt. Diese Option sollte nur verwendet werden, wenn die vordefinierte v5-Navigationsstruktur zu vielen Änderungen unterzogen wurde. Fügen Sie die Option vor der Migration zur Konsole im **[!UICONTROL Administration > Optionen]** node:

* Interner Name: NlMigration_KeepFolderStructure
* Datentyp: Ganzzahl
* Wert (text): 1

Wenn Sie diese Option verwenden, müssen Sie nach der Migration veraltete Ordner löschen, die neuen Ordner hinzufügen und alle erforderlichen Prüfungen durchführen.

**Liste neuer Ordner**:

Nach der Migration müssen die folgenden Ordner hinzugefügt werden:

| Interner Name | Titel | Bedingung |
|---|---|---|
| nmsAutoObjects | Automatisch erstellte Objekte | - |
| nmsCampaignAdmin | Kampagnenverwaltung | - |
| nmsCampaignMgt | Kampagnenverwaltung | - |
| nmsCampaignRes | Kampagnenverwaltung | - |
| nmsModels | Vorlagen | - |
| nmsOnlineRes | Online | - |
| nmsProduction | Produktion | - |
| nmsProfilProcess | Prozesse | - |
| xtkDashboard | Dashboards | - |
| xtkPlatformAdmin | Plattform | - |
| nmsLocalOrgUnit | Organisationseinheiten | - |
| nmsMRM | Marketing-Ressourcen (MRM) | MRM installiert |
| nmsOperations | Kampagnen | Campaign installiert |

**Liste veralteter Ordner**:

Die veralteten Ordner, die nach der Migration gelöscht werden sollen, lauten wie folgt:

>[!NOTE]
>
>Der gesamte Inhalt der veralteten Ordner muss überprüft werden und der Berater entscheidet für jedes Element, ob es beibehalten oder gelöscht werden soll. Die beizubehaltenden Gegenstände müssen an den entsprechenden Ort verschoben werden.

| Interner Name | Titel | Bedingung |
|---|---|---|
| nmsAdministration | Administration | - |
| nmsDeliveryMgt | Kampagnenausführung | - |
| ncmContent | Content Management | Content Manager installiert |
| ncmForm | Formular | Content Manager installiert |
| ncmImage | Bilder | Content Manager installiert |
| ncmJavascript | JavaScript-Codes | Content Manager installiert |
| ncmJst | JavaScript-Templates | Content Manager installiert |
| ncmParameters | Konfiguration | Content Manager installiert |
| ncmSrcSchema | Datenschemata | Content Manager installiert |
| ncmStylesheet | XSL-Stildateien | Content Manager installiert |
| nmsAdminPlan | Administration | Campaign installiert |
| nmsResourcePlan | Ressourcen | Campaign installiert |
| nmsResourcesModels | Vorlagen | Campaign installiert |
| nmsRootPlan | Kampagnenverwaltung | Campaign installiert |
| nmsOperator | Marketing-Operatoren | MRM installiert |


## Spezifische Konfigurationen von v6.02 bis v7{#specific-configurations-in-v6-02}

![](../../assets/v7-only.svg)

Im folgenden Abschnitt wird die zusätzliche Konfiguration beschrieben, die für die Migration von v6.02 erforderlich ist. Sie sollten auch die Einstellungen konfigurieren, die im Abschnitt [diese Seite](../../migration/using/general-configurations.md).

### Web-Anwendungen {#web-applications-v6}

Wenn Sie von v6.02 migrieren, werden möglicherweise Fehlerprotokolle zu Webanwendungen vom Typ &quot;Übersicht&quot;angezeigt. Beispiele für Fehlermeldungen:

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

Diese Webanwendungen verwendeten SQLData und sind aufgrund erhöhter Sicherheit nicht mit v7 kompatibel. Diese Fehler führen zu einem Migrationsfehler.

Wenn Sie diese Webanwendungen nicht verwendet haben, führen Sie das folgende Bereinigungsskript aus und führen Sie das Postupgrade erneut aus:

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

Wenn Sie diese Webanwendungen geändert haben und sie weiterhin in v7 verwenden möchten, müssen Sie die **allowSQLInjection** in Ihren verschiedenen Sicherheitszonen und starten Sie das Postupgrade neu. Siehe Abschnitt [SQLData](../../migration/using/general-configurations.md#sqldata) finden Sie weitere Informationen dazu.

### Message Center {#message-center}

Nach der Migration der Kontrollinstanz von Message Center müssen Sie die Transaktionsnachrichten-Vorlagen erneut veröffentlichen, damit sie funktionieren.

In v7 haben sich die Namen der Transaktionsnachrichten-Vorlagen auf Ausführungsinstanzen geändert. Sie erhalten derzeit das Präfix des Operatornamens, der der Kontrollinstanz entspricht, auf der sie erstellt werden, z. B. **control1_template1_rt** , **control1** der Name des Benutzers). Wenn Sie eine große Menge an Vorlagen haben, empfehlen wir, alte Vorlagen in Kontrollinstanzen zu löschen.
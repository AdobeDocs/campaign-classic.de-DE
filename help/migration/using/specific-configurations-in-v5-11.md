---
product: campaign
title: Spezifische Konfigurationen in v5.11
description: Spezifische Konfigurationen in v5.11
audience: migration
content-type: reference
topic-tags: configuration
exl-id: 978e1249-f79b-4f5f-9a94-3bb2510785de
source-git-commit: e719c8c94f1c08c6601b3386ccd99d250c9e606b
workflow-type: tm+mt
source-wordcount: '1045'
ht-degree: 5%

---

# Spezifische Konfigurationen in v5.11{#specific-configurations-in-v5-11}

![](../../assets/v7-only.svg)

In diesem Abschnitt wird die zusätzliche Konfiguration beschrieben, die für die Migration von Version 5.11 erforderlich ist. Sie sollten auch die Einstellungen konfigurieren, die im Abschnitt [Allgemeine Konfigurationen](../../migration/using/general-configurations.md) Abschnitt.

## Web-Anwendungen {#web-applications}

Die folgende Warnung wird während der Migration automatisch angezeigt:

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side JavaScript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Einige Komponenten von Webanwendungen, z. B. die verschiedenen Formelfelder, haben @id-Attribute. Diese werden im XML-Code von Webanwendungen verwendet und nicht mehr auf die gleiche Weise generiert. Sie sind in der Benutzeroberfläche nicht sichtbar und dürfen normalerweise nicht verwendet werden. In einigen Fällen können jedoch @id-Attribute verwendet worden sein, um das Rendering von Webanwendungen zu personalisieren, z. B. über ein Stylesheet oder mit JavaScript-Code.

Während der Migration **must** Überprüfen Sie den in der Warnung angegebenen Pfad der Protokolldatei:

* **Die Datei ist nicht leer**: Es enthält Warnungen, die sich auf Inkonsistenzen beziehen, die vor der Migration aufgezeichnet wurden und noch existieren. Dies kann JavaScript-Code in einer Webanwendung sein, der auf eine nicht vorhandene ID verweist. Jeder Fehler muss überprüft und korrigiert werden.
* **Die Datei ist leer**: Dies bedeutet, dass Adobe Campaign keine Probleme erkannt hat.

Unabhängig davon, ob die Datei leer ist oder nicht, müssen Sie sicherstellen, dass diese IDs nicht für die Konfiguration an anderer Stelle verwendet werden (und die Konfiguration anpassen, falls dies der Fall ist).

## Workflows {#workflows}

Da sich der Name des Adobe Campaign-Installationsordners geändert hat, funktionieren einige Workflows nach der Migration möglicherweise nicht mehr. Wenn ein Workflow in einer seiner Aktivitäten auf das Verzeichnis nl5 verweist, wird ein Fehler ausgegeben. Ersetzen Sie diese Referenz durch **build**. Sie können eine SQL-Abfrage ausführen, um diese Workflows zu identifizieren (PostgreSQL-Beispiel):

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

## Benutzerfreundlichkeit {#user-friendliness}

Die Adobe Campaign v5.11-Homepage ist nicht mehr verfügbar.

Obwohl dies nicht empfohlen wird, gibt es bestimmte Lösungen, wenn Sie bestimmte Schnittstellen von Adobe Campaign v5.11 beibehalten möchten. Für weitere Informationen kontaktieren Sie uns bitte.

## MySQL {#mysql}

>[!IMPORTANT]
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
1. Führen Sie das Postupgrade gemäß dem im Abschnitt  [Voraussetzungen für die Migration auf Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) Abschnitt.
   >[!NOTE]
   >
   >Sie müssen unbedingt die Migrationsschritte ausführen, die im Abschnitt [Voraussetzungen für die Migration auf Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) Abschnitt.
1. SQL-Änderungen neu integrieren.

In diesem Beispiel wird eine **NmcTrackingLogMessages** -Ansicht erstellt wurde und diese **Zeitstempel** Feld namens **tslog**. In diesem Fall schlägt der Migrationsprozess fehl und die folgende Fehlermeldung wird angezeigt:

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

Um sicherzustellen, dass das Postupgrade funktioniert, müssen Sie die Ansicht vor der Migration löschen und nach der Migration neu erstellen und sie gleichzeitig an den TIMESTAMP MIT TIMEZONE-Modus anpassen.

## Tracking {#tracking}

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

## Baumstruktur von Adobe Campaign v7 {#campaign-vseven-tree-structure}

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

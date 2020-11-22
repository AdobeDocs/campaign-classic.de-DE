---
solution: Campaign Classic
product: campaign
title: Spezifische Konfigurationen in v5.11
description: Spezifische Konfigurationen in v5.11
audience: migration
content-type: reference
topic-tags: configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1045'
ht-degree: 5%

---


# Spezifische Konfigurationen in v5.11{#specific-configurations-in-v5-11}

In diesem Abschnitt werden die zusätzlichen Konfigurationsschritte beschrieben, die bei der Migration von Version 5.11 erforderlich sind. Sie sollten auch die Einstellungen konfigurieren, die im Abschnitt [Allgemeine Konfigurationen](../../migration/using/general-configurations.md) beschrieben sind.

## Webanwendungen {#web-applications}

Die folgende Warnung wird während der Migration automatisch angezeigt:

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side javascript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Einige Komponenten von Webanwendungen, z. B. die verschiedenen Formelfelder, haben @id-Attribute. Diese werden im XML-Code von Webanwendungen verwendet und nicht mehr auf dieselbe Weise generiert. Sie sind auf der Oberfläche nicht sichtbar und dürfen normalerweise nicht verwendet werden. In einigen Fällen wurden @id-Attribute jedoch möglicherweise verwendet, um die Darstellung von Webanwendungen zu personalisieren, z. B. über ein Stylesheet oder mit JavaScript-Code.

Während der Migration **müssen** Sie den in der Warnung angegebenen Pfad der Protokolldatei überprüfen:

* **Die Datei ist nicht leer**: Er enthält Warnungen, die Inkonsistenzen betreffen, die vor der Migration festgestellt wurden und die noch bestehen. Dies kann JavaScript-Code in einer Webanwendung sein, der auf eine nicht vorhandene ID verweist. Jeder Fehler muss überprüft und korrigiert werden.
* **Die Datei ist leer**: Dies bedeutet, dass Adobe Campaign keine Probleme erkannt hat.

Unabhängig davon, ob die Datei leer ist oder nicht, müssen Sie überprüfen, ob diese IDs nicht für die Konfiguration an anderer Stelle verwendet werden (und die Konfiguration anpassen, falls dies der Fall ist).

## Workflows {#workflows}

Da sich der Name des Installationsordners des Adobe Campaigns geändert hat, funktionieren einige Workflows nach der Migration möglicherweise nicht mehr. Wenn ein Workflow in einer seiner Aktivitäten auf den Ordner &quot;nl5&quot;verweist, wird ein Fehler ausgegeben. Ersetzen Sie diese Referenz durch **Build**. Sie können eine SQL-Abfrage ausführen, um folgende Workflows zu identifizieren (PostgreSQL-Beispiel):

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

## Benutzerfreundlichkeit {#user-friendliness}

Die Startseite Adobe Campaign v5.11 ist nicht mehr verfügbar.

Obwohl dies nicht empfohlen wird, gibt es bestimmte Lösungen, wenn Sie bestimmte Schnittstellen von Adobe Campaign v5.11 beibehalten möchten. Für weitere Informationen kontaktieren Sie uns bitte.

## MySQL {#mysql}

>[!IMPORTANT]
>
>MySQL wird nur in v7 als Haupt-Datenbank-Engine bei der Migration von Version 6.02 oder 5.11 mit dieser Engine unterstützt.

MySQL verwaltet Zeitzonen nicht standardmäßig. Führen Sie zum Aktivieren der Zeitzonenverwaltung den folgenden Befehl aus:

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>Weitere Informationen finden Sie auf der [Seite https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html) .

Wenn Änderungen an der Datenbankstruktur vorgenommen wurden, z. B. während der Konfiguration (Erstellung spezifischer Indizes, Erstellung von SQL-Ansichten usw.), sollten bei der Migration bestimmte Vorsichtsmaßnahmen getroffen werden. Tatsächlich können bestimmte Änderungen aus Inkompatibilitäten mit dem Migrationsverfahren herrühren. Das Erstellen von SQL-Ansichten mit **Zeitstempelfeldern** ist beispielsweise nicht mit der **Option usetimestamptz** kompatibel. Wir empfehlen Ihnen daher, die folgenden Empfehlungen zu befolgen:

1. Sichern Sie die Datenbank, bevor Sie die Migration starten.
1. Löschen Sie SQL-Änderungen.
1. Führen Sie die Nachrüstung gemäß dem im Abschnitt [Voraussetzungen für die Migration zu Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) beschriebenen Verfahren durch.
   >[!NOTE]
   >
   >Sie müssen unbedingt die Migrationsschritte ausführen, die im Abschnitt [Voraussetzungen für die Migration zu Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) beschrieben werden.
1. SQL-Änderungen neu integrieren.

In diesem Beispiel wurde eine **NmcTrackingLogMessages** -Ansicht erstellt, die ein **Zeitstempelfeld** mit dem Namen **tslog** enthält. In diesem Fall schlägt der Migrationsvorgang fehl und die folgende Fehlermeldung wird angezeigt:

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

Um sicherzustellen, dass die Nachrüstung funktioniert, müssen Sie die Ansicht vor der Migration löschen und nach der Migration neu erstellen, während Sie sie an den TIMEZONE-Modus anpassen.

## Tracking {#tracking}

Die Verfolgungsformel wurde geändert. Bei der Migration wird die alte Formel (v5) durch die neue (v7) ersetzt. Wenn Sie eine personalisierte Formel in Adobe Campaign v5 verwenden, muss diese Konfiguration in Adobe Campaign v7 angepasst werden (Optionen **NmsTracking_ClickFormel** und **NmsTracking_OpenFormel** ).

Das Webtracking-Management wurde ebenfalls geändert. Nachdem die Migration zu v7 durchgeführt wurde, müssen Sie den Bereitstellungsassistenten Beginn haben, um die Konfiguration der Web-Verfolgung abzuschließen.

![](assets/migration_web_tracking.png)

Drei Modi sind verfügbar:

* **Sitzungs-Webverfolgung**: Wenn das **[!UICONTROL Leads]** -Paket nicht installiert wurde, ist diese Option standardmäßig aktiviert. Diese Option ist hinsichtlich der Leistung am besten geeignet und ermöglicht es Ihnen, die Größe der Trackinglogs zu beschränken.
* **Ständiges Webtracking**
* **Anonymes Webtracking**: Wenn das **[!UICONTROL Leads]** -Paket installiert ist, ist diese Option standardmäßig aktiviert. Es ist die ressourcenintensivste Option. Wie oben beschrieben, muss die Spalte **sSourceId** indiziert werden (in der Verfolgungstabelle und der **Tabelle CrmIncomeLead** ).

>[!NOTE]
>
>For more information on these three modes, refer to [this section](../../configuration/using/about-web-tracking.md).

## Baumstruktur des Adobe Campaigns v7 {#campaign-vseven-tree-structure}

Während der Migration wird die Baumstruktur automatisch entsprechend den v7-Standards neu organisiert. Die neuen Ordner werden hinzugefügt, die veralteten Ordner gelöscht und ihr Inhalt wird im Ordner &quot;Zu verschieben&quot;abgelegt. Alle Elemente in diesem Ordner müssen nach der Migration überprüft werden, und der Berater muss entscheiden, sie entweder zu behalten oder sie zu löschen. Die zu pflegenden Gegenstände müssen dann an den richtigen Ort verschoben werden.

Es wurde eine Option zur Deaktivierung der automatischen Migration der Navigationsstruktur hinzugefügt. Dieser Vorgang ist jetzt manuell. Veraltete Ordner werden nicht gelöscht und neue Ordner werden nicht hinzugefügt. Diese Option sollte nur verwendet werden, wenn die vordefinierte v5-Navigationsstruktur zu vielen Änderungen unterzogen wurde. hinzufügen Sie die Option vor der Migration im Knoten **[!UICONTROL Administration > Optionen]** in die Konsole:

* Interner Name: NlMigration_KeepFolderStructure
* Datentyp: Integer
* Wert (Text): 1

Wenn Sie diese Option verwenden, müssen Sie nach der Migration veraltete Ordner löschen, die neuen Ordner hinzufügen und alle erforderlichen Prüfungen durchführen.

**Liste neuer Ordner**:

Nach der Migration müssen die folgenden Ordner hinzugefügt werden:

| Interner Name | Titel | Bedingung |
|---|---|---|
| nmsAutoObjects | Objekte automatisch erstellt | - |
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
| nmsOperations | Kampagnen | Kampagne installiert |

**Liste veralteter Ordner**:

Die veralteten Ordner, die nach der Migration gelöscht werden sollen, lauten wie folgt:

>[!NOTE]
>
>Der gesamte Inhalt der veralteten Ordner muss überprüft werden, und für jedes Element entscheidet der Berater, ob es beibehalten oder gelöscht werden soll. Die aufzubewahrenden Gegenstände müssen an den geeigneten Ort verbracht werden.

| Interner Name | Titel | Bedingung |
|---|---|---|
| nmsAdministration | Administration | - |
| nmsDeliveryMgt | Kampagnenausführung | - |
| ncmContent | Content Management | Content Manager installiert |
| ncmForm | Eingabeformular | Content Manager installiert |
| ncmImage | Bilder | Content Manager installiert |
| ncmJavascript | JavaScript-Codes | Content Manager installiert |
| ncmJst | JavaScript-Templates | Content Manager installiert |
| ncmParameters | Konfiguration       | Content Manager installiert |
| ncmSrcSchema | Datenschemata | Content Manager installiert |
| ncmStylesheet | XSL-Stildateien | Content Manager installiert |
| nmsAdminPlan | Administration | Kampagne installiert |
| nmsResourcePlan | Ressourcen | Kampagne installiert |
| nmsResourcesModels | Vorlagen | Kampagne installiert |
| nmsRootPlan | Kampagnenverwaltung | Kampagne installiert |
| nmsOperator | Marketing-Operatoren | MRM installiert |


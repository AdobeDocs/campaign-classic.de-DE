---
solution: Campaign Classic
product: campaign
title: Datensynchronisierung über CRM-Connectoren
description: Daten zwischen Campaign und Ihrem CRM verwalten
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 2838ced5f5d562914c0791e6a0b8f02dd61006b4
workflow-type: tm+mt
source-wordcount: '1618'
ht-degree: 100%

---


# Datensynchronisation zwischen Campaign und dem CRM-System {#data-synchronization}

Die Datensynchronisation zwischen Adobe Campaign und dem CRM-System erfolgt über die spezifische Workflow-Aktivität [CRM-Connector](../../workflow/using/crm-connector.md).

Erstellen Sie zum Importieren der Daten aus Microsoft Dynamics in Adobe Campaign beispielsweise folgenden Workflow:

![](assets/crm_connectors_msdynamics_07.png)

Dieser Workflow importiert die Kontakte über Microsoft Dynamics, synchronisiert sie mit den in Adobe Campaign vorhandenen Daten, löscht doppelte Kontakte und aktualisiert die Adobe Campaign-Datenbank.

Die Aktivität **[!UICONTROL CRM-Connector]** muss für die Synchronisation der Daten konfiguriert werden.

![](assets/crm_connectors_msdynamics_08.png)

Mit dieser Aktivität können Sie:

* Aus dem CRM-System importieren – [Weitere Informationen](#importing-from-the-crm)
* In das CRM-System exportieren – [Weitere Informationen](#exporting-to-the-crm)
* Objekte importieren, die im CRM gelöscht wurden – [Weitere Informationen](#importing-objects-deleted-in-the-crm)
* Objekte im CRM löschen – [Weitere Informationen](#deleting-objects-in-the-crm)

![](assets/crm_task_select_op.png)

Wählen Sie zunächst das externe Konto aus, das dem CRM-System entspricht, mit dem Sie eine Synchronisation konfigurieren möchten, und anschließend das zu synchronisierende Objekt: Konto, Opportunities, Leads, Kontakte etc.

![](assets/crm_task_select_obj.png)

Die Konfiguration der Aktivität hängt von der gewählten Option ab und wird im Folgenden dargestellt:

## Import aus CRM {#importing-from-the-crm}

Zum Import von CRM-Daten in Adobe Campaign ist ein Workflow nach folgendem Muster zu erstellen:

![](assets/crm_wf_import.png)

Gehen Sie zur Konfiguration der **[!UICONTROL CRM-Connector]**-Aktivität wie folgt vor:

1. Wählen Sie den Vorgang vom Typ **[!UICONTROL Import aus CRM]**.
1. Wählen Sie in der Dropdown-Liste des Felds **[!UICONTROL Remote-Objekt]** das vom Vorgang betroffene Objekt aus. Das Objekt entspricht einer der Tabellen, die bei der Connector-Konfiguration in Adobe Campaign erstellt wurden.
1. Geben Sie im Abschnitt **[!UICONTROL Remote-Felder]** die zu importierenden Felder an.

   Um ein Feld hinzuzufügen, klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]** in der Symbolleiste und anschließend auf **[!UICONTROL Ausdruck bearbeiten]**.

   ![](assets/crm_task_import_add_field.png)

   Falls nötig, kann das Datenformat über die Dropdown-Liste der Spalte **[!UICONTROL Konvertierung]** geändert werden. Mögliche Konvertierungen werden im Abschnitt [Datenformat](#data-format) beschrieben.

   >[!IMPORTANT]
   >
   >Um die Objekte aus dem CRM-System mit denen in der Adobe-Campaign-Anwendung zu verknüpfen, wird die Kennung des CRM-Datensatzes benötigt. Diese wird automatisch bei Bestätigung des Dialogfensters hinzugefügt.
   >
   >Außerdem ist das Datum der letzten CRM-seitigen Änderung erforderlich, um einen inkrementellen Datenimport zu ermöglichen.

1. Je nach Bedarf können die zu importierenden Daten gefiltert werden. Klicken Sie hierzu auf den Link **[!UICONTROL Filter bearbeiten...]**.

   Im folgenden Beispiel importiert Adobe Campaign nur Kontakte, die nach dem 1. November 2012 aktiv waren.

   ![](assets/crm_task_import_filter.png)

   >[!IMPORTANT]
   >
   >Einschränkungen in Bezug auf Datenfilter werden im Abschnitt [Datenfilter](#filtering-data) beschrieben.

1. Die Option **[!UICONTROL Automatischen Index verwenden...]** erlaubt die automatische Verwaltung der inkrementellen Synchronisation der Objekte zwischen dem CRM-System und Adobe Campaign in Abhängigkeit vom letzten Änderungsdatum.

   Weitere Informationen hierzu finden Sie im Abschnitt [Variablenverwaltung](#variable-management).

### Variablenverwaltung {#variable-management}

Durch Aktivierung der Option **[!UICONTROL Automatischer Index]** ist es möglich, nur die seit dem letzten Import geänderten Objekte abzurufen.

![](assets/crm_task_import_option.png)

Das Datum der letzten Synchronisation wird in einer im Konfigurationsfenster angezeigten Option gespeichert. Standardmäßig ist dies: **LASTIMPORT_&lt;%=instance.internalName%>_&lt;%=activityName%>**.

>[!NOTE]
>
>Dieser Hinweis gilt nur für die allgemeine **[!UICONTROL CRM-Connector]**-Aktivität. Für andere CRM-Aktivitäten läuft der Prozess automatisch ab.
>
>Diese Option muss unter **[!UICONTROL Administration]** > **[!UICONTROL Plattform]** > **[!UICONTROL Optionen]** manuell erstellt und spezifiziert werden. Dabei muss es sich um eine Textoption handeln, deren Wert das folgende Format aufweist: **jjjj/MM/tt hh:mm:ss**.
> 
>Diese Option muss bei jedem weiteren Import manuell aktualisiert werden.

Sie können jedoch auch ein anderes CRM-Remote-Feld angeben, um die letzten Änderungen zu identifizieren.

Unten stehende Felder kommen (in der angegebenen Reihenfolge) zur Anwendung:

* Bei Microsoft Dynamics: **modifiedon**,
* Bei Salesforce.com: **LastModifiedDate**, **SystemModstamp**.

Die Aktivierung der Option **[!UICONTROL Automatischer Index]** erzeugt drei Variablen, die im Synchronisations-Workflow über eine **[!UICONTROL JavaScript]**-Aktivität genutzt werden können. Diese Variablen sind:

* **vars.crmOptionName**: entspricht dem Datum des letzten Imports.
* **vars.crmStartImport**: entspricht dem Startdatum des letzten Datenabrufs (einschließlich).
* **vars.crmEndDate**: entspricht dem Enddatum des letzten Datenabrufs (ausschließlich).

   >[!NOTE]
   >
   >Die Daten werden im Format **yyyy/MM/dd hh:mm:ss** ausgedrückt.

### Datenfilter {#filtering-data}

Um eine effiziente Funktionsweise mit den diversen CRM-Systemen sicherzustellen, sind bei der Filtererstellung folgende Regeln zu beachten:

* Jedes Filterniveau darf nur einen Operatortyp verwenden.
* Der AND-NOT-Operator wird nicht unterstützt.
* Vergleiche dürfen sich nur auf Werte vom Typ &quot;ist leer&quot;/&quot;ist nicht leer&quot; oder auf Zahlen beziehen. Der Wert (rechte Spalte) wird ausgewertet und das Ergebnis muss eine Zahl sein. JOIN-Vergleiche werden nicht unterstützt.
* Der in der rechten Spalte angegebene Wert wird in JavaScript ausgewertet.
* Vergleiche vom Typ JOIN werden nicht unterstützt.
* Der Ausdruck (linke Spalte) muss zwingend ein Feld sein. Er darf weder eine Kombination aus mehreren Ausdrücken, noch eine Ziffer usw. sein.

So wären z. B. folgende Filterbedingungen im Rahmen eines CRM-Imports UNGÜLTIG, da der ODER-Operator auf demselben Niveau wie die UND-Operatoren verwendet wird:

* Der ODER-Operator befindet sich auf dem gleichen Niveau wie die UND-Operatoren.
* Die Vergleiche beziehen sich auf Zeichenketten.

![](assets/crm_import_wrong_filter.png)

### Sortierreihenfolge {#order-by}

In Microsoft Dynamics und Salesforce.com haben Sie die Möglichkeit, die zu importierenden Remote-Felder auf- oder absteigend zu sortieren.

Klicken Sie hierfür auf **[!UICONTROL Sortierreihenfolge]** und fügen Sie die Spalten zur Liste hinzu.

Die Spaltenreihenfolge der Liste zeigt die Sortierreihenfolge an:

![](assets/crm_import_order.png)

### Datensatz-Identifizierung {#record-identification}

Statt im CRM-System enthaltene (und u. U. gefilterte) Elemente direkt zu importieren, können Sie eine zuvor im Workflow berechnete Population verwenden.

Kreuzen Sie hierfür die Option **[!UICONTROL Die zuvor berechnete Population verwenden]** an und geben Sie das die Remote-Kennung enthaltende Feld an.

Wählen Sie anschließend die aus der Eingangspopulation zu importierenden Felder wie in unten stehendem Beispiel aus:

![](assets/crm_wf_import_calculated_population.png)

## Export in CRM {#exporting-to-the-crm}

Der Export von Daten aus Adobe Campaign ermöglicht die vollständige Kopie eines Inhalts in ein CRM-System.

Zum Export von Daten in ein CRM-System ist ein Workflow nach folgendem Muster zu erstellen:

![](assets/crm_export_diagram.png)

Gehen Sie bei der Konfiguration der **[!UICONTROL CRM-Connector]**-Aktivität wie folgt vor:

1. Wählen Sie den Vorgang vom Typ **[!UICONTROL Export in das CRM]**.
1. Wählen Sie in der Dropdown-Liste des Felds **[!UICONTROL Remote-Objekt]** das vom Vorgang betroffene Objekt aus. Das Objekt entspricht einer der Tabellen, die bei der Connector-Konfiguration in Adobe Campaign erstellt wurden.

   >[!IMPORTANT]
   >
   >Die Exportfunktion der Aktivität **[!UICONTROL CRM-Connector]** kann Felder auf der CRM-Seite einfügen oder aktualisieren. Um Feldaktualisierungen im CRM zu aktivieren, müssen Sie den Primärschlüssel der Remote-Tabelle angeben. Wenn der Schlüssel fehlt, werden Daten eingefügt (anstatt dass sie aktualisiert werden).

1. Geben Sie im Abschnitt **[!UICONTROL Mapping]** die zu exportierenden Adobe-Campaign-Felder und die entsprechenden CRM-Felder an.

   ![](assets/crm_export_config.png)

   Um ein Feld hinzuzufügen, klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]** in der Symbolleiste und anschließend auf **[!UICONTROL Ausdruck bearbeiten]**.

   >[!NOTE]
   >
   >Wenn für ein Feld keine CRM-seitige Entsprechung existiert, werden die enthaltenen Werte nicht aktualisiert, sondern direkt dem CRM-System hinzugefügt.

   Falls nötig, kann das Datenformat über die Dropdown-Liste der Spalte **[!UICONTROL Konvertierung]** geändert werden. Mögliche Konvertierungen werden im Abschnitt [Datenformat](#data-format) beschrieben.

   >[!NOTE]
   >
   >Die Liste der zu exportierenden Datensätze und das Exportergebnis werden in einer temporären Datei gespeichert, die zugänglich bleibt, solange der Workflow nicht abgeschlossen oder neu gestartet wurde. Dies gewährleistet, dass der Vorgang im Falle von Fehlern wieder aufgenommen werden kann, ohne Gefahr zu laufen, einen Datensatz mehrmals zu exportieren oder Daten zu verlieren.

## Ergänzende Konfigurationen {#additional-configurations}

### Datenformat {#data-format}

Es besteht die Möglichkeit, das Datenformat beim Import aus dem oder beim Export in das CRM-System direkt zu konvertieren.

Wählen Sie hierzu in der entsprechenden Spalte die anzuwendende Konvertierung aus.

![](assets/crm_task_import.png)

Im **[!UICONTROL Standard]**-Modus entspricht die Konvertierung zumeist einem einfachen Kopieren/Einfügen der Daten. Die verschiedenen Zeitzonen werden in jedem Fall berücksichtigt.

Darüber hinaus sind folgende Konvertierungen möglich:

* **[!UICONTROL Nur Datum]**: löscht die Uhrzeit aus Feldern vom Typ Datum+Uhrzeit.
* **[!UICONTROL Ohne Zeitverschiebung]**: gibt im Gegensatz zum Standardmodus die Uhrzeit ohne Berücksichtigung der Zeitzonen wieder.
* **[!UICONTROL Kopieren/Einfügen]**: verwendet die ursprünglichen Daten als Strings weiter (keine Konvertierung).

### Umgang mit Fehlern {#error-processing}

Im Rahmen eines Imports oder Exports ist es möglich, einen spezifischen Umgang mit Fehlern und Zurückweisungen zu definieren. Wählen Sie diesbezüglich im Tab **[!UICONTROL Verhalten]** die Optionen **[!UICONTROL Zurückweisungen in einer Datei speichern]** und **[!UICONTROL Fehler verarbeiten]** aus.

![](assets/crm_export_options.png)

Diese Optionen erzeugen die entsprechenden ausgehenden Transitionen.

![](assets/crm_export_transitions.png)

Nun können Sie nach Wunsch Aktivitäten im Zusammenhang mit den Vorgängen positionieren.

Im Bezug auf den Umgang mit Fehlern können Sie beispielsweise eine Warte-Aktivität anfügen und Wiederaufnahmen vorsehen.

Zurückweisungen werden mit dem Fehlercode und der entsprechenden Nachricht erfasst. Dies bietet die Möglichkeit, eine Zurückweisungsverfolgung zu etablieren, um Ihre Synchronisationsprozesse zu optimieren.

>[!NOTE]
>
>Auch wenn die Option **[!UICONTROL Zurückweisungen in einer Datei speichern]** nicht aktiviert wurde, werden für jede zurückgewiesene Spalte ein Fehlercode und die entsprechende Nachricht erzeugt.

Die ausgehende Transition **[!UICONTROL Zurückweisung]** verleiht Ihnen Zugang zum Ausgabeschema, welches die Spalten für Fehlermeldungen und -Codes und enthält. Bei Salesforce.com lautet die Spalte **errorSymbol** (Fehlersymbol, unterscheidet sich vom Fehler-Code), **errorMessage** (Beschreibung des Fehlerkontexts).

## Import der im CRM gelöschten Objekte {#importing-objects-deleted-in-the-crm}

Für eine umfassende Datensynchronisation besteht die Möglichkeit, CRM-seitig gelöschte Objekte in Adobe Campaign zu importieren.

Gehen Sie hierzu wie folgt vor:

1. Wählen Sie den Vorgang vom Typ **[!UICONTROL Import der im CRM gelöschten Objekte]** aus.
1. Wählen Sie in der Dropdown-Liste des Felds **[!UICONTROL Remote-Objekt]** das vom Vorgang betroffene Objekt aus. Das Objekt entspricht einer der Tabellen, die bei der Connector-Konfiguration in Adobe Campaign erstellt wurden.
1. Bestimmen Sie durch Eingabe von **[!UICONTROL Startdatum]** und **[!UICONTROL Enddatum]** den Zeitraum, für den gelöschte Objekte importiert werden sollen. Der Zeitraum versteht sich einschließlich Start- und Enddatum.

   ![](assets/crm_import_deleted_obj.png)

   >[!IMPORTANT]
   >
   >Der Löschzeitraum für die zu importierenden Objekte muss die Einschränkungen des jeweiligen CRM-Systems berücksichtigen. So ist es z. B. in Salesforce.com nicht möglich, Daten abzurufen, die vor mehr als 30 Tagen gelöscht wurden.

## Löschung von Objekten im CRM {#deleting-objects-in-the-crm}

Zur Löschung von Objekten im CRM ist die Angabe der Primärschlüssel der zu löschenden Remote-Elemente erforderlich.

![](assets/crm_delete_in_crm.png)

Im Tab **[!UICONTROL Verhalten]** kann die Zurückweisungsverarbeitung aktiviert werden. Dies erzeugt eine weitere ausgehende Transition aus der **[!UICONTROL CRM-Connector]**-Aktivität. Konsultieren Sie diesbezüglich die [Fehlerverarbeitung](#error-processing).

>[!NOTE]
>
>Auch wenn die Option **[!UICONTROL Zurückweisungen in einer Datei speichern]** nicht aktiviert wurde, wird für jede zurückgewiesene Spalte ein Warnhinweis erzeugt.


---
product: campaign
title: Best Practices beim Import und Export
description: Erfahren Sie mehr über Best Practices, die beim Importieren oder Exportieren von Daten befolgt werden sollten
feature: Data Management
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: automating
content-type: reference
topic-tags: workflow-general-operation
exl-id: 03d35202-d221-4136-aad4-00704aabb356
TQID: https://experienceleague.adobe.com/fHl4uUPkoQ48OuUI41YMFQK6J6X6YiIjERUeNKM0904
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
feature_v2: id: afa4204e-6d08-4e29-bc35-26aafb656d48
subfeature_v2: id: f529d0bd-1401-4c88-9833-43228cc1d40fid: d6330382-c886-4f7a-a4f7-74e3f36c0d9cid: f5293531-9312-4099-bfa3-9e67df6a8750id: efa38731-2723-4334-8d8b-a778af834835
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 555
ht-degree: 100%

---

# Best Practices beim Import und Export {#import-export-best-practices}



Eine sorgfältige Arbeitsweise und die Befolgung der unten stehenden einfachen Regeln helfen Ihnen, die Datenbank konsistent zu halten und gängige Fehler bei der Datenbankaktualisierung oder beim Datenexport zu vermeiden.

## Verwenden von Workflow-Vorlagen {#using-import-templates}

Die meisten Workflows für den Import von Daten sollten folgende Aktivitäten beinhalten: **[!UICONTROL Datei laden]**, **[!UICONTROL Abstimmung]**, **[!UICONTROL Segmentierung]**, **[!UICONTROL Deduplizierung]**, **[!UICONTROL Daten-Update]**.

Workflow-Vorlagen vereinfachen die Durchführung ähnlicher Importe und halten die Datenbank konsistent.

In vielen Projekten werden Importe ohne **[!UICONTROL Deduplizierung]** erstellt, da die im Projekt verwendeten Dateien ohnehin keine Duplikate aufweisen. Beim Import verschiedener Dateien können jedoch Duplikate entstehen. Dann ist eine Deduplizierung schwierig. Deshalb ist eine Deduplizierung eine gute Vorsichtsmaßnahme bei jedem Import-Workflow.

Verlassen Sie sich nicht darauf, dass die eingehenden Daten konsistent und korrekt sind oder dass sich die IT-Abteilung oder der Adobe Campaign-Verantwortliche darum kümmert. Führen Sie stattdessen während des Projekts die Datenbereinigung durch. Achten Sie beim Datenimport auf die Deduplizierung, die Abstimmung und die Gewährleistung der Konsistenz.

Ein Beispiel für eine allgemeine Workflow-Vorlage zum Datenimport finden Sie unter [Beispiel: Workflow-Vorlage zum Importieren von Daten](../../platform/using/creating-import-export-templates.md).

## Flache Dateiformate verwenden {#using-flat-file-formats}

Das effizienteste Format für Importe sind flache Dateien, die im Bulk-Modus auf Datenbankebene importiert werden können.

Beispiel:

* Trennzeichen: Tabulator oder Semikolon
* Erste Zeile mit Headern
* Keine Zeichenfolgen-Qualifizierer
* Datumsformat: `YYYY/MM/DD HH:mm:SS`

Beispiel einer zu importierenden Datei:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

## Komprimierung verwenden {#using-compression}

Verwenden Sie für Importe und Exporte möglichst ZIP-Dateien. GZIP wird standardmäßig unterstützt. Beim Import von Dateien können Sie über die Workflow-Aktivität **[!UICONTROL Datei laden]** eine Vorbearbeitung hinzufügen. Bei der Datenextraktion können Sie über die Workflow-Aktivität **[!UICONTROL Dateiextraktion]** eine Nachbearbeitung hinzufügen.

**Verwandte Themen:**

* [Aktivität „Laden (Datei)“](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/data-loading-file.html?lang=de){target="_blank"}
* [Aktivität „Extraktion (Datei)“](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/extraction-file.html?lang=de){target="_blank"}.

## Im Deltamodus importieren {#importing-in-delta-mode}

Regelmäßige Importe müssen im Deltamodus durchgeführt werden. Damit wird gewährleistet, dass nicht jedes Mal die gesamte Tabelle, sondern nur geänderte oder neue Daten an Adobe Campaign gesendet werden.

Vollständige Importe sollten nur für das erstmalige Laden verwendet werden.

## Konsistenz gewährleisten {#maintaining-consistency}

Um die Konsistenz der Adobe Campaign-Datenbank zu gewährleisten, befolgen Sie die unten stehenden Grundsätze:

* Wenn die importierten Daten einer Referenztabelle in Adobe Campaign entsprechen, sollten sie im Workflow mit dieser Tabelle abgestimmt werden. Nicht übereinstimmende Datensätze sollten abgelehnt werden.
* Achten Sie darauf, dass die importierten Daten (E-Mail, Telefonnummer, Briefpostanschrift) stets **&quot;bereinigt&quot;** werden und dass diese Bereinigung zuverlässig ist und sich im Laufe der Jahre nicht verändert. Andernfalls könnten in der Datenbank Duplikate entstehen. Da Adobe Campaign keine Tools zum &quot;unscharfen&quot; Abgleich besitzt, ist es dann sehr schwierig, diese Duplikate zu verwalten und zu entfernen.
* Transaktionsdaten sollten einen Abstimmschlüssel aufweisen und mit den bestehenden Daten abgestimmt werden, damit keine Duplikate entstehen.
* **Importieren Sie verknüpfte Dateien in der richtigen Reihenfolge**. Wenn der Import aus mehreren miteinander verbundenen Dateien besteht, sollte im Workflow darauf geachtet werden, dass die Dateien in der richtigen Reihenfolge importiert werden. Wenn der Import einer Datei fehlschlägt, werden auch die anderen nicht importiert.
* Achten Sie beim Datenimport auf die **Deduplizierung**, die Abstimmung und die Gewährleistung der Konsistenz.

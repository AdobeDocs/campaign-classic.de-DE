---
product: campaign
title: Überwachen der Ausführung von Vorgängen
description: Erfahren Sie, wie Sie die Ausführung von Import- und Exportvorgängen überwachen
feature: Monitoring
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 415c5137-2eb0-4581-a46e-26e8e3d264fa
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 91%

---

# Überwachen der Ausführung von Vorgängen {#monitoring-job-execution}



Sie können die Ausführung von Import- und Exportvorgängen direkt über die Liste der Import-/Exportvorgänge verfolgen.

![](assets/s_ncs_user_export_list_and_details.png)

* Im Tab **[!UICONTROL Journal]** können Sie die zur Exportdurchführung gehörigen Protokollnachrichten einsehen.
* Der Tab **[!UICONTROL Zurückweisungen]** listet die Datensätze auf, die nicht verarbeitet werden konnten. Weitere Informationen finden Sie in [diesem Abschnitt](../../platform/using/executing-import-jobs.md#behavior-in-the-event-of-an-error).

Im Tab **[!UICONTROL Allgemein]** gibt das Feld **[!UICONTROL Status]** den aktuellen Status eines Vorgangs an.

Jeder Status wird durch ein spezielles Symbol und eine spezielle Bezeichnung repräsentiert. Die Statusangaben und zugehörigen Symbole sind im Folgenden aufgeführt:

![](assets/s_ncs_user_export_status.png)

* **In Bearbeitung**

  Vorgang wird durch einen Benutzer bearbeitet.

* **Ausführung in Gang**

  Vorgang wird ausgeführt.

* **Rückgängig**

  Der laufende Vorgang wurde durch Klick auf die Schaltfläche **[!UICONTROL Abbrechen]** abgebrochen.

* **Wird abgebrochen**

  Der Abbruch wurde berücksichtigt und der Vorgang ist im Abbruch begriffen.

* **Wird ausgesetzt**

  Klick auf die Schaltfläche **[!UICONTROL Pause]**: Die Aussetzung des Vorgangs ist in Gang.

* **Ausgesetzt**

  Klicks **[!UICONTROL Anhalten]**: Der Auftrag wird ausgesetzt. Er kann durch Klicken auf **[!UICONTROL Starten]**.

* **Abgeschlossen**

  Die Ausführung des Vorgangs ist abgeschlossen.

* **Abgeschlossen mit Fehlern**

  Der Vorgang konnte aufgrund eines technischen Fehlers nicht ausgeführt werden.

* **Server wird heruntergefahren**

  Der laufende Vorgang wurde aufgrund eines Stopps des Adobe-Campaign-Servers unterbrochen.

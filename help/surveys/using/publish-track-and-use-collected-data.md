---
product: campaign
title: Erfasste Daten veröffentlichen, tracken und verwenden
description: Erfahren Sie, wie Sie in einer Umfrage erfasste Daten veröffentlichen, tracken und verwenden.
badge-v7: label="v7" type="Informative" tooltip="Gilt für Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Surveys
exl-id: 3cf3c486-6640-4d67-95cf-50d5767deb60
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '892'
ht-degree: 78%

---

# Erfasste Daten veröffentlichen, tracken und verwenden{#publish-track-and-use-collected-data}



Nachdem das Formular erstellt, konfiguriert und veröffentlicht wurde, können Sie den Link mit Ihrer Zielgruppe teilen und die Antworten tracken.

>[!NOTE]
>
>Der Lebenszyklus einer Umfrage in Adobe Campaign sowie ihre Veröffentlichungs- und Versandmodi sind ähnlich jenen von Webformularen: Diese werden in [diesem Abschnitt](../../web/using/about-web-forms.md) beschrieben.

## Umfrage-Dashboard {#survey-dashboard}

Jede Umfrage besitzt ihr eigenes Dashboard, über das Sie den Status, die Beschreibung, die öffentliche URL und die zeitliche Verfügbarkeit aufrufen können. Zusätzlich können Sie die verfügbaren Berichte einsehen. [Weitere Informationen](#reports-on-surveys).

Die öffentliche URL der Umfrage wird im Dashboard angezeigt:

![](assets/survey_public_url.png)

## Antworten tracken {#response-tracking}

Sie können die Antworten auf die Umfrage in Logs und Berichten verfolgen.

### Umfrage-Logs {#survey-logs}

Sie können die Antworten aller bereitgestellten Umfragen im Tab **[!UICONTROL Logs]** verfolgen. In diesem Tab wird die Liste der Teilnehmer an der Umfrage sowie ihre Herkunft angezeigt:

![](assets/s_ncs_admin_survey_logs.png)

Durch Doppelklick auf eine Zeile öffnet sich das vom reagierenden Kontakt ausgefüllte Umfrageformular. Sie können die gesamte Umfrage durchsuchen, auf die vollständigen Antworten zugreifen und diese in eine externe Datei exportieren. Weitere Informationen finden Sie unter [Antworten exportieren](#exporting-answers).

Die Herkunft wird in der Umfrage-URL durch Hinzufügen folgender Buchstaben gekennzeichnet:

```
?origin=xxx
```

während die Umfrage bearbeitet wird, enthält ihre URL den Parameter **[!UICONTROL __uuid]**, was anzeigt, dass es sich in einer Testphase befindet und noch nicht online ist. Wenn Sie über diese URL auf die Umfrage zugreifen, werden die erstellten Datensätze beim Tracking (in Berichten) nicht berücksichtigt. Der Ursprung wird auf den Wert **[!UICONTROL Adobe Campaign]**.

Weiterführende Informationen zu URL-Parametern finden Sie auf [dieser Seite](../../web/using/defining-web-forms-properties.md#form-url-parameters).

### Berichte zu Umfragen {#reports-on-surveys}

Der Zugriff auf Umfrageberichte erfolgt über das Dashboard-Tab. Klicken Sie einfach auf einen Namen, um den entsprechenden Bericht anzuzeigen.

![](assets/s_ncs_admin_survey_report_doc.png)

Im Bericht **[!UICONTROL Dokumentation]** wird die Struktur der Umfrage dargestellt.

Im Tab **[!UICONTROL Berichte]** sind zwei weitere Berichte zu Webumfragen verfügbar: **[!UICONTROL Allgemein]** und **[!UICONTROL Antwortenverteilung]**.

* Allgemein

  Dieser Bericht enthält allgemeine Informationen zur Umfrage: die Veränderung der Anzahl der Antworten im Zeitverlauf und die Verteilung nach Herkunft und Sprache.

  Beispiel für einen allgemeinen Bericht:

  ![](assets/s_ncs_admin_survey_report_0.png)

* Antwortenverteilung

  Dieser Bericht zeigt die Antwortenverteilung für jede Frage. Diese Aufschlüsselung ist nur für Antworten auf Felder verfügbar, die in gespeichert sind. **[!UICONTROL Frage]** Typbehälter. Sie gilt nur für Auswahldialoge (beispielsweise keine Aufschlüsselung für Textfelder).

  ![](assets/s_ncs_admin_survey_report_2.png)

## Antworten exportieren {#exporting-answers}

Antworten auf Umfragen können zur späteren Verarbeitung in eine externe Datei exportiert werden. Dazu gibt es zwei Möglichkeiten:

1. Berichtsdaten exportieren

   Um Berichtsdaten zu exportieren, wählen Sie die Schaltfläche **[!UICONTROL Exportieren]** und danach das Exportformat aus.

   Weiterführende Informationen zum Exportieren von Berichtdaten finden Sie in [diesem Abschnitt](../../reporting/using/about-reports-creation-in-campaign.md).

1. Antworten exportieren

   Um Antworten zu exportieren, klicken Sie auf die Schaltfläche **[!UICONTROL Antworten]** und klicken Sie mit der rechten Maustaste auf die Umfrage. Auswählen **[!UICONTROL Export...]**.

   ![](assets/s_ncs_admin_survey_logs_export_menu.png)

   Geben Sie anschließend die Informationen ein, die Sie exportieren möchten, sowie die Speicherdatei.

   Sie können den Inhalt und das Format der Ausgabedatei im Export-Assistenten konfigurieren.

   Sie können beispielsweise:

   * Spalten zur Ausgabedatei hinzufügen und Informationen über den Empfänger abrufen (die in der Datenbank gespeichert sind);
   * die exportierte Datei formatieren;
   * das Codierungsformat für die Daten in der Datei auswählen.

   Wenn die zu exportierende Umfrage mehrere **[!UICONTROL Mehrzeiliger Text]** oder **[!UICONTROL HTML-Text]** -Felder, muss er exportiert werden in **[!UICONTROL XML]** Format. Wählen Sie dazu dieses Format in der Dropdown-Liste der **[!UICONTROL Ausgabeformat]** wie unten gezeigt:

   ![](assets/s_ncs_admin_survey_logs_export_xml.png)

   Klicken Sie auf **[!UICONTROL Starten]**, um mit dem Export zu beginnen.

   >[!NOTE]
   >
   >Der Datenexport und die Konfigurationsschritte werden in [diesem Abschnitt](../../platform/using/about-generic-imports-exports.md) beschrieben.

## Die erfassten Daten nutzen {#using-the-collected-data}

Die mithilfe von Online-Umfragen gesammelten Informationen können im Rahmen eines Zielgruppen-Workflows abgerufen werden. Verwenden Sie dazu die **[!UICONTROL Umfrageantworten]** ankreuzen.

Im folgenden Beispiel soll den fünf Empfängern, die bei einer Online-Umfrage die höchste Punktzahl hatten und mindestens zwei Kinder haben, ein Webangebot gemacht werden. Die Antworten auf die Umfrage lauteten:

![](assets/s_ncs_admin_survey_responses_wf_box_4.png)

Im Zielgruppen-Workflow werden die **[!UICONTROL Umfrageantworten]** folgendermaßen konfiguriert:

![](assets/s_ncs_admin_survey_responses_wf_box_1.png)

Wählen Sie zuerst die entsprechende Umfrage und dann in der Mitte des Fensters die zu extrahierenden Daten aus. In diesem Fall muss zumindest die Punktzahl-Spalte extrahiert werden, da sie in der Aufspaltungsbox zum Abrufen der fünf höchsten Punkte verwendet wird.

Geben Sie die Filterbedingungen für Antworten ein, indem Sie den Link **[!UICONTROL Abfrage bearbeiten...]** auswählen.

![](assets/s_ncs_admin_survey_responses_wf_box_2.png)

Starten Sie den Zielgruppen-Workflow. Bei der Abfrage werden acht Empfänger abgerufen.

![](assets/s_ncs_admin_survey_responses_wf_box_5.png)

Um sie anzuzeigen, rechtsklicken Sie auf die ausgehende Transition der Sammlungsbox.

![](assets/s_ncs_admin_survey_responses_wf_box_6.png)

Platzieren Sie dann eine Aufspaltungsbox in den Workflow, um die fünf Empfänger mit den meisten Punkten abzurufen.

Bearbeiten Sie die Aufspaltungsbox, um sie zu konfigurieren:

* Wählen Sie zunächst im Tab **[!UICONTROL Allgemein]** das entsprechende Schema aus und konfigurieren Sie dann die Untereinheit:

  ![](assets/s_ncs_admin_survey_responses_wf_box_6b.png)

* Gehen Sie zum Tab **[!UICONTROL Teilmengen]** und wählen Sie die Option **[!UICONTROL Anzahl von Datensätzen begrenzen]** und danach den Link **[!UICONTROL Bearbeiten...]** aus.

  ![](assets/s_ncs_admin_survey_responses_wf_box_7.png)

* Wählen Sie die **[!UICONTROL Nur die ersten Datensätze nach der Sortierung beibehalten]** und wählen Sie die Sortierungsspalte aus. Überprüfen Sie die **[!UICONTROL Absteigende Sortierung]** -Option.

  ![](assets/s_ncs_admin_survey_responses_wf_box_8.png)

* Wählen Sie die Schaltfläche **[!UICONTROL Weiter]** aus und beschränken Sie die Anzahl der Datensätze auf fünf.

  ![](assets/s_ncs_admin_survey_responses_wf_box_9.png)

* Wählen Sie **[!UICONTROL Beenden]** aus und starten Sie dann den Workflow neu, um die Zielgruppe zu validieren.

## Daten vereinheitlichen {#standardizing-data}

Sie können in Adobe Campaign für gesammelte Daten Vereinheitlichungsprozesse mithilfe von Alias einrichten. Damit können Sie die in der Datenbank gespeicherten Daten vereinheitlichen. Definieren Sie dazu Alias in den Auflistungen, die die entsprechenden Informationen enthalten. [Weitere Informationen](../../platform/using/managing-enumerations.md#about-enumerations)

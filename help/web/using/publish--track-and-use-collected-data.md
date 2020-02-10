---
title: Erfasste Daten publizieren, tracken und verwenden
seo-title: Erfasste Daten publizieren, tracken und verwenden
description: Erfasste Daten publizieren, tracken und verwenden
seo-description: null
page-status-flag: never-activated
uuid: eac16f2c-0423-4727-a2da-3af1d6c616ec
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: 434a4bda-0907-42a7-8a75-2db658bba046
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Erfasste Daten publizieren, tracken und verwenden{#publish-track-and-use-collected-data}

Nachdem das Formular erstellt, konfiguriert und veröffentlicht wurde, können Sie den Link für Ihre Zielgruppe freigeben und die Antworten verfolgen.

>[!NOTE]
>
>Der Lebenszyklus einer Umfrage in Adobe Campaign sowie ihre Publikations- und Versandmodi sind ähnlich jenen von Webformularen: Diese werden in [diesem Abschnitt](../../web/using/about-web-forms.md) beschrieben.

## Umfrage-Dashboard {#survey-dashboard}

Jede Umfrage verfügt über ein eigenes Dashboard, über das Sie ihren Status, ihre Beschreibung, ihre öffentliche URL und ihren Verfügbarkeitsplan anzeigen können. Sie können auch die verfügbaren Berichte anzeigen. Weitere Informationen finden Sie unter [Berichte zu Umfragen](#reports-on-surveys).

Die öffentliche URL der Umfrage wird im Dashboard angezeigt:

![](assets/survey_public_url.png)

## Antworten tracken {#response-tracking}

Sie können die Antworten auf die Umfrage in Logs und Berichten verfolgen.

### Umfrage-Logs {#survey-logs}

Für jede bereitgestellte Umfrage können Sie die Antworten auf der **[!UICONTROL Logs]** Registerkarte verfolgen. Auf dieser Registerkarte werden die Liste der Benutzer angezeigt, die die Umfrage abgeschlossen haben, und ihr Ursprung:

![](assets/s_ncs_admin_survey_logs.png)

Doppelklicken Sie auf eine Zeile, um das Umfrageformular so anzuzeigen, wie es vom Befragten ausgefüllt wurde. Sie können die Umfrage vollständig durchsuchen und die Antworten vollständig aufrufen. Diese können in eine externe Datei exportiert werden. For more on this, refer to [Exporting answers](#exporting-answers).

Die Herkunft wird in der Umfrage-URL durch Hinzufügen folgender Buchstaben gekennzeichnet:

```
?origin=xxx
```

während die Umfrage bearbeitet wird, enthält die URL den Parameter **[!UICONTROL __uuid]**, der angibt, dass sie sich in einer Testphase befindet und noch nicht online ist. Wenn Sie über diese URL auf die Umfrage zugreifen, werden die erstellten Datensätze bei der Verfolgung (den Berichten) nicht berücksichtigt. Der Ursprung wird zum Wert gezwungen **[!UICONTROL Adobe Campaign]**.

Weiterführende Informationen zu URL-Parametern finden Sie auf [dieser Seite](../../web/using/defining-web-forms-properties.md#form-url-parameters).

### Berichte zu Umfragen {#reports-on-surveys}

Der Zugriff auf Umfrageberichte erfolgt über das Dashboard-Tab. Klicken Sie einfach auf einen Namen, um den entsprechenden Bericht anzuzeigen.

![](assets/s_ncs_admin_survey_report_doc.png)

The structure of the survey is visible in the **[!UICONTROL Documentation]** report.

Zwei weitere Berichte zu Web-Umfragen sind auf der **[!UICONTROL Reports]** Registerkarte der Umfragen verfügbar: **[!UICONTROL General]** und **[!UICONTROL Breakdown of responses]**.

* Allgemein

   Dieser Bericht enthält allgemeine Informationen zur Umfrage: die Veränderung der Anzahl der Antworten im Zeitverlauf und die Verteilung nach Herkunft und Sprache.

   Beispiel für einen allgemeinen Bericht:

   ![](assets/s_ncs_admin_survey_report_0.png)

* Antwortenverteilung

   Dieser Bericht zeigt die Aufschlüsselung der Antworten für jede Frage. Diese Aufschlüsselung ist nur für Antworten auf Felder verfügbar, die in **[!UICONTROL Question]** Typbehältern gespeichert werden. Sie ist nur für Auswahlsteuerelemente gültig (z. B. keine Aufschlüsselung nach Textfeldern).

   ![](assets/s_ncs_admin_survey_report_2.png)

## Antworten exportieren {#exporting-answers}

Antworten auf Umfragen können zur späteren Verarbeitung in eine externe Datei exportiert werden. Dazu gibt es zwei Möglichkeiten:

1. Berichtsdaten exportieren

   To export report data, click the **[!UICONTROL Export]** button and choose the export format.

   Weiterführende Informationen zum Exportieren von Berichtdaten finden Sie in [diesem Abschnitt](../../reporting/using/about-reports-creation-in-campaign.md).

1. Antworten exportieren

   To export answers, click the **[!UICONTROL Responses]** tab of the survey and right-click. Auswählen **[!UICONTROL Export...]**.

   ![](assets/s_ncs_admin_survey_logs_export_menu.png)

   Geben Sie anschließend die Informationen ein, die Sie exportieren möchten, sowie die Speicherdatei.

   Sie können den Inhalt und das Format der Ausgabedatei im Export-Assistenten konfigurieren.

   Sie können beispielsweise:

   * Spalten zur Ausgabedatei hinzufügen und Informationen über den Empfänger abrufen (die in der Datenbank gespeichert sind);
   * die exportierte Datei formatieren;
   * das Codierungsformat für die Daten in der Datei auswählen.
   Wenn die Umfrage, die Sie exportieren möchten, mehrere **[!UICONTROL Multi-line text]** oder **[!UICONTROL HTML text]** Felder enthält, muss sie im **[!UICONTROL XML]** Format exportiert werden. Wählen Sie dazu dieses Format in der Dropdown-Liste des **[!UICONTROL Output format]** Felds aus, wie nachfolgend gezeigt:

   ![](assets/s_ncs_admin_survey_logs_export_xml.png)

   Click **[!UICONTROL Start]** to run the export.

   >[!NOTE]
   >
   >Der Datenexport und die Konfigurationsschritte werden in [diesem Abschnitt](../../platform/using/generic-imports-and-exports.md) beschrieben.

## Die erfassten Daten nutzen {#using-the-collected-data}

Die über Online-Umfragen erfassten Informationen können im Rahmen eines Targeting-Workflows wiederhergestellt werden. Verwenden Sie dazu das **[!UICONTROL Survey responses]** Kontrollkästchen.

Im folgenden Beispiel soll den fünf Empfängern, die bei einer Online-Umfrage die höchste Punktzahl hatten und mindestens zwei Kinder haben, ein Webangebot gemacht werden. Die Antworten auf die Umfrage lauteten:

![](assets/s_ncs_admin_survey_responses_wf_box_4.png)

In the targeting workflow, the **[!UICONTROL Survey responses]** will be configured as follows:

![](assets/s_ncs_admin_survey_responses_wf_box_1.png)

Wählen Sie zuerst die entsprechende Umfrage und dann in der Mitte des Fensters die zu extrahierenden Daten aus. In diesem Fall muss zumindest die Punktzahl-Spalte extrahiert werden, da sie in der Aufspaltungsbox zum Abrufen der fünf höchsten Punkte verwendet wird.

Indicate the filtering conditions for answers by clicking the **[!UICONTROL Edit query...]** link.

![](assets/s_ncs_admin_survey_responses_wf_box_2.png)

Starten Sie den Zielgruppen-Workflow. Bei der Abfrage werden acht Empfänger abgerufen.

![](assets/s_ncs_admin_survey_responses_wf_box_5.png)

Um sie anzuzeigen, rechtsklicken Sie auf die ausgehende Transition der Kollektionsbox.

![](assets/s_ncs_admin_survey_responses_wf_box_6.png)

Platzieren Sie dann eine Aufspaltungsbox in den Workflow, um die fünf Empfänger mit den meisten Punkten abzurufen.

Bearbeiten Sie die Aufspaltungsbox, um sie zu konfigurieren:

* Start by selecting the adequate schema in the **[!UICONTROL General]** tab, then configure the sub-set:

   ![](assets/s_ncs_admin_survey_responses_wf_box_6b.png)

* Gehen Sie zur **[!UICONTROL Sub-sets]** Registerkarte und wählen Sie die **[!UICONTROL Limit the selected records]** Option. Klicken Sie dann auf den **[!UICONTROL Edit...]** Link.

   ![](assets/s_ncs_admin_survey_responses_wf_box_7.png)

* Wählen Sie die **[!UICONTROL Keep only the first records after sorting]** Option und dann die Sortierspalte aus. Aktivieren Sie die **[!UICONTROL Descending sort]** Option.

   ![](assets/s_ncs_admin_survey_responses_wf_box_8.png)

* Click the **[!UICONTROL Next]** button and limit the number of records to 5.

   ![](assets/s_ncs_admin_survey_responses_wf_box_9.png)

* Click **[!UICONTROL Finish]** then restart the workflow to approve targeting.

## Daten vereinheitlichen {#standardizing-data}

Sie können in Adobe Campaign für gesammelte Daten Vereinheitlichungsprozesse mithilfe von Alias einrichten. Damit können Sie die in der Datenbank gespeicherten Daten vereinheitlichen. Definieren Sie dazu Alias in den Auflistungen, die die entsprechenden Informationen enthalten.

Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../platform/using/managing-enumerations.md#about-enumerations).

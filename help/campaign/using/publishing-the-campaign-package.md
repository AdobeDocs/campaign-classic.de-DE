---
title: Kampagnenkits publizieren
seo-title: Kampagnenkits publizieren
description: Kampagnenkits publizieren
seo-description: null
page-status-flag: never-activated
uuid: f2d35a8d-191f-4c53-8682-7ccce2a94257
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 8653d4fc-e47f-451a-95f2-c9209a252664
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '483'
ht-degree: 100%

---


# Kampagnenkits publizieren{#publishing-the-campaign-package}

Die Benutzer der Zentralstelle veröffentlichen in der **[!UICONTROL Kampagnenkit-Liste]** die Kits, die den Lokalstellen zur Verfügung gestellt werden sollen.

Vor der Veröffentlichung in der Liste der Kampagnenkits müssen diese von der Zentralstelle validiert werden. Sie haben die Möglichkeit, hierzu einen einzelnen oder eine Gruppe von Validierern über den Link **[!UICONTROL Validierungsparameter...]** des Kampagnenkits festzulegen.

## Validierenden Benutzer bestimmen {#assigning-a-reviewer}

Um den Validierer anzugeben, klicken Sie auf den Link **[!UICONTROL Validierungsparameter...]** des Kampagnenkits und wählen Sie den jeweiligen Benutzer in der Dropdown-Liste aus.

![](assets/s_advuser_mkg_dist_define_valid.png)

Um den Validierungsprozess zu starten, klicken Sie auf die Schaltfläche **[!UICONTROL Zur Validierung unterbreiten]**.

![](assets/s_advuser_mkg_dist_valid_process.png)

Der validierungsverantwortliche Benutzer erhält daraufhin eine Benachrichtigung, um die Verfügbarkeit des Kampagnenkits zu bestätigen. Über einen in der Nachricht enthaltenen Link kann er per Webzugriff die Validierung akzeptieren oder ablehnen.

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>Auf Organisationseinheitsebene können Sie auch validierende Benutzer angeben, um Bestellungen zu validieren. Weitere Informationen hierzu finden Sie unter [Organisationseinheiten](../../campaign/using/about-distributed-marketing.md#organizational-entities).

## Weitere validierende Benutzer hinzufügen {#adding-other-reviewers}

Über den Link **[!UICONTROL Bearbeiten...]** im Fenster der **[!UICONTROL Validierungsparameter]** des Kampagnenkits können weitere validierungsverantwortliche Benutzer hinzugefügt werden.

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## Validierungs-Deadlines {#approval-periods}

Wenn nicht anders angegeben, muss die Validierung innerhalb von drei Tagen ab dem Unterbreitungsdatum erfolgen.

Im unteren Abschnitt des Bearbeitungsfensters der Validierer können Sie Erinnerungen konfigurieren, die bei einer ausstehenden Validierung eines Kits an die Validierungsverantwortlichen geschickt werden. Klicken Sie hierzu auf den Link **[!UICONTROL Erinnerung hinzufügen]** und anschließend auf die Schaltfläche **[!UICONTROL Hinzufügen]**.

Die Erinnerung kann zu einem gegebenen Datum und/oder **x** Tage vor der Validierungs-Deadline verschickt werden. Der Erinnerungstyp wird in der ersten Spalte der Tabelle ausgewählt. Im unten stehenden Beispiel erhalten die Validierungsverantwortlichen eine Erinnerungsnachricht einen Tag vor Ablauf der Validierungsfrist, also zwei Tage nach dem Unterbreitungsdatum, und eine zweite Erinnerung am 29.1.2014, also zwei Tage vor dem in der Spalte **[!UICONTROL Datum]** ausgewählten Datum.

![](assets/s_advuser_mkg_dist_reminder_planning.png)

Wenn die Planung festgelegt und das Kit zur Validierung unterbreitet wurde, wird die Vorgangsplanung im Tab **[!UICONTROL Verfolgung]** angezeigt. Er gibt die auf der vorangehenden Konfiguration basierend berechnete Bearbeitungs-Deadline sowie die Daten der konfigurierten Erinnerungen an.

## Validierung über die Adobe-Campaign-Konsole {#approving-via-the-adobe-campaign-console}

Wenn kein Validierungsverantwortlicher bestimmt wurde oder keiner der benachrichtigten Benutzer das Kit validiert hat, kann die Validierung direkt über die Schaltfläche **[!UICONTROL Kampagnenkit validieren]** des **[!UICONTROL Dashboards]** des Kampagnenkits oder über die Übersicht der Kits erfolgen.

![](assets/s_advuser_mkg_dist_valid_button.png)

Sobald die Kampagne validiert ist wird sie automatisch publiziert, d. h. sie wird der Liste der Kampagnenkits hinzugefügt. Ab ihrem Verfügbarkeitsdatum kann sie von den Lokalstellen genutzt werden. Sofern bei der Kampagnenerstellung teilnehmende Lokalstellen bestimmt wurden, werden die Benutzer der Gruppe „Benachrichtigung bezüglich Kampagnenkits“ über die Verfügbarkeit der Kampagne benachrichtigt. Ist dies nicht der Fall, ist die Kampagne standardmäßig für alle Lokalstellen zugänglich. Weitere Informationen hierzu finden Sie unter [Organisationseinheiten](../../campaign/using/about-distributed-marketing.md#organizational-entities).

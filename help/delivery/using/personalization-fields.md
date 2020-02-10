---
title: Personalisierungsfelder
seo-title: Personalisierungsfelder
description: Personalisierungsfelder
seo-description: null
page-status-flag: never-activated
uuid: 3a94a50e-259e-40c3-ae67-8a2c42e9fad7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: 27c8e443-ee6b-4d58-bc2d-81cf8391c5de
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f5062117b5cefbdd2570018f6803f114c14a3fae

---


# Personalisierungsfelder{#personalization-fields}

Personalisierungsfelder bilden die erste Stufe einer Anpassung des Nachrichteninhalts. Durch Einfügen der Felder wird angegeben, an welcher Stelle die aus der gewählten Datenquelle stammenden Informationen angezeigt werden sollen.

So ersetzt Adobe Campaign das Personalisierungsfeld **&lt;%= recipient.lastName %>** durch den in der Empfängertabelle der Datenbank enthaltenen Nachnamen des Empfängers.

>[!NOTE]
>
>Inhalt von Personalisierungsfeldern darf 1024 Zeichen nicht überschreiten.

## Datenquellen {#data-sources}

Je nach ausgewähltem Versandmodus können die Personalisierungsfelder auf zwei verschiedene Datenquellen zurückgreifen:

* Die Adobe-Campaign-Datenbank. Dies ist der gängigste Fall. Man spricht von Personalisierungsfeldern des Empfängers. Hierbei kommen sämtliche in der Empfängertabelle enthaltene Felder infrage, gleich ob es sich um Standardfelder (Nachname, Vorname, Anschrift, Geburtsdatum usw.) oder benutzerdefinierte Felder handelt.
* Eine externe Datei. Hierbei kommen sämtliche in der externen Datei enthaltene Felder infrage.

>[!NOTE]
>
>Ein Adobe Campaign Personalisierungs-Tag präsentiert sich stets in folgender Form: **&lt;%=Tabelle.Feld%>**.

## Personalisierungsfeld einfügen {#inserting-a-personalization-field}

Klicken Sie zum Einfügen von Personalisierungsfeldern auf das Symbol der Dropdown-Liste, das bei der Bearbeitung des Betreffs, des Nachrichten-Headers und des Nachrichten-Textkörpers zur Verfügung steht.

![](assets/s_ncs_user_add_custom_field.png)

Nach Auswahl einer Datenquelle (Empfängerfelder oder Dateifelder) erfolgt diese Einfügung in Form eines Befehls, der von Adobe Campaign interpretiert und durch den Wert des Felds für einen bestimmten Empfänger ersetzt wird. Der physische Austausch kann dann auf der **[!UICONTROL Preview]** Registerkarte angezeigt werden.

## Beispiel für Personalisierungsfelder {#personalization-fields-example}

In unserem Beispiel wird eine E-Mail erstellt, in der der Empfängername im Betreff und das Datum der Profilerstellung im Nachrichten-Textkörper eingefügt werden soll. Gehen Sie wie folgt vor:

1. Erstellen Sie einen neuen Versand oder öffnen Sie einen existierenden E-Mail-Versand.
1. In the delivery wizard, click **[!UICONTROL Subject]** to edit the subject of the message and enter a subject.
1. Geben Sie &quot; **[!UICONTROL Special offer for]** &quot;ein und verwenden Sie die Schaltfläche in der Symbolleiste, um ein Personalisierungsfeld einzufügen. Auswählen **[!UICONTROL Recipients>Title]**.

   ![](assets/s_ncs_user_insert_custom_field.png)

1. Wiederholen Sie den Vorgang, um den Nachnamen der Empfänger einzufügen. Vergessen Sie die Leerzeichen zwischen den Personalisierungsfeldern nicht.
1. Click **[!UICONTROL OK]** to validate.
1. Im nächsten Schritt wird der Nachrichten-Textkörper angepasst. Klicken Sie dazu in das Inhaltsfeld der Nachricht und danach auf die Schaltfläche zum Einfügen von Personalisierungsfeldern.
1. Auswählen **[!UICONTROL Recipient>Other...]**.

   ![](assets/s_ncs_user_insert_custom_field_b.png)

1. Markieren Sie das Feld, das die gewünschte Information enthält, und klicken Sie auf **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_insert_custom_field_c.png)

1. Klicken Sie auf die **[!UICONTROL Preview]** Registerkarte, um das Personalisierungsergebnis anzuzeigen. Sie müssen einen Empfänger auswählen, um die Nachricht des Empfängers anzuzeigen.

   ![](assets/s_ncs_user_insert_custom_field_d.png)

   >[!NOTE]
   >
   >Wenn eine Bereitstellung Teil eines Workflows ist, können Sie die Daten aus der Tabelle für den temporären Workflow verwenden. Diese Daten werden im **[!UICONTROL Target extension]** Menü gruppiert. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../workflow/using/executing-a-workflow.md#target-data).

## Personalisierung optimieren {#optimizing-personalization}

Sie können die Personalisierung mithilfe einer dedizierten Option optimieren: **[!UICONTROL Prepare the personalization data with a workflow]**, verfügbar auf der **[!UICONTROL Analysis]** Registerkarte der Bereitstellungseigenschaften.

Diese Option ermöglicht es, im Zuge der Versandanalyse automatisch einen Workflow zu erstellen und auszuführen, welcher alle auf eine Zielgruppe bezogenen Daten in einer temporären Tabelle speichert (insbesondere Daten aus über FDA verknüpften Tabellen).

Durch Aktivierung dieser Option werden erhebliche Leistungsverbesserungen bei der Versandpersonalisierung erzielt.

Sollten Sie beispielsweise beim Versand an zahlreiche Empfänger Leistungsprobleme feststellen, wenn Sie viele Personalisierungsfelder und/oder Gestaltungsbausteine im Nachrichteninhalt verwenden, können Sie mit dieser Option die Personalisierung und somit den Nachrichtenversand beschleunigen.

Um diese Option zu verwenden, gehen Sie wie folgt vor:

1. Kampagne erstellen. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign).
1. In the **[!UICONTROL Targeting and workflows]** tab of your campaign, add a **Query** activity to your workflow. For more on using this activity, refer to [this section](../../workflow/using/query.md).
1. Fügen Sie dem Workflow eine **[!UICONTROL Email delivery]** Aktivität hinzu und öffnen Sie sie. For more on using this activity, refer to [this section](../../workflow/using/delivery.md).
1. Gehen Sie zur **[!UICONTROL Analysis]** Registerkarte **[!UICONTROL Delivery properties]** und wählen Sie die **[!UICONTROL Prepare the personalization data with a workflow]** Option aus.

   ![](assets/perso_optimization.png)

1. Konfigurieren Sie den Versand und starten Sie den Workflow, um mit der Analyse zu beginnen.

Nach Abschluss der Analyse werden die Personalisierungsdaten mithilfe eines technischen Workflows, der während der Analyse eingerichtet wird, in einer temporären Tabelle gespeichert.

Dieser Workflow ist nicht in der Adobe-Campaign-Benutzeroberfläche sichtbar. Er ist lediglich ein technisches Hilfsmittel, um Personalisierungsdaten rasch zu speichern und zu handhaben.

Nachdem die Analyse abgeschlossen ist, gehen Sie zum Workflow **[!UICONTROL Properties]** und wählen Sie die **[!UICONTROL Variables]** Registerkarte aus. Dort können Sie den Namen der temporären Tabelle sehen, die Sie zum Aufrufen von SQL verwenden können, um die darin enthaltenen IDs anzuzeigen.

![](assets/perso_optimization_temp_table.png)

## Zeitüberschreitung bei der Personalisierung {#timing-out-personalization}

Um den Bereitstellungsschutz zu verbessern, können Sie einen Timeout-Zeitraum für die Personalisierungsphase festlegen.

Wählen Sie auf der **[!UICONTROL Delivery]** Registerkarte der **[!UICONTROL Delivery properties]** Option einen Maximalwert in Sekunden für die **[!UICONTROL Maximum personalization run time]** Option aus.

Wenn die Personalisierungsphase während der Vorschau oder beim Senden die in diesem Feld festgelegte maximale Zeit überschreitet, wird der Prozess mit einer Fehlermeldung abgebrochen und die Bereitstellung schlägt fehl.

![](assets/perso_time-out.png)

Der Standardwert ist 5 Sekunden.

Wenn Sie diese Option auf 0 einstellen, gibt es keine Zeitbeschränkung für die Personalisierungsphase.
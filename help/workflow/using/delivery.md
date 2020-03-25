---
title: Delivery
seo-title: Delivery
description: Delivery
seo-description: null
page-status-flag: never-activated
uuid: 3a74fd0b-8598-46a0-bf13-cf35db0987d7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 9fd7122e-22c7-4f9a-a2a4-5de3daaa3c2e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 366d2149933fa68dfec2a732d1014e1875709cff

---


# Versand{#delivery}

Die Aktivität **Versand** wird je nach Kontext zur Konfiguration oder zum Start eines Versands verwendet. Dabei können Elemente aus eingehenden Transitionen verwendet werden.

Öffnen Sie die Aktivität und wählen Sie in den verschiedenen Bereichen die gewünschten Optionen aus.

![](assets/edit_diffusion.png)

1. **Versand**

   Sie haben folgende Möglichkeiten:

   * Handeln Sie auf dem in der Transition &quot;Inbound&quot;angegebenen Versand. Wählen Sie dazu die erste Option im **[!UICONTROL Delivery]** Abschnitt des Fensters aus.

      Diese Option kann verwendet werden, wenn eine vorangehende Workflow-Aktivität bereits den Versand erstellt oder bezeichnet. Dies kann wie in unten stehendem Beispiel durch eine Aktivität des gleichen Typs erfolgen, die eine ausgehende Transition erzeugt.

      Im Beispiel wird zunächst der Versand erstellt. Dann werden die Zielgruppe und der Inhalt definiert. Schließlich werden die drei Elemente über die eingehende Transition einer zweiten Versandaktivität übermittelt und der Versand gestartet.

      ![](assets/specified_transition_option_exemple.png)

   * Wählen Sie den Versand direkt aus. Wählen Sie dazu die **[!UICONTROL Explicit]** Option aus und wählen Sie den Versand aus der Dropdown-Liste des **[!UICONTROL Delivery]** Felds aus.

      Die Liste zeigt standardmäßig nicht fertige Versand im Ordner &quot; **Versand** &quot;an. Um auf andere Kampagnen zuzugreifen, klicken Sie auf das **[!UICONTROL Select link]** Symbol.

      ![](assets/diffusion_edit_1.png)

      Select the campaign from the drop-down list of the **[!UICONTROL Folder]** field, or click **[!UICONTROL Display sub-levels]** to display all of the deliveries contained in sub-folders:

      ![](assets/diffusion_edit_2.png)

      After selecting the delivery action, you can display the content by clicking the **[!UICONTROL Edit link]** icon.

   * Erstellen Sie ein Skript zur Berechnung des Versands. Wählen Sie dazu die **[!UICONTROL Computed by a script]** Option aus und geben Sie das Skript ein. Sie können ein Eingabefenster öffnen, indem Sie auf die **[!UICONTROL Edit...]** Option klicken. Im folgenden Beispiel wird der Bezeichner des Versands wiederhergestellt:

      ![](assets/diffusion_edit_3.png)

   * Erstellen Sie einen neuen Versand. Wählen Sie dazu die **[!UICONTROL New, created from a template]** Option aus und wählen Sie die Versandvorlage aus, auf der der Versand basieren soll.

      ![](assets/diffusion_edit_4.png)

      Click the **[!UICONTROL Select link]** icon to browse the folders, and click the **[!UICONTROL Edit link]** icon if you wish to view the content of the selected template.

1. **Bereich Empfänger**

   Die Versandempfänger können durch eingehende Ereignisse angegeben werden, beispielsweise Dateiimport, oder Versand. Sie können außerdem aus einer oder mehreren Dateien stammen.

   ![](assets/diffusion_edit_5.png)

1. **Content**

   Der Versandinhalt kann entweder direkt im Versand oder über das eingehende Ereignis definiert werden.

   ![](assets/diffusion_edit_6.png)

1. **Auszuführende Aktion**

   Der Versand kann gespeichert, vorbereitet oder gestartet werden. Weitere Optionen sind die Schätzung der Zielgruppe und das Auslösen eines Testversands.

   ![](assets/diffusion_edit_7.png)

   Kreuzen Sie eine der möglichen Optionen an:

   * **[!UICONTROL Save]**: Mit dieser Option können Sie den Versand erstellen und speichern. Es wird nicht analysiert oder bereitgestellt.
   * **[!UICONTROL Estimate the target]**: Mit dieser Option können Sie die Zielgruppe des Versands berechnen, um sein Potenzial zu bewerten (Phase der ersten Analyse). Dies entspricht der Auswahl der **[!UICONTROL Estimate the population to be targeted]** Option und dem Klicken, **[!UICONTROL Analyze]** wenn ein Versand per **Versand** an die Hauptdatei gesendet wird.
   * **[!UICONTROL Prepare]**: Mit dieser Option können Sie den gesamten Prozess der Analyse (Zielgruppe und Inhaltsvorbereitung) ausführen. Der Versand wird nicht gesendet. Diese Aktion entspricht dem Auswählen der **[!UICONTROL Deliver as soon as possible]** Option und dem Anklicken **[!UICONTROL Analyze]** , wenn ein Versand mit **Versand** an die Haupt-Zielgruppe gesendet wird.
   * **[!UICONTROL Send a proof]**: Mit dieser Option können Sie einen Testversand des Versands senden. Dies entspricht dem Klicken auf die **[!UICONTROL Send a proof]** Schaltfläche in der Symbolleiste eines Versands mit **Versand**
   * **[!UICONTROL Prepare and start]**: Diese Option startet den gesamten Prozess der Analyse (Zielgruppe und Inhaltsvorbereitung) und sendet den Versand. Diese Aktion entspricht dem Klick **[!UICONTROL Deliver as soon as possible]**, **[!UICONTROL Analyze]** und der **[!UICONTROL Confirm delivery]** Option, wenn ein Versand mit **Versand** an die Haupt-Zielgruppe gesendet wird.
   Mit der **[!UICONTROL Act on a delivery]** Aktivität, die im Workflow weiter verwendet wird, können Sie alle verbleibenden Schritte starten, die zum Starten des Versands erforderlich sind (Zielgruppe, Inhaltsvorbereitung, Versand). For more on this, refer to [Delivery control](../../workflow/using/delivery-control.md).

   Darüber hinaus stehen folgende Optionen für die Aktivität zur Verfügung:

   * **[!UICONTROL Generate an outbound transition]**

      Erzeugt eine ausgehende Transition im Anschluss an die Aktivität. Sie haben die Wahl, die Zielgruppe der Versandaktion in der Transition zu übermitteln, oder nicht.

   * **[!UICONTROL Do not recover target]**

      Die Zielgruppe wird nicht mit der ausgehenden Transition übermittelt.

   * **[!UICONTROL Processing errors]**

      Siehe [Versand-Steuerung](../../workflow/using/delivery-control.md).
   Im Tab **Script** können die Versandparameter angepasst werden.

   ![](assets/edit_diffusion_fil_script.png)

## Beispiel: Versand-Workflow {#example--delivery-workflow}

Erstellen Sie einen neuen Workflow und fügen Sie Aktivitäten aus der unten dargestellten Grafik hinzu:

![](assets/new-workflow-5.png)

Öffnen Sie die **Versand**-Aktivität und definieren Sie die Eigenschaften folgendermaßen:

* Wählen Sie im **[!UICONTROL Delivery]** Abschnitt eine Versandvorlage aus **[!UICONTROL New, created from a template]** und wählen Sie sie aus.
* Wählen Sie im **[!UICONTROL Recipients]** Abschnitt **[!UICONTROL Specified in the delivery]**.
* Behalten Sie im **[!UICONTROL Action to execute]** Abschnitt die **[!UICONTROL Prepare]** Option bei.

![](assets/new-workflow-param-delivery.png)

Klicken Sie auf **[!UICONTROL OK]** , um das Eigenschaftenfenster zu schließen. Sie haben soeben eine Aktivität konfiguriert, die darin besteht, einen neuen Versand zu erstellen und vorzubereiten, der auf einer Versandvorlage basiert, deren Zielgruppe darin angegeben wird.

Öffnen Sie die Aktivität **Validierung** und definieren Sie folgende Eigenschaften:

1. Wählen Sie im **[!UICONTROL Assignment type]** Feld eine Gruppe aus, in der Sie registriert sind. Wenn Sie über das Admin-Konto eine Verbindung hergestellt haben, wählen Sie die Administratorgruppe aus.
1. Vergeben Sie einen Titel und geben Sie folgenden Text in den Nachrichten-Textkörper ein:

   ```
   Do you wish to approve delivery (<%= vars.recCount %> recipient(s))?
   ```

   Diese Meldung enthält einen in JavaScript geschriebenen Ausdruck: Die **[!UICONTROL vars.recCount]** Anzahl der Empfänger, auf die sich der Versand der vorherigen Aufgabe bezieht. Weitere Informationen zu JavaScript-Ausdrücken finden Sie unter [JavaScript-Skripten und -Vorlagen](../../workflow/using/javascript-scripts-and-templates.md).

   ![](assets/new-workflow-param-validation.png)

   The Approval task is detailed in [Approval](../../workflow/using/approval.md).

## Eingabeparameter {#input-parameters}

Versand-ID, wenn die **[!UICONTROL Specified in the transition]** Option im **[!UICONTROL Delivery]** Abschnitt ausgewählt ist.

* deliveryId
* tableName
* schema

Jedes eingehende Ereignis muss eine durch diese Parameter definierte Zielgruppe angeben.

>[!NOTE]
>
>Dieser Parameter wird nur angezeigt, wenn die **[!UICONTROL Specified by inbound event(s)]** Option im **[!UICONTROL Recipients]** Abschnitt ausgewählt ist.

* filename

   Vollständiger Name der erstellten Datei, wenn die **[!UICONTROL File(s) specified by inbound event(s)]** Option im **[!UICONTROL Recipients]** Abschnitt ausgewählt ist.

* contentId

   Content Identifier, wenn die **[!UICONTROL Specified by inbound events]** Option im **[!UICONTROL Content]** Abschnitt ausgewählt ist.

## Ausgabeparameter {#output-parameters}

* tableName
* schema
* recCount

Dieser Satz von drei Werten identifiziert die Zielgruppe, die sich aus dem Versand ergibt. **[!UICONTROL tableName]** ist der Name der Tabelle, die die Bezeichner der Zielgruppe speichert, das Schema der Population (normalerweise nms:Empfänger) und die Anzahl der Elemente in der Tabelle **[!UICONTROL schema]** ist **[!UICONTROL recCount]** die Anzahl der Elemente.

Die Transition des Komplements weist die gleichen Parameter auf.

>[!NOTE]
>
>Es gibt keine Ausgabeparameter, wenn die **[!UICONTROL Do not recover target]** Option ausgewählt ist.


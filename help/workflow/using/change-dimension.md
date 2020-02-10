---
title: Dimensionsänderung
seo-title: Dimensionsänderung
description: Dimensionsänderung
seo-description: null
page-status-flag: never-activated
uuid: 6cb309c0-4096-47ce-b1d4-37a3ddafaaa1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 61583062-2349-4ab3-a3bf-310d21894f34
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Dimensionsänderung{#change-dimension}

Die Dimensionsänderung ermöglicht den Wechsel der Zielgruppendimension im Verlauf der Zielbestimmung. Je nach Datenmodell und Eingangsdimension können Sie beispielsweise von der Dimension &quot;Policen&quot; zur Dimension &quot;Kunden&quot; wechseln.

Diese Aktivität bietet des Weiteren die Möglichkeit, Zusatzspalten für die neue Zielgruppe zu definieren.

Außerdem können Deduplizierungskriterien für die Daten angegeben werden.

## Konfiguration {#configuration-mode}

Gehen Sie wie folgt vor:

1. Select the new targeting dimension via the **[!UICONTROL Change dimension]** field.

   ![](assets/s_user_change_dimension_param1.png)

1. Sie können entscheiden, ob alle oder nur bestimmte Elemente in der ausgehenden Transition übermittelt werden sollen. Im vorliegenden Beispiel wird die Anzahl der möglichen Dubletten auf 2 begrenzt.

   ![](assets/s_user_change_dimension_limit.png)

   Wenn Sie nur einen Datensatz beibehalten wollen, erscheint im Arbeitsschema eine Kollektion, welche alle Datensätze, die nicht im Endergebnis enthalten sind, enthält. Anhand dieser Kollektion können Sie, wie bei anderen Kollektionen auch, Aggregate berechnen oder Informationen abrufen.

   For example, if you change the **[!UICONTROL Customers]** dimension to the **[!UICONTROL Recipients]** dimension, it will be possible to target customers of a specific store, while adding the number of purchases made.

1. Wenn Sie nicht alle Datensätze beibehalten, können Sie die Deduplizierungsparameter bestimmen.

   ![](assets/s_user_change_dimension_param2.png)

   Mithilfe der blauen Pfeile lässt sich die Reihenfolge der Dublettenverarbeitung bestimmen.

   Im vorliegenden Beispiel erfolgt die Deduplizierung zunächst über die E-Mail-Adresse und bei Bedarf anschließend über die Kundennummer.

1. The **[!UICONTROL Result]** tab lets you add additional information.

   For example, you can recover the county based on the zip code by using a **Substring** type function. Gehen Sie dazu wie folgt vor:

   * Klicken Sie auf den **[!UICONTROL Add data...]** Link und wählen Sie **[!UICONTROL Data linked to the filtering dimension]**.

      ![](assets/wf_change-dimension_sample_01.png)

      >[!NOTE]
      >
      >For information on creating and managing additional columns, refer to [Adding data](../../workflow/using/query.md#adding-data).

   * Select the previous targeting dimension (before axis switch) and select the **[!UICONTROL Zip Code]** in the recipient&#39;s **[!UICONTROL Location]** sub-tree, then click **[!UICONTROL Edit expression]**.

      ![](assets/wf_change-dimension_sample_02.png)

   * Klicken Sie auf **[!UICONTROL Advanced selection]** und wählen Sie **[!UICONTROL Edit the formula using an expression]**.

      ![](assets/wf_change-dimension_sample_03.png)

   * Verwenden Sie die Funktionsliste, um die Formel zu erstellen.

      ![](assets/wf_change-dimension_sample_04.png)

   * Geben Sie abschließend einen Titel für die neu erstellte Spalte an.

      ![](assets/wf_change-dimension_sample_05.png)

1. Starten Sie den Workflow, um das Ergebnis zu prüfen. Die folgenden Abbildungen zeigen die Tabellen vor und nach der Dimensionsänderung sowie die Struktur der Workflow-Tabellen:

   ![](assets/wf_change-dimension_sample_06.png)

   ![](assets/wf_change-dimension_sample_07.png)


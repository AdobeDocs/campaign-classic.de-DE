---
product: campaign
title: Dimensionsänderung
description: Dimensionsänderung
feature: Workflows, Targeting Activity
hide: true
exl-id: c3de99f8-089f-4c7c-be11-f375a9463eaa
TQID: https://experienceleague.adobe.com/b9Vd8VOP-JcDHPeEInwq3UaFYrjLv2rWkcgyYOMAsiE
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 398
ht-degree: 100%

---

# Dimensionsänderung{#change-dimension}



Mit der Aktivität „Dimensionsänderung“ können Sie die Zielgruppendimension beim Erstellen der Zielgruppe ändern. Die Achsenverschiebung hängt von der Datenvorlage und der Eingabedimension ab. Sie können beispielsweise von der Dimension „Verträge“ zur Dimension „Kunden“ wechseln.

Diese Aktivität bietet des Weiteren die Möglichkeit, Zusatzspalten für die neue Zielgruppe zu definieren.

Außerdem können Deduplizierungskriterien für die Daten angegeben werden.

## Konfiguration {#configuration-mode}

Gehen Sie wie folgt vor:

1. Wählen Sie im Feld **[!UICONTROL Dimensionsänderung]** die neue Zielgruppendimension aus.

   ![](assets/s_user_change_dimension_param1.png)

1. Bei der Dimensionsänderung können Sie alle Elemente beibehalten oder die in der Ausgabe beizubehalten Elemente auswählen. Im folgenden Beispiel ist der Wert für „Max. Anzahl der Duplikate“ auf 2 gesetzt.

   ![](assets/s_user_change_dimension_limit.png)

   Wenn Sie nur einen Eintrag beibehalten möchten, wird im Arbeitsschema eine Sammlung angezeigt, die alle Einträge enthält, die nicht im Endergebnis enthalten sind (da nur Eintrag beibehalten wird). Wie alle anderen Sammlungen können Sie mit dieser Sammlung Aggregate berechnen oder Informationen in Spalten abrufen.

   Wenn Sie beispielsweise von der Dimension **[!UICONTROL Kunden]** zur Dimension **[!UICONTROL Empfänger]** wechseln, können Sie die Kunden eines bestimmten Geschäfts unter Angabe der getätigten Käufe abrufen.

1. Wenn Sie nicht alle Datensätze beibehalten, können Sie die Deduplizierungsparameter bestimmen.

   ![](assets/s_user_change_dimension_param2.png)

   Mithilfe der blauen Pfeile lässt sich die Reihenfolge der Duplikatverarbeitung bestimmen.

   Im vorliegenden Beispiel erfolgt die Deduplizierung zunächst über die E-Mail-Adresse und bei Bedarf anschließend über die Kundennummer.

1. Im **[!UICONTROL Ergebnis]**-Tab kann die Hinzufügung von Zusatzinformationen konfiguriert werden.

   Sie können beispielsweise den Bezirk anhand der Postleitzahl wiederherstellen, indem Sie eine **Substring**-Funktion verwenden. Gehen Sie dazu wie folgt vor:

   * Klicken Sie auf den Link **[!UICONTROL Daten hinzufügen...]** und kreuzen Sie die Option **[!UICONTROL Daten in Relation mit der Filterdimension]** an.

     ![](assets/wf_change-dimension_sample_01.png)

     >[!NOTE]
     >
     >Weitere Informationen zur Erstellung und Verwendung von Zusatzspalten finden Sie unter [Daten hinzufügen](query.md#adding-data).

   * Wählen Sie die ursprüngliche Zielgruppendimension aus (vor der Dimensionsänderung), markieren Sie die **[!UICONTROL Kundennummer]** und klicken Sie auf **[!UICONTROL Ausdruck bearbeiten]****[!UICONTROL .]**

     ![](assets/wf_change-dimension_sample_02.png)

   * Klicken Sie auf die Schaltfläche **[!UICONTROL Erweiterte Auswahl]** und kreuzen Sie die Option **[!UICONTROL Formel von einem Ausdruck ausgehend erstellen]** an.

     ![](assets/wf_change-dimension_sample_03.png)

   * Verwenden Sie die Funktionsliste, um die Formel zu erstellen.

     ![](assets/wf_change-dimension_sample_04.png)

   * Geben Sie abschließend einen Titel für die neu erstellte Spalte an.

     ![](assets/wf_change-dimension_sample_05.png)

1. Führen Sie den Workflow aus, um das Ergebnis dieser Konfiguration anzuzeigen. Die folgenden Abbildungen zeigen die Tabellen vor und nach der Dimensionsänderung sowie die Struktur der Workflow-Tabellen:

   ![](assets/wf_change-dimension_sample_06.png)

   ![](assets/wf_change-dimension_sample_07.png)

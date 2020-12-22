---
title: Verwenden der Merge-Funktion der Deduplizierung-Duplikate-Aktivität
description: Erfahren Sie, wie Sie die Merge-Funktion der Deduplizierung-Duplikate-Aktivität verwenden
page-status-flag: never-activated
uuid: 8887574e-447b-48a5-afc6-95783ffa7fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 4113c3fe-a279-4fe1-be89-ea43c96edc34
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 32a14eb99847dc04a582623204bc856c29fa4359
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 8%

---


# Verwenden der Merge-Funktion der Deduplizierung-Duplikate-Aktivität {#deduplication-merge}

## Über diesen Verwendungsfall {#about-this-use-case}

In diesem Verwendungsfall wird beschrieben, wie Sie die Funktion **[!UICONTROL Zusammenführen]** in der Aktivität **[!UICONTROL Deduplizierung-Duplikate]** verwenden.

Weitere Informationen zu dieser Funktion finden Sie in [diesem Abschnitt](../../workflow/using/deduplication.md#merging-fields-into-single-record).

Die Aktivität **[!UICONTROL Deduplizierung-Duplikate]** wird zum Entfernen von Duplikat-Zeilen aus einem Datensatz verwendet. In diesem Fall werden die unten angezeigten Daten anhand des E-Mail-Felds dupliziert.

| Datum der letzten Änderung | Vorname | Nachname | E-Mail | Mobiltelefon | Phone |
|-----|------------|-----------|-------|--------------|------|
| 19.05.2020 | Robert | Tisner | bob@mycompany.com | 444-444-444 | 777-777-7777 |
| 22.07.2020 | Bobby | Tisner | bob@mycompany.com |  | 777-777-7777 |
| 03.10.2020 | Bob |  | bob@mycompany.com |  | 888-888-8888 |

Mit der Funktion **[!UICONTROL Zusammenführen]** der Deduplizierung-Duplikate-Aktivität können Sie einen Regelsatz für das Deduplizierung-Duplikate konfigurieren, um eine Feldgruppe zu definieren, die zu einem einzigen Ergebnisdatensatz zusammengeführt werden soll. Bei einer Reihe von Duplikat-Datensätzen können Sie beispielsweise die älteste Telefonnummer oder den neuesten Namen beibehalten.

## Aktivieren der Funktion zum Zusammenführen {#activating-merge}


Um die Zusammenführungsfunktion zu aktivieren, müssen Sie zunächst die Aktivität **[!UICONTROL Deduplizierung-Duplikate]** konfigurieren. Gehen Sie dazu wie folgt vor:

1. Öffnen Sie die Aktivität und klicken Sie dann auf den Link **[Konfiguration bearbeiten]**.

1. Wählen Sie das für das Deduplizierung-Duplikate zu verwendende Abgleichungsfeld aus und klicken Sie dann auf **[!UICONTROL Weiter]**. In diesem Beispiel möchten wir die Duplizierung basierend auf dem E-Mail-Feld deduplizieren.

   ![](assets/uc_merge_edit.png)

1. Klicken Sie auf den Link **[!UICONTROL Erweiterte Parameter]** und aktivieren Sie dann die Optionen **[!UICONTROL Datensätze zusammenführen]** und **[!UICONTROL Verwenden Sie mehrere Optionen zum Zusammenführen von Datensätzen]**.

   ![](assets/uc_merge_advanced_parameters.png)

1. Die Registerkarte **[!UICONTROL Zusammenführen]** wird dem Konfigurationsbildschirm **[!UICONTROL Deduplizierung-Duplikate]** hinzugefügt. Auf dieser Registerkarte können Sie die Daten angeben, die beim Ausführen des Deduplizierung-Duplikate zusammengeführt werden sollen.

## Konfigurieren der zusammenzuführenden Felder {#configuring-rules}

Hier sind die Regeln, mit denen die Daten in einem Datensatz zusammengeführt werden sollen:

* Belassen Sie den neuesten Namen (Vorname- und Nachname-Felder),
* Behalten Sie das neueste Mobiltelefon bei.
* Halten Sie die älteste Telefonnummer,
* Alle Felder in einer Gruppe müssen ungleich null sein, damit sie für den endgültigen Datensatz infrage kommen.

Gehen Sie wie folgt vor, um diese Regeln zu konfigurieren:

1. Öffnen Sie die Registerkarte **[!UICONTROL Zusammenführen]** und klicken Sie dann auf die Schaltfläche **[!UICONTROL Hinzufügen]**.

   ![](assets/uc_merge_add.png)

1. Geben Sie den Bezeichner und die Beschriftung der Gruppe der zusammenzuführenden Felder an.

   ![](assets/uc_merge_identifier.png)

1. Geben Sie die Bedingungen für die Auswahl der zu berücksichtigenden Datensätze an.

   ![](assets/uc_merge_filter.png)

1. Sortieren Sie nach dem Datum der letzten Änderung, um den neuesten Namen auszuwählen.

   ![](assets/uc_merge_sort.png)

1. Wählen Sie die zusammenzuführenden Felder aus. In diesem Beispiel möchten wir die Felder für Vor- und Nachnamen beibehalten.

   ![](assets/uc_merge_keep.png)

1. Die Felder werden dem Datensatz hinzugefügt, der zusammengeführt werden soll, und dem Workflow-Schema wird ein neues Element hinzugefügt.

   Wiederholen Sie diese Schritte, um die Felder für Mobiltelefone und Smartphones zu konfigurieren.

   ![](assets/dedup8.png)

   ![](assets/dedup9.png)

## Ergebnisse {#results}

Nach dem Konfigurieren dieser Regeln werden die folgenden Daten am Ende der Aktivität **[!UICONTROL Deduplizierung-Duplikate]** empfangen.

| Änderungsdatum | Vorname | Nachname | E-Mail | Mobiltelefon | Telefon |
-----|------------|-----------|-------|--------------|------|
| 19.05.2020 | Robert | Tisner | bob@mycompany.com | 444-444-444 | 777-777-7777 |
| 22.07.2020 | Bobby | Tisner | bob@mycompany.com |  | 777-777-7777 |
| 03.10.2020 | Bob |  | bob@mycompany.com |  | 888-888-8888 |

Das Ergebnis wird aus den drei Datensätzen gemäß den zuvor konfigurierten Regeln zusammengeführt. Nach dem Vergleich wird der Schluss gezogen, dass der aktuelle Name und das Mobiltelefon zusammen mit der ursprünglichen Telefonnummer verwendet werden.

| Vorname | Nachname | E-Mail | Mobiltelefon | Telefon |
|------------|-----------|-------|--------------|------|
| Bobby | Tisner | bob@mycompany.com | 444-444-4444 | 888-888-8888 |

>[!NOTE]
>
> Beachten Sie, dass der Vorname, der zusammengeführt wurde, &quot;Bobby&quot;ist, da wir eine &quot;Name&quot;-Regel konfiguriert haben, die sowohl aus dem Vor- als auch dem Nachnamen besteht.
>
>Daher konnte &quot;Bob&quot;(der letzte Vorname) nicht berücksichtigt werden, da das zugehörige Feld für den Nachnamen leer war. Die neueste Kombination aus Vor- und Nachnamen wurde im finalen Datensatz zusammengeführt.

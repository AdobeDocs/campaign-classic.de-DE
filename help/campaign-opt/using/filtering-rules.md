---
product: campaign
title: Filterregeln
description: Informationen zur Verwendung von Filterregeln in Adobe Campaign
role: User, Developer
feature: Typology Rules, Campaigns
hide: true
exl-id: a4d12445-5680-4704-9c67-e43e0ea6631b
source-git-commit: 720a5f4edf534788f7fd143a476c25e58a6f1586
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 83%

---

# Filterregeln{#filtering-rules}

Mit Filterregeln können Sie die auszuschließenden Nachrichten auf der Grundlage von in einer Abfrage definierten Kriterien definieren. Diese Regeln sind mit einer Zielgruppendimension verknüpft.

Filterregeln können mit anderen Regeltypen (Kontrolle, Druck usw.) verknüpft werden in Typologien oder in einer eigenen Typologie **Filterung** zusammengefasst. Weitere Informationen finden Sie unter [Filtertypologien erstellen und anwenden](#creating-and-using-a-filtering-typology).

## Erstellen einer Filterregel {#creating-a-filtering-rule}

Sie können beispielsweise die Abonnenten Ihrer Newsletter filtern, um keine Nachrichten an minderjährige Empfänger zu senden.

Gehen Sie wie folgt vor:

1. Erstellen Sie eine Typologieregel vom Typ **[!UICONTROL Filter]**, die sich auf alle Kommunikationskanäle anwenden lässt.

   ![](assets/campaign_opt_create_filter_01.png)

1. Ändern Sie die Standard-Zielgruppendimension und wählen Sie die Abonnements aus (**nms:subscription**).

   ![](assets/campaign_opt_create_filter_02.png)

1. Erstellen Sie den Filter über den Link **[!UICONTROL Abfrage von der Zielgruppendimension ausgehend bearbeiten]**.

   ![](assets/campaign_opt_create_filter_03.png)

1. Verbinden Sie die Regel mit einer Kampagnentypologie und speichern Sie sie.

   ![](assets/campaign_opt_create_filter_04.png)

Wenn diese Regel in einem Versand verwendet wird, werden minderjährige Abonnenten automatisch ausgeschlossen. Eine bestimmte Meldung gibt die Anwendung der Regel an:

![](assets/campaign_opt_create_filter_05.png)

## Erstellen von Bedingungen für eine Filterregel {#conditioning-a-filtering-rule}

Die Anwendungskriterien einer Filterregel können dem verknüpften Versand oder Versandentwurf entsprechend eingeschränkt werden.

Gehen Sie hierzu in den Tab **[!UICONTROL Allgemein]** der Typologieregel, wählen Sie das Anwendungskriterium aus und erstellen Sie den Filter wie nachfolgend dargestellt:

![](assets/campaign_opt_create_filter_06.png)

In diesem Fall wird die Regel nur auf die Sendungen angewandt, die den Kriterien des Filters entsprechen, auch wenn die Regel mit allen Sendungen verbunden ist.

>[!NOTE]
>
>Typologien und Filterregeln können in einem Workflow über die Aktivität **[!UICONTROL Versandentwurf]** verwendet werden. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../workflow/using/delivery-outline.md).

## Erstellen und Verwenden einer Filtertypologie {#creating-and-using-a-filtering-typology}

Sie haben die Möglichkeit, Typologien zu erstellen, die nur Filterregeln enthalten.**&#x200B;**

![](assets/campaign_opt_create_typo_filtering.png)

Diese spezifischen Typologien können bei der Zielgruppenbestimmung einem Versand zugeordnet werden: Klicken Sie Versandassistenten auf den Link **[!UICONTROL An]** und dann auf den Tab **[!UICONTROL Ausschlüsse]**.

![](assets/campaign_opt_apply_typo_filtering.png)

Wählen Sie dann die Filtertypologie aus, die auf den Versand angewendet werden soll. Klicken Sie dazu auf die Schaltfläche **[!UICONTROL Hinzufügen]** und wählen Sie die Typologien aus, die angewendet werden sollen.

Sie können Filterregeln auch direkt über diese Registerkarte verknüpfen, ohne sie in einer Typologie zu gruppieren. Verwenden Sie dazu den unteren Bereich des Fensters.

![](assets/campaign_opt_select_typo_filtering.png)

>[!NOTE]
>
>In diesem Auswahlfenster sind nur Filtertypologien und -regeln verfügbar.
>
>Diese Konfigurationen können in Versandvorlagen vorgenommen werden, um sie automatisch bei jedem mithilfe dieser Vorlagen erstellten Versand anzuwenden.
>

## Standardmäßige Ausschlussregeln für Zustellbarkeit {#default-deliverability-exclusion-rules}

Standardmäßig sind zwei Filterregeln verfügbar: **[!UICONTROL Adressen ausschließen]** ( **[!UICONTROL addressExclusions]** ) und **[!UICONTROL Domains ausschließen]** ( **[!UICONTROL domainExclusions]** ). Während der E-Mail-Analyse vergleichen diese Regeln die E-Mail-Adressen der Empfänger mit den unzulässigen Adressen oder Domain-Namen aus einer verschlüsselten globalen Unterdrückungsliste, die in der Zustellbarkeitsinstanz verwaltet wird. Im Falle einer Übereinstimmung wird die Nachricht nicht an den jeweiligen Empfänger gesendet.

Auf diese Weise soll das Hinzufügen zur Blockierungsliste aufgrund von schädlichen Aktivitäten, insbesondere durch die Verwendung von Spamtraps, vermieden werden. Wenn beispielsweise für die Anmeldung über ein Web-Formular eine Spamtrap verwendet wird, wird automatisch eine Bestätigungs-E-Mail an diese Spamtrap gesendet. Als Folge davon wird Ihre Adresse automatisch auf die Blockierungsliste gesetzt.

>[!NOTE]
>
>Die Adressen und Domain-Namen in der globalen Unterdrückungsliste sind verborgen. In den Versandanalyse-Logs wird nur die Anzahl der ausgeschlossen Empfänger angegeben.

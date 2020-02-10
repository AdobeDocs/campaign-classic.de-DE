---
title: Filterregeln
seo-title: Filterregeln
description: Filterregeln
seo-description: null
page-status-flag: never-activated
uuid: 24238a99-1f0f-4d04-9807-557ec2a5ba16
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 0d50826e-2211-4c3b-8413-ca1453bba6c4
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Filterregeln{#filtering-rules}

Filterregeln ermöglichen es, auszuschließende Nachrichten nach in einer Abfrage definierten Kriterien zu bestimmen. Diese Regeln werden mit einer Zielgruppendimension verknüpft.

Filtering rules can be linked to other types of rules (control, pressure, etc.) in typologies, or grouped in a dedicated **Filtering** typology. Weitere Informationen finden Sie unter [Erstellen und Verwenden einer Filtertypologie](#creating-and-using-a-filtering-typology).

## Filterregel erstellen {#creating-a-filtering-rule}

Sie können beispielsweise die Abonnenten Ihrer Newsletter filtern, um keine Nachrichten an minderjährige Empfänger zu senden.

Gehen Sie wie folgt vor:

1. Create a **[!UICONTROL Filtering]** typology rule applicable to all communication channels.

   ![](assets/campaign_opt_create_filter_01.png)

1. Verändern Sie die Standard-Zielgruppenbestimmung und wählen Sie die Abonnements aus (**nms:subscription**).

   ![](assets/campaign_opt_create_filter_02.png)

1. Erstellen Sie den Filter mithilfe des **[!UICONTROL Edit the query from the targeting dimension...]** Links.

   ![](assets/campaign_opt_create_filter_03.png)

1. Verbinden Sie die Regel mit einer Kampagnentypologie und speichern Sie sie.

   ![](assets/campaign_opt_create_filter_04.png)

Bei Anwendung dieser Regel in einem Versand werden minderjährige Abonnenten automatisch ausgeschlossen. Eine spezifische Nachricht gibt die Anwendung der Regel an:

![](assets/campaign_opt_create_filter_05.png)

## Bedingungen für Filterregeln erstellen {#conditioning-a-filtering-rule}

Die Anwendungskriterien einer Filterregel können dem Versand oder dem verknüpften Versandentwurf entsprechend eingeschränkt werden.

To do this, go to the **[!UICONTROL General]** tab of the typology rule, select the type of restriction to apply and create the filter, as shown below:

![](assets/campaign_opt_create_filter_06.png)

In diesem Fall wird die Regel nur auf die Sendungen angewandt, die den Kriterien des Filters entsprechen, auch wenn die Regel mit allen Sendungen verbunden ist.

>[!NOTE]
>
>Typologies and filtering rules can be used in a workflow, in the **[!UICONTROL Delivery outline]** activity. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../workflow/using/delivery-outline.md).

## Filtertypologien erstellen und anwenden {#creating-and-using-a-filtering-typology}

You can create **[!UICONTROL Filtering]** typologies: they only contain filtering rules.

![](assets/campaign_opt_create_typo_filtering.png)

These specific typologies can be linked to a delivery when the target is selected: in the delivery wizard, click the **[!UICONTROL To]** link, then click the **[!UICONTROL Exclusions]** tab.

![](assets/campaign_opt_apply_typo_filtering.png)

Wählen Sie dann die Filtertypologie aus, die auf die Bereitstellung angewendet werden soll. Klicken Sie dazu auf die **[!UICONTROL Add]** Schaltfläche und wählen Sie die anzuwendenden Typologien aus.

Im unteren Bereich des gleichen Tabs können Sie zudem einzelne Filterregeln hinzufügen, die nicht in einer Typologie zusammengefasst sind.

![](assets/campaign_opt_select_typo_filtering.png)

>[!NOTE]
>
>* In diesem Auswahlfenster sind nur Filtertypologien und -regeln verfügbar.
>* Diese Konfigurationen können in Versandvorlagen vorgenommen werden, um sie automatisch bei jedem mithilfe dieser Vorlagen erstellten Versand anzuwenden.
>



## Standardmäßige Ausschlussregeln für Zustellbarkeit {#default-deliverability-exclusion-rules}

Standardmäßig sind zwei Filterregeln verfügbar: **[!UICONTROL Exclude addresses]** ( **[!UICONTROL addressExclusions]** ) und **[!UICONTROL Exclude domains]** ( **[!UICONTROL domainExclusions]** ). Während der E-Mail-Analyse vergleichen diese Regeln die E-Mail-Adressen der Empfänger mit den unzulässigen Adressen oder Domain-Namen aus einer verschlüsselten globalen Unterdrückungsliste, die in der Zustellbarkeitsinstanz verwaltet wird. Im Falle einer Übereinstimmung wird die Nachricht nicht an den jeweiligen Empfänger gesendet.

Auf diese Weise soll Blacklisting aufgrund von schädlichen Aktivitäten, insbesondere durch die Verwendung von Spamtraps, vermieden werden. Wenn beispielsweise für die Anmeldung über ein Webformular eine Spamtrap verwendet wird, wird automatisch eine Bestätigungs-E-Mail an diese Spamtrap gesendet. Als Folge davon wird Ihre Adresse automatisch auf die Blacklist gesetzt.

>[!NOTE]
>
>Die Adressen und Domain-Namen in der globalen Unterdrückungsliste sind verborgen. In den Versandanalyse-Logs wird nur die Anzahl der ausgeschlossen Empfänger angegeben.


---
title: Über Kampagnentypologien
seo-title: Über Kampagnentypologien
description: Über Kampagnentypologien
seo-description: null
page-status-flag: never-activated
uuid: ec89fb14-7e2f-4e9f-b7ab-3c2caf93a697
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 72c5151c-ce1e-425a-9aee-beefe9f21a67
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 44d8ba19f2e79d30229239312e6a5148d247fb28

---


# Über Kampagnentypologien{#about-campaign-typologies}

Die Kampagnenoptimierung ist das Adobe Campaign-Modul, mit dem Sie das Senden von Auslieferungen steuern, filtern und überwachen können. Um Konflikte zwischen Kampagnen zu vermeiden, kann Adobe Campaign verschiedene Kombinationen testen, indem es spezifische Beschränkungsregeln anwendet. Dadurch wird gewährleistet, dass die gesendeten Nachrichten den Bedürfnissen und Erwartungen der Kunden und den Kommunikationsrichtlinien des Unternehmens entsprechen.

>[!NOTE]
>
>Abhängig von Ihrem Abonnement ist die Kampagnenoptimierung entweder im Lieferumfang enthalten oder als Add-on verfügbar. Überprüfen Sie diesbezüglich bitte Ihren Lizenzvertrag.

## Typologieregeln {#typology-rules}

Mit Adobe Campaign können vier Arten von Typologieregeln erstellt und angewendet werden:

1. **Filtern** von Regeln, mit denen Sie einen Teil des Ziels auf der Grundlage von Kriterien ausschließen können. For more on this, refer to [Filtering rules](../../campaign/using/filtering-rules.md).
1. **Druckregeln** , mit denen Sie Marketingmüdigkeit kontrollieren können. For more on this, refer to [Pressure rules](../../campaign/using/pressure-rules.md).
1. **Kapazitätsregeln** , mit denen Sie Lasten begrenzen können, um optimale Verarbeitungsbedingungen zu gewährleisten. For more on this, refer to [Controlling capacity](../../campaign/using/consistency-rules.md#controlling-capacity).
1. **Steuerungsregeln** , mit denen Sie die Gültigkeit von Nachrichten überprüfen können, bevor sie gesendet werden. For more on this, refer to [Control rules](../../campaign/using/control-rules.md).

Nach ihrer Erstellung werden die Typologieregeln in Kampagnentypologien gruppiert, die in den Sendungen referenziert werden. Siehe [Anwenden von Typologien](#applying-typologies).

## Typologien {#typologies}

Eine Kampagnentypologie kann mehrere [Typologieregeln](#typology-rules) enthalten, eine Sendung kann jedoch nur eine Typologie referenzieren.

The **[!UICONTROL Rules]** tab lets you add, delete or view the typology rules to apply.

![](assets/campaign_opt_rules_tab.png)

## Anwenden von Typologien {#applying-typologies}

Gehen Sie wie folgt vor, um eine Typologie zu erstellen und auf Ihre Sendungen anzuwenden:

1. Erstellen Sie Typologieregeln.

   Typologieregeln finden Sie im **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** Knoten.

   Erläuterungen zu den verschiedenen in Campaign verfügbaren Regeln finden Sie in den folgenden Abschnitten: [Werbedruck-Regeln](../../campaign/using/pressure-rules.md), [Kapazitätsregeln](../../campaign/using/consistency-rules.md#controlling-capacity), [Kontrollregeln](../../campaign/using/control-rules.md) und [Filterregeln](../../campaign/using/filtering-rules.md).

1. Erstellen Sie eine Typologie und referenzieren Sie diese mit den Regeln, die Sie erstellt haben.

   Der Zugriff auf Typologien erfolgt über den Knoten **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]** .

1. Konfigurieren Sie Ihre Sendung so, dass sie die von Ihnen erstellte Typologie verwendet. Näheres hierzu finden Sie in [diesem Abschnitt](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery).
1. Führen Sie eine Kampagnensimulation durch, um das Verhalten zu testen und anzupassen. Näheres zur Simulation von Kampagnen finden Sie in [diesem Abschnitt](../../campaign/using/campaign-simulations.md).

Bei der Versandvorbereitung werden diejenigen Empfänger ausgeschlossen, die das jeweilige Kriterium erfüllen. Über die Logs können Sie überprüfen, welche Empfänger vom Versand ausgeschlossen wurden. Anwendungsbeispiele für Typologieregeln vom Typ &quot;Druck&quot; finden Sie auf [dieser Seite](../../campaign/using/pressure-rules.md#use-cases-on-pressure-rules).

**Verwandtes Thema**

* [Anwendung automatischer Geschäftsregeln auf Auslieferungen auf einem beliebigen Kanal](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)
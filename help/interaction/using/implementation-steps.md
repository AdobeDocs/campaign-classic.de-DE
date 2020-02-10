---
title: Umsetzung
seo-title: Umsetzung
description: Umsetzung
seo-description: null
page-status-flag: never-activated
uuid: 11582071-00a2-4245-af3e-bc81174ce223
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: general-operation
discoiquuid: 7f79c0d8-77b0-4cc6-a888-7dbd32d2f3b6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Umsetzung{#implementation-steps}

## Konfiguration {#configuring-interaction}

>[!NOTE]
>
>Die im Folgenden beschriebenen Konfigurationsschritte sind von einem **Administrator** durchzuführen. Sie betreffen ausschließlich Design-Umgebungen.

1. Erstellen von Benutzerprofilen. For more on this, refer to [Operator profiles](../../interaction/using/operator-profiles.md).
1. Erstellen einer Angebotsumgebung durch Targeting-Dimension. Weitere Informationen finden Sie unter [Erstellen einer Angebotsumgebung](../../interaction/using/live-design-environments.md#creating-an-offer-environment).
1. Erstellen von Typologieregeln für jede Umgebung. Weitere Informationen hierzu finden Sie unter [Erstellen und Verweisen auf eine Angebotsbildungsregel](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule).
1. Erstellen von Angebotsbereichen für jede Umgebung und Konfigurieren von Renderfunktionen. For more on this, refer to [Creating offer spaces](../../interaction/using/creating-offer-spaces.md).

   >[!NOTE]
   >
   >Wenn eine Platzierung in einem Einzelmodus-Kanal als identifiziert definiert wurde, müssen ihre erweiterten Parameter angegeben werden.

1. Konfiguration des Angebotsmoduls für eingehende Interaktionen, um Angebote zu unterbreiten und zu aktualisieren.

   Die verschiedenen Integrationsmodi werden unter [Eingehende Kanäle](../../interaction/using/about-inbound-channels.md)beschrieben.

   >[!NOTE]
   >
   >Bei Erstellung einer Platzierung für den Web-Kanal (eingehend) ist auch die Seite zu konfigurieren, auf der das Angebot angezeigt werden soll.

## Verwaltung des Angebotskatalogs {#managing-the-offer-catalog-}

>[!NOTE]
>
>Die im Folgenden beschriebenen Schritte sind von einem **Angebotsverantwortlichen** durchzuführen.

1. Erstellen von Angebotskategorien in Designumgebungen. For more on this, refer to [Creating offer categories](../../interaction/using/creating-offer-categories.md).
1. Erstellen von Angeboten in Designumgebungen. For more on this, refer to [Creating an offer](../../interaction/using/creating-an-offer.md).
1. Genehmigung und Veröffentlichung von Angeboten an einem oder mehreren Stellen, um sie in Live-Umgebungen für den Bereitstellungsmanager verfügbar zu machen. Weitere Informationen finden Sie unter [Genehmigen und Aktivieren eines Angebots](../../interaction/using/approving-and-activating-an-offer.md).

## Verwendung des Angebotskatalogs {#using-the-offer-catalog-}

>[!NOTE]
>
>Die im Folgenden beschriebenen Schritte sind von einem **Versandverantwortlichen** durchzuführen. Dieser hat nur auf Angebote in Live-Umgebungen Zugriff.

1. Kampagnen erstellen.
1. Verweis auf ein Angebot in einer Kampagne oder Kampagnenbereitstellung. For more on this, refer to [About outbound channels](../../interaction/using/about-outbound-channels.md).


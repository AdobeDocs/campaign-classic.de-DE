---
product: campaign
title: Implementierungsschritte
description: Implementierungsschritte für das Campaign Interaction-Modul
feature: Interaction, Offers
exl-id: 82b88ab7-6a95-4bb3-b8b3-abea0fdd4ca0
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 100%

---

# Implementierungsschritte{#implementation-steps}



## Konfiguration {#configuring-interaction}

>[!NOTE]
>
>Die im Folgenden beschriebenen Konfigurationsschritte sind von einem **Administrator** durchzuführen. Sie betreffen ausschließlich Design-Umgebungen.

1. Erstellung von Benutzerprofilen. Weitere Informationen hierzu finden Sie im Abschnitt [Benutzerprofile](../../interaction/using/operator-profiles.md).
1. Erstellung von Angebotsumgebungen anhand von Zielgruppendimensionen. Weiterführende Informationen dazu finden Sie unter [Angebotsumgebungen](../../interaction/using/live-design-environments.md#creating-an-offer-environment).
1. Erstellung von Typologieregeln für einzelne Umgebungen. Weitere Informationen hierzu finden Sie unter [Unterbreitungsregeln erstellen und zuweisen](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule).
1. Erstellung von Angebotsplatzierungen für einzelne Umgebungen und Konfiguration von Rendering-Funktionen. Weitere Informationen hierzu finden Sie unter [Angebotsplatzierungen](../../interaction/using/creating-offer-spaces.md).

   >[!NOTE]
   >
   >Wenn eine Platzierung in einem Einzelmodus-Kanal als identifiziert definiert wurde, müssen ihre erweiterten Parameter angegeben werden.

1. Konfiguration des Angebotsmoduls für eingehende Interaktionen, um Angebote zu unterbreiten und zu aktualisieren.

   Die verschiedenen Integrationsmodi werden im Abschnitt [Über eingehende Kanäle](../../interaction/using/about-inbound-channels.md) beschrieben.

   >[!NOTE]
   >
   >Bei Erstellung einer Platzierung für den Web-Kanal (eingehend) ist auch die Seite zu konfigurieren, auf der das Angebot angezeigt werden soll.

## Verwaltung des Angebotskatalogs {#managing-the-offer-catalog-}

>[!NOTE]
>
>Die im Folgenden beschriebenen Schritte sind von einem **Angebotsverantwortlichen** durchzuführen.

1. Erstellung von Angebotskategorien in Design-Umgebungen. Weitere Informationen hierzu finden Sie unter [Angebotskategorien](../../interaction/using/creating-offer-categories.md).
1. Erstellung von Angeboten in Design-Umgebungen. Weiterführende Informationen finden Sie unter [Erstellung eines Angebots](../../interaction/using/creating-an-offer.md).
1. Validierung und Veröffentlichung der Angebote in einer oder mehreren Platzierungen, um sie in den Live-Umgebungen für den Versandverantwortlichen verfügbar zu machen. Weitere Informationen finden Sie unter [Angebotsvalidierung](../../interaction/using/approving-and-activating-an-offer.md).

## Verwendung des Angebotskatalogs {#using-the-offer-catalog-}

>[!NOTE]
>
>Die im Folgenden beschriebenen Schritte sind von einem **Versandverantwortlichen** durchzuführen. Dieser hat nur auf Angebote in Live-Umgebungen Zugriff.

1. Kampagnen erstellen.
1. Verweis auf ein Angebot in einer Kampagne oder im gebündelten Versand einer Kampagne. Weitere Informationen hierzu finden Sie im Abschnitt [Über ausgehende Kanäle](../../interaction/using/about-outbound-channels.md).

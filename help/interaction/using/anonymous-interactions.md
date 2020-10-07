---
title: Anonyme Interaktionen
seo-title: Anonyme Interaktionen
description: Anonyme Interaktionen
seo-description: null
page-status-flag: never-activated
uuid: 6e28e8a4-8d2f-4747-8dd0-680fbf02b25d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: unitary-interactions
discoiquuid: 3fd7a1ef-b0e2-4a7e-9e36-044d997db785
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 100%

---


# Anonyme Interaktionen{#anonymous-interactions}

Sehen Sie sich dieses [Video](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&amp;ref=helpx.adobe.com) an, um einen Überblick darüber zu erhalten, wie Angebote an identifizierte und anonyme Zielgruppen gesendet werden.

## Umgebung für anonyme Interaktionen {#targeting-and-storing-an-environment-for-anonymous-interactions}

Standardmäßig wird Interaction mit einer Umgebung geliefert, die für ein Zielgruppen-Mapping der Empfängertabelle konfiguriert ist, also für Angebote an identifizierte Kontakte. Sollten Sie eine andere Tabelle (beispielsweise die Besuchertabelle für anonyme Angebote) verwenden wollen, müssen Sie eine neue Umgebung mit einem entsprechenden Zielgruppen-Mapping erstellen. Hierzu steht Ihnen ein Assistent zur Verfügung. Weiterführende Informationen finden Sie unter [Angebotsumgebungen](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

Bei der Erstellung einer anonymen Umgebung mithilfe des Assistenten ist im Tab **[!UICONTROL Allgemein]** das Feld **[!UICONTROL Für anonyme eingehende Interaktionen reservierte Umgebung]** bereits angekreuzt.

Die **[!UICONTROL Zielgruppendimension]** wird vorausgefüllt und verweist standardmäßig auf die Besuchertabelle.

Auch das Feld **[!UICONTROL Besucherordner]** enthält bereits den Ordner **[!UICONTROL Besucher]**. Dieses Feld dient der Angabe des Speicherorts der Besucherprofile.

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>Wenn Sie verschiedene Besuchertypen unterscheiden möchten, beispielsweise im Fall von anonymen Angeboten verschiedener Marken, müssen Sie für jede Marke eine Umgebung und einen zugeordneten **[!UICONTROL Besucher]**-Ordner erstellen.

## Angebotskataloge für anonyme Interaktionen {#offer-catalog-for-anonymous-interactions}

Wie bei ausgehenden spielt der Angebotskatalog auch bei eingehenden Interaktionen eine zentrale Rolle. Er enthält alle nach Kategorien geordneten Angebote.

Wenden Sie zum Erstellen von Kategorien und Platzierungen denselben Prozess an wie für identifizierte Besucher (siehe [Angebotskategorien](../../interaction/using/creating-offer-categories.md) und [Angebotsumgebungen](../../interaction/using/live-design-environments.md#creating-an-offer-environment)).

## Anonyme Besucher {#anonymous-visitors}

Anonyme Besucher können beim Webseitenaufruf einem Identifizierungsversuch durch Cookies unterzogen werden. Diese s. g. implizite Erkennung beruht auf dem Navigationsverlauf des Besuchers.

Während dieser Etappe werden die mithilfe der Cookies gesammelten Informationen zu den in Ihrer Datenbank enthaltenen Daten in Beziehung gebracht. Auf diese Weise können gewisse Besucher erkannt, also implizit identifiziert werden. Gelingt die Identifizierung nicht, bleibt der Besucher anonym.

Kreuzen Sie in der Platzierung das Feld **[!UICONTROL Person implizit über den Navigationsverlauf identifizieren]** an, wenn Sie diese Möglichkeit nutzen wollen.

![](assets/identification_anonymous_visitors.png)

## Umgang mit anonymen, nicht identifizierten Besuchern {#processing-unidentified-anonymous-visitors}

Wenn ein Besucher nicht identifiziert werden konnte, können seine Daten in einer bestimmten Platzierung gespeichert werden. Auf diese Weise können ihm spezifische Angebote unterbreitet werden, die speziell für diesen Besuchertyp definierten Typologieregeln entsprechen.

Für nicht identifizierte Kontakte oder solche, die zwar implizit identifiziert werden können, denen Sie aber keine für bekannte Kontakte erstellten Angebote unterbreiten möchten, haben Sie die Möglichkeit, in eine anonyme Umgebung wechseln.

Kreuzen Sie hierfür das Feld **[!UICONTROL Zu einer anonymen Platzierung wechseln, wenn keine Zielperson identifiziert wurde]** an und geben Sie im Feld **[!UICONTROL Zugeordnete anonyme Platzierung]** die den nicht identifizierten Besuchern vorbehaltene Umgebung an.

![](assets/anonymous_to_anonymous_environment.png)


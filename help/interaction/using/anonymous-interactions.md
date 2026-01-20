---
product: campaign
title: Anonyme Interaktionen
description: Anonyme Interaktionen
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: a8face46-a933-4f2c-8299-ccb66f05967d
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: ht
source-wordcount: '443'
ht-degree: 100%

---

# Anonyme Interaktionen{#anonymous-interactions}



![](assets/do-not-localize/how-to-video.png) Sehen Sie sich dieses [Video](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&ref=helpx.adobe.com) an, um einen Überblick darüber zu erhalten, wie Angebote an identifizierte und anonyme Zielgruppen gesendet werden.

## Umgebung für anonyme Interaktionen {#targeting-and-storing-an-environment-for-anonymous-interactions}

Interactio verfügt standardmäßig über eine vorab konfigurierte Umgebung, in der die Empfängertabelle (identifizierte Angebote) ausgewählt werden kann. Um eine andere Tabelle (beispielsweise die Besuchertabelle für anonyme Angebote oder eine spezifische Empfängertabelle) zu verwenden, steht Ihnen ein Assistent zur Verfügung, um die Umgebung mit den entsprechenden Zielgruppen-Mappings zu erstellen. Weiterführende Informationen finden Sie unter [Angebotsumgebungen](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

Bei der Erstellung einer anonymen Umgebung mithilfe des Assistenten zur Zuordnungserstellung ist im Tab **[!UICONTROL Allgemein]** das Feld **[!UICONTROL Für anonyme eingehende Interaktionen reservierte Umgebung]** bereits angekreuzt.

Die **[!UICONTROL Zielgruppendimension]** wird vorausgefüllt und verweist standardmäßig auf die Besuchertabelle.

Das Feld **[!UICONTROL Besucherordner]** erscheint. Es enthält bereits den Link zum Ordner **[!UICONTROL Besucher]**. In diesem Feld können Sie auswählen, wo Besucherprofile gespeichert werden sollen.

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>Wenn Sie verschiedene Besuchertypen unterscheiden möchten, beispielsweise im Fall von anonymen Angeboten verschiedener Marken, müssen Sie für jede Marke eine Umgebung und einen zugeordneten **[!UICONTROL Besucher]**-Ordner erstellen.

## Angebotskataloge für anonyme Interaktionen {#offer-catalog-for-anonymous-interactions}

Genau wie die ausgehenden Interaktionen werden die eingehenden Interaktionen in einem Angebotskatalog organisiert, der aus Kategorien und Angeboten besteht.

Wenden Sie zum Erstellen von Kategorien und Platzierungen denselben Prozess an wie für identifizierte Besucher (siehe [Angebotskategorien](../../interaction/using/creating-offer-categories.md) und [Angebotsumgebungen](../../interaction/using/live-design-environments.md#creating-an-offer-environment)).

## Anonyme Besucher {#anonymous-visitors}

Anonyme Besucher können einem Cookie-Identifizierungsprozess unterzogen werden, wenn sie eine Verbindung herstellen. Diese implizite Erkennung basiert auf dem Navigationsverlauf des Besuchers.

In diesem Schritt werden die von den Cookies abgerufenen Daten mit denen in Ihrer Datenbank verglichen. In einigen Fällen werden Besucher erkannt (sie werden dann implizit identifiziert), in anderen Fällen werden sie nicht erkannt (und bleiben daher anonym).

Kreuzen Sie in der Platzierung das Feld **[!UICONTROL Person implizit über den Navigationsverlauf identifizieren]** an, wenn Sie diese Möglichkeit nutzen wollen.

![](assets/identification_anonymous_visitors.png)

## Umgang mit anonymen, nicht identifizierten Besuchern {#processing-unidentified-anonymous-visitors}

Wenn ein Besucher nicht identifiziert werden konnte, können seine Daten in einer bestimmten Platzierung gespeichert werden. Auf diese Weise können ihm spezifische Angebote unterbreitet werden, die speziell für diesen Besuchertyp definierten Typologieregeln entsprechen.

Für nicht identifizierte Kontakte oder solche, die zwar implizit identifiziert werden können, denen Sie aber keine für bekannte Kontakte erstellten Angebote unterbreiten möchten, haben Sie die Möglichkeit, in eine anonyme Umgebung wechseln.

Kreuzen Sie hierfür das Feld **[!UICONTROL Zu einer anonymen Platzierung wechseln, wenn keine Zielperson identifiziert wurde]** an und geben Sie im Feld **[!UICONTROL Zugeordnete anonyme Platzierung]** die den nicht identifizierten Besuchern vorbehaltene Umgebung an.

![](assets/anonymous_to_anonymous_environment.png)

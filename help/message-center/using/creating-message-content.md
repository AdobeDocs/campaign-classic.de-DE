---
title: Nachrichteninhalt erstellen
seo-title: Nachrichteninhalt erstellen
description: Nachrichteninhalt erstellen
seo-description: null
page-status-flag: never-activated
uuid: 4ee013fc-fba2-4120-b796-dd4008000ea9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 1f420652-c9af-4a49-8d5c-a640e960aced
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2c0d4054fbc15a88ea0370269b62c7d647aea033

---


# Nachrichteninhalt erstellen{#creating-message-content}

Die Erstellung des Inhalts einer Transaktionsnachricht erfolgt nach dem gleichen Prinzip wie für einen klassischen Versand in Adobe Campaign. Für einen E-Mail-Versand können Sie zum Beispiel einen Inhalt im HTML- oder im Textformat erstellen und Anhänge hinzufügen oder den Betreff des Versands personalisieren. Mehr Informationen erhalten Sie im Kapitel [E-Mail-Versand](../../delivery/using/about-email-channel.md) des entsprechenden Handbuchs.

>[!CAUTION]
>
>In Nachrichten enthaltene Bilder müssen öffentlich zugänglich sein. Adobe Campaign verfügt über keinen Mechanismus zum Online-Stellen der Bilder für Transaktionsnachrichten.\
>Im Gegensatz zu JSSP oder webApp gibt es `<%=` keine standardmäßige Escape-Funktion.
>
>In diesem Fall müssen Sie alle Daten, die aus dem Ereignis stammen, ordnungsgemäß entschlüsseln. Dieses Escape-Zeichen hängt davon ab, wie dieses Feld verwendet wird. Verwenden Sie beispielsweise innerhalb einer URL encodeURIComponent. Um im HTML-Code angezeigt zu werden, können Sie escapeXMLString verwenden.

Integrieren Sie nach der Erstellung des Inhalts die Ereignisinformationen in den Nachrichten-Textkörper, um die Nachricht zu personalisieren. Verwenden Sie hierzu die zur Verfügung stehenden Personalisierungsfelder.

![](assets/messagecenter_create_content_001.png)

* Alle Personalisierungsfelder stammen aus der Nutzlast.
* Es ist möglich, auf einen oder mehrere Personalisierungsblöcke in einer Transaktionsnachricht zu verweisen. Der Blockinhalt wird während der Veröffentlichung zur Ausführungsinstanz zum Bereitstellungsinhalt hinzugefügt.

Gehen Sie wie folgt vor, um Personalisierungsfelder in einen E-Mail-Nachrichteninhalt einzufügen:

1. Klicken Sie in der Nachrichtenvorlage auf den Tab, der dem E-Mail-Format entspricht (HMTL oder Text).
1. Verfassen Sie den Inhalt der Nachricht.
1. Fügen Sie das Tag im Textkörper mithilfe der **[!UICONTROL Real time events>Event XML]** Menüs ein.

   ![](assets/messagecenter_create_custo_002.png)

1. Ergänzen Sie das Feld unter Einhaltung folgender Syntax: .**Elementname**.@**Attributname**. Beispiel:

   ![](assets/messagecenter_create_custo_003.png)


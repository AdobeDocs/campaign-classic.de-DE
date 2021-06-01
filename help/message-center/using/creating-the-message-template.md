---
product: campaign
title: Transaktionsnachrichten-Vorlagen erstellen
description: Erfahren Sie, wie Sie in Adobe Campaign Classic eine Transaktionsnachrichtenvorlage erstellen und entwerfen.
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: a52bc140-072e-4f81-b6da-f1b38662bce5
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 74%

---

# Erstellen von Transaktionsnachrichten-Vorlagen {#creating-the-message-template}

Um sicherzustellen, dass jedes Ereignis in eine personalisierte Nachricht umgewandelt werden kann, müssen Sie eine Nachrichtenvorlage erstellen, die jedem Ereignistyp entspricht.

>[!IMPORTANT]
>
>Ereignistypen müssen zuvor erstellt werden. Weiterführende Informationen finden Sie unter [Ereignistypen erstellen](../../message-center/using/creating-event-types.md).

Transaktionsnachrichten-Vorlagen enthalten die erforderlichen Informationen zur Personalisierung der Transaktionsnachricht. Sie können Vorlagen auch verwenden, um die Vorschau der Nachricht zu testen und einen Testversand an Testadressen zu senden, bevor Sie an die endgültige Zielgruppe versenden. Weiterführende Informationen dazu finden Sie unter [Vorlagen für Transaktionsnachrichten testen](../../message-center/using/testing-message-templates.md).

## Nachrichtenvorlage erstellen {#creating-message-template}

1. Wechseln Sie zum Knoten **[!UICONTROL Message Center > Transaktionsnachrichten-Vorlagen]** im Adobe Campaign-Navigationsbaum.

1. Klicken Sie mit der rechten Maustaste in die Liste der Vorlagen und wählen Sie **[!UICONTROL Neu]** im Kontextmenü aus oder klicken Sie direkt auf die Schaltfläche **[!UICONTROL Neu]** oberhalb der Liste.

   ![](assets/messagecenter_create_model_001.png)

1. Wählen Sie im Versand-Assistenten die Versandvorlage aus, die dem gewünschten Kommunikationskanal entspricht.

   ![](assets/messagecenter_create_model_002.png)

1. Ändern Sie bei Bedarf den Titel.

1. Wählen Sie den Ereignistyp aus, der der zu sendenden Nachricht entspricht.

   ![](assets/messagecenter_create_model_003.png)

   Ereignistypen müssen zuvor in der Konsole erstellt werden. Weiterführende Informationen finden Sie unter [Ereignistypen erstellen](../../message-center/using/creating-event-types.md).

   >[!IMPORTANT]
   >
   >Ein Ereignistyp kann nicht mit mehreren Vorlagen verknüpft werden.

1. Geben Sie eine Art und eine Beschreibung ein und klicken Sie dann auf **[!UICONTROL Weiter]**, um den Nachrichtentext zu erstellen (siehe [Nachrichteninhalt wird erstellt](#creating-message-content)).

   ![](assets/messagecenter_create_model_004.png)

## Nachrichteninhalt erstellen {#creating-message-content}

Die Erstellung des Inhalts einer Transaktionsnachricht erfolgt nach dem gleichen Prinzip wie für einen klassischen Versand in Adobe Campaign. Für einen E-Mail-Versand können Sie zum Beispiel einen Inhalt im HTML- oder im Textformat erstellen und Anhänge hinzufügen oder den Betreff des Versands personalisieren. Mehr Informationen erhalten Sie im Kapitel [E-Mail-Versand](../../delivery/using/about-email-channel.md) des entsprechenden Handbuchs.

>[!IMPORTANT]
>
>In Nachrichten enthaltene Bilder müssen öffentlich zugänglich sein. Adobe Campaign verfügt über keinen Mechanismus zum Online-Stellen der Bilder für Transaktionsnachrichten.\
>Im Gegensatz zu JSSP oder webApp bietet `<%=` keine standardmäßige Escape-Funktion.
>
>In diesem Fall müssen Sie alle Daten, die aus dem Ereignis stammen, ordnungsgemäß maskieren. Dieses Escape-Sequenz hängt davon ab, wie dieses Feld verwendet wird. Verwenden Sie beispielsweise innerhalb einer URL encodeURIComponent. Für eine Anzeige im HTML-Code, können Sie escapeXMLString verwenden.

Integrieren Sie nach der Erstellung des Inhalts die Ereignisinformationen in den Nachrichten-Textkörper, um die Nachricht zu personalisieren. Verwenden Sie hierzu die zur Verfügung stehenden Personalisierungsfelder.

![](assets/messagecenter_create_content_001.png)

* Alle Personalisierungsfelder stammen aus den Nutzdaten.
* Es ist möglich, in einer Transaktionsnachricht auf einen oder mehrere Gestaltungsbausteine zu verweisen. Der Bausteininhalt wird während der Veröffentlichung in der Ausführungsinstanz zum Versandinhalt hinzugefügt.

Gehen Sie wie folgt vor, um Personalisierungsfelder in einen E-Mail-Nachrichteninhalt einzufügen:

1. Klicken Sie in der Nachrichtenvorlage auf den Tab, der dem E-Mail-Format entspricht (HTML oder Text).

1. Verfassen Sie den Inhalt der Nachricht.

1. Fügen Sie das Tag im Textkörper mithilfe des Menüs **[!UICONTROL Echtzeit-Ereignisse > Ereignis-XML]** ein.

   ![](assets/messagecenter_create_custo_002.png)

1. Ergänzen Sie das Feld unter Einhaltung folgender Syntax: .**Elementname**.@**Attributname**. Beispiel:

   ![](assets/messagecenter_create_custo_003.png)

1. Speichern Sie Ihren Inhalt.

Ihre Nachricht kann jetzt [getestet](../../message-center/using/testing-message-templates.md) sein.

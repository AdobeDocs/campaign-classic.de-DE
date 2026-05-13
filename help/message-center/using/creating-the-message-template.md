---
product: campaign
title: Konzipieren von Transaktionsnachrichtenvorlagen
description: Erfahren Sie, wie Sie in Adobe Campaign Classic eine Transaktionsnachrichtenvorlage erstellen und konzipieren
feature: Transactional Messaging, Message Center, Templates
exl-id: a52bc140-072e-4f81-b6da-f1b38662bce5
TQID: https://experienceleague.adobe.com/lVjiHCruVE2IpwsTkjcNtccmpoSF1aeZ-PFRjcIwf7g
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 513
ht-degree: 83%

---

# Konzipieren von Transaktionsnachrichtenvorlagen {#creating-the-message-template}



Um sicherzustellen, dass alle Ereignisse in eine personalisierte Nachricht umgewandelt werden können, müssen Sie für die einzelnen Ereignistypen jeweils eine Nachrichtenvorlage erstellen.

>[!IMPORTANT]
>
>Zunächst müssen Ereignistypen erstellt werden. Weiterführende Informationen hierzu finden Sie unter [Ereignistypen erstellen](../../message-center/using/creating-event-types.md).

Transaktionsnachrichtenvorlagen enthalten die für die Personalisierung der Transaktionsnachricht erforderlichen Informationen. Sie können Vorlagen auch verwenden, um die Vorschau der Nachricht zu testen und einen Testversand an Testadressen zu senden, bevor Sie sie an die endgültige Zielgruppe versenden. Weiterführende Informationen hierzu finden Sie unter [Testen von Transaktionsnachrichtenvorlagen](../../message-center/using/testing-message-templates.md).

## Nachrichtenvorlage erstellen {#creating-message-template}

1. Wechseln Sie zum Knoten **[!UICONTROL Message Center > Transaktionsnachrichten-Vorlagen]** im Adobe Campaign-Navigationsbaum.

1. Klicken Sie mit der rechten Maustaste in die Liste der Vorlagen und wählen Sie **[!UICONTROL Neu]** im Kontextmenü aus oder klicken Sie direkt auf die Schaltfläche **[!UICONTROL Neu]** oberhalb der Liste.

   ![](assets/messagecenter_create_model_001.png)

1. Wählen Sie im Versand-Assistenten die Versandvorlage aus, die dem gewünschten Kommunikationskanal entspricht.

   ![](assets/messagecenter_create_model_002.png)

1. Ändern Sie bei Bedarf den Titel.

1. Wählen Sie den Ereignistyp aus, der der zu sendenden Nachricht entspricht.

   ![](assets/messagecenter_create_model_003.png)

   Ereignistypen müssen zuvor in der Konsole erstellt werden. Weiterführende Informationen hierzu finden Sie unter [Ereignistypen erstellen](../../message-center/using/creating-event-types.md).

   >[!IMPORTANT]
   >
   >Ein Ereignistyp kann nicht mit mehr als einer Vorlage verknüpft werden.

1. Geben Sie die Art sowie eine Beschreibung der Vorlage an und klicken Sie auf **[!UICONTROL Fortfahren]**, um den Nachrichteninhalt zu erstellen (siehe [Nachrichteninhalt erstellen](#creating-message-content)).

   ![](assets/messagecenter_create_model_004.png)

## Nachrichteninhalt erstellen {#creating-message-content}

Die Definition des Inhalts der Transaktionsnachricht entspricht der für den regulären Versand in Adobe Campaign. So können Sie z. B. für einen E-Mail-Versand Inhalte im HTML- oder Textformat erstellen, Anhänge hinzufügen oder das Versandobjekt personalisieren. Weiterführende Informationen hierzu finden Sie im Kapitel zum [&#x200B; E-Mail-Versand](../../delivery/using/about-email-channel.md).

>[!IMPORTANT]
>
>Die in der Nachricht enthaltenen Bilder müssen öffentlich zugänglich sein. Adobe Campaign bietet keinen Mechanismus zum Hochladen von Bildern für Transaktionsnachrichten.\
>Im Gegensatz zu JSSP oder webApp bietet `<%=` keine standardmäßige Escape-Funktion.
>
>In diesem Fall müssen Sie alle Daten, die aus dem Ereignis stammen, ordnungsgemäß maskieren. Dieses Escape-Sequenz hängt davon ab, wie dieses Feld verwendet wird. Verwenden Sie beispielsweise innerhalb einer URL encodeURIComponent. Für eine Anzeige im HTML-Code, können Sie escapeXMLString verwenden.

Nachdem Sie den Nachrichteninhalt definiert haben, können Sie Ereignisinformationen in den Nachrichtentext integrieren und personalisieren. Ereignisinformationen werden mithilfe von Personalisierungs-Tags in den Textkörper eingefügt.

![](assets/messagecenter_create_content_001.png)

* Alle Personalisierungsfelder stammen aus der Payload.
* Es ist möglich, in einer Transaktionsnachricht auf einen oder mehrere Gestaltungsbausteine zu verweisen. Der Bausteininhalt wird während der Veröffentlichung in der Ausführungsinstanz zum Versandinhalt hinzugefügt.

Gehen Sie wie folgt vor, um Personalisierungsfelder in einen E-Mail-Nachrichteninhalt einzufügen:

1. Klicken Sie in der Nachrichtenvorlage auf den Tab, der dem E-Mail-Format entspricht (HTML oder Text).

1. Verfassen Sie den Inhalt der Nachricht.

1. Fügen Sie das Personalisierungsfeld über das Menü **[!UICONTROL Echtzeit-Ereignisse > Ereignis-XML]** ein.

   ![](assets/messagecenter_create_custo_002.png)

1. Füllen Sie das Tag wie folgt aus: **Elementname**.@**Attributname**, wie unten dargestellt.

   ![](assets/messagecenter_create_custo_003.png)

1. Speichern Sie Ihren Inhalt.

Sie können Ihre Nachricht jetzt [testen](../../message-center/using/testing-message-templates.md).

---
product: campaign
title: Testen von Transaktionsnachrichtenvorlagen
description: Erfahren Sie, wie Sie in Adobe Campaign Classic Testadressen in Transaktionsnachrichten zur Anzeige in einer Vorschau und zum Testen verwalten.
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 417004c9-ed96-4b98-a518-a3aa6123ee7b
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 100%

---

# Testen von Transaktionsnachrichtenvorlagen {#testing-message-templates}

![](../../assets/v7-only.svg)

Führen Sie nach Fertigstellung Ihrer [Nachrichtenvorlage](../../message-center/using/creating-the-message-template.md) die folgenden Schritte aus, um sie in einer Vorschau anzuzeigen und zu testen.

## Testadressen in Transaktionsnachrichten verwalten {#managing-seed-addresses-in-transactional-messages}

Testadressen dienen dazu, eine Nachrichtenvorschau zu erzeugen, Testsendungen auszuführen und die Personalisierung der Nachricht vor dem eigentlichen Versand per E-Mail, SMS oder Mobile Apps zu prüfen. Sie werden für jeden Versand separat erstellt und können nicht in mehreren Sendungen verwendet werden.

Gehen Sie zur Erstellung von Testadressen in einer Transaktionsnachricht wie folgt vor:

1. Gehen Sie in den Tab **[!UICONTROL Testadressen]** der Transaktionsnachrichten-Vorlage.

   ![](assets/messagecenter_create_seedaddr_001.png)

1. Erfassen Sie einen Titel, um die Adresse später bei der Vorschauerstellung auswählen zu können.

   ![](assets/messagecenter_create_seedaddr_002.png)

1. Geben Sie die Testadresse an, je nach Versandkanal eine E-Mail-Adresse oder eine Mobiltelefonnummer.

   ![](assets/messagecenter_create_seedaddr_003.png)

1. Geben Sie eine externe Kennung an. Dieses optionale Feld dient dazu, einen allen Anwendungen Ihrer Webseite gemeinsamen, benutzerdefinierten Schlüssel zu vergeben (eindeutige Kennung, Name + E-Mail etc.), um Ihre Profile zu identifizieren. Wenn dieses Feld auch in der Adobe-Campaign-Datenbank vorhanden ist, haben Sie die Möglichkeit, Ereignisse mit Profilen der Datenbank abzustimmen.

   ![](assets/messagecenter_create_seedaddr_003bis.png)

1. Fügen Sie Testdaten ein (siehe [Personalisierungsdaten](#personalization-data)).

   ![](assets/messagecenter_create_custo_001.png)

   <!--## Creating several seed addresses {#creating-several-seed-addresses}-->
1. Klicken Sie auf den Link **[!UICONTROL Testadressen ergänzen]** und anschließend auf die Schaltfläche **[!UICONTROL Hinzufügen]**.

   ![](assets/messagecenter_create_seedaddr_004.png)

   <!--1. Follow the configuration steps for a seed address detailed in the [Creating a seed address](#creating-a-seed-address) section.-->
1. Wiederholen Sie diesen Vorgang, um beliebig viele weitere Testadressen zu erstellen.

   ![](assets/messagecenter_create_seedaddr_008.png)

Sobald die Adressen erstellt wurden, können Sie eine Vorschau der Nachricht und ihrer Personalisierung erzeugen. Siehe [Transaktionsnachrichten-Vorschau](#transactional-message-preview).

## Personalisierungsdaten {#personalization-data}

Sie können Daten aus der Nachrichtenvorlage verwenden, um die Personalisierung von Transaktionsnachrichten zu testen. Diese Funktion wird verwendet, um eine Vorschau zu erstellen oder einen Testversand durchzuführen. Ebenfalls können Sie anzeigen, wie die Nachricht bei verschiedenen Internet-Anbietern dargestellt wird. Weiterführende Informationen dazu finden Sie im Abschnitt [Inbox Rendering](../../delivery/using/inbox-rendering.md).

Diese Daten dienen nur dazu, die Nachrichten vor dem eigentlichen Versand zu testen, und entsprechen nicht den tatsächlich verarbeiteten Daten. Ihre XML-Struktur muss jedoch identisch mit der des in der Ausführungsinstanz gespeicherten Ereignisses sein, wie im Folgenden gezeigt:

![](assets/messagecenter_create_custo_006.png)

Diese Informationen erlauben die Personalisierung des Nachrichteninhalts mithilfe von Personalisierungs-Tags. (Näheres hierzu siehe [Nachrichteninhalt erstellen](../../message-center/using/creating-the-message-template.md#creating-message-content).)

1. Wählen Sie die Transaktionsnachrichtenvorlage aus.

1. Klicken Sie in der Nachrichtenvorlage auf den Tab **[!UICONTROL Testadressen]**.

1. Geben Sie im Inhalt des Ereignisses die Testinformationen im XML-Format ein.

   ![](assets/messagecenter_create_custo_001.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Transaktionsnachrichten-Vorschau {#transactional-message-preview}

Nach der Erstellung einer oder mehrerer Testadressen sowie des Nachrichteninhalts können Sie eine Vorschau Ihrer Nachricht erzeugen und ihre Personalisierung überprüfen:

1. Klicken Sie in der Nachrichtenvorlage auf den Tab **[!UICONTROL Vorschau]**.

   ![](assets/messagecenter_preview_001.png)

1. Klicken Sie in der Dropdown-Liste auf **[!UICONTROL Testadresse...]**.

   ![](assets/messagecenter_preview_002.png)

1. Wählen Sie eine der vorab erstellten Testadressen aus, um die personalisierte Nachrichtenvorschau zu erzeugen.

   ![](assets/messagecenter_create_seedaddr_009.png)

Mit Testadressen können Sie außerdem anzeigen, wie die Nachricht bei verschiedenen Internet-Anbietern dargestellt wird. Weiterführende Informationen dazu finden Sie im Abschnitt [Inbox Rendering](../../delivery/using/inbox-rendering.md).

## Durchführen eines Testversands {#sending-a-proof}

Mithilfe von Testadressen haben Sie die Möglichkeit, vor dem eigentlichen Versand einen Testversand durchzuführen.

Das Senden eines Testversands erfolgt nach demselben Verfahren wie bei einem [Standardversand](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof). Bei Transaktionsnachrichten müssen Sie jedoch zuvor die folgenden Schritte durchführen:

* Eine oder mehrere [Testadressen](#managing-seed-addresses-in-transactional-messages) mit [Personalisierungsdaten](#personalization-data) erstellen.
* [Nachrichteninhalt erstellen](../../message-center/using/creating-the-message-template.md#creating-message-content).

Gehen Sie zur Durchführung des Testversands wie folgt vor:

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Testversand]** im Versandfenster.
1. Analysieren Sie den Versand.
1. Korrigieren Sie eventuelle Fehler und bestätigen Sie den Versand.

   ![](assets/messagecenter_send_proof_001.png)

1. Stellen Sie sicher, dass die Nachricht an die Testadresse geschickt wurde und der Inhalt Ihren Konfigurationen entspricht.

   ![](assets/messagecenter_send_proof_002.png)

Die Testsendungen können im Tab **[!UICONTROL Verfolgung]** jeder Vorlage eingesehen werden. Weiterführende Informationen hierzu finden Sie unter [Testversand durchführen](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

![](assets/messagecenter_send_proof_003.png)

Ihre Nachrichtenvorlage ist jetzt zur [Veröffentlichung](../../message-center/using/publishing-message-templates.md) bereit.
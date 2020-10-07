---
title: Testadressen in Transaktionsnachrichten verwalten
seo-title: Testadressen in Transaktionsnachrichten verwalten
description: Testadressen in Transaktionsnachrichten verwalten
seo-description: null
page-status-flag: never-activated
uuid: 51c4e79d-53bb-4d46-9c7d-e90066f5317d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 12e7043e-e8b5-48a9-8a2f-99e2e6040c3c
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 100%

---


# Testadressen in Transaktionsnachrichten verwalten{#managing-seed-addresses-in-transactional-messages}

Testadressen dienen dazu, eine Nachrichtenvorschau zu erzeugen, Testsendungen auszuführen und die Personalisierung der Nachricht vor dem eigentlichen Versand per E-Mail, SMS oder Mobile Apps zu prüfen. Sie werden für jeden Versand separat erstellt und können nicht in mehreren Sendungen verwendet werden.

## Testadressen erstellen {#creating-a-seed-address}

1. Gehen Sie in den Tab **[!UICONTROL Testadressen]** der Transaktionsnachrichten-Vorlage.

   ![](assets/messagecenter_create_seedaddr_001.png)

1. Erfassen Sie einen Titel, um die Adresse später bei der Vorschauerstellung auswählen zu können.

   ![](assets/messagecenter_create_seedaddr_002.png)

1. Geben Sie die Testadresse an, je nach Versandkanal eine E-Mail-Adresse oder eine Mobiltelefonnummer.

   ![](assets/messagecenter_create_seedaddr_003.png)

1. Geben Sie eine externe Kennung an. Dieses optionale Feld dient dazu, einen allen Anwendungen Ihrer Webseite gemeinsamen, benutzerdefinierten Schlüssel zu vergeben (eindeutige Kennung, Name + E-Mail etc.), um Ihre Profile zu identifizieren. Wenn dieses Feld auch in der Adobe-Campaign-Datenbank vorhanden ist, haben Sie die Möglichkeit, Ereignisse mit Profilen der Datenbank abzustimmen.

   ![](assets/messagecenter_create_seedaddr_003bis.png)

1. Fügen Sie Testdaten ein (siehe [Personalisierungsdaten](../../message-center/using/personalization-data.md)).

   ![](assets/messagecenter_create_custo_001.png)

## Mehrere Testadressen erstellen {#creating-several-seed-addresses}

1. Klicken Sie auf den Link **[!UICONTROL Testadressen ergänzen]**, dann auf die Schaltfläche **[!UICONTROL Hinzufügen]**.

   ![](assets/messagecenter_create_seedaddr_004.png)

1. Folgen Sie den Konfigurationsetappen einer Testadresse im Abschnitt [Testadressen erstellen](#creating-a-seed-address).
1. Wiederholen Sie diesen Vorgang, um beliebig viele weitere Testadressen zu erstellen.

   ![](assets/messagecenter_create_seedaddr_008.png)

Sobald die Adressen erstellt wurden, können Sie eine Vorschau der Nachricht und ihrer Personalisierung erzeugen. Siehe [Transaktionsnachrichten-Vorschau](../../message-center/using/transactional-message-preview.md).

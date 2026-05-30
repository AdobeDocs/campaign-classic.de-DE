---
product: campaign
title: Erstellen von SMS mit Campaign
description: Erfahren Sie, wie Sie SMS mit Campaign erstellen.
feature: SMS
role: User
hide: true
exl-id: 94aa4628-d973-433d-b963-b078e2d6672b
TQID: https://experienceleague.adobe.com/ENt9cwc7OjXcMr5tbkg2f3BxpPBNtVytVTw70NQZPyI
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 473
ht-degree: 75%

---

# Erstellen eines SMS-Versands {#creating-a-sms-delivery}

## Versandkanal auswählen {#selecting-the-delivery-channel}

Gehen Sie wie folgt vor, um einen neuen SMS-Versand zu erstellen:

>[!NOTE]
>
>Allgemeine Methoden zur Versanderstellung finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=de){target="_blank"}.

1. Erstellen Sie einen neuen Versand, beispielsweise im Versand-Dashboard.
1. Wählen Sie die zuvor erstellte Versandvorlage **Mobiltelefon-Versand (SMPP)** aus. Lesen Sie diesbezüglich auch den Abschnitt [Versandvorlage ändern](sms-set-up.md#changing-the-delivery-template).

   ![](assets/s_user_mobile_wizard.png)

1. Geben Sie einen Titel, einen Code und eine Beschreibung für Ihren Versand ein. Weitere Informationen finden Sie in diesem Abschnitt der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=de#create-the-delivery){target="_blank"}.
1. Klicken Sie auf **[!UICONTROL Fortfahren]**, um die Eingaben zu bestätigen und in das Fenster zur Nachrichtenkonfiguration zu gelangen.

## SMS-Inhalt erstellen {#defining-the-sms-content}

Um den Inhalt der SMS zu erstellen, gehen Sie wie folgt vor:

1. Geben Sie den Nachrichteninhalt im Bereich **[!UICONTROL Textinhalt]** des Assistenten ein. Mit den Schaltflächen der Symbolleiste können Sie Inhalte importieren, speichern oder suchen. Die letzte Schaltfläche in der Symbolleiste dient der Einfügung von Personalisierungsfeldern.

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   Die Verwendung von Personalisierungsfeldern wird im Abschnitt [Über die Personalisierung](about-personalization.md) beschrieben.

1. Durch Auswahl der Registerkarte **[!UICONTROL Vorschau]** unten auf der Seite können Sie das Rendering der personalisierten Nachricht prüfen. Um die Vorschau zu starten, wählen Sie eine Empfängerin bzw. einen Empfänger mithilfe der Schaltfläche **[!UICONTROL Personalisierung testen]** in der Symbolleiste. Wählen Sie eine Empfängerin bzw. einen Empfänger aus der Zielgruppe oder ein anderes Profil aus.

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   Sie können die SMS-Nachricht genehmigen. Sie können den Inhalt der SMS auch auf dem Mobiltelefonbildschirm anzeigen, der rechts neben dem Inhaltseditor angezeigt wird. Klicken Sie auf den Bildschirm und verwenden Sie die Maus, um durch den Inhalt zu scrollen.

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. Der Link **[!UICONTROL Geladene Daten]** ermöglicht die auszugsweise Anzeige des Empfängerprofils.

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >SMS-Nachrichten sind auf eine Länge von 160 Zeichen beschränkt, wenn die Code-Seite Latin-1 (ISO-8859-1) verwendet wird. Wenn die Nachricht in Unicode geschrieben ist, darf sie 70 Zeichen nicht überschreiten. Bestimmte Sonderzeichen können sich auf die Nachrichtenlänge auswirken. Weitere Informationen zur Nachrichtenlänge finden Sie im Abschnitt [Transliteration von SMS-Zeichen](#about-character-transliteration).
   >
   >Wenn Personalisierungsfelder oder bedingte Inhaltsfelder vorhanden sind, variiert die Größe der Nachricht von einem Empfänger zum anderen. Die Länge der Nachricht muss nach der Personalisierung ausgewertet werden.
   >
   >Während der Analysephase wird die Nachrichtenlänge geprüft und im Falle eines Überschreitens ein Warnhinweis erzeugt.

1. Wenn Sie den NetSize-Connector oder einen SMPP-Connector verwenden, besteht die Möglichkeit, den Absendernamen des Versands zu personalisieren. Weitere Informationen hierzu finden Sie im Abschnitt [Erweiterte Parameter](#advanced-parameters).

## Zielpopulation bestimmen {#selecting-the-target-population}

Die detaillierten Schritte zur Auswahl der Zielpopulation eines Versands finden Sie in [diesem Abschnitt](steps-defining-the-target-population.md).

Weitere Informationen zur Verwendung von Personalisierungsfeldern finden Sie in [diesem Abschnitt](about-personalization.md).

Weitere Informationen zur Verwendung von Testadressen finden Sie auf [dieser Seite](about-seed-addresses.md).

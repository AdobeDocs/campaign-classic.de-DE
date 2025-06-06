---
product: campaign
title: Erstellen von SMS mit Campaign
description: Erfahren Sie, wie Sie SMS mit Campaign erstellen.
feature: SMS
role: User
hide: true
hidefromtoc: true
exl-id: 94aa4628-d973-433d-b963-b078e2d6672b
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 100%

---

# Erstellen eines SMS-Versands {#creating-a-sms-delivery}

## Versandkanal auswählen {#selecting-the-delivery-channel}

Gehen Sie wie folgt vor, um einen neuen SMS-Versand zu erstellen:

>[!NOTE]
>
>Allgemeine Methoden zur Versanderstellung finden Sie in [diesem Abschnitt](steps-about-delivery-creation-steps.md).

1. Erstellen Sie einen neuen Versand beispielsweise im Versand-Dashboard.
1. Wählen Sie die zuvor erstellte Versandvorlage **Mobiltelefon-Versand (SMPP)** aus. Lesen Sie diesbezüglich auch den Abschnitt [Versandvorlage ändern](sms-set-up.md#changing-the-delivery-template).

   ![](assets/s_user_mobile_wizard.png)

1. Geben Sie für Ihren Versand einen Titel, einen Code und eine Beschreibung ein. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](steps-create-and-identify-the-delivery.md#identifying-the-delivery).
1. Klicken Sie auf **[!UICONTROL Fortfahren]**, um die Eingaben zu bestätigen und in das Fenster der Nachrichtenkonfiguration zu gelangen.

## SMS-Inhalt erstellen {#defining-the-sms-content}

Um den Inhalt der SMS zu erstellen, gehen Sie wie folgt vor:

1. Geben Sie den Nachrichteninhalt im Bereich **[!UICONTROL Textinhalt]** des Assistenten ein. Mit den Schaltflächen der Symbolleiste können Sie Inhalte importieren, speichern oder suchen. Die letzte Schaltfläche in der Symbolleiste dient der Einfügung von Personalisierungsfeldern.

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   Die Verwendung von Personalisierungsfeldern wird im Abschnitt [Über die Personalisierung](about-personalization.md) beschrieben.

1. Durch Auswahl der Registerkarte **[!UICONTROL Vorschau]** unten auf der Seite können Sie das Rendering der personalisierten Nachricht prüfen. Um die Vorschau zu starten, wählen Sie eine Empfängerin bzw. einen Empfänger mithilfe der Schaltfläche **[!UICONTROL Personalisierung testen]** in der Symbolleiste. Wählen Sie eine Empfängerin bzw. einen Empfänger aus der Zielgruppe oder ein anderes Profil aus.

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   Sie können nun den personalisierten Nachrichteninhalt sowie die Anzeige der SMS auf dem rechts im Bild angezeigten Mobiltelefondisplay prüfen. Klicken Sie auf das Display, um die Nachricht mit der Maus zu scrollen.

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. Der Link **[!UICONTROL Geladene Daten]** ermöglicht die auszugsweise Anzeige des Empfängerprofils.

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >Bei Verwendung der Codepage „Latin-1 (ISO-8859-1)“ ist die Länge von SMS auf 160, bei Unicode auf 70 Zeichen begrenzt. Gewisse Sonderzeichen können die Länge der Nachricht beeinflussen. Weitere Informationen zur Nachrichtenlänge finden Sie im Abschnitt [Transliteration von SMS-Zeichen](#about-character-transliteration).
   >
   >Wenn die Nachricht Personalisierungsfelder oder bedingte Inhalte enthält, kann die Länge von Empfänger zu Empfänger variieren. Daher sollte die Länge jeweils nach erfolgter Personalisierung ausgewertet werden.
   >
   >Während der Analysephase wird die Nachrichtenlänge geprüft und im Falle eines Überschreitens ein Warnhinweis erzeugt.

1. Wenn Sie den NetSize-Connector oder einen SMPP-Connector verwenden, besteht die Möglichkeit, den Absendernamen des Versands zu personalisieren. Weitere Informationen hierzu finden Sie im Abschnitt [Erweiterte Parameter](#advanced-parameters).

## Zielpopulation bestimmen {#selecting-the-target-population}

Die detaillierten Schritte zur Auswahl der Zielpopulation eines Versands finden Sie in [diesem Abschnitt](steps-defining-the-target-population.md).

Weitere Informationen zur Verwendung von Personalisierungsfeldern finden Sie in [diesem Abschnitt](about-personalization.md).

Weitere Informationen zur Verwendung von Testadressen finden Sie auf [dieser Seite](about-seed-addresses.md).

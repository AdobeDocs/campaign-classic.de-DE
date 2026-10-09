---
product: campaign
title: Kanalübergreifender Versand
description: Weitere Informationen zu kanalübergreifenden Sendungen.
feature: Workflows, Channels Activity
hide: true
exl-id: 3bb468e2-7bcf-456f-8d8f-1c4e608e2b25
TQID: 'https://experienceleague.adobe.com/BXn5nJkGD-NL8Rh5kYtltXfGJiWlYQqbyzcdZ1SleJA'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: bce277d1-7efa-48d8-9a1b-b588bb45ba1c
    internal-label: Channels Activity
source-git-commit: 3e213ecc670d5a3cb8299c092ccbb5303858327d
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 100%
---
# Kanalübergreifender Versand{#cross-channel-deliveries}



Auf kanalübergreifende Sendungen kann auf der Registerkarte **[!UICONTROL Sendungen]** von Kampagnen-Workflows zugegriffen werden.

Die verfügbaren Kanäle sind:

* [E-Mail](../../delivery/using/about-email-channel.md)
* [Briefpost](../../delivery/using/about-direct-mail-channel.md)
* [Mobile](../../delivery/using/sms-channel.md)
* [X (früher bekannt als Twitter)](../../social/using/about-social-marketing.md)
* [iOS](../../delivery/using/create-notifications-ios.md)
* [Android](../../delivery/using/create-notifications-android.md)

Wählen Sie die Vorlage aus, auf der der Versand basieren soll, und definieren Sie ihre Inhalte.

Die Zielgruppe des Versands kann mithilfe der verschiedenen dedizierten Zielgruppenbestimmungs-Aktivitäten vorab im Workflow definiert werden.

Hier erstellen wir beispielsweise einen Workflow für den Versand einer E-Mail oder einer SMS an Abonnenten einer Push-Benachrichtigung sowie für eine Push-Benachrichtigung eine Woche später. Gehen Sie dazu wie folgt vor:

1. Erstellen Sie eine Kampagne.
1. Fügen Sie in Ihrer Kampagne dem Workflow im Tab **[!UICONTROL Zielgruppenbestimmungen und Workflows]** eine **[!UICONTROL Abfrage]** hinzu.
1. Konfigurieren Sie Ihre Abfrage. In unserem Beispiel wählen wir als Zieldimension die Empfängerinnen und Empfänger aus, die Push-Benachrichtigungen abonniert haben.

   >[!NOTE]
   >
   >Verwenden Sie für Push-Benachrichtigungen die Zieldimension **Abonnierte Anwendungen**.

   ![](assets/cross_channel_delivery_1.png)

1. Fügen Sie Ihrer Abfrage die Filterbedingungen hinzu. In diesem Fall wählen wir Empfängerinnen und Empfänger aus, die über eine Mobiltelefonnummer oder E-Mail-Adresse verfügen.

   ![](assets/cross_channel_delivery_2.png)

1. Fügen Sie Ihrem Workflow eine **[!UICONTROL Aufspaltung]** hinzu, um Empfänger in Besitzer einer Mobiltelefonnummer und in Besitzer einer E-Mail-Adresse zu unterteilen.
1. Wählen Sie im Tab **[!UICONTROL Versand]** für jeden Zieldatensatz einen Versand.

   Erstellen Sie Ihren Versand auf dieselbe Weise wie mit dem klassischen Versandassistenten, indem Sie die Versandaktivität in Ihrem Workflow per Doppelklick auswählen. Weiterführende Informationen hierzu finden Sie auf [dieser Seite](../../delivery/using/about-email-channel.md).

   ![](assets/cross_channel_delivery_3.png)

1. Fügen Sie eine **[!UICONTROL Warten]**-Aktivität hinzu und konfigurieren Sie sie, damit die Empfänger nicht zu viele Sendungen gleichzeitig erhalten.
1. Fügen Sie eine **[!UICONTROL Aufspaltung]** hinzu, um Abonnenten in Anwender von iOS- und Android-Apps zu unterteilen.

   Wählen Sie für jedes Betriebssystem einen Dienst aus. Weiterführende Informationen zur Abonnementerstellung finden Sie auf dieser [Seite](../../delivery/using/configuring-the-mobile-application.md).

   ![](assets/cross_channel_delivery_4.png)

1. Wählen Sie für jedes Betriebssystem einen Mobile-App-Versand aus und konfigurieren Sie ihn.

   ![](assets/cross_channel_delivery_5.png)

---
product: campaign
title: Erste Schritte mit dem App-Kanal
description: Erste Schritte mit dem Mobile-App-Kanal in Adobe Campaign
feature: Push
role: User
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
TQID: 'https://experienceleague.adobe.com/hNwtWC-TnFXsSv7CqqzKqr29sk67h2rwMBOTcBTToDs'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
  - id: a4657621-810c-498b-8a27-7ced9c176dda
    internal-label: Push notifications
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
source-git-commit: 0fdce84d7da1ff42a406ace8f1a180f6a426646a
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 91%
---
# Erste Schritte mit dem App-Kanal{#about-mobile-app-channel}

Richten Sie mit Adobe Campaign den Versand von Push-Benachrichtigungen ein, um personalisierte Nachrichten an Benutzende Ihrer App zu senden.

>[!NOTE]
>
>Im Zuge der Umstellung von Campaign v7 auf v8 wurde die Campaign Classic-Dokumentation optimiert und neu organisiert. Allgemeine Funktionen sind jetzt nur noch in der Dokumentation zu Campaign v8 verfügbar. Weitere Informationen zum Push-Benachrichtigungskanal finden Sie in der Dokumentation zu [ v8 ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/push/push){target=_blank}.
>
>[![Bild](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/push/push){target="_blank"}

Die folgenden Informationen gelten spezifisch für Campaign Classic.

+++ **Paket-Installation**

![](assets/do-not-localize/how-to-video.png) [Video zur Installation des Mobile-App-Package ](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html?lang=de#sending-messages)

Wenn Sie Campaign als Hybrid- oder gehostete Bereitstellung nutzen, wenden Sie sich an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html), um Zugriff auf den Kanal für Push-Benachrichtigungen in Campaign zu erhalten.

Wenn Sie Campaign als On-Premise-Bereitstellung nutzen, müssen Sie ein integriertes Paket installieren.

>[!CAUTION]
>
>Weitere Informationen zu integrierten Campaign-Paketen, Best Practices und Empfehlungen finden Sie auf [dieser Seite](../../installation/using/installing-campaign-standard-packages.md).

Die Installationsschritte sind:

1. Greifen Sie über **[!UICONTROL Werkzeuge > Erweitert > Package-Import]** in der Adobe Campaign-Client-Konsole auf den Package-Import-Assistenten zu.

   ![](assets/package_ios.png)

1. Wählen Sie **[!UICONTROL Standard-Package installieren]** aus.

1. Markieren Sie in der angezeigten Liste **[!UICONTROL Mobile-App-Kanal (Mobile App Channel)]**.

   ![](assets/package_ios_2.png)

1. Klicken Sie auf **[!UICONTROL Weiter]** und dann auf **[!UICONTROL Starten]**, um die Package-Installation zu starten.

   Sobald die Packages installiert sind, wird in der Fortschrittsleiste **100 %** angezeigt. Folgende Meldung wird in den Installationsprotokollen angezeigt: **[!UICONTROL Die Installation der Packages wurde erfolgreich beendet]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Schließen]** Sie das Installationsfenster.

Nach Abschluss dieses Schritts können Sie Ihre Android- und iOS-Apps konfigurieren. Weitere Informationen finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=de){target="_blank"}.

+++

+++ **Fehlerbehebung**

Wenn Ihr Mobilgerät mit einem WLAN verbunden ist und Sie keine Benachrichtigungen erhalten, stellen Sie sicher, dass die FCM/APNS-Ports nicht von Ihrer Firewall gesperrt werden.

**Android**: Das Mobilgerät stellt eine Verbindung zu den FCM-Servern an den Ports 5228 bis 5230 her. Daher müssen Sie Ihre Firewall so konfigurieren, dass sie die Verbindung mit FCM autorisiert. Die zu öffnenden Ports sind 5228 (am häufigsten verwendet), 5229 und 5230.

**iOS**:

HTTP/2-Connector: Erlauben Sie die Kommunikation zu und von den folgenden Servern:

* api.push.apple.com: Port 443
* api.development.push.apple.com: Port 443

>[!NOTE]
>
>Weitere Informationen zu den beiden Connectoren finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=de){target="_blank"}.

+++

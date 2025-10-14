---
product: campaign
title: Erste Schritte mit dem Mobile-App-Kanal
description: Erste Schritte mit dem Mobile-App-Kanal in Adobe Campaign
feature: Push
role: User
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 39%

---

# Erste Schritte mit dem Mobile-App-Kanal{#about-mobile-app-channel}

Erstellen Sie mit Adobe Campaign einen Push-Benachrichtigungs-Versand, um personalisierte Nachrichten an Benutzende Ihrer Mobile App zu senden.

Mit Push-Benachrichtigungen können Sie Benutzerinnen und Benutzer in iOS und Android in Echtzeit ansprechen. Unabhängig davon, ob Sie Aktualisierungen, Ankündigungen oder Promotions senden, können Sie Inhalt, Timing und Zielgruppenbestimmung steuern. In der Dokumentation zu [Adobe Campaign v8 erfahren Sie, wie Sie den Push-Kanal einrichten und verwenden, Abonnements verwalten, mit APNs und FCM integrieren und Nachrichten ](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/emails/email){target=_blank}.

Im Zuge der Umstellung von Campaign v7 auf v8 wurde der Campaign Classic-Dokumentationssatz optimiert und neu organisiert. Allgemeine Funktionen sind jetzt ausschließlich im Dokumentationssatz zu Campaign v8 verfügbar.

>[!BEGINTABS]

>[!TAB Dokumentation zum Push-Kanal]

Weitere Informationen zum Push-Benachrichtigungskanal finden Sie in der [ zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html){target=_blank}.

[![Bild](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html){target=_blank}


>[!TAB Erstellung eines Push-Versands]

Die wichtigsten Schritte zur Erstellung eines Push-Versands **Sie in der Dokumentation zu Campaign v8**:

* [Push-Benachrichtigung erstellen](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html#push-create){target="_blank"} Erfahren Sie mehr über die verschiedenen Schritte, die zum Erstellen eines Push-Versands erforderlich sind.
* [Push-Benachrichtigung senden und überwachen](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html#push-test){target="_blank"} Erfahren Sie, wie Sie Ihre Sendungen validieren, senden und verfolgen können.
* [Entwerfen eines Rich-Push-Versands für Android](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/rich-push/rich-push-android.html){target="_blank"}: Erfahren Sie, wie Sie Rich-Push-Benachrichtigungen für Android-Geräte erstellen und konfigurieren.
* [Entwerfen eines Rich-Push-Versands für iOS](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/rich-push/rich-push-ios.html){target="_blank"}: Erfahren Sie, wie Sie Rich-Push-Benachrichtigungen für iOS-Geräte in Adobe Campaign v8 entwerfen und konfigurieren.


>[!TAB Push-Parameter]

Auf diesen Seiten erfahren Sie mehr über Push-Parameter **in der Dokumentation zu Campaign v8**:

* [Konfigurationsvoraussetzungen](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html#before-starting){target="_blank"}: Erfahren Sie, wie Sie Berechtigungen einrichten und Ihre App konfigurieren.
* [Launch-Eigenschaft konfigurieren](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html#launch-property){target="_blank"}: Erfahren Sie, wie Sie eine mobile Tag-Eigenschaft in der Adobe Experience Platform-Datenerfassung einrichten, um Push-Benachrichtigungen zu aktivieren.
* [Konfigurieren von Push-Services für mobile Services](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html#push-service){target="_blank"}: Richten Sie iOS- und Android-Push-Services in Adobe ein, um gezielte Push-Benachrichtigungen für Benutzer Ihrer mobilen App zu aktivieren.
* [Konfigurieren Sie die Erweiterung in Ihrer Mobile-Eigenschaft](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html#configure-extension){target="_blank"}: Integrieren Sie die Campaign-Erweiterung in Ihre Mobile-Eigenschaft, um Push-Benachrichtigungen zu aktivieren und Benutzerinteraktionen effektiv zu verwalten.

>[!ENDTABS]


Die folgenden Informationen sind spezifisch für Campaign Classic.

+++ **Paketinstallation**

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

Sobald dieser Schritt abgeschlossen ist, können Sie Ihre Android- und iOS-Apps konfigurieren. Weitere Informationen finden Sie in der [ zu Campaign v8 ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html){target="_blank"}.

+++

+++ **Fehlerbehebung**

Wenn Ihr Mobilgerät mit einem WLAN verbunden ist und Sie keine Benachrichtigungen erhalten, stellen Sie sicher, dass die FCM/APNS-Ports nicht von Ihrer Firewall gesperrt werden.

**Android**: Das Mobilgerät verbindet sich mit den FCM-Servern über die Ports 5228 bis 5230. Ihre Firewall muss also dahingehend konfiguriert werden, dass sie die Verbindung mit FCM zulässt. Folgende Ports sind zu öffnen: 5228 (am häufigsten verwendet), 5229 und 5230.

**iOS**:

HTTP/2-Connector: Erlauben Sie die Kommunikation zu und von den folgenden Servern:

* api.push.apple.com: Port 443
* api.development.push.apple.com: Port 443

>[!NOTE]
>
>Weitere Informationen zu den beiden Connectoren finden Sie in der Dokumentation zu Campaign v8 [](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html){target="_blank"}.

+++

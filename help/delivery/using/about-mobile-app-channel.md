---
product: campaign
title: Erste Schritte mit dem App-Kanal
description: Erste Schritte mit dem Mobile-App-Kanal in Adobe Campaign
feature: Push
role: User
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: ht
source-wordcount: '590'
ht-degree: 100%

---

# Erste Schritte mit dem App-Kanal{#about-mobile-app-channel}

Richten Sie mit Adobe Campaign den Versand von Push-Benachrichtigungen ein, um personalisierte Nachrichten an Benutzende Ihrer App zu senden.

Mit Push-Benachrichtigungen können Sie Benutzerinnen und Benutzer auf iOS und Android in Echtzeit ansprechen. Unabhängig davon, ob Sie Aktualisierungen, Ankündigungen oder Promotions senden, können Sie Inhalt, Timing und Zielgruppenbestimmung steuern. In der [Dokumentation zu Adobe Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/emails/email){target=_blank} erfahren Sie, wie Sie den Push-Kanal einrichten und verwenden, Abonnements verwalten, mit APNs und FCM integrieren und Nachrichten personalisieren.

Im Zuge der Umstellung von Campaign v7 auf v8 wurde der Campaign Classic-Dokumentationssatz optimiert und neu organisiert. Allgemeine Funktionen sind jetzt nur noch in der Dokumentation zu Campaign v8 verfügbar.

>[!BEGINTABS]

>[!TAB Dokumentation zum Push-Kanal]

Weitere Informationen zum Push-Kanal finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=de){target=_blank}.

[![Bild](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=de){target=_blank}


>[!TAB Erstellen eines Push-Versands]

Die wichtigsten Schritte zur Erstellung eines Push-Versands finden Sie in der **Dokumentation zu Campaign v8**:

* [Erstellen einer Push-Benachrichtigung](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=de#push-create){target="_blank"}: Erfahren Sie mehr über die verschiedenen Schritte, die zum Erstellen eines Push-Versands erforderlich sind.
* [Senden und Überwachen einer Push-Benachrichtigung](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=de#push-test){target="_blank"}: Erfahren Sie, wie Sie Ihre Sendungen validieren, senden und nachverfolgen können.
* [Entwerfen eines Rich-Push-Versands für Android](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/rich-push/rich-push-android.html?lang=de){target="_blank"}: Erfahren Sie, wie Sie Rich-Push-Benachrichtigungen für Android-Geräte erstellen und konfigurieren.
* [Entwerfen eines Rich-Push-Versands für iOS](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/rich-push/rich-push-ios.html?lang=de){target="_blank"}: Erfahren Sie, wie Sie Rich-Push-Benachrichtigungen für iOS-Geräte in Adobe Campaign v8 entwerfen und konfigurieren.


>[!TAB Push-Parameter]

Auf den folgenden Seiten in der **Dokumentation zu Campaign v8** erfahren Sie mehr über Push-Parameter:

* [Konfigurationsvoraussetzungen](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=de#before-starting){target="_blank"}: Erfahren Sie, wie Sie Berechtigungen einrichten und Ihre App konfigurieren.
* [Konfigurieren der Launch-Eigenschaft](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=de#launch-property){target="_blank"}: Erfahren Sie, wie Sie eine Tag-Eigenschaft „Mobile“ in der Datenerfassung von Adobe Experience Platform einrichten, um Push-Benachrichtigungen zu aktivieren.
* [Konfigurieren von Push-Services für mobile Services](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=de#push-service){target="_blank"}: Richten Sie iOS- und Android-Push-Services in Adobe ein, um zielgerichtete Push-Benachrichtigungen für Benutzende Ihrer App zu aktivieren.
* [Konfigurieren der Erweiterung in Ihrer Mobile-Eigenschaft](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=de#configure-extension){target="_blank"}: Integrieren Sie die Campaign-Erweiterung in Ihre Mobile-Eigenschaft, um Push-Benachrichtigungen zu aktivieren und Benutzerinteraktionen effektiv zu verwalten.

>[!ENDTABS]


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

**Android**: Das Mobilgerät verbindet sich mit den FCM-Servern über die Ports 5228 bis 5230. Ihre Firewall muss also dahingehend konfiguriert werden, dass sie die Verbindung mit FCM zulässt. Folgende Ports sind zu öffnen: 5228 (am häufigsten verwendet), 5229 und 5230.

**iOS**:

HTTP/2-Connector: Erlauben Sie die Kommunikation zu und von den folgenden Servern:

* api.push.apple.com: Port 443
* api.development.push.apple.com: Port 443

>[!NOTE]
>
>Weitere Informationen zu den beiden Connectoren finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=de){target="_blank"}.

+++

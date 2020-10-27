---
title: 'Konfiguration der Mobile App in Adobe Campaign '
description: Erfahren Sie, wie Sie mit der Konfiguration der mobilen Anwendung Beginn machen
page-status-flag: never-activated
uuid: aff1a4a0-34e7-4ce0-9eb3-30a8de1380f2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 7b5a1ad6-da5a-4cbd-be51-984c07c8d0b3
translation-type: tm+mt
source-git-commit: fd75f7f75e8e77d7228233ea311dd922d100417c
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 53%

---


# Erste Schritte mit der App-Konfiguration

In diesem Abschnitt finden Sie ein Konfigurationsbeispiel, das auf einer Firma basiert, die Online-Urlaubspakete verkauft. Seine mobile Anwendung (Neotrips) steht seinen Kunden in zwei Versionen zur Verfügung: Neotrips für Android und Neotrips für iOS.

Um Push-Benachrichtigungen in Adobe Campaign zu senden, müssen Sie:

* Erstellen Sie für die Neotrips-App einen Informationsdienst vom Typ **[!UICONTROL Mobile App.]** Lesen Sie [diesen Abschnitt für iOS](../../delivery/using/configuring-the-mobile-application.md#configuring-ios-service). und [diesen Abschnitt für Android](../../delivery/using/configuring-the-mobile-application-android.md#configuring-android-service).
* Fügen Sie diesem Dienst die iOS- und Android-Versionen der App hinzu.
* Erstellen Sie je einen Versand für iOS und Android. [Mehr dazu erfahren Sie auf dieser Seite](../../delivery/using/creating-notifications.md).

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>Im **[!UICONTROL Abonnement]**-Tab des Dienstes finden Sie alle Abonnenten, d. h. alle Nutzer, die die App auf ihrem Mobilgerät installiert und dem Erhalt von Benachrichtigungen zugestimmt haben.

## Package-Installation {#installing-package-ios}

Wenden Sie sich als Hybrid-/Hosting-Kunde an das Kundendienstteam der Adobe, um in der Kampagne auf den Kanal für Push-Benachrichtigungen zuzugreifen.

Als lokaler Kunde müssen Sie die folgenden Installationsschritte ausführen:

1. Greifen Sie über **[!UICONTROL Tools > Erweitert > Package-Import...]** in der Adobe-Campaign-Clientkonsole auf den Package-Import-Assistenten zu.

   ![](assets/package_ios.png)

1. Wählen Sie **[!UICONTROL Standard-Package installieren]** aus.

1. Markieren Sie in der angezeigten Liste **[!UICONTROL Mobile-App-Kanal (Mobile App Channel)]**.

   ![](assets/package_ios_2.png)

1. Klicken Sie auf **[!UICONTROL Weiter]** und dann auf **[!UICONTROL Starten]**, um die Package-Installation zu starten.

   Sobald die Packages installiert sind, wird in der Fortschrittsleiste **100 %** angezeigt. Folgende Meldung wird in den Installationsprotokollen angezeigt: **[!UICONTROL Die Installation der Packages wurde erfolgreich beendet]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Schließen]** Sie das Installationsfenster.

Nach Abschluss dieses Schritts können Sie Ihre Android- und iOS-Apps konfigurieren.
Beachten Sie die folgenden Abschnitte:

* [Konfigurationsschritte für iOS](../../delivery/using/configuring-the-mobile-application.md)

* [Konfigurationsschritte für Android](../../delivery/using/configuring-the-mobile-application-android.md)

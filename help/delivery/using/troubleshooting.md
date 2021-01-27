---
solution: Campaign Classic
product: campaign
title: Fehlerbehebung
description: Fehlerbehebung
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 100%

---


# Fehlerbehebung{#troubleshooting}

Wenn Ihr Mobilgerät mit einem WLAN verbunden ist und Sie keine Benachrichtigungen erhalten, stellen Sie sicher, dass die FCM/APNS-Ports nicht von Ihrer Firewall gesperrt werden.

**Android**: Das Mobilgerät verbindet sich mit den FCM-Servern über die Ports 5228 bis 5230. Ihre Firewall muss also dahingehend konfiguriert werden, dass sie die Verbindung mit FCM zulässt. Folgende Ports sind zu öffnen: 5228 (am häufigsten verwendet), 5229 und 5230.

**iOS**:

Binärer Connector: Um Benachrichtigungen zu versenden, muss der ein- und ausgehende TCP-Verkehr über den Port 2195 zugelassen werden. Die mit dem Push-Dienst verbundenen Geräte müssen den ein- und ausgehenden TCP-Verkehr über den Port 5223 zulassen.

HTTP/2-Connector: Erlauben Sie die Kommunikation zu und von den folgenden Servern:

* api.push.apple.com: Port 443
* api.development.push.apple.com: Port 443

>[!NOTE]
>
>Weiterführende Informationen zu den beiden Connectoren finden Sie unter [Konfiguration der Mobile App in Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).

---
product: campaign
title: Fehlerbehebung bei Push-Benachrichtigungen
description: Fehlerbehebung bei Push-Benachrichtigungen
feature: Push, Troubleshooting
role: User
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 100%

---

# Fehlerbehebung{#troubleshooting}

Wenn Ihr Mobilgerät mit einem WLAN verbunden ist und Sie keine Benachrichtigungen erhalten, stellen Sie sicher, dass die FCM/APNS-Ports nicht von Ihrer Firewall gesperrt werden.

**Android**: Das Mobilgerät verbindet sich mit den FCM-Servern über die Ports 5228 bis 5230. Ihre Firewall muss also dahingehend konfiguriert werden, dass sie die Verbindung mit FCM zulässt. Folgende Ports sind zu öffnen: 5228 (am häufigsten verwendet), 5229 und 5230.

**iOS**:

HTTP/2-Connector: Erlauben Sie die Kommunikation zu und von den folgenden Servern:

* api.push.apple.com: Port 443
* api.development.push.apple.com: Port 443

>[!NOTE]
>
>Weiterführende Informationen zu den beiden Connectoren finden Sie unter [Konfiguration der Mobile App in Adobe Campaign](configuring-the-mobile-application.md).

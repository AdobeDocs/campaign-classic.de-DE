---
product: campaign
title: Fehlerbehebung bei Push-Benachrichtigungen
description: Fehlerbehebung bei Push-Benachrichtigungen
feature: Push, Troubleshooting
role: User
hide: true
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
source-git-commit: 720a5f4edf534788f7fd143a476c25e58a6f1586
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 63%

---

# Fehlerbehebung{#troubleshooting}

Wenn Ihr Mobilgerät mit einem WLAN verbunden ist und Sie keine Benachrichtigungen erhalten, stellen Sie sicher, dass die FCM/APNS-Ports nicht von Ihrer Firewall gesperrt werden.

**Android**: Das Mobilgerät stellt eine Verbindung zu den FCM-Servern an den Ports 5228 bis 5230 her. Daher müssen Sie Ihre Firewall so konfigurieren, dass sie die Verbindung mit FCM autorisiert. Die zu öffnenden Ports sind: 5228 (am häufigsten verwendet), 5229 und 5230.

**iOS**:

HTTP/2-Connector: Erlauben Sie die Kommunikation zu und von den folgenden Servern:

* api.push.apple.com: Port 443
* api.development.push.apple.com: Port 443

>[!NOTE]
>
>Weiterführende Informationen zu den beiden Connectoren finden Sie unter [Konfiguration der Mobile App in Adobe Campaign](configuring-the-mobile-application.md).

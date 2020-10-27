---
title: Fehlerbehebung
seo-title: Fehlerbehebung
description: Fehlerbehebung
seo-description: null
page-status-flag: never-activated
uuid: 02bd48cf-3928-4817-97b0-1e64cc8ad8ef
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: b64c9729-cfe2-4d02-8c59-9e53efd34a96
translation-type: tm+mt
source-git-commit: fd75f7f75e8e77d7228233ea311dd922d100417c
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 79%

---


# Fehlerbehebung{#troubleshooting}

Wenn Ihr Mobilgerät mit WLAN verbunden ist und Sie keine Benachrichtigungen erhalten, überprüfen Sie, ob die FCM/APNs-Anschlüsse nicht von Ihrer Firewall blockiert werden.

**Android**: Das Mobilgerät verbindet sich mit den FCM-Servern über die Ports 5228 bis 5230. Ihre Firewall muss also dahingehend konfiguriert werden, dass sie die Verbindung mit FCM zulässt. Folgende Ports sind zu öffnen: 5228 (am häufigsten verwendet), 5229 und 5230.

**iOS**:

Binärer Connector: Um Benachrichtigungen zu versenden, muss der ein- und ausgehende TCP-Verkehr über den Port 2195 zugelassen werden. Die mit dem Push-Dienst verbundenen Geräte müssen den ein- und ausgehenden TCP-Verkehr über den Port 5223 zulassen.

HTTP/2-Connector: Erlauben Sie die Kommunikation zu und von den folgenden Servern:

* api.push.apple.com: Port 443
* api.development.push.apple.com: Port 443

>[!NOTE]
>
>Weiterführende Informationen zu den beiden Connectoren finden Sie unter [Konfiguration der Mobile App in Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).

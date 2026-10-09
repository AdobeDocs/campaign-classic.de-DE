---
product: campaign
title: Technote – Aktualisierung des Server-Zertifikats des Push-Benachrichtigungs-Service von Apple
description: Aktualisierung des Server-Zertifikats des Push-Benachrichtigungs-Service von Apple
feature: Technote, Push
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
TQID: 'https://experienceleague.adobe.com/3tQ4npyE0-ZfCgVPYy3kiRv1q0HPcq-DI4rpAXTCXb0'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: ab81f6c3-9317-564f-af92-6670a8784294
    internal-label: Technote
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Analytics integration
  - id: a4657621-810c-498b-8a27-7ced9c176dda
    internal-label: Push notifications
source-git-commit: 3e213ecc670d5a3cb8299c092ccbb5303858327d
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 100%
---
# Aktualisierung des Server-Zertifikats des Push-Benachrichtigungs-Service von Apple {#apns-certificate-update}



Am 17. Oktober 2024 wirkte sich eine Infrastrukturaktualisierung des Push-Benachrichtigungsdienstes von Apple (Apple Push Notification service, APNs) auf den iOS-Kanal von Adobe Campaign Classic aus. Eine Anpassung der Konfiguration des Betriebssystems ist **obligatorisch**, um einen Ausfall des iOS-Push-Kanals zu vermeiden.

Weitere Informationen zu den APNs-Änderungen finden Sie [auf dieser Seite](https://developer.apple.com/news/?id=09za8wzy).

Als gehosteter Kunde besteht kein Handlungsbedarf: Adobe hat das neue Stammzertifikat bereits in Ihre Umgebung integriert.

Als On-Premise-/Hybrid-Kundin bzw. -Kunde müssen Sie Ihre Konfiguration aktualisieren, um einen nahtlosen Übergang **vor dem 24. Februar 2025** zu gewährleisten.

Gehen Sie wie folgt vor, um das neue Zertifikat zu integrieren:

1. Laden Sie [auf dieser Seite](https://www.sectigo.com/knowledge-base/detail/Sectigo-Intermediate-Certificates/kA01N000000rfBO) das Stammzertifikat **SHA-2 Root : USERTrust RSA Certification Authority** herunter.

1. Überprüfen Sie, ob das AAA-Zertifikat sowohl in Ihrem Betriebssystem als auch in den JAVA-TrustStores vorhanden ist. Ist dies nicht der Fall, fügen Sie es hinzu.

1. Starten Sie den Adobe Campaign-Webdienst neu:

   ```
   nlserver restart web
   ```

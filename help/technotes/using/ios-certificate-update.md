---
product: campaign
title: Technote – Aktualisierung des Server-Zertifikats des Push-Benachrichtigungs-Service von Apple
description: Aktualisierung des Server-Zertifikats des Push-Benachrichtigungs-Service von Apple
feature: Technote, Push
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 0143e0d6ebcdbd96d183ddd0c7f07beb149a9670
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 64%

---

# Aktualisierung des Server-Zertifikats des Push-Benachrichtigungs-Service von Apple {#apns-certificate-update}



Am 17. Oktober 2024 hatte ein Infrastrukturupdate des Apple Push Notification Service (APNs) Auswirkungen auf den Adobe Campaign Classic iOS-Kanal. Eine Anpassung der Konfiguration des Betriebssystems ist **obligatorisch**, um einen Ausfall des iOS-Push-Kanals zu vermeiden.

Weitere Informationen zu APNs-Änderungen finden Sie [auf dieser Seite](https://developer.apple.com/news/?id=09za8wzy).

Als gehosteter Kunde besteht kein Handlungsbedarf: Adobe hat das neue Stammzertifikat bereits in Ihre Umgebung integriert.

Als On-Premise-/Hybrid-Kunde müssen Sie Ihre Konfiguration aktualisieren, um einen nahtlosen Übergang sicherzustellen (**24. Februar 2025**.

Gehen Sie wie folgt vor, um das neue Zertifikat zu integrieren:

1. Laden Sie das **SHA-2-Stammzertifikat : USERTrust RSA Certification Authority Certificate**-Stammzertifikat [von dieser Seite](https://www.sectigo.com/knowledge-base/detail/Sectigo-Intermediate-Certificates/kA01N000000rfBO) herunter.

1. Überprüfen Sie, ob das AAA-Zertifikat sowohl in Ihrem Betriebssystem als auch in den JAVA-TrustStores vorhanden ist. Ist dies nicht der Fall, fügen Sie es hinzu.

1. Starten Sie den Adobe Campaign-Webdienst neu:

   ```
   nlserver restart web
   ```

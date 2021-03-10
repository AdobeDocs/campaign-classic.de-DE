---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: false
hidefromtoc: true
translation-type: tm+mt
source-git-commit: a21f970b6b81105517a11bcbd7f334173acc76e4
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---


# Apple Push Notification Service-Serverzertifikat aktualisieren {#apns-certificate-update}

Am 29. März 2021 wirkt sich ein Infrastrukturupdate des Apple Push Notification Service (APNs) auf den Adobe Campaign Classic iOS-Kanal aus. Eine Änderung der Betriebssystemkonfiguration ist **obligatorisch**, um einen Ausfall des iOS-Push-Kanals zu vermeiden.

Erfahren Sie mehr über die APNs-Änderungen [auf dieser Seite](https://developer.apple.com/news/?id=7gx0a2lp).

Als gehosteter Kunde ist keine Aktion erforderlich: Adobe hat das neue Stammzertifikat bereits in Ihre Umgebung integriert.

Als Vor-Ort-/Hybridkunde müssen Sie Ihre Konfiguration aktualisieren, um eine nahtlose Transition **vor dem 29. März 2021** sicherzustellen.

Gehen Sie wie folgt vor, um das neue Zertifikat zu integrieren:

1. Laden Sie das **AAACertificateServices 5/12/2020**-Stammzertifikat [von dieser Seite](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL) herunter.

1. hinzufügen es in den OS Trust Store.

1. Adobe Campaign-Webdienst neu starten:

   ```
   nlserver restart web
   ```

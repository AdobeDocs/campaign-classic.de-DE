---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: false
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 08c6e84e07da2811c91aa58ddf40c5781de2b163
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 60%

---


# Apple Push Notification Service-Serverzertifikat aktualisieren {#apns-certificate-update}

Ab dem 29. März 2021 wird sich ein Infrastruktur-Update des Apple Push Notification Service (APNs) auf den iOS-Kanal von Adobe Campaign Classic auswirken. Eine Änderung der Betriebssystemkonfiguration ist **zwingend erforderlich**, um einen Ausfall des iOS-Push-Kanals zu vermeiden.

Weitere Infos über die APNs-Änderungen erhalten Sie [auf dieser Seite](https://developer.apple.com/news/?id=7gx0a2lp).

Als gehosteter Kunde sind keine Maßnahmen erforderlich: Adobe hat das neue Stammzertifikat bereits in Ihre Umgebung integriert.

Als On-Premise- oder Hybrid-Kunde müssen Sie Ihre Konfiguration aktualisieren, um einen nahtlosen Übergang **vor dem 29. März 2021** zu gewährleisten.

Gehen Sie wie folgt vor, um das neue Zertifikat zu integrieren:

1. Laden Sie das **AAACertificateServices 5/12/2020**-Stammzertifikat [von dieser Seite](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL) herunter.

1. Überprüfen Sie, ob das AAA-Zertifikat sowohl in Ihrem Betriebssystem als auch in JAVA-Trusts vorhanden ist. Ist dies nicht der Fall, fügen Sie es hinzu.

1. Adobe Campaign-Webdienst neu starten:

   ```
   nlserver restart web
   ```


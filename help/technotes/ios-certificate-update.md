---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: false
hidefromtoc: true
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
translation-type: tm+mt
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 87%

---

# Aktualisierung des Server-Zertifikats des Push-Benachrichtigungsdienstes von Apple (Apple Push Notification service) {#apns-certificate-update}

Die für 29. März 2021 geplante Infrastrukturaktualisierung des Push-Benachrichtigungsdienstes von Apple (Apple Push Notification service, APNs) wirkt sich auf den iOS-Kanal von Adobe Campaign Classic aus. Eine Anpassung der Konfiguration des Betriebssystems ist **obligatorisch**, um einen Ausfall des iOS-Push-Kanals zu vermeiden.

Weitere Informationen zu APNs-Änderungen finden Sie [auf dieser Seite](https://developer.apple.com/news/?id=7gx0a2lp).

Als gehosteter Kunde besteht kein Handlungsbedarf: Adobe hat das neue Stammzertifikat bereits in Ihre Umgebung integriert.

Als On-Premise-/Hybrid-Kunde müssen Sie Ihre Konfiguration aktualisieren, um einen nahtlosen Übergang **vor dem 29. März 2021** zu gewährleisten.

Gehen Sie wie folgt vor, um das neue Zertifikat zu integrieren:

1. Laden Sie das Stammzertifikat **AAACertificateServices 5/12/2020** [von dieser Seite](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL) herunter.

1. Überprüfen Sie, ob das AAA-Zertifikat sowohl in Ihrem Betriebssystem als auch in JAVA-Trusts vorhanden ist. Ist dies nicht der Fall, fügen Sie es hinzu.

1. Starten Sie den Adobe Campaign-Web-Dienst neu:

   ```
   nlserver restart web
   ```

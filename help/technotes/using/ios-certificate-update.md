---
product: campaign
title: Technote - Aktualisierung des Apple Push Notification Service-Zertifikats
description: Aktualisierung des Server-Zertifikats des Push-Benachrichtigungs-Service von Apple
feature: Technote, Push
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 94%

---

# Aktualisierung des Server-Zertifikats des Push-Benachrichtigungs-Service von Apple {#apns-certificate-update}



Am 29. März 2021 wirkte sich eine Infrastrukturaktualisierung des Push-Benachrichtigungsdienstes von Apple (Apple Push Notification service, APNs) auf den iOS-Kanal von Adobe Campaign Classic aus. Eine Anpassung der Konfiguration des Betriebssystems ist **obligatorisch**, um einen Ausfall des iOS-Push-Kanals zu vermeiden.

Weitere Informationen zu APNs-Änderungen finden Sie [auf dieser Seite](https://developer.apple.com/news/?id=7gx0a2lp).

Als gehosteter Kunde besteht kein Handlungsbedarf: Adobe hat das neue Stammzertifikat bereits in Ihre Umgebung integriert.

Als On-Premise-/Hybrid-Kunde müssen Sie Ihre Konfiguration aktualisieren, um einen nahtlosen Übergang **vor dem 29. März 2021** zu gewährleisten.

Gehen Sie wie folgt vor, um das neue Zertifikat zu integrieren:

1. Laden Sie das Stammzertifikat **AAACertificateServices 5/12/2020** [von dieser Seite](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL) herunter.

1. Überprüfen Sie, ob das AAA-Zertifikat sowohl in Ihrem Betriebssystem als auch in den JAVA-TrustStores vorhanden ist. Ist dies nicht der Fall, fügen Sie es hinzu.

1. Starten Sie den Adobe Campaign-Webdienst neu:

   ```
   nlserver restart web
   ```

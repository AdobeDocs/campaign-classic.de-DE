---
product: campaign
title: Verwenden Sie Ihre Adobe ID, um eine Verbindung mit Adobe Campaign herzustellen
description: Erfahren Sie mehr über die Adobe IMS-Implementierung in Adobe Campaign
feature: Configuration
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 8dad8fa9-674c-433c-af30-8c6d0aadf525
TQID: https://experienceleague.adobe.com/i9Ncu86b4PZaAY6yROb-6kUdOgjbYNV1nE0Rj-Jb-OY
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: d5ef99fa-df0c-4153-bf94-105ad0724167
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 194
ht-degree: 100%

---

# Über die Adobe ID {#about-adobe-id}

Adobe Identity Management System (IMS) hilft Administratoren beim Erstellen und Verwalten des Benutzerzugriffs auf Anwendungen und Dienste. Weiterführende Informationen zu den verschiedenen Arten von Adobe-Kennungen finden Sie auf [dieser Seite](https://helpx.adobe.com/de/enterprise/using/identity.html).

Benutzerinnen und Benutzer von Campaign können mit ihrer Adobe ID eine Verbindung zur Adobe Campaign-Konsole herstellen, statt über die [native Benutzer-/Passwort-Authentifizierung](../../platform/using/access-management-operators.md). Diese Implementierung bietet folgende Vorteile:

* Verwendung ein und derselben ID für alle Adobe Experience Cloud-Lösungen.
* Speicherung der Verbindung bei der Verwendung von Adobe Campaign mit den verschiedenen Integrationen.
* Sicherere Sicherheitsrichtlinien für die Passwortverwaltung anstelle der Anmeldung mit nativem Login/Passwort.
* Verwendung von Konten des Typs Federated ID (externer ID-Provider).

>[!IMPORTANT]
>
> Hinweis: In Campaign v8 ist das Verbinden mit Benutzername/Passwort (auch als native Authentifizierung bezeichnet) nicht zulässig. **Adobe empfiehlt, diese Migration ab Campaign v7.3.5 durchzuführen, um eine reibungslose Migration zu Campaign v8 zu ermöglichen.**
>
>Informationen zur Migration zu Adobe IMS finden Sie in [diesem Abschnitt](../../technotes/using/ac-ims.md).
>


<!--
>[!IMPORTANT]
>
>If you are connecting to Campaign through Adobe Identity Service (IMS), you need to upgrade to the latest build to be able to connect to Campaign after **June 30, 2021**. This upgrade is mandatory for both Campaign server and client console. 
>
>Depending on your current version, you must upgrade to one of the following releases: 
>
> * [Campaign [!DNL Gold Standard] 11](../../rn/using/gold-standard.md)
> * [Campaign 21.1.4](../../rn/using/latest-release.md)
>
>[Learn more about IMS updates](../../technotes/using/ims-updates.md)
-->

## Mehr Ressourcen

| Nützliche Seiten | Zusätzliche Ressourcen |
|---|---|
| [IMS konfigurieren](../../integrations/using/configuring-ims.md) | [Häufig gestellte Fragen zu Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html?lang=de) |
| [IMS implementieren](../../integrations/using/implementing-ims.md) | [Zugriffsverwaltung](../../platform/using/access-management.md) |
| [Fehlerbehebung bei IMS](../../integrations/using/ims-troubleshooting.md) | [Installieren von Kampagnenkits](../../installation/using/installing-campaign-standard-packages.md) |

---
product: campaign
title: Verwenden Sie Ihre Adobe ID, um eine Verbindung mit Adobe Campaign herzustellen.
description: Weitere Informationen zur Adobe IMS-Implementierung in Adobe Campaign
feature: Configuration
badge-v7: label="v7" type="Informative" tooltip="Gilt für Campaign Classic v7"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 8dad8fa9-674c-433c-af30-8c6d0aadf525
source-git-commit: 49271e291953483ee14709b26ec053217a336718
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 60%

---

# Über die Adobe ID {#about-adobe-id}

Adobe Identity Management System (IMS) hilft Administratoren beim Erstellen und Verwalten des Benutzerzugriffs auf Anwendungen und Dienste. Weiterführende Informationen zu den verschiedenen Arten von Adobe-Kennungen finden Sie auf [dieser Seite](https://helpx.adobe.com/de/enterprise/using/identity.html).

Campaign-Benutzer können über ihre Adobe ID statt über die [native Benutzer-/Kennwortauthentifizierung](../../platform/using/access-management-operators.md). Diese Implementierung bietet folgende Vorteile:

* Verwendung ein und derselben ID für alle Adobe Experience Cloud-Lösungen;
* Die Verbindung wird bei Verwendung von Adobe Campaign mit verschiedenen Integrationen beibehalten.
* Sicherheitsrichtlinie für die Kennwortverwaltung anstelle der nativen Anmeldung/des nativen Kennworts.
* Verwendung von Konten des Typs Federated ID (externer Identity Provider).

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

---
title: Über Adobe Experience Manager
seo-title: Über Adobe Experience Manager
description: Über Adobe Experience Manager
seo-description: null
page-status-flag: never-activated
uuid: c523822f-8178-4989-bd88-ab402470e540
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 0d617f1c-0d0b-489f-9027-a92b1f1eee37
translation-type: tm+mt
source-git-commit: d15e953740b0a4dd8073b36fd59b4c4e44906340
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 75%

---


# Über Adobe Experience Cloud-Auslöser{#about-adobe-experience-triggers}

[!DNL Triggers] ist eine Integration zwischen Adobe Campaign und Adobe Analytics mithilfe der Pipeline. Die Pipeline ruft Aktionen oder Auslöser der Benutzer von Ihrer Website ab. Ein Beispiel für einen Auslöser ist ein Warenkorbabbruch. Auslöser werden in Adobe Campaign verarbeitet, um in nahezu Echtzeit E-Mails zu senden.

[!DNL Triggers] führen nach der Aktion eines Benutzers in einem kurzen Zeitraum Marketing-Aktionen aus. Die typische Reaktionszeit beträgt weniger als eine Stunde.

Dadurch werden flexiblere Integrationen möglich, da der Konfigurationsaufwand minimal ist und keine Drittanbieter beteiligt sind.
Unterstützt werden auch große Traffic-Volumen, ohne dass die Performance von Marketing-Aktivitäten leidet. Beispielsweise kann die Integration eine Million Auslöser pro Stunde verarbeiten.

## [!DNL Triggers]-Architektur {#triggers-architecture}

Der [!DNL pipelined]-Prozess wird auf dem Adobe Campaign-Marketing-Server kontinuierlich ausgeführt. Er stellt eine Verbindung zur Pipeline her, ruft die Ereignisse ab und verarbeitet sie sofort.

![](assets/triggers_2.png)

Der [!DNL pipelined]-Prozess meldet sich mit einem Authentifizierungsdienst bei Experience Cloud an und sendet einen privaten Schlüssel. Der Authentifizierungsdienst gibt ein Token zurück. Das Token dient beim Abrufen der Ereignisse zum Authentifizieren.

For more information on authentication, refer to this [page](../../integrations/using/configuring-adobe-io.md).

>[!NOTE]
>
>Die weitere Verarbeitung von Ereignissen erfolgt im Rahmen des ACX-Pakets, das außerhalb der Standardimplementierung bereitgestellt wird. Empfangenes Ereignis wird sofort mit JavaScript-Code verarbeitet. Er wird ohne weitere Verarbeitung in Echtzeit in einer Datenbanktabelle gespeichert. Die Auslöser werden für das Targeting von einem Kampagnen-Workflow verwendet, der E-Mails sendet. Die Kampagne wird so eingerichtet, dass der Kunde, der das Ereignis ausgelöst hat, eine E-Mail erhält.

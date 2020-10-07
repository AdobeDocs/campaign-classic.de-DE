---
title: Regenerieren von Schemata
seo-title: Regenerieren von Schemata
description: Regenerieren von Schemata
seo-description: null
page-status-flag: never-activated
uuid: 455c37f1-cbaf-4503-b2e9-5eec7fad6e97
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 0f7c835e-b429-422b-87ae-1234c7dd8fe6
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 7%

---


# Regenerieren von Schemata{#regenerating-schemas}

Wenn Sie ein Schema ändern und die Änderungen speichern, wird automatisch ein erweitertes Schema generiert. Möglicherweise müssen Sie Schema jedoch manuell neu generieren, um Änderungen anzuwenden. Gehen Sie dazu wie folgt vor:

1. Wählen Sie die zu regenerierenden Schema aus.
1. Klicken Sie mit der rechten Maustaste und wählen Sie &quot; **[!UICONTROL Aktionen&quot;> &quot;Ausgewählte Schema neu generieren&quot;...]** .
1. Klicken Sie auf **[!UICONTROL OK]** , um den Prozess zu bestätigen und zu starten.

Anschließend können Sie die Struktur des generierten Schemas auf den Registerkarten &quot;Vorschau&quot;und &quot;Dokumentation&quot;überprüfen. For more on this, refer to the [Principles](../../configuration/using/data-schemas.md#principles) section.

>[!NOTE]
>
>Wenn Sie die Wiederherstellung des gesamten Schemas erzwingen müssen, um beispielsweise bestimmte Abhängigkeitsprobleme in den Reverse-Links zu lösen, können Sie den folgenden Befehl vom Adobe Campaign-Anwendungsserver starten:
>
>**nlserver config -postupgrade -instance:` &lt;instance_name>&#39; -force**
>
>Anschließend müssen Sie den Adobe Campaign-Anwendungsserver neu starten und die Verbindung zur Client-Konsole trennen/wiederherstellen.
